---
title: "Two Pc's, only one can connect"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by el mariachi on 2007-06-30
I just installed Xubuntu 7.04 on my old PIII (3Com ethernet 10/100 network board) and, just to do some updates and install a couple of packages, I plugged my cable modem (Motorola SB5101) into it. Now, on my current desktop running Ubuntu 7.04 it connects to the internet just fine but the Xu one doesn't.

The problem is not Xubuntu - i tried Xu on my Desktop and it worked fine. Also when I switch back the modem from Xu to Ubuntu I have to restart the PC to get connected. It's as if the modem doesn't want to connect in a different computer....

If the problem is in the Network card how can I know?
Thanks y'all

---

### Post by spd106 on 2007-07-06
Does the Xubuntu machine receive an IP address from the modem? Can you ping it?

---

### Post by el mariachi on 2007-07-06
> **spd106 said:**
> Does the Xubuntu machine receive an IP address from the modem? Can you ping it?

nothing at all... but Xu says there is a wired connection working which is weird. It also doesn't find any DNS or search domains and adding them manually doesn't work either. I think it's configured the right way, since everything is set to default and it's a fresh install.

What i don't get is why when I reconnect the cable to my desktop (ubuntu) I have to restart to get an ip address assigned, that is, I get one but it doesn't work, the only fix is a reboot (which I tried in the Xu machine without success)

Can you tell me some commands to help you diagnose the Xu machine? ping, etc

---

### Post by punx45 on 2007-07-06
i have found that with both cable and dsl modems, you need to power cycle the modem every time you connect it to a different device whether it be a PC or router.   try unplugging the power to the modem as you restart the computer, then plug it back in about 30-60 secs. later.

---

### Post by spd106 on 2007-07-06
You shouldn't need to reboot, try this command instead
```
sudo /etc/init.d/networking restart
```

This command will show you the current status of the interfaces and whether they have an IP address. The line in red is highlighted for emphasis and I have obscured some of the sensitive numbers.
```
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:E0:xx:xx:xx:xx  
          [COLOR="Red"]inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0[/COLOR]
          inet6 addr: fe80::2e0:xxff:fexx:xxxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:74233 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43229 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:97642179 (93.1 MiB) 
          TX bytes:3597633 (3.4 MiB)
          Interrupt:3 Base address:0x300 
```
This command will attempt to get an IP address from the modems DHCP server.
```
sudo dhclient eth0
```
It may take a couple of minutes to time out. If it fails and goes to sleep then you are probably not be receiving a response from the modem.

As suggested above some modems cache particular MAC addresses, which means they won't work immediately if you try a different card. Though they often will update if you wait a while, others won't and need a power cycle. So you might as well try that anyway.

---

### Post by el mariachi on 2007-07-06
Thanks! I'll try that!
My ISP keeps track of the MAC address to bill me every bit of data that I download/upload so that may be the problem... I'll try it and post the results, thanks!

---

### Post by el mariachi on 2007-07-06
well unfortunately it didn't work..
this is the outcome of the commands you told me about.
[B]dhclient
[/B]```
Listening on LPF/eth0/00:01:02:d9:48:dc
Sending on   LPF/eth0/00:01:02:d9:48:dc
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```
[B]ifconfig -a
[/B]```

eth0      Link encap:Ethernet  HWaddr 00:01:02:D9:48:DC  
          inet6 addr: fe80::201:2ff:fed9:48dc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1249 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:312966 (305.6 KiB)  TX bytes:10961 (10.7 KiB)
          Interrupt:11 Base address:0xe000 

eth0:avah Link encap:Ethernet  HWaddr 00:01:02:D9:48:DC  
          inet addr:169.254.7.253  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:354 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27240 (26.6 KiB)  TX bytes:27240 (26.6 KiB)
```
[B]sudo /etc/init.d/networking restart
[/B]```
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 5081
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:01:02:d9:48:dc
Sending on   LPF/eth0/00:01:02:d9:48:dc
Sending on   Socket/fallback
eth1: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:01:02:d9:48:dc
Sending on   LPF/eth0/00:01:02:d9:48:dc
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]
```
any clues? I did unplug the power and waited a few seconds/minutes like you said (while restarting and all that).

---

### Post by t4thfavor on 2007-07-06
Your ISP is blocking all macs but the one on your pc. You need to get a router ad clone the mac of the ubuntu desktop and then both pc's will connect just fine. 

I know there is a way to clone the mac under ubuntu, but I am not aware of the process.


You could turn on nat on the ubuntu machine and use it as a router for your network, but that is beyond the scope of this post.

---

### Post by spd106 on 2007-07-06
Using NAT/ICS is probably the best way to go, see these wiki pages.
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)
[https://help.ubuntu.com/community/InternetConnectionSharing](https://help.ubuntu.com/community/InternetConnectionSharing)

If that isn't feasible, then the mac changer utility might work. In my experience it has been the most likely way to get it working. It was in the Ubuntu repos. last time I checked.
[http://www.alobbs.com/macchanger/](http://www.alobbs.com/macchanger/)

Alternatively ifconfig might work, though not all drivers support this method.
```
sudo ifconfig eth0 ether hw xx:xx:xx:xx:xx:xx
```

---

### Post by el mariachi on 2007-07-07
ifconfig gave me an error showing the right way to use it..

i typed this:
sudo ifconfig eth0 peace-garden hw mac-address

---

