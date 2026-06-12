---
title: "Speedstream 6520"
date: 2006-12-13
forum: Networking &amp; Wireless
---

### Post by Valencik on 2006-12-13
Hello

Ok, well I am a subscriber to Aliant Highspeed, they recently upgraded/changed their internet service and sent me a new modem in the mail. So i get the siemens speedstream 6520 router (in the mail) hook it up and no go. After some troubles it turns out that something on their end wasn't right. Today a techie came over fixed it up while I was at school, he got it all working fine on his laptop (he apparently had no knowledge of linux), i get home, and no go. I try to connect to google, nothing, so i browse to the IP of the router 192.168.2.1 and get ausername password prompt, enter what should be correct in and it doesn't work. I guess the story is, I'm currently connected to my internet on an old windows 98 computer with no problems. What am I doing wrong on Ubuntu? 

I think you guys are my last hope, Aliant doesn't offer tech support for linux(no surprises).

I've tried playing with network settings
System > Administration > Networking
Under the Connections tab > Ethernet connection (The interface eth0 is active) > Properties:
enable this connection is clicked
configuration (i've tried both DHCP and Static IP address)
For Static IP address:
IP address: 192.168.2.13
Subnet mask: 255.255.255.0
Gateway address: 192.168.2.1

nothing
can't even get the password prompt when i browse to [http://192.168.2.1](http://192.168.2.1) anymore

help please

---

### Post by dmizer on 2006-12-13
if you configure for dhcp, do you get an ip (check ifconfig in the command line)?  if so, from the command line, can  you ping the router?

have you tried disabling ipv6?

---

### Post by Valencik on 2006-12-20
if i configure it to DHCP i get no IP back (i'm pretty sure) and pinging the router only works if i have it set to static IP and i can then ping the custom IP
Maybe this will help

```
andrew@Andrew-ubuntu:~$ sudo ifup eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:0a:e6:60:e1:9b
Sending on   LPF/eth0/00:0a:e6:60:e1:9b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
:~$andrew@Andrew-ubuntu <mailto:andrew@Andrew-ubuntu>

andrew@Andrew-ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0A:E6:60:E1:9B
          inet6 addr: fe80::20a:e6ff:fe60:e19b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:3801
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:12564 (12.2 KiB)
          Interrupt:5 Base address:0xdc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12037 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12037 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2547414 (2.4 MiB)  TX bytes:2547414 (2.4 MiB)

```


To me it looks like i'm not getting any response from the router. But right now i have the exact same router hooked up to an old win95 box and it works fine. Also tried live booting ubuntu to see if maybe it would try and re-establish DHCP settings or something, no luck. Sorry i can't provide more info, i'm not overly experienced with this.

---

### Post by dmizer on 2006-12-21
wow ... sorry i'm so late on this.  your problem has a simple fix.  just disable ipv6.

this line here:
```
inet6 addr: fe80::20a:e6ff:fe60:e19b/64 Scope:Link
```
means you're picking up an ipv6 ip address from your router, but it won't work this way.

disable ipv6 by pasting the following into your terminal:
```
sudo echo "blacklist ipv6" >> /etc/modprobe.d/blacklist
```
reboot, or restart networking, and all should be well.

if that fails, you'll have to manually edit the file.

---

### Post by Valencik on 2006-12-21
Hm, didn't seem to work.

```
andrew@Andrew-ubuntu:~$ sudo echo "blacklist ipv6" >> /etc/modprobe.d/blacklist
bash: /etc/modprobe.d/blacklist: Permission denied
andrew@Andrew-ubuntu:~$
```

So i opened up File Browser (Root), type in password, find /etc/modprobe.d/blacklist, add "blacklist ipv6" to the bottom of the file, save, exit, reboot. Same problem. However, the ipv6 address is now gone.

```
andrew@Andrew-ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0A:E6:60:E1:9B
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:99
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:3762 (3.6 KiB)
          Interrupt:5 Base address:0xdc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2252 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2252 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:587833 (574.0 KiB)  TX bytes:587833 (574.0 KiB)

```

I then ran ifdown eth0 and ifup eth0, same as before.

```
andrew@Andrew-ubuntu:~$ sudo ifdown eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:0a:e6:60:e1:9b
Sending on   LPF/eth0/00:0a:e6:60:e1:9b
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.2.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
andrew@Andrew-ubuntu:~$ sudo ifup eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:0a:e6:60:e1:9b
Sending on   LPF/eth0/00:0a:e6:60:e1:9b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
andrew@Andrew-ubuntu:~$
```

Under 'System > Administration > Networking' i have eth0 configured to DHCP. Not sure what else to do.

---

### Post by dmizer on 2006-12-21
humm ... let's take a little deeper look then.  post the output of:
lspci

as well as the output of:
lsmod

and the contents of your /etc/network/interfaces file.

---

### Post by Valencik on 2006-12-22
Thanks again.
Here:

```
andrew@Andrew-ubuntu:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
andrew@Andrew-ubuntu:~$ 
```

```
andrew@Andrew-ubuntu:~$ lsmod
Module                  Size  Used by
nls_cp437               5888  1
msdos                  10240  1
fat                    53020  1 msdos
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
radeon                116000  1
drm                    73236  2 radeon
ppdev                   9220  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
md_mod                 72532  0
dm_mod                 58936  1
lp                     11844  0
rsrc_nonstatic         13440  0
pcmcia_core            42640  1 rsrc_nonstatic
af_packet              22920  2
tsdev                   8000  0
snd_seq_dummy           3844  0
snd_seq_oss            33536  0
i2c_viapro              8980  0
snd_seq_midi            9376  0
i2c_core               21904  2 i2c_acpi_ec,i2c_viapro
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                51984  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_mpu401              6728  0
usbhid                 39904  0
analog                 12320  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
floppy                 62148  1
via_ircc               26900  0
pcspkr                  2180  0
irda                  187068  1 via_ircc
crc_ccitt               2304  1 irda
snd_via82xx            28824  1
psmouse                36100  0
gameport               15496  2 analog,snd_via82xx
rtc                    13492  0
snd_ac97_codec         93216  1 snd_via82xx
snd_ac97_bus            2304  1 snd_ac97_codec
serio_raw               7300  0
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
via_rhine              23940  0
snd_pcm                89864  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  2 snd_seq,snd_pcm
snd_page_alloc         10632  2 snd_via82xx,snd_pcm
snd_mpu401_uart         7808  2 snd_mpu401,snd_via82xx
mii                     5888  1 via_rhine
snd_rawmidi            25504  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8716  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
snd                    55268  14 snd_seq_oss,snd_seq,snd_mpu401,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10208  1 snd
via_agp                 9856  1
agpgart                34888  2 drm,via_agp
evdev                   9856  1
ext3                  135816  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               34184  0
uhci_hcd               33808  0
usbcore               130820  4 usbhid,ehci_hcd,uhci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  4
via82cxxx               9988  0 [permanent]
generic                 5124  0
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit
:~$andrew@Andrew-ubuntu
```


And here are the contents of /etc/network/interfaces 

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
auto eth0

# The primary network interface
iface eth0 inet dhcp
```


Hope this helps.

---

### Post by dmizer on 2006-12-23
i think (think) i may have found your fix.

make and model of your laptop will be helpful.

try this:
```
gksudo gedit /boot/grub/menu.lst
```
scroll all the way to the bottom and look for your boot line, it should look something like the following:
> title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

now add the following boot parm to the end of the **"kernel"** line:
acpi=off

so your kernel line will now look something like this:
> kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash acpi=off

save the file and reboot.  see if you can get connected.

---

### Post by Valencik on 2006-12-23
My computer isn't a laptop, it's a rather old sort of mixture of parts. Running a AMD Athlon XP with just about everything intergrated into the motherboard (including the network card).

Well I opened up the grub menu file and I had plenty of lines at the bottom that looked like you described. So here is the entire end of the file, did you mean the VERY bottom?

```


## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, kernel 2.6.12-10-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Adding it to the first one didn't work. Oh, and in comparison to your example are my kernals not really out of date?

---

### Post by dmizer on 2006-12-23
top one is the one ... this one:
```
title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot
```
so if it didn't work by adding acpi=off to that line, then we haven't fixed your problem yet.  your kernels are not old, the difference is that my kernel example was taken from edgy and yours is from dapper.

all the rest of the entries in there are from old kernels.  you can go into synaptic and uninstall them to save hard drive space.

post the output of:
```
cat /proc/interrupts
```

---

### Post by qamelian on 2006-12-23
It may be a defective unit as well. I fought with Aliant for a week trying to get mine working. They eventually sent out a tech who agreed that it was faulty. Apparently, there have been a fair number of bad Speedstream units from what the tech told me. They swapped mine out for a Comtrend CT-301 and no all is right with my world...at least, internet-wise.

---

### Post by handy on 2006-12-23
This link may help with access to the firmware of the modem:

[http://whirlpool.net.au/index.cfm?a=h_view&model_id=279](http://whirlpool.net.au/index.cfm?a=h_view&model_id=279)**__**

---

### Post by Valencik on 2006-12-24
Wow, thank you so much for all the support so far. Ubuntu has a ridiculously awesome community behind it.

```
andrew@Andrew-ubuntu:~$ cat /proc/interrupts
           CPU0
  0:      54146          XT-PIC  timer
  1:         99          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  5:        964          XT-PIC  uhci_hcd:usb1, uhci_hcd:usb2, eth0
  7:          1          XT-PIC  parport0
  8:          3          XT-PIC  rtc
 10:          0          XT-PIC  MPU401 UART
 11:          2          XT-PIC  ehci_hcd:usb4
 12:       1969          XT-PIC  uhci_hcd:usb3, VIA8233
 14:       6929          XT-PIC  ide0
 15:       3456          XT-PIC  ide1
NMI:          0
LOC:          0
ERR:          0
MIS:          0
andrew@Andrew-ubuntu:~$
```

Not sure what that tell you or what it means but there you go.

---

### Post by dmizer on 2006-12-24
> **Valencik said:**
> Not sure what that tell you or what it means but there you go.

that's the linux inequivalent of checking for irq conflicts.  it also tells me that your computer does indeed see your network card as eth0.  sometimes everything says eth0, but really the card is eth1.  try this:
```
sudo ifdown eth0
sudo modprobe -r uhci_hcd
sudo ifup eth0
```

this may disable usb hardware (like a usb mouse).  so be aware.  this is not a permanent arrangement, so if this disables your mouse, all you'll have to do is disconnect it and reconnect it and it will work again.

---

### Post by Valencik on 2006-12-25
Well i think we made some progress. 

```
andrew@Andrew-ubuntu:~$ sudo ifdown eth0
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:0a:e6:60:e1:9b
Sending on   LPF/eth0/00:0a:e6:60:e1:9b
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.2.1 port 67

andrew@Andrew-ubuntu:~$ sudo modprobe -r uhci_hcd
andrew@Andrew-ubuntu:~$ sudo ifup eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:0a:e6:60:e1:9b
Sending on   LPF/eth0/00:0a:e6:60:e1:9b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.2.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.10 - - renewal in 117008 seconds.

```

To mean that looks great. Discover, offer, request, acknowledgment, bound to an IP, awesome...... No go :(
I try to browse to google and the connection was reset by server, or it just waits for a replying forever.

However now if i just do ifdown eth0 and ifup eth0 the same thing happens. Whatever the other line (sudo modprobe -r uhci_hcd) did must have been permanent?



Note no (sudo modprobe -r uhci_hcd)
```
andrew@Andrew-ubuntu:~$ sudo ifdown eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:0a:e6:60:e1:9b
Sending on   LPF/eth0/00:0a:e6:60:e1:9b
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.2.1 port 67
andrew@Andrew-ubuntu:~$ sudo ifup eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:0a:e6:60:e1:9b
Sending on   LPF/eth0/00:0a:e6:60:e1:9b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPOFFER from 192.168.2.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.10 -- renewal in 120971 seconds.
andrew@Andrew-ubuntu:~$

```


* Not sure what this means but i just booted ubuntu (6.06) on my Dad's laptop hooked up to the SpeedStream 6520 and it works fine on the internet. I assume this means the problem is with my computer alone and not some compatibility issue in general. However when i booted of the live CD on my desktop the internet still did not work. Rawr! I don't understand why this isn't working!

---

### Post by dmizer on 2006-12-26
okay, here's a little run down to let you know how i've gotten to where we are so far.

you remember from cat /proc/interrupts, you see this line:
```
 12:       1969          XT-PIC  uhci_hcd:usb3, VIA8233
```
VIA8233 is the module (driver) for your pci bridge (how your network adapter talks to your computer).  i know this from the output of "lspci" back on page one.  uhci_hcd is the module for your usb adapters.  this i already know, but you can find out what modules are driving what hardware by taking a look at the output of "lsmod" (again back on page 1).

in this case, both the usb and the nic are appearing on the same interrupts.  i've had this issue with other cards before so i suspected it might be a problem.

the "modprobe -r uhci_hcd" command removed the conflicting usb module, and allowed you to pull an ip.  now, why you couldn't browse ... that's our next target.  for that we'll need to edit grub again, just like in [post 8](http://www.ubuntuforums.org/showpost.php?p=1921654&postcount=8) so that the line reads:
```
 kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash acpi=noirq
```

reboot, and see if you get an ip again:
```
ifconfig
```
if so, can you ping anything?  google?  if you can't ping google, can you ping google by ip?
```
ping 66.249.89.104
```
if you can ping by ip but not by url, then we'll need to take a look at your dns settings next.

---

### Post by Valencik on 2006-12-26
Don't know if this tells you anything at all but i booted up my computer, got the hasn't checked for 30 boots so it starts scanning (the kernal i believe?) and i get these messages.

```
.............      /sys/devices/platform/i82365.0/bus failed
modprobe: WARNING: Not loading blacklisted module ipv6     |29.8%

modprobe: WARNING: Not loading blacklisted module ipv6

```

Other than that it booted fine, changed the grub menu, rebooted, got this:

```
andrew@Andrew-ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0A:E6:60:E1:9B
          inet addr:192.168.2.10  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:5
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2788 (2.7 KiB)  TX bytes:3113 (3.0 KiB)
          Interrupt:5 Base address:0xdc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:513 errors:0 dropped:0 overruns:0 frame:0
          TX packets:513 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:122365 (119.4 KiB)  TX bytes:122365 (119.4 KiB)

andrew@Andrew-ubuntu:~$ ping 66.249.89.104
PING 66.249.89.104 (66.249.89.104) 56(84) bytes of data.
64 bytes from 66.249.89.104: icmp_seq=3 ttl=241 time=218 ms
64 bytes from 66.249.89.104: icmp_seq=4 ttl=241 time=219 ms
64 bytes from 66.249.89.104: icmp_seq=5 ttl=241 time=219 ms
64 bytes from 66.249.89.104: icmp_seq=6 ttl=241 time=218 ms
64 bytes from 66.249.89.104: icmp_seq=7 ttl=241 time=218 ms
64 bytes from 66.249.89.104: icmp_seq=8 ttl=241 time=217 ms
64 bytes from 66.249.89.104: icmp_seq=9 ttl=241 time=218 ms
64 bytes from 66.249.89.104: icmp_seq=11 ttl=241 time=217 ms
64 bytes from 66.249.89.104: icmp_seq=12 ttl=241 time=219 ms
64 bytes from 66.249.89.104: icmp_seq=13 ttl=241 time=218 ms
64 bytes from 66.249.89.104: icmp_seq=14 ttl=241 time=219 ms

--- 66.249.89.104 ping statistics ---
15 packets transmitted, 11 received, 26% packet loss, time 14043ms
rtt min/avg/max/mdev = 217.819/218.508/219.486/0.738 ms
andrew@Andrew-ubuntu:~$

```

seems like i am connected and it is working just not very well. However, with firefox i get nothing.

```
andrew@Andrew-ubuntu:~$ ping google.ca
PING google.ca (64.233.187.104) 56(84) bytes of data.
64 bytes from 64.233.187.104: icmp_seq=1 ttl=237 time=59.5 ms
64 bytes from 64.233.187.104: icmp_seq=4 ttl=238 time=57.8 ms
64 bytes from 64.233.187.104: icmp_seq=5 ttl=237 time=59.2 ms
```
with 50% packet loss

---

### Post by dmizer on 2006-12-26
lol ... the error is telling you that ipv6 is not being loaded.  which of course is true because we black listed it because we don't want it enabled.  so the error is merely reporting to you that what we did to blacklist the ipv6 is indeed working as it should.

now, we need to fix your dns servers.  if you don't already know what your ISP's DNS server addresses are, you can find them this way:  check your network settings (system > administration > networking, click on the DNS tab).  the DNS server addresses are going to be the addresses that do not start with 192.168 ...

now, edit your dhclient configuration like so:
```
sudo nano /etc/dhcp3/dhclient.conf
```
and find the line that looks like this:
> #prepend domain-name-servers 127.0.0.1;
remove the "#" from the front of the line, and edit it so it looks like this:
> prepend domain-name-servers x.x.x.x, x.x.x.x;
where "x.x.x.x" is replaced with your ISP's DNS server addresses.

save the file, and restart networking or reboot, and you should be able to browse :)

might also (for good measure) disable ipv6 in firefox, by typing: **about:config** in the address bar.  type **ipv6** in the search bar, and double click on the line to change it from false to true.

---

### Post by Valencik on 2006-12-26
System > Administration > networking > DNS

I see two entries, both of which are they same:

**192.168.2.1**

You said they shouldn't start with 192.168....?
So are these my DNS servers or should I call my ISP?


I'm heading out now to rent some video games :cool: If there's no reply when I get back I'll just use those IPs, err, IP.

Thanks again.


Oh, and for search domains i have one entry

```
no-domain-set.aliant
```

---

### Post by dmizer on 2006-12-26
heh ... using your router (read: 192.168.2.1) as your dns server will cause exactly the problem your now having.

try using these dns server addresses instead: 208.67.222.222 and 208.67.220.220

so the dhclient.conf line should look exactly like this:
```
prepend domain-name-servers 208.67.222.222, 208.67.220.220;
```

for more information about where i got those numbers, see this site: [http://www.opendns.com/](http://www.opendns.com/)

---

### Post by Valencik on 2006-12-26
alright, i changed my DNS settings. Still nothing.
Hmm, this laptop i'm on is also hooked up to the speedstream router and it appears to have it's DNS servers set to the router as well.

```
Microsoft(R) Windows DOS
(C)Copyright Microsoft Corp 1990-2001.


C:\DOCUME~1\DAVIDV~1>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : DAVID-VALENCIK
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Hybrid
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : no-domain-set.aliant

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : no-domain-set.aliant
        Description . . . . . . . . . . . : Broadcom 570x Gigabit Integrated Con
troller
        Physical Address. . . . . . . . . : 00-11-43-67-5E-58
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.2.11
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.2.1
        DHCP Server . . . . . . . . . . . : 192.168.2.1
        DNS Servers . . . . . . . . . . . : 192.168.2.1
                                            192.168.2.1
        Lease Obtained. . . . . . . . . . : 26 December 2006 11:35:03
        Lease Expires . . . . . . . . . . : 29 December 2006 11:35:03

C:\DOCUME~1\DAVIDV~1>
```

How come it works here but not on Ubuntu? 
I hope i'm not asking stupid questions
](*,)

---

### Post by dmizer on 2006-12-26
lol ... no, not stupid questions.

humm ... did you reboot or restart networking after editing dhclient.conf?  if not, you might try one more time.  my fault for neglecting to mention it ... i was very sleepy.

if you have already rebooted, and it still doesn't work, then reboot your entire network.  make sure you do that in this order:
1)  shut down all your connected computers.
2) power off the router.
3) power off the modem.
4) wait 10 seconds.
5) power on the modem (wait for it to sync)
6) power on the router (wait for it to sync)
7) power on your ubuntu computer.

