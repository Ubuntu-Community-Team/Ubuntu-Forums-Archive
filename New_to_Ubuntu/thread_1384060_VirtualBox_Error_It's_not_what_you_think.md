---
title: "VirtualBox Error *It's not what you think*"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by Goveynetcom on 2010-01-17
I am experimenting with virtual machines once again... and I ran into this error. I learned that the version of VirtualBox on the Ubuntu software software is the OSE version in which usb cannot be used. So i grabbed the normal version (after installing the previous). The .deb said that it wouldn't install because it conflicted with the OSE version. So... I removed it, but the package still says there is an error? Does this mean that there was an error removing said package or I am i need of a reboot? I have attached a picture showing off what I meant...

---

### Post by warfacegod on 2010-01-18
How did you remove Virtual Box?

FYI Set the delay for 2 seconds or so. That way when you take a screen shot, that window doesn't appear in the image. Makes it easier to read.

---

### Post by alwayshere on 2010-01-18
I have a macbook 1.1 with ubuntu 8.04 LTS as THE o.s and i have virtual box running win xp just fine usb and all .

do you have  guest additions installed ??

---

### Post by alwayshere on 2010-01-18
try ?

sudo apt-get remove virtualbox

---

### Post by alwayshere on 2010-01-18
try ?

sudo apt-get remove virtualbox-ose-source

---

### Post by Goveynetcom on 2010-01-18
> **alwayshere said:**
> try ?

sudo apt-get remove virtualbox-ose-source

I'd  did that and it removed something... Then I removed the folder left by virtualbox ose, .VirtualBox, and it didn't do anything. I'm gonna reboot then check it again. I browsed around the folders that normal Vbox wants to install into, but there are still files there.

---

### Post by Goveynetcom on 2010-01-18
OI, I have been so very stupid. It said conflict with package virtualbox-ose... I removed it with the Ubuntu Software Center Uninstaller. But I didn't realize exactly what it was saying. It was saying that package remained, so i just did a quick sudo apt-get remove virtualbox-ose , and done. Thanks for your help. I love when I find out that a problem is just something simple like that and not a huge critical error.

---

### Post by warfacegod on 2010-01-18
If Vbox is still refusing to install then:

```
sudo apt-get purge virtualnameofsoftwarebox
```

After that hunt down its .vboxname folder in your home folder and really any other folders it used and dump them. Make sure they aren't needed by Linux. If in doubt... well you know.

---

### Post by alwayshere on 2010-01-18
In Synaptic, search for "virtualbox-ose" and check if it's installed and if it is right-click and completely remove it

---

### Post by woodmaster on 2010-01-18
in synaptic, find the packages for virtualbox and right click.
select mark for complete removal.
click apply button

---

