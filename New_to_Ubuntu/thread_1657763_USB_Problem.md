---
title: "USB Problem"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by trekguy on 2011-01-01
Dual boot Ubuntu 10.10 and XP.  Started when I couldn't print.  Didn't seem to be connecting to the printer.  Then, I noticed that it wouldn't see my flash drives either.  I tried them in XP, and they work just fine.  When this would happen in XP, I would just uninstall the USB controller, then restart, and Windows would reinstall.  How do I fix it in Ubuntu?

---

### Post by blazemore on 2011-01-01
What machine are you running Ubuntu on?

If it's a laptop or desktop, can you post the model number?
If you built it yourself, can you post the model of the motherboard?

---

### Post by trekguy on 2011-01-01
Home build... May 08... Gigabyte MA69GM-S2H... AMD Athlon 64

---

### Post by trekguy on 2011-01-02
Bump

---

### Post by Mindswap1 on 2011-01-02
Hey really sorry my english skills are not top notch so just to clearify you want your USb flash drives, and printers to appear in Ubuntu right? 

Do me a favor and open up terminal and type in the following command. 

```
lsusb
```And then copy the results here.

Make sure you have your printer and flash drives inserted before you type this into the terminal.

---

### Post by trekguy on 2011-01-02
lsusb does nothing, just sits there.  When I close Terminal, it says Terminal is still running... lsusb, I assume... but how long should it take?

