---
title: "how to install driver"
date: 2007-09-19
forum: Networking &amp; Wireless
---

### Post by ride3k on 2007-09-19
ok so I am brand new to ubuntu.  I have a m9700 ALienware laptop with a Realtek 8185 wireless card.  I don't know if this is a supported card or not, but by looking at the list it seems like it is.  I have ndiswrapper installed and that where I get lost.  I have no idea how to install the driver for this card so I can use wirelss, please help a noob =(

---

### Post by ride3k on 2007-09-19
this is the wireless card as lspci -v | less

01:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
        Subsystem: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
        Flags: bus master, medium devsel, latency 64, IRQ 3
        I/O ports at 8800 [size=256]
        Memory at fa0ff000 (32-bit, non-prefetchable) [size=512]
        Capabilities: <access denied>

---

### Post by Motoxrdude on 2007-09-19
Download this[ zip file ]("ftp://202.65.194.212/cn/wlan/x86-8185(1094).zip") and extract the 3 files into your home directory.
Now open up the terminal (Applications>>Accesories>>Terminal) and run this
```

sudo ndiswrapper -m

```
You only need to run that once.

Now run
```

sudo ndiswrapper -i net8185.inf

```
Then run
```

sudo modprobe ndiswrappe

```

Let me know if you run into problems.

---

### Post by ride3k on 2007-09-19
that worked perfectly, thank you very much

---

### Post by Motoxrdude on 2007-09-19
your welcome :)

---

### Post by KenMac on 2007-09-21
Hi guys.  I also have a REALTEK 8185 wireless card that does not seem to be working.  I am running 64-bit Feisty on a Gateway MT3423 laptop.  My output from  lspci -v|less is:

06:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.1
1a/b/g Wireless LAN Controller (rev 20)
        Subsystem: Realtek Semiconductor Co., Ltd. Unknown device 8225
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 6000 [size=256]
        Memory at b3400000 (32-bit, non-prefetchable) [size=512]
        Capabilities: <access denied>

I tried the steps suggested by Motoxrdude with apparently no success.  It seems that the 'Unknown device 8225' line in my output might be a problem.  Any help with this would be greatly appreciated!

---

### Post by kevdog on 2007-09-21
You might be out of luck with this card -- 

1. first you need a 64 bit driver (I think this may be a problem).
2. There is a native driver r818x.  Im fairly certain this should be in the default installation.  Try going into the blacklist file (/etc/modprobe.d/blacklist) and commenting out (#) the blacklist r818x statement.  From what I remember however this driver is missing the user space utilities, however its worth a shot.
3. For most rtl wireless cards I usually recommend ndiswrapper with win98 driver.  Im fairly certain however win98 never came in a 64 bit edition.  I guess you could try ndiswrapper in combo with the winxp 64 bit drivers if you can find them.

Again, rtl wireless chipsets are kind of a pain in the A$$

---

### Post by KenMac on 2007-09-21
Hi kevdog.  Thanks very much for your reply.  I commented-out the blacklist per your suggestion and my card now seems to be working!:)  The only problem I am having now is that the signal strength is quite low (30%) and I have not been able to actually access the internet with it.  Could this still be a driver issue or is it simply that my card is not that great?
Again, thank you for the help.

---

### Post by tipiglen on 2007-09-21
Mototrdude,

Thanks a million for that!  It solved a problem which had me puzzled for a good while.

I had the driver and had ndiswrappered it, but without the "-m", so it didn't boot the wlan0, and I had to open a treminal and do 

sudo modprobe ndiswrapper 

to get the wireless up and running every time.  Now it should boot.

A drink of your choice is at the virtual bar of your choice!

Namaste
ed

---

### Post by KenMac on 2007-09-22
Hi guys.  Does anyone know why I would be able to detect wireless networks but not connect to them?  When I click on Network Settings I see a list of the networks in the area.  However, no matter which one I connect to I get signal strength 30% and I cannot get out to the web.  Any ideas would be much appreciated.

---

### Post by kevdog on 2007-09-23
Dont worry about the signal strength -- those might not be actually real percentages.  This is a documented problem.

Can you post the following:
lshw -C network
iwlist scan

The iwlist scan results are going to show me all the routers broadcasting in your area.  Can you tell me which one you are trying to connect to.  Then we can try to establish a manual connection.

---

