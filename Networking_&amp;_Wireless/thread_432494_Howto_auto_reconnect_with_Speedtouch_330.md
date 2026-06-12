---
title: "Howto auto reconnect with Speedtouch 330"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by lethu on 2007-05-04
Since there were many people (including me) asking in vain for how to make their Speedtouch modem auto reconnect, here is the solution which I found by simply reading the pppd man.
All you have to do is adding "persist" (without the quotes) to your pppd configuration file which is usually located in the peers folder (/etc/ppp/peers/) and named speedtch in case you followed the Ubuntu's community documentation ([https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch](https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch)) to install your modem.
Below you can see how your file should look after adding the magic word : ).

```
#noipdefault
defaultroute
user 'xxx@xxx'
noauth
updetach
[COLOR="Sienna"]persist[/COLOR]
#usepeerdns
plugin pppoatm.so
8.35

### You may need to uncomment these
### options to connect with some ISP's.
### They disable compression.

 noaccomp
 nobsdcomp
 nodeflate
 nopcomp
 noccp
 novj
 novjccomp

### If the firmware loads and pppd won't
### connect uncomment this option to make
### pppd be more verbose in the system log

# debug

### For more details (and more options)
### Read man pppd
```

Of course besides the "persist" command your list shouldn't look exactly the same, as it depends on your ISP's configuration.
That's it, now pppd will reconnect all alone, no more "pppd call speedtch" every 24 hours : ).
Hope this helps, cya!

---

### Post by lethu on 2007-05-21
I just discovered a new USB ADSL Modem Manager project designed for Gnome that supports Speedtouch modems and the next release enhancements of which will be options to enable/disable the redial if connection dropped function. Another very attractive feature is the availability of a tray icon that reports the state of the modem and its connection status. What? Still reading? Rush download and try this new gem :p!

The main project's launchpad : [https://launchpad.net/usb-adsl-modem-manager](https://launchpad.net/usb-adsl-modem-manager)
Deb packages for Ubuntu 6.06, 6.10, 7.04 : [http://www.squeezedonkey.com/svn/linux/trunk/releases/](http://www.squeezedonkey.com/svn/linux/trunk/releases/)

Enjoy :).

---

