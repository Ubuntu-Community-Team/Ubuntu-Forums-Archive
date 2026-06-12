---
title: "hanging during suspend or hibernate after installing madwifi"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by stanley drew on 2008-06-21
So I recently installed Ubuntu 8.04 and eventually got my Atheros AR5007 wireless card to work using madwifi and wicd thanks to the threads in this forum. But my HP Pavilion dv6700 laptop hangs with a bunch of text on the screen during suspend or hibernate and I always have to do a hard reboot. The last line on the screen is [end trace] with some numbers after it but the line just before it mentions something about wlan (I think this is about right):

EIP: [...] ieee8u211_virtfs_vdelach +0x8e/0xf0 [wlan]

I'm not sure whether suspend and hibernate worked before i installed madwifi but is this a common problem? I'd like to get suspend and hibernate working when I open and close the screen too but for now just having them work at all would be nice. Does this have anything to do with the madwifi driver or wicd?

Thanks for helping out a first-time poster.

---

### Post by kevmitch on 2008-06-21
It sounds like your kernel is freaking out on suspend. I've found that this level of instability is almost always caused by third party modules or patches that are added into the kernel. In other words madwifi is a likely candidate as are any binary graphics modules like nvidia or fglrx (ati).

The dump you're seeing to the screen is likely only of use to kernel developers and if my suspicions of a third party culprit are correct, not even said kernel developers will want to look at it as it is not output from an "untainted" kernel.

If you have the "acpi-support" package installed, it is likely removing the ath_pci (madwifi) kernel module before suspend, but you might want to try removing it (and friends) yourself before suspend by running the command
```

sudo madwifi-unload

```
If that doesn't work, then it may still be the result of residual upset from madwifi. You can rule this out once and for all by booting the system without ever loading the madwifi module (i.e., remove ath_pci from /etc/modules or even add "blacklist ath_pci" to /etc/modprobe.d/blacklist) at all and then try to suspend. 

You can see a list of all kernel modules loaded by running the command "lsmod". Look for things like "ath_pci" "wlan" "wlan_ccmp", "wlan_acl","wlan_scan_sta","ath_rate_sample" all of which should be removed by the madwifi-unload command.

Let me know what happens. I've got a few contingency plans.

---

### Post by alightly on 2008-06-21
Hi

I get the same issue, will see about "sudo madwifi-unload" and try hibernating then.

Thanks

---

### Post by stanley drew on 2008-06-21
Thanks kevmitch. I tried to unload madwifi but got a segmentation fault and had to reboot. I then blacklisted ath_pci and magically suspend and hibernate worked! (Although the return from hibernate was a little rough.) So is there anything I can do to manually unload madwifi? And if I do can I easily reload it after returning from suspend?

Thanks again for your help.

---

### Post by kevmitch on 2008-06-21
Ok, well it sounds like the problem is actually with unloading the module, rather than suspending with it loaded. Since, as I said, it is probably getting unloaded automatically on suspend, you could try preventing this from happening by adding ath_pci to MODULES_WHITELIST in /etc/default/acpi-support. If that does't work, you could try using ndiswrapper: [http://www.linuxquestions.org/questions/linux-wireless-networking-41/wireless-not-working-atheros-ar5007ug-with-hardy-8.04-and-medion-laptop-647942/]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/wireless-not-working-atheros-ar5007ug-with-hardy-8.04-and-medion-laptop-647942/"). In any case, it would probably be worth while to file a detailed bug report with madwifi.

---

### Post by stanley drew on 2008-06-21
If I don't unload it on suspension will it affect anything?

I will go ahead and file the bug report with madwifi. I just can't believe this hasn't come up more...

---

### Post by kevmitch on 2008-06-21
The only reason it unloads on suspend, is that suspending with wireless drivers is often the source of problems. In your case, however the problem arises from removing the module, so we need to amend the suspend procedure a bit. 

The tricky thing about suspend is that it's difficult for a distribution to implement a procedure that works on every platform. If you take a look in /etc/acpi/suspend.d /etc/acpi/resume.d you'll begin to see that this is the case. As such, you can almost always benefit from tweaking things for your system and that's why your /etc/defaults/acpi-support file has so many options.

As for madwifi, I've found that it's stability is up and down. If you're using the subversion snapshot, you have to expect some bumps in the road. Just keep an eye out for future snapshots (they usually update several times daily) that might fix the problem. If you want stability, I would recommend using ndiswrapper.

---

