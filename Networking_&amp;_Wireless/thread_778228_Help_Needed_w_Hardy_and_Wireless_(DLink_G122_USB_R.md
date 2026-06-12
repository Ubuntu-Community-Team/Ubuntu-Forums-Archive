---
title: "Help Needed w/ Hardy and Wireless (DLink G122 USB Rev B)"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by r.d. on 2008-05-01
Hi,

This is my first post to these wonderful forums, which I have found to be very helpful in even getting a wireless connection to work.

My problem, however, is that my initial connection appears ok, I get activity lights on the DLink USB stick, but after a few seconds, my signal strength drops significantly.  As a result, surfing the web is incredibly slow, and on occasion, Firefox just gives up trying to load the web pages.

Pasted below are the outputs of some diagnostic commands I have run:

**lsusb**

Bus 002 Device 002: ID 413c:3010 Dell Computer Corp. Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 2001:3c00 D-Link Corp. [hex] DWL-G122 802.11g rev. B1 [ralink]
Bus 001 Device 001: ID 0000:0000  



**iwconfig** (initially was 55/100, but dropped as per below)

wlan0     IEEE 802.11g  ESSID:"mynet"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:B7:AA:BA   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=34/100  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


**lshw -C network**

  *-network DISABLED
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth0
       version: 10
       serial: 00:4f:4e:12:86:6e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:13:46:63:99:87
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.100 multicast=yes wireless=IEEE 802.11g


**cat /etc/network/interfaces**

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless_essid mynet
#wlan_ng_key0 xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx
wireless_mode managed
wireless_enc on
wireless_key xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx
wlan_ng_authtype sharedkey

pre-up iwconfig wlan0 rate 54M


------------------

What am I missing here?  Why can't my connection remain as strong as it was when it runs on XP?  Any help is much appreciated.

Thanks,
R.D.

---

### Post by r.d. on 2008-05-02
Here's some additional info..

**sudo ndiswrapper -l**

netrtusb : driver installed
	device (2001:3C00) present (alternate driver: rt2500usb)


And the wireless interface (wlan0) is WEP-enabled.  Please help with the signal strength.. This is driving me crazy!!

---

### Post by acad1 on 2008-05-02
[http://ubuntuforums.org/showthread.php?t=739139&page=3](http://ubuntuforums.org/showthread.php?t=739139&page=3)

Have a look at the above link. I installed the rt2570 driver along with rtutilt and my usb device, which is the same as yours, now works with 8.04 and 7.10.

Sorry, I think my device is Rev B1, so the driver may be different to yours

---

### Post by r.d. on 2008-05-02
Thank you - I will give that a try later today and will post my results.

---

### Post by r.d. on 2008-05-02
acad1,

I've installed the rtutilt application as well as the rt2570 drivers (I also have the Dlink Rev B1 version), and while my link quality has improved to about 85%, I do not get an IP address (when looking at the Link Status screen from within rtutilt).

Do I need to clear out my /etc/network/interfaces file? Could it be conflicting with the default Network Manager program?

I'm not sure what to try next, but I appreciate your help on this..!

---

### Post by acad1 on 2008-05-03
r.d.
Sorry for not getting back to you, but I have been re-installing 8.04 and getting rid of 7.10. I have had a few problems getting a wireless connection again on the fresh install, but eventually made it. I think one should shut down and re-start the machine after making any changes, and that seems to help. I have not un-installed Network Manager. I don't have much experience with Ubuntu as yet but I will be willing to exchange the data I get for "ifconfig, iwlist" and so on, if you think that will help.
I have made no changes to my /etc/network/interfaces file but can post you my info, if it will help. By the way I am using WEP.

I notice that you are using ndiswrapper. I am not using this.

---

### Post by r.d. on 2008-05-03
Thanks acad, I am also using WEP. Whatever you could post that you think might be helpful, would definitely be appreciated.  I love 8.04 - it's just the wireless networking that's holding things up!

---

### Post by acad1 on 2008-05-04
> **r.d. said:**
> Thanks acad, I am also using WEP. Whatever you could post that you think might be helpful, would definitely be appreciated.  I love 8.04 - it's just the wireless networking that's holding things up!

Have you completed the information in Network Settings?
System > Admin > Network Settings then fill in Network Name, Password Type, Network Password. In Configuration Settings, select Automatic (DHCP) then click OK.
I think I eventually re-booted the computer, before the connection was made.

In Network Settings, my USB wireless device is identified as rausb0.
I can post my information for lsusb. iwconfig, lshw -C network, cat /etc/network/interfaces if you wish.

---

### Post by r.d. on 2008-05-04
I've tried that before with no luck, but will try it again now and reboot.  Would I need to also enter it into the rtutilt program?  

Yes, if you could post the results of those commands, that would be helpful.  Thanks again for your help!

---

### Post by acad1 on 2008-05-04
> **r.d. said:**
> I've tried that before with no luck, but will try it again now and reboot.  Would I need to also enter it into the rtutilt program?  

Yes, if you could post the results of those commands, that would be helpful.  Thanks again for your help!

I have not entered anything into the rtutilt program, but the program does show the signal strength and IP information when connection is made.


andy@andy-desktop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 2001:3c00 D-Link Corp. [hex] DWL-G122 802.11g rev. B1 [ralink]
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000  
andy@andy-desktop:~$ iwconfig
lo        no wireless extensions.

rausb0    RT2500USB WLAN  ESSID:"G604T-WIRELESS"  Nickname:""
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:1B:2F:72:75:A8   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=85/100  Signal level:-56 dBm  Noise level:-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

andy@andy-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: ATM network controller
       product: AccessRunner PCI ADSL Interface Device
       vendor: Conexant
       physical id: 2.1
       bus info: pci@0000:01:02.1
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32
  *-network
       description: Wireless interface
       physical id: 1
       logical name: rausb0
       serial: 00:13:46:63:1e:ae
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.3 multicast=yes wireless=RT2500USB WLAN
andy@andy-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface wlan0 inet dhcp
wireless-key **************************
wireless-essid G604T-WIRELESS

auto wlan0

iface rausb0 inet dhcp
wireless-key **************************
wireless-essid G604T-WIRELESS

auto rausb0
andy@andy-desktop:~$

---

### Post by r.d. on 2008-05-04
Thanks, I've had to switch to a cable connection to get things to work for now.

Here is my output:

**lsusb**
Bus 002 Device 002: ID 413c:3010 Dell Computer Corp. Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 2001:3c00 D-Link Corp. [hex] DWL-G122 802.11g rev. B1 [ralink]
Bus 001 Device 001: ID 0000:0000  

**iwconfig**
wlan0     IEEE 802.11g  ESSID:"mynet"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:B7:AA:BA   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=-115 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:82/100  Signal level:-43 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**lshw -C network**
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth0
       version: 10
       serial: 00:4f:4e:12:86:6e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.100 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:13:46:63:99:87
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netrtusb driverversion=1.52+D-Link,04/01/2004, 1.00.00. ip=192.168.0.102 multicast=yes wireless=IEEE 802.11g

**cat /etc/network/interfaces**
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
pre-up iwconfig wlan0 rate 54M
wireless-key **************************
wireless-essid mynet

I see that I have the ndiswrapper reference in my drivers, and you didn't.  How do I replace it?

---

### Post by acad1 on 2008-05-04
> **r.d. said:**
> Thanks, I've had to switch to a cable connection to get things to work for now.

Here is my output:

**lsusb**
Bus 002 Device 002: ID 413c:3010 Dell Computer Corp. Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 2001:3c00 D-Link Corp. [hex] DWL-G122 802.11g rev. B1 [ralink]
Bus 001 Device 001: ID 0000:0000  

**iwconfig**
wlan0     IEEE 802.11g  ESSID:"mynet"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:B7:AA:BA   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=-115 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:82/100  Signal level:-43 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**lshw -C network**
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth0
       version: 10
       serial: 00:4f:4e:12:86:6e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.100 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:13:46:63:99:87
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netrtusb driverversion=1.52+D-Link,04/01/2004, 1.00.00. ip=192.168.0.102 multicast=yes wireless=IEEE 802.11g

**cat /etc/network/interfaces**
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
pre-up iwconfig wlan0 rate 54M
wireless-key **************************
wireless-essid mynet

I see that I have the ndiswrapper reference in my drivers, and you didn't.  How do I replace it?

I am not sure, but check the link below to uninstall ndiswrapper:

[http://ubuntuforums.org/showthread.php?t=222184](http://ubuntuforums.org/showthread.php?t=222184)

Your usb device appears to be called wlan0 - Did you use "sudo ifconfig wlan0 up" in the terminal?

---

### Post by pytheas22 on 2008-05-04
If you and acad both have the same wireless device (which lsusb confirms), then the alias for both of you should be rausb0.  But in your case, r.d., it is wlan0.  This is probably because you are still using ndiswrapper to drive the device, instead of the serialmonkey drivers.

To prevent ndiswrapper from loading, run the command:

```
sudo echo "blacklist ndiswrapper" >> /etc/modprobe.d/blacklist
sudo echo "blacklist rt2500usb" >> /etc/modprobe.d/blacklist

```

Then run:
```

sudo modprobe -r ndiswrapper
sudo modprobe -r rt2500usb
sudo modprobe rt2570
sudo ifconfig rausb0 up
```

If these commands run without errors, then open rutilt and see if you can connect.  If you still can't, post the output of "iwconfig" after the commands above have been run.

EDIT: after looking at Alien.col's thread, I realized that another problem could be the default wireless drivers interfering with the ones you installed from serialmonkey, so I've added commands above to make sure you blacklist the bad drivers as well.

---

### Post by r.d. on 2008-05-05
Thanks guys.  I will try the recommendations later tonight and post the results.

---

### Post by Alien.col on 2008-05-05
Guys check this out: [http://ubuntuforums.org/showthread.php?t=783366](http://ubuntuforums.org/showthread.php?t=783366)

I wrote that guide, hopefully it will help.

Cheers

---

### Post by r.d. on 2008-05-06
Pytheas22, I ran through the steps to disable ndiswrapper, and it still seems stuck on rausb0.

Here's the output of iwconfig:

rausb0    RT2500USB WLAN  ESSID:"mynet"  Nickname:""
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=11 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-50 dBm  Noise level:-84 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Alien, I'll try your guide out next, thanks... Most likely tomorrow though

---

### Post by Alien.col on 2008-05-06
To unable ndiswrapper simply unable the driver:

    * "Ndiswrapper -e"  drivername  This allows you to remove an installed driver. (where drivername is the name of your driver, ex. bcmwl5)

---

### Post by pytheas22 on 2008-05-06
> Pytheas22, I ran through the steps to disable ndiswrapper, and it still seems stuck on rausb0.

Here's the output of iwconfig:

rausb0 RT2500USB WLAN ESSID:"mynet" Nickname:""

You want it to be rausb0, so that's good...ndiswrapper is no longer controlling the card.  Did you try connecting with both Network Manager and Rutilt and had no luck with either?  If so, what was the behavior like, and if you run Rutilt from a command line and try to connect, what output do you get?

Also, do you get any results if you run the command:

```
iwlist rausb0 scan
```

---

### Post by r.d. on 2008-05-06
Hi guys, thanks again for all the help.  Still no go though.  Here's the output:

**iwconfig**
rausb0    RT2500USB WLAN  ESSID:"mynet"  Nickname:""
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-48 dBm  Noise level:-84 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

(And the iwscan on rausb0 didn't turn up anything)

Because I'm able to get things connected using a LAN cable, along with the fact that I'll be moving in a couple of weeks, I think I'll be taking a bit of a break from connecting wirelessly.  I was hoping to get it working sooner rather than later, but, such is life!

Thanks again everyone... I will be back!

---

### Post by acad1 on 2008-05-07
How can I find out which wireless driver is being used? I notice in both r.d.'s and my own readout of iwconfig, it states:

rausb0 RT2500USB WLAN ESSID:

I have installed the rt2570 driver and as far as I am aware have not blacklisted rt 2500 driver.

---

### Post by pytheas22 on 2008-05-07
Two things:

acad, what is the output of:

```
cat /etc/modprobe.d/blacklist
```

and r.d.,

please open terminal and run the command:

```
sudo ifconfig rausb0 up
```

then start Rutilt by typing:

```
rutilt
```

now try to connect to your network.  If it fails on the first try, wait ten seconds and press the connect button again.  If it still doesn't work, close Rutilt, and then please copy and paste here all of the information that has been dumped to the terminal since starting Rutilt.

And also, just to be sure: acad, you are using Rutilt to connect and have no problems, right?  And you compiled the serialmonkey drivers, yes?

---

### Post by acad1 on 2008-05-07
andy@andy-desktop:~$ cat  /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

andy@andy-desktop:~$ 

Above is my output for the blacklist. Yes, rutilt is running OK, and I did compile the driver for rt 2570 from the serial monkey as you had described to me previously for 7.10. I re-installed 8.04 and managed to get the wireless connection up and running again using your previous instructions. So now I only have 8.04 on my hard disk.

---

### Post by r.d. on 2008-05-07
pytheas, thanks - I will give that a try this evening and will post the output.

---

### Post by r.d. on 2008-05-07
Pytheas, I thought I had it there........

I ran the "sudo ifconfig rausb0 up" line and had it working after a reboot!  The bad news is that, as I was typing my reply here, the connection dropped by the time I hit "post"... So close...!

Here's the output of iwconfig after I ran the commands, and before the reboot:

rausb0    RT2500USB WLAN  ESSID:"mynet"  Nickname:""
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:13:46:B7:AA:BA   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=79/100  Signal level:-49 dBm  Noise level:-84 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

We're almost there it seems.  I just don't know why the connection dropped like that all of a sudden.  Now, whenever I reboot, I no longer get a link light on the USB stick...

---

### Post by pytheas22 on 2008-05-07
That's strange that the connection would die.  Was Rutilt still running when it died?  Try connecting again using Rutilt.  If you can't connect on the first try, wait ten seconds and click connect again (the reason I emphasize this is because I used to have to click connect twice in Rutilt...it always failed the first time for some obscure reason...using a card very similar to yours).  It would still also be helpful if you ran Rutilt from the command line and posted the output that you get there.

Also, another potential problem that I've just thought of is that Network Manager is trying to interfere.  This could be why the connection dropped...sometimes NM does dumb things and interferes with other wireless managers.  So before starting Rutilt, run:
```

sudo kill -9 $(ps -e | grep NetworkManager)
```

to kill NM.

---

### Post by Alien.col on 2008-05-08
> **r.d. said:**
> Pytheas, I thought I had it there........

I ran the "sudo ifconfig rausb0 up" line and had it working after a reboot!  The bad news is that, as I was typing my reply here, the connection dropped by the time I hit "post"... So close...!

Here's the output of iwconfig after I ran the commands, and before the reboot:

rausb0    RT2500USB WLAN  ESSID:"mynet"  Nickname:""
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:13:46:B7:AA:BA   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=79/100  Signal level:-49 dBm  Noise level:-84 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

We're almost there it seems.  I just don't know why the connection dropped like that all of a sudden.  Now, whenever I reboot, I no longer get a link light on the USB stick...

Try and configure your network called "mynet" in the network manager. If the stick can't connect it won't light up, even if the device is operating properly.

---

### Post by pytheas22 on 2008-05-08
> Try and configure your network called "mynet" in the network manager. If the stick can't connect it won't light up, even if the device is operating properly.

This may work, but I wanted to point out that as far as I know, none of the serialmonkey drivers will work with Network Manager.  You have to use Rutilt if you're using the serialmonkey drivers.  Network Manager might be able to see the device and make you think that it can connect, but it won't work.  So I would keep on trying with Rutilt if I were you.

As a disclaimer, however, I haven't used the serialmonkey drivers since Gutsy, so it's possible that they now work with NM, but I would be surprised.

---

### Post by acad1 on 2008-05-08
I don't want to confuse the issue, but I entered my wireless data through System>Administration>Network and it was accepted, I think after one or two attempts. RuTilt WLAN Manager was installed but I have never entered any data into this. If I type rutilt in the terminal it opens the RutilT WLAN Manager Box and all of the details about the connection are shown.
I used the serialmonkey driver to install rt2570 driver in 8.04, but I don't think I blaclisted any drivers - see #22 above.

---

### Post by Alien.col on 2008-05-08
> **pytheas22 said:**
> This may work, but I wanted to point out that as far as I know, none of the serialmonkey drivers will work with Network Manager.  You have to use Rutilt if you're using the serialmonkey drivers.  Network Manager might be able to see the device and make you think that it can connect, but it won't work.  So I would keep on trying with Rutilt if I were you.

As a disclaimer, however, I haven't used the serialmonkey drivers since Gutsy, so it's possible that they now work with NM, but I would be surprised.

I use the rt2570 with network manager, i don't use the rutil utility. I used the network manager with gutsy also.

---

### Post by Alien.col on 2008-05-08
> **acad1 said:**
> I don't want to confuse the issue, but I entered my wireless data through System>Administration>Network and it was accepted, I think after one or two attempts. RuTilt WLAN Manager was installed but I have never entered any data into this. If I type rutilt in the terminal it opens the RutilT WLAN Manager Box and all of the details about the connection are shown.
I used the serialmonkey driver to install rt2570 driver in 8.04, but I don't think I blaclisted any drivers - see #22 above.

So did it work???

Try uninstalling rutil and working with network manager, just give it a shot, if not you can go back to rutil.

Network manager works but i've noticed lately that it puts the usb stick to sleep if i leave my connection idle for a while. It does recover the connection without problems when that happens though.

---

### Post by r.d. on 2008-05-08
Thanks guys, I will give this a try this weekend

---

### Post by acad1 on 2008-05-09
> **Alien.col said:**
> So did it work???

Try uninstalling rutil and working with network manager, just give it a shot, if not you can go back to rutil.

Network manager works but i've noticed lately that it puts the usb stick to sleep if i leave my connection idle for a while. It does recover the connection without problems when that happens though.

Hi Alien.col 
I already have the DLink G122 Rev B1 working on 8.04 and also have NWM and Rutilt installed, and there appears to be no conflict. I also installed the rt2750 driver using serialmonkey.

---

