---
title: "wifi%d: request_irq failed"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by lukemack on 2008-06-22
Hi,

I have an atheros based Netgear wireless card (see attached for lspci output). I have just installed Ubuntu on a brand new system (8.04 Hardy) and neither the onboard wifi (which I have now disabled in the bios) nor the netgear card work out of the box. Hardy has installed and enabled the Atheros HAL and support for Atheros cards which I can see in the Hardware drivers menu. This happened after i plugged the netgear card in (after giving up on the onboard wifi). However. iwconfig does not show a wireless interface so something is wrong. In dmesg I have:

[   60.519497] wifi%d: request_irq failed

Which I think must be related. After searching around, I tried the suggestion of adding acpi=force to my kernel line in menu.list but this made no difference.


lsmod shows ath_hal and ath_pci are loaded.

Does anyone have any idea how I can get my card working?

thanks,

lukemack.

dmesg and lspci output attached

---

### Post by chili555 on 2008-06-22
How are the IRQs set up in your BIOS? In my collection of Ebay cast-offs, each seems to work best set to 'Auto Select.'

---

### Post by lukemack on 2008-06-23
Thanks for your reply.

I've tried it with plug and play os set to Yes and No in the BIOS - same result. Will have to have a proper look at the IRQ settings.

Do you think that is the problem rather than a madwifi issue? I think thats what Hardy uses for the Atheros cards.

---

### Post by chili555 on 2008-06-23
> Do you think that is the problem rather than a madwifi issue?I definitely do. This whole sequence worries me:> [   60.519472] ACPI: Unable to derive IRQ for device 0000:05:00.0
[   60.519497] wifi%d: request_irq failed
[   60.519506] ACPI: Unable to derive IRQ for device 0000:05:00.0Uh, oh! Time for another of Chili's rants. I have seen the weirdest problems here. I have seen improper settings in the router, router hooked up wrong (!!!), trying to get wireless working with wired already working and connected (contrary to Network Manager's intention), incorrect encryption (WEP, WPA or Klingon) and almost universally, the user's *very first step* is to install a different driver! People! If you have a healthy *iwconfig* and you can scan for networks, the chances are 95% that a new driver is NOT your solution!

End rant.

---

### Post by lukemack on 2008-06-23
fair enough, but i don't have a healthy iwconfig as it is not displaying any wireless interfaces. 

anyway, i cant see anything useful in the BIOS. Maybe you can? (see attached).

---

### Post by chili555 on 2008-06-23
My rant was not aimed at you, sorry. These emational cleansings happen when you answer 2,000 posts!

May I please see:```
cat /proc/interrupts
```Your BIOS seems to offer only Plug-n-Play on or off, both of which you have tried.

---

### Post by lukemack on 2008-06-23
interrupts.txt attached. thanks!

---

### Post by lukemack on 2008-06-23
Update: I have now tried all the boot options here:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

and also moved the card to a different pci slot. 

None of this got rid of the error :-(

I have also recompiled madwifi from source - no help.

sudo lshw -C network shows :

```
*-network UNCLAIMED
       description: Ethernet controller
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:05:01.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=168 maxlatency=255 mingnt=255

```

This makes me think that this IS more of a driver issue than a hardware one.

---

### Post by chili555 on 2008-06-24
> *-network UNCLAIMEDThis usually means the driver is not in place. Did you *sudo modprobe ath_pci* or whatever the driver is for the card? After doing so, is there any change in *sudo lshw -C network *?

---

### Post by lukemack on 2008-06-25
Yes - I tried that and there was no change.

---

### Post by coubi64 on 2008-07-02
No evolutive on the opened ticket here.... :(

[https://bugs.launchpad.net/ubuntu/+bug/221310]("https://bugs.launchpad.net/ubuntu/+bug/221310")

---

### Post by lukemack on 2008-07-02
I got the on-board wlan chip working in the end so gave up on this card.

---

### Post by tgyorgyi on 2008-07-11
I have the same issue: "network unclaimed" when running the lshw... command. Only, I had no problems with the wifi from the Live CD or right after installing. But when I run Ubuntu for the first time after the kernel update following install, wifi gone. :-( Meanwhile, the Atheros HAL driver and the support for Atheros are shown as up and running under closed drivers.

---

