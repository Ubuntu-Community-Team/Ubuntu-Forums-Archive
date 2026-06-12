---
title: "trouble Joining in windows domain"
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by ubuscout on 2007-03-23
Hi folks,

I'm starting to join a ubuntu desktop in windows domain and so after some topic search here, I start to follow this guideline

[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

but of course I've ogt some little problem :( 

1) the command  "/etc/init.d/ntpdate restart" give me the answer "No such file or directory" so after little bit trouble I see that file don't start like a service from init.d but I can find it under /usr/sbin/  and from there "sudo /usr/sbin/ntpdate <servername>" works fine. But if I want start it at boot like a service what I must do ? (ps. I've just configured /etc/default/ntpdate as suggested in guideline)


2) after modified smb.conf and stopping/restarting winbind and samba deamon, when I enter "sudo net ads join -U <myusername>" I get this error :

"[2007/03/23 09:48:26, 0] utils/net_ads.c:ads_startup(191)
  ads_connect: Transport endpoint is not connected"

...and here I am... :(

plz some advice, I really want to use ubuntu in domain !

thx for all

---

### Post by ubuscout on 2007-03-23
Some progress :)

I've joined in domain, but I would like automatize the kerberos ticket request and start ntpdate as service at boot... how I can do it ?

...I've tried to create two link on etc/rc5.d, but for kerberos ticket I need pass the password when it launch "kinit" command how can i automatize this ?

---

### Post by machu on 2007-04-04
Hello 

How did you manage to correct this error: " ads_connect: Transport endpoint is not connected"  ? ?

I'm stuck on it.

---

### Post by ubuscout on 2007-04-04
oops almost forgot it...  ;) 

If I remember well, It was 'cause I've missed the option

"password server = 10.0.0.1" in smb .conf

here u must insert your server's ip address.

bye :D

---

### Post by ubuscout on 2007-04-04
sorry, almost forget another time... :(  

The solution for automatize login authentication I've follow this post

[http://ubuntuforums.org/showthread.php?t=370989&highlight=script+login](http://ubuntuforums.org/showthread.php?t=370989&highlight=script+login)

with rc.local

...everything works fine  :)

---

