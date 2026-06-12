---
title: "External 2.5&quot;  Hard Drive Caddy."
date: 2009-09-01
forum: New to Ubuntu
---

### Post by colintivy on 2009-09-01
I have not had any response to a very much earlier post about trying to use a 20GB 2.5" drive in a USB caddy. This drive has Win98SE and all sorts of guff from my laptop which is redundant. I do not have a working Win machine but have checked the drive on someonelse's Win machine and it works OK there. My ubuntu setup will not recognise the drive at all. I want to reformat it and use it for Linux backup purposes. Is this because of its present file structure and must I reformat it from a Win machine before it is recognised by my machine??? Where do I go from here ??

cointivy :confused:

---

### Post by gordintoronto on 2009-09-01
> **colintivy said:**
> I have not had any response to a very much earlier post about trying to use a 20GB 2.5" drive in a USB caddy. This drive has Win98SE and all sorts of guff from my laptop which is redundant. I do not have a working Win machine but have checked the drive on someonelse's Win machine and it works OK there. My ubuntu setup will not recognise the drive at all. I want to reformat it and use it for Linux backup purposes. Is this because of its present file structure and must I reformat it from a Win machine before it is recognised by my machine??? Where do I go from here ??

cointivy :confused:

The current format is not blocking recognition.

When it is plugged in, what does 
   lsusb
reveal?

---

### Post by LewRockwell on 2009-09-01
we've experienced previous permission issues with mounting media utilizing Ubuntu

we most often use Puppy Linux when we want to manipulate/copy/move/edit existing data

.

---

### Post by egalvan on 2009-09-01
> **colintivy said:**
> ...trying to **[B]use a 20GB 2.5" drive in a USB caddy**[/B].
 This drive has Win98SE and all sorts of guff from my laptop which is redundant.

I do this all the time with old drives...
Ubuntu has not failed to detect drives.
Of course, neither has Puppy 4.x or PartedMagic...
Have you tried accessing the drive via a disk partitioner,
such as gparted?

>  I do not have a working Win machine but have checked the drive on someonelse's Win machine and it works OK there.
** My ubuntu setup will not recognise the drive at all.** 

Does this mean that there is NO response from the computer?
Does the external drive enclosure have an indicator light?
Does it light up when plugged in?
Can you hear or feel the drive spin up when plugged in?

It may be the hardware on the laptop, or
the cable may be defective, or
the port may not have the current needed to power the drive, or
the port may not be working at all.


> 
I want to reformat it and use it for Linux backup purposes.
 Is this because of its present file structure and must I reformat it from a Win machine before it is recognised by my machine???
 Where do I go from here ??
cointivy :confused:

As others have said, the current files system is of no concern to *nix.
It can be a totally blank drive, and if the hardware is working, *nix will "see" it.

---

### Post by colintivy on 2009-09-12
Hi  gordintoronto!
Thanks for reply. Just got back to keyboard. (Liked Toronto when last visited)

lsusb below:-

colin@colin-laptop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 04b4:6830 Cypress Semiconductor Corp. USB-2.0 IDE Adapter
Bus 001 Device 005: ID 03f0:2702 Hewlett-Packard Photosmart A 626
Bus 001 Device 004: ID 07ab:fc03 Freecom Technologies USB2-IDE IDE bridge CDROM W
Bus 001 Device 003: ID 03f0:0904 Hewlett-Packard DeskJet 845c
Bus 001 Device 002: ID 04cc:1521 Philips Semiconductors USB 2.0 Hub
Bus 001 Device 001: ID 0000:0000  
colin@colin-laptop:~$ 

Light on Akasa Integral flashes steadly. Cannot hear drive spinning but may have stopped after intial start-up. 

Hope that this helps.

colintivy :)

---

### Post by colintivy on 2009-09-12
Hi! egalvan,

Some of your queries are covered in my previous post. The drive is powered by an external hub and the other USB devices all work from it. It lights up as I have said. I cannot fault the cable, I have used it with other devices OK. Everything else seems to have been sucessfully detected.  All very strange. My plan is to dump all the laptop HD contents on the external drive to allow updating to next LTS with security. I plan to put the Home folder in its own partition as well.

