---
title: "Issue with WiFi adapter."
date: 2020-05-05
forum: Networking &amp; Wireless
---

### Post by moxiblu on 2020-05-05
Hello all, I'm extremely new to Linux so I watched a few youtube videos and looked up some guides; I made myself a bootable USB to test out PopOS, which didn't go well, so I swapped to Ubuntu. However even after swapping to ubuntu I'm still having the same issue, my WiFi adapter is a rtl8821ce which is apparently not officially supported and therefore I don't have access to wifi at all. I tried doing this [https://aur.archlinux.org/packages/rtl8821ce-dkms-git/](https://aur.archlinux.org/packages/rtl8821ce-dkms-git/) because apparently it also works for Ubuntu, but to no avail. I'm not sure if it just doesn't work due to an updated kernel? Or maybe because I'm trying to do these installations via USB (I'm extremely uncomfortable with the idea of making the swap before I know I can get everything working properly)? From what I know, I'm just on Ubuntu 20.04 AMD64; any help would be appreciated, especially if it leads to my being able to make the swap. Also, I'm on a laptop so I'm not sure how easily I would be able to physically swap out the WiFi adapter as I have almost no experience tinkering with laptops.

There was also a video on Youtube about being able to use the additional drivers program in Ubuntu to download the drivers, however when I do that it tells me there are no additional drivers even though in the video it obviously shows exactly what I need. *EDIT* If you tell me that you need any additional information, please if you would include instructions or a link to instructions so that I may provide you with the information that you need; Please pardon my ignorance.

---

### Post by jeremy31 on 2020-05-05
In terminal check ```
mokutil --sb-state
```
If Secure Boot is enabled it will prevent the driver from loading
There is also a package in the Ubuntu repos for that wifi, if you have ethernet connection, install by
```
sudo apt update && sudo apt install rtl8821ce-dkms
```

---

### Post by moxiblu on 2020-05-05
> **jeremy31 said:**
> In terminal check ```
mokutil --sb-state
```
If Secure Boot is enabled it will prevent the driver from loading
There is also a package in the Ubuntu repos for that wifi, if you have ethernet connection, install by
```
sudo apt update && sudo apt install rtl8821ce-dkms
```

Okay, so for mokutil --sb-state I got "EFI Variables are not supported on this system

And as for the sudo apt update && sudo apt install rtl8821ce-dkms I got some output and E: unable to locate package rtl8821ce-dkms.

Thank you for helping me by the way, I appreciate it.

---

### Post by jeremy31 on 2020-05-05
try this ```
wget http://mirrors.kernel.org/ubuntu/pool/universe/r/rtl8821ce/rtl8821ce-dkms_5.5.2.1-0ubuntu3_all.deb
sudo dpkg -i rtl8821ce-dkms_5.5.2.1-0ubuntu3_all.deb
```

---

### Post by moxiblu on 2020-05-05
> **jeremy31 said:**
> try this ```
wget http://mirrors.kernel.org/ubuntu/pool/universe/r/rtl8821ce/rtl8821ce-dkms_5.5.2.1-0ubuntu3_all.deb
sudo dpkg -i rtl8821ce-dkms_5.5.2.1-0ubuntu3_all.deb
```

So, for this one the first command went off perfectly fine, the second one however I encountered this:

 dpkg: error processing package rtl8821ce-dkms (--install): Dependency problems - leaving unconfigured 
errors were encountered while processing: rtl8821ce-dkms

---

### Post by jeremy31 on 2020-05-05
Does this run ok ```
sudo apt install dkms
```

---

### Post by moxiblu on 2020-05-05
> **jeremy31 said:**
> Does this run ok ```
sudo apt install dkms
```

Yes, that command runs without issue.

---

### Post by jeremy31 on 2020-05-05
Try ```
sudo apt install rtl8821ce-dkms
```
Post any errors

---

### Post by moxiblu on 2020-05-05
> **jeremy31 said:**
> Try ```
sudo apt install rtl8821ce-dkms
```
Post any errors

rtl8821ce.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.4.0-7625-generic/updates/

depmod....

DKMS: install completed.

However I still don't see an option for wireless in the upper righthand corner? Would I need to restart; In WiFi settings it still says there's no adapter found.

---

### Post by xxteraxx on 2020-05-05
Yes you woudl need to restart I have the same wifi adapter

Or sometimes this command works [COLOR=#212529][FONT=Inconsolata]sudo systemctl restart networking[/FONT][/COLOR]

---

### Post by jeremy31 on 2020-05-05
> **moxiblu said:**
> rtl8821ce.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.4.0-7625-generic/updates/

depmod....

DKMS: install completed.

However I still don't see an option for wireless in the upper righthand corner? Would I need to restart; In WiFi settings it still says there's no adapter found.

You should reboot now so the driver can load

---

### Post by moxiblu on 2020-05-05
> **xxteraxx said:**
> Yes you woudl need to restart I have the same wifi adapter

Or sometimes this command works [COLOR=#212529][FONT=Inconsolata]sudo systemctl restart networking[/FONT][/COLOR]

And this works for the most updated kernel? Thank god, for a second there I was worried I would have to downgrade my kernel in order to get it to work. Well, in that case I guess it's time to install for real then. If it doesn't work then, I'll be back lol; thank you both very much for your help, it's greatly appreciated.

---

### Post by jeremy31 on 2020-05-05
I missed the part about using USB, this will work on an install but you could try ```
sudo modprobe rtl8821ce
``` or it might be ```
sudo modprobe 8821ce
```

---

### Post by moxiblu on 2020-05-06
> **jeremy31 said:**
> I missed the part about using USB, this will work on an install but you could try ```
sudo modprobe rtl8821ce
``` or it might be ```
sudo modprobe 8821ce
```

I just made the leap and decided to install considering the results of the last recommendation were positive and guess what.. It worked! Haha, thank you very much for your help, I was wracking my brain for a couple days before I relented and came to ask on here. Glad to finally be a part of the community; Thank you again, how can I change the post to solved by chance?

---

