---
title: "WLAN doesn't start automatically after Upgrade to Edgy"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by kregen on 2006-10-31
Hallo, 
Yesterday ich upgraded from Dapper to Edgy. Befor upgrading there are no problems with the WLAN. After upgrading the WLAN doesn't starts automatically!

[B]Hardware (lspci) 
[/B]
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03) 
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) 
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) 
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) 
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) 
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02) 
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02) 
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 01d7 (rev a1) 
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02) 
06:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02) 
06:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
```

**Configuration (Interfaces)**

```
auto lo 
iface lo inet loopback 

auto eth1 
iface eth1 inet dhcp 
wireless-essid rookery 
wireless-key s:xxxxxxxxxx 
wireless-rate 54M 
wireless-nick acer 
wireless-channel 10 

```

**resolv.conf**
```
nameserver 192.168.178.1 
```

**hosts**
```
127.0.0.1 localhost corvuscorax 
127.0.1.1 corvuscorx corvuscorax 
192.168.178.21 laptop laptop.rookery.net 
::1 ip6-localhost ip6-loopback 
fe00::0 ip6-localnet 
ff00::0 ip6-mcastprefix 
ff02::1 ip6-allnodes 
ff02::2 ip6-allrouters 
ff02::3 ip6-allhosts 

```

**ifconfig** 
```
eth0      Protokoll:Ethernet  Hardware Adresse 00:0F:B0:F0:C9:77  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:74 

eth1      Protokoll:Ethernet  Hardware Adresse 00:13:02:09:13:2C  
          UP BROADCAST MULTICAST  MTU:1492  Metric:1 
          RX packets:11319 errors:0 dropped:1999 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:193 Basisadresse:0x4000 Speicher:d2100000-d2100fff 

lo        Protokoll:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0 
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0 
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:212 (212.0 b)  TX bytes:212 (212.0 b) 

```

**iwconfig**

```
lo        no wireless extensions. 

eth0      no wireless extensions. 

eth1      unassociated  ESSID:off/any  Nickname:"acer" 
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated    
          Bit Rate=0 kb/s   Tx-Power:16 dBm    
          Retry limit:15   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:2089   Missed beacon:0 

sit0      no wireless extensions. 

```


**but when i enter the following commds, all is OK!**
```
sudo iwconfig eth1 mode managed 
sudo iwconfig eth1 channel 10 
sudo iwconfig eth1 essid rookery 
sudo iwconfig eth1 key s:SKYCONNECTSK5 
sudo dhclient eth1

```

What ist wrong?

Thnks for Help
cu 
kai

---

### Post by kregen on 2006-11-01
is there noboby, who can help me?

---

### Post by dca on 2006-11-01
I wish I could help, but my wife has a similar issue with her Ubuntu PC that has a D-Link (either DWL-G510 or G520) WiFi PCI card installed...  Which ever one it is, it's the one w/ the revised Atheros chipset so the instructions are built into the kernel.  I was happy as heck when it worked out of the box, however, some times, she starts the PC, and no internet.  Shutdown, restart, it then works.  I've been unable to go into the network settings for the card and convincing it to work.  It may have something to do w/ DNS settings BUT to make a long story short the ESSID also displays 'Not-Associated' when running 'ifconfig' even though it's clearly listed in the WLAN properties GUI...  Annoying....

---

### Post by lonce on 2006-11-01
If you start the PC and no wireless is there.  All you have to do is open the network manager, uncheck and then recheck the wireless card.  It will then restart your wireless and log onto your router.  Thats what I do when it happens.  Works like a champ and takes a couple seconds compared to re booting.

---

### Post by dca on 2006-11-01
Cool, thanks.  Any ideas as to why it works sometimes on start-up but sometimes not???  Just curious...

---

### Post by lonce on 2006-11-01
It would do that to me until I did a fresh install of edgy.  When i booted the live CD.  I setup my wireless while still on the live CD then did the install.  It installed with my wireless setup and havent had the issue since.

---

### Post by trubblemaker on 2006-11-01
**if when you enter the following commds, all is OK!**
```
sudo iwconfig eth1 mode managed 
sudo iwconfig eth1 channel 10 
sudo iwconfig eth1 essid rookery 
sudo iwconfig eth1 key s:SKYCONNECTSK5 
sudo dhclient eth1