[IMG][[IMG]http://img412.imageshack.us/img412/7436/lsusb.th.png[/IMG]](http://img412.imageshack.us/i/lsusb.png/)[/IMG]

[IMG][[IMG]http://img148.imageshack.us/img148/7194/closeterminal.th.png[/IMG]](http://img148.imageshack.us/i/closeterminal.png/)[/IMG]

---

### Post by HunkirDowne on 2011-01-02
> **trekguy said:**
> lsusb does nothing, just sits there.  When I close Terminal, it says Terminal is still running... lsusb, I assume... but how long should it take?



lsusb should take anywhere from 15-20 microseconds :^) IOW: It's quick.

Try this:
```
sudo lshw -C bus

```

---

### Post by trekguy on 2011-01-02
dean@dean-desktop:~$ sudo lshw -C bus
[sudo] password for dean: 
  *-core                  
       description: Motherboard
       product: GA-MA69GM-S2H
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
  *-usb:0
       description: USB Controller
       product: SB600 USB (OHCI0)
       vendor: ATI Technologies Inc
       physical id: 13
       bus info: pci@0000:00:13.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: ohci bus_master
       configuration: driver=ohci_hcd latency=32
       resources: irq:16 memory:fe02e000-fe02efff
  *-usb:1
       description: USB Controller
       product: SB600 USB (OHCI1)
       vendor: ATI Technologies Inc
       physical id: 13.1
       bus info: pci@0000:00:13.1
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: ohci bus_master
       configuration: driver=ohci_hcd latency=32
       resources: irq:17 memory:fe02d000-fe02dfff
  *-usb:2
       description: USB Controller
       product: SB600 USB (OHCI2)
       vendor: ATI Technologies Inc
       physical id: 13.2
       bus info: pci@0000:00:13.2
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: ohci bus_master
       configuration: driver=ohci_hcd latency=32
       resources: irq:18 memory:fe02c000-fe02cfff
  *-usb:3
       description: USB Controller
       product: SB600 USB (OHCI3)
       vendor: ATI Technologies Inc
       physical id: 13.3
       bus info: pci@0000:00:13.3
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: ohci bus_master
       configuration: driver=ohci_hcd latency=32
       resources: irq:17 memory:fe02b000-fe02bfff
  *-usb:4
       description: USB Controller
       product: SB600 USB (OHCI4)
       vendor: ATI Technologies Inc
       physical id: 13.4
       bus info: pci@0000:00:13.4
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: ohci bus_master
       configuration: driver=ohci_hcd latency=32
       resources: irq:18 memory:fe02a000-fe02afff
  *-usb:5
       description: USB Controller
       product: SB600 USB Controller (EHCI)
       vendor: ATI Technologies Inc
       physical id: 13.5
       bus info: pci@0000:00:13.5
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm debug ehci bus_master cap_list
       configuration: driver=ehci_hcd latency=32
       resources: irq:19 memory:fe029000-fe0290ff
  *-serial
       description: SMBus
       product: SBx00 SMBus Controller
       vendor: ATI Technologies Inc
       physical id: 14
       bus info: pci@0000:00:14.0
       version: 14
       width: 32 bits
       clock: 66MHz
       capabilities: ht cap_list
       configuration: driver=piix4_smbus latency=0
       resources: irq:0 ioport:b00(size=16)
  *-firewire
       description: FireWire (IEEE 1394)
       product: TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
       vendor: Texas Instruments
       physical id: e
       bus info: pci@0000:02:0e.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm ohci bus_master cap_list
       configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
       resources: irq:22 memory:fddff000-fddff7ff memory:fddf8000-fddfbfff
dean@dean-desktop:~$

---

### Post by Mindswap1 on 2011-01-02
Thats very strange open up terminal once more, and plug in the following command. 

```
sudo apt-get install usbutils
```

And then once more try 
```

lsusb 
```

And if you get results post back. 

Also note of advice. Whenever you are pasting results that are rather long highlight them, and then click the number symbol icon. This should put the CODE in the beginning, and end of your info. The number symbol can be found when you are making a reply/ new post.

---

### Post by trekguy on 2011-01-02
Said usbutils was already the newest version.  lsusb... same result.

---

### Post by trekguy on 2011-01-02
Ah... I see.  Thanks!

```
dean@dean-desktop:~$ sudo lshw -C bus
[sudo] password for dean: 
  *-core                  
       description: Motherboard
       product: GA-MA69GM-S2H
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
  *-usb:0
       description: USB Controller
       product: SB600 USB (OHCI0)
       vendor: ATI Technologies Inc
       physical id: 13
       bus info: pci@0000:00:13.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: ohci bus_master
       configuration: driver=ohci_hcd latency=32
       resources: irq:16 memory:fe02e000-fe02efff
  *-usb:1
       description: USB Controller
       product: SB600 USB (OHCI1)
       vendor: ATI Technologies Inc
       physical id: 13.1
       bus info: pci@0000:00:13.1
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: ohci bus_master
       configuration: driver=ohci_hcd latency=32
       resources: irq:17 memory:fe02d000-fe02dfff
  *-usb:2
       description: USB Controller
       product: SB600 USB (OHCI2)
       vendor: ATI Technologies Inc
       physical id: 13.2
       bus info: pci@0000:00:13.2
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: ohci bus_master
       configuration: driver=ohci_hcd latency=32
       resources: irq:18 memory:fe02c000-fe02cfff
  *-usb:3
       description: USB Controller
       product: SB600 USB (OHCI3)
       vendor: ATI Technologies Inc
       physical id: 13.3
       bus info: pci@0000:00:13.3
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: ohci bus_master
       configuration: driver=ohci_hcd latency=32
       resources: irq:17 memory:fe02b000-fe02bfff
  *-usb:4
       description: USB Controller
       product: SB600 USB (OHCI4)
       vendor: ATI Technologies Inc
       physical id: 13.4
       bus info: pci@0000:00:13.4
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: ohci bus_master
       configuration: driver=ohci_hcd latency=32
       resources: irq:18 memory:fe02a000-fe02afff
  *-usb:5
       description: USB Controller
       product: SB600 USB Controller (EHCI)
       vendor: ATI Technologies Inc
       physical id: 13.5
       bus info: pci@0000:00:13.5
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm debug ehci bus_master cap_list
       configuration: driver=ehci_hcd latency=32
       resources: irq:19 memory:fe029000-fe0290ff
  *-serial
       description: SMBus
       product: SBx00 SMBus Controller
       vendor: ATI Technologies Inc
       physical id: 14
       bus info: pci@0000:00:14.0
       version: 14
       width: 32 bits
       clock: 66MHz
       capabilities: ht cap_list
       configuration: driver=piix4_smbus latency=0
       resources: irq:0 ioport:b00(size=16)
  *-firewire
       description: FireWire (IEEE 1394)
       product: TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
       vendor: Texas Instruments
       physical id: e
       bus info: pci@0000:02:0e.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm ohci bus_master cap_list
       configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
       resources: irq:22 memory:fddff000-fddff7ff memory:fddf8000-fddfbfff
dean@dean-desktop:~$ 
```

---

### Post by Mindswap1 on 2011-01-02
I really wish I was better at computers so I could help you out. I remember I had a similar problem however mine was fixed when I just plugged in the flash drive to the usb ports located on the back of the desktop instead of the front ones. Try that. I'll keep looking around for a solution tho. I know it sucks when things like this happen so I'll try my best.

Edit- 

Btw what is the model of your printer?

---

### Post by trekguy on 2011-01-02
Yep, tried the ports in the back... same deal.

Thanks!  I will keep looking as well.

---

### Post by Mindswap1 on 2011-01-02
Do you know the model your printer is?

---

### Post by HunkirDowne on 2011-01-02
> **trekguy said:**
> 

  *-usb:0
       description: USB Controller
       product: SB600 USB (OHCI0)
       vendor: ATI Technologies Inc
       physical id: 13
       bus info: pci@0000:00:13.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: ohci bus_master
       configuration: driver=ohci_hcd latency=32
       resources: irq:16 memory:fe02e000-fe02efff
  *-usb:1
       description: USB Controller


OK.  Your usb hardware is recognized.  This much is good.

USB support is delivered by the kernel as a module.  I'm running wubi (kde) 10.04 at the moment and entering CODE I get the output that follows.
```
 lsmod | grep usb 
```
> usb_storage            49961  1 
usbhid                 41116  0 
hid                    83472  1 usbhid


Also, I checked the dependencies of the modules:
(Caveat: be careful with 'modprobe' because you can turn stuff off without meaning to if you are sloppy on the command line.  But then it's also easy to look at your history and figure out where you messed up and can then undo it.)

```
 sudo modprobe -show-depends usb_storage 
```
>  insmod /lib/modules/2.6.32-27-generic/kernel/drivers/usb/storage/usb-storage.ko


```
 sudo modprobe -show-depends usbhid 
```
>  insmod /lib/modules/2.6.32-27-generic/kernel/drivers/hid/hid.ko 
insmod /lib/modules/2.6.32-27-generic/kernel/drivers/hid/usbhid/usbhid.ko 


```
 sudo modprobe -show-depends hid 
```
>  insmod /lib/modules/2.6.32-27-generic/kernel/drivers/hid/hid.ko


You should get similar results.  If you do not there are two things to try next: (1:quick&dirty) load the modules using modprobe or (2:slow&clean) reinstall the kernel.  I'd really recommend the second so that's the one that I will post here.

```

sudo aptitude reinstall linux-headers-$(uname -r) linux-image-$(uname -r) -P

```

Do this and reboot and see if you get any better results.

(Note, if you didn't know or haven't yet figured it out, the "$(uname -r)" grabs *your* kernel version.  The $(<command>) will insert the stdout of the command you place within the parentheses into your commands.)

HTH!

---

### Post by trekguy on 2011-01-02
HP Deskjet F380 All-in-One... has worked great up til now.

---

### Post by trekguy on 2011-01-02
Thanks!  Will try when I get back from bowling.

---

### Post by HunkirDowne on 2011-01-02
> **trekguy said:**
> HP Deskjet F380 All-in-One... has worked great up til now.

Yeah, and correct me if I'm wrong but it doesn't sound like a printer problem but a usb problem.  I'm basing this on: USB flash drives do not work in Ubuntu either and in Windows the printer works (and therefore USB -- including flash drives?).

This would make this the Linux equivalent of a Windows driver problem, which is, in this case at least, a linux module problem.

If reinstalling the kernel images doesn't get it, the next step might be to dive into the init files to see what was up but it's been so long since I had to do that I'd probably have to remember more than I forgot.  :-/

Even before that I would try booting off of a live CD and see if you got any better results that way.  At least then you would have something to compare it to.

---

### Post by Mindswap1 on 2011-01-02
Try the following. Plug in your USB flash drive then go to System>Administrator>Disk Utility. If the flash drive is listed then click on it and format it. There should be option to format volume. After clicking that choose NTFS format, where it ask for the type. Name it whatever you want to, and then click format. And then try plugging it into the different usb ports.

---

### Post by trekguy on 2011-01-02
Ran all codes... didn't get anything like your quotes.  Reinstalled kernel.. no joy.

Agree, not a printer problem, but a USB problem.

The Disk Utility does not see the flash drive, so there's nothing to format.

The USB ports do have power, as I can charge my phone... fyi.

](*,)

---

### Post by HunkirDowne on 2011-01-04
trekguy, have you tried running the liveCD?  If that works, I'm wondering if a kernel upgrade might be in play.

---

### Post by trekguy on 2011-01-07
Ubuntu magic today.  There was an update... should have paid more attention to what was in there.  I don't know if that fixed it, or what?  I can print today... flash drives work.  Weird.  Nice, but weird.  A couple of days ago, I did add some USB stuff in Synaptic... so today when I stuck the flash drive in... it wouldn't let me take it out!  It showed two devices in "computer"... one a regular USB drive, and one looked like a fixed-drive icon named usb0.  Found a thread here somewhere with the answer... removed all "usb" stuff that wasn't default... and now it works perfectly.

Marking it Solved (magically).

:D

---

