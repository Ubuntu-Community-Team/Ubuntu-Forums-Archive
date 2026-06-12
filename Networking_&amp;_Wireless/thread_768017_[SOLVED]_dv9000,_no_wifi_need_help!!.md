---
title: "[SOLVED] dv9000, no wifi need help!!"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by jlandaw on 2008-04-26
I have an hpdv9000 with Broadcom wifi

I have been trying to get my wifi to work ever since i updated... and no luck.

I have done about 13 different procedures and not luck at all.

Everyone says you should be able at least see some sort of option for your wifi in the restricted drivers menu, but only my video card is there.

Pleas help me.

---

### Post by doorknob60 on 2008-04-26
Can you post your output of this:
```
lspci | grep Broadcom
```

If it says, something like BCM94311, this could be helpful: [http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)

That's the ONLY thing that could get wireless working correctly on my dv9008nr.

---

### Post by nivesh on 2008-04-26
i have the exactly same problem....only my video card shows in hardware drivers and wifi dont work

---

### Post by jlandaw on 2008-04-26
"lspci | grep Broadcom"  output

03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

---

### Post by brew1brew on 2008-04-26
I have the  BCM94311MCG wlan mini-PCI (rev 02), you can use ndiswarper, the instructions are [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff"), I had to follow the instructions to install from source, I also used the "Hardy bug fix" to bring my wireless back up after upgrading to Hardy.

Les

---

### Post by doorknob60 on 2008-04-26
> **jlandaw said:**
> "lspci | grep Broadcom"  output

03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

Ahh, yeah, that's the same as my dv9008nr, this should almost definitely work [http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/) (it works in Hardy too, and unless they didn't fix the ndiswrapper bug that was in Alpha 6, then you won't have to do anything extra either)

EDIT: Looks like that evil bug that wasted so much of time time still isn't fixed yet -.- Luckily, the bug is easy to fix once you know that that's the problem. Run this command: ```
echo -e '\n#hardy ssb bug-fix\nrmmod b43\nrmmod b44\nrmmod ssb\nrmmod ndiswrapper\nmodprobe ndiswrapper\nmodprobe ssb' | sudo tee -a /etc/init.d/rc.local
``` (From Ubuntu Wiki: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-cbc75fcb762da2057fa8dbe904358e4b611353c0](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-cbc75fcb762da2057fa8dbe904358e4b611353c0) )

---

### Post by jlandaw on 2008-04-27
Thank you ervery one!!!!

Thank you Doorknob!!

I am  now able to use my wifi!!!

One Note: I did everything doorknob said, but I also reinstalled fwcutter using aptitud NOT synapti, but i have no idea if that had any berring on the out come...[http://ubuntuforums.org/showthread.php?t=769333](http://ubuntuforums.org/showthread.php?t=769333)

Thanks again too all.

PS, I did make a thread that outline(for beginners) how to install the ndiswrapper and drivers for this very computer on gusty, and will modify the tread to include the bug fix for hardy
[COLOR="Red"]
[http://ubuntuforums.org/showthread.php?t=769990](http://ubuntuforums.org/showthread.php?t=769990)[/COLOR]

---

