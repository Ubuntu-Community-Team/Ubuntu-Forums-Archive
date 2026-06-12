---
title: "ethernet module e100 wont completely blacklist inhibiting eepro100 loading"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by koshari on 2008-05-28
**ok heres the details**, 

using 8.04 on a local system the intel ethernet card doesnt support the e100 module. no problem it runs fine using the eepro100 module.

in 7.04 i simply placed the e100 on the blacklist and the eepro100 would load and all was fine.

however when i installed 8.04 and did the same (blacklisted the e100 module) the eepro100 is seen to load using lsmod however the hardware is not available in ifconfig.

if i rmmod eepro100 and then modprobe eepro100 all works fine.

after a boot looking at dmesg there are 2 lines that suggest e100 is trying to load, 

i realise that eepro100 is obsolete BUT its the only module i can get my ethernet to run successfully with.


so in summary i would like the machine to boot in a state where the ethernet was active without having tu run the 2 commands as root to remove and modprobe the eepro100 module.


**workaround** 
thanks to the replies so far and yes i did *remove the eepro100 module* from the default blacklist.

it turns out that e100 is loading in the initfs process and stopping the eepro100 module from loading properly. 

many thanks to enouf from the ##linux irc channel for supplying the workaround.


solution is, 

> you need to remake/upgrade your initrd. Add modules to /etc/initramfs-tools/modules, then run it

so i added

```
eepro100
``` to ```
/etc/initramfs-tools/modules
```

and then ran:

```
sudo update-initramfs
```.

one reboot and the network was up and happily connected at 100mb :-).

---

### Post by chili555 on 2008-05-28
Is the problem that eepro100 is itself on the blacklist:> # replaced by e100
blacklist eepro100I suggest changing this to:```
# replaced by e100
#blacklist eepro100
blacklist e100
```It's not clear to me, from your post, if you already tried this. I would then:```
sudo modprobe eepro100
sudo depmod -a
```Then I would see if this survives a reboot.

---

### Post by mazamazine on 2008-05-29
Same kind of problem for me... 
I've blacklisted ohci1394 and ieee1394 as I can't disable firewire through the BIOS bur it still load it.
eth1394 was blacklisted by default so I tried to "unblacklist" this module to see what happen and after reboot, it still be blacklisted !!
It seems that everything I can do on /etc/modrpobe.d/blacklist is not applied...

---

### Post by chili555 on 2008-05-29
> It seems that everything I can do on /etc/modrpobe.d/blacklist is not applied...What is the exact process you followed? What did you do to edit the file? May we see the current file"```
cat /etc/modrpobe.d/blacklist
```Thanks.

---

### Post by mazamazine on 2008-05-29
Here is the part of my blacklist concerned :

```
# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394
blacklist ohci1394
blacklist ieee1394
```

And here is lsmod | grep 1394, where it still appears :
```
ohci1394               36532  0 
ieee1394              106968  2 sbp2,ohci1394
```

To see what happen, I also tried to comment eth1394 and reboot. It should appear but the result of lsmod still be the same...

---

### Post by chili555 on 2008-05-29
Does it work if you also blacklist sbp2?> ohci1394               36532  0 
ieee1394              106968  2 **sbp2**,ohci1394

---

### Post by mazamazine on 2008-05-29
I tried it !

In fact I didn't explained my problem as it's not really linked...
(Here is my "real" ! problem : [http://ubuntuforums.org/showthread.php?p=5010954#post5010954](http://ubuntuforums.org/showthread.php?p=5010954#post5010954))

To sum up I have boot problems and I know I have to disable firewire. By blacklisting sbp2 it seemed to work but after 3 or 4 reboot my problem get back... And sbp2 still appeared in lsmod...

---

### Post by chili555 on 2008-05-29
From your dmesg:> [ 9.708000] irq 5: nobody cared (try booting with the "irqpoll" option)Did you try this? I suggest *sudo gedit /boot/grub/menu.lst* Find the first line that looks like this:```
title           Ubuntu 8.04, kernel 2.6.24-17-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-17-generic root=UUID=4b70eff7-c255-4e38-9af6-1a9d9af90fe3 ro quiet splash
initrd          /boot/initrd.img-2.6.24-17-generic
quiet

```Add 'irqpoll' like this:```
title           Ubuntu 8.04, kernel 2.6.24-17-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-17-generic root=UUID=4b70eff7-c255-4e38-9af6-1a9d9af90fe3 ro quiet splash **irqpoll**
initrd          /boot/initrd.img-2.6.24-17-generic
quiet

```Save and close gedit; reboot. Is booting faster?

---

### Post by mazamazine on 2008-05-29
I don't know what is irqpoll so before I prefer to let you know my grub is a kind of special ! I spend so many time before it works properly so have a look please !! ;)

```
title		Ubuntu 8.04
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot

title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
chainloader +1
makeactive
```

I want to add that I also can't boot at all sometimes due to initrd... A link ??!

---

### Post by chili555 on 2008-05-29
That's a dandy grub menu and I gather it took a bit of fiddling to get dual boot going. It looks like it's on two different harddrives; not an easy thing to do. I may have to save this one myself! irqpoll will not harm that; it will either get the IRQs working well or not. Another thing to try from your dmesg: PCI: If a device doesn't work, try "pci=routeirq".

I would add irqpoll to your boot menu like this:```
title		Ubuntu 8.04
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda1 ro quiet splash **irqpoll**
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot

