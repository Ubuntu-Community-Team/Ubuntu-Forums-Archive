---
title: "Wireless suddenly stops working"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by JoeyJoeJoe on 2007-04-29
Worked pretty well for the first week or so when I was hibernating my laptop. Come out of hibernation, wait 20-60 seconds (a bit too long if you ask me) and Ubuntu would find and connect to my wireless network (WPA), no problem.

After rebooting last night I not only don't see my network, I don't even see any of my neighbors' open networks which used to appear all the time.

I am a total Linux newbie and was having fun using Ubuntu, but now I'm back on the Windows side of my dual-boot laptop. :(

Please let me know what log files I can post and where they live in the filesystem.

Thanks,
JM

---

### Post by coxy on 2007-04-29
You could try restarting your networking.

```

sudo /etc/init.d/networking restart

```

I doubt that ill have much effect because networking is started when you boot up. I can't help much more than that i'm afraid. You could also post the output of:

```

ifconfig

```

The only other thing that comes to mind is that your wireless card is disabled in some way. You should be able to check in network manager.

---

### Post by JoeyJoeJoe on 2007-04-29
Results of ifconfig
```
joe@UbuntuLaptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0B:DB:D7:4F:74  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 aerrors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

eth0:avah Link encap:Ethernet  HWaddr 00:0B:DB:D7:4F:74  
          inet addr:169.254.7.199  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1120 (1.0 KiB)  TX bytes:1120 (1.0 KiB)

```

Results of  network restart
```
joe@UbuntuLaptop:~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 6158
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0b:db:d7:4f:74
Sending on   LPF/eth0/00:0b:db:d7:4f:74
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0b:db:d7:4f:74
Sending on   LPF/eth0/00:0b:db:d7:4f:74
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
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
                                                                         [ OK ]
joe@UbuntuLaptop:~$ 
```

results of iwconfig
```
joe@UbuntuLaptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by JoeyJoeJoe on 2007-04-30
I don't get it. Now it works again.

Sometimes it sees available networks, sometimes not
Sometimes it asks for my keychain password, sometimes not
Sometimes a reboot fixes it, sometimes not

Very strange. Also, it takes 60-90 seconds to authenticate to any network (open or encrypted).

---

