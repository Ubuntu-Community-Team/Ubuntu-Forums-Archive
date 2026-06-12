---
title: "Wireless Setup"
date: 2005-11-30
forum: Networking &amp; Wireless
---

### Post by xinman on 2005-11-30
I know you have all heard this story plenty but I've searched the forums and I've tried as much as I think I can.

I have a Trendnet TEW-423PI wireless card, with a Linksys router.  The card was in a windows machine on the network so I know it works fine.  The only security I have on it at the moment is MAC filtering.  Which yes the MAC address is in there.  When I installed the card in the machine and booted up I immediatly saw wlan0 in the network configuration.  So I enabled it and tried to use it...nothing.  So I read about ndiswrapper and tried that solution.  I tried using the Windows 98 driver, then the Windows 2k driver and also the windows xp driver... nothing.  It's not even pulling an IP.  I tried manually setting the IP and stuff it still is not working.  Oh and in the ssid field there is nothing so I'm assuming that it's not even picking up the ssid but my ssid is broadcasting.  Any thoughts would be great.  This is the first time I've tried to setup wireless networking in linux.  And this is my first ubuntu box, but so far so good.

Thanks,
Dan

---

### Post by Lambert on 2005-11-30
With out doing anything and the card showing up in network-admin that means there is probalby a driver that supports your card in ubuntu. Looking at the model this is one with a marvel chipset (not supported) and one with a Texas Instruments chipset which uses the acx111 driver. I'm guessing you have the TI chipset.

So let's find out.

run this command from terminal

sudo lshw -businfo

Find your device in the list and notice what class it is. then this command

sudo lshw -C <class>

where <class> = the class from the first command with out the <> in the command.

Post that output here along with the output of 

lspci -v

just the part on the card.

If you're trying to use ndiswrapper and the acx111 driver is still loading, the acx111 driver will always take precedence and ndiswrapper will never be used. If we go the ndiswrapper route, there is a way to disable the acx111.

Also try to connect to the router and post the out put of these commands.

iwconfig
ifconfig

---

### Post by xinman on 2005-12-01
Here are the outputs for the first two commands, I will have to do the other two when I get home from work.

OUTPUT FROM *sudo lshw -C network*

```
*-network:0
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 5
       bus info: pci@02:05.0
       logical name: wlan0
       version: 00
       serial: 00:40:f4:c8:6d:69
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci multicast=yes wireless=IEEE 802.11b+/g+
       resources: iomemory:f6020000-f6021fff iomemory:f6000000-f601ffff irq:17
```


OUTPUT FROM *lspci -v*

```
0000:02:05.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
        Subsystem: Texas Instruments: Unknown device 9067
        Flags: bus master, medium devsel, latency 32, IRQ 17
        Memory at f6020000 (32-bit, non-prefetchable) [size=8K]
        Memory at f6000000 (32-bit, non-prefetchable) [size=128K]
        Capabilities: <available only to root>
```

I will post the results of the other ASAP.

Thanks,
Dan

---

### Post by xinman on 2005-12-01
And here are the results for the other commands:

iwconfig:
```
wlan0     IEEE 802.11b+/g+  ESSID:"xinman"  Nickname:"acx100 v0.2.0pre8"
          Mode:Auto  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

ifconfig:

```
wlan0     Link encap:Ethernet  HWaddr 00:40:F4:C8:6D:69
          inet6 addr: fe80::240:f4ff:fec8:6d69/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17

```

---

### Post by Lambert on 2005-12-01
So the device looks ok and the acx111 driver is loaded for this device.

try this command

sudo iwlist wlan0 scan

you should be able to see your router 

then to connect try this

```
sudo iwconfig wlan0 essid ___ ap ___  freq ____  commit
``` 
where 
essid =  exactly what it says
ap= the router's  mac address 
freq= the freq of the channel

iwconfig shows the device is set at channel 1 right now. So if router is broadcasting at channel 1 then you can cut that part out. To find the channels/frequency's you can click on the WTG in my sig.

---

### Post by xinman on 2005-12-01
Ok, I tried that but these are the results:

```
sh-3.00$ sudo iwlist wlan0 scan
wlan0     No scan results

```

Why would that be, my laptop works fine with my AP in windows.

---

### Post by learningubuntu on 2005-12-06
[QUOTE=xinman]Ok, I tried that but these are the results:

```
sh-3.00$ sudo iwlist wlan0 scan
wlan0     No scan results

```

Why would that be, my laptop works fine with my AP in windows.[/QUOTE]

Hi all,

I am a newbie to both Linux and Ubuntu (actually today is just the second day that I have been playing around with Ubuntu). And I have been experiencing the same problem as mentioned by xinman. I tried following the instructions mentioned in the wireless troubleshoot guide link provided by Lambert but I am stuck with the "No scan results" from the iwlist scan.

Hope that anyone can help me on this.

Thanks in advance.

---

### Post by Cobbydaler on 2005-12-06
I too am new to Linux/Ubuntu.

Using the LiveCD for 5.10 I have exactly the same problem.

My Netgear WG311V2 is recognised, drivers loaded etc., but no scan results for my Netgear DG834G router.

It's not a hardware problem as another PC in the room connects OK under XP.

I've searched the forums but have found no answer so far.

Has anyone else seen this behaviour & solved it?

---

### Post by mpvano on 2005-12-06
1. Note that iwlist doesn't do a complete scan unless you run it as root (i.e. using sudo).

2. Many common cards do not support scanning at all with the default drivers (like the very common orinoco cards, sold by several vendors under their own names). 

This doesn't mean they can't be used, but it just means you can't get a list of access points to choose from - you need to know the essid of the access point or the correct "wild card" essid name to use them.

Some cards take the essid name "any", others require that an empty name be set, still others require that you do not set the essid name at all. This inconsistency between linux driver supported behavior causes a LOT of confusion.

hope this helps a little,

Mario

---

### Post by Lambert on 2005-12-06
Go [here]("http://www.houseofcraig.net/acx100_howto.php"). Just skip past the compiling and installing the driver part. You may want to pay attention to installing the firmware though.

---

### Post by xinman on 2005-12-06
> Lambert
Go here. Just skip past the compiling and installing the driver part. You may want to pay attention to installing the firmware though.

I will try this and post my results ASAP, but I'm very busy right now so it may be a few days.

Thanks for the Input,
Dan

---

