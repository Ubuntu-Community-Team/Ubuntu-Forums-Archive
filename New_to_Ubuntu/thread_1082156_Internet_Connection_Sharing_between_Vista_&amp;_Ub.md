---
title: "Internet Connection Sharing between Vista &amp; Ubuntu host"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by Psyclips3 on 2009-02-27
Hi,

I am extremely new at this and would appreciate all and any help!

I have 2 laptops, 1 has Ubuntu 8.10 and the other has Windows Vista (with Norton 360 V 2.0). They are both connected via wireless lan. Ubuntu however, cannot view anything on Vista. Not sure about the other way around either, tried to share a folder but not visible from Vista.
This has been perplexing me for quite a while now... tried to search the forums but no luck. :(

Thanking you in advance!

---

### Post by tbastian on 2009-02-27
Do you have samba enabled? You can follow the included link to find out how to set it up if you're not sure.

[http://www.watchingthenet.com/enable-file-sharing-in-ubuntu-using-samba.html](http://www.watchingthenet.com/enable-file-sharing-in-ubuntu-using-samba.html)

---

### Post by Psyclips3 on 2009-02-28
Hi tbastian,

Thank you for replying. If the purpose of the link was to ensure that I had Samba enabled, then yes, I do. The instructions on the link however were hard to follow. The first instruction to go to System \ Administration \ Networking... the closest thing that's on my menu is Network Tools & doesn't look anything like what's on the video or in the steps to follow (neither does it have the functionality that is required by the instructions).
Does this mean that another App needs to be installed or am I still okay?

---

### Post by tbastian on 2009-03-03
Psyclips3,

I did some more searching and did some testing myself and realised that the tutorial posted earlier was directed to an older version of ubuntu and wasn't that helpful. I found another tutorial that was for 8.10 and worked well for me. This is to configure the linux computer, but you may have to run the 'setup network' wizard under windows to get it working the other way.

[http://jngalloway.wordpress.com/2008/06/08/easy-file-sharing-in-ubuntu-no-editing-text-files/](http://jngalloway.wordpress.com/2008/06/08/easy-file-sharing-in-ubuntu-no-editing-text-files/)

I hope this helps you. let me know how it turns out!

---

### Post by Iowan on 2009-03-03
A quick/dirty check is to use smb://ip-address-of-WinBox/sharename in the Location box of Places>Network.  A more permanent fix *might* involve installing **Winbind** and editing **nsswitch.conf** (I'll need to look for details).

---

### Post by Ms_Angel_D on 2009-03-03
Hello Psyclips3,

I was having the hardest time mounting my windows vista shares from ubuntu until I found this thread ([http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)) You might want to take a look at it. I hope this helps.

Angel

---

### Post by bodhi.zazen on 2009-03-03
You mentioned wireless and so I suggest you first connect over a hard wired connection. Some wireless routers, for security, will not allow you to connect to a samba server (clients OK).

---

