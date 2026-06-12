---
title: "ipw3945 not showing up"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by Thomi on 2007-04-29
[Solved. see bottom of this post for solution]


Hi,

I notice that several other people have had similar problems, but none of them seem to be exactly the same as mine.

I installed Kubuntu 7.04 on an Asus A7J laptop - it has an Intel PRO/Wireless ABG chip built in. The problem is this:

[LIST]
[*]lspci shows the device correctly
[*]lshw -C network lists the device correctly
[*]Device works in windows correctly
[*]but ifconfig / iwconfig and network-manager don't list the device at all!
[/LIST]

I've made sure that the correct kernel module is loaded. One hint:

when I load the module, it complains that the "radio kill switch is on". This laptop hsa two methods of turning off the wireless. A physical switch (which is set correctly), and a keyboard key combination (Fn + F2). The key combination seems to do nothing.

Also, the wireless works fine under windows XP, so I'm assuming that the hardware is OK. FInally, the wireless worked perfectly under Kubuntu 6.10, and it seems like it *should* work here - the correct drivers are loaded, but for some reason ifconfig & iwconfig don't see the interfaces.

I've been using various Linux distributions for a number of years now, but this has got me stumped. As I mentioned at the top of my post, several other people seem to be having trouble with this, although none of them describe my situation exactly..


Any ideas? Tips? I have to reboot into windows to post here, so please excuse any delay in getting exact command dumps!



Solved!


The solution was to do this:

echo 1 > /proc/acpi/asus/wled


As root. After that, the kill switch works as it should. Great!

---

### Post by chili555 on 2007-04-29
Ahh! The old rf_kill problem. Please try:```
sudo echo 0 > /sys/bus/pci/drivers/ipw3945/*/rf_kill
```Did it stick? Did your wireless spring to life? If so, perhaps this will help: [http://ubuntuforums.org/showthread.php?t=303897](http://ubuntuforums.org/showthread.php?t=303897)

---

### Post by Thomi on 2007-04-29
> **chili555 said:**
> Ahh! The old rf_kill problem. Please try:```
sudo echo 0 > /sys/bus/pci/drivers/ipw3945/*/rf_kill
```Did it stick? Did your wireless spring to life? If so, perhaps this will help: [http://ubuntuforums.org/showthread.php?t=303897](http://ubuntuforums.org/showthread.php?t=303897)


Nope,

the rf_kill file contains a '2' - setting it to 0 does nothing - the file remains unchanged. Changing the kill switch (both physical and the one on the keyboard) does nothing to the contents of the file.


Any other ideas?

---

### Post by chili555 on 2007-04-29
Further research and a success on my own machine, suggests the command is actually:```
echo 0 | sudo tee /sys/bus/pci/drivers/ipw3945/*/rf_kill
```Is *this* productive?

---

### Post by Thomi on 2007-04-29
> **chili555 said:**
> Further research and a success on my own machine, suggests the command is actually:```
echo 0 | sudo tee /sys/bus/pci/drivers/ipw3945/*/rf_kill
```Is *this* productive?


Nope - that does exactly the same thing. The reason you might want to use the tee command rather than redirection is that redirection doesn't work nicely with sudo. However, I was logged in as root when I executed those commands.

So, it still mysteriously doesn't show up under ifconfig / iwconfig... Odd, and annoying! I can't access the Internet without it!

:(

---

### Post by Thomi on 2007-04-29
Well, I mamanged to get lots of information - hopefully this will help:

first, lspci output:

```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
01:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
01:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
01:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
01:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
01:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
01:02.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
06:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]

```

And lshw -C network shows the same thing:

```

  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@05:00.0
       logical name: eth0
       version: 01
       serial: 00:17:31:34:ef:70
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.2.1 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s
       resources: ioport:a800-a8ff iomemory:fdfff000-fdffffff irq:16
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@04:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0
       resources: iomemory:fdeff000-fdefffff irq:17

```

By this point it's prettyy obvious that the driver is loaded, but just in case, lsmod | grep ipw shows the following:

```

ipw3945               118816  1 
ieee80211              34760  1 ipw3945

```

Where to from here? ifconfig -a shows this:

```

eth0      Link encap:Ethernet  HWaddr 00:17:31:34:EF:70  
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe34:ef70/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:513 (513.0 b)  TX bytes:6953 (6.7 KiB)
          Interrupt:16 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2464 (2.4 KiB)  TX bytes:2464 (2.4 KiB)

```

(eth0 is my gigabit wired adaptor, not my wireless adaptor).

and iwconfig shows this:
```

lo        no wireless extensions.

eth0      no wireless extensions.

```

Finally, there are a few messages in Dmesg about the kill switch being on, and how wireless won't work while it's on. I tried setting the switch in both positions and rebooting, no difference. I tried using the keyboard wireless switch, same deal.

Attached is the "lspci -v" output - I don't know if that will be useful or not.

This is a clean install of feisty! The *only* package update I've done is to install xorg-driver-fglrx from the DVD, which I had to do in order to get X working properly.

Can anyone help? I'm tearing my hair out here ;-)


Cheers!

---

### Post by jlwood on 2007-04-29
I was looking thru the  fourm and found your post. I have a Toshiba A135-S4427 with the Intel 3945 abg card. I am dual booting with Vista Home. The wireless worked fine in Vista but when I installed Ubuntu I could not get the wireless or sound to work. I tried some of the suggestions but nothing was working. I even reinstalled the OS. I ran the command on the rf_kill and that did the trick. I can now connect to my linksys BEFW11S4 wireless router without encryption. I just started playing with linux so I have alot to learn. Next week I will figure out the encryption and sound issue.

---

### Post by Thomi on 2007-04-30
Well my sound works fine, and I can't seem to do anything with the rf_kill file.

I'll try recompiling the kernel driver, and see if that helps...

---

### Post by piovisqui on 2007-05-02
I have the same problem. No answer till now :(
Another thread about this:
[http://ubuntuforums.org/showthread.php?t=429382&highlight=ipw3945+loaded+interface](http://ubuntuforums.org/showthread.php?t=429382&highlight=ipw3945+loaded+interface)

---

### Post by piovisqui on 2007-05-04
First: lol o.O

Do you remember that some notebooks have a mechanical switch to turn off wireless and bluetooth? It was just switched off....

---

### Post by caesar753 on 2007-05-27
Hi all,
I have the same problem but the given soltions doesn't do anything.
Also I have an Asus 6000 and the wireless card is turned on by th Fn+F2 key combination, I tried to give the command

```
echo 1>/proc/acpi/asus/wled
```

but it doesn't function, do you have some idea how to turn on the wireless card? Please, help me... :(

---

### Post by pkeavney on 2007-05-29
I've been unable to get the ipw3945 card working since I got my laptop back in December. I was hoping upgrading to Feisty from Edgy would do the trick. I have tried every proposed solution I came across, which has worked for others, but nothing seems to work for me. Here's a recent link [http://ubuntuforums.org/showthread.php?t=441313&highlight=ipw3945](http://ubuntuforums.org/showthread.php?t=441313&highlight=ipw3945) I came across on this forum which contains another link describing the problem. Let us know if this helps.

---

