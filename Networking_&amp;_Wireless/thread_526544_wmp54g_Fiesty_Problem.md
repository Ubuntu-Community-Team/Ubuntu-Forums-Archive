---
title: "wmp54g Fiesty Problem"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by bzaks on 2007-08-15
I've been looking around and digging for the past few days, and I can't seem to find a feasible solution to my problem:

I have been using my WMP54G Ver 4. Wireless card since Feisty first came out, the computer has been updated regularly without a problem since then. However, about a week ago, my wireless simply stopped working. I rebooted the router, I rebooted my machine, however, it has been simply to no avail.

I have since then put in a new HD (temporarily) to put on XP to test, thus checking the card to make sure that it working fine. I was able to surf around and do whatever I want.

Returning to ubuntu:

I'd show the lspci and iwconfig and ifconfig output, but I'm not at home at the moment.

Please keep in mind: there were no updates prior to the card failing, nor have I changed any settings.
There is no encryption on the network, and I'm doing manual configuration pointing directly to the router (ssid: "default").

Thanks for your help!

Michael

---

### Post by kevdog on 2007-08-15
Can you post:

lshw -C network

One your updates broke the kernel driver module of your card.  Impossible to know which one at this point.  The solution is to reinstall your wireless driver and place the appropriate module back into the kernel.

Im attempting to find the chipset of your device so I know what to do or how to proceed.  Did you ever install any drivers for the card way back when??

---

### Post by AnotherMuggle on 2007-08-15
I also use a WMP54G Ver 4 and find that I can only connect to wireless networks if I use the Manual Config. option.

I also find that after entering all of the settings I need to reboot to make the connection active.

Linux noob...but I'm getting somewhere :-)

---

### Post by bzaks on 2007-08-15
I too have only had luck with Manual config. However, I have found rather than a reboot, you can just log out and log back on and you'll have the same results. 

> 
One your updates broke the kernel driver module of your card. Impossible to know which one at this point. The solution is to reinstall your wireless driver and place the appropriate module back into the kernel.

Im attempting to find the chipset of your device so I know what to do or how to proceed. Did you ever install any drivers for the card way back when??


Fortunately, Fiesty came totally configured to run my wmp54gv4. Heck, even 6.10 and 6.04 worked straight out of the box! (Gotta say, I was pretty impressed)

I have to get my hands on a flash drive so I can copy and paste the information requested, I'll hopefully have something for you tomorrow AM.

Thanks everyone,  I really appreciate this.

---

### Post by bzaks on 2007-08-15
Okay, so I got the internet to work, but I feel it's only a temporary solution, and finding a solid one would be a lot better:

```

sudo ifconfig ra0 down
sudo iwconfig ra0 essid "default"
sudo ifconfig ra0 up
sudo dhclient3

```

However, again, I'm concerned this is not a permanent solution and I'm just curious if anyone can give me any answers. 

This is the output before I ran the above commands:
```

user@computer:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: a
       bus info: pci@01:0a.0
       logical name: ra0
       version: 01
       serial: 00:12:17:64:22:45
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT2500STA driverversion=1.1.0 BETA4 latency=32 link=yes multicast=yes wireless=RT2500 Wireless
       resources: iomemory:e6000000-e6001fff irq:19
***********************************************************
user@computer:~$ ifconfig
ra0       Link encap:Ethernet  HWaddr 00:12:17:64:22:45  
          inet6 addr: fe80::212:17ff:fe64:2245/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13982 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:568424 (555.1 KiB)
          Interrupt:19 Base address:0xc000
***********************************************************
user@computer:~$ iwconfig
ra0       RT2500 Wireless  ESSID:""  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s   Tx-Power:-2 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-206 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
***********************************************************
user@computer:~$ lspci | grep Network
01:0a.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

```

---

### Post by kevdog on 2007-08-15
Congrats at the manual solution.  Since you have a ra chipset with rt2500 driver a more permanent and functional solution requires you to download and compile the newest version of the rt2500 driver (known as serial monkey drivers), and if you desire a GUI to manage you wireless card, use rutilt (which can be downloaded at the serial monkey site).

If you need help please post back.

---

### Post by bzaks on 2007-08-16
Okay, fair enough, I need to compile a new driver yada yada yada... but why did it just suddenly stop? It worked perfectly fine! Absolutely no problems what so ever... I'd like to keep my computer as much "out of the box" as possible. (I almost did a complete reformat after this problem started up, but I decided I'd just wait til october and get Gutsy instead)

Thanks for your help again!

---

### Post by kevdog on 2007-08-16
I dont have a crystal ball to tell you why it stopped working.  In fact Im surprised its working at all, but more power to you.  I dont know if gusty will have the updated drivers (rumor is no), but possibly it will work with the upgrade.

I guess however if it works -- dont fix it is a good philosophy for the time being.

---

### Post by bzaks on 2007-11-12
I know this is really old. BUt I don't get online much anymore. The problem was the PSU had gone bad and wasn't generating enough power for my box.

---