can you browse now?

---

### Post by Valencik on 2006-12-28
Ok, so i turned off all my computers, my modem (have no router, the speedstream is kind of like a router and modem in one), and left it like that over night (more like 36 hours). So i turn the modem on today, let it finish, turn on my Ubuntu Desktop, still can't browse. I don't think I'm even getting an IP anymore.

```
andrew@Andrew-ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0A:E6:60:E1:9B
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:6
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:2394 (2.3 KiB)
          Interrupt:5 Base address:0xdc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:235 errors:0 dropped:0 overruns:0 frame:0
          TX packets:235 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:61393 (59.9 KiB)  TX bytes:61393 (59.9 KiB)

andrew@Andrew-ubuntu:~$ ping google.ca
ping: unknown host google.ca
andrew@Andrew-ubuntu:~$ ping 66.249.89.104
connect: Network is unreachable
andrew@Andrew-ubuntu:~$ sudo ifup eth0
Password:
ifup: interface eth0 already configured
andrew@Andrew-ubuntu:~$

```

So i now try to bring down eth0 and bring it back.

```
andrew@Andrew-ubuntu:~$ sudo ifdown eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:0a:e6:60:e1:9b
Sending on   LPF/eth0/00:0a:e6:60:e1:9b
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.2.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
andrew@Andrew-ubuntu:~$ sudo ifup eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:0a:e6:60:e1:9b
Sending on   LPF/eth0/00:0a:e6:60:e1:9b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
andrew@Andrew-ubuntu:~$

```



