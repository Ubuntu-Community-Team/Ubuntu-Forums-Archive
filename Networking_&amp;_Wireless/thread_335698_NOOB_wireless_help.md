---
title: "NOOB wireless help"
date: 2007-01-10
forum: Networking &amp; Wireless
---

### Post by gloscherrybomb on 2007-01-10
Hi,

I'm in desperate need of some help, for a few different probably related issues.

1. I have an INPROCOMM 2220 Wireless Car din my laptop, and have successfully installed the drivers for it using ndiswrapper.

2. using system>administration>networking I can get it to work if I disable then enable the device, but it doesn't work from when I restart the computer.

3. Network manager doesn't even recognise the fact there is a wireless card on my computer, it works fine for a wired connection but shows nothing at all to do with a wireless connection.

I have fiddled with lots of different files from guides on the net and hope it isnt because of this that its not working. If you need and information from the console just tell me what to do...

Please help!
!

---

### Post by gloscherrybomb on 2007-01-10
By the way my network interfaces file looks like this:

auto lo
iface lo inet loopback

#iface eth0 inet static
#address 192.168.2.19
#netmask 255.255.255.0
#gateway 192.168.2.1

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp
#wireless-essid belkin54g

#auto eth0

#iface wlan0 inet dhcp
#address 192.168.0.5
#netmask 255.255.255.0
#gateway 192.168.0.1
#wireless-essid SKY57247
#wireless-key s:WCRPPJGD

#auto wlan0

---

### Post by meng on 2007-01-10
Well, assuming that your wireless interface is wlan0, and the ESSID and WEP key are correct (just tell me where you live and I'll be in the area real soon to get free internet access....) ahem! Then just edit your interfaces file to remove all the comment symbols (#) from the last 6-7 lines, that should get your wlan0 started automatically at boot.

---

### Post by gloscherrybomb on 2007-01-10
Doesn't work I'm afraid!

Do you know why networkmanager isn't recognising anything wireless?

---

### Post by usererror on 2007-01-10
If network manager works for the WIRED network, but not wireless and it doesn't even SEE the wireless card...this was the same problem I had.

In order to fix it I had to remove the Check Mark on "enable this device" under System > Administration > Network ...

Once I removed that check ( i may have rebooted I can't remember, no maybe I just #'ed out all my /etc/network/interfaces (that's how it's set now) and then killed network-manager and then restarted it and also /etc/init.d/networking restart ) Network-Manager started seeing my wifi card and i have not had any problems since for WPA & WEP networks.

hopefully that'll help. :-k

---

### Post by gloscherrybomb on 2007-01-10
Tried that and made no difference!

---

### Post by gloscherrybomb on 2007-01-11
Please can  someone help me, its almost so bad as to force be back on to windows.

---

### Post by Vox754 on 2007-02-13
Look here
[http://ubuntuforums.org/showthread.php?t=324967](http://ubuntuforums.org/showthread.php?t=324967)

[http://ubuntuforums.org/showthread.php?t=339802&highlight=inprocomm](http://ubuntuforums.org/showthread.php?t=339802&highlight=inprocomm)

---

