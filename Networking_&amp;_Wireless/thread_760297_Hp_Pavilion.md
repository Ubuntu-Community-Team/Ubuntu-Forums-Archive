---
title: "Hp Pavilion"
date: 2008-04-20
forum: Networking &amp; Wireless
---

### Post by hurtinDv200 on 2008-04-20
I am using a live cd version of hardy beta, i can not get my wireless card to show up ne where, not under ifconfig or iwconfig.... can only help i have tried so many different things i am close to bangin my head into the wall.

---

### Post by Astura on 2008-04-20
Hell yea bro im here too with you only I got hardy fully installed. for over a month now actualy. I did actualy get the driver for our card installed but it wont pick up the hardware itself

---

### Post by hardfire_avk on 2008-04-20
yeah! true .. i m not able to install wireless in mine HP pavilion .. using ubuntu 7.1 gusty

---

### Post by Astura on 2008-04-20
gutsy wasnt even installing for me and fiesty had screwy sound that I couldnt fix but so far other then wireless hardy is working excellent.

again i stress that the driver is installed but its not finding the hardware, is there anyone who knows how to check what hardware is actualy booting up? maybe theres a bios problem here?

---

### Post by Astura on 2008-04-20
alrighty. just clarification here. but restricted drivers/hardware drivers does not show a click box for the wireless, so I used ndiswrapper to install the bcmwl6 driver from the hp website (this reads back as device present:yes) but under any configuration option concerning wireless i get no results.

only eth0 and lo. im convinced there is supposed to be more than  just eth and lo. is there anyone who understands what eth and lo actualy mean and what i would need to do to see wireless show up there?

---

### Post by lswest on 2008-04-20
can you put the output of ```
lshw -C network
``` which will tell us what driver is being used for the card presently.

---

### Post by Astura on 2008-04-20
Sure thing, here we go


> 
astral@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1d:72:44:36:f0
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.101 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
astral@ubuntu:~$ 



---

### Post by benvantende on 2008-04-20
Ok problems with a pavilion here too in combination with Hardy. I have a dv9000. The Intel 4965 card is recognized. Everything seems to work I only do not get an IP address. I have two other Hardy machines and two windows, all wireless, so you could say I know what I am doing. Couldn't find any other posts on problems with 4965 and Hardy.

gRTz

ben

---

### Post by hurtinDv200 on 2008-04-20
i have eth0 and lo, but my wireless card isnt showing up at all, i have tried a couple different live cds, i have tried ndiswrapper and nothing, the actual hardware not showing up seems to be my major problem. i'm using a broadcom internal wireless, and it doesnt show up AT ALL! very stressed out.

---

### Post by lswest on 2008-04-21
If the broadcom card isn't showing up, chances are you can't install drivers for the device.  Are you sure the card works?

@ Astura:
your card is recognized, but no drivers seem to be in use for it, have you tried ndiswrappering the bcmwl5 drivers? they worked for my card.

@ Benvantende:
Can you get an IP if you do ```
sudo dhclient [name of wireless device]
``` manually in the terminal?

---

### Post by Astura on 2008-04-21
lswest

I have tried several bcmwl5 drivers and they all have read back as hardware not present, but I do understand there are different versions of bcmwl5 drivers out there so I will continue trying.

okay Iv found a bcmwl5 driver that reads as hardware present  ( [http://ftp.us.dell.com/network/R174291.exe](http://ftp.us.dell.com/network/R174291.exe) )
though I still get no wireless?

Beh!


*updated*

---

### Post by lswest on 2008-04-21
Astura, what process did you use in setting up your ndiswrapper?
```
sudo ndiswrapper -i [driver name]
sudo modprobe ndiswrapper
sudo gedit /etc/modules # then append "ndiswrapper" to the end of that file
sudo reboot
``` should get it working.

---

### Post by Astura on 2008-04-21
Woot! Thanks SO much bro!

If only I knew how simple it would be I coulda had wireless a month ago! lol

What I needed to do to get the bcmwl5.inf driver to function was uninstall the old one, reboot, install the new one, reboot. and here I am posting this on wireless!

---

### Post by lswest on 2008-04-21
great ^^ glad you got working wireless now :) and thanks for the thanks.

---

### Post by benvantende on 2008-04-21
Hi lswest,

This is my output:

```
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1d:e0:a0:85:39
Sending on   LPF/wlan0/00:1d:e0:a0:85:39
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Maybe it has to do with "unknown hardware address"

I hope this tells you something

tHNx

ben

---

### Post by lswest on 2008-04-26
sorry about the slow reply, didn't remember to subscribe to this thread :P  and yeah, that dhcp output about wmaster can be ignored, it happens to me too when i'm using the b43 driver.  That said, can you post the output of ```
lshw -C network
``` it seems you're using the b43 driver, and if your card is unsupported you may need to switch to ndiswrapper.

---

