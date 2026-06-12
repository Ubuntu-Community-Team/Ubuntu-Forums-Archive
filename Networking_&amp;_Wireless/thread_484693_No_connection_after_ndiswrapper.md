---
title: "No connection after ndiswrapper"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by oldcpu on 2007-06-26
Please help.  I have been trying to get my wireless working.  I got 3 wireless cards and 2 was suppose to work, but did not.  So I am down to this one.  The TRENDnet TEW-423PI.

Using this guide:
[http://ubuntuforums.org/showthread.php?t=400258](http://ubuntuforums.org/showthread.php?t=400258)

I am stuck at Step 13.  How do I do that in CLI?

Do I still have to do Step 13 if I only have 1 connection?  I have disabled LAN on BIOS.  So the only network I got is the wireless card.

I can not get a ping back when tried the connection.

Anyone used this same guide to set up the same card?  If so, please help.

Also, would you please post your /etc/network/interface too?  Because I think things changed a bit in Feisty.

---

### Post by Ayuthia on 2007-06-26
Usually network manager does not have anything configured for wireless so it will provide you the list that it finds is available.  You will then click to connect.

If you are doing it from a terminal, you can use

iwlist scan

to see the available sites and

sudo iwconfig <wtype> essid <essid>

where <wtype> is something like eth1, wlan0, etc. and <essid> is the name of the wireless site.

You can type 'man iwconfig' for more options.

My /etc/network/interfaces looks like this:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by Sjovan on 2007-06-26
what happens when you tyoe ndiswrapper -l ?

show me your interface, and do you want to connect to a wep or wpa network?

---

### Post by oldcpu on 2007-06-27
```
$ ndiswraper -l
mrv8335 : driver installed
        device (11AB:1FAA) present
```

---

### Post by Ayuthia on 2007-06-27
Can you also show the following:
ndisrapper -v
ifconfig
iwconfig

---

### Post by oldcpu on 2007-06-27
```
$ ndiswrapper -v
utils Error: No version specified!
driver version: 1.38
vermagic: 2.6.20-15-server SMP mod-unloaded 686

```
```
$ ifconfig
lo      Link encap:Local loopback
        inet addr: 127.0.0.1  Mask: 255.0.0.0
        UP LOOPBACK RUNNING MTU: 16436  Metric:1
        RX packs: 0 errors: 0 dropped: 0 overruns: 0 frame: 0
        TX packs: 0 errors: 0 dropped: 0 overruns: 0 carrier: 0
        collisions: 0 txqueuelen: 0
        RX bytes: 0 (0.0b)  TX bytes: 0 (0.0b)

```
```
$ iwconfig
lo      no wireless extensions.

```

---

### Post by Sjovan on 2007-06-28
```
apt-get install ndiswrapper-utils-1.9

nano /etc/moudules  -----> add nwisrapper to the list

nano /etc/network/interfaces ----> should look somehting like this:
iface <connection> inet dhcp
wireless-essid <network to join>
Wireless-key <pasword>
(ths is for a wep key. if you are on a wpa network you need to install some more progs and stuff)

```
Try to enable every connection for one strange reason you can't se any of your connections on ifconfig. Something is defently wrong. Your wlan connection should be named wlan0, ath0 or something like that and it should be in the iwconfig. Enable everything in the bios,  add my comands and try again :)

---

### Post by oldcpu on 2007-06-28
Sjovan, THANK YOU SO MUCH!!!

It worked after I added ndiswrapper to /etc/modules.

Now I have to learn about this WEP and WPA thing since I am a newbie at wireless.

Finally...  A connected and usable Linux after 2 months of Windows tolerance.  What a relief!

Thanks again!

---

### Post by Sjovan on 2007-06-28
If you are going to set up the wLAN then i sugest that you use a WEP-cryptation. That way you don't have to install more progs and stuff to get the wlan to work.
important! wireless-essid --->name is case sensitive.

---

