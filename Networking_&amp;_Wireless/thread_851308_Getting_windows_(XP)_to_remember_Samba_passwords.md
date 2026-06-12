---
title: "Getting windows (XP) to remember Samba passwords"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by masterdam79 on 2008-07-06
Hiya everyone,

Just something that's busting my nuts is the following..

[SETUP]

Ubuntu 7.10 desktop server with Samba server and smb user Ina with setup password with "smbpasswd -a Ina"

Windows Vista (Home Premium) desktop with windows user "masterdam79"

Windows XP (Home) Laptop with windows user "Ina"

[PROBLEMS SOLVED]

Am now able to access the Samba shares from my Windows Vista machine WITHOUT entering username/password for my Samba user because I made a Samba user equal to my Vista windows user "masterdam79".

I was able to select the "Remember my password" checkbox on my Vista machine, first time I logged on into the Ubuntu server.

[PROBLEMS NOT SOLVED]

Am able to access the Samba shares from my Windows XP machine WITH entering username/password for my Samba user which I made equal to my XP windows user "Ina"

I was NOT able to select the "Remember my password" checkbox on my XP machine, which brings me to the target set out on the subject of this post.

How do I make Windows XP remember my Samba password and why is Vista remembering it without a problem?

Where is my "Remember my password" checkbox on XP?


Much thanks!!:popcorn:

---

