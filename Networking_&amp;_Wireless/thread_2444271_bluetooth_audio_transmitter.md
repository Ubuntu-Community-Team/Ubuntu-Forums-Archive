---
title: "bluetooth audio transmitter"
date: 2020-05-27
forum: Networking &amp; Wireless
---

### Post by rkonrad on 2020-05-27
I'm writing for a friend who wishes his hearing aid to connect with his ubuntu system.  He has just bought an Aluratek Audio Transmitter and can't get it to work.  I've plugged it into my Linux Mint system (latest kernel) and get the message "no bluetooth adapters found".   I can't seem to see it when I enter "lspci" but then it is an output device (like speakers) so maybe that's why..

My friend  is using Ubuntu 18.04.3. .Please let me know if you need any additional information.

thanks!

Richard

---

### Post by chili555 on 2020-05-27
The device plugs in to the headphone jack of your computer and then transmits the sound received at the headphone jack by bluetooth. It therefore will not appear in lspci or lsusb or elewhere as a bluetooth device. To your Mint computer and your friend's Ubuntu computer, it appears to be headphones. 

Other than guessing what's paired by observing the pairing LED on the Aluratek, there is no way to determine successful pairing.

In Settings > Sound, be certain that the output device is set to headphones.

Not all hearing aids, even if they have bluetooth connectivity, connect to any and all devices. Mine, for instance, connect to my iPad perfectly every time. They never, ever connect to my Ubuntu computer, nor my Chromebook.

[https://www.amazon.com/Aluratek-Bluetooth-Universal-Transmitter-ABT01F/dp/B013JK4U1C](https://www.amazon.com/Aluratek-Bluetooth-Universal-Transmitter-ABT01F/dp/B013JK4U1C)

> Tried it under Windows 7 and Ubuntu 16.04 on two separate Toshiba Satellite laptops that did not have Bluetooth running. I loaded the Bluetooth drivers. Nothing I did got the Aluratek Bluetooth recognized.


---

### Post by DuckHook on 2020-05-27
> **chili555 said:**
> …Not all hearing aids, even if they have bluetooth connectivity, connect to any and all devices. Mine, for instance, connect to my iPad perfectly every time. They never, ever connect to my Ubuntu computer, nor my Chromebook…
You too chili? <sigh> …well, sometimes, it's nice knowing that one is in good company as one ages.

Hearing aids almost entirely use the proprietary Apple MFi standard which computers and even Android phones don't use. Since it is proprietary, the only devices which have implemented the standard are Apple. Since devices without the appropriate circuitry/proprietary codecs cannot physically connect, there are no drivers that one can install. The usual workaround is to have a bridge device that receives the MFi signal and re-transmit to standard Bluetooth. Mine is this tiny little box that I can wear around my neck and costs more than its weight in gold. <Grumble>

The hearing aid [s]racket[/s] market is obscenely profitable, but things are getting better for us poor consumers. A number of earbud manufacturers are making initial inroads into the market by experimenting with upscale music buds that also double as hearing aids. I patiently await the day when I won't have to swap out my hearing aids for decent music buds.

---

### Post by chili555 on 2020-05-27
> You too chili? <sigh> …well, sometimes, it's nice knowing that one is in good company as one ages.
Yes. One can live in denial only so long and one can start every conversation with, "WHAT??" only so long.
> Hearing aids almost entirely use the proprietary Apple MFi standard which computers and even Android phones don't use. Since it is proprietary, the only devices which have implemented the standard are Apple. Since devices without the appropriate circuitry/proprietary codecs cannot physically connect, there are no drivers that one can install. Unless the manufacturer of the hearing aids in question can confirm that they *will* work with the Aluratek, then it almost certainly will not.

---

### Post by rkonrad on 2020-05-28
The result of "lsusb; lspci -nnk | grep -iA2 net; dmesg | egrep -i 'blue|firm'; rfkill list all; uname -a:  is

Bus 002 Device 002: ID 8087:8000 Intel Corp.
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 002: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:3098]
Kernel driver in use: r8169
Kernel modules: r8169
[    0.028370] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    0.042264] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
Linux bert-ThinkCentre-E73 4.15.0-101-generic #102-Ubuntu SMP Mon May 11 10:07:26 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

Thanks

---

### Post by chili555 on 2020-05-28
Just as we expected: > 
It therefore will not appear in lspci or lsusb or elewhere as a bluetooth device. To your Mint computer and your friend's Ubuntu computer, it appears to be headphones.

And further:

> Unless the manufacturer of the hearing aids in question can confirm that they will work with the Aluratek, then it almost certainly will not.Sorry.

---

### Post by rkonrad on 2020-05-29
Thanks to all who responded.  Your help was most appreciated!  It seems the best course is to contact Oticon.

Cheers  Richard

---

### Post by VMC on 2020-05-29
I want a hearing aid for watching TV only. The "around your neck" kind I've checked out, they don't work for me. As far as the "What, who, etc", I just smile and nod my head. 
Sorry for the off-topic. I came here because of the bluetooth question. I can only get my bluetooth speaker to work once on Linux, then never again.

---

