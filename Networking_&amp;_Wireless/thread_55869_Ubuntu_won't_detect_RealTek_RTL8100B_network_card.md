---
title: "Ubuntu won't detect RealTek RTL8100B network card"
date: 2005-08-10
forum: Networking &amp; Wireless
---

### Post by nighttime on 2005-08-10
I have an M6VLR ([http://www.biostar-usa.com/mbdetails.asp?model=m6vlr](http://www.biostar-usa.com/mbdetails.asp?model=m6vlr)) motherboard with an integrated RealTek RTL8100B network card that ubuntu just won't detect. I fear the card might be damadged because one of the LEDs is allways on. Is there a driver I can download and install so I can use my network card? I had this problem before and I was told to try some commands in this forum that showed a list of devices (in wich the card wasn't listed) just so you know I already tried that. I'd like to know what else I can try. If all else fails, I'd like to know what kind of network card I can buy that will fit my motherboard.

Help, please?

---

### Post by nighttime on 2005-08-14
No replies yet?  :(

---

### Post by kleeman on 2005-08-14
In your /boot/grub/menu.lst try adding 

noapic

to the end of the kernel line (i.e. the kernel line for the kernel image you boot)

See:

[http://www.linuxquestions.org/questions/showthread.php?threadid=52305](http://www.linuxquestions.org/questions/showthread.php?threadid=52305)

---

### Post by nighttime on 2005-08-17
Ok... I set the noapic option and rebooted my computer... now what? (please excuse my newbieness)

---

### Post by kleeman on 2005-08-17
See if the module/driver loaded with:

sudo lsmod | grep 8139

The driver is called 8139too and if it did not load then try

sudo modprobe 8139too

if that looks ok try

sudo ifup eth0

this brings up the network interface eth0 but assumes you have dhcp assigning ip addresses not a manual network...

Let me know what responses you get....

---

### Post by nighttime on 2005-08-21
Ok, at first there was no 8139too in lsmod, so I did

sudo modprobe 8139too

and with

lsmod | grep 8139

I got

8139too   24320   0
mii            4736     1 8139too

but when trying

sudo ifup eth0

Igot

Ignoring unknown interface eth0=eth0

Also on reboot 8139too and mii disappear from the lsmod list

---

### Post by kleeman on 2005-08-21
OK try loading the modules as you did above and then looking at the output of
ifconfig 

to see what interfaces are up

also after you load the module see what happens in 

dmesg

---

### Post by nighttime on 2005-08-21
x

---

### Post by nighttime on 2005-08-21
Ok, so I re-booted my machine and loaded the modules...

and this is what I got from ifconfig:

lo Link encap: Local Loopback
    inet addr:127.0.0.1 Mask:255.0.0.0
    inet6 addr:  ::1/128 Scope:Host
    UP LOOPBACK RUNNING MTU:16436 Metric:1
    RX packets: 7986 errors:0 dropped:0 overruns:0 frame:0
    TX packets: 7986 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:0
    TX Bytes: 725440 (708.7 KiB)    RX Bytes: 725440 (708.7 KiB)

There's nothing with eth0 or anything...

And I didn't know exactly what to look for in the output of dmesg... anyway, here are a few lines I think could be of some relevance:

Kernell command line: root=/dev/hda1 ro quiet splash noapic
Found and enabled local APIC!
mapped APIC to ffffd000 (fee00000)

And the very last line of the dmesg output was:

8139too Fast Etherner driver 0.9.27

And... if I may ask a kind of personal question... Am I being annoying having to be spoonfed like this? :P

---

### Post by kleeman on 2005-08-21
Not annoying- people need to learn somehow, the more you fiddle around yourself (google is your friend) after advice the faster you can sort things out yourself.

The interface is not up after loading the module. Try bringing it up explictly with

sudo ifconfig eth0 up

---

### Post by nighttime on 2005-08-22
I tried

sudo modprobe 8139too
sudo ifconfig eth0 up

and got

eth0: Error while opening interface flags: No such device

I don't know... I'm thinking it would be a lot easier just to get a new NIC cause I think mine might be damadged since one of the LEDs beside the jack is allways on, even when the computer's off (and plugged, ofcourse)

---

