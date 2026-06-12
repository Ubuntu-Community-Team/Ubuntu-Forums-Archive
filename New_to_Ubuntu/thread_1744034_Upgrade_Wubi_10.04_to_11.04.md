---
title: "Upgrade Wubi 10.04 to 11.04"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by webmanoffesto on 2011-04-30
How can I upgrade Wubi 10.04 (Lucid Lynx) to 11.04 (Natty Narwhal)

I now have a dual-boot system. I used Wubi installer to install Ubuntu 10.04. I'd like to upgrade that to 11.04. 
I followed the instructions here
[https://help.ubuntu.com/9.10/about-ubuntu/C/upgrade.html](https://help.ubuntu.com/9.10/about-ubuntu/C/upgrade.html)
and it just offered to upgrade me to 10.10. Is that because I must upgrade to 10.10 before 11.04?

What's the best way to upgrade?

Is it worthwhile upgrading to 10.10 on a desktop. What I found online is that 10.10 
"was announced by Mark Shuttleworth on 2 April  2010, along with the release's goals of improving the netbook  experience and a server focus on hybrid cloud computing."

---

### Post by beew on 2011-04-30
> **webmanoffesto said:**
> How can I upgrade Wubi 10.04 (Lucid Lynx) to 11.04 (Natty Narwhal)

I now have a dual-boot system. I used Wubi installer to install Ubuntu 10.04. I'd like to upgrade that to 11.04. 
I followed the instructions here
[https://help.ubuntu.com/9.10/about-ubuntu/C/upgrade.html](https://help.ubuntu.com/9.10/about-ubuntu/C/upgrade.html)
and it just offered to upgrade me to 10.10. Is that because I must upgrade to 10.10 before 11.04?

What's the best way to upgrade?

Is it worthwhile upgrading to 10.10 on a desktop. What I found online is that 10.10 
"was announced by Mark Shuttleworth on 2 April  2010, along with the release's goals of improving the netbook  experience and a server focus on hybrid cloud computing."

First of all, WUBI is not a "dual boot". It is not a real ubuntu install, it is for try and see. A dual boot means Ubuntu and Windows existing side by side as equals, not when Ubuntu is given a folder to run within Windows.

Secondly, never mind upgrade, just use Add/Remove in Windows to remove it and install a newer version. Even people with real install into hard drive have enough problems upgrading (as oppose to clean install)

---

### Post by bcbc on 2011-04-30
> **webmanoffesto said:**
> How can I upgrade Wubi 10.04 (Lucid Lynx) to 11.04 (Natty Narwhal)

I now have a dual-boot system. I used Wubi installer to install Ubuntu 10.04. I'd like to upgrade that to 11.04. 
I followed the instructions here
[https://help.ubuntu.com/9.10/about-ubuntu/C/upgrade.html](https://help.ubuntu.com/9.10/about-ubuntu/C/upgrade.html)
and it just offered to upgrade me to 10.10. Is that because I must upgrade to 10.10 before 11.04?

What's the best way to upgrade?

Is it worthwhile upgrading to 10.10 on a desktop. What I found online is that 10.10 
"was announced by Mark Shuttleworth on 2 April  2010, along with the release's goals of improving the netbook  experience and a server focus on hybrid cloud computing."
There are still problems with the Wubi upgrade from 10.04 to 10.10 (see [here]("http://http://ubuntuforums.org/showthread.php?t=1639198")). There are no issues with the Wubi 10.10 to 11.04 upgrade, but you'd have to deal with the 10.10 upgrade issues. 

If you decide to upgrade take a backup first of your virtual disk (root.disk).

PS uninstalling from windows will delete everything on Ubuntu.

---

