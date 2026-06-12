---
title: "can't share folder from one HDD with samba"
date: 2017-07-08
forum: Networking &amp; Wireless
---

### Post by moscatheway on 2017-07-08
hello all,

i started to use samba nearly one year ago. in the beginnig all worked perfectly but suddenly, after i reinstalled ubuntu, everything stopped working. 
i have an SSD for the OS (ubuntu 17.04) and one HDD that i use to store my video library. i need to share all the video library but in the moment i create a new directory in the HDD samba can't share it. in other words on my others PCs i can see the directory but cannot open it (probably for permissions or something like that). 
but if i create the same directory on the SSD and use the same kind permissions on this directory it works perfectly. anyone has an idea why that happens? (sorry for my english, hope that the message is clear if not please ask, i can try to explain it more).

on both directories i used the following comands: 
   chmod  -R myuser:nogroup /path
   chown -R 0777 /path

using these works perfectly on the SSD but not on the HDD...

this is what i changed in the smb.conf

[name]
path = /path
browsable = yes
writeable = yes
guest ok = yes
read only = no
force user = nobody

---

### Post by manselem on 2017-07-09
I have been trying to get a similar setup going. My issue is samba speeds. But i had same issue using the smb.conf file to manage permissions. so even though technically one should avoid using nautilus for managing permissions i did. i opened terminal(ctl+alt+t), typed gksudo gedit nautilus, entered password at prompt and than superuser root nautilus browser opens. I right clicked on the sambashare Drive and went to properties. there is 3 tabs on top. i made sure i enabled everything and changed permissions to be 777. I wish i could help you more with getting users and passwords and .conf files all working but it was to convuluted for me and always giving me headaches on client side not have correct permissions. i think most people use samba at home behind firewall and they just want to use it as a local NAS so there is no need for all this fancy logins and authentications etc.. as for your speeds what kind of transfer rates you getting?

---

### Post by Morbius1 on 2017-07-09
> on both directories i used the following comands: 
   chmod  -R myuser:nogroup /path
   chown -R 0777 /path
Can I assume you meant to post:
> on both directories i used the following comands: 
   **[COLOR=#0000cd]chown[/COLOR]** -R myuser:nogroup /path
**[COLOR=#0000cd]chmod[/COLOR]** -R 0777 /path 
What exactly is the /path? One man's path is another man's obstacle.

If the path something like /mnt/Video it is one thing. If it's something like /media/**[COLOR=#0000cd]myuser[/COLOR]**/Video then your share definition will not work regardless of who owns the folder and permissions. The only way it will work is if the share definition changes to this:
> [name]
path = /path
browsable = yes
writeable = yes
guest ok = yes
read only = no
[COLOR=#0000cd]force user = **myuser**[/COLOR]         
There is an access control list on /media/myuser that prevents everyone accept myuser from gaining access to what’s beyond it.

---

