---
title: "Broadcom 4311 ills"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by elpresidente on 2007-02-15
Just purchased a new laptop - Gateway MX8711 with a Broadcom 4311 wireless chipset (or so lspci says). The default driver used (in Edgy) is bcm43xx. This seems to load up fine. I can see the device in device manager and network settings. I can configure and enable it in network settings, putting in the essid (no encryption). Unfortunately, when I restart networking or attempt to ifup it, it will not get an IP (wireless works fine with multiple other computers). It says that the device (eth1) is not present. GTKwifi shows no wireless networks available but does see the card. I have tried using ndiswrapper with the bcmwl5 driver. That installs just fine (driver present, hardware present) but cannot find the device in device manager or in network settings or ifconfig.

I bought this laptop for my wife with no intention of running Windows, but if I can't get the wifi to work, I'll have to put it back on there for her (and of course the restore CD is not working - lol).

Please help me.

---

### Post by Floppyjoe on 2007-02-15
Did you blacklist the bcm43xx driver when you used ndiswrapper? This is required.
```
sudo gedit /etc/modprobe.d/blacklist
```
add the line:
```
blacklist bcm43xx
```
then save and exit gedit. A networking restart may be required or just reboot.

---

### Post by elpresidente on 2007-02-15
> **Floppyjoe said:**
> Did you blacklist the bcm43xx driver when you used ndiswrapper? This is required.

Yes, I did. And rebooted as well. I think I know what the problem is:

[http://wiki.waningsun.net/index.php?title=Dell_E1405_%26_Linux_HOWTO](http://wiki.waningsun.net/index.php?title=Dell_E1405_%26_Linux_HOWTO)

I found this article and it mentions that you need to compile a newer version of ndiswrapper, which I did not do (and which would make complete sense of my symptoms). Unfortunately, the laptop is at home, so I can't try it out right now but I will later on tonight and report back. Thanks for the reply.

---

### Post by Floppyjoe on 2007-02-15
Downloading and installing the new version of ndiswrapper is very easy. If you have an ethernet connection that works with the computer in question there is a walkthrough here:

[http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=3](http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=3)

---

### Post by elpresidente on 2007-02-16
Installing the latest ndiswrapper made no difference. It doesn't make sense to me. Ndiswrapper reports that the driver and hardware is present. Why won't it work?

---

### Post by Floppyjoe on 2007-02-16
Have you issued these commands?
```
sudo depmod -a
```
```
sudo modprobe ndiswrapper
```
```
sudo ndiswrapper -m
```
```
sudo gedit /etc/modules
```
Add the word ndiswrapper then save and exit gedit.

---

### Post by dbott67 on 2007-02-16
> **elpresidente said:**
> Installing the latest ndiswrapper made no difference. It doesn't make sense to me. Ndiswrapper reports that the driver and hardware is present. Why won't it work?

I just got mine working yesterday.  

**_Broadcom 4311 Wireless:_**

I was able to get the wireless card working, however, I needed to blacklist the existing bcm43xx module and use ndiswrapper:

1. Install **build-essential** from Synaptic (for compiling ndiswrapper)

2. Download latest stable version of **ndiswrapper** from [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)

3. Compile **ndiswrapper** according to [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

4.  Blacklist the bcm43xx module:
```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

5.  In order to get 'iwlist scanning' to display results, I needed to edit my /etc/network/interfaces file to contain the appropriate settings for my AP:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
[COLOR="Red"]wireless-essid MYSSID
wireless-key s:mysecretwepkey
[/COLOR]
auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

I'm not sure why my wireless card is now using eth1 (it used to be wlan0 in Dapper), but hey, it's working! :)

```
dbott@edgy:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:40:05:B2:AF:45
                    ESSID:"bott"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:92/100  Signal level:-37 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

[COLOR="Red"]Note: any kernel updates will require that ndiswrapper be recompiled[/COLOR]


Read the first post here for instructions on ATI, Beryl & Broadcom wifi for Edgy & Dapper:

[http://www.ubuntuforums.org/showthread.php?t=274915](http://www.ubuntuforums.org/showthread.php?t=274915)

-Dave

---

### Post by dekalbave on 2007-02-16
I have a Compaq Presario with a Broadcom 4311 miniPCIe card in it.  I used these rather complex instructions, and it works great with network-manager-gnome:

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

Hope this helps you out.

---

### Post by elpresidente on 2007-02-16
Wow. Somre great suggestions. I can't wait to try them out when I get home. I'll report back after.

Thanks to all!

---

### Post by elpresidente on 2007-02-17
> **dekalbave said:**
> I have a Compaq Presario with a Broadcom 4311 miniPCIe card in it.  I used these rather complex instructions, and it works great with network-manager-gnome:

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

Hope this helps you out.

Thank you for showing me this link. It was so comprehensive that I was able to finally get it working. I believe the fact that I hadn't copied the .conf may have made a difference. Anyway, thanks to all that helped. Now I can finish setting this new laptop up for my wife and she can enjoy her kickass Ubuntu laptop (by her request, God love her!)

---

