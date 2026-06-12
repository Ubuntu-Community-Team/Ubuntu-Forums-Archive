---
title: "ssh tranfer speeds"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by satipera on 2009-04-15
I have eventually managed to configure ssh between two computers on my home network but it is only between 1.7 and 2 mb/sec. I am using 54 mb/sec wireless. Is this a driver problem? and if so any ideas when it will be fixed? If it is something else I would welcome ideas.

---

### Post by nandemonai on 2009-04-15
It's most likely a wireless issue I'm guessing.

Have you tried other protocols? NFS / FTP or HTTP?

Some info on your wireless would likely help to.

Please post the output from these commands in terminal:

PCI card:

```
$ lspci
```

USB:

```
$ lsusb
```

---

### Post by lavinog on 2009-04-15
ssh has some additional overhead (data and cpu).
Also wireless communication also adds additional overhead (with additional encryption)

Generally I get low xfer rates with ssh if one machine is a low performance machine.
using a samba share instead usually triples the rate. I have also found the same to be true with http, but not every machine is going to have a web server installed.

There is another trick to reduce the overhead by changing the default encryption to blowfish.
To do this:
on the client (not the ssh server):
```
gksudo gedit /etc/ssh/ssh_config
```
find this line:
```

#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc

```
change to: (remove # and move blowfish-cbc to front of the list)
```

   Ciphers blowfish-cbc,aes128-cbc,3des-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc

```
This changes the prefered encryption cipher to reduce the perfomance hit that the default causes. I believe this sacrifices some, but not all encryption.
The ssh client determines the cipher to use, so you will have to do this on any computer that you want to connect with.
I think there might be a way to just tell the server to only accept blowfish connections, but it might cause compatibility issues.

---

### Post by lavinog on 2009-04-15
To make the server only use blowfish
on the server:
```
sudo nano -w /etc/ssh/sshd_config
```
add this line at the end:
```

Ciphers blowfish-cbc

```
press ctrl-x (press y then enter to save)

Note: I have not tested this type of setup. I got the info from the sshd_config man page.

---

### Post by satipera on 2009-04-15
Here are the logs, thanks each of you for your suggestions I will look very closely at them soon. The other computers log do you need them?


lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
ian@ian-laptop:~$ 

lsusb
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ian@ian-laptop:~$

---

### Post by freak42 on 2009-04-15
just to make sure.. you are not mixing ub megabits and megabytes.. because transfer speeds of 1.7-2 megabytes would be normal for this sort of wlan.

---

### Post by satipera on 2009-04-15
About 680 megabytes of information is taking about or a over 7 minutes to transfer between 1.5 and two megabits per second. This is my understanding. It seems to be about 10 times slower than my very ordinary disc transfer rates.

---

### Post by freak42 on 2009-04-15
> **satipera said:**
> About 680 megabytes of information is taking about or a over 7 minutes to transfer between 1.5 and two megabits per second. This is my understanding. It seems to be about 10 times slower than my very ordinary disc transfer rates.

680 MegaByes (+- 1 CD-ROM full) in 7 minutes is 1.6 MB/s (MegaBytes per Second). Your wlan transfer speed is 56 mbit/s (MegaBits per second) which is 7 MegaBytes per second, however this maximum speed is rarely achieved. I get about 3 MegaBytes per second over my wlan, and wlan is split across all connected computers.. so if both of your computers are connected via wlan 1.6 MegaBytes is perfectly normal, and you won't be able to increase it much, if at all.
If one of the computers is stationary, consider hoocking it up over lan cable, that way your transfer speed will approximately double. Hooking both computers up via lan cable will increase your throuput to maybe 60-80 MegaBits per seoncd or approx 8-9 MegaBytes per second.

hth

---

### Post by The Cog on 2009-04-15
680 megabytes over 7 minutes is around 1.6 megabytes/Sec which is around 13 megabits/Sec. Not the theoretical top speed, but not too bad, I feel. It might be interesting to watch the throughput with something like the sysyem monitor, or iftop. My guesss is that there are pauses waiting for a retransmission when the occasional packet gets lost.

---

### Post by satipera on 2009-04-15
I tried putting one comp on a cable and it made next to no difference. But I am glad that the system is running more or less as expected. Thanks for the help.

---

### Post by stchman on 2009-04-15
> **satipera said:**
> I have eventually managed to configure ssh between two computers on my home network but it is only between 1.7 and 2 mb/sec. I am using 54 mb/sec wireless. Is this a driver problem? and if so any ideas when it will be fixed? If it is something else I would welcome ideas.

Wirelss G is max theoretical 54mbs.  This translates to a max transfer rate of 6.75MB/s.

If you are getting ~1.5MB/s that is not bad.  When I transfer files via ssh or NFS from Wireless G laptop to another PC I get around 3MB/s.

I have found that a wire gives far better transfer than wireless.

---

### Post by MrWES on 2009-04-15
> **stchman said:**
> Wirelss G is max theoretical 54mbs.  This translates to a max transfer rate of 6.75MB/s.

If you are getting ~1.5MB/s that is not bad.  When I transfer files via ssh or NFS from Wireless G laptop to another PC I get around 3MB/s.

I have found that a wire gives far better transfer than wireless.


For what it's worth -- I get ~2.6MB/s when scp from my server to my laptop via wireless.

Bill

---

### Post by freak42 on 2009-04-15
> **satipera said:**
> I tried putting one comp on a cable and it made next to no difference. But I am glad that the system is running more or less as expected. Thanks for the help.

make sure the comp is actually using the wire and not the wifi, if you hook up a cable.

---

