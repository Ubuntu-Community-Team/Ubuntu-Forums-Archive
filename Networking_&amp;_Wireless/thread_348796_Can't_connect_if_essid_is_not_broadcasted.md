---
title: "Can't connect if essid is not broadcasted"
date: 2007-01-29
forum: Networking &amp; Wireless
---

### Post by blekc on 2007-01-29
Hi,

My system works **fine as long as** my AP broadcasts it's ssid. If I ask the ssid to be hidden (no broadcast), I can't connect anymore through *network manager*. My configuration :

Computer

[LIST]
[*]HP Pavillion ze2000
[*]Edgy Eft 32 bits
[*]integrated Broadcom 4318 chispset
[*]ndiswrapper driver
[*]network manager
[/LIST]

Access Point

[LIST]
[*]Linksys WRT54G
[*]DD-WRT v23 SP2
[*]WPA-PSK
[/LIST]

Any idea ?

I'm sorry if it's a common question but I didn't find any thread about it....

Bleck

---

### Post by PreachersPoker on 2007-02-26
Same issue... I read the sticky about hacking up the network file.  Doesn't seem in line with "It Should 'Just Work'(tm)". :confused: 

I made the following changes to enable WPA (source:  [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html))

sudo apt-get
sudo apt-get install wpasupplicant
sudo apt-get install network-manager-gnome network-manager
sudo gedit /etc/network/interfaces
Comment out everything other than “lo” entries in that file and save the file
Create a file called /etc/default/wpasupplicant, add entry ENABLED=0 and save the file
sudo touch /etc/default/wpasupplicant
Reboot your system or use the following command
sudo /etc/init.d/dbus restart

And that works like a charm...except...

If the wifi router is configured to not broadcast the SSID, I cannot connect.  I can manual enter it -- still no luck.  If I change the setting to 'broadcast SSID', I'm on.

I would like to not broadcast my SSID.  I've been actively hunting for 4 days now (I don't do much at the office :) )

---

