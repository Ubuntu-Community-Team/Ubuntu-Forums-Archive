---
title: "I can't turn on Wi-Fi in Ubuntu 14"
date: 2015-02-22
forum: Networking &amp; Wireless
---

### Post by jsabath on 2015-02-22
[COLOR=#000000]Hey. I just installed Ubuntu 14 on my Lenovo x131e. I had Windows 7 Professional on it before installation, and I am a first time Ubuntu user, so I don't know much. Upon installing Ubuntu, I found that I can not turn on Wi-Fi. The button to turn it on in system settings does not work or even switch to on. I can only hook up to the internet through ethernet, which is really irritating. What should I do to allow Wi-Fi to run from the minute I turn on my computer? I really need help here. The forums I have looked into have been of no help. Your help would be much appreciated.[/COLOR]

---

### Post by kerry_s on 2015-02-22
what wifi card ? it's most likely you just need to install the firmware.

---

### Post by Hadaka on 2015-02-22
hi,please do..
```
sudo modprobe -r ideapad-laptop
sudo rfkill unblock all
rfkill list all
```
if it works..do this
```
sudo -i
echo "blacklist ideapad-laptop"  >>  /etc/modprobe.d/blacklist.conf
exit
```
thanks.

---

### Post by jsabath on 2015-02-25
Yeah, so I did all of the code that you suggested, but it didn't work.  I have a broadcom wifi card which is supposedly supported in additional drivers of software & update in system settings.  However, I cannot seem to remove the hardblock on the bluetooth and the wifi.  I think that I had them turned off in Windows when installing Ubuntu, and now I can't seem to turn them off.  I have tried the buttons on my keyboard to turn them on, but it does not function.  Does this help?

---

