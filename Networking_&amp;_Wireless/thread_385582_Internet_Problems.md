---
title: "Internet Problems"
date: 2007-03-15
forum: Networking &amp; Wireless
---

### Post by royrules22 on 2007-03-15
I have some problems with my Internet and connections.  

Firstly when I'm in my dorm, I use a wired Ethernet LAN connection (as in I connect to the school's wired network and thus get my Internet). With just the cable plugged in, the Internet works fine which is great. However at random times (usually in a 15-20min period or when I'm downloading) the Internet disconnects. And then I have to wait another 15min period and it connects again. Anyone know how to fix it? I can't find any configuration window or anything.

Secondly, it's my wireless connection. I have Intel's integrated Wireless chip (I have T2500 Core Duo chip, so whatever comes with that). I don't want it enabled or connected to a connection when I'm plugged in via Ethernet, but I do want it to connect to a preffered network ('cause there are many available ones but only one good one), when I'm disconnected. Currently the only way I can see is to manually input the SSID and hope it connects (which it doesn't). Is there any GUI tool that allows me to connect and is there any settings I can change so that it will connect to a preffered network when I'm not on ethernet?

Sorry for being such a n00b. 

PS: Speaking of n00bs, what's the <super> key?

---

### Post by Mr. C. on 2007-03-15
Let's take one at a time.  Wired.

When you say "disconnected", what exactly do you mean ?

Does ping to some IP address work from a terminal window when it seems "disconnected"?  Do you have an IP address during that time ?  Perhaps you are talking about browsing troubles?

MrC

---

### Post by royrules22 on 2007-03-16
Yes I have an IP address
I can ping my own ip address (169...)
I cannot ping anything else
Nothing loads in Firefox

---

### Post by Mr. C. on 2007-03-16
> **royrules22 said:**
> Yes I have an IP address
I can ping my own ip address (169...)
I cannot ping anything else
Nothing loads in Firefox

With that IP address, you never will.

The 169.254.xx.xx addresses are private local link addresses.  They are used when there is no static IP configuration and no dynamic IP service such as DHCP is found or available.

Your system is not obtaining its dynamic IP.  This typically indicates there is no communication with a router or other device.

A host can always ping itself.  Don't be fooled into thinking this means your network is working.  It only means your "loopback" network is working.  Its like talking to one's self - not much of a conversation.

Since you say that you do get internet access, my guess is either a faulty cable, faulty router (if you have one), or a faulty network card.  Your NIC is loosing the connection for some reason.

MrC

---

### Post by royrules22 on 2007-03-16
Ok first of all the IP address is 169.229.72.15 and dns lookup will tell you that it is che-72-15.Reshall.Berkeley.EDU which is appropriate because I'm in a dorm at UC Berkeley right now. And I realize pinging myself is useless, I was just listing everything. As for faulty cable or card, that cannot be simply because I'm on Windows right now and there is absolutly no problem whatsoever with my NIC. It's just in Linux. Which makes me thing it's some setting or driver issue.

---

### Post by Mr. C. on 2007-03-16
Don't get huffy.  I tried to make some educated guesses, based upon your incomplete information, and misleading guesses.  I cannot read the crystal ball, and I have no idea what your sophistication level is with computers.  And DNS can't tell me anything about "169..."

There is no shutdown-the-NIC-connection-every-15-minutes setting.

If you believe are losing connection due to a driver issue, examine syslog for anomalies.  Drivers don't just start and stop willy-nilly.  The log messages when problems exist.

Examine your ethernet stats.  You seem to know about these things.  What sorts of errors do you see?  How do your NIC stats look?

MrC

---

### Post by royrules22 on 2007-03-16
I'm sorry for acting like a jack***, I'm a bit like Chloe 'O Brian and Edgar Stiles w/o the smartness at times. It's just that I [can't boot into Ubuntu]("http://www.ubuntuforums.org/showthread.php?p=2305939#post2305939"). And I apologize for the 169.. thing (I figured that you could guess that it was an external IP and it didn't really matter what it was. Guess I didn't realize that there exists a set of address begining with 169 that are private-link address. My bad). 

In any case, I actually don't know much about how everything runs in Linux. I can find the information in Windows but not without help in Linux. However I remember reading t[his thread]("http://ubuntuforums.org/showthread.php?t=252286") and running *ethtool -s eth0 autoneg off* and it telling me that my card didn't have that setting (I don't have the exact wording since I can't boot into it right now).

---

### Post by Mr. C. on 2007-03-16
Ok, when you get back to booting, let's have a look at:
```

ifconfig -a
lshw -C network
ethtool -S eth0  # change to what interface you use
```

Good luck with the boot,
MrC

---

### Post by royrules22 on 2007-03-16
> **Mr. C. said:**
> Ok, when you get back to booting, let's have a look at:
```

ifconfig -a
lshw -C network
ethtool -S eth0  # change to what interface you use
```

Good luck with the boot,
MrC

Ok here we go.

ifconfig gives:

```
eth0      Link encap:Ethernet  HWaddr 00:17:31:3F:9A:08  
          inet addr:169.229.72.15  Bcast:169.229.72.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe3f:9a08/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3612 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1637 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1783908 (1.7 MiB)  TX bytes:257433 (251.3 KiB)
          Interrupt:169 Base address:0xc800 

eth1      Link encap:Ethernet  HWaddr 00:13:02:6F:9D:CB  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5111 errors:0 dropped:3851 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Base address:0x8000 Memory:fe1ff000-fe1fffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:140369 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140369 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:111366168 (106.2 MiB)  TX bytes:111366168 (106.2 MiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

lshw:

```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 01
       serial: 00:17:31:3f:9a:08
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r1000 ip=169.229.72.15 multicast=yes
       resources: ioport:c800-c8ff iomemory:fe0ff000-fe0fffff irq:169
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth1
       version: 02
       serial: 00:13:02:6f:9d:cb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 multicast=yes wireless=unassociated
       resources: iomemory:fe1ff000-fe1fffff irq:177
  *-usb
       description: Bluetooth wireless interface
       vendor: ASUSTek Computer, Inc.
       physical id: 2
       bus info: usb@2:2
       version: 19.15
       serial: 0194E8-5B-0002
       capabilities: bluetooth usb-2.00
       configuration: driver=hci_usb maxpower=0mA speed=12.0MB/s

```

and..

```
nakul@nakul-laptop:~$ ethtool -S eth0
Cannot get driver information: Operation not permitted

```

also..

```

nakul@nakul-laptop:~$ ethtool -s eth0 autoneg off
Cannot get current device settings: Operation not permitted
  not setting autoneg

```

---

### Post by royrules22 on 2007-03-16
anyone?

---

### Post by Mr. C. on 2007-03-16
All those permission denied and "you should run this program as super-user" mean you need to run them as root.

tack **sudo **onto the front of each command, or open a root shell with 

```
sudo -s
```

and then type the commands in.

MrC

---

### Post by royrules22 on 2007-03-16
Nope:

```

root@nakul-laptop:~# ethtool -S eth0
Cannot get driver information: Operation not supported
root@nakul-laptop:~# ethtool -s eth0 autoneg off
Cannot get current device settings: Operation not supported
  not setting autoneg

```

:(

---

### Post by Mr. C. on 2007-03-16
Ok, so no ethtool capabilities in that driver.

There are several drivers available for the realtek chip.  Which module are you using:

```
sudo lspci
sudo lspci -n
sudo lsmod
```


Also, disable IPv6:

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

MrC

---

### Post by royrules22 on 2007-03-17
```

nakul@nakul-laptop:~$ sudo lspci
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
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 71c5
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8168 (rev 01)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
06:01.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
06:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
06:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
06:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

```

```

00:00.0 0600: 8086:27a0 (rev 03)
00:01.0 0604: 8086:27a1 (rev 03)
00:1b.0 0403: 8086:27d8 (rev 02)
00:1c.0 0604: 8086:27d0 (rev 02)
00:1c.1 0604: 8086:27d2 (rev 02)
00:1c.2 0604: 8086:27d4 (rev 02)
00:1d.0 0c03: 8086:27c8 (rev 02)
00:1d.1 0c03: 8086:27c9 (rev 02)
00:1d.2 0c03: 8086:27ca (rev 02)
00:1d.3 0c03: 8086:27cb (rev 02)
00:1d.7 0c03: 8086:27cc (rev 02)
00:1e.0 0604: 8086:2448 (rev e2)
00:1f.0 0601: 8086:27b9 (rev 02)
00:1f.2 0101: 8086:27c4 (rev 02)
01:00.0 0300: 1002:71c5
02:00.0 0200: 10ec:8168 (rev 01)
03:00.0 0280: 8086:4222 (rev 02)
06:01.0 0c00: 1180:0832
06:01.1 0805: 1180:0822 (rev 19)
06:01.2 0880: 1180:0843 (rev 01)
06:01.3 0880: 1180:0592 (rev 0a)
06:01.4 0880: 1180:0852 (rev 05)

```

```

Module                  Size  Used by
arc4                    3200  2 
ieee80211_crypt_wep     6528  1 
ipv6                  272288  12 
binfmt_misc            13448  1 
rfcomm                 42260  0 
hidp                   34176  3 
l2cap                  27136  14 rfcomm,hidp
fglrx                 406988  36 
speedstep_centrino      9760  1 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  2 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sbs                    16804  0 
sony_acpi               6412  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
i2c_core               23424  1 i2c_ec
hotkey                 11556  0 
dev_acpi               12292  0 
button                  7952  0 
battery                11652  0 
container               5632  0 
ac                      6788  0 
asus_acpi              17688  0 
nls_utf8                3200  2 
ntfs                  112116  2 
nls_iso8859_1           5248  1 
nls_cp437               6912  1 
vfat                   14720  1 
fat                    56348  1 vfat
af_packet              24584  4 
sbp2                   24584  0 
parport_pc             37796  0 
lp                     12964  0 
parport                39496  2 parport_pc,lp
snd_hda_intel          23192  1 
snd_hda_codec         223104  1 snd_hda_intel
joydev                 11200  0 
snd_pcm_oss            47616  0 
snd_mixer_oss          19584  1 snd_pcm_oss
sr_mod                 18212  0 
ipw3945               124576  1 
tsdev                   9152  0 
cdrom                  38944  1 sr_mod
sg                     37404  0 
r1000                  17792  0 
snd_pcm                85892  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
ieee80211              35272  1 ipw3945
ieee80211_crypt         7552  2 ieee80211_crypt_wep,ieee80211
sdhci                  20108  0 
mmc_core               32136  1 sdhci
hci_usb                18068  3 
snd_timer              25220  1 snd_pcm
snd                    65288  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11656  2 snd_hda_intel,snd_pcm
bluetooth              53476  8 rfcomm,hidp,l2cap,hci_usb
shpchp                 42144  0 
tpm_infineon            9496  0 
tpm                    17568  1 tpm_infineon
psmouse                41352  0 
irda                  214332  0 
crc_ccitt               3200  1 irda
tpm_bios                8832  1 tpm
serio_raw               8452  0 
pci_hotplug            32828  1 shpchp
intel_agp              26012  1 
agpgart                34888  2 fglrx,intel_agp
pcspkr                  4352  0 
evdev                  11392  1 
ext3                  142856  1 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
uhci_hcd               24968  0 
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
ide_generic             2432  0 
usbcore               134912  4 hci_usb,ehci_hcd,uhci_hcd
sd_mod                 22656  6 
generic                 6276  0 
ata_piix               11780  5 
libata                 74892  1 ata_piix
scsi_mod              144648  5 sbp2,sr_mod,sg,sd_mod,libata
thermal                15624  0 
processor              31560  2 speedstep_centrino,thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

```

---

### Post by royrules22 on 2007-03-17
er...

---

### Post by Mr. C. on 2007-03-17
royrules22,

The driver you need for your eth0 Realtek chip is the r8169.   This device ( 8168 ) was not supported in the kernel that you booted:
> 02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8168 (rev 01)

There have been a number of bug fixes to this driver in the latest 3 kernel releases of 2.6.20.{1,2,3}, but an even more important fix is only available in the 2.6.21-rc4 pre-patch version of the kernel.

```
  r8169: revert bogus BMCR reset
    
    The current code requests a reset but prohibits autoneg, 1000 Mb/s,
    100 Mb/s and full duplex. The 8168 does not like it at all.
    
```

If you want your eth0 device to function, you are going to need to update to at least this version of the kernel.  Support for this device begain in the 2.6.19 kernel, but has had several important fixes since.  If you want to run this kernel, run at least kernel 2.6.20 + the patches required for 2.6.21-rc4.  There are two patches, one only to the r8169 driver, and one which benefits that driver but also is used for others.  I do not know the interdependencies of the patch, so taking only two of the patches may not work.

Once you've upgraded to this kernel, things will most likely work fine.  If you want to go with the already built 2.6.20 kernel, you can configure your NIC to work in 10mbs mode instead and that may work as well.


MrC

---

### Post by royrules22 on 2007-03-17
Quick question, you mean the linux kernel itself? Is there no way to just plain old update the driver?

---

### Post by chili555 on 2007-03-17
I think ethtool wants you to call her sweetheart....er, I mean sudo, before she will play. **sudo** ethtool <command>

> Is there no way to just plain old update the driver?If someone has written a second-party driver, then yes. If not, you have no way to get a better driver than a better kernel.

Installing a new kernel is painless. Mr.C and I love to scare the noobs with it, but we haven't hurt one yet. If you have a CDRW on that Windows machine, we can direct you what to download, You can burn the CD, boot into linux and install. If Mr.C has not crossed his fingers and toes tight enough and it all goes wrong (highly unlikely), you can boot into your current kernel and erase 2.6.20. By the way, I am running 2.6.20-5-generic on This Old Laptop and it works fine.

If you'd like to get started, put on your safety glasses and issue the command: ```
dpkg -l | grep linux
``` Among other things, it will tell us what version of linux image we need to match (generic, i386, etc.), if you need linux-headers and linux-restricted-modules. 

Let's go!

---

### Post by Mr. C. on 2007-03-17
You will likely need to build the kernel.

Chili - I've believe that prepatch 2.6.21-rc4 is required to obtain a complete fix, so building against 2.6.20.3 with that prepatch should be sufficient.

MrC

---

### Post by mzlizzy on 2007-03-17
I'm a novice.  But, I would find ***autoneg** *& turn it on.  Seems like you got it if it's off; just turn it on somehow, I guess.  Don't you think?  Good luck!

---

### Post by mzlizzy on 2007-03-17
Just turn on the autoneg, I guess.  I'm just a novice but it only makes sense; seems you have an autoneg.  Good luck!

---

### Post by Mr. C. on 2007-03-17
> **mzlizzy said:**
> I'm a novice.  But, I would find ***autoneg** *& turn it on.  Seems like you got it if it's off; just turn it on somehow, I guess.  Don't you think?  Good luck!

Doubtful.  It would be safe to say that all Ethernet hardware today supports auto-negotiation, and it is enabled by default.

More likely, the OP would need to *disable* auto-negotiation to set a lower speed such as 10mbit.  This can be done either with driver options (options passed to the driver during NIC startup) or for some cards, via firmware.

Tools like ethtool allow changing such parameters, should the driver support the ethtool interface.

MrC

---

### Post by royrules22 on 2007-03-18
Ok autoneg is not off. I can't get ethtools to work even with sudo. My card has no problem with high speeds because it works in WinXP. It's not an old system (I bought it August 06). Also now at home my wired connection works flawlessly, unlike at dorm. The only difference is that at home it's a plain old DSL while at college it is I believe a T3 with insane speeds.

Also my wireless works perfectly at home (in fact I'm using it now). I would just like to have a GUI configuration tool that automatically shows what networks are available, etc just like the Windows one.

---

### Post by Mr. C. on 2007-03-18
Comparisons to Windows are only useful enough to affirm it can work, not that it should.  The drivers are completely different, as is the entire network stack.

Simply disabling auto-negotiation is not enough to guarantee 10Mpbs.  That has to be manually configured.  Link speed must then be verified once the NIC is operational.  Regardless, my the suggestion here was to attempt reducing the speed of the NIC to determine of that bypassed the problem.  It was also intended to counter the arbitrary (and wrong) suggestion by the previous poster about *enabling* auto-negotiation.  As you discovered, it was already enabled - no surprise.

Ethtool requires the driver to support it.  If the driver has no ethtool code, it can't work.

I do not have my Ununtu system currently booted; check to see if **man mii-tool** gives you a pointer to an alternate interface

I spent a considerable amount of time yesterday evaluating the changes to the driver you need, in half  a dozen kernel releases and patches.  Without obtaining the updates I suggested, there is not much more that can be done.

MrC

---

### Post by royrules22 on 2007-03-22
Sorry for the delay but everything works now w/o me doing anything.. too weird.

---

