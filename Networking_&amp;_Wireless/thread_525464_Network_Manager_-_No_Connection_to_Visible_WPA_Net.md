---
title: "Network Manager - No Connection to Visible WPA Network"
date: 2007-08-14
forum: Networking &amp; Wireless
---

### Post by bwinfrey on 2007-08-14
OK, Here's what Ive got:
Laptop running Ubuntu 6.06
Linksys card - used fwcutter for driver
Linksys router - WPA TKIP
```

iwconfig:
eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.484 GHz  Access Point: 00:18:39:57:82:38
          Bit Rate=11 Mb/s   Tx-Power=10 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I am able to see the wireless network in Network Manager.  I have modified these files as per instructions:
```

sudo gedit /etc/network/interfaces

```
Comment out everything other than &#8220;lo&#8221; entries in that file and save the file
```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

#iface eth1 inet dhcp
#wireless-essid ####
#wireless-key s:########

```
Create a file called /etc/default/wpasupplicant, add entry ENABLED=0 and save the file
```

ENABLED=0

```
```

sudo touch /etc/default/wpasupplicant

```
```

sudo /etc/init.d/dbus restart

```
At this point Network Manager attempts to login, but the icon's indicators never change to green on tx or rx.  The networking finally falls back to wired if connected or disconnected if not connected to wired.

I had this configuration running in FC4, but was disatisfied with FC6 and after tesing many distros decided on Ubuntu.  Any help is appreciated.

---

### Post by bmartin on 2007-08-14
I highly recommend you use something other than Network Manager to deal with wireless connectivity. A lot of people have had success with **wifi-radar**, which is in the Universe repo (you can add that repo via Synaptic). Another option is [wicd]("http://wicd.sourceforge.net/download.php"), but it's not in a supported repo; wicd claims to have built-in support for WPA1/2 and other kinds of security. It also has a nifty tray icon. Both are written in Python.

I hope this works for you. If you ever need to set up a Broadcom chipset again, try [this thread]("http://ubuntuforums.org/showthread.php?t=405990").

---

### Post by kevdog on 2007-08-14
Have you installed the wpasupplicant package??? You need this package to use wpa.  It looks like you are using the instructions from the debian admin website.  

Have you tried just connecting from the command line -- ie perform a manual connection to your wpa router rather than an automatic approach line networkmanager??  Sometimes this gives some debugging information.

If you could post the following it would help:

iwlist scan
lshw -C network

Thanks

---

### Post by bwinfrey on 2007-08-15
Thanks for the ideas.

bmartin - I'd like to stick with the supported package, as I've had it working before.  I may wind up using something else if it doesn't work out - probably just script it.

I changed my configuration.  Uninstalled fwcutter and used the script in this post
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

Installed wifi-radar and left network manager (is that a problem?).  I get no connection with either.

The error reported using static ip is:
```

sudo wifi-radar -d
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; Invalid argument.
SIOCADDRT: File exists

```

---

