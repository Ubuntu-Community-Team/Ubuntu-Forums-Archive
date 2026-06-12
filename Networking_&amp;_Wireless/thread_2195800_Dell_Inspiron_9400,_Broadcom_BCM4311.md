---
title: "Dell Inspiron 9400, Broadcom BCM4311"
date: 2013-12-26
forum: Networking &amp; Wireless
---

### Post by dwilliams2 on 2013-12-26
Hi there,

I have this old Dell laptop that I am trying to install Kubuntu 12.04 32 bit onto.  I can't get it to install as it errs out with a screen load of information, that doesn't mean a great deal to me :( Here is the beginning of the message, any help to get Kubuntu installed would be much appreciated.

kernel bug at include/net/cfg80211.h:2209!
invalid opcode: 0000 [#1] SMP
CPU 0
Modules linked in: wl(P+) cfg80211 lib80211 d_crypt snd_hda_codec_idt_intel snd_hda_codec snd_hwdep ....... (and quite a few more)

Maybe this laptop is too old and not a good fit for Kubuntu?

Again, any help would be much appreciated.

Thanks.

---

### Post by dwilliams2 on 2013-12-26
So, by selecting not to install the 3rd party software it looks like the installation is moving forward, but from what I have been reading maybe I won't be able to get the wireless working, which I really need to do since where the laptop will be located it will need to use the wireless connection.

Hopefully other people have come across this issue and can recommend a way to fix it.  Will keep you guys posted once I have Kubuntu installed.

---

### Post by mörgæs on 2013-12-26
Hi, welcome to the fora.
Are you installing using wired internet access?

---

### Post by dwilliams2 on 2013-12-26
Yes, I did the install using a hard wired connection to the laptop, but now that I have Kubuntu installed I need to get the wireless card working.  From some google searches that I did it looks like the Broadcom STA wireless card is a common issue, but I am hoping some kind person on here can help me to get this up and running so that I can move away from Windows Vista!  I am a newbie to Kubuntu so please bear with me.  From reading some of the google threads it seems the following command provides more information on the wireless card that I have in my laptop:

 dwilliams@Laptop2:~$ lspci -nnk|grep -iEA3 "(wireless|network|wlan)"
 0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
 Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
 Kernel driver in use: b43-pci-bridge
 Kernel modules: wl, ssb

---

### Post by mörgæs on 2013-12-27
Yes, the [COLOR=#000000]BCM4311 is well-known. There should be lots of threads here providing a solution.

Did you also apply all updates using the wired connection? [/COLOR]

---

### Post by dwilliams2 on 2013-12-27
Yes, as soon as I did the install I did an update.  But still no luck with this :( I found one thread ([http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers-bcm43xx](http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers-bcm43xx)) and was trying to follow that but if I try and uninstall bcmwl-kernel-source I am told that the package manage (or something like that) is already being used by another process.  I've rebooted my laptop and still I get the same message when I try and uninstall using Muon.  I can't even install anything new since I am told there is another process! Really frustrating :(

---

### Post by chili555 on 2013-12-27
> **dwilliams2 said:**
> Yes, as soon as I did the install I did an update.  But still no luck with this :( I found one thread ([http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers-bcm43xx](http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers-bcm43xx)) and was trying to follow that but if I try and uninstall bcmwl-kernel-source I am told that the package manage (or something like that) is already being used by another process.  I've rebooted my laptop and still I get the same message when I try and uninstall using Muon.  I can't even install anything new since I am told there is another process! Really frustrating :(What is the exact message? Usually, a message appears if Update Manager or Synaptic or Software Center is hanging open.

Please see here: [http://askubuntu.com/questions/395920/the-old-wireless-problem/](http://askubuntu.com/questions/395920/the-old-wireless-problem/)> The Broadcom STA proprietary driver offered by the Additional Drivers tool is *wrong* for your Broadcom 4311 device.

---

### Post by dwilliams2 on 2013-12-27
Ok, so I tried the following from the command line:

*sudo apt-get remove --purge bcmwl-kernel-source*

and go the following message: **dkpg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct this problem**.
The last time I ran 'sudo dpkg --configure -a' my laptop crashed on me :(

If I try and remove the bcmwl-kernel-source from the package manger I get the following message:
**Unable to obtain lock.  Another application seems to be using the package system at this time. You must close all other package managers before you will be able to install or remove packages.**

The only application I have open is the Muon package manager!

I am at a complete loss now as I don't know how to get past this issue so that I can remove the bcmwl-kernel-source package.

---

### Post by chili555 on 2013-12-27
>  Another application seems to be using the package system at this time. You must close all other package managers before you will be able to install or remove packages.> The only application I have open is the Muon package manager!
Then close it and reboot. Now open a terminal *ONLY* and do:```
sudo dpkg --configure -a
```And if successful, then:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree

```

---

### Post by dwilliams2 on 2013-12-27
I have tried that...but will try again and report back.

---

### Post by dwilliams2 on 2013-12-27
Ok, so when I rebooted my laptop, only opened a terminal window and ran the following command:

sudo dpkg --configure -a

the laptop crashes with a message similar to the one at the very start of this thread.  The message starts:

kernel bug at include/net/cfg80211.h:2209!

At this point there is nothing else I can do but to power off the laptop and then I am back to square 1!

Any other suggestions or am I back to doing a reinstall?

---

### Post by chili555 on 2013-12-27
There are probably a number of things we could try; however, you could reinstall in 20 minutes; that's what I'd do. Do not allow Additional Drivers to install a wireless driver. Install without networking. After it's done, hook up the ethernet and do:```
sudo apt-get install linux-firmware-nonfree
```Detach the ethernet and do:```
sudo modprobe -r b43 && sudo modprobe b43
```Your wireless should spring to life.

---

