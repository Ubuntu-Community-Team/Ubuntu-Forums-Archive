---
title: "secure ftp to lame terastation"
date: 2007-07-26
forum: Networking &amp; Wireless
---

### Post by dannemil on 2007-07-26
I have a TeraStation NAS-device that I use to backup data and store files. When I am behind the router I can use samba to mount this device as a folder on my machine so there is no problem in copying files to or from it.

I would also like to be able to get and put files on this device when I am at home outside the router. The terastation has an ftp server that will work for this, but I am worried because then my password could be sniffed and the NAS compromised.

The terastation does not have an ssh server, and it will not accept sftp connections. I should also mention that to get to the terastation I have set up port forwarding on the router to forward ftp connections on port 21 from the router to the terastation. But of course, I still have to send my password for the ftp server to the router unencrypted.

So unless I hack the terastation to enable ssh (something I am loathe to do at this point), I am stuck with having to access files using ftp. Can anyone suggest a way to secure my password for the ftp server or is this just an impossibility at this point?

---

### Post by yanyan on 2008-04-02
Hi, I am facing the same problem as you solved before. I need to work on Ubuntu system and connect to terastation inside my lab. It is great that you did that. Could you tell me how you did that? How to use Samba to do that? I am a newcomer to Ubuntu. Thanks a lot.[http://ubuntuforums.org/images/smilies/star.png](http://ubuntuforums.org/images/smilies/star.png)

---

