---
title: "Cannot &quot;see&quot; ethernet card in System&gt;Networking"
date: 2007-09-13
forum: Networking &amp; Wireless
---

### Post by _sunshine_ on 2007-09-13
Very very newbie for Ubuntu here.  I really really need help.

I just purchased a desktop computer and installed Ubuntu.  Everything is working fine except for one.  I cannot connect to the internet.  

When I go to Systems>Networking, I can only see the Dial-up Modem, nothing else.  The LAN socket (is that how you call it?) at the back of the computer (is that LED?) blinks when I connect the network cable, but it still wouldn't show in the Systems>Networking window and the LAN icon on top of my desktop says "not connected" even though this is already set to enable.  

I am running on Intel Core Duo Processor and ASUS P5S-MX SE motherboard.

Please help.  This is something I will never figure out on my own.  :confused: :(

Thank you.

---

### Post by Zorael on 2007-09-13
Could you paste the output of the following, please?
```
lshw -C network
```

You need to open a terminal/console and type it there.

---

### Post by progymax on 2007-09-13
I've had the same problem with mine. I checked out the Linux drivers at Asus; but I'm not into kernel patching. There seem to be issues with SATA drives as well.

So I thought I'd wait, using THE alternate inferior OS, until the drivers for the motherboard were incorporated into Ubuntu. 

Hopefully if enough posts are generated we can get it happening sooner.

Cheers

---

### Post by _sunshine_ on 2007-09-13
> **Zorael said:**
> Could you paste the output of the following, please?
```
lshw -C network
```

You need to open a terminal/console and type it there.

description:  Ethernet controller
product:  191 Gigabit Ethernet Adapter
vendor:  Silicon Integrated Systems (Sis)
Physical id: 4
Bus info: pci@00:04.0
Version:  02
Width: 32 bits
clock:  33 MHz
capabilities: cap_list
configuration: latency=0
resources:  iomemory: feafcc00-feafcc7f  ioport:dc00-dc7f   irq:19


That was what it said.  Thanks for replying.

---

### Post by _logic on 2007-10-25
same with me... i even started disabling the LAN card from the BIOS and put an external card in one of its PCI slots like what this guy did,

[http://ubuntuforums.org/showthread.php?t=556999](http://ubuntuforums.org/showthread.php?t=556999)

until read this thread:

[http://ubuntuforums.org/showthread.php?t=482284](http://ubuntuforums.org/showthread.php?t=482284)

now all is smoooothly working.... hope yours will too... :)

---

### Post by _sunshine_ on 2007-10-25
Actually, I didn't really spend much time to see how it can be resolved - what I did was the easy way out.  Buy a USB Wireless Adapter (Netgear WG111) - worked out of the box! 

:)

---

### Post by _logic on 2007-10-25
yup, way to go there...

---

### Post by _sunshine_ on 2007-10-25
hi _logic,

Actually, I'm quite curious how you're able to make the LAN work - I did open and read the link you have attached but see, I tried doing it but i'm having problems with it.  For one thing, it doesn't allow me to access the source code.  It's asking me if i'm root - what do I do after that?  Sorry I'm new on ubuntu  and i'm not even a programmer, so I may seem really stupid about this.

_sunshine_

---

### Post by _logic on 2007-10-26
hmmmm... ok lets see....
1. you have to install the kernel source first, my 'uname -r' yields 2.6.22 so I downloaded the linux-source-2.6.22 package from another computer and copied it to my computer.
2. do a ' lspci -nn | grep ISA' to determine what ISA address your computer is using. Mine says --- 00:02.0 0601: 1039:**0968** (rev 59) ----- take note of the numbers in bold
3. go to /usr/src/linux-source-xxxx ---- xxxx is your kernel version from 'uname -r'
4. as root or using sudo, open drivers/net/sis190.c and find the phrase:

sa_bridge = pci_get_device(PCI_VENDOR_ID_SI, 0x0965, NULL);
        if (!isa_bridge) {
                net_probe(tp, KERN_INFO "%s: Can not find ISA bridge.\n",
                          pci_name(pdev));
                return -EIO;
        }

and edit/change the value 0x0965 with the noted address mentioned in 2 (in bold). Save and exit.
5. do a 'sudo make oldconfig' and 'sudo make drivers/net/sis190.ko'
6. if there are no errors, you should have a sis190.ko file in your drivers/net directory. Copy that to /lib/modules/`your kernel version`/kernel/drivers/net/ overwriting the any existing one.
7. remove the existing module running in your system by 'sudo rmmod sis190.ko'
8. probe the new sis module by 'sudo modprobe sis190'
9. restart networking by 'sudo /etc/init.d/networking restart'
10. have a cold beer or an ice cream perhaps

good luck

---

