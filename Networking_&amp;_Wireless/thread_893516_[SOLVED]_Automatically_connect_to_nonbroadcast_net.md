---
title: "[SOLVED] Automatically connect to nonbroadcast network"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by gig4ls on 2008-08-18
Hi guys, I'm new here. I searched the forums to see if there were any posts by keywords and I didn't find anything, so if there is a thread or threads that address my issue, please let me know!

My situation is that whenever I start up my ubuntu (heron), I have to manually connect to my wireless. I would like ubuntu to automatically connect to the wireless similar to how other OSs might.

Using the GUI I've been having 0 success (and I hear it's not the most reliable way anyway); I disable roaming and enter in the specifics of my wireless, and upon the next restart i am not connected to my network (or any others, since I disabled roaming).

Some notes on my configuration:
Network: wpa, nonbroadcasting ssid, wireless g, dhcp set by router
Machine: built-in wireless (not a separate pcmcia card) for b + g

If anyone has any suggestions or needs more info, please let me know. Thanks for your help!

---

### Post by Sam Lars on 2008-08-18
I would suggest working with your /etc/network/interfaces file... could you post what's in that file here?  If it has your password/key in it you can remove that before posting.

---

### Post by jimv on 2008-08-18
Use WICD instead of NetworkManager.  Then go into WICD, add your wireless network, put in your encryption info, and check "Automatically Connect to this Network"

---

### Post by gig4ls on 2008-08-18
> **Sam Lars said:**
> I would suggest working with your /etc/network/interfaces file... could you post what's in that file here?  If it has your password/key in it you can remove that before posting.


This is what's in the file:
--------------------------
auto lo
iface lo inet loopback

allow-hotplug wlan0
--------------------------

I am currently connected (obviously)

---

### Post by Sam Lars on 2008-08-19
I think trying WICD as jimv suggested is a good idea.
If you want to try the interfaces file, you can also check out this guide:
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo?highlight=(wpa](https://help.ubuntu.com/community/WifiDocs/WPAHowTo?highlight=(wpa))

---

### Post by gig4ls on 2008-08-20
WICD refuses to work, even if I set my ssid to broadcast and encryption off, so I tried editing the interfaces file directly. After that, I then renewed my interfaces, and this is what I got:
--------------------------
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                           * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...fail!
run-parts: /etc/network/if-down.d/50firestarter exited with return code 2
There is already a pid file /var/run/dhclient.wlan0.pid with pid 6276
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
--------------------------
Should I be worried about these last two lines?

---

### Post by Sam Lars on 2008-08-22
Yes, I don't think that's a good sign.  It looks WICD is trying to get an IP address, but it isn't able to use the card.  Could you post your interfaces file with the changes you made to it?

---

### Post by gig4ls on 2008-08-23
Thanks for all of your help, despite the clearly confusing situation that I was in :)
I flattened and reloaded Ubuntu and now my wireless connection sticks. For the record, I can't say that anything in my configuration is different, I just used the network manager and added the connection manually.
Upon examining the interfaces file, I can see nothing interesting:

_____
auto lo
iface lo inet loopback
_____

I will mark this thread as answered.

---

