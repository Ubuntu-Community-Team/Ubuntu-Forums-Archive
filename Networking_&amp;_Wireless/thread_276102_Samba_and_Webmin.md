---
title: "Samba and Webmin"
date: 2006-10-12
forum: Networking &amp; Wireless
---

### Post by EmyrB on 2006-10-12
Hi,

I am trying to set up a ubuntu 6.10 server and have managed to get over a few hurdles and I have finally got webmin to work. I installed samba through apt-get and it all seemd to go fine, the problem is that webmin says that it cannot find any of the samba files as they are missing.

I did a check on the samba module within webmin and the path it gives for samba is /usr/local/samba. My server does not have a samba entry in /usr/local. The config file is under /etc/samba and I can't seem to find anything else, for instance where does smbd live?

Any help with this would be very greatfully recieved.

Cheers

EmyrB

---

### Post by thelarster on 2006-10-12
I'm a newbie so I'm not sure how much this will help, but I used SWAT to help install Samba - quick howto - [http://www.jonhoweonline.com/blog/node/87]("http://www.jonhoweonline.com/blog/node/87")


I think my smbd is at /usr/sbin/

I also followed this [http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")

---

### Post by EmyrB on 2006-10-13
Hi thelarster, thanks for the reply. I have downloaded swat and I shall now spend some time reading up on samba now.

I would be happier with just webmin to do it all, so if anybody knows where samba hides smbd and nmbd in Ubuntu I would be very greatfull.

In the meantime, show me to the section on Samba my good man.

---

### Post by Iowan on 2006-10-13
> **EmyrB said:**
> ... so if anybody knows where samba hides smbd and nmbd in Ubuntu I would be very greatfull.
 You could try (from a terminal):
```
find / -name "smbd"
```

---

### Post by EmyrB on 2006-10-16
Hey thanks for that Iowan, I shall give that a try :)

---

