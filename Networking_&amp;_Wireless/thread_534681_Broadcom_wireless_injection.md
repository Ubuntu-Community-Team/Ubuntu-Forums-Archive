---
title: "Broadcom wireless injection"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by mencargo on 2007-08-25
I have Ubuntu 7.04, kernel 2.6.20-16
Aircrack-ng suite 0.9.1 ([_installed from tar_]("http://www.aircrack-ng.org/doku.php?id=install_aircrack"))
Linksys WPC54G ( Broadcom 4306 ) 
Acer Aspire 3000 ZL5 wireless card ( Broadcom 4318 )
Already with bcm43xx driver working after [_bcm43xx-fwcutter stuff_]("http://ubuntuforums.org/showthread.php?t=185174")
airodump-ng works "fine", but my cards seem to "reset" from time to time, and stop monitoring...
I don't know if this has something to do with ubuntu's network manager... ?
And it seems that 4318 it's _[not fully supported,]("http://bcm43xx.berlios.de/?go=devices")_ "transmission power issues"... and it does "reset" more often than 4306, I call it reset because the red led in the laptop's button for wireless blinks, and airodump stops receiving data.
But I think the 4306 can stay up long enough to catch the ivs needed to wep crack, anyway, ivstools can merge ivs, although aircrack-ng -z (ptw) doesn't work with ivs, but well... wireless "works"...
I followed the [_injection patch_]("http://www.aircrack-ng.org/doku.php?id=broadcom")
Recompiled my kernel, rebooted, and tryed to play with wireless, but this is what I got:> [QUOTE]
[QUOTE]Couldn't find the location of inject_nofcs. Is your bcm34xx driver patched?
NB: this attack is more effective when targeting
a connected wireless client (-c <client's mac>).
16:40:59  Sending DeAuth to broadcast -- BSSID: [00:18:3F:4D:B5:D1]

Then weird characters flows... and on, and on...
And there's no activity at the airodump-ng
inject_nofcs not found? But I followed the howto, step by step...
Am I missing something?

---

### Post by MrSootentai on 2007-09-02
Bumpity Bump 
I need help with this too.

---

### Post by WattoDaToydarian on 2007-09-04
mencargo, first of all, I found that the network manager automatically changes the wifi nic to managed mode. You have to right click on it and uncheck "Enable Wireless". Then your wifi interface will stay on monitor mode.

As far as the the patched driver goes... I did the whole thing today and it all worked fine for me.
If you tell me where I can post a copy of my patched driver I can upload it so people don't have to compile the kernel.
Remember to reboot after you overwrite your old one with it.
It goes in "/lib/modules/2.6.20-16-generic/kernel/drivers/net/wireless/bcm43xx/" in case you didn't know.:KS

---

### Post by ajmorris on 2007-09-15
> **WattoDaToydarian said:**
> mencargo, first of all, I found that the network manager automatically changes the wifi nic to managed mode. You have to right click on it and uncheck "Enable Wireless". Then your wifi interface will stay on monitor mode.

As far as the the patched driver goes... I did the whole thing today and it all worked fine for me.
If you tell me where I can post a copy of my patched driver I can upload it so people don't have to compile the kernel.
Remember to reboot after you overwrite your old one with it.
It goes in "/lib/modules/2.6.20-16-generic/kernel/drivers/net/wireless/bcm43xx/" in case you didn't know.:KS

can u post it here for us please ?
just add it as an attachment

---

### Post by tturrisi on 2007-09-15
You must use a patched driver to get injection working, no ifs ands or buts.
[http://www.aircrack-ng.org/doku.php?id=broadcom](http://www.aircrack-ng.org/doku.php?id=broadcom)
[http://tinyshell.be/aircrackng/forum/index.php?topic=2045.0](http://tinyshell.be/aircrackng/forum/index.php?topic=2045.0)

---

### Post by WattoDaToydarian on 2007-09-15
tturrisi, I know...
ajmorris, ubuntuforums doesn't let me post .ko files and it's 1.7MB which is over the 1MB limit so taring wont work.

So, I uploaded it to megaupload.
[bcm43xx-patched-ubuntu-2.6.20]("http://www.megaupload.com/?d=HMWB321P")  < Click this link do download it.

---

### Post by android6011 on 2007-09-15
i assume the patched driver isnt compatible with 2.6.22-11-generic that you uploaded, but do you know if I do everything manually if it will work?

---

### Post by WattoDaToydarian on 2007-09-15
> **android6011 said:**
> i assume the patched driver isn't compatible with 2.6.22-11-generic that you uploaded, but do you know if I do everything manually if it will work?
I have not tried it on a 2.6.22 kernel, I think it would depend on the changes that were made between the two so it may or may not work.
You can always recompile the kernel with the patch as described in the how-to's.

---

### Post by vxbinaca on 2007-10-25
Where is the source in Gutsy? I've been looking all over for it (yes I installed the source package) and cannot for the life of me find it.

---

### Post by abs on 2007-10-26
hello al,

I am tring to patch my driver, I use 7.10 AMD x64, i tied to download the patched driver but the download does not work, can some one please send it to me or email it over.

I am not sure about recompiling the kernal as i might screw things up knowing my inpatiance.

thanks all

---

### Post by jvillegasl on 2007-10-31
I have installed ubuntu 7.10 with the 2.6.22.14 Kernel and I also get the message:

Couldn't find the location of inject_nofcs. Is your bcm34xx driver patched?
Saving ARP requests in replay_arp-1031-150243.cap
You should also start airodump-ng to capture replies.
Read 598 packets (got 0 ARP requests), sent 0 packets...(0 pps)

I'm really starting to learn linux and I've tried to compile the driver but I can't, could somebody give me the instructions of how I can accomplish this or could you send me the file compiled for me???

Regards.

---

