---
title: "Can't get eth0 to get a DHCP addr"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by Bob3 on 2007-04-16
I have a laptop which I installed Ubuntu (6.10) on. Where I did the install all I had was dialup phone line so when it came to internet connect that's what I setup. And all was working fine.
Now I'm back home and I have cable modem and a D-link router and I just can't seem to make it get a DHCP address like it should. When I run the Ubuntu live CD it comes up and the eth0 connection works just fine.

Here is some information about my system: uname -a
Linux holetooth2 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux

When I run ifconfig eth0 I get:
eth0 Link encap:Ethernet HWaddr 00:A0:D1:2C:24:B1
inet6 addr: fe80::2a0:d1ff:fe2c:24b1/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:63 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:10 Base address:0x2000

cat /etc/network/interfaces gives me:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp

dhclient eth0 gives:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:a0:d1:2c:24:b1
Sending on LPF/eth0/00:a0:d1:2c:24:b1
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

and finally ethtool eth0 gives me:
Settings for eth0:
Supported ports: [ TP MII ]
Supported link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
Supports auto-negotiation: Yes
Advertised link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
Advertised auto-negotiation: Yes
Speed: 100Mb/s
Duplex: Full
Port: MII
PHYAD: 32
Transceiver: internal
Auto-negotiation: on
Supports Wake-on: pumbg
Wake-on: d
Current message level: 0x00000007 (7)
Link detected: yes

I feel I must have done something when I setup the original dialup because when I run the Ubuntu live CD it comes up and the eth0 connection works just fine. It uses DHCP just like I'm trying to do and the interface file is the exact same.
Please let me know if you need more info and thanks inadvance for the help. Much appreciated.

Regards,
Bob

---

### Post by Floppyjoe on 2007-04-16
Are you trying to get a Wired or wireless connection working?
If wireless please post the result of:
```
lspci
```

---

### Post by arizal on 2007-04-16
I had similar problem after installing ubuntu,
Finaly I found that the eth0 link was down after boot.
The switch showed connection but the my laptop thought there was no link.
The solution was to modprobe -r r8169 and than to load it again.
This fixes the link problem,
Dont know if your problem is the same but at least u can try this.
Also check the output of 'dmesg'.

---

### Post by dbott67 on 2007-04-16
Can you also post the output of:
```
dbott@feisty:~$ [COLOR=Red]**sudo lshw -C network**[/COLOR]
Password:
  *-network               
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: b
       bus info: pci@02:0b.0
       logical name: eth0
       version: 10
       serial: 00:50:ba:c0:a7:55
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.106 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:b000-b0ff iomemory:be800000-be8000ff irq:17

```

-Dave

---

### Post by Bob3 on 2007-04-16
First off thanks for the replies.

Secondly, no this isn't wireless. I'll try to get that working once I've wired working.
I did run a lspci cmd to file which I have attached (I hope I did it correctly)

And finally the output of the sudo lshw -C network command is:
  *-network:0 DISABLED
       description: Wireless interface
       product: AR5005G 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 4
       bus info: pci@02:04.0
       logical name: wifi0
       version: 01
       serial: 00:11:f5:c8:87:33
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.2.1) multicast=yes wireless=IEEE 802.11b
       resources: iomemory:c0200000-c020ffff irq:11
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@02:07.0
       logical name: eth0
       version: 10
       serial: 00:a0:d1:2c:24:b1
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:a000-a0ff iomemory:c0211000-c02110ff irq:10

and I did try the modprobe but that didn't seem to change anything even after I did a networking restarted.

Still seems funny to me that the Live CD is working but because I didn't install the system with ethernet it doesn't work.

Regards,
    Bob

---

### Post by dbott67 on 2007-04-17
Hi Bob,

Your network card is a RealTek RTL-8139 and should use the same driver as mine (which is a D-Link 538 that uses the RTL8139 chipset).

