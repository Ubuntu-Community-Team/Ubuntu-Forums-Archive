---
title: "[SOLVED] How to install 64 bits windows wireless drivers on Ubuntu"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by Tony Flury on 2009-01-04
Is there there a good way of install Windows wireless 64 Bit drivers on Ubuntu (specifically for the wg111v3 adapter)

clearly ndiswrapper wont work (it only does 64 bit) - and i have followed a how to on the specific driver i need - but it just generates errors : 

[http://ubuntuforums.org/showthread.php?t=848305](http://ubuntuforums.org/showthread.php?t=848305) (post #5)

I would really appreciate any help - this is bugging me now.

---

### Post by igknighted on 2009-01-04
Can you run the command 'lspci' and post the output first?  Almost every card has a linux-native driver that usually works better and more reliably than the windows driver running through ndiswrapper, so lets see which card you have and what the best approach might be.

---

### Post by Tony Flury on 2009-01-04
it is not a pci card - it is a usb card - so as i understand it - it wont show up under lspci

```

tony@laptop:~$ lsusb
Bus 002 Device 003: ID 093a:2510 Pixart Imaging, Inc. 
Bus 002 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 0846:4260 NetGear, Inc. 
Bus 001 Device 003: ID 0c45:62c0 Microdia 
Bus 001 Device 001: ID 0000:0000 

```

it is a netgear wg111v3 - the chipset is a rtl8187b (not entirely sure how to confirm that though)

---

### Post by igknighted on 2009-01-04
Maybe try 'sudo lshw -c network'

---

### Post by Tony Flury on 2009-01-04
```

tony@laptop:~$ sudo lshw -C network
tony@laptop:~$

```

---

### Post by anewguy on 2009-01-04
Try sudo lsusb.  This will at least list the devices on the USB busses.

Dave

---

### Post by Tony Flury on 2009-01-04
anewguy - see post #3 - reposted here 

```

tony@laptop:~$ lsusb
Bus 002 Device 003: ID 093a:2510 Pixart Imaging, Inc. 
Bus 002 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 0846:4260 NetGear, Inc. 
Bus 001 Device 003: ID 0c45:62c0 Microdia 
Bus 001 Device 001: ID 0000:0000

```

---

### Post by Tony Flury on 2009-01-05
I am guessing no-one has a clue about this ?

---

### Post by Guille Damke on 2009-01-05
Hi,
Can you try to get the 32 bit drivers for Windows and use ndiswraper to install them?
Probably this can help:[HTML]http://ubuntuforums.org/showthread.php?t=732827[/HTML]

Good luck.

---

### Post by Tony Flury on 2009-01-05
Will try that and report back - although I am fairly sure i tried it before

---

### Post by Tony Flury on 2009-01-05
I just tried that and it did fail : 

```

tony@laptop:~$ dmesg | grep ndiswrapper
[   35.101518] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   35.416332] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[   35.416339] ndiswrapper (load_sys_files:210): couldn't prepare driver 'wg111v3'
[   35.416778] ndiswrapper (load_wrap_driver:112): couldn't load driver wg111v3; check system log for messages from 'loadndisdriver'
[   35.418534] usbcore: registered new interface driver ndiswrapper

```

it seems from this that i need a 64 bit driver - and ndiswrapper does not handle 64 bit drivers from what i know.

---

### Post by anewguy on 2009-01-06
found a few posts on the net for this:

- for an older version of Ubuntu, but worth trying:
[http://ja.meswilson.com/blog/2007/03/11/wg311v3-64-bit-driver/]("http://ja.meswilson.com/blog/2007/03/11/wg311v3-64-bit-driver/")

dave :)

---

### Post by Tony Flury on 2009-01-06
anewguy : these are for wg311v3 card - which is different from the wg111v3 card I have - Thanks for trying though :-)

However you have inspired me ito do some more digging : Is there a 64 bit driver for the Realtek chip that the netgear dongle uses.

---

### Post by anewguy on 2009-01-06
hey, I also found these in reference to a 64 bit driver for the wg111v3:

[http://http://en.opensuse.org/SDB:WG111v3]("http://http://en.opensuse.org/SDB:WG111v3")

[http://files.aoaforums.com/I3048-wg111v3_1_0_0_setup.exe.html]("http://files.aoaforums.com/I3048-wg111v3_1_0_0_setup.exe.html") (doesn't specifically say 64 bit, but I'm guessing it's in there)


Don't know if those will help or not.

dave :)

---

