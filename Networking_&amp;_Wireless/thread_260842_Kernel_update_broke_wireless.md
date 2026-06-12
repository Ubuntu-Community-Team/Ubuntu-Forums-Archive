---
title: "Kernel update broke wireless"
date: 2006-09-19
forum: Networking &amp; Wireless
---

### Post by Qwarsdog on 2006-09-19
I looked around for this one and didn't see it posted. My network card is completely gone from networking connection properties. Its not being detected at all. In device manager I see it listed 

Ar5212 802.11abg Nic

When I do a lshw 
under network it states 

*-Network UNCLAIMED
Description: Ethernet controller
Etc.. all the stats. How do I get it redetected as an interface?

This is Atheros so the driver was auto installed. Did not need to use an NDIS wrapper. Any help would be appreciated.

Thanks

---

### Post by OmniDistortion on 2006-09-19
Bump. Same exact problem here. Having to use my uncle's PC to even get on the net... Worked excellent before the update.

---

### Post by spd106 on 2006-09-19
Check that you have the correct linux-restricted-modules installed. Ie 2.6.15-27 and that you are booting the new kernel. Maybe check that the driver modules are being loaded **lsmod | grep ath** should produce something like this:
```
:~$ lsmod | grep ath
ath_pci                96288  0
ath_rate_sample        15360  1 ath_pci
wlan                  202460  5 wlan_wep,wlan_scan_sta,ath_pci,ath_rate_sample
ath_hal               191568  3 ath_pci,ath_rate_sample

```

I'll also mention that since I build my own madwifi-ng driver, I had to recompile it after updating the kernel headers.

---

### Post by Qwarsdog on 2006-09-19
> **spd106 said:**
> Check that you have the correct linux-restricted-modules installed. Ie 2.6.15-27 and that you are booting the new kernel. Maybe check that the driver modules are being loaded **lsmod | grep ath** should produce something like this:
```
:~$ lsmod | grep ath
ath_pci                96288  0
ath_rate_sample        15360  1 ath_pci
wlan                  202460  5 wlan_wep,wlan_scan_sta,ath_pci,ath_rate_sample
ath_hal               191568  3 ath_pci,ath_rate_sample

```

I'll also mention that since I build my own madwifi-ng driver, I had to recompile it after updating the kernel headers.


Ahhh hAAAAAAAAAAAAA! :D It was the Linux - restricted drivers! I deselected them because I thought a credit card window would pop up [-X  LOL! Thanks dude that fixed it!

---

### Post by Matt0001 on 2006-09-19
I had the same problem with the new kernel, and this worked for me as well. Is there a reason the restricted module was not updated automatically with the new kernel? I'm not complaining, I love every chance to learn something new, but I am curious.

---

### Post by chris_aldworth on 2006-09-20
> Check that you have the correct linux-restricted-modules installed. Ie 2.6.15-27 and that you are booting the new kernel

I have the same problem, as Im quite new to linux/ubuntu, can someone explain how to check and unrestrict modules and do this?

I would really appreciate this,

Cheers ;)

---

### Post by Qwarsdog on 2006-09-20
What I did was use synaptic package manager and do a search for Linux-restricted. Then when you get a group of them select all the ones for your platform (386,pentium) is Intel. 686 I think is amd?

---

### Post by spd106 on 2006-09-21
[QUOTE=Matt0001]Is there a reason the restricted module was not updated automatically with the new kernel? I'm not complaining, I love every chance to learn something new, but I am curious.[/QUOTE]

There are several psuedo (or meta) packages that exist purely to depend on other packages and keep them in sync. For example linux-image-386 depend on the latest kernel image. Thus ensuring that when you update you have the latest kernel, rather than a previous one. You can also see that the linux-386 package depends on linux-image-386 and linux-restricted-modules-386 for this reason.

The problem comes when some people don't want the restricted modules such as when you want to install the latest graphics or network card drivers.

Sometimes these meta packages should be installed but aren't, or they are removed by another package that clashes. Most of the time it isn't a problem since they don't actually do anything.

[QUOTE=Qwarsdog]Then when you get a group of them select all the ones for your platform (386,pentium) is Intel. 686 I think is amd?[/QUOTE]

Most PC cpus are compatible with 386, PowerPC (Mac) and recently Sparc (Sun) have their own repos. 686 is all Intel and Intel compatible (ie AMD) since Pentium Pro. K7 is AMD specific and SMP are for multiple processors/cores. As far as I know there isn't much benefit to choosing a kernel other than 386, since all packages are compiled for 386 compatibility. Though obviously it is better to have SMP on a multi-processor system.

---

### Post by cosmolee on 2007-02-28
I had a similar problem, except that I was upgrading from 2.6.15-27-686 to 2.6.15-28-686.  Fortunately, I noticed the problem right after upgrading the kernel, so I was able to figure out the problem immediately.  I just use the old kernel.  

However, other folks may not be so lucky.  If one is doing a new installation, they may be frustrated to find that "linux doesn't work for them", because they can't get wifi to work, even though it should.

Thinkpad T22, Dlink DWL-G630 wifi card.

HTH.

---

