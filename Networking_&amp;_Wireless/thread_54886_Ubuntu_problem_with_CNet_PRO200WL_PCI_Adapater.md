---
title: "Ubuntu problem with CNet PRO200WL PCI Adapater"
date: 2005-08-06
forum: Networking &amp; Wireless
---

### Post by UnderXP on 2005-08-06
Hello, i'm a ** ultra new linux user **, and I am very impressed with Ubuntu/Kubuntu. I installed both in one PC with lan adapter (CNET PCI) the installer automatically "see" and configure my lan, but the conection is broken. Can't do ping, traceroute,browse, NOTHING. I search in this forum but the solution don't work. I read that the problem is the driver. Can anyone linux expert user help me please ?

---

### Post by wbeck85 on 2005-08-09
[QUOTE=UnderXP]Hello, i'm a ** ultra new linux user **, and I am very impressed with Ubuntu/Kubuntu. I installed both in one PC with lan adapter (CNET PCI) the installer automatically "see" and configure my lan, but the conection is broken. Can't do ping, traceroute,browse, NOTHING. I search in this forum but the solution don't work. I read that the problem is the driver. Can anyone linux expert user help me please ?[/QUOTE]
 Hey, welcome to ubuntu.
I actually have the same problem. I just installed ubuntu on an old box(p3 500mhz,) with the intent to use it as a small server for my home as well as an internet router. However, my Pro200WL NIC card doesnt seem to work, like at all.
And here I thought ubuntu was to have supreme hardware support. Tis a shame.

Not that I'm bashing ubuntu. Far from it! So far, ubuntu has been my fav distro and I have tried to convince everyone I know to use it.

But yeah, funny this adapter doesnt work out of the box.

I downloaded a driver for it, but I dont feel like fiddling with it at the moment. good luck UnderXP and I hope that someone pops up and gives us a little guidence!

---

### Post by blind0wl on 2005-08-09
Can you post the output of ```
lspci
``` and ```
lsmod
``` Looks like either the kernel is not aware of it or the module isnt loading....what does ```
ifconfig
``` say?

---

### Post by wbeck85 on 2005-08-09
lspci yeilds ```
0000:00:11.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)
```

lsmod yeilds ```
Module                  Size  Used by
nls_cp437               5888  0
isofs                  33720  0
udf                    77060  0
ipt_state               2048  1
ipt_MASQUERADE          3584  1
ipt_LOG                 6656  7
iptable_mangle          2944  0
iptable_filter          3840  1
iptable_nat            24648  2 ipt_MASQUERADE
ip_conntrack           43668  3 ipt_state,ipt_MASQUERADE,iptable_nat
ip_tables              17408  6 ipt_state,ipt_MASQUERADE,ipt_LOG,iptable_mangle,iptable_filter,iptable_nat
ppp_deflate             6016  0
zlib_deflate           20632  1 ppp_deflate
bsd_comp                5760  0
ppp_async              10752  1
crc_ccitt               2176  1 ppp_async
ppp_generic            27668  7 ppp_deflate,bsd_comp,ppp_async
slhc                    7040  1 ppp_generic
ipv6                  229504  15
dmfe                   18716  0
tulip                  46112  0
snd_es1968             27648  3
snd_ac97_codec         64608  1 snd_es1968
snd_pcm_oss            47652  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  4 snd_es1968,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  2 snd_es1968,snd_pcm
gameport                4608  1 snd_es1968
snd_mpu401_uart         7168  1 snd_es1968
snd_rawmidi            22944  1 snd_mpu401_uart
snd_seq_device          8332  1 snd_rawmidi
snd                    50276  14 snd_es1968,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  1 snd
i2c_piix4               8592  0
i2c_core               21264  1 i2c_piix4
uhci_hcd               30224  0
usbcore               107384  2 uhci_hcd
pci_hotplug            30512  0
intel_agp              20636  1
agpgart                31784  1 intel_agp
floppy                 54864  0
pcspkr                  3816  0
rtc                    12216  0
md                     43856  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
tsdev                   7488  0
evdev                   9088  0
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  1 ide_cd
ext3                  120968  1
jbd                    54168  1 ext3
ide_generic             1664  0
piix                    9988  1
ide_disk               18176  4
ide_core              118988  4 ide_cd,ide_generic,piix,ide_disk
unix                   26164  246
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb

```
and ifconfig yields ```
eth0      Link encap:Ethernet  HWaddr 00:08:A1:0D:5A:9D
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:a1ff:fe0d:5a9d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:891 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:9 Base address:0xe800
```
It looks to me like ubuntu thinks it's there with eth0 up and all, but I don't really know how to fix it.