### Post by KenMac on 2007-09-23
Thank you for the reply.  My output from lshw -C network:

WARNING: you should run this program as super-user.  
  *-network                      
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@06:09.0
       logical name: wlan0
       version: 20
       serial: 00:c0:a8:f3:89:13
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 ming
nt=32 multicast=yes wireless=802.11b/g
       resources: ioport:6000-60ff iomemory:b3400000-b34001ff irq:11

and from iwlist scan:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:16:B6:35:65:5F
                    ESSID:"linksys_SES_26932"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key: on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:0  Signal level:0  Noise level:158
                    Extra: Last beacon: 196ms ago

          Cell 02 - Address: 00:1A:70:78:70:25
                    ESSID:"jaded tattoo and body art"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key: on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:0  Signal level:0  Noise level:158
                    Extra: Last beacon: 107ms ago

          Cell 03 - Address: 00:0F:B5:1F:4E:FE
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key: off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54 
                    Quality:0  Signal level:0  Noise level:158
                    Extra: Last beacon: 0ms ago

          Cell 04 - Address: 00:09:5B:72:91:5E
                    ESSID:"NetSmack"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:6
                    Encryption key: on
                    Bit Rates:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 
                    Quality:0  Signal level:0  Noise level:158
                    Extra: Last beacon: 478ms ago

I am attempting to connect to the unencrypted router "NETGEAR" listed under cell 03.  If you can help me connect to it you will win the undying gratitude of a noob! :)

---

### Post by kevdog on 2007-09-23
Owww-your using a rlt wireless card -- hate those chipsets.


Anyway lets just try this.

sudo ifconfig wlan0
sudo ifconfig wlan0 0.0.0.0
sudo ifconfig wlan0 up
sudo iwconfig essid "NETGEAR"
sudo iwconfig mode Managed
sudo dhclient wlan0

Also post
route -n

---

### Post by KenMac on 2007-09-24
Hi.  Thanks for the reply.  I have changed locations and I am now trying to connect to the router "ukyedu".  My output from iwlist scan is:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:13:19:0F:FA:B0
                    ESSID:"ukyedu"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key: off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 5.5 11 12 18 24 36 48 54 
                    Quality:0  Signal level:0  Noise level:158
                    Extra: Last beacon: 198ms ago

When I ran sudo iwconfig essid "ukyedu" I received the following error:

Error : unrecognised wireless request "ukyedu"

My output from route -n is:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
128.163.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         128.163.40.1    0.0.0.0         UG    0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 wlan0

Any ideas?  Thanks for your help.
Ken

---

### Post by kevdog on 2007-09-24
I typed the syntax of the commands wrong, here is what is supposed to be:

sudo iwconfig wlan0 essid "NETGEAR"
sudo iwconfig wlan0 mode Managed

---

### Post by KenMac on 2007-09-24
Thanks for the reply.  I re-ran the list of commands and I get the following output:

There is already a pid file /var/run/dhclient.pid with pid 16306
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:c0:a8:f3:89:13
Sending on   LPF/wlan0/00:c0:a8:f3:89:13
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I am noob-enough to not know if this is good or bad but still no wireless signal.  It sees the routers but shows no signal.

---

### Post by brons2 on 2007-11-09
> **Motoxrdude said:**
> Download this[ zip file ]("ftp://202.65.194.212/cn/wlan/x86-8185(1094).zip") and extract the 3 files into your home directory.
Now open up the terminal (Applications>>Accesories>>Terminal) and run this
```

sudo ndiswrapper -m

```
You only need to run that once.

Now run
```

sudo ndiswrapper -i net8185.inf

```
Then run
```

sudo modprobe ndiswrappe

```

Let me know if you run into problems.

I just set up a dual boot with XP Pro and Ubuntu on this laptop, a ThinkPad R32.  The Realtek 8185 works fine in Windows.  

Anyways, I tried to take the steps you listed above but the terminal told me that "sudo: ndiswrapper: command not found".  Where do I download ndiswrapper from?  I'm an extreme Linux newbie.  (windows system admin who needs to learn!)

---

### Post by brons2 on 2007-11-09
OK I figured out to install ndiswrapper from the Synaptics Package Manager.  But when I tried to run

sudo ndiswrapper -i net8185.inf

it said 8185 was already installed.  

And the third command sudo modprobe ndiswrapper didn't work at all.