colintivy :confused:

---

### Post by izziere on 2009-09-12
try locating the device in the /dev/ directory.  To do this use

```
dmesg
```

and note tha last system message.  Then plus in the drive and run dmesg again.  It should give you indications of what has gone on and should give you the three letter device address.  You can manually mount this (eg mount /dev/[3 letter drive address] /media/usbdrive (make sure you have already done sudo mkdir /media/usbdrive.

This might work, if it is just not mounting automatically.

---

### Post by colintivy on 2009-09-13
Hi izziere!

Thanks for that.. the two dmesg's are here (in part)

dmesg..no drive attached:-
[ 2165.267768] floppy0: unexpected interrupt 
[ 2165.267862] floppy0: sensei repl[0]=80 
[ 2170.479303] floppy0: unexpected interrupt 
[ 2170.479399] floppy0: sensei repl[0]=80 
[ 2172.388988] floppy0: unexpected interrupt 
[ 2172.389070] floppy0: sensei repl[0]=80 
[ 2176.967318] floppy0: unexpected interrupt 
[ 2176.967411] floppy0: sensei repl[0]=80 
[ 2177.570014] floppy0: unexpected interrupt 
[ 2177.570100] floppy0: sensei repl[0]=80 
[ 2178.775403] floppy0: unexpected interrupt 
[ 2178.775496] floppy0: sensei repl[0]=80 
[ 2183.202051] floppy0: unexpected interrupt 
[ 2183.202135] floppy0: sensei repl[0]=80 
[ 2184.306017] floppy0: unexpected interrupt 
[ 2184.306109] floppy0: sensei repl[0]=80 
[ 2185.511406] floppy0: unexpected interrupt 
[ 2185.511492] floppy0: sensei repl[0]=80 
[ 2186.114105] floppy0: unexpected interrupt 
[ 2186.114198] floppy0: sensei repl[0]=80 
[ 2235.099310] floppy0: unexpected interrupt 
[ 2235.099396] floppy0: sensei repl[0]=80 
[ 2493.594961] usb 1-1.4: USB disconnect, address 3
colin@colin-laptop:~$ 

dmesg..drive attached:-
[ 2184.306109] floppy0: sensei repl[0]=80 
[ 2185.511406] floppy0: unexpected interrupt 
[ 2185.511492] floppy0: sensei repl[0]=80 
[ 2186.114105] floppy0: unexpected interrupt 
[ 2186.114198] floppy0: sensei repl[0]=80 
[ 2235.099310] floppy0: unexpected interrupt 
[ 2235.099396] floppy0: sensei repl[0]=80 
[ 2493.594961] usb 1-1.4: USB disconnect, address 3
[ 2701.618338] usb 1-1.4: new full speed USB device using ohci_hcd and address 8
[ 2701.729585] usb 1-1.4: configuration #1 chosen from 1 choice
[ 2701.793081] scsi6 : SCSI emulation for USB Mass Storage devices
[ 2701.796791] usb-storage: device found at 8
[ 2701.796807] usb-storage: waiting for device to settle before scanning
[ 2706.793259] usb-storage: device scan complete
[ 2712.363814] usb 1-1.4: reset full speed USB device using ohci_hcd and address 8
colin@colin-laptop:~$ 

That says a lot! presumably hcd is the device address. The fill dmesg seemed to show the new device much further up the list. I will check this now I know a bit more about it.


Thanks again,

colintivy :)  :)

Tried sudo mkdir/media/usbdrive but got no command found..must have boobed somewhere.

---

### Post by louieb on 2009-09-13
> **colintivy said:**
> Tried sudo mkdir/media/usbdrive but got no command found..must have boobed somewhere.

typo? need a space between mkdir and /media/usbdrive.

---

### Post by izziere on 2009-09-13
Seems to be an occasional problem relating to USB drivers.  it is certainly not loading the device properly according to the dmesg output, but then you knew that from post 1, so apologies for pointing out the obvious!

Have a look at [this thread]("http://www.neowin.net/forum/lofiversion/index.php/t556286.html") for possible solutions.

Good luck

---

