---
title: "Netgear wg311t works in ubuntu 7.10 but not ubuntu server 7.10 ??? help"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by wolfsta on 2007-10-29
Hi all :)

Just installed a box to use for basic network gateway httpd server etc.. and put my wifi network card in it to share net over wireless.

Thought I was going crazy but a standard install of ubuntu server 7.10 does not see the card but if I boot to the live install cd for the desktop its auto installed.

This is the output from lspci -v for the card from within desktop live install cd

> 05:07.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
        Subsystem: Netgear Unknown device 5a00
        Flags: bus master, medium devsel, latency 168, IRQ 22
        Memory at fbff0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

when i do an iwconfig from the desktop it shows up

> ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-90 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

on a server install I only see lo and eth0

Any help on how to get it working would be grand :)

Wolfsta

---

### Post by Selcal on 2007-10-29
i found that when i reset my router it all worked out wifi then.  I think that my router had a firmware issue when i updated it though.  I just worked better after i did the NETGEAR reset and just set it all up again.

---

### Post by wolfsta on 2007-10-29
Nah its the pci card on the machine not being recogised.. i dont have an access point at all i was hoping to turn the ubuntu server box into an access point if this card will let me use ap mode.

But ubuntu server not showing it up at all at the moment.  Here is the output from the server lspci -v
> 
05:07.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
        Subsystem: Netgear Unknown device 5a00
        Flags: bus master, medium devsel, latency 64, IRQ 5
        Memory at fbff0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2

Cheers

---

### Post by Selcal on 2007-10-29
> **wolfsta said:**
> Nah its the pci card on the machine not being recogised.. i dont have an access point at all i was hoping to turn the ubuntu server box into an access point if this card will let me use ap mode.

But ubuntu server not showing it up at all at the moment.  Here is the output from the server lspci -v


Cheers


This seems to be over my head.  I did read something about mounting eth# to a mac address, this may force it to do what you need it to.  I don't know the in and outs of this process because right before i was going to try it my stuff started working.

---

### Post by wolfsta on 2007-10-29
yeh no not that..  i think i need to possibly compile wireless driver in the kernel?? maybe its disabled in the server install?? anyone? or something.. because the device doesnt show up in iwconfig

---

### Post by Nixus_Maximus on 2007-10-29
You have an Atheros Chipset. Have you installed the linux-restricted-modules? The Atheros drivers are not in the kernel because they are non-free.

Cheers,
Simon

---

### Post by wolfsta on 2007-10-29
Brilliant :D

knew it would be something like that.  Thanks heaps for your help am investigating now.

Wolfsta

---

### Post by wolfsta on 2007-10-29
ok so I did 

sudo apt-get install linux-restricted-modules

and now i can see /lib/modules/2....generic and 2....server

also /lib/linux-restricted-modules/


but how do i get the ath module installed
have tried insmod ath_pci with no luck  not too good with kernel stuff yet

and lsmod | grep ath shows nothing

Any help greatly appreciated

Cheers

Wolfsta

---

### Post by wolfsta on 2007-10-29
And

sudo modprobe ath_pci

that doesnt work either.. Fatal: module ath_pci not found

---

### Post by ttthebear on 2007-11-06
Hi,

Any luck getting this sorted.  I have the same problem.

So when I changed the driver module it is not loading for my atheros card. what I think has happened is that modprobe cannot find the ath_pci.ko module because it is not in the proper directory.

It is currently here

/lib/modules/2.6.22-14-generic/madwifi/

but I think it should be here

/lib/modules/2.6.22-14-server

So how do I get ubuntu to read that directory as well??

Thanks

Tom

---

### Post by wolfsta on 2007-11-06
Nope I havent resolved it yet.  I ended up pulling down the ubuntu-alternate install cd instead as it still has the encrypt during install option and option to not install Xorg etc. 

The wifi card works out of the box in this install.  But still really wanna know how to resolve that as would love to utilize the out of the box LAMP install.

Anyone out there ideas?

Wolfy

---

### Post by ttthebear on 2007-11-07
From what I have been told the driver for the generic modules may not be compiled for the server kernel.  I tried copying the modules to /lib/modules/2.6.22-14-server with no success.  There were some errors on loading the dependencies.

/lib/modules/2.6.22-14-generic/madwifi/
vs
/lib/modules/2.6.22-14-server

There were some errors on loading the dependencies.

From what I been told you may need to recompile a new ath_pci kernel module for the 2.6.22-14-server kernel.

So because I only wanted to use ubuntu server to get xen working with my problematic nvidia combination I am going to resolve that problem instead of this.  However, I did post in a couple other places and if I get the answer or steps to fix it I will post it here.

---

### Post by gdsimpson on 2008-01-30
this worked for me

#add /etc/etch/sources.list
#Madwifi Stable 
deb [ftp://ftp.au.debian.org/debian](ftp://ftp.au.debian.org/debian) stable main contrib non-free
deb-src [ftp://ftp.au.debian.org/debian](ftp://ftp.au.debian.org/debian) stable main contrib non-free

#get card info
lspci -v

#enable wireless card
apt-get install module-assistant
apt-get install wireless-tools
apt-get install pcmcia-cs
apt-get install pcmciautils
apt-get update
apt-get install madwifi-source
apt-get install madwifi-tools
m-a prepare
m-a a-i madwifi
modprobe ath_pci
echo ath_pci >> /etc/modules

#open network setting and you should now see ath0 wireless 

[http://wiki.rd-robotics.com/wiki/index.php/Debian](http://wiki.rd-robotics.com/wiki/index.php/Debian)

---

