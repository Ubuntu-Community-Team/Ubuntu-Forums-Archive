---
title: "Any installation returns with Error -1 coz of firmware-b43-installer"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by jvacek996 on 2011-01-04
Ok, I might not be an absolute begginer, but this thing seems like a minor issue to me, so yeah, excuse me for being.
To the point, whenever I do anything including installation, upgrade, uninstallation or updates, i ALWAYS, literally every time, get an error such as the one quoted below. I know that the error basically doesn't really mean anything, everything works just fine even tho there is that little problem.
Maybe I should also say that I am amd64, even though I have no idea how will that help :P

(Randomly chosen from an upgrade i did just 5 seconds ago)
> [COLOR="Navy"]installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 149465 files and directories currently installed.)
Preparing to replace docky 2.1.0~bzr1746-0ubuntu1~10.10~dockycore1 (using .../docky_2.1.0~bzr1748-0ubuntu1~10.10~dockycore1_all.deb) ...
Unpacking replacement docky ...
Replaced by files in installed package stacks ...
Preparing to replace docky-dbg 2.1.0~bzr1746-0ubuntu1~10.10~dockycore1 (using .../docky-dbg_2.1.0~bzr1748-0ubuntu1~10.10~dockycore1_all.deb) ...
Unpacking replacement docky-dbg ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for gconf2 ...
Processing triggers for python-support ...
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up docky (2.1.0~bzr1748-0ubuntu1~10.10~dockycore1) ...
Setting up docky-dbg (2.1.0~bzr1748-0ubuntu1~10.10~dockycore1) ...
Errors were encountered while processing:
 firmware-b43-installer
Setting up firmware-b43-installer (4.150.10.5-4) ...
[B]Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1[/COLOR][/B]


I get this every time. And I don't like it. 1., It is friggin annoying, 2., it sometimes messes stuff up, like the last time I did a partial upgrade, it gave me this error again, and because the installation saw that there was some kind of an error, it aborted itself.

Anyone please help?

** I realised that there is something wrong with that firmware-b43-installer thing, but how to get rid of it? Anyone? I tried my "force" with -f but without any real positive result**

---

### Post by jvacek996 on 2011-01-04
Ok, my bad, my wifi drivers weren't installed properly :D that was quite unsmart

---

### Post by TeoBigusGeekus on 2011-01-04
See [this]("https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/651010") page; Kontza's post.

---

### Post by jvacek996 on 2011-01-04
thanks, but i managed to solve it already :P

---

### Post by jchw on 2011-01-23
I have exactly the same problem. Can you say how you fixed yours because I have not found a solution yet.

---

### Post by jvacek996 on 2011-04-03
Sorry for the delay :D I just installed it from the restricted fevers again, sOmehow it worked that time

---

