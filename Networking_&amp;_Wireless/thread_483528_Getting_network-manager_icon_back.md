---
title: "Getting network-manager icon back"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by genericlifeform on 2007-06-24
Hi,

After a long fight with my wireless network card, I am finally able to use it.  However, in the process I had to uninstall and reinstall network-manager.  In doing so I lost the little icon next to the clock to and am wondering if there is a way to get it back so that I can use network-manager to manage the card now.  The only way for me to connect as of now to the access point is using the following commands:

```

sudo ifconfig ra0 down
sudo iwconfig ra0 essid <SSID>
sudo ifconfig ra0 up
sudo dhclient3 ra0

```

Thanks in advance!

---

### Post by scrooge_74 on 2007-06-24
open a terminal and type nm-applet  That should do the trick

---

### Post by genericlifeform on 2007-06-24
That worked, thanks.

Unfortunately, while I can still use the commands above to connect, the nm-applet is unable to connect to the wireless network.  I'm using a Hawking HWP54G wireless adapter that uses the "ra2500" driver.  The network itself is unsecured, using MAC address filtering.  Should be a piece of cake but apparently is not.

---

### Post by scrooge_74 on 2007-06-24
try telling it to connect to a new network, sometimes network manager is a picky about connecting

---

### Post by genericlifeform on 2007-06-24
Looks to work with manual configuration.  Thank you much.

---

### Post by all4als on 2007-06-27
I tried doing this in the terminal. I don't get any response. The terminal just hangs there. So I closed via the X in the upper right hand corner and tried again. Second time, the same thing occured. What am I doing wrong?

This is how it was resolved for my situation. Sorry I am a little slow. [http://ubuntuforums.org/showthread.php?t=419129&highlight=missing+icon+network+manager](http://ubuntuforums.org/showthread.php?t=419129&highlight=missing+icon+network+manager)

---

### Post by genericlifeform on 2007-06-27
I assume you're talking about the 4 commands I gave above.  If so, then don't run the last command unless you have dhcp on your network, doing so might cause this behavior.  Also you might need to change "ra0" in all your commands to be your actual interface, which you can find by running:

```
sudo ifconfig
```

Also, you don't need to run any of those commands if network manager is finding your network ok.  I just used them because I didn't have nm-applet installed.

---

### Post by Gnub_Daemon on 2007-06-28
So yeah...I'm having the same problem, and ```
nm-applet
``` just sits there until I close the shell and start a new one.  As for the R0 stuff, well...I see nothing about that when I run ```
sudo ifconfig
```.  All I want is my connection manager icon back, unless there is another wifi connection manager that I can use that will work in pretty much the same way.

```

eth0      Link encap:Ethernet  HWaddr 00:16:D4:B6:3F:E5
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1016 (1016.0 b)  TX bytes:1016 (1016.0 b)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:75.116.75.114  P-t-P:209.97.103.26  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:3731 errors:42 dropped:0 overruns:0 frame:0
          TX packets:3554 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:3299804 (3.1 MiB)  TX bytes:436399 (426.1 KiB)

```

My ppp0 is connected using KPPP, but I still would like the Connection Manager for WiFi.

---

### Post by Gnub_Daemon on 2007-06-28
Oops...I meant "ra0"...not "R0."

---

