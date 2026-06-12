---
title: "Wireless drops connection periodically"
date: 2006-12-07
forum: Networking &amp; Wireless
---

### Post by Sam Lars on 2006-12-07
I upgraded to Edgy, and since then the wireless has been weird.  It works fine, but after a while it will stop.  I have to iwconfig the card and reset the rate and sometimes the channel and then set the ap to auto to get the network back up.  Then after a while it will stop working again.
/etc/network/interfaces
```
auto eth0

iface eth0 inet static
    address 192.158.7.103

    netmask 255.255.255.0

    network 192.158.7.0

    broadcast 192.158.7.255

    gateway 192.158.7.1

    wireless-essid essid

    wireless-key key

    wireless-rate 11M

    wireless-channel 11

    wireless-mode managed

    wireless-ap auto
```
I also think I have to ifup eth0 whenever I start the computer because it doesn't happen automatically.

---

### Post by dbott67 on 2006-12-07
Can you post a little information about your hardware.

Specifically, the output from the following 2 commands:
```
dbott@edgy:~$ **sudo lshw -C video**
Password:
  *-display:0
       description: VGA compatible controller
       product: RV350 AP [Radeon 9600]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@01:00.0
       version: 00
       size: 256MB
       width: 32 bits
       clock: 66MHz
       capabilities: vga bus_master cap_list
       configuration: driver=fglrx_pci
       resources: iomemory:e0000000-efffffff ioport:d800-d8ff iomemory:bf800000-bf80ffff irq:217
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV350 AP [Radeon 9600] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@01:00.1
       version: 00
       size: 256MB
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       resources: iomemory:c0000000-cfffffff iomemory:bf000000-bf00ffff

```
and
```
dbott@dapper:~$ **sudo lshw -C network**
Password:
  *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:ce:31:88:6f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.25 firmware=Broadcom,11/02/2005, 4.10.40.0 ip=192.168.1.105 link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:dfcfc000-dfcfffff irq:169
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:0c:ad:05
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=0.97 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:df9fe000-df9fffff irq:217

```

Thanks,
Dave

---

### Post by Sam Lars on 2006-12-07
```
  *-display               
       description: VGA compatible controller
       product: Riva128
       vendor: NVidia / SGS Thomson (Joint Venture)
       physical id: 0
       bus info: pci@01:00.0
       version: 22
       size: 16MB
       width: 32 bits
       clock: 66MHz
       capabilities: vga bus_master cap_list
       resources: iomemory:fd000000-fdffffff iomemory:db000000-dbffffff irq:11

```

```
  *-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@00:0e.0
       logical name: eth0
       version: 03
       serial: 00:0f:66:74:0c:76
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.17-10-generic ip=192.158.7.103 link=yes multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:febfe000-febfffff irq:10

```

---

### Post by dbott67 on 2006-12-07
Okay.. it seems you've got the nVidia card and you're using NDISWrapper with Broadcom (a couple of the symptoms that others have had).

The next 2 things to check for are:
1. Check dmesg log for ndiwrapper IRQ conflict
```
dmesg | grep 177
```
If there's a message that ndiswrapper is disabling irq #177 then you more than likely need to change your video driver.

2. Which video driver are you using?
```
cat /etc/X11/xorg.conf
```

When you have the proprietary binaries installed, you should have a section:
```
Section "Device"
    Identifier     "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
    Driver         "**[COLOR="Red"]nvidia[/COLOR]**"
        Option          "RenderAccel"           "true"
EndSection
```

If you have the 'nvidia' driver listed, this is the trouble.  Apparently the 'nvidia' driver is causing issues with the Broadcom wireless.  Try changing the driver to 'nv'.

