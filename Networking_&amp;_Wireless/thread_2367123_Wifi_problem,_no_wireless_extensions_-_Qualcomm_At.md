---
title: "Wifi problem, no wireless extensions - Qualcomm Atheros QCA9565 / AR9565"
date: 2017-07-26
forum: Networking &amp; Wireless
---

### Post by jeaniko on 2017-07-26
Hello everyone,

I have a problem with wifi on Asus laptop, maybe can anyone help me, this is an output from pastebin: [http://paste.ubuntu.com/25175670/](http://paste.ubuntu.com/25175670/)

Thank you in advance!

---

### Post by chili555 on 2017-07-26
Wow! That's a lot of drivers you have there!!!> rt73usb                36864  0
crc_itu_t              16384  1 rt73usb
rt2800usb              28672  0
rt2x00usb              20480  2 rt73usb,rt2800usb
rt2800lib              94208  1 rt2800usb
rt2x00lib              53248  4 rt2800lib,rt73usb,rt2800usb,rt2x00usb
asus_nb_wmi            28672  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
ath3k                  20480  0
ath9k                 147456  0
ath9k_common           36864  1 ath9k
ath9k_hw              466944  2 ath9k,ath9k_common
ath                    28672  3 ath9k_hw,ath9k,ath9k_common
mac80211              782336  4 rt2800lib,rt2x00lib,rt2x00usb,ath9k
cfg80211              602112  5 rt2x00lib,mac80211,ath9k,ath,ath9k_commonI assume that you tried a USB wireless or two or three and that the drivers are still loaded and conflicting. Please leave the USBs aside and reboot. Then let us have a new wireless script. We'd also like to see:```
dmesg | grep ath
```

---

### Post by jeaniko on 2017-07-26
Thanks for help, i have reinstalled, and now i have a fresh installation of Ubuntu 16.04.02, everything seems good, except wifi, the connectivity very weak, works only when sitting next to modem.

I ave updated, upgraded and after reboot no changes :/

This is a new output from pastebinit: [http://paste.ubuntu.com/25177229/](http://paste.ubuntu.com/25177229/)

root@tir:~# dmesg | grep ath
> [   17.136647] usbcore: registered new interface driver ath3k
[   17.502438] ath: phy0: WB335 1-ANT card detected
[   17.502440] ath: phy0: Set BT/WLAN RX diversity capability
[   17.511220] ath: phy0: Enable LNA combining
[   17.518115] ath: phy0: ASPM enabled: 0x43
[   17.518119] ath: EEPROM regdomain: 0x6c
[   17.518120] ath: EEPROM indicates we should expect a direct regpair map
[   17.518123] ath: Country alpha2 being used: 00
[   17.518123] ath: Regpair used: 0x6c
[   20.760156] ath9k 0000:02:00.0 wlp2s0: renamed from wlan0


---

### Post by chili555 on 2017-07-26
Please try:```
sudo modprobe -r ath9k
```Your wireless connection will stop.```
sudo modprobe ath9k btcoex_enable=1
```If it helps, make it permanent:```
sudo -i
echo "options ath9k btcoex_enable=1"  >  /etc/modprobe.d/ath9k.conf
exit
```I also notice this:> [   17.518120] ath: EEPROM indicates we should expect a direct regpair map
[   17.518123] ath: Country alpha2 being used: 00Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Any improvement?

---

### Post by jeaniko on 2017-07-27
Hello, thanks for help, i followed your instructions carefully - but not helped...

---

### Post by BenginM on 2017-07-27
Hiya , So what seems to be the problem now.. weak signal! Distance problems; *Physical* obstructions; Wireless interferences ..  

```

Distance problems ..

Wireless devices have limitations when it comes to their signal range.  For devices running on 2.4 GHz, the range can go up to 100-150 feet (30-46 meters).  If your wireless network devices are too far from each other, consider relocating the devices.  Remember that distance is directly proportional to signal strength.  The farther you are from the access point, the weaker the signal.

To check if you&#8217;re getting a stable connection, perform a continuous ping.  If you&#8217;re getting replies most of the time, this means the connection is stable.  If time outs are occurring frequently, the connection is not that stable. 

Wireless networks are susceptible to obstructions that may lead to low signal.  Oftentimes, the signal gets reflected, refracted, or absorbed by the obstruction.

Common obstructions are:

      &#8226;    Cabinets or drawers
      &#8226;    Mirrors, Glasses
      &#8226;    Metal Objects
      &#8226;    Thick walls and ceilings
      &#8226;    Aquariums

Wireless interferences..

Common sources of interference are:

      &#8226;    Neighboring wireless networks
      &#8226;    Microwave ovens
      &#8226;    2.4 GHz cordless telephones
      &#8226;    Bluetooth® devices
      &#8226;    Wireless baby monitors

To solve the problem, change the channel and SSID on the router.  Preferred channels to use are 1, 6, 9 and 11 since they&#8217;re considered as non-overlapping channels.


```
Sources :
[http://is6.nohold.net/Linksys/ukp.aspx?pid=80&vw=1&articleid=3759](http://is6.nohold.net/Linksys/ukp.aspx?pid=80&vw=1&articleid=3759)

##
if you don't have an extender wifi adapter you  might need one.

for the encryption security mode , WPA2 with AES is preferred.

you might also be hitting this bug :

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1160188](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1160188)

---

### Post by vasa1 on 2017-07-27
@BenginM, when you copy-paste material here which has been published elsewhere, please use [QUOTE] tags and provide appropriate credit to the source. This site doesn't approve of reproducing material the way you have done above. Any repetition of such activity may result in curbs on your posting privileges.

---

### Post by jeaniko on 2017-07-27
It is not a router problem! I have another notebook with Ubuntu and no problem..  

P.S. Before installation of Ubuntu on this "Asus" laptop all worked fine.

---

### Post by BenginM on 2017-07-27
> **vasa1 said:**
> [noparse]@BenginM, when you copy-paste material here which has been published elsewhere, please use [QUOTE] tags and provide appropriate credit to the source. This site doesn't approve of reproducing material the way you have done above. Any repetition of such activity may result in curbs on your posting privileges.[/noparse]

Hiya , Done. anything else ..! thanks for the love and support.

---

### Post by jeaniko on 2017-07-28
any help? :-?

---

### Post by jeaniko on 2017-08-06
:guitar:

---

### Post by BenginM on 2017-08-06
What's that suppose to mean ..! problem solved or what?

---

### Post by jeremy31 on 2017-08-06
I am not quite sure what is happening with the internal Atheros device but the following command should help your USB device
```
printf "[device]\nwifi.scan-rand-mac-address=0\n"| sudo tee -a /etc/NetworkManager/*.conf
sudo sed -i 's/2/3/' /etc/NetworkManager/conf.d/*
systemctl restart network-manager.service
```

The commands disable MAC randomization which causes issues with USB wireless devices in 17.04 and the other prevents Network Manager from trying to enable wifi power management

---

### Post by jeaniko on 2017-08-06
Thank you jeremy32 for help, my USB devices works good, except internal Atheros device.

[COLOR=#000000]Now i have a fresh installation of Ubuntu 16.04.02, everything works good, except internal Atheros device, the connectivity very weak, works only when sitting next to modem.[/COLOR]

[COLOR=#000000]This is a last output from pastebinit: [/COLOR][http://paste.ubuntu.com/25177229/](http://paste.ubuntu.com/25177229/)

[COLOR=#000000]root@tir:~# dmesg | grep ath[/COLOR]
[COLOR=#000000][I][ 17.136647] usbcore: registered new interface driver ath3k
[ 17.502438] ath: phy0: WB335 1-ANT card detected
[ 17.502440] ath: phy0: Set BT/WLAN RX diversity capability
[ 17.511220] ath: phy0: Enable LNA combining
[ 17.518115] ath: phy0: ASPM enabled: 0x43
[ 17.518119] ath: EEPROM regdomain: 0x6c
[ 17.518120] ath: EEPROM indicates we should expect a direct regpair map
[ 17.518123] ath: Country alpha2 being used: 00
[ 17.518123] ath: Regpair used: 0x6c
[ 20.760156] ath9k 0000:02:00.0 wlp2s0: renamed from wlan0 
[/I]
[/COLOR]
any ideas?

---

### Post by jeremy31 on 2017-08-07
I would check the antenna connections on the card

---

### Post by Hadaka on 2017-08-07
Hi, your country code is still unset..
Let's see if we can fix that, Please open a terminal
then Copy and paste..
```
sudo iw reg set AM
sudo sed -i 's/=.*/=AM/' /etc/default/crda
```
Where are you setting your static route of 192.168.2.229 for your wifi ?
in the router or in network interfaces ? Please post the output of..
```
cat /etc/network/interfaces
```
Thanks

---

