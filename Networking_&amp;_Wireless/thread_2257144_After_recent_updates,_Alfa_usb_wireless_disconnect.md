---
title: "After recent updates, Alfa usb wireless disconnects often"
date: 2014-12-17
forum: Networking &amp; Wireless
---

### Post by esheesle on 2014-12-17
I've been running on Ubuntu 14.04 for a while now and had no big problems with my alfa usb card.  It's been up for weeks at a time.  All of a sudden about 3-4 weeks ago after I allowed some updates, it now drops every 5-60 minutes.  By drop, I mean it disconnects from the wifi ap and doesn't even try to reconnect (and sees no wifi networks in network-manager).  If I restart network-manager it immediately starts working again.  Same if i ifconfig down and up the adapter.

Any clues on what I can do to get it to remain more stable?  If not, any ideas on how to best monitor the interface in an automated fashion and at least have it auto down/up to keep connectivity mostly functional?

The dmesg shows this right beforehand:
ieee80211 phy0:  wlan0:  No probe response from AP xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx after 500ms, disconnecting

---

### Post by chili555 on 2014-12-17
> eee80211 phy0: wlan0: No probe response from AP xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx after 500ms, disconnectingThat's the whole answer. Your computer asks the router to respond every 500 ms. Hearing no response, it gives up and disconnects. We can increase the timeout to 1000, 3000, or whatever milliseconds but the better way is to address the router.

What signal strength are you seeing?```
iwconfig
```> wlan0     IEEE 802.11abgn  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: xx:D7:19:41:54:xx 
          Bit Rate=78 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          [COLOR="#FF0000"]Link Quality=59/70[/COLOR]  Signal level=-51 dBm  
If it is low, indicating that the router is far away or has a few walls between it and you, then you might see if changing the orientation of the router helps. In my own case, I get better signal strength with the router propped up at an angle. My old router supplied better strength standing on its nose.

If your router has antennas, move them around and try to get a better link quality. Some routers allow you to increase the transmit power: [http://s18.postimg.org/imunrlb21/16_6_2014_2_05_19.png](http://s18.postimg.org/imunrlb21/16_6_2014_2_05_19.png) If yours does, you might increase it slightly.

Finally, you might ask the system to increase the probe response time. In a terminal:```
sudo -i
echo "options mac80211 probe_wait_ms=3000"  >  /etc/modprobe.d/mac80211.conf
exit
```Reboot and tell us if disconnects are gone or at least improved.

---

### Post by esheesle on 2014-12-17
Signal strength is pretty low (far end of my house and several walls between).  I'll try the increased checkin but am curious why all wifi ap's disappear out of network-manager after this happens (normally can see 5, but after this occurs i see none even when trying to force a scan).  Almost seems like either the kernel module or network-manager itself has a bit of an issue (that never happened before updates a month ago).

---

### Post by chili555 on 2014-12-17
Let's turn our attention to the driver. Please run and post:```
lsusb
```

---

### Post by esheesle on 2014-12-17
Bus 002 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 13ba:0018 PCPlay Barcode PCP-BCG4209
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c521 Logitech, Inc. Cordless Mouse Receiver
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1058:1001 Western Digital Technologies, Inc. External Hard Disk [Elements]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



Just happened again even with the increased timeout.  This time error said 3000ms like expected as well.  It tries to reassociate but fails seemingly.  Still odd that a simply down/up of the adapter fixes it though.

---

### Post by esheesle on 2014-12-19
Should I try building drivers for the adapter myself by chance?

Anyone know of an application or script that can quickly check for the association status of a wifi adapter and then execute an action based on it (could allow me to at least bounce the adapter automatically)?

---

### Post by chili555 on 2014-12-19
Before we build a different, maybe better, maybe worse driver, I suggest you try the suggestions here, not including the different driver, at the accepted answer: [http://askubuntu.com/questions/453110/rtl8187-wireless-card-drops-signal-within-seconds](http://askubuntu.com/questions/453110/rtl8187-wireless-card-drops-signal-within-seconds)

---

### Post by esheesle on 2014-12-19
Giving those a try now.  Should know within an hour.  Odd that it started in recent updates though.  Makes me think some change in the kernel or module caused it.

---

### Post by esheesle on 2014-12-20
Tried those settings and while it seemed to stay up for longer, the adapter still dropped after 5 hours or so.  Any ideas?

---

### Post by warren3 on 2014-12-20
I'm having the same probem after a big update a week ago.  I have an Intel 7260 PCI-E module and wifi just craps out after a few minutes.  I have a connection but it just tries to load a page indefinitely.  It was fine before the update.

I am having to load a previous kernel to get it back to normal.  I just hope this gets fixed in the next update.

---

### Post by chili555 on 2014-12-20
> **warren3 said:**
> I'm having the same probem after a big update a week ago.  I have an Intel 7260 PCI-E module and wifi just craps out after a few minutes.  I have a connection but it just tries to load a page indefinitely.  It was fine before the update.

I am having to load a previous kernel to get it back to normal.  I just hope this gets fixed in the next update.Since you haven't an Alfa USB wireless, the subject of this thread, I suggest you start your own new thread.

---

