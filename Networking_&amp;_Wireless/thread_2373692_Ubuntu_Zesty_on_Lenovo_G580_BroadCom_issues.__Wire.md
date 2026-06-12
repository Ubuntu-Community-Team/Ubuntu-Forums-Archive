---
title: "Ubuntu Zesty on Lenovo G580 BroadCom issues.  Wireless doesn't show."
date: 2017-10-08
forum: Networking &amp; Wireless
---

### Post by bandana.blue on 2017-10-08
New install of Ubuntu. 

I'm trying to get the wireless card to work.  The wireless symbol doesn't show in the upper right part of screen.  No list of wireless signals.  Which is strange because they did show when I was installing.  Although I couldn't get them to work while installing.  If I type ```
sudo service network-manager restart
``` into the terminal the wireless symbol shows up in a popup window that says the wireless is closed.

First I ran this code.
```
echo -e "blacklist b43\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
from this thread: [https://ubuntuforums.org/showthread.php?t=2229619](https://ubuntuforums.org/showthread.php?t=2229619)
Because that person has the same computer as me and I figured it was the same problem, but that didn't fix it.

Then I found this thread.
[https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)
Using the code there figured out that the
pci.id is 14e4:4727 making it special case 1

and ran wireless_script to try to figure out what was going on.

Then I blacklisted b43 and ssb because the stickied thread said that might work but it didn't.

Then I read the sticked notes and the other one recommended I update so I did that and also ran wireless_script such that it pasted to 
ubuntu pastebin.

[URL="http://paste.ubuntu.com/25704537/"]http://paste.ubuntu.com/25704537/
[/URL]
Also ran the code to blacklist b43 and ssb again just in case having the updates would make a difference.

---

### Post by jeremy31 on 2017-10-09
```
sudo apt-get purge bcmwl-kernel-source
```
Reboot and see if it works

---

### Post by Hadaka on 2017-10-10
Hi, your second wireless printout shows multiple issues.
From a working wired connection please do.
*as jeremy31 suggested ~
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo modprobe -rf bcma
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
Please Copy and paste..
```
sudo iw reg set US
sudo sed -i 's/=.*/=US/' /etc/default/crda
```
*Since you are NOT using the b43 or wl driver there is no need
to blacklist b43  or  ssb... Correct driver is..[COLOR=#ff0000]brcmfmac[/COLOR]
Please do..
```
sudo sed -i '/b43\|ssb/ d' /etc/modprobe.d/blacklist.conf
```
then do..
```
sudo modprobe -rf brcmfmac
sudo modprobe -v brcmfmac
```
remove wired connection,boot and test wireless
Thanks.

# @bandana.blue..corrected command 
#sudo modprobe rm -rf bcma..incorrect
#sudo modprobe -rf bcma..correct

---

### Post by bandana.blue on 2017-10-10
```
sudo apt-get dist-upgrade
```

Wasn't working but then I pressed update under ubuntu software and it worked up until

```
sudo modprobe rm -rf bcma

```
Which gave:
modprobe: FATAL: Module rm not found.


```
sudo apt-get remove --purge bcmwl-kernel-source
```
worked
```
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
rm: cannot remove '/etc/modprobe.d/blacklist-bcm43.conf': No such file or directory


Everything else went.  Going to boot and test wireless now.

---

### Post by bandana.blue on 2017-10-10
IT WORKS.  Thank you Jeremy and Hadaka. :guitar:




In retrospect I should have just edited this into the previous post.

---

### Post by jeremy31 on 2017-10-10
Please use the thread tools menu near the top right of the page to mark thread as solved

---

