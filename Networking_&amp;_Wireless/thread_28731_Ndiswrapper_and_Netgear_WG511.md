---
title: "Ndiswrapper and Netgear WG511"
date: 2005-04-21
forum: Networking &amp; Wireless
---

### Post by alastair lewis on 2005-04-21
I have searched the fora for a solution without success. Here is the problem.

I am trying to set up a Netgear WG511 (v3 made in china) on a Gateway Solo9300.
I have installed ndiswrapper-source and -tools.
I have used ndiswrapper -i to install the correct driver (as per ndiswrapper wiki)

ndiswrapper -l  returns
   2802w (the driver)   hardware present,fuzzy

modprobe ndiswrapper returns no error

iwconfig returns
   l0          no wireless extensions
   eth0     no wireless extensions
   sit 0      no wireless extensions

dmseg returns

Losing some ticks... checking if CPU frequency changed.
Losing too many ticks!
TSC cannot be used as a timesource.
Possible reasons for this are:
  You're running with Speedstep,
  You don't have DMA enabled for your hard disk (see hdparm),
  Incorrect TSC synchronization on an SMP system (see dmesg).
Falling back to a sane timesource now.

Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
PCI: Found IRQ 9 for device 0000:00:0c.0
PCI: Sharing IRQ 9 with 0000:00:0b.0
PCI: Sharing IRQ 9 with 0000:00:0c.1
PCI: Sharing IRQ 9 with 0000:01:00.0
Yenta: CardBus bridge found at 0000:00:0c.0 [107b:9300]
Yenta: ISA IRQ mask 0x0c18, PCI irq 9
Socket status: 30000020
PCI: Found IRQ 9 for device 0000:00:0c.1
PCI: Sharing IRQ 9 with 0000:00:0b.0
PCI: Sharing IRQ 9 with 0000:00:0c.0
PCI: Sharing IRQ 9 with 0000:01:00.0
Yenta: CardBus bridge found at 0000:00:0c.1 [107b:9300]
Yenta: ISA IRQ mask 0x0c18, PCI irq 9
Socket status: 30000006
Loaded prism54 driver, version 1.2
PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
eth0: islpci_open()
eth0: resetting device...
eth0: uploading firmware...
eth0: firmware uploaded done, now triggering reset...
ieee1394: Initialized config rom entry `ip1394'
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
PCI: Found IRQ 5 for device 0000:00:0c.2
PCI: Sharing IRQ 5 with 0000:00:08.0
ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[5]  MMIO=[f4004000-f40047ff]  Max Packet=[2048]
eth0: device soft reset timed out
eth0: timeout waiting for mgmt response 1000, triggering device
eth0: timeout waiting for mgmt response


eth0: mgmt tx queue is still full
ndiswrapper version 0.10 loaded (preempt=yes,smp=no)
ndiswrapper: driver 2802w.sys (SMC,04/29/2004, 3.0.11.1) added
eth0: mgmt tx queue is still full
eth0: mgmt tx queue is still full

Can anyone tell my what is going on,
I have the latest versions of wireless tools installed.

---

### Post by dataw0lf on 2005-04-21
I believe I've seen this before; from what I recall, it's an actual firmware problem.  Try replacing the firmware.agent with the one you can obtain from Prism.

---

### Post by alastair lewis on 2005-04-22
[QUOTE=dataw0lf]I believe I've seen this before; from what I recall, it's an actual firmware problem.  Try replacing the firmware.agent with the one you can obtain from Prism.[/QUOTE]


Thanks, can you point me to a HOWTO, I havn't the first idea about how to approach this.

---

### Post by alastair lewis on 2005-05-25
[QUOTE=dataw0lf]I believe I've seen this before; from what I recall, it's an actual firmware problem.  Try replacing the firmware.agent with the one you can obtain from Prism.[/QUOTE]
 Ok. I have made some progress.
I upgraded to Hoary and reinstalled ndiswrapper and the .inf files. Now ndiswrapper -l shows that card and driver are installed (no recurrance of the fuzzy problem).

modprobe ndiswrapper does not return any errors
dmesg shows card and drivers are present and correct

BUT.. no lights come on on the card.

I have tried reinserting the card, deactivating eth0 (the 10/100 card) and rebooting with neither card in and then inserting the wifi card. No lights with any of these and iwconfig gives card NOT READY in the first line.

I have not or disabled anything (eg. prism54) because I don't know how, or installed the kernal headers.

Loving linux (Ubuntu in particular) and would like to crack this.

Have I missed a key step.

---

### Post by elsewhere on 2005-05-25
You do need to blacklist the prism54 driver, otherwise hotplug loads it and prevents ndiswrapper from taking control of the card.
All you need to do is add a line with "prism54" to /etc/hotplug/blacklist.

You can then either reboot, or probably do an "rmmod prism54" and then a "modprobe ndiswrapper".

Hope this helps...

Cheers,
KV

---

### Post by alastair lewis on 2005-06-01
Excellent. Blacklisted prism54 and moved ACX.
Now I can get some flashing lights.
Next move to configure the card properly and either switch to WEP or try to get WPA active.

Cheers elsewhere.

---

### Post by elsewhere on 2005-06-12
Glad to hear that did the trick.  Have you been able to get it working ?  wpa_supplicant works great for handling wpa.

Cheers,
KV

---

### Post by alastair lewis on 2005-06-13
I tried WPA_supplicant, but couldn't get the configuration sorted out. I switched back to WEP which worked right away.  Now happliy surfing my Wifi internet connection and printing to the HP 6800 network printer. 
Hewlet-Packard's linux support is excellent.

---

