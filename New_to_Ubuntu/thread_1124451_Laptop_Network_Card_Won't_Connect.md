---
title: "Laptop Network Card Won't Connect"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by planegenius on 2009-04-13
Let me just start off by saying that I've been a windows user all my life, but I am ready to switch to Ubuntu on my laptop.  So far, so good, but I can't seem to connect to the net.

I am running Ubuntu 8.10 off a CD image, I want to check if it works before I ditch windows.  The GUI is gnome.

The Network Adapter in question is a D-Link DWL-650.  When I use the GUI network manager, i see all of the available routers in my area, including mine.  The lights on the device are on.  However whenever I click to connect to a router, it loads, and then displays the message-

"The Network Connection has been disconnected."

Another thing I noticed.  To check something on the card, I removed it and put it back in.  When I put it back in, the lights didn't come back on, and I couldn't see any possible connections.

I have no idea what to do! Is it a driver issue or a connectivity issue? I have also read that this can happen because I am running it from a CD. 

I really like Ubuntu and can't wait to get started with it, and I thank you in advance for any and all help. :smile:

---

### Post by superprash2003 on 2009-04-13
well. your wireless should work with ubuntu.. testing wireless through a live cd  can be tricky.. you would have to install the drivers and sometimes reboot etc..post an output of the following from the terminal..
1)lshw -C network
2)iwlist scanning
3)iwconfig
4)ifconfig

---

### Post by planegenius on 2009-04-13
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:09:02.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:ee:9e:1a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network
       description: Wireless interface
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: wmaster0
       version: 20
       serial: 00:0d:88:64:ea:54
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 mingnt=32 module=rtl8180 multicast=yes wireless=IEEE 802.11b
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: de:19:0c:50:0b:be
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
ubuntu@ubuntu:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:A5:0D:AD:45
                    ESSID:"Motorola"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=17/100  Signal level:-130 dBm  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000072b546f189
                    Extra: Last beacon: 40ms ago

pan0      Interface doesn't support scanning.

ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"Motorola"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:A5:0D:AD:45   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=85/100  Signal level:-129 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:ee:9e:1a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:432 errors:0 dropped:0 overruns:0 frame:0
          TX packets:432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27072 (27.0 KB)  TX bytes:27072 (27.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0d:88:64:ea:54  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-0D-88-64-EA-54-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ubuntu@ubuntu:~$

---

### Post by planegenius on 2009-04-13
Is this all of what you guys need?

Any diagnosis from this?

---

### Post by planegenius on 2009-04-13
After installing the software and drivers for another adapter, something changed.

I installed the software and drivers for the Dynex Enhanced Wireless G USB Network Adapter in Windows.  The USB adapter didn't seem to work in Ubuntu, so I put the Dlink card back in.

Now the card seems to have limited range and strength.  I see my router but its signal strength is very very low.  When I select it, it does connect.  However, it only stays connected for a short time and then disconnects.

I have no idea what to do.  I REALLY want to use Ubuntu, but I need the internet.  I really need your help here.

Thanks

---

### Post by benerivo on 2009-04-13
I'm not sure what you can try from within ubuntu to improve connectivity to your signal, which may be coming in too weakly, or very inconsistently. I would try two things in this order...

1. Change the router broadcast settings. In the router settings you can change the channel it broadcasts on. You currently use channel 1. You can also change the wireless type -- i think these are known as a, b, and g.

2. You can change the network manager in ubuntu, from networkmanager applet, to wicd. I think this is automatically done (setup) if you install wicd.

---

### Post by Shpongle on 2009-04-13
yea it could most likly be the router settings, my friend was having the same prob that fixed it

---

### Post by planegenius on 2009-04-13
Alright, thanks for the reply guys.

I changed those settings on my router, and still nothing.  Heres the thing, I have a list of several routers that I can connect to, and none of them work.  I also tried to install the alternate manager you suggested, but it would not install saying it conflicted with the current manager.

I read about installing the drivers in a special way with a special program. Is that what needs to be done?

Thanks again!

---

### Post by benerivo on 2009-04-13
You can get wicd to install be removing networkmanager first, but i don't think this is relevant to your problem, as it looks like it is your card being poorly supported in ubuntu. I also get this impression from a brief google search. I think i know what you mean by 'special' driver installation. It sounds like the option to use the windows driver inside ubuntu. I have never had to use this myself, but for a start the official web page is...
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by planegenius on 2009-04-13
Yep, that was it.

I tried it out, and still nothing.

After the newer driver wouldn't work, I tried an older one and it took it.  It says that the hardware isn't present though.  When I click 'configure network' I get the error message-

"Could not find a network configuration tool"

Any ideas? I really appreciate your help.

---

### Post by benerivo on 2009-04-13
The error message sounds strange, but it may be a false lead to finding a solution. Here is a link to a confirmed bug...
[https://bugs.launchpad.net/ubuntu/+source/ndisgtk/+bug/295892](https://bugs.launchpad.net/ubuntu/+source/ndisgtk/+bug/295892)

I'm really of no help to you now, but from what i have seen, it seems that there are many people with your card with similar problems. It may be worth trying wicd as a lucky solution.

---

### Post by planegenius on 2009-04-13
Well good news and bad news...

Good news is with all this tinkering, I'm learning how to get around Ubuntu well!

Bad News is that wicd didn't fix it.

Is it possible to set up the dynex ehanced wirless g usb?

This is so very frustrating, I want this OS, but I need to be able to connect to the net.  I appreciate everyone's help!

---

### Post by planegenius on 2009-04-13
I think I may have found a solution here.  I looked and a couple different sources, and they all point to this-

[https://bugs.launchpad.net/ubuntu/+source/restricted-manager/+bug/123292](https://bugs.launchpad.net/ubuntu/+source/restricted-manager/+bug/123292)

Updating the firmware on the card, and then changing something else...

Can I ask for some kind soul to look at this and tell me how exactly to do all that it asks.  I'm still new to this and could use some help, I don't want to mess my card up.

Thanks!

---

