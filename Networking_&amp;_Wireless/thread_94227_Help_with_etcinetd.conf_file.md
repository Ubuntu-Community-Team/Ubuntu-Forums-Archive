---
title: "Help with /etc/inetd.conf file"
date: 2005-11-23
forum: Networking &amp; Wireless
---

### Post by QWERTY on 2005-11-23
I am a big newbee to linux and I have been strugling a lot with the wu-ftpd to get it to work. In the /etc/inetd.conf I had the following line, but wu-ftpd did not work (connection refused):

ftp		stream	tcp	nowait	root	/usr/sbin/tcpd	/usr/sbin/wu-ftpd

I then try to change "ftp" to "ftptest" and now it works :confused: :

ftptest		stream	tcp	nowait	root	/usr/sbin/tcpd	/usr/sbin/wu-ftpd


I have read somewhere that the "ftp" and "ftptest" refers to entries in the /etc/services file but there is no ftptest entry here - only the ftp.

My question is then:
what is it you are specifying in the inetd.conf file?
What is the meaning with "/usr/sbin/tcpd" and "/usr/sbin/wu-ftpd" in the inetd.conf line? Is it important what these are? And what are they used for?

Regards and thanks

---

### Post by mlomker on 2005-11-23
TCPD is a tcp wrapper--it handles logging and provides some additional security over running a daemon on its own.  Think of it as running a program inside of a box so that it can only do things that you allow it to.

I think the problem with getting it to run from inetd.conf is related to the root account being disabled in Ubuntu (everything runs by sudo).  I got it to work by doing a **sudo dpkg-reconfigure wu-ftpd** and selecting it to run 'standalone' rather than in inetd mode.

---

