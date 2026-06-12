---
title: "Wireless connection very slow"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by Stuart Thomas on 2009-04-03
Hi

I am a newby and have been up and running on 8.1 for a few days now. Everything seems to be working OK accept that when I connect my lap top to the router with my Belkin 54g F5d7010 V 3000 uk wireless card the download speed is very slow (like 30 seconds to load a page) although I can connect by cable to the router and get the sort of downloads speeds I am used to with Windows. The card was working like this after installation and I havn't tried any tweaking or anything. I have the laptop set up for dual boot and the wireless card works just fine with windows. 

My question to the group is are there any tweaks I can try or maybe there is a better driver available?

Thanks Stuart

---

### Post by hyper_ch on 2009-04-03
post the ouptut of
```

iwconfig

```

---

### Post by Stuart Thomas on 2009-04-03
> **hyper_ch said:**
> post the ouptut of
```

iwconfig

```
Hi 
The output of the code is:


lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:4D:11:05:CC   
          Bit Rate=1 Mb/s   Tx-Power=25 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=69/100  Signal level:-65 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

Thanks Stuart

---

### Post by hyper_ch on 2009-04-03
when posting output of a command or file content then put it individually into [noparse]```

```[/noparse] brackets. That makes it easier to read.

---

### Post by anewguy on 2009-04-03
If you could also post the output of lspci and lsusb it would be helpful.  Some laptops use a PCI device for the wireless, but some route the wireless through internal USB.  This will help us identify the wireless adapter on your laptop.

Why?  Well, even though the adapter is running, it appears to running at 1mps - this is VERY slow.  Perhaps there is another driver for your laptop, perhaps you actually need to manually specify the speed for the adapter - I think you do that with one of the i*config statements, but I haven't ever had to use it.

And another dumb question, if you'll forgive me:

Does it make any difference how far away from the router you are?  If you run your laptop within 2 or 3 feet of the router, with no walls, no "junk", etc., between the laptop and the router, is it still slow?

Thanks,

Dave ;)

---

### Post by Stuart Thomas on 2009-04-03
> **anewguy said:**
> If you could also post the output of lspci and lsusb it would be helpful.  Some laptops use a PCI device for the wireless, but some route the wireless through internal USB.  This will help us identify the wireless adapter on your laptop.

Why?  Well, even though the adapter is running, it appears to running at 1mps - this is VERY slow.  Perhaps there is another driver for your laptop, perhaps you actually need to manually specify the speed for the adapter - I think you do that with one of the i*config statements, but I haven't ever had to use it.

And another dumb question, if you'll forgive me:

Does it make any difference how far away from the router you are?  If you run your laptop within 2 or 3 feet of the router, with no walls, no "junk", etc., between the laptop and the router, is it still slow?

Thanks,

Dave ;)

Hi Dave

lspci output is:

```
lspci
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 04)
00:02.1 Display controller: Intel Corporation 82830 CGC [Chipset Graphics Controller]
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
02:01.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:04.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
03:00.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01) 
```


lsusb output is:

```
lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

It doesn't make any difference how close to the router I use the laptop. The download speed is the same ie very slow.

Thanks Stuart

---

### Post by anewguy on 2009-04-03
I'm not positive on this, but you may want to try

sudo ifconfig wlan0 speed 100 duplex full

I hope that's the correct syntax.  The speed 100 says to set the connection speed to 100mps, while the duplex full should set it to full duplex.

Hope it works.  Please post back any error messages or if you have success and how your speed seems.

According to the lspci, you wireless is using the rt2500.  I'm not sure if there is a restricted driver for it or not (you apparently already have some sort of driver).  I believe I have seen a lot of mention of madwifi drivers for these.  You may want to do a search in the forum with rt2500 driver and see what comes up.

Dave ;)

---

### Post by hyper_ch on 2009-04-04
the problem is that your card gets set at 1Mb.

I solved this by

```

sudo nano /etc/network/if-up.d/rate54M

```

and paste

```

#!/bin/sh

# set the wireless bit rate
iwconfig wlan0 rate 54M

```

In that file.

And then chmodding it
```

sudo chmod 0755 /etc/network/if-up.d/rate54M

```

Wifi is now set at 54M

---

### Post by Stuart Thomas on 2009-04-04
> **hyper_ch said:**
> the problem is that your card gets set at 1Mb.

I solved this by

```

sudo nano /etc/network/if-up.d/rate54M

```

and paste

```

#!/bin/sh

# set the wireless bit rate
iwconfig wlan0 rate 54M

```

In that file.

And then chmodding it
```

sudo 0755 /etc/network/if-up.d/rate54M

```

Wifi is now set at 54M

Hi

I followed your instructions (I think) and the download speed remains much the same. The outputs are:

```
sudo nano /etc/network/if-up.d/rate54M
```

I now get output

```
                      

#!/bin/sh

# set the wireless bit rate
iwconfig wlan0 rate 54M
sudo 0755 /etc/network/if-up.d/rate54M

```

```
iwconfig
```

I now get output

```
 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:4D:11:05:CC   
          Bit Rate=1 Mb/s   Tx-Power=25 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=69/100  Signal level:-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

Regards Stuart

---

### Post by hyper_ch on 2009-04-04
well, should be:

sudo chmod 0755 ..........

---

### Post by Stuart Thomas on 2009-04-04
> **hyper_ch said:**
> well, should be:

sudo chmod 0755 ..........

The config file still shows 1mbs but the download speed seems to have increased dramatically? Not as fast as Windows but still pretty good. A page that took 30 secs to load now only takes 5 or 6 seconds so many thanks for the advice.

Stuart

---

### Post by hyper_ch on 2009-04-05
well, that script is run after bootup....

---