by the way thanks for the really quick reply

~Will

---

### Post by blind0wl on 2005-08-10
I was googling around and noticed that you have both modules loaded for the nic card.  Depending on the version of kernel your using, the dfme driver is most suitable for higher than 2.2 version kernels....tulip is compatible but not as good supposedly.  Id try removing the tulip module for a start:

```
modprobe -r tulip
```

It might also help to know whether you entered a static IP into the interface, as I can see that you have 192.168.0.1 all ready there?  Your saying your not getting anywhere via ping etc?  What is your PC connected to to use that range?  I suppose Im just trying to picture how your network is setup....it might be something simple, like a bad gateway address if you have one etc...any info will help me.

Oh...I think I noticed some sarcasm at the bottom of your message....something about the quick reply...  ;-)

---

### Post by wbeck85 on 2005-08-10
[QUOTE=blind0wl]I was googling around and noticed that you have both modules loaded for the nic card.  Depending on the version of kernel your using, the dfme driver is most suitable for higher than 2.2 version kernels....tulip is compatible but not as good supposedly.  Id try removing the tulip module for a start:

```
modprobe -r tulip
```

It might also help to know whether you entered a static IP into the interface, as I can see that you have 192.168.0.1 all ready there?  Your saying your not getting anywhere via ping etc?  What is your PC connected to to use that range?  I suppose Im just trying to picture how your network is setup....it might be something simple, like a bad gateway address if you have one etc...any info will help me.

Oh...I think I noticed some sarcasm at the bottom of your message....something about the quick reply...  ;-)[/QUOTE]
 Sarcasm? I think not, that was genuine gratitude, you replied in 5 minutes to my post, thanks again.

My network is composed of 5 computers and a networked printer, all running XP except the one that I am trying to configure currently and, of course, the printer. None have a firewall up, so I know that that isn't blocking my ping efforts. I have all five computers setup using static ip addresses. IP address range = 192.168.0.xxx, subnet mask = 255.255.255.0, the gateway will be the ubuntu box, whose NIC IP I tried to configure to be 192.168.0.1, and so the other 4+printer all have that address as their gateway. DNS server for the other computers is the ubuntu box, as well.

I am at work right now, so when I get home, I'll try removing tulip.

Thanks again for the help (no sarcasm there!)  :)

---

### Post by blind0wl on 2005-08-10
I was answering the last of the unanswered threads...working my way up :)  This one was near the bottom when I posted, so you must of got in just before me....sorry for the confusion....original post was the 8th July...didnt bother looking at your post :)

Silly question that I need to get out of the way...you have a link light etc at the back of your PC on the NIC dont you? And on the hub/switch your using?

Could you also post the output of:

```
dmesg | grep 'eth0'
```

Also a output of:

```
more /etc/network/interfaces
```

May come in handy

---

### Post by wbeck85 on 2005-08-11
I removed the tulip module. then to get eth0 back, i reloaded the dmfe module.

Interesting, the two leds on the back of the card are blinking at approximately one second intervals, at the same time. On my hub (Linksys WRT54g wireless router) All three leds (Link/Act, Full/Col, 100) are blinking in tandem at approximately one second intervals as well.

