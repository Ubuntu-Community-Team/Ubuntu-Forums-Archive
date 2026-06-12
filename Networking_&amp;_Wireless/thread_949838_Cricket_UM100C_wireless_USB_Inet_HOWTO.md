---
title: "Cricket UM100C wireless USB Inet HOWTO"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by opm8 on 2008-10-16
The good news is that this thing works flawlessly with minimal config.  So far on the first day I'm getting up to 750kbps download speed and about 500kbps upload on a 3 out of 4 LEDs strength signal and am typing this post connected through it. :)

The bad news is that the device needs to be activated on a windows pc before it'll work on linux.  So run the setup cd you got with the device on a windows pc and activate it.  Then plug the device into your laptop.

Disclaimer: I'm running KDE on Debian but this should work in your flavor of *buntu. If you're using Gnome I think there's a gppp.

Once you've done that there are two ways to initiate a connection: kppp and wvdial.

1) kppp, the preferred choice since this one automatically sets up your routing table after you connect, gives you a pretty status icon with blinking lights for network activity and has a nice bandwidth graph.
```

sudo apt-get install kppp
```

Create a blank /etc/ppp/peers/kppp_options file because kppp will complain that the file doesn't exist otherwise. I fiddled with my ppp settings so I'm not sure if this file existed in the first place.

From a root prompt start up kppp:
```
$ sudo kppp
```

Click Configure.

Create a new account, giving it the phone number #777.  Authentication PAP/CHAP.

Click the Modem tab and add a modem.  Give it /dev/ttyACM0 as the "Modem device".  Check the output of dmesg to be sure that's where it got recognized.

OK out of all these windows, then put in your USB device phone numbers as the LoginID.  Password is "cricket" without the quotes.  Click Connect and you're done.

2) wvdial, works just as well but you have to manually add a default route after you connect.  

```
sudo apt-get install wvdial
```

Run wvdialconf then edit your /etc/wvdial.conf.  You'll need to change the three commented out entries: Username, Password, and Modem (maybe not Modem, I can't remember what the 3rd one was ;) )

/etc/wvdial.conf:
```
[Dialer Defaults]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Phone = #777
ISDN = 0
Username = 1112223333
Init1 = ATZ
Password = cricket
Modem = /dev/ttyACM0
Baud = 460800
```

To be on the safe side, check the output of dmesg to see if the device is recognized at /dev/ttyACM0, which is the default.

Run wvdial as root:
```
$ sudo wvdial
```

In the console output of wvdial find the line that looks like this:
```
--> local  IP address 10.6.105.163
```
then add this as your default gateway:
```
sudo route add default gw 10.6.105.163
```

Done!

---

### Post by cr33dog on 2009-01-26
The device works for me in gnome, using gnome-ppp (kppp hangs on new account) - under 8.10 (Intrepid).

In 8.10, it also appears under Network Manager, although I have no idea if it was there before I ran through gnome-ppp.

In 8.04, gnome-ppp works, but it is not shown in Network Manager - so you manually have to put FF in online mode on startup.

Chris

---

### Post by SithLord_101053 on 2009-02-10
I have this device, but gedit will not allow me to save the modification. It says that I don't have permission....Please advise

---

### Post by JK3mp on 2009-02-10
Well thats good. My verizon air card works perfect too. I just used wvdial to dial it out.

---

### Post by inhalentbroom on 2009-02-11
@Sithlord

try open gedit through the command line with gksu

```
gksu gedit /etc/wvdial.conf
```

See if that will let you save your changes.

---

### Post by XRzero4 on 2009-04-10
I have .
Will these instructions work for the Cricket USB model A600 as well?
I was told the 100 has been discontinued when I went in to buy this one.
Anyone played with one of these yet?

---

### Post by ricprice on 2010-04-06
Yes, A600 does work with Ubuntu -- found instructions at 

[http://www.ubuntugeek.com/how-to-setup-cricket-wireless-a600-broadband-modem-in-ubuntu.html](http://www.ubuntugeek.com/how-to-setup-cricket-wireless-a600-broadband-modem-in-ubuntu.html)

pretty easily done.  I got it up and running in about 10 min - and I'm a newbie.

---

### Post by pdc on 2010-04-06
well done; thanks for that; good to know which blogs are most helpful; enjoy

---

