---
title: "Need wireless networking help Netgear WG111T"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by osideconnect on 2009-01-25
First time kubuntu user.  Just successfully installed Kubuntu 7.10.   Trying to connect my Netgear WG111T wireless USB dongle.  Read previous threads that describe installing NDISwrapper and NDISGTK.  My GUI is different from what is described in the other threads.  I do not have Synaptic package manager, I have Adept package manager. I cannot find ndiswrapper to install.

---

### Post by diablo75 on 2009-01-25
[http://kbserver.netgear.com/release_notes/d102626.asp](http://kbserver.netgear.com/release_notes/d102626.asp). You'll want to install athfmwdl.inf and netwg11t.inf with ndiswrapper. So hook your laptop up to a ethernet connection. Then open Applications>Add/Remove and search for "ndiswrapper". Install it, as well as downloading the linked driver above.

After that's installed, you should see a new entry in your System>Administration folder called something like "Windows Wireless Drivers".

That will open up a simple gui that will ask you to browse for an *.inf file. You just extract the above zip file out to a folder temporarily, add that inf, and that should do the trick. You can delete the folder once the inf has been added.

---

### Post by osideconnect on 2009-01-25
Diablo thanks for the info.  Was able to install the device.  i found my wireless network, but I keep getting errors when I try to open up any websites.  I'll look for other threads but any insights?

---

### Post by diablo75 on 2009-01-25
Well if you were able to successfully connect to your wireless network, perhaps you should ping your router to make sure that your computer and it are communicating.  Open a Terminal window (Applications>Accessories>Terminal) and type:

ifconfig

Look for a device (like wifi0 perhaps) that has an IP address next to it.  It will likely look something like 192.168.1.x or 10.0.0.x (x being some random number between 1 and 255).

This will narrow down your network, and you can guess the IP address of your router from there.  If it were 10.0.0.x, then your routers IP address could be 10.0.0.1, or 10.0.0.100 (perhaps .10, but unlikely).  Same thing goes for the 192.168.1.x addresses.  Sometimes you'll come across a 10.0.1.x, so pay attention to that if it comes up.

Then in terminal type:

ping 10.0.0.1

If you hit the correct address of your router, you should get output like this:

```
PING 10.0.0.1 (10.0.0.1) 56(84) bytes of data.
64 bytes from 10.0.0.1: icmp_seq=1 ttl=64 time=1.45 ms
64 bytes from 10.0.0.1: icmp_seq=2 ttl=64 time=1.41 ms
64 bytes from 10.0.0.1: icmp_seq=3 ttl=64 time=1.37 ms
64 bytes from 10.0.0.1: icmp_seq=4 ttl=64 time=1.38 ms
64 bytes from 10.0.0.1: icmp_seq=5 ttl=64 time=2.26 ms
^C
--- 10.0.0.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4017ms
rtt min/avg/max/mdev = 1.375/1.579/2.268/0.347 ms

```

And NOT like this:

```
PING 10.0.0.100 (10.0.0.100) 56(84) bytes of data.
From 10.0.0.9 icmp_seq=1 Destination Host Unreachable
From 10.0.0.9 icmp_seq=2 Destination Host Unreachable
From 10.0.0.9 icmp_seq=3 Destination Host Unreachable
^C
--- 10.0.0.100 ping statistics ---

```

(Hit CTRL-C to Cancel the pings)

Just for the heck of it, you might as well shoot for the moon and see what happens when you type:

ping [www.google.com](www.google.com)

If you're able to get to your router, and you're sure your modem is functioning, you should get replies back from google's servers.  If not... it could be your modem, or it might be a DNS issue.  Perhaps simply doing a power cycle on your router and cable/DSL modem will reset some IP addresses as well and fix it.  Lots of things to try.  Good luck!

---

### Post by osideconnect on 2009-01-26
I ran the  ifconfig and this is what I get for my wireless connection.  I'm typing this from my laptop which is connected wirelessly.  I restarted my wireless router and modem still no joy on the wireless.  I have DHCP on my router but I'm only getting an IP6 address and no IP4 address. I have four other machines connected wirelesly is there a way around having to go back and manually configure IP routing on all those machines?


wlan0     Link encap:Ethernet  HWaddr 00:14:6c:e5:8f:99
          inet6 addr: fe80::214:6cff:fee5:8f99/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

