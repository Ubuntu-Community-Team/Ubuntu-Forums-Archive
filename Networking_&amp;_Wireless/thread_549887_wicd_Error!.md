---
title: "wicd Error!"
date: 2007-09-13
forum: Networking &amp; Wireless
---

### Post by kalej on 2007-09-13
While starting wicd gui ...

kalej@kalej-laptop:~$ /opt/wicd/gui.py 
attempting to connect daemon...
success
starting...
refreshing...
3
ESSID : FON_AP
making a new network entry...
disabling ip
disabling dns
0
ESSID : MyPlace
making a new network entry...
disabling ip
disabling dns
0
Traceback (most recent call last):
  File "/opt/wicd/gui.py", line 956, in <module>
    app = appGui()
  File "/opt/wicd/gui.py", line 695, in __init__
    self.refresh_networks(fresh=False)
  File "/opt/wicd/gui.py", line 878, in refresh_networks
    tempNetwork = PrettyWirelessNetworkEntry(x)
  File "/opt/wicd/gui.py", line 297, in __init__
    PrettyNetworkEntry.__init__(self,WirelessNetworkEntry(networkID))
  File "/opt/wicd/gui.py", line 539, in __init__
    print "ESSID : " + wireless.GetWirelessProperty(networkID,"essid")
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 169, in __call__
    reply_message = self._connection.send_message_with_reply_and_block(message, timeout)
dbus.DBusException: org.freedesktop.DBus.Python.UnicodeError: Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/dbus/service.py", line 488, in _message_cb
    _method_reply_return(connection, message, method_name, signature, *retval)
  File "/var/lib/python-support/python2.5/dbus/service.py", line 232, in _method_reply_return
    reply.append(signature=signature, *retval)
UnicodeError: String parameters to be sent over D-Bus must be valid UTF-8

The tray applet runs without any problem but when i try to start wicd gui gives me this error...
Does anyone have an idea?

ps - Sorry about my English

---

### Post by compwiz18 on 2007-09-13
Can you give the output of ```
sudo iwlist scan
``` when you get that error? thanks!

---

### Post by unisol on 2007-09-13
you could also try the wicd forum: [http://wicd.sourceforge.net](http://wicd.sourceforge.net)

---

### Post by imdano on 2007-09-13
I think we had someone else report this bug on launchpad, Adam.  It's a problem with a weird character being used in ESSIDs.  dbus can't handle them.  I think we either have to try to convert them to utf-8, or ignore the offending essid.

Also, no need to post on the wicd forums since two of our devs are reading this thread.

---

### Post by compwiz18 on 2007-09-13
Yeah, I figured it was that problem, but I wanted to confirm it.

I'll play around with it later and see if I can fix it.

to the OP: We're working on it :D

---

### Post by kalej on 2007-09-13
> **compwiz18 said:**
> Can you give the output of ```
sudo iwlist scan
``` when you get that error? thanks!

I also thought that could have anything to do with the essid but it's quite strange since the only wireless network that iwlist s discovers is my own network named "MyPlace" 

eth1      Scan completed :
          Cell 01 - Address: 00:18:84:2A:C0:7A
                    ESSID:"MyPlace"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=63/100  Signal level=-69 dBm  Noise level=-69 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 8ms ago

i hope that developers can fix this quick 'cause i'm tired of network-manager and i think that wicd is really a valid alternative.

---

### Post by imdano on 2007-09-13
Sometimes wireless cards won't display all the networks that are actually available when already connected to a network (I know my ipw3945 acts this way), because scanning for a long period of time can interrupt your connection.  Try running the scan a couple of times in a row, or disassociate from any wireless network you're on and scan again.

---

### Post by kevdog on 2007-09-14
Just curious to know if wicd utilizes wireless-tools - specifically iwlist to scan for available networks.  Would upgrading the wireless tools package be of any help, since the version installed with ubuntu is quite old.  I think the default version is 22 and the package is now distributing an alpha 29, beta 28, and stable v 27.  If this has nothing to do with anything, then just tell me Im way off base.

---

### Post by imdano on 2007-09-14
We do use iwlist to scan for networks.  I'm not exactly sure if getting a new version of wireless-tools will make a difference.  The crash is because a non-UTF-8 character is in the essid.  When wicd tries to send the essid over dbus, dbus crashes since it only supports UTF-8.  If the newer version of wireless-tools handle exotic characters differently, it might make a difference.

---

### Post by kevdog on 2007-09-14
Thanks for the clarification.  It seems a newer wireless-tools package wouldnt make a difference.  Just wondering if you've had a chance to check out the newer version.  Seems like the developer is trying to add in some wpa capabilities, however Im not exactly sure if they are working fully.  I know you had mentioned this as a great stumbling block for you with the different network cards, and wondered if any of these new options would be helpful for you (ie with ra cards).

---

