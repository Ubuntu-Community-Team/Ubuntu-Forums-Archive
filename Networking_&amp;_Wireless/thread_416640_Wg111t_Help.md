---
title: "Wg111t Help"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by Phoenix18G on 2007-04-21
Hello  recently i have installed ubuntu feisty:) 

But i try to install the drivers for this device with a little help from the ubuntu forums and ndiswrapper..

i install the drivers and i type ndiswrapper -l and i get this :

athfmwdl.inf harware present driver install
netwg11t.inf driver install

and when i type 

ifconfig wlan0

it returns a message and it writes device not found
when i go networking i do not see the interface ath0 or wlan0

What i am doing wrong here ? please help ?


PS:sorry about my english..

---

### Post by mstep on 2007-04-29
ok I had problems with this too.

As root run the command **gedit /etc/iftab/** then at the bottom of the file that opens, add this line:

**wlan0 mac 00:00:00:00:00:00**

Where all those zeroes are replaced by your card's mac address (should be on the side of the dongle somewhere).

---

### Post by Staudie on 2007-04-30
[http://http://ubuntuforums.org/showthread.php?t=258732&page=2&highlight=wg111t]("http://http://ubuntuforums.org/showthread.php?t=258732&page=2&highlight=wg111t")

Follow the instructions on post #13. This is what I used to get mine up and running.

-Staudie

---

### Post by rizwanjavaid on 2007-04-30
What I did was install those two drivers that you mention:

sudo ndiswrapper -i netwg11t.inf
sudo ndiswrapper -i athfmwdl.inf

then what I did was:

sudo depmod -a
sudo modprobe ndiswrapper

This should light up the WG111T card. If the system crashes, I restarted and then issued the modprobe command again and it worked.

I then issued the command:

sudo ndiswrapper -m

to save the config info and load on startup.

I then set my router encryption off and then in Ubuntu I issued the following:

sudo iwlist wlan0 scan

This found the router details with full info.

I then issued the command:

sudo iwconfig wlan0 essid <ESSID> ap <MAC ADDRESS>
sudo iwconfig wlan0 essid <ESSID> on

You can run:

sudo iwconfig

to check the wireless settings, hopefully all should be the same as your iwlist command you issued earlier. Then run your web browser and it should connect.

_WPA_

I had wpa_supplicant installed already on my machine. On command line I typed in:

sudo wpa_passphrase <ESSID>

This generates the passphrase and config for you on command line, simply paste this into a conf file on /etc/wpa_supplicant.conf

I then tested it like this:

sudo wpa_supplicant -i wlan0 -c /etc/wpa_supplicant.conf -D ndiswrapper -w

I got the output:

Trying to associate with 00:ff:00:1e:a7:7d (SSID='NetworkEssid' freq=0 MHz)
  Associated with 00:ff:00:1e:a7:7d
  WPA: Key negotiation completed with 00:ff:00:1e:a7:7d [PTK=TKIP GTK=TKIP]

I hit CTRL-c to terminate the app. 

I then needed to run wpa_supplicant on startup correctly so I edited /etc/network/interfaces:

Inside this file I looked for:

auto wlan0
iface wlan0 inet dhcp

and modified it to:

auto ath0
iface ath0 inet dhcp
wpa-driver ndiswrapper
wpa-conf /etc/wpa_supplicant.conf

Now when Ubuntu runs or shutdown, it automatically runs the wpa_supplicant for you. If you want to do it yourself too for testing run these commands:

sudo ifup wlan0
sudo ifdown wlan0

It should work without problems. I did it and restarted Ubuntu 3 to 4 times to make sure my USB dongle was picked up and also if detected and it did with no problems also running WPA mode.

Most of this is from the top of my head so there maybe some errors. Any problems post on here and I shall try and help as much as I can. I am a bit of an Ubuntu noob! :P

Regards,
Riz

---

