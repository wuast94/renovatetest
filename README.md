i had a config that had opend an PR for sonarr to update the version.
then i changed the allowedVersions by adding missconfig in the middle so renovate cant find any valid version anymore
`"allowedVersions": "/^\\d{1,2}\\.missconfig\\d{1,2}\\.\\d{1,2}\\.\\d+-ls\\d+$/"`

no we have exactly the case mentioned in the discussion:
  - renovate detects the version from this repo
  - shows it normal in the dashboard under detected deps
  - no errors or warnings in the log file

and really nothing that would show me that i messed something up, the only reason i know that there is something wrong is becouse i know ther is an update.

this is why it would be nice if renovate would always show what version is present and what version would be applied. in this case it would say null or no match found or anything like that.
even worse, if my present version would be the latest i wouldnt have anything to check if my config or rules are right, the only way i have is to set a lower version and then check if renovate creates the PR or not.

and as i said, adding this info would be an easy way to check if everything is working or not, relying on warnings or error messages that SHOULD show up is just a bad design decission.

what i would do? just as an idea

## Detected dependencies OLD

<details><summary>docker-compose</summary>
<blockquote>

<details><summary>stacks/test.yml</summary>

 - `linuxserver/radarr 5.11.0.9244-ls240@sha256:1a50d4f08e283aa9ff4c723b940dceb4e8aeff7946e1993213efd0de3d5a4adb`
 - `linuxserver/sonarr 4.0.9.2244-ls255@sha256:98c21a64377619ec74778c70cc2e74d3e978a4d2c61f97b9ad88a0e5bc0766f9`
 - `linuxserver/sonarr 4.0.8.1874-ls251@sha256:0777b308a414000505651059a95af373ded6aba8ce5a40b50d7aad333dc912e2`
 - `linuxserver/sabnzbd:4.3.3-ls188@sha256:5ae714b1a941a38471c2cc381ec407f93b3d7823c5a77a9a651502036b70ad69`

</details>

</blockquote>
</details>

## Detected dependencies NEW

<details><summary>docker-compose</summary>
<blockquote>

<details><summary>stacks/test.yml</summary>

 - `linuxserver/radarr 5.11.0.9244-ls240@sha256:1a50d4f08e283aa9ff4c723b940dceb4e8aeff7946e1993213efd0de3d5a4adb` found `4.3.3-ls188`
 - `linuxserver/sonarr 4.0.9.2244-ls255@sha256:98c21a64377619ec74778c70cc2e74d3e978a4d2c61f97b9ad88a0e5bc0766f9` found `NULL`
 - `linuxserver/sonarr 4.0.8.1874-ls251@sha256:0777b308a414000505651059a95af373ded6aba8ce5a40b50d7aad333dc912e2` found `NULL`
 - `linuxserver/sabnzbd:4.3.3-ls188@sha256:5ae714b1a941a38471c2cc381ec407f93b3d7823c5a77a9a651502036b70ad69` found `4.3.3-ls188`

</details>

</blockquote>
</details>
