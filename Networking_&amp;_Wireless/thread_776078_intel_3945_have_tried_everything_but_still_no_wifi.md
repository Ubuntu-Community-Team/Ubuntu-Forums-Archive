---
title: "intel 3945 have tried everything but still no wifi"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by eleses on 2008-04-30
I have now installed hardy about 10 times and it looks good. I like the fact that it can (almost) recognise my external monitor and set up a seperate xscreen for it which is the one thing I found really trying in Gutsy. Anyway, the one thing which is stopping me from using it is the wifi problem.

I have the intel 3945abg card and I have tried:

[LIST]
[*]updating using the backports and then 
```

sudo apt-get install linux-backports-modules-hardy-generic
``` as explained on [**this**]("http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/") blog

[*] then trying this:
```
sudo modprobe -r iwl3945
sudo modprobe iwl3945
``` which I found in this forum and which makes my led light up for about a second and then die again.

[*] I have tried everything mentioned on **[this]("https://help.ubuntu.com/community/WifiDocs/Driver/iwlwifi_Intel_3945_4965/gutsy")** bug report

[*] I have basically tried everything I can find on these forums but with no effect 
[/LIST]

One thing which might be contributing is this:

When I do "lshw -C network" I get this:```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 13
       serial: 00:13:a9:61:d4:9f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:c1:60:99
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g 
``` which says that the logical name is wmaster0 but when I do "ifconfig" I get this ```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``` which references wlan0

Is this the reason it isn't working? If so, how do I fix it and if not, any other ideas?

(I have even gone as far as updating using hardy proposed just to see what would happen but even though I got 52 updates still no wifi.

Thanks in advance.

---

### Post by |{urse on 2008-04-30
open a terminal and try 
sudo ifconfig wlan0 up
whats that give you?
if no luck you'll need ndiswrapper and the win drivers to do it

---

### Post by eleses on 2008-04-30
that gives me ```
wlan0: ERROR while getting interface flags: No such device
```

(by the way, wow - quick reply! thanks a lot.)

---

### Post by nwadams on 2008-04-30
i have the exact same problem, and am getting the exact same things. I had no problem in gusty wiht the ipw driver. I believe the problem is with the wmaster0 wlan0 thing, but don't know how to fix it

---

### Post by |{urse on 2008-05-01
for (probably both) you guys:

[http://ubuntuforums.org/showthread.php?t=31926]("http://ubuntuforums.org/showthread.php?t=31926")

---

### Post by Sub101 on 2008-05-01
I have the same wireless card as you and it works fine without ndiswrapper.
My wireless connection runs as eth1 although lshw also gives me wmaster0 as the wireless interface.

  Im not too sure what wmaster is as it wasn't there on Feisty?

  How do you mean its not working? Is it not discovering any networks on just not connecting?

---

### Post by nwadams on 2008-05-01
it isn't discovering networks or connecting.
how can I change it to use eth1 instead of wmaster0

---

### Post by Sub101 on 2008-05-01
I don't think you need to? My iwconfig gives me 
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Winter"  Nickname:""
          Mode:Managed  Frequency:2.447 GHz  Access Point: **:**:**:**:** 
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=80/100  Signal level=-54 dBm  Noise level=-84 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

it seems to be exactly the same as yours? I presume you have got the card switched on?

---

### Post by nwadams on 2008-05-01
oh see mine says wlan 0 instead of eth1
are u using the iwl driver or the ipw driver?

---

### Post by Sub101 on 2008-05-01
IWL3945 - this driver installed by default. What are you using?

---

### Post by nwadams on 2008-05-01
same as you, did you do anything other than install/update to hardy. Is there any way i can change it to use eth1 instead of wlan0

---

### Post by RobHart on 2008-05-01
Hi

This is somewhat the blind leading the blind as I have only just switched to Ubuntu..

I have an Asus V1J with the Intel 3945 and I have now got it working, but it refused (and continues to do so) to work with WPA. If you can try it in unsecured mode, that might help.

For your info, here's what shows up when I do an ifconfig...

wlan0     Link encap:Ethernet  HWaddr 00:18:de:20:49:3d  
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fe20:493d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50822 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10616 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21229054 (20.2 MB)  TX bytes:1417452 (1.3 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-20-49-3D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by nwadams on 2008-05-01
what did you do to get it working for an unsecured network?. I can't even see a network not to mention connect to one

---

### Post by RobHart on 2008-05-01
It was pretty simple - I just installed Ubuntu 8.04 (Desktop). I then spent hours trying to work out why I couldn't connect to my WAP network. Once I switched the network to unsecured, I could connect.

Still can't get WAP-PSK working though...

---

### Post by nwadams on 2008-05-01
oh see, I can't see wireless networks period, so I can't connect to anything. 

the iwl3945 is really buggy, hopefully it gets patched soon.

---

### Post by |{urse on 2008-05-02
> **nwadams said:**
> what did you do to get it working for an unsecured network?. I can't even see a network not to mention connect to one

sudo iwconfig wlan0 mode Managed

should take care of all that, but since your chipset (rather driver) isn't currently functional you're going to have to use ndiswrapper or pay for an online service (whose name i refuse to mention to even my worst enemy) which configures it all for you. Unfortunately the price you pay for upgrades are possible incompatibilities. Perhaps you should go back to gutsy until progress is made in your individual favor.


[http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926)

---

### Post by lnogueir on 2008-05-04
Hi! Is there any way to install ipw driver on Hardy? It's a lot better then iwl!

Thanks!

---

### Post by pjfl on 2008-05-04
Try this [http://james.colannino.org/downloads.html](http://james.colannino.org/downloads.html)
Please post to let us know it it works

---

