---
title: "Wireless Connection"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by kevb8ll on 2008-11-20
I can't get my wireless connection to work. I previous was hard wired into my router and that worked with out a problem.

I'm a newbie to kubuntu and would appreciate help.

I also appreciate that you prob get asked questions like this regularly. I tried following some instruction that looked like it was a similar problem - but it didn't seem to work.

I have 8.04 and using KDE4

Thanks

---

### Post by kevb8ll on 2008-11-21
Can anyone help me with this please?

Thanks

---

### Post by superprash2003 on 2008-11-21
go to the terminal and post output of the following commands
1)iwconfig
2)lshw -C network

---

### Post by kevb8ll on 2008-11-21
iwconfig:

lo No wireless extensions
eth0 as above
wifi as above
ath0 ieee 802.11 essid: *.* then a pile of technical data


with the 2nd one - I get more options such as:

format can be

-html output hardware tree as html


I hope that makes sense




Just out of interest I used a PCLinuxOS 2007 live disc, and it had an installation system looking for hardware. Basically it detected my card and all I had to do was "connect" and put the password in and I was away.

---

### Post by superprash2003 on 2008-11-22
well typing the output is not a nice idea.. its better you copy paste it here.. if you dont have internet either through a pen drive or something.. its necessary to know which wifi card you have.. please do post output of lshw

---

### Post by kevb8ll on 2008-11-23
Ok here you go, after some faffing around - I've managed to do it :lolflag::


**iwconfig**

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
          Bit Rate: 0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1
          Retry: off   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:19  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0
[B]
lshw -C network[/B]

Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.12.01)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
        -quiet          don't display status
        -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

---

### Post by kevb8ll on 2008-11-24
Any idea with this?

---

### Post by arenahr on 2008-11-24
Hi guys, I have exactly the same problem.. Also new to Kubuntu (8.10 with KDE 4.1.2) and with an Intel PRO/Wireless 2200BG adapter.
I've tried both giving my wireless connection a static IP or leaving it on DHCP, but still no go. It either moans about iwconfig not being in my $PATH directory, or DHCPCD not being in $PATH directory.
I think I'm missing something basic, like an entry in a start-up file, or a command to save the config, or something like that.
Secondary question is that of encryption. We have WPA at home, and when I connect to the network, it asks me for an Encryption key/password - which I have to repeat twice. Doesn't seem quite right.
Here are the results of the commands mentioned above (note I'm not in range of the wireless network at this time.. I'm at work and the wireless LAN is at home.)

*****
username@hostname:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0     
          Retry limit:7   RTS thr:off   Fragment thr:off          
          Power Management:off                                    
          Link Quality:0  Signal level:0  Noise level:0           
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

username@hostname:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0                                      
       description: Wireless interface             
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth1
       version: 05
       serial: 00:15:00:44:f7:5f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 maxlatency=24 mingnt=3 module=ipw2200multicast=yes wireless=unassociated
  *-network:1
       description: Ethernet interface
       product: NetXtreme BCM5705M_2 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:02:0e.0
       logical name: eth0
       version: 03
       serial: 00:14:c2:df:de:7e
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5705-v3.24 ip=155.237.227.40 latency=64 mingnt=64 module=tg3 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 12:d3:11:8d:2e:61
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by superprash2003 on 2008-11-24
@kevb811 your lshw -C network output seems to be wrong, it should something similar to @arenahr's output.. in that format i mean.. please check
@arenhar try testing with a WEP network instead of WPA

---

### Post by kevb8ll on 2008-11-24
> **superprash2003 said:**
> @kevb811 your lshw -C network output seems to be wrong, it should something similar to @arenahr's output.. in that format i mean.. please check
@arenhar try testing with a WEP network instead of WPA

I have ran it twice - that is the result I get.

As soon as I saw what was written I guessed it was wrong - do you have any advice of how I can get it to register?

I typed EXACTLY what you suggested. The result indicates the wrong format is being used. Just to clarify I'm running Kubuntu 8.04 and KDE 4.0

---

