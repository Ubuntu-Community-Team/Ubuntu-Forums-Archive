---
title: "Installed 12.04. But lost Wifi capability"
date: 2014-03-30
forum: Networking &amp; Wireless
---

### Post by gabmuks on 2014-03-30
Hello and good day.

I have read the stickies posted here but could not find solution.

I found my broadcom identification number.

It is:      [14e4:4318] (rev 02)

But I could not figure out how to find it or install it (even if I did find it).
Can anyone help?

Thank you for your time.

---

### Post by Hadaka on 2014-03-30
hi, open a terminal..ctrl/alt/t and do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo modprobe -rf wl
```
then from a wired connection to the internet....do
```
sudo apt-get update
sudo apt-get upgrade
```
then to install the correct driver...do..
```
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```
boot.
*IGNORE any offer of proprietary or additional drivers ...they are incorrect !
how to mark SOLVED ->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by chili555 on 2014-03-30
Did you check this sticky? [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110) Your device is listed. If you have tried the steps there and not been successful, please tell us what went wrong.

EDIT: Hadaka is quite correct.

---

### Post by gabmuks on 2014-03-30
Worked!!!!

Thank you much!!!
Wifi is up and runnng.
Thank you Master!!!\\:D/\\:D/\\:D/

---

### Post by Hadaka on 2014-03-30
Glad its working !

---

