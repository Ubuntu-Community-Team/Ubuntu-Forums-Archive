---
title: "Ndiswrapper request for IRQ 0 Failed (acpi=off) HELP!"
date: 2008-02-03
forum: Networking &amp; Wireless
---

### Post by anabelle on 2008-02-03
HI, i just completed 15 hours fighting with Ndiswrapper and reinstalled the whole system twice.

I installed Ndiswrapper 1.5.2 correctly from source, no errors, i used my windows wireles drivers (.inf). And everything worked fine.

 My wireless card is a:

```
Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
```

acording to lspci.

Even though everything seems fine my wireless card refuses to work. I thought Ndiswrapper was bad installed, but then I figured out I had a much more ironic problem.

My laptop is a Compaq presario C706LA and due to i don't know what i have to boot my kernel with the following options:

> ro quiet splash acpi=off pnpbios=off noapic noacpi

Or else I wont get to the login screen (it stalls at boot)

When troubleshooting my wireless card I took a look at "dmesg" and saw this:

```
[   63.016229] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   63.087468] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   63.087649] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   63.093846] ndiswrapper (IoConnectInterrupt:569): request for irq 0 failed
[   63.093850] ndiswrapper: request for IRQ 0 failed
[   63.093966] ndiswrapper (mp_init:216): couldn't initialize device: C000009A
[   63.093972] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[   63.093985] ndiswrapper (mp_halt:259): device f0e94500 is not initialized - not halting
[   63.093992] ndiswrapper: device eth%d removed
[   63.094006] ndiswrapper: probe of 0000:03:00.0 failed with error -22

```

So I started to look around and found out that the ndiswrapper: request for IRQ 0 failed error was caused because acpi (whatever it is) is not active (acpi=off at boot options).

I tried to boot without the acpi=off switch and the wireless indicator turned blue :) but saddly enough my pc is to unstable without the acpi=off so i never get to the login screen. I once got to the terminal and doing "sudo iwlist scanning" brought up my wireless connection! so i know the driver is working, but i cant boot without acpi=off

What can i do to get around this?

---

### Post by Ayuthia on 2008-02-04
You might see if you can use the information from this post:
[http://www.ubuntu-es.org/index.php?q=node/77633](http://www.ubuntu-es.org/index.php?q=node/77633)

I tried to translate it using google's translator, but it did not help me too much.  It looks like the person is using a different boot option that is working, but you will not be able to get the splash screen to see the progress.  Here is a portion of what they said:
> sudo gedit /boot/grub/menu.lst y en las últimas lineas cambias quiet splash por nosplash vga=791 y guardas
From what I can tell, they are changing the boot to be nosplash vga=791.

I hope that helps.

---

### Post by anabelle on 2008-02-04
Thank you very much, but actually that was the first thread I saw, and the first boot option I tried, with no luck.


Any other idea?

---

### Post by rtrommer on 2008-03-14
You and I have been wrestling the same demon, and your comment regarding acpi=off worked for me, so thanks for sharing that ! I removed acpi=off parameter and the led went instantly blue but even then I had wlan issues to resolve. So far though I have no issues with instability. Running an HP DV9000 laptop, same dreadful broadcom card as you. I am completely new to Ubuntu and linux - total newbie - but I finally got my wireless working. I also had to mod my Linksys router to use WPA Personal(TKIP). I changed the router channel to match card config  - 2.462 GHz. See this: [http://johnbokma.com/mexit/2007/12/29/my-linksys-wrt54gl-ubuntu-wireless-settings.html](http://johnbokma.com/mexit/2007/12/29/my-linksys-wrt54gl-ubuntu-wireless-settings.html)

FWIW here are my parameters in /boot/grub/menu.lst:
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.22-14-genericroot=UUID=025e1ad6-032a-47d9-b387-11eb2020f081 ro quiet splash noapic nolapic pnpbios=off

I could not get restricted drivers to work and resorted to ndiswrapper. So far so good. With my lack of expertise not sure how much more I can help, but to share my settings. It's been quite an experience for me, and your post was the last piece of my puzzle, so thanks for that.

---

### Post by rustybronco on 2008-03-14
boot options...
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Option: irqpoll? and remove acpi=off?
some boot options to try.

---