```

k this is a work around or a cheap hack their is likely a proper way to get this done, but as I have a girl that likes it when things "work" and doesn't car about "properly" I give you the work around.

you can add a post-up to your "/etc/network/interfaces" file to run those commands when you connect to the network.
Create a nice name like '/home/user-name/connextion':
```

#/bin/bash
sudo iwconfig eth1 mode managed 
sudo iwconfig eth1 channel 10 
sudo iwconfig eth1 essid rookery 
sudo iwconfig eth1 key s:SKYCONNECTSK5 
sudo dhclient eth1

```
then change the permissions so it can run
```
 chmod u+x connextion 
```
then add this to your "/etc/network/interfaces" 
```

auto lo wlan0
iface lo inet loopback

iface wlan0 inet dhcp
        post-up /home/user-name/connextion

```

now those commands will be run after the interface is brought up, 
(as an aside if for some reason any of the commands fail the device will not be brought up. This is good for troubleshooting and a intended effect.)  Alternatively you can run this as a pre-up to change things before you bring up the interface but then you should change things like not run "sudo dhclient wlan0" as that would be redundant and you would also need to "ifconfig eth0 up" before running commands I think but it's been a while.

Hope this gets you fixed up or helps point to the issue!

---

### Post by dca on 2006-11-01
Great, thanks...

---

### Post by kregen on 2006-11-01
great thanks.... trubblemaker 

it works... a very nice worksaroud.... :) 

ok, one litle problem: the system is waiting a long time and i don't know what is the system waiting for :confused: :-k

---

### Post by trubblemaker on 2006-11-01
waiting on boot? or to get a connection to the net? waiting for what?

---

### Post by trubblemaker on 2006-11-01
I'm going to guess that it takes a long time at boot to get going, this is becuase you technnically could be 

waiting to get dhcp
then after getting it you run a script that does this over again.

I mentioned that it wasn't a "fix" but a "work-around"  you could do the detection once with a pre-up, but this is less reliable if there are issues with your driver "waking up" properly (which seemed to be the original issue that was asked about)  regardless of where it's run (post/pre) it won't run as fast as a normal boot. Your running a script, and scripts are slower than a compiled program.

if you do want to try and getting it done with a pre-up, please remember the aforementioned issues with the script

---

### Post by kregen on 2006-11-02
after i have switch of the bootscreen.. i have seen that the laptop is waiting for a connection... it's ok, i go and have a cup of coffee... after returning the computer is ready :) 

thanks for all

i will wait for a fix 

cu
kai

---

### Post by puppy on 2006-11-02
Hmm, this is interesting because I've been having the same problem for about a week - on startup my Broadcom card (using ndiswrapper) is down. I have to issue commands 'ifconfig', 'sudo ifdown wlan0' and a 'sudo ifup wlan0' to get it to start. Once started however, it is absolutely rock solid and doesn't go down again, but I'm sure it was powering up automatically on startup before... strange.

---

### Post by trubblemaker on 2006-11-02
sounds like your /etc/network/interfaces file may need some tweaking.  I've also heard that some people that have issues with network cards do this before trying to connect

"/etc/network/interfaces"
```

auto lo wlan0
iface lo inet loopback

iface wlan0 inet dhcp
        pre-up ifconfig wlan0 down
        pre-up ifconfig wlan0 up
        pre-up ifconfig wlan0 down
        <config stuff>

```

this is like gently shaking the card awake before you try to configure it.  might help you if you do ifdown ifup. 

Are you switching networks alot?  --> can show you howto right a script to connect to your preferred networks.

If you're not switching what is the output of 
```
 iwlist scan 
cat /etc/network/interfaces
iwconfig

``` 
I might be able to see an error in your config.

---

### Post by puppy on 2006-11-02
that did the trick, trubblemaker - all green lights whenever I start gnome now - great, thanks :mrgreen:

---

### Post by euphro on 2007-11-06
I'm having the same problem with a Netgear WPNT511 pcmcia card on Gutsy.  Unless my /etc/network/interfaces file is blank (apart from loopback) I can't even get the card to work with the stop>start method in Network Manager. I'd love to be able to get it to work on boot without this fiddle.  The above work-around didn't work for me.  I did learn quite a bit though, so thank you :)

---

