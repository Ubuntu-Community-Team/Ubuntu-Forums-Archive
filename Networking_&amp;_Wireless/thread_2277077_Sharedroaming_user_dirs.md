---
title: "Shared/roaming user dirs"
date: 2015-05-06
forum: Networking &amp; Wireless
---

### Post by markeee on 2015-05-06
Hi all.

Not quite sure where to post this / what exactly to title it
basically I have several machines , 2 laptops / netbook / desktop / and then a Linux server and a raspberry pi

I'd like to create a scenario whereby Windows user dirs are actually stored on the server - and I can login to any windows machine using the same user/pass (stored on the server ) and it loads the dir off the server

From what I've read NFS and Samba as a PDC? I don't need openLDAP or Kerberos for this?



Thanks

---

### Post by TheFu on 2015-05-07
For Windows - you want Samba4.  NFS is only for Unix-to-Unix (not really true, but nobody uses it for Windows).
However, if the user's directories are on the network and you take the laptop/netbook away - what happens?

For the raspberry pi, the networking is slow, so accessing a HOME on the "server" might not be as great as you hope.  Use NFS for this, make the userids/groupids match and all will be fine - well except if any files are platform dependent. The rpi is ARM and I suspect the server is x86. Sometime having different GUI config files in the same HOME doesn't work well.  I know it is possible - I had the same HOME for about 12 different OSes in the mid-1990s, just had to be careful trying to run compiled programs in my ~/bin/ on the wrong platform. Obviously, running a solaris program on an HP-UX system doesn't work - but it is not too hard to make scripts cross-platform provided the dependencies are available on all the needed platforms.

Clear as mud?

Anyway - for Samba4 stuff - I'd start reading at the samba.org website. We don't use Windows much here, so I can't help any more than that.  There are probably books with how-to chapters.  Google found this: [https://help.ubuntu.com/lts/serverguide/samba-dc.html](https://help.ubuntu.com/lts/serverguide/samba-dc.html) which appears to answer the Windows/Samba4 question.

---

