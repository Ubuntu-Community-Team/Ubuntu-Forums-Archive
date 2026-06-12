---
title: "PLEASE HELP - Hardy + broadcom 4311"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by LaGzo on 2008-09-09
I need help getting my wireless to work. When I do *lspci* it doesn't even show the card name. I know it's a broadcom 4311 because it did work before. Please help me.

---

### Post by LaGzo on 2008-09-11
Anyone?

---

### Post by Crafty Kisses on 2008-09-11
The current (Spring 2008, kernel 2.6.24) wireless-2.6 branch of the linux kernel provides two new unified wireless drivers, called WifiDocs/Driver/b43 and b43-legacy. These drivers replace the old bcm43xx. The reason there are two is that b43 works with v4 broadcom firmware and b43-legacy works with the v3 firmware.

New b43 driver still doesn't work without proprietary firmware, which isn't included in Ubuntu and must be downloaded separately, using b43-fwcutter package (from Ubuntu universe) or simply by installing b43-firmware package from [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) (from Hardy distribution). New b43 driver doesn't work with old bcm43xx firmware. 

So lets get started, first you should install the following package: ```
sudo apt-get install ndisgtk
```
After you have that package installed, open the ndiswrapper, and find the .inf file from the driver you downloaded, you can download a pretty stable driver right [**here**.]("http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.28.tar.gz?modtime=1162136432&big_mirror=0")
So after you have extracted this file, look for the .inf file, and then obviously open it in **ndisgtk** then press install, and then do the following:
```
ndiswrapper -l
```
See if it recognizes the Wireless card, you may have competing drivers and you need to disable them, do the following:
```
gksu gedit /etc/udev/rules.d/70-persistent-net.rules
```If there are any lines assigning the name **wlan0** to a MAC identifier then either remove that line or comment it out with the **"#"** character. The line assigning the name eth1 may also need to be commented out.
If that does work, then you would probably want to create a record that looks like this: (I'm using 128bit WEP encryption)
```
iface wlan0 inet dhcp
wireless-essid My_Essid
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX
auto wlan0
```
One of the things you really have to do is make the ndiswrapper driver permanent, so you'd do the following:
```
/bcm4311$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
couldn't add module alias:  at /usr/sbin/ndiswrapper line 717.
```
Make sure you check the file /**etc/modprobe.d/ndiswrapper** file and make sure that the ndiswrapper alias is wlan0 an not something else such as eth1.

The second to last thing is of course, testing the device. Try this command in Terminal: ```
iwconfig
```You should get an output of something like this: ```
user@ubuntu:~bcm4311$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"My_Essid"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:08:74:02:01:FC
          Bit Rate:11 Mb/s
          RTS thr:2432 B   Fragment thr:2432 B
          Power Management:off
          Link Quality:95/100  Signal level:-35 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```
If you see that, everything should be OK, if I were you I'd run one more test, run this in the Terminal: ```
netstat -m
``` Then you should be able to see the correct setup of the network, and it will look something like this: ```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
0.0.0.0         192.168.0.2     0.0.0.0         UG        0 0          0 wlan0

```
Then try resetting the Network Manager by doing the following: ```
sudo /etc/init.d/dbus restart
```
Then you should be set. I'm aware this is a lot, but this should get it working, if you have any problems please let me know, thanks.

---

