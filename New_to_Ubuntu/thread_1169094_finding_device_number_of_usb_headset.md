---
title: "finding device number of usb headset"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by Falc7 on 2009-05-24
Hi
I am trying to find out what the device number my usb headset it, i was told to put 

[precat /proc/asound/cards[/pre] 

into terminal, but it dosen't work, can someone help me?

---

### Post by Didius Falco on 2009-05-24
Hi,

Try ```
lsusb
``` with the headset plugged in.

Regards,

Didius

---

### Post by Dill on 2009-05-24
Immediately after you plug in your headset, open a Terminal and type 

```
dmesg | tail | grep /dev
```

When you plug in your headset, you'll probably see an entry in *dmesg* for the device file with which it's associated. The above command will help you narrow down the output, and the last device file you see will likley be your headset.

Cheers,
Dill

---

### Post by Falc7 on 2009-05-24
thanks guys, perhaps you could help me interpret the info? They seem to give different answers.


wer@wer-laptop:~$ lsusb
Bus 008 Device 003: ID 064e:a115 Suyin Corp. 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 046d:c043 Logitech, Inc. MX320 Laser Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 147e:1000  
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:070f Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
wer@wer-laptop:~$ dmesg | tail | grep /dev
[ 4023.614698] input: Microsoft LifeChat LX-3000  as /devices/pci0000:00/0000:00:1a.2/usb3/3-2/3-2:1.3/input/input13



Just incase its useful, here is the part of the guide i am following:


1) Configure ALSA. (Optional, only for voice chat on separate device or USB headset)
If you are like me and using a separate device or a USB headset then we need to alter our Alsa configuration.

First thing we need to know is what device number or headset is.
Open up a terminal and type the following:

[precat /proc/asound/cards[/pre]

You should then see something like this:

 0 [M44            ]: ICE1712 - M Audio Delta 44

                      M Audio Delta 44 at 0xdc00, irq 19

 1 [Headset        ]: USB-Audio - Logitech USB Headset

                      Logitech Logitech USB Headset at usb-0000:00:02.0-9, full speed



This shows us our main card, and our USB Headset.
Device #0 is our M Audio Delta 44
Device #1 is our Logitech USB Headset.

---

### Post by Didius Falco on 2009-05-24
This is the command he is referencing:

```
cat /proc/asound/cards
``` I'm guessing he missed the tailing ] on the first part of that command...

If you look at the output from the two previous command, you'll see:

**Bus 003 Device 002**: ID 045e:070f Microsoft Corp. 

                               and

 4023.614698] input: Microsoft LifeChat LX-3000  as /devices/pci0000:00/0000:00:1a.2/usb3/**3-2**/3-2:1.3/input/input13

Which tells me that you have a Microsoft LifeChat LX-3000 on Bus 3, Device 2.

---

### Post by Falc7 on 2009-05-24
Thanks for your help! :)

---

### Post by Didius Falco on 2009-05-24
My Pleasure. Kill something for me in Warcraft. <G>

Regards,

Didius

---

