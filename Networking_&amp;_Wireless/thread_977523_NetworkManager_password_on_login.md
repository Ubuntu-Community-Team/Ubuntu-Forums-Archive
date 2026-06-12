---
title: "NetworkManager password on login"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by HunterGuy2 on 2008-11-10
Hi,
Is it possible to get Network-manager to *stop* asking for my gnome password whenever I login (8.10)? In Gutsy (the last version I tried), I remember it would automatically login to my preferred wireless network without me having to enter my wifi password on every reboot. Please help me out here, I've actually done a fair bit of searching, but it seems like nobody has posted this problem since Dapper.

Thanks!


**EDIT: I installed with the auto-login option, could that be related?

---

### Post by Mark224 on 2008-11-10
In Hardy the only way I managed to solve this was to configure networking entirely manually.

If you changed your password then this can sometimes cause problems.

---

### Post by Rhubarb on 2008-11-10
> **HunterGuy2 said:**
> ... **EDIT: I installed with the auto-login option, could that be related?

Yes, if you turn off auto-login (System --> Administration --> Login Window
Security tab, uncheck "Enable Automatic Login" and "Enable Timed Login".

I'm sure there are other ways to get rid of the password prompt - at a some risk to security.

---

### Post by HunterGuy2 on 2008-11-10
Thanks, I'll try that out when I get home.

>>I'm sure there are other ways to get rid of the password prompt - at a some risk to security. 

I saw an app in the administration menu which seemed to allow pre-granting access rights; there was an entry for network-manager, with an action something along the lines of 'change system connections'. I tried granting permission for that, but it didn't do anything that I could see. Do you know if I can use this (or some other tool) to achieve password-less network login?

Thanks!

---

### Post by Rhubarb on 2008-11-10
Very good point there HunterGuy2, I think that may just work.
System --> Administration --> Athorizations
org --> freedesktop --> network-manager-settings --> system --> Modify system connections
Then somewhere in there you should be able to give your user automatic authorizations.

I haven't tried this myself, but it looks like it just might work for you.

---

### Post by Zer0Nin3r on 2008-11-17
> **Rhubarb said:**
> Very good point there HunterGuy2, I think that may just work.
System --> Administration --> Athorizations
org --> freedesktop --> network-manager-settings --> system --> Modify system connections
Then somewhere in there you should be able to give your user automatic authorizations.

I haven't tried this myself, but it looks like it just might work for you.

Has anyone verified this yet?

---

