---
title: "Wireless problems in Gutsy"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by rkakkar on 2007-10-29
As usual the network manager is acting funny. I have attached a screenshot displaying the problem. I was able to access the wireless network and surf the internet for a bit, but the minute I rebooted the link died. Now its just not communicating with any wireless network. ping simply returns "destination host unreachable". My wifi is well within range because it works in windows on the same machine. Earlier it used to automatically find my wireless network, but the minute i manually configured it, it no longer automatically detects my wireless network no matter how many times i shut it down or reboot my machine.

what could be the problem?

---

### Post by rkakkar on 2007-10-29
I'm using a D-Link wireless adapter card. Anyone?

---

### Post by thegentleman on 2007-10-29
So you did some manual configuration. Can you show us the /etc/network/interfaces file?

---

### Post by rkakkar on 2007-10-29
> **thegentleman said:**
> So you did some manual configuration. Can you show us the /etc/network/interfaces file?

sure man... here you go...i had to zip it in order to attach the file...

---

### Post by Trueno22 on 2007-10-29
have you tried using wicd to connect I completely dumped the netwrok manager in favor of it.

---

### Post by rkakkar on 2007-10-29
> **Trueno22 said:**
> have you tried using wicd to connect I completely dumped the netwrok manager in favor of it.

No. But I wouldn't mind try anything that works. I don't have internet connectivity on my linux box since the wireless is not working, but I have it on my windows box. Please tell me the location where I can get wicd and how do I go about installing in on kubuntu.

---

### Post by thegentleman on 2007-10-29
The key is ten chars in length. I suspect you didn't post the full key. That's good, but just to verify: is the key correct?

and what is the output of the command ```
iwconfig
``` 

actually I'm just repeating what the wiki says:
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)
[https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting](https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting)

not to disrespect your questions, but take a look and perhaps you could tell us what you've tried and what did and did not work.

---

### Post by rkakkar on 2007-10-29
> **thegentleman said:**
> The key is ten chars in length. I suspect you didn't post the full key. That's good, but just to verify: is the key correct?

and what is the output of the command ```
iwconfig
``` 

actually I'm just repeating what the wiki says:
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)
[https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting](https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting)

not to disrespect your questions, but take a look and perhaps you could tell us what you've tried and what did and did not work.

Hi, the key is correct and 10 characters long. iwconfig throws the following:

```
$ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"kaks"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:11:A2:23:24
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link Signal level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by MariusSilverwolf on 2007-10-29
You're not, by chance, using a Ralink based card are you?  They've been notoriously problematic in Gutsy, using the rt2x00 drivers instead of card specific drivers.

If, by the off chance you are, these might be of some help:

WUSB54Gv4: [http://ubuntuforums.org/showthread.php?t=588045](http://ubuntuforums.org/showthread.php?t=588045)
RT2500 PCI: [http://ubuntuforums.org/showthread.php?t=584657&highlight=rt2500](http://ubuntuforums.org/showthread.php?t=584657&highlight=rt2500)

If it's a different chipset, obviously those won't specifically work, but they might help with additional troubleshooting.

---

### Post by rkakkar on 2007-10-29
> **MariusSilverwolf said:**
> You're not, by chance, using a Ralink based card are you?  They've been notoriously problematic in Gutsy, using the rt2x00 drivers instead of card specific drivers.

If, by the off chance you are, these might be of some help:

WUSB54Gv4: [http://ubuntuforums.org/showthread.php?t=588045](http://ubuntuforums.org/showthread.php?t=588045)
RT2500 PCI: [http://ubuntuforums.org/showthread.php?t=584657&highlight=rt2500](http://ubuntuforums.org/showthread.php?t=584657&highlight=rt2500)

If it's a different chipset, obviously those won't specifically work, but they might help with additional troubleshooting.


Hi,

It started to work. I think it was a problem with a wrong network mask address. However I'm getting pathetic speeds: 1/10th the speed I'm supposed to get. And yes, I'm using a Ralink based wireless lan card. :-(. How can I get my speed back to normal?

---

### Post by thegentleman on 2007-10-29
Funny thing is, I had the same problem. I thought I didn't but when I switched on today, I had the exact same problem. rt61 in my case. I also got it working now. I was fooling around with all the Ralink topics. Even removed the gnome network manager, don't know if that's of any influence. Anyhow, this is what else I did.

I manually configured it to a static IP address.
/etc/network/interfaces looks like this (part of it):
```
iface wlan0 inet dhcp
address 192.168.100.102
netmask 255.255.255.0
network 192.168.100.1
wireless-key *mykey*
wireless-channel 5
wireless-essid *myessid*
```

Yeah, I know, I forgot the 'static'. But after an 'ifup' I did get the IP address.
After a reboot it still works, only I have to manual ifup the wlan0.

---

### Post by MariusSilverwolf on 2007-10-29
rkkakar,

WiFi speed is controlled by the effective transmit/receive rate the driver is controlling on the device.  In your case, it sounds like your the version of the driver you're using is disabling parallel communication or limiting the transmit/receive rate.

If you're using a PCI card, best bet to get an updated driver would be to follow the WUSB54G How-To, but substituting in the device specific driver package you need.  A guide listing the driver package to specific hardware can be found here: [http://rt2x00.serialmonkey.com/wiki/index.php/Hardware](http://rt2x00.serialmonkey.com/wiki/index.php/Hardware)

G'luck!  Let us know how it goes.

---