If you notice the last line of your 'lshw -C network' output, it shows that the card is using the 8139too driver:
```
configuration: autonegociation=on broadcast=yes [COLOR=Red]**driver=8139too**[/COLOR] driverversion=0.9.27 duplex=full link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:a000-a0ff iomemory:c0211000-c02110ff irq:10
```Let's check to see if the driver is loaded.  My computer uses the same driver, so I run 'lsmod | grep 8139' and it shows that the driver is loaded:
```
dbott@feisty:~$ lsmod | grep 8139
8139too                26112  0
mii                     5632  1 8139too

```Having said all that, I have noticed a few threads where people are having difficulties with the RealTek cards.

There are 3 things that you can try, 2 of which won't cost any money:

**1. You can try disabling some options at boot time by editing grub:**
[https://help.ubuntu.com/community/DebuggingIRQProblems](https://help.ubuntu.com/community/DebuggingIRQProblems)

> **How do I know there is a problem?**

The following are some symptoms which may indicate an IRQ-related problem:

    * [COLOR=Blue]Hardware devices being detected, but not functional[/COLOR] (sound, [COLOR=Blue]network[/COLOR], etc.)
    * Problems using two hardware devices at the same time, or only when devices are connected at the same time.
    * System hangs (lockup).

**What do I do?**

If you think you may be experiencing such a problem, [COLOR=Blue]try these steps in order[/COLOR]:

    * Boot the system with the [COLOR=Red]noapic[/COLOR] boot parameter
    * Boot the system with the [COLOR=Red]pci=routeirq[/COLOR]
    * Boot the system with the [COLOR=Red]pci=noacpi[/COLOR] boot parameter
    * Boot the system with the [COLOR=Red]acpi=off[/COLOR] boot parameter

To add these options to the boot command line, use the [COLOR=Red]edit[/COLOR] option in the [COLOR=Red]grub boot menu[/COLOR]. Full instructions on how to use grub:
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

**2. Blacklist the 8139too driver and use ndiswrapper.**

I use ndiswrapper on my laptop and have some specific instructions that relate to Broadcom:
[http://ubuntuforums.org/showthread.php?t=274915](http://ubuntuforums.org/showthread.php?t=274915)

Read the part called 'Broadcom Wireless' and follow steps 1-4, however, you would blacklist [COLOR=Red]8139too[/COLOR], not the [COLOR=Red]bcm43xx[/COLOR].

Steps 5 & up are not required, as you're not using wireless.

** 3. Buy a new NIC ($)**

I would suggest trying #1 & 2 first, as they are free and pretty easy to test.  If you happen to have a spare NIC lying around, you may just want to swap it out.
-Dave

---

### Post by Bob3 on 2007-04-17
Thanks Dbott67,

I tried the lsmod command and got this:
gtoo@holetooth2:~$ lsmod | grep 8139
8139cp                 24832  0 
8139too                29056  0 
mii                     6912  2 8139cp,8139too

I'm guessing that the 8139cp is for my modem?
Anyway how do I get rid of it. You mentioned blacklisting but I really don't know how to do that.

Thanks for the help.

Regards,
      Bob
PS: I noticed you are from Ontario. I am too, in Ajax.

---

### Post by dbott67 on 2007-04-17
Hi Bob,

Nice to meet a fellow Ontarian here.

A couple of caveats first:

1.  Did you try the noapic and other boot options first?

If they failed to work, then we can move on to ndiswrapper:

2. Installing ndiswrapper requires getting some packages or drivers from online.  Obviously, if you can't get online with your current setup, how the hack are you going to get online to fix it?  If you've got another working machine, you can download the drivers to floppy or USB and then bring them over to your Ubuntu machine first.

3. The ndiswrapper package should be on the installation CD, so you should be okay to install it using Synaptic or apt-get.

_**GETTING STARTED**_

Before you begin, can you please post the output of lspci, so that we can find the PCI ID of your NIC:
```
dbott@feisty:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 12)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 12)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)
02:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
02:0a.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
[COLOR=Red][COLOR=Blue]02:0b.0[/COLOR] Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)[/COLOR]
02:0d.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
02:0d.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
02:0d.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
02:0d.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)

```With this information, we then run the command 'lspci -n':
```
dbott@feisty:~$ lspci -n
00:00.0 0600: 8086:1a30 (rev 03)
00:01.0 0604: 8086:1a31 (rev 03)
00:1e.0 0604: 8086:244e (rev 12)
00:1f.0 0601: 8086:2440 (rev 12)
00:1f.1 0101: 8086:244b (rev 12)
00:1f.2 0c03: 8086:2442 (rev 12)
00:1f.3 0c05: 8086:2443 (rev 12)
00:1f.4 0c03: 8086:2444 (rev 12)
00:1f.5 0401: 8086:2445 (rev 12)
01:00.0 0300: 1002:4150
01:00.1 0380: 1002:4170
02:0a.0 0401: 1102:0002 (rev 07)
02:0a.1 0980: 1102:7002 (rev 07)
[COLOR=Red][COLOR=Blue]02:0b.0 0200:[/COLOR] 1186:1300 (rev 10)[/COLOR]
02:0d.0 0c03: 10b9:5237 (rev 03)
02:0d.1 0c03: 10b9:5237 (rev 03)
02:0d.2 0c03: 10b9:5237 (rev 03)
02:0d.3 0c03: 10b9:5239 (rev 01)

```This allows us to go to the "[official ndiswrapper lis]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")t" and get the correct driver.  In my case, I would search the page for "[COLOR=Red]1186:1300[COLOR=Black]" (yours will be different).

_**BLACKLISTING**_
[/COLOR][/COLOR]
Anyhow, to blacklist a module, you just have to add it to the blacklist (go figure).

To look at your current blacklist, you can use this command:
```
dbott@feisty:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187

```You can see that the developers already have a few modules listed.  What you need to do is add the command 'blacklist 8139too' to the bottom.  You can open the file with gedit and just add it to the bottom:
```
sudo gedit /etc/modprobe.d/blacklist
```Add this to the bottom:
```
# Built-in wired ethernet Realtek 8139 --- added by Bob from Ajax!
blacklist 8139too
blacklist 8139cp
blacklist mii

```and save the file.

**REBOOT.**

[COLOR=Red]*Just be sure to make note that you have blacklisted the module, because the developers may fix it in a future kernel release and you would want to remove it.*[/COLOR]

Next, you can download & install ndiswrapper from the CD/repos:
```
sudo apt-get install ndiswrapper-common
```According to the ndiswrapper list, you probably need this driver (we can confirm with the output of lspci & lspci -n):
> Laptop: Toshiba M55-S1001 (rtl8139c wired ethernet)

    * Chipset: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    * pccid: 0000:04:06.0 0200: 10ec:8139 (rev 10)
    * Driver: Originally from [295] Toshiba driver does not work by default! Use this [driver]("http://www.voxpopulimedia.com/pub/ToshibaM55-rtl8139-WinXP-ndis.tar.gz") [296] modified file instead!
    * Other: Switched to ndis driver because standard driver (8139too) has problem with timing out on large files. Tested working on Ubuntu Dapper Drake. Before installing, unload existing 8139too and other drivers with "sudo rmmod 8139cp 8139too mii" 

Save the Windows drivers from the link to your home directory and unpack them.  There should be a [COLOR=Blue]NetopOEM.inf[/COLOR] & [COLOR=Blue]Rtlnicxp.sys[/COLOR] file now saved in your home directory.

Now load the driver from your home directory:
```
sudo ndiswrapper -i NetopOEM.inf
```Verify that it loaded:
```
ndiswrapper -l
```You should see something like:
```

NetopOEM: driver installed
        device (14E4:4320) present
```Next create the module dependencies:
```
sudo depmod -a
```Then load ndiswrapper:
```
sudo modprobe ndiswrapper
```There will be some final tweaking depending on the output.  Open a terminal and type:
```
ifconfig -a
```Look for the serial number[COLOR=Red] 00:a0:d1:2c:24:b1[COLOR=Black] and the logical interface name (eth0, eth1, eth2, etc. [/COLOR][/COLOR]Note that ndiswrapper may change the logical name of your NIC).
Then try activating the appropriate interface:
```
sudo ifup eth0
```Good luck,
Dave

---

### Post by Bob3 on 2007-04-18
Dbott67,
Actually I have noacpi already turned on. I had problems with my USB mouse and that solved it.

I went back and read your link to see how blacklists could be used to rid myself of 8139cp. That worked fine but apparently wasn't the problem. The 8139cp entry is gone but even with a reboot my problem remains,

I'm resisting the wrappers options as I was running 6.06 before with no problems and when I run 6.10 live CD I have no problems. So I feel I must have caused the problem when I setup dial up. Though what I did I can't seem it find.

I'll play with it for a few more days and if I still can't get it to work I'll backup the Home files and re-install. This will, in all likelihood, fix my network problem. Then all I have to do is spend 3 or 4 days putting everything back together.

But I want to thank you for all your efforts. They are much appreciated. I really enjoyed learning about the backlist process. I've made a copy of the instructions. You never know when I could use that information.

So it was nice to meet someone else from Ontario, take care and thanks again,
Regards,
     Bob

---

### Post by nspires66 on 2007-04-18
Hi Bob3

Im a newbe at this but I was having prety much the same problem and I just got it fix, (after much hair pulling). I had been bouncing back and forth between several Freespire and Ubuntu distros and only my old beta version of Freespire would see any of my 3 wireless cards (one internal and 2 usb). Anyway I just put in the Ubuntu cd and it recognized that there were uninstalled packages on it and opened up the utility to install them. I scrolled through the entire list and checked the few that I thought I needed and one had something to do with wireless networking that was not installed originaly. After installing everything I wanted I rebooted and whala my USB adapter was recognized and all I had to do was configure it. 

Like I said Im new to this and dont know if this will help but Im extatic that I got mine to work.

Have a good one
Tex

---

### Post by dbott67 on 2007-04-18
> **Bob3 said:**
> ... when I run 6.10 live CD I have no problems...

Hi Bob,

One thing you can try:

Boot from the Live CD and print out or save to file the output of the following commands:
```
lsmod
```
```
ifconfig -a
```
```
cat /etc/network/interfaces
```
```
sudo lshw -C network
```

These commands contain the key information about your network configuration and which drivers are loaded.

Compare the Live CD version with the installed version and make note of any differences (loaded modules, driver version #, config settings, etc.) and edit the appropriate files accordingly.

If you can post the output of the above commands from the Live CD and from your installed version, I can help.

-Dave

---

### Post by Bob3 on 2007-04-19
Dave,
Thanks for your reply and continued efforts to help me.

I've uploaded the max 5 files. The first 4, all filenames starting with disk, are from my current system.
The final file starts with live and is from the Ubuntu live 6,10 CD. My current system is 6,10 so everything should be comparable.
I will send the other 3 files in a follow-up post.
The second part of each filename is the command so you will likely have no problem sorting them out.

I looked at each file and the only thing I noticed was with the lshw command.
In the live file the eth0 IRQ was 209 while in the disk file the IRQ was 10.
There was too much in the lsmod command for me to see anything other than the disk file doesn't have the 8139cp in it. But that would be because I blacklisted it hoping that would solve my problem. It didn't.

So thanks again for the help,
Regards,
         Bob

---

### Post by Bob3 on 2007-04-19
Dave,
Here is the follow up post to give you the remaining 3 live files.
Regards,
      Bob

---

### Post by dbott67 on 2007-04-19
Hi Bob,

I see the IRQ differences that you point out (for ath0 and eth0).  The other difference may be related to kernel version.  Can you post the output of 'uname -a' from both the Live & installed versions.
```
dbott@feisty:~$ uname -a
Linux feisty 2.6.20-15-386 #2 Sat Apr 14 00:50:49 UTC 2007 i686 GNU/Linux

```
I'm willing to bet that there's been a kernel update to the installed version that has somehow crippled the NIC.

-Dave

---

### Post by Bob3 on 2007-04-19
Dave,

OK I did some checking of the logs and found some curious things,
But first the uname info:

For installed:
Linux holetooth2 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux

For live:
Linux ubuntu 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux

I've also attached the various log files from /var/log 
You may look at them and see things I don't but I saw disk I/O errors and a lot of DHCP errors.
But if you will, take a look and see what you see.

Regards,
       Bob

---

### Post by dbott67 on 2007-04-20
Hi Bob,

I took a look at the logs, but I can't really make heads nor tails out of what the problem might be.  My only suggestion to try before trying a different NIC would be this:

In grub (located in /boot/grub/menu.lst) there is a list of all previously installed kernels that you can boot from:
```
dbott@feisty:/boot/grub$ cat menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

[COLOR=Red] ## default num[/COLOR]
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
[COLOR=Red] default         0[/COLOR]

[I][COLOR=DarkOrchid]## ...
## Lots of other stuff snipped for brevity
## ...[/COLOR][/I]

## ## End Default Options ##

[COLOR=Red]_*# This is default  0*_
title           Ubuntu, kernel 2.6.20-15-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-386 root=UUID=ffed2999-c91c-4121-8b8a-68706665bf2f ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-386
savedefault[/COLOR]

title           Ubuntu, kernel 2.6.20-15-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-386 root=UUID=ffed2999-c91c-4121-8b8a-68706665bf2f ro single
initrd          /boot/initrd.img-2.6.20-15-386

[COLOR=Blue]_*# This is default  2*_
title           Ubuntu, kernel 2.6.20-14-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-14-386 root=UUID=ffed2999-c91c-4121-8b8a-68706665bf2f ro quiet splash
initrd          /boot/initrd.img-2.6.20-14-386
savedefault[/COLOR]

title           Ubuntu, kernel 2.6.20-14-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-14-386 root=UUID=ffed2999-c91c-4121-8b8a-68706665bf2f ro single
initrd          /boot/initrd.img-2.6.20-14-386

title           Ubuntu, kernel 2.6.17-11-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-386 root=UUID=ffed2999-c91c-4121-8b8a-68706665bf2f ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-386
savedefault

title           Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-386 root=UUID=ffed2999-c91c-4121-8b8a-68706665bf2f ro single
initrd          /boot/initrd.img-2.6.17-11-386

title           Ubuntu, kernel 2.6.15-28-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-28-386 root=UUID=ffed2999-c91c-4121-8b8a-68706665bf2f ro quiet splash
initrd          /boot/initrd.img-2.6.15-28-386
savedefault

title           Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-28-386 root=UUID=ffed2999-c91c-4121-8b8a-68706665bf2f ro single
initrd          /boot/initrd.img-2.6.15-28-386

title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=UUID=ffed2999-c91c-4121-8b8a-68706665bf2f ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault

title           Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=UUID=ffed2999-c91c-4121-8b8a-68706665bf2f ro single
initrd          /boot/initrd.img-2.6.15-27-386

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=UUID=ffed2999-c91c-4121-8b8a-68706665bf2f ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=UUID=ffed2999-c91c-4121-8b8a-68706665bf2f ro single
initrd          /boot/initrd.img-2.6.15-26-386

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

```By default, it loads "default  0" or the first item on the list (scroll down to the part in red).  You could change 'default  0' to read 'default  2' (in blue) if you wanted to load the previous kernel.  In my case, it would load 2.6.20-14-386 instead of 2.6.20-15-386.

Just look through your list of kernels for **Ubuntu, kernel 2.6.17-10-generic #2** and set it as default.

I hope it works.

-Dave

---

### Post by dbott67 on 2007-04-21
> **dbott67 said:**
> **1. You can try disabling some options at boot time by editing grub:**
[https://help.ubuntu.com/community/DebuggingIRQProblems](https://help.ubuntu.com/community/DebuggingIRQProblems)

Full instructions on how to use grub:
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

Hi Bob,

Someone with the same card posted success with setting acpi=off for the realtek card.

[http://ubuntuforums.org/showthread.php?t=402236&highlight=realtek+8139+problems](http://ubuntuforums.org/showthread.php?t=402236&highlight=realtek+8139+problems)

You may want to give it another try with this option.

-Dave

---

### Post by Bob3 on 2007-04-21
Dave,

Sorry to be gone so long. I have been busy with other things but I also tried what you suggested with using a different kernel. My main kernel is 2.6.17-11 but I also have 2,6,17-10 installed too.
When I booted with 17-10 there was still no joy. So I tried removing Firestarter (firewall app) and while I was at it I took out the noacpi kernel parameter. And suddenly there was joy - a wonderful internet connection.
So it must have been the firewall, right. Well I put the noacpi parm back in and rebooted.
And you guessed it not internet. So the issue is the noacpi parm.
I put the parm in to resolve an issue last fall with Ubuntu 6.06. The issue was that my USB mouse would just stop working. I checked the forums and one of the said to add the parm to the kernel as others have been having problems too but this would solve everything. Which it did at the time.
So now I've been googling trying to find other options to have both my USB ports and my internet working. I've found a number of options to try (“noapic nolapic pci=noacpi acpi=off”), now it will just take time to try the various items and combos.
I'll also read the things you posted plus try try disabling some options at boot time.
I see you saw someone has success with acpi=off. Thats one of the items I'll be trying.
Well I guess we solved the initial problem so I want to thank you again for hanging in there with me. You may find we asking the group for help again if I can't get the USB mouse working. But that's another forum.
Thanks again,
Regards,
       Bob

---

### Post by obz on 2007-04-22
> **Bob3 said:**
> Dave,

Sorry to be gone so long. I have been busy with other things but I also tried what you suggested with using a different kernel. My main kernel is 2.6.17-11 but I also have 2,6,17-10 installed too.
When I booted with 17-10 there was still no joy. So I tried removing Firestarter (firewall app) and while I was at it I took out the noacpi kernel parameter. And suddenly there was joy - a wonderful internet connection.
So it must have been the firewall, right.

How did you uninstall the Firewall? Through add/remove programs? I'm having similar problems and would like to see if this may be the issue. I search for it in Add/Remove and didn't find it.

---

### Post by dbott67 on 2007-04-22
Hi obz,

The firewall front-end GUI is known as Firestarter (although there are others available); the backend is called 'iptables'.

You can check the status by typing:
```
dbott@feisty:~$ sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
```If your output is the same as mine, there is no firewall in effect.

Actually, I think Bob3 ***thought*** it was the firewall, but it turns out that it was the 'noacpi' kernel parameter (he disabled the firewall at the same time as booting with noacpi).

Follow [these instructions]("https://help.ubuntu.com/community/GrubHowto#head-28c697721b2f5d2352e43074a55f4621c415293d") carefully for details on how to add the options.

You will have a line in your [COLOR=Blue]**/boot/grub.menu.lst**[/COLOR] file that looks similar to his:
```
# kopt=root=UUID=ffed2999-c91c-4121-8b8a-68706665bf2f ro
```
Add the 'noapci' option to the end, save the file and then run 'sudo update-grub':
```
# kopt=root=UUID=ffed2999-c91c-4121-8b8a-68706665bf2f ro [COLOR=Red]noapic[/COLOR]
```If this fails, try each of the other options starting with 'acpi=off':
```
# kopt=root=UUID=ffed2999-c91c-4121-8b8a-68706665bf2f ro [COLOR=Red]acpi=off[/COLOR]
```Let us know.

-Dave

---

### Post by obz on 2007-04-22
my iptables are the same as yours.

tried :
# kopt=root=UUID=ffed2999-c91c-4121-8b8a-68706665bf2f ro noapic

did nothing.

tried :
# kopt=root=UUID=ffed2999-c91c-4121-8b8a-68706665bf2f ro acpi=off

did nothing.

:(

---