Maybe I need a library modprobe?

---

### Post by freeflyerme on 2007-11-15
I have a similar if not identical problem.  I have probably the same chipset (output of lshw -C network)

WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:05:07.0
       logical name: wlan0
       version: 20
       serial: 00:18:e7:2e:13:59
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 late

I am fairly certain that Ubuntu already detects my card and knows it's there, but I don't know why "iwlist scan" returns no results.  

I have already used ndiswrapper to install the net8185 drivers, and I tried to compile the open source Linux drivers, though that was a failure.  There is an blacklist entry for r818x.  I have tried a lot of other things in the past few days, and I think one of them even installed some modules into my kernel.  Hopefully none of the false trials have messed up my chances for getting wireless to work.

Any help on this is greatly appreciated.

Oh, when I type ifconfig, there's an extra entry of 

wlan0:ava Link encap:Ethernet  HWaddr 00:18:E7:2E:13:59  
          inet addr:169.254.4.122  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Memory:f88f0000-f88f0100 

This being different from the usual wlan0, I'm not sure if it serves any relevant purpose.

Thanks again.

---

### Post by freeflyerme on 2007-11-15
Wow, I got iwlist working.  There are two things that could have contributed to this:

1. Apparently, blacklist entry 818x was commented, silly me.  However, I uncommented it, restarted multiple times, and still no luck.  (maybe I just need to try harder)
2. I went back to an older version of my kernel, 2.6.20, which lacked videocard support, so I'm now looking at a very funky display.  However, iwlist has worked, showing me all of the wireless near me.

Actually, I am connected to the network!  I just googled "blwaerk", and it returned a result, though the CAT5 is disconnected.  

So now my question is: how do I find out what are the new modules I've loaded in the last day, and remove them?  I would really like to get this to work on the most updated kernel, along with non-funky graphics.

----
Below is a summary of all my efforts (minus the wrong turns) that has taken me to this point.  Hopefully someone can benefit from this.  Honestly, I don't know if there was support for my card out of the box, but if there isn't, then what I've done below might be a path to a working wireless with the board.

1. follow the steps in page 1.  Install ndiswrapper (and dependencies), install windows driver (net8185) that comes with it.
2. blacklist 818x
3. restart.
4. MANUALLY Connect to wireless.  This part sucks, because I have probably gotten my wireless to work a day ago, except I kept thinking there should be a wireless icon displayed and informing me of the connection.  Somehow, there isn't one, and I probably foolishly loaded unnecessary modules into my kernel.
Important: manually set your network configuration through network manager (System -> Admin -> Networks; alternatively, left click on the upper right icon for your Ethernet, and click Manual Config).  If an entry for wireless is listed, then the card is detected,  If above 3 steps worked, you might see a list of network SSIDs near you.  Else, type in your SSID, if there's no security, leave password blank, don't worry about encryption type if it's not there.  Finally, set the connection type to DHCP.  It's the default setting in my Trendnet wireless router.
5. Unplug Cat5 and Google "blwaerk" in Firefox, to make sure your wireless is working.

Don't install linux drivers that are associated with the card.  Don't load modules into your kernel if you don't know what you're doing.

----
Finally, can someone tell me how to remove unneeded modules from my kernel?  Thanks a bunch.

---

### Post by freeflyerme on 2007-11-15
Sweet, after Googling: lsmod lists all installed modules, rmmod temporarily removes (until kernel reloaded after reboot) a loaded module, "modprobe -r" removes the module (permanently?)

So I did,
lsmod > lsmod.out   (in old kernel)
lsmod > lsmod.out.2 (in new kernle)
vimdiff lsmod.out lsmod.out.2

Vimdiff wasn't too enlightening, but I did a "grep r8" (looking for unneeded modules) and found an "ieee" something and an r8180 were in the new kernel but not in the old.  rmmod'ding them in the new kernel simple removed my wireless card from Network manager.  Instead, modprobe -r got rid of these permanently, I rebooted, and wireless works.

Also, what I wrote earlier about getting wireless to work, I think I forgot a command that loaded the ndiswrapper into the kernel.  But in essence, what I wrote are the instructions on the first page, with the hint of actually manually "iwlist scan" and checking and connecting network connections after following the steps.  Even now, I don't have a wireless icon on my upper right of my desktop, but wireless is working.

That's all.  Hope someone finds something useful in here.

---

