---
title: "AR9485 WiFi and Bluetooth not starting on boot, Ubuntu 16.04"
date: 2016-07-23
forum: Networking &amp; Wireless
---

### Post by Matt_Nona on 2016-07-23
I have replaced my wireless card in my laptop last night as the previous one stopped working.
The new card is Qualcomm Atheros AR9485, I found it much better than my previous wifi card as it has better signal, doesn't drop connection and bluetooth is working, the only thing is neither the wireless or bluetooth work on startup so I have to suspend my laptop before I even get to log in which is a bit annoying, after it wakes up everything is working perfectly.

I ran the wireless-info script twice, before I suspended the laptop and after and compared the results with "sdiff". I noticed that ```
bnep,ath3k,btbcm,btrtl,btusb,rfcomm,btintel
``` were being loaded only after I suspended the laptop so I added them manually to load on startup which they do now but that hasn't fixed my problem.

Here's the full output of my wireless-info script of both before (left column) and after (right column) suspending
[ATTACH]270281[/ATTACH]

Also in dmesg it looks like the wireless and bluetooth card doesn't go on until after the wakeup
```

[  694.053141] PM: Finishing wakeup.
[  694.053145] Restarting tasks ... done.
[  694.131556] usb 1-1.3: new full-speed USB device number 4 using ehci-pci
[  694.225849] usb 1-1.3: New USB device found, idVendor=0930, idProduct=0219
[  694.225859] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  694.225864] usb 1-1.3: Product: Bluetooth USB Host Controller
[  694.225868] usb 1-1.3: Manufacturer: Atheros Communications
[  694.225872] usb 1-1.3: SerialNumber: Alaska Day 2006

```

Is there any way to force this device to be enabled on startup?

---

### Post by jeremy31 on 2016-07-23
I would go into BIOS and reset to defaults, if that doesn't work remove your additions to /etc/modules and file a [bug report](https://ubuntuforums.org/showthread.php?t=1011078) against package linux

I don't know why your wifi is hard blocked at boot and the bluetooth device isn't discovered.  Also remove whatever package that installed rtbth as that was for a Ralink bluetooth device and yours is Atheros.

---

### Post by Matt_Nona on 2016-07-23
Thanks for your reply, I have already reset BIOS to defaults last night but that didn't help.
I am not sure why it's hard blocked, there's no switch on my HP Pavilion g6.
Is blacklisting rtbth enough? It's from my old wireless card.

---

### Post by jeremy31 on 2016-07-23
Do you have secure boot enabled in BIOS?  I found a [patch](http://git.kernel.org/cgit/linux/kernel/git/next/linux-next.git/commit/drivers/platform/x86/hp-wmi.c?id=fc8a601e1175ae351f662506030f9939cb7fdbfe) that may fix the wifi hard block and a bug report could get that patch put into an Ubuntu kernel at some point

---

### Post by Matt_Nona on 2016-07-23
No, secure boot is disabled and legacy mode enabled otherwise I get a message about not having any operating system installed.
Ok this is embarrassing but do you mind telling me how to use that patch or at least point me to some instructions :confused:

---

### Post by jeremy31 on 2016-07-23
I compiled a module and will attach it to the post but we will backup the original module
```
sudo cp /lib/modules/4.4.0-31-generic/kernel/drivers/platform/x86/hp-wmi.ko /lib/modules/4.4.0-31-generic/kernel/drivers/platform/x86/hp-wmi.ko.bak
```

Chances are it will be downloaded into the Downloads folder, right click and choose extract here, then you should be able to ```
cd Downloads
sudo cp hp-wmi.ko /lib/modules/4.4.0-31-generic/kernel/drivers/platform/x86/
```

Reboot and see if it fixes the issue

If you want to see the source code after patching [https://github.com/jeremyb31/hp-wmi/blob/master/hp-wmi.c](https://github.com/jeremyb31/hp-wmi/blob/master/hp-wmi.c)

---

### Post by Matt_Nona on 2016-07-24
Thanks very much for your effort and instructions, unfortunately it didn't fix the issue, rfkill still shows that my wireless card is hard blocked. 
After suspending and waking up the laptop wifi works but bluetooth is gone.

I have edited my /etc/rc.local file and added ```
sudo rtcwake -u -s 3 -m mem
``` as my workaround but I don't know if this is good for my laptop or the system itself? It just suspends the laptop for 3 seconds and wakes it up automatically with working wifi and bluetooth. Not a perfect solution but will have to do until I find a better way of fixing it.

---