Here's dmseg | grep 'eth0' ```
will@server:~$ dmesg | grep 'eth0'
eth0: Davicom DM9102/DM9102A rev 49 at 0001e800, 00:08:A1:0D:5A:9D, IRQ 9.
eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
NETDEV WATCHDOG: eth0: transmit timed out
eth0: 21140 transmit timed out, status fc759147, SIA ffffff5e 00000000 00000000 00000000, resetting...
eth0: transmit timed out, switching to MII media.
NETDEV WATCHDOG: eth0: transmit timed out
NETDEV WATCHDOG: eth0: transmit timed out
eth0: no IPv6 routers present
NETDEV WATCHDOG: eth0: transmit timed out
NETDEV WATCHDOG: eth0: transmit timed out
NETDEV WATCHDOG: eth0: transmit timed out
NETDEV WATCHDOG: eth0: transmit timed out
NETDEV WATCHDOG: eth0: transmit timed out
NETDEV WATCHDOG: eth0: transmit timed out
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Davicom DM9102 at pci0000:00:11.0, 00:08:a1:0d:5a:9d, irq 9.
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: no IPv6 routers present
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: no IPv6 routers present
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
eth0: Tx timeout - resetting
will@server:~$
```

and here's /etc/network/interfaces ```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet static
	address 192.168.0.1
	netmask 255.255.255.0
	network 192.168.0.0
	broadcast 192.168.0.255
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.0.1 
```

---

### Post by blind0wl on 2005-08-11
ok...think I found the issue.  tulip and dmfe can work together no worries so dont worry about removing them....you'll need to add this line to your grub kernel line.

```
pci=noacpi
```

Turns out its a common fault with acpi management of the pci bus with this card.

HTH

---

### Post by UnderXP on 2005-08-11
Ok, i'll probe this solution tomorrow, thanks for your replies...

---

### Post by wbeck85 on 2005-08-12
blind0wl, I love you man, you have made my day!

underXP, if you are not sure what to do to add this to your grub kernel line (you did say you are an ultra noob with asterisks!) here's a quick how-to:

open up a terminal, type ```
sudo gedit /boot/grub/menu.lst
```scroll down through the commented out lines until you get to the pertinent stuff near the bottom, change the line that reads ```
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hdb1 ro silent splash
``` to ```
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hdb1 ro silent splash pci=noacpi
```

save it and exit gedit (text editor)

in the console type```
sudo grub update
```let that work. When it is done, the grub console opens in the terminal. You can just exit the terminal and reboot. hopefully the card works now, mine does!

Good luck underXP and thanks again blind0wl

---

### Post by blind0wl on 2005-08-12
No problems...glad I could help.

---

### Post by UnderXP on 2005-08-15
I add to grub the option pci=noacpi and don't work my lan card yet  ](*,) 

the command "lsmod" says:
dmfe                  18716  0
tulip                  46112  0

the command "lspci | grep Eth" says:
0000:00:0a.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 40)

the command "dmesg | grep eth0" says:
eth0: Davicom DM9102/DM9102A rev 64 at 0001b800, 00:08:A1:82:FE:1B, IRQ 18.
eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
eth0: no IPv6 routers present
eth0: no IPv6 routers present

and this line is repeat many times !!!!1
0000:00:0a.0: tulip_stop_rxtx() failed

Can help me please? I Think that problem is IPv6, but I don't know how disable it!!!!

---

### Post by thetmanvn on 2005-08-24
@UnderXP : I had the same result with u when I added pci=noacpi in menu.lst, so I tried to remove tulip module and reload dmfe with these commands below then it's work :

$sudo modprobe -r tulip
$sudo modprobe -r dmfe
$sudo modprobe dmfe

So try it to find out ur self !
Goodluck !

---

### Post by aardwolf on 2006-04-07
I know this thread is from last year... but your commands just helped me get my CNet PRO200WL working in Fedora core 5.  The only issue I have is that I have to type that after every reboot.  Is there any way to make those changes permanent?

---

### Post by aardwolf on 2006-04-08
[QUOTE=aardwolf]I know this thread is from last year... but your commands just helped me get my CNet PRO200WL working in Fedora core 5.  The only issue I have is that I have to type that after every reboot.  Is there any way to make those changes permanent?[/QUOTE]

Ummm... nevermind.  I just blacklisted tulip and everything is working properly.

---

### Post by ben ogle on 2007-06-21
The post that the top of this page solved my problem. But only on a reboot. If I make some changes, say, to my ip address then do a /etc/init.d/networking restart, its broken again.

What do I have to change to make the networking script recognize the pci=noacpi switch?

Ben

---

### Post by funkyidol on 2007-06-22
I followed all the above given steps but im still not able to make it work.
on running "sudi pppoeconf" it runs some test and says tht it could not connect using my card....
please help

---

