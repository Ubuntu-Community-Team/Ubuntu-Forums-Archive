---
title: "Ubuntu box gets inaccessible after some time"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by acken on 2007-05-03
Upgraded my edgy box to feisty and started getting some problems with accessing it remote (ssh,apache,vnc etc). Tried to reinstall a fresh version but still got the same problem. I can start my ubuntu box and everything runs fine for some time then suddenly I can't even ping it from my local network. I can access internet and everything from the ubuntu box but its inaccessible to other computers. Seems to happen faster when using vnc or cygwin/ssh or any kind of remote UI stuff. Im quite lost so if anyone has any idea that would be great!

---

### Post by acken on 2007-05-10
I hva avvoided running vnc and ssh/cygwin for some time now and I don't get the same problem. But then again I REALLY want to run GUI stuff remote. Am I the only one having this problem?

I have one network adapter and static IP, Firestarter is not installed and no other firewall either if feisty don't provide one by default.

Slowly but surely working on an ulcer so please anyone! :)

---

### Post by Yakyb on 2007-05-10
[http://ubuntuforums.org/showthread.php?t=437843]("http://ubuntuforums.org/showthread.php?t=437843")

my link above details the exact same problems although using Samba (although it does occur using VNC as well). did this occur on edgy  as  im considering moving back down to it until this issue is resolved

---

### Post by acken on 2007-05-10
Trouble started after upgrading to feisty. Although VNC didn't work for me under edgy I used ssh/cygwin all the time without running in to this problem.

---

### Post by acken on 2007-05-21
Tried a couple of things last time it happened without any luck. ifconfig down / up did not work. init.d/networking restart complained about /dev/eth0 not found but again after a restart it was up again. Now of course its down again and my server has become a waste of space in my apartment. Would really appreciate some help. Don't want to spend a month getting another distro up and running..

---

