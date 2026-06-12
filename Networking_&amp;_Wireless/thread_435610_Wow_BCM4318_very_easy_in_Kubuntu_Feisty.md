---
title: "Wow BCM4318 very easy in Kubuntu Feisty"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by misfitpierce on 2007-05-07
Im guessing it would be the same in Ubuntu feisty but I just connected a lan cord for a few seconds.... updated like 5 updates... Typed in sudo apt-get install bcm43xx-fwcutter and it asked if i would like to obtain firmware... click yes and waalaaa... I gotta say im very impressed with this.

---

### Post by BinaryMadman on 2007-05-11
Wow, dude.  You are totally right.  I just wasted 45mins trying it with a script someone made until I copy & pasted what you wrote.  I have Ubuntu 7.04 and it really was freakishly simple! :)  The difficulty of setting up my wireless connection was what kept me from using Ubuntu as my main OS (hate being tethered with an ethernet cord) in the past.  Now that I know it will be this simple if anything happens, it'll be my main OS....w00t!

---

### Post by ghostboy on 2007-05-11
> **misfitpierce said:**
> Im guessing it would be the same in Ubuntu feisty but I just connected a lan cord for a few seconds.... updated like 5 updates... Typed in sudo apt-get install bcm43xx-fwcutter and it asked if i would like to obtain firmware... click yes and waalaaa... I gotta say im very impressed with this.

Are you serious?  It took me two days and this thread [http://ubuntuforums.org/showthread.php?t=197102]("http://ubuntuforums.org/showthread.php?t=197102") to get my wireless network working.  I didnt even think about the LAN connection! **_[COLOR="Red"]ARRRRGGGGGHHHHHHH!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!![/COLOR]_**

---

### Post by englandschorsch on 2007-05-30
> **misfitpierce said:**
> Im guessing it would be the same in Ubuntu feisty but I just connected a lan cord for a few seconds.... updated like 5 updates... Typed in sudo apt-get install bcm43xx-fwcutter and it asked if i would like to obtain firmware... click yes and waalaaa... I gotta say im very impressed with this.

Well, so was I until I tried an encrypted network. :(
I have a brand new Ubuntu Feisty installation on a Dell Latitude D620 here. I installed the bcm43xx-fwcutter an everything was fine. I could connect to my unprotected WLAN at home and surf the internet.

But when i came to the office last morning I could not connect to the Wlan there which uses WEP-Encryption. So please, let's not discuss WEP vs. WPA vs. WPA2, we all know what's secure and what's not. I have to connect via WEP as I am not the admin here.

The funny thing is that on the router here my laptop's MAC-address shows up as "authenticated". So apparently the WEP works. Still, I don't get any IP-address assigned and static IP doesn't work either. When I try it via the GUI, Ubuntu's Network Manager keeps coming back with a dialog and bugging me for WEP-Key input.

Here's part of my lsbpci output:
```
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

```

Here my procedure:
```

sudo ifconfig eth1 down
sudo iwconfig essid PILGRIM key s:fooba
sudo ifconfig eth1 up
sudo dhclient eth1

```
The DHCP-Client keeps sending DHCPDISCOVER forever and ever and ever... :(

A "sudo iwconfig" gives me the following output:
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"PILGRIM"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.447 GHz  Access Point: 00:06:B1:15:14:37   
          Bit Rate=11 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:6C75-6E64-79   Security mode:open
          Link Quality=58/100  Signal level=-64 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:1099  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
Any ideas?
Thanks a lot in advance.

---