[http://www.ubuntuforums.org/archive/index.php/t-193350.html](http://www.ubuntuforums.org/archive/index.php/t-193350.html)


Other references (start at post #42) in this thread:
[http://www.ubuntuforums.org/showthread.php?t=295787&page=5](http://www.ubuntuforums.org/showthread.php?t=295787&page=5)

The official bug:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57355](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57355)

-Dave

---

### Post by Sam Lars on 2006-12-07
Sorry, I'm actually using the Broadcom support with the kernel.  I should also mention that there is a second computer with the same card and same symptoms with Edgy.

---

### Post by dbott67 on 2006-12-07
> **Sam Lars said:**
> Sorry, I'm actually using the Broadcom support with the kernel.  

Oops... of course you are... I don't know what I was reading there. 

When the network drops out, what is the output of the following commands:
```
dbott@dapper:~$ **ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:15:C5:0C:AD:XX
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:438044459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:438044459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1712747473 (1.5 GiB)  TX bytes:1712747473 (1.5 GiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:CE:31:88:XX
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe31:886f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:738503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:500344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:658372626 (627.8 MiB)  TX bytes:64530804 (61.5 MiB)
          Interrupt:169 Memory:dfcfc000-dfd00000
```
and
 
```
dbott@dapper:~$ **iwlist scanning**

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :

Cell 01 - Address: 00:40:05:B2:AF:YY
              ESSID:"bott"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=34/100  Signal level=39/100  Noise level=11/100
              Encryption key:on
              Bit Rate:22 Mb/s

Cell 02 - Address: 00:05:5D:FA:B2:XX
              ESSID:"soni"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=24/100  Signal level=27/100  Noise level=12/100
              Encryption key:on
              Bit Rate:54 Mb/s

sit0      Interface doesn't support scanning.
```

Also, check dmesg for any clues.  Other possible causes are EMI/RFI interference from cordless phones. 

-Dave

---

### Post by Sam Lars on 2006-12-08
```
 ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0F:66:74:0C:76  
          inet addr:192.158.7.103  Bcast:192.158.7.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:66ff:fe74:c76/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:191764 errors:0 dropped:1322 overruns:0 frame:0
          TX packets:312210 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:66929419 (63.8 MiB)  TX bytes:268071308 (255.6 MiB)
          Interrupt:10 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11081 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11081 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:998537 (975.1 KiB)  TX bytes:998537 (975.1 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

```
iwlist scanning
lo        Interface doesn't support scanning.

eth0      Scan completed :
          Cell 01 - Address: 00:0F:66:57:F3:74
                    ESSID:"winetworkufounodos"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-51 dBm  
                    Extra: Last beacon: 80ms ago

sit0      Interface doesn't support scanning.


```

```
[17268649.188000] bcm43xx: Controller RESET (TX timeout) ...
[17268650.220000] bcm43xx: Controller restarted

```

It's weird, because everything looks as it should, really.  It's just that in iwconfig the rate is at 1Mb/s.  Setting it to 11 still doesn't bring up the network, but once I set ap to auto, even though that looks fine too, it starts working.

---

### Post by dbott67 on 2006-12-08
A few things come to mind:
1. Check the AP website for updates to firmware. Make note of your settings before updating, as the updates tend to reset router to factory defaults.
2. Try changing the AP channel from 11 to 6 (or 1)
3. (Temporarily) turn off encryption to see if the problem persists

-Dave

---

### Post by ildfroe on 2006-12-09
Hello

I have the same problem with the wireless connection dropping. When the connection drops, I go to the system -> network and deactivate/activate the card.
I use the bcm43xx driver, fglrx driver and no ndiswrapper. 
I never had any problems on dapper, and no problems on warty, hoary, and breezy with ndiswrapper. And no problems on windows.

---

### Post by kingcharles1666 on 2006-12-09
I have the same issue, but i believe it has to do with the changes in the nm-applet. it used to keep the interface up all the time.

---

### Post by eggdeng on 2006-12-09
I have this problem too but using a Conceptronic USB Wireless Adapter, so it's not exclusive to Broadcom. It persists with the nvidia driver disabled, so, in my case, it doesn't seem to be a driver conflict either. No problems on the windows partition.](*,)

---

### Post by dbott67 on 2006-12-09
Is everyone that is having this problem running Edgy?

Maybe someone brave soul that is running Edgy can re-install Dapper & see if they still have the problem.  It may well be related to network manager.

-Dave

---

### Post by ildfroe on 2006-12-09
Well, as I said, I didn't have any problems on dapper. It's only edgy. And I really don't know if it's related to network manager or some other thing. And I don't know how to check... (Well, maybe install network manager from dapper. But I don't know if it's possible nor how to do it).

---

### Post by Sam Lars on 2006-12-09
[http://mirror.anl.gov/pub/ubuntu/pool/main/n/network-manager/](http://mirror.anl.gov/pub/ubuntu/pool/main/n/network-manager/)
I'd get the package from there and install it.  I'm not sure which one would be the Dapper version, and I'm not sure how it would work out.  I might try that.

---

### Post by Sam Lars on 2006-12-09
Actually I guess that's the special manager that I never got to work...
And I'm not sure what application would configure the network...

---

### Post by Sam Lars on 2006-12-09
What I did was copy all of the edgy sources in my sources.list and made them edgy, so that Synaptic now reads both Edgy and Dapper packages.  You can force it to install the Dapper version.  I'm not sure which package, though.

---

### Post by Sam Lars on 2006-12-09
Well I installed gnome-system-tools from Dapper, and tried starting the Network Settings, but after typing in my password it told me I had the wrong password, even though gksudo passed it.  And when I opened it again, there was no gksudo, and it still said I had the wrong password.

---

### Post by ildfroe on 2006-12-10
Yes, I was afraid something like that would happen when installing an older package. Good try though :-)

---

### Post by fredj on 2006-12-11
I have Dapper installed on a Samsung Q35 notebook and I use
network-manager to connect to my wireless network and it also
drops the connection periodically. Its the only problem I still
have to solve but obviously it's not just an Edgy problem more
likely a network-manger problem.

---

### Post by saz on 2006-12-11
hey, dbott, could you please have look here?
[http://www.ubuntuforums.org/showthread.php?t=316917]("http://www.ubuntuforums.org/showthread.php?t=316917")

cuz maybe you could help me, thnks, anyway ;)

---

### Post by eggdeng on 2006-12-12
Has anyone else found that, even when the network is unreachable (you can't ping the router), the wireless card is still seeing the access point (iwconfig will tell you the mac address of the ap). This has to point to a problem somewhere higher up than the actual physical connection issue.

---

### Post by sitara on 2006-12-20
I have a similar problem on one machine and no problem on another. Both machines are running edgy.

The machine that works flawlessly:

Has an Nvidia card.
Is running an SMC wireless card.
Was upgraded from Dapper via update-manager.
Has a very strong signal +/- 60.

The machine that drops the connection:

Does not have an Nvidia card.
Has a new install of edgy from CD.
Has a Senao wifi card (same chipset provider as SMC).
Has a weaker signal +/- 20

I find it takes a lot of fiddling to get the interface back up when it is dropped. Does anybody have a reliable solution?

Thanks,

Keith

---

### Post by J`ve on 2006-12-20
I have 2 laptops with edgy.
first one has a 2200bg and it runs perfectly. (it has an older installation and i didnt make any update since)
second one has an intel 2100b. i was installed and updated fresh edgy 2 days ago. but its disconnects nearly every 5min. at office. (%60 Coverage)
but at home (%100) its much better. 1 hour or more.. but its still disconnecting..
both networks have Wpa encryption and we have two different AP (Asus & 3com)

---

### Post by Sam Lars on 2007-01-02
I don't know if this helps anyone, but I made an icon on my panel to run this command:
```
sudo iwconfig eth0 rate 11M ap auto
```
All I have to do is type in my password and the network reconnects and works again.
I also opened a bug on my problem here: [https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/77747](https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/77747)

---

### Post by nahfuten on 2007-01-09
I am having this problem too with the bcm43xx.  Something else strange that I noticed though...

If my connection is dead, and I attempt to load a page in Firefox (unsuccessfully), and I then attempt to bring up the terminal, it will fail loading.  I also cannot type in any program, as if my keyboard died.

If my connection dies, and I DO NOT load Firefox, the terminal comes up fine.

---

### Post by firstc624 on 2007-01-17
I too have this happen.  My edgy is running the bcm43 drivers and i don't knwo if it is specifically associated w/ that or not.

Does anyone knwo if the nidswrapper conenction is better?

---

### Post by Sam Lars on 2007-02-08
I'm not sure what the cause is, but lately it seems to have gotten worse.  I haven't noticed any packages in question updated and I haven't changed anything that I know of.
Doing the iwconfig commands won't always do it alone anymore.  I've ended up with an AP of "Invalid."  If I do an iwlist scanning, it will set that, but sometimes set the wrong channel.  I have to do a lot of working to get rate, channel, and AP to be correct, since to set the channel I must set AP to "auto" to "set" the changes, and doing that sometimes sets the AP to "Invalid," which is reset by iwlist, which sometimes messes up the channel...
Just a little update.  I'm hoping they get this fixed sooner rather than later, since it is a rather annoying problem, especially since it takes some fiddling now.

---

### Post by ildfroe on 2007-02-09
It seemed to get worse for me too. A few days ago I dist-upgraded to Feisty, and so far there hasn't been any problems :-)

---

### Post by bennybawlz on 2007-02-09
I have this problem, too, on a Toshiba Satellite laptop with a Belkin 54g PCMCIA card, which has a Broadcom wireless chipset (bcm43xx).

I am not using nVidia drivers. I am, of course, using Edgy.

Another poster mentioned that the keyboard seems to stop working in relation to this problem. I am having the same experience. I can't yet confirm that the keyboard stops loading as soon as I launch Firefox (after the connection has dropped-out), but I will check for that the next time it happens.

I am using 128-bit WPA.

---