title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
chainloader +1
makeactive
```Reboot and if it still takes 3 minutes to boot up, we know it's not yet fixed. Then you can remove it, add pci=routeirq in its place and try again. Again, if your boot still takes 3 minutes or so, we still have not fixed it and you may safely remove that. 

After that, we may have another tool out in the garage, behind the water heater.

---

### Post by mazamazine on 2008-05-29
I tried to add irqpoll and it *seems* to be ok. I insist on *seems* as it seemed to work each time I tried something before and after some reboot, it did it again (very often after a long time off).

So I wait a bit and confirm if it does work after several boots.

---

### Post by chili555 on 2008-05-29
You can probably tell pretty easily by checking dmesg to see if all this confusion has gone away:> [    9.780000] ohci1394: fw-host4: Runaway loop while stopping context: ...
[    9.728000] ohci1394: fw-host4: Runaway loop while stopping context: ...
[    9.780000] ohci1394: fw-host4: OHCI-1394 165.165 (PCI): IRQ=[16]  MMIO=[fdfa0000-fdfa07ff]  Max Packet=[65536]  IR/IT contexts=[32/32]
[    9.780000] ohci1394: fw-host4: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[    9.880000] ohci1394: fw-host4: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[    9.980000] ohci1394: fw-host1: Get PHY Reg timeout [0x00000000/0x00000000/100]
[    9.980000] ohci1394: fw-host4: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   10.080000] ohci1394: fw-host4: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   10.176000] ohci1394: fw-host4: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   10.276000] ohci1394: fw-host4: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   10.376000] ohci1394: fw-host4: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   10.476000] ohci1394: fw-host4: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   10.576000] ohci1394: fw-host4: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   10.676000] ohci1394: fw-host4: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   10.772000] ohci1394: fw-host4: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   10.872000] ohci1394: fw-host4: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   10.972000] ohci1394: fw-host4: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   11.072000] ohci1394: fw-host4: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   11.172000] ohci1394: fw-host4: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   11.272000] ohci1394: fw-host4: Set PHY Reg timeout [0xffffffff/0x00004000/100]No reason not to try it over several days, however if all these timeouts are gone and your boot is quick, you are probably fixed. Check with:```
dmesg | grep timeout
```

---

### Post by mazamazine on 2008-05-29
I checked dmesg each time I tried to fix the problem, and each time, after normal boot I had only one "normal" line about ohci fw-host and no timeout stuffs.
When I tried to blacklist sbp2, it booted properly and dmesg displayed that too (as now) :
```
ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[fd2ff000-fd2ff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
```

Despite that, the problem wasn't fixed actually
It's really strange... It seems to appear "randomly" !!
That's why I said I will confirm, as I don't think I can be sure the problem is totally fixed this way. The experiences showed it can "come back" aaargh ! hehe ;)

---

### Post by mazamazine on 2008-05-29
Ooh, maybe I should add this (I don't know if there's any link ?).
In dmesg I found that error :
```
ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found
```

---

### Post by chili555 on 2008-05-29
> ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not foundI this, too. Please see: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/58386](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/58386) especially this:> The purpose of this optional kernel feature, enabled by "CONFIG_ACPI_CUSTOM_DSDT_INITRD=y" in the kernel .config at build-time, is to allow the user to replace the BIOS Advanced Configuration & Power Interface (ACPI) Differentiated System Description Table (DSDT) with one that has been modified to solve problems in the BIOS shipped by manufacturers.

The message you see is correct. As far as the kernel is concerned it is an error because it is told to expect to find a replacement DSDT.aml and it isn't there. However the message could be altered somewhat to make it sound less harsh.It doesn't seem like anything either of us should worry about.

---

### Post by mazamazine on 2008-05-29
Ok so I forgot that !

About my boot problem I'll tell you that tomorrow as, strangely, this problem appears for sure each mornings, after a long time shutted down... But not each time if I reboot during the day... ?!?

---

### Post by mazamazine on 2008-05-30
Hi,

Two new infos :
- A man I'm takling with, on an other forum, has tried to add the irqpoll option and it didn't changed anything for him...
- This morning the problem has changed ! It didn't boot at all.
I had to boot 3 times and it finaly booted normaly.
As I reseted, I don't have the dmesg but I wrote some of the messages. 
Many lines like this :
```
(ohci_irq_handler+0x0/0+910 [ohci1394])
```
Then, ```
disabling IRQ#5
``` and ```
ata.1 status DRDY
```
To finish, every 30s a line saying ```
revalidation failed
```

---

### Post by mazamazine on 2008-06-03
Bad new ! irqpoll doesn't work... It did it again...
I wonder if it's not an hardware problem. A man as the same problem and has a Shuttle SN68SG2 too... Maybe something about the motherboard ?

---

### Post by mazamazine on 2008-06-05
pci=routeirq option doesn't work...
I aslo tried to disable IRQ in the BIOS but without results !

---

### Post by jan777 on 2008-10-17
Hi,

This is most definitely a hardware problem.
I have been searching the net for a long time and I have more or less the same problem.
PC runs OK all day and then the next day I have a very long boot caused by several instances (32) of The ohci1394 controller.
I have tried it with XP and the problems are the same.
I also use a Shuttle SN68SG2 barebone.
Problem is that firewire cannot be disabled in the BIOS.

---

### Post by monster on 2010-09-03
The solution posted in the first message helped me to remove automatic ohci1394 and ieee1394 loading whereas it was blacklisted in /etc/modprode.d/blacklist
I have added firewire-core to the /etc/initramfs-tools/modules and run update-initramfs and my Ubuntu Karmic Koala (10.04) loads firewire-core every bootup.
Thanks for info.

---