And my laptop is again plugged into the speedstream and currently working fine. RAWR! Did I miss something?

---

### Post by dmizer on 2006-12-30
i've spent the past several days crawling the net for an answer to your problem here, and everything i've found about your card not working is from years ago.  the simple fact is that your card should be working fine.

i don't know how difficult it will be for you, but my best suggestion at this point is to try another access point.  haul your machine over to a friend's house and see if you can get it connected (making sure of course that they don't have your same router/modem).  if it works at another location, your only recourse at this point will be to push your provider into giving you a different modem.

i found some hacks for it, but it's really old stuff, and i wouldn't suggest using information that dated.

additionally, i might suggest burning a copy of [knoppix](http://www.knoppix.org/) and boot to it (live cd).  if you can get connected in knoppix, then we'll have some more information to go on.

---

### Post by Valencik on 2006-12-31
Thanks a million, really, I would have been no where without your support. I'll try some more live boots (Ubuntu, Kubuntu, Knoppix STD) see if I get anything there. A couple questions before I'm on my on.

Is it at all possible that it is my network card? And that replacing that may help?

Would reinstalling Ubuntu help at all?

And I guess, in your opinion, is this a hardware problem or a software problem?


Thanks again.

---

### Post by dmizer on 2007-01-02
with the above suggestions, i'm actually trying to establish if this is a hardware or software problem.

1) if by using an independent non-ubuntu based os (knoppix) you are able to connect, then we've verifed that the problem is in the os rather than the speedstream or the network card.
2) if you are able to connect your machine to another device (not your speedstream) then we'll know a couple of things ... first, that the nic works fine, and second, that the problem is in the speedstream itself.

something else you can try if it's too much trouble to move your machine ... is simply borrow a wired router from someone.  the router does not need to be connected to the internet in order for it to hand an ip to your machine.  so, connect power to the router, and ethernet cable from the router to your troubled ubuntu network card, restart networking and see if you pull a 192.168.x.x ip address.

again, if you can pull an ip address from an independent router, then you know that the problem is with the speedstream and neither your nic, nor ubuntu.

---

### Post by handy on 2007-01-03
You could re-flash the firmware if that is supported, sometimes firmware becomes corrupt, & sometimes ISP's modify it when they supply...

---

### Post by pinboy on 2007-10-02
if you have a 6520 you should reset the 6520 to fatory defaults, locate the reset button on the bottom of the 6520 and while holding the reset button watch the power light when it flashes red release it. then you can go to the config utility 192.168.2.1 , you can then configure the 6520 with your aliant UN and PW info. you will know it has connected when the internet light comes on solid green. the 6520 will then send an IP to you linux box probably a 192.168.2.10. and the connection is established. this should solve the problem. please let me know.

---

