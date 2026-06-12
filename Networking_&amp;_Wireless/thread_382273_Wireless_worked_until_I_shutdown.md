---
title: "Wireless worked until I shutdown"
date: 2007-03-11
forum: Networking &amp; Wireless
---

### Post by Lotus_Eater on 2007-03-11
Ok, so I have a HP Pavillion ze2308 with a BCM4318 Airforce One 54 wireless card.
I got my wireless running by using the Windows Drivers, then after I restarted my computer, it worked, until I shut it down, then started it up again, now I can no longer get it to work.
I tried downloading a Wireless Assistant, however it will not allow me to connect.  The Network  Manager Applet worked once, the first time, but now neither will allow me to connect.
I also tried resetting my router through the reset button and removing power for a time.  Neither way helped.
I am simply out of ideas.

Thanks,
Lotus

---

### Post by x64Jimbo on 2007-03-11
I'm assuming that you're using ndiswrapper to run the device. You need to add ndiswrapper to your /etc/modules file, then reboot. Or run sudo modprobe ndiswrapper to get it working without a reboot.

---

### Post by Lotus_Eater on 2007-03-12
Ya, I use the ndiswrapper.
Now, please forgive the fact that I am pretty bad at this for the most part, but how exactly do I add the ndiswrapper to /etc/modules file?  Is there something specific I should look for?

---

### Post by foofi22 on 2007-03-12
In the terminal type 

```
sudo gedit /etc/modules
```

Another window will open with the module file, just add the line 

```
ndiswrapper
```

to the end.  Hope that helps. :)

---

### Post by Lotus_Eater on 2007-03-13
Nope, still nothing.
I'm about ready to throw it out the window, and my wife is tired of climbing over the cable.

---

### Post by x64Jimbo on 2007-03-13
Can you see your interface in ifconfig after you've modprobed the module?

---

### Post by Lotus_Eater on 2007-03-13
> 
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:F2:73:09  
          inet addr:192.168.1.47  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fef2:7309/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28143 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26903 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25631842 (24.4 MiB)  TX bytes:4100108 (3.9 MiB)
          Interrupt:209 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:14:A5:1F:02:2A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 Memory:d0204000-d0206000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)


Does this help?
I should probably note my Wireless hub is a Westell Versalink 327w.  Not sure if this makes a big difference.  So apprently my Wireless card is being detected, but it is unable to connect to the network for unknown reasons.

---

### Post by x64Jimbo on 2007-03-14
I'm guessing that after you reboot, the eth1 entry goes away...

---

### Post by SactoBob on 2007-03-14
I think that is what is happening is this:
You  did a successful installation with ndiswrapper, and then entered

> sudo modprobe ndiswrapper

Everything went active and was fine.  But ndiswrapper is not now loading and associating with the desired port at boot.  You can tell if this is correct by going to the console and again typing

> sudo modprobe ndiswrapper

If you are up and running again, then you know that the problem is simply that ndiswrapper is not loading and associating at boot.

In that case, 

> sudo ndiswrapper -m

should add the necessary module and alias to start at boot.

Bob

---

