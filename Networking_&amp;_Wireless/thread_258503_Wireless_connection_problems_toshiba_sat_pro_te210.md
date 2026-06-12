---
title: "Wireless connection problems: toshiba sat pro te2100, minitar PCI card"
date: 2006-09-16
forum: Networking &amp; Wireless
---

### Post by roncrump on 2006-09-16
Hi,

As I sit here typing this my wife is sat at the other side of the table streaming video happily from the UK on a windows XP laptop.

Meanwhile, my wireless seems to bounce up and down - either going from
0 to about 80% connectivity, or no change showing on the monitoring tool but me sitting here waiting while sites are being looked up, connected to, waited for. Very frustrating.

I have Dapper installed, all updated, on a Toshiba Satellite Pro TE2100. The wireless router/ADSL modem is a billion 7500G, with the firmware all up to date.

My wireless card is a minitar CardBus card, it is based on one of the supported chipsets (Ralink? Something like that). Would it be worth trying ndiswrapper?

Are there any tools I can use to diagnose my problems? Any suggested routines?

Better still, any suggested solutions? This is getting frustrating.

Regards,
Ron.

---

### Post by roncrump on 2006-09-16
Ok, no replies yet.

Looking into ndiswrapper. My cardbus card is not listed on the ndiswrapper compatability list: the MN54GCB (ie Broadcom chipset) is, but not the MN54GCB-R (Ralink chipset). I presume this is not definitive and it may work.

My wife is happily streaming media from the BBC at the moment. I'm struggling to read football reports. I'm sure it isn't just relative positioning of our computers - we both use our PCs from different spots in the flat, and I always have more problems than she does (she hardly has any).

If I start, can I back out to the current ralink 2500 kernel support? Easily?

If I get into this am I in danger of making things worse? 

Ron.

---

### Post by unco on 2006-09-17
Mate your in luck, I have just got back to looking at ubuntu after a year and a half, having given up last time because not being able to get wireless to work. But guess what, I got it going sweet as.

Even better is I am the kind of geek that writes howtos and have just done so.  Problem is that the post hasn't shown up on the ubuntu forum.

But even better I put it on my own site first either search on ubuntu for 'HOWTO: Configure Minitar MN54GPC Wireless PCI Card with WPA'
or go to [www.intodis.com/info](www.intodis.com/info) and then into ubuntu/linux and then look for same title.

But even better my router is also Billion 7500G.

Good Luck

---

### Post by unco on 2006-09-17
Seems needs a moderator to approve the content so he ya go:

**HOWTO Summary**
A complete set of steps for configuring a Minitar MN54GPC Wireless PCI Card (but could be ported to any card i guess) on Ubuntu 6.06 LTS using ndiswrapper and also configuring to use WPA encryption.

**References** *(can skip this)*
Thanks goes to their respective authors:
[LIST]
[*][*(Post #1) Configuring wireless connection with ndispwrapper*]("http://www.ubuntuforums.org/showthread.php?t=201902")
[*][*(Post #1) Configuring wpa_supplicant*]("http://www.ubuntuforums.org/showthread.php?t=253028")
[*][*(Post #13) My first (semi-success) but good reference howto from 2 years ago*]("http://ubuntuforums.org/showthread.php?t=22312&page=2")
[/LIST]

**HOWTO Instructions**

[LIST=1]
[*]Install Ubuntu 6.06 ...

[*]Update Ubuntu .... (need internet connection)

[*]Update following files, Change any *eth1* references to *wlan0*
```
sudo gedit /etc/modprobe.d/ndiswrapper
sudo gedit /etc/network/interfaces
sudo gedit /etc/iftab
```
[*]Restart ubuntu to bind wlan0 in place of eth1

[*]Open System\Administration\Networking from the main menu and close by clicking 'OK' to populate the /etc/network/inferfaces file .  This should have shown wireless connection as wlan0.  If not need to repeat step 3 and 4.

[*]For broadcom cards:
```
sudo rmmod bcm43xx
```
*if yours is different then need to find the appropriate driver reference being used (refer to first reference link above for how to do this ...)*

[*]```
sudo gedit /etc/modprobe.d/blacklist
```
And add following to the bottom and save
```
# custom wireless card setup ...
blacklist bcm43xx
```
[*]```
sudo apt-get install ndiswrapper-utils
```
*Need internet connection or get off cd.*

[*]Goto card makers site and download the driver zip file to the Desktop, In this case I got *802.11g USB, PCI & CardBus Updated Drivers (4.1.19.29)* from the Minitar download page.

[*]This code unzips the file, creates /drivers/wireless folder to hold driver files, move appropriate drive files and backs up zip to wireless folder.
```
unzip ~/Desktop/4.1.19.29.zip -d ~/Desktop/
mkdir ~/Desktop/wireless
sudo mkdir /drivers
cp ~/Desktop/4.1.19.29/driver/Windows_2000/ms68bm.* ~/Desktop/wireless
cp ~/Desktop/4.1.19.29.zip ~/Desktop/wireless
sudo mv ~/Desktop/wireless /drivers/wireless
sudo rm -rf ~/Desktop/4.1.19.29.*
sudo rm -rf ~/Desktop/4.1.19.29
```
[*]```
sudo ndiswrapper -i /drivers/wireless/ms68bm.inf
```
*Your driver folder can be anywhere, and your driver .inf file may have different name if not using same driver.*

[*]```
ndiswrapper -l
```
Check that hardware is present.

[*]```
sudo ndiswrapper -m
```
[*]```
sudo modprobe ndiswrapper
```
[*]```
sudo apt-get install wpasupplicant
```
[*]```
sudo gedit /etc/wpa_supplicant.conf
```
To create/edit the WPA settings file.  And add the following to the file.
```
ctrl_interface=/var/run/wpa_supplicant

network={
  proto=WPA
  key_mgmt=WPA-PSK
  ssid="MyEssid"
  psk="TopSecret"
}
```
These are all the settings I needed. But you may need more so check out reference link 2 above and also /usr/share/doc/wpa_supplicant/examples.

The psk can also be encrypted using passphrase (but I haven't been able to get this to work yet, will update if I can work it out):
```
# which wpa_passphrase
/sbin/wpa_passphrase

# sudo /sbin/wpa_passphrase MyEssid TopSecret
network={
         ssid="MyEssid"
        #psk="TopSecret"
         psk=e46827d16672b883657307d7e8e12823c63cbfa7a6d5a8364f5d8aa8bbbeacb2
}
```
[*]```
sudo gedit /etc/network/interfaces
```
and add at the bottom of the file
```
pre-up modprobe ndiswrapper
pre-up iwconfig wlan0 essid MyEssid
pre-up iwconfig wlan0 mode Managed
pre-up ifconfig wlan0 up
pre-up wpa_supplicant -D ndiswrapper -i wlan0 -c /etc/wpa_supplicant.conf -B w
pre-up ifconfig wlan0 down
```
[*]```
sudo /etc/init.d/networking restart
```
To restart your networking.
[/LIST]

**Troubleshooting**
[LIST]
[*]Show the network configuration.
```
iwconfig
```
[*]Show wireless access points that you card is picking up.
```
iwlist wlan0 scan
```
[*]Start the wireless connection.
```
ifconfig wlan0 down
```
[*]Stop the wireless connection.
```
ifconfig wlan0 up
```
[*]Useful debugging/error details shown when using flag -dd.
```
wpa_supplicant -D ndiswrapper -i wlan0 -c /etc/wpa_supplicant.conf -B w -dd
```
[/LIST]

---

### Post by roncrump on 2006-09-18
Cheers for that.
I shall work my way through it.
Ron.

---

