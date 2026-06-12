---
title: "[SOLVED] stuck with wlan"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by seul on 2007-11-06
I am trying to get a dlink DWL-G122 H/W Ver C1 usb dongle to work with feisty. When I first plugged it in, I could see some networks (though not all I see under windows). When I tried to connect by clicking on the double monitor icon, I could enter all the data and then the icon would change into the rotating thing with the two dots (I presume this is the network manager applet at work?), but after a while I would see the two monitors again without being connected.

I tried to figure why wlan0 and wmaster0 showed up when I only had one thing attached. In the forum somebody suggested in another thread to download the driver from serielmonkey to sort this. I fetched RT73 and followed the instructions. All went well, but after a reboot, the green status lights of the dongle are not showing any more and I still can't connect.

In a lot of threads people ask for ifconfig:

 ifconfig 
```
eth0      Link encap:Ethernet  HWaddr 00:E0:18:D4:8B:A2  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:18ff:fed4:8ba2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4395 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4117 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3230469 (3.0 MiB)  TX bytes:881463 (860.8 KiB)
          Interrupt:11 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:17:9A:82:D4:2F  
          inet6 addr: fe80::217:9aff:fe82:d42f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:480 (480.0 b)

```

and iwlistscan
 iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

```

I have no idea what that means or where to go from here. Thanks for your help in advance.

---

### Post by seul on 2007-11-07
I followed this howto [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236) and everything went smooth until sudo dhclient wlan0:```

There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:17:9a:82:d4:2f
Sending on   LPF/wlan0/00:17:9a:82:d4:2f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```

I'm still stuck, I still don't grasp what I am doing and what the terminal is trying to tell me, and I'm a bit frustrated, too, as this is the second wireless that refuses to work with ubuntu (my other one is a Belkin that freezes the entire system when inserted). I really enjoy ubuntu but I still find myself working with windows most of the time because of internet access.

---

### Post by -Stevey-Wonder-1990- on 2007-11-07
> **seul said:**
> I followed this howto [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236) and everything went smooth until sudo dhclient wlan0:```

There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:17:9a:82:d4:2f
Sending on   LPF/wlan0/00:17:9a:82:d4:2f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```

I'm still stuck, I still don't grasp what I am doing and what the terminal is trying to tell me, and I'm a bit frustrated, too, as this is the second wireless that refuses to work with ubuntu (my other one is a Belkin that freezes the entire system when inserted). I really enjoy ubuntu but I still find myself working with windows most of the time because of internet access.

i have the same problem, the same output etc anyone any ideas?

---

### Post by seul on 2007-11-08
Hey Stevey-Wonder,

I just managed to get my other wifi card running (Belkin Wireless G F5D7010 ver6000uk) which uses rt61 drivers. I used [http://ubuntuforums.org/showthread.php?t=563547&page=18](http://ubuntuforums.org/showthread.php?t=563547&page=18) and I'm sure it will work for the rt73, too. 
I went for the safe option and blacklisted all drivers wieman01 mentioned. I tried doing it for the Dlink dongle, too, but I couldn't get hold of the drivers from the cd. 

Good luck!

---

### Post by seul on 2007-11-08
Good news if you want to use ndiswrapper: 

For the Dlink DWL-G122 H/W Ver C1 get the driver [here]("http://www.dlink.co.uk/?go=jN7uAYLx/oIJaWVdDbgYU93ygJVYLelXSNvhLPG3yV3oUop7hqltbNlwaaRp7D06VHqqnHtB85pJVJ23gKftOQ5A8ruEaoqgXYP+pmsMmdsPTbhHNpbF3RLA5TSEJcbefr8r/Ep+/J4S7CoTftygjm/wjSNavmmlFx8="),
unzip the file and use dr71WU.inf (to be found in 
/DWL-G122_revB1v2.04_revC1v3.10.zip_FILES/D-Link DWL-G122.B1V2.04 G122.C1V3.10 Build 60719 S0012/Drivers) 
and follow [this Howto]("http://ubuntuforums.org/showthread.php?t=563547&page=18") 
I'm posting this using the abovementioned Dlink dongle, I hope it works for you (and everybody else), too!

---

### Post by p|_eX on 2007-11-10
i had some troubele with rt73 drivers too, but it can be fixed.
Ubuntu tries to use rt73usb drivers , instead of rt73. so you should blacklist this;
add these 2 lines to the file /etc/modprobe.d/blacklist
```
blacklist rt73usb
blacklist rt2x00lib
```
then install the rt73 module (you can get it from serialmonkey.com ).  
```

# tar xvfz rt73-cvs-daily.tar.gz
# cd ./rt73-cvs-YYYYMMDDHH/Module
# make && make install
# modprobe rt73
```
 then add this line to the file  /etc/modprobe.conf:
alias wlan* rt73

I needed to reboot the machine to get everything working. So, after a reboot, do 
```
# ifup wlan0
# iwlist s
```
now you should see the active network(s) appear instead of 'No scan results'.

---

### Post by seul on 2007-11-11
> **p|_eX said:**
> i had some troubele with rt73 drivers too, but it can be fixed.
Ubuntu tries to use rt73usb drivers , instead of rt73. so you should blacklist this;


The tutorial I mentioned above has rt73usb to be blacklisted among others (step 11), I did exactly as the tutorial said and still couldn't connect, so I don't really know if it indeed is the rt73usb causing the trouble.

---

### Post by p|_eX on 2007-11-14
Everything seems to be ok then, except it cannot find the accesspoint and get an IP-address...
The output you get from iwlist , dhclient look normal.
But the ifconfig sow that it does transmit, but not receive anything (see last line in  ifconfig)

Could you check check a few things (just to make sure...)
- if you do     lsmod |grep usbcore    ,  does it show the rt73 ?
- is your wireless-router functioning ok? does it accept connections from your usb-device (is there a mac-address restriction)?
- what is the channel your accesspoint uses, is it >11 ? (above channel 11 might need some extra adjustments.)
- if you do       dmesg |grep usbcore   , does it show something like : 
usbcore: registered new interface driver rt73

that's about all i can think of right now...

---

### Post by seul on 2007-11-15
I really appreciate your help, p|_eX. As I said above, I am using ndiswrapper now. It worked instantly with no fuss whatsoever. Because of that, I am not sure whether the outputs will be of use. I didn't have mac restriction (do have it now) and I was using channel 8.

Would you know how I can mark this thread as solved?

Thanks again for your replies, cheers,
seul

---

### Post by wrathkeg on 2008-01-16
> **seul said:**
> 
Would you know how I can mark this thread as solved?

Click on the "Thread tools" menu for any thread you created, and it should be there.
WK

---

