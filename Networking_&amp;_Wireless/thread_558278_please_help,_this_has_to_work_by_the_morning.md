---
title: "please help, this has to work by the morning"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by jasonhr on 2007-09-23
I have got our company server here and have dual booted it so that we can switch to linux. 

Everything is working now but when I try to map a drive to a shared home directory it brings up the user name and password box but won't let me log on.

I am using the exact same smb.conf as a small server sitting next to it which works perfectly  (names changes obviously) but cannot get the share to work.

Can anyone help me here as my knowledge of Linux is as limited as you'd expect after a weekends very steep learning curve. 

The samba log says "[2007/09/23 15:47:01, 0] smbd/service.c:make_connection_snum(849)
  Can't become connected user!"

Just a few pointers or things to try would be amazing!

Thanks guys

Feisty 7.04
to 
win XP machines
Latest samba
Webmin

---

### Post by wieman01 on 2007-09-24
Have you followed this HOWTO?

[http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")

---

### Post by jasonhr on 2007-09-24
Thanks for replying, I did use that how to to set up the initial machine and used the same basic .conf for the second.

I actually worked out what was wrong by about 4 in the morning. I hadn't registered the passwords in Samba....  :mad:  Hmmm...

All is working beautifully now.  :guitar:

---