### Post by kevb8ll on 2008-11-25
I would really appreciate help. :(

---

### Post by Doy22 on 2008-11-25
I recently updated from Ubuntu 7.10 to Kubuntu 8.04 but Now I can't boot My Hard drive with Vista on it. I can boot Kubuntu fine but When I use the Grub boot loader and choose Vista as a choice it comes up with an error message. I think it was because I had 7.10 installed inside of windows and it changed the BCD registry. Not sure and would appreciate the help!

---

### Post by Ayuthia on 2008-11-25
> **kevb8ll said:**
> I have ran it twice - that is the result I get.

As soon as I saw what was written I guessed it was wrong - do you have any advice of how I can get it to register?

I typed EXACTLY what you suggested. The result indicates the wrong format is being used. Just to clarify I'm running Kubuntu 8.04 and KDE 4.0

The commands in the Terminal are case sensitive.  You will need to make sure that the -C is an upper case C and not the lower case c.  Hope that helps.

---

### Post by kevb8ll on 2008-11-25
> **Ayuthia said:**
> The commands in the Terminal are case sensitive.  You will need to make sure that the -C is an upper case C and not the lower case c.  Hope that helps.

You're right - I was using lower case.

Here is the result:


WARNING: you should run this program as super-user.
  *-network:0
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: wifi0
       version: 01
       serial: 00:1d:0f:f9:72:cb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:03:0b.0
       logical name: eth0
       version: 10
       serial: 00:01:2e:0b:05:f4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes

---

### Post by kevb8ll on 2008-11-26
Hi guys, any more thoughts on this - after I have updated the log.

---

### Post by kevb8ll on 2008-11-27
I'm desperate to get my card working and would REALLY appreciate advice. 

Because of the other posts splitting up my log - here is the information that superprash requested again - all together:

**iwconfig**

lo no wireless extensions.

eth0 no wireless extensions.

wifi0 no wireless extensions.

ath0 IEEE 802.11g ESSID:"" Nickname:""
Mode:Managed Frequency:2.437 GHz Access Point: Not-Associated
Bit Rate: 0 kb/s Tx-Power:16 dBm Sensitivity=1/1
Retry: off RTS thr: off Fragment thr: off
Power Management: off
Link Quality=0/70 Signal level=-96 dBm Noise level=-96 dBm
Rx invalid nwid:19 Rx invalid crypt: 0 Rx invalid frag: 0
Tx excessive retries: 0 Invalid misc: 0 Missed beacon: 0

**lshw -C network**

WARNING: you should run this program as super-user.
*-network:0
description: Wireless interface
product: AR2413 802.11bg NIC
vendor: Atheros Communications Inc.
physical id: 6
bus info: pci@0000:03:06.0
logical name: wifi0
version: 01
serial: 00:1d:0f:f9:72:cb
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
*-network:1
description: Ethernet interface
product: RTL-8139/8139C/8139C+
vendor: Realtek Semiconductor Co., Ltd.
physical id: b
bus info: pci@0000:03:0b.0
logical name: eth0
version: 10
serial: 00:01:2e:0b:05:f4
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
1 Day Ago 04:01 PM

---

### Post by xadder on 2008-11-27
Did you try the suggestion I posted in this thread:

[http://ubuntuforums.org/showthread.php?t=981247]("http://ubuntuforums.org/showthread.php?t=981247")

Worked great for me.

---

### Post by kevb8ll on 2008-11-27
> **xadder said:**
> Did you try the suggestion I posted in this thread:

[http://ubuntuforums.org/showthread.php?t=981247]("http://ubuntuforums.org/showthread.php?t=981247")

Worked great for me.

Hi mate - just checked, my file is already edited to exactly what you suggest.

I'm beginning to get frustrated. I had a connection when I used a network cable plugged into the router - but now I have to use wireless due to the router being downstairs.

It works perfectly in XP and perfectly in PCLinuxOS 2007, but I want to use Kubuntu.

Please can someone help.

---

### Post by enthy on 2009-03-17
Hi;

i use xUbuntu 8.10 with NetworkManager Applet 0.7

i want to disable (desactived) ... my onboard wireless card...

- no i can't do that by the BIOS
- no i don't have a button for shutdown it
- i can't disable the driver with BootUp Manager
- i can't disable it by the Network Manager
- no i can't put a # on my file /etc/network/interfaces
because my file interfaces have just these line
        auto lo
        iface lo inet loopback

my config is:
eth0 my onboard lancard
eth1 nickname ipw2100 i want to disable it because my antenna is dead.
wifi0 an alias of eth1
ath0 my wireless pcmcia card i want to use it.

sorry for my english i'm a french canadian.

please reply me the file where i can edit my hardware configuration.

---

