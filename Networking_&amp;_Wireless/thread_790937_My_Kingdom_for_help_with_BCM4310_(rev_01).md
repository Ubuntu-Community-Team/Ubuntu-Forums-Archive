---
title: "My Kingdom for help with BCM4310 (rev 01)"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by ASULutzy on 2008-05-11
I picked up a nice little laptop today, HP Pavillion dv6000. I had very high hopes as just about everything worked out of the box, but for the life of me I cannot seem to get wireless to work at all.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

I followed that thread (step 2e) and others with the same card say they have gotten it to work just fine with ndiswrapper, but I can't seem to get the card to ever show up. Please, if anyone has this card and has gotten it to work, then I'd be forever grateful for a hand here.

I have a decent amount of Linux experience, but absolutely no real wireless experience, so if it's necessary for me to post the output of a command that might be helpful, please let me know!

```
02:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
``` is from lspci

Please help!

---

### Post by dmizer on 2008-05-11
in addition to blacklisting bcm43xx as shown in step 1, you'll also need to blasklist the ssb module:

```
sudo modprobe -r ssb
echo 'blacklist ssb' | sudo tee -a /etc/modprobe.d/blacklist
modprobe ndiswrapper
```

if this is not successful, post the output of the following commands:
```
lshw -C network
```
and
```
ndiswrapper -l
```

---

### Post by SurferGTO on 2008-05-16
i had the exact same problem. 
[URL="http://ubuntuforums.org/showthread.php?t=794816&page=2"]
http://ubuntuforums.org/showthread.php?t=794816&page=2[/URL]

follow what i did in that thread up to whatever point your at now. hope it helps.

specifically a link for a "hack" is all i had to do and it was up and working. also, i suggest using wicd for the network manager. the packaged network-manager app and wifi-radar wouldnt connect for me. also. dont forget to actually turn on the wireless button.

---

### Post by levien on 2009-01-29
I can confirm this. I just got wireless working on a HP Pavilion laptop (DV6000 series, a DV6700 as I recall) running Hardy Heron 8.04. There are basically two ways you can get it to work, either with ndiswrapper or using the updated wl kernel driver (introduced with an update in September 2008 ).

It turns out that while the wireless network controller in this laptop was listed by lspci and lshw as being a Broadcom Corporation BCM4310 USB Controller (rev 01), this is incorrect. The device is actually a BCM4312 PCI wireless controller, but it's PCI ID is not recognised correctly. This should be fixed after you update Hardy to the latest version.

So with Hardy and Intrepid, the Broadcom wireless controller should actually work out-of-the-box using the wl module, as long as you make sure you've installed the latest kernel updates and the restricted-modules packages.

Unfortunaly the wl driver seems to work improperly for some people / in some cases. If so, you can simply install ndiswrapper and the Windows driver, as described elsewhere. (There is no need to build it from source, Hardy has an up-to-date version.) If you've followed instructions for the BCM4310, you either need to reinstall a newer version of the driver, or alternatively you can add the card's identifier to the list recognised by ndiswrapper (the "hack" described above). Otherwise ndiswrapper will load the driver, but report no hardware present. Simply look up the card's ID using "lspci -pp" (14E4:4315 for the card in this laptop), and create a symbolic link in /etc/ndiswrapper/bcmwl5/ like this:

sudo ln -s /etc/ndiswrapper/bcmwl5/14E4:4311.5.conf /etc/ndiswrapper/bcmwl5/14E4:4315.5.conf

If you prefer using a new driver, try this one: [ftp://ftp.hp.com/pub/softpaq/sp37501-38000/sp37950.exe](ftp://ftp.hp.com/pub/softpaq/sp37501-38000/sp37950.exe)
Note that I haven't tried this myself.

Finally, don't forget to unload the spp kernel module because apparently it interferes with ndiswrapper. This is not needed if you're using the default wl driver.

Good luck!
Levien

---

