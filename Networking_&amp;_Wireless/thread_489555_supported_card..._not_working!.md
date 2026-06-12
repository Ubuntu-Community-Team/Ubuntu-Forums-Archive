---
title: "supported card... not working!"
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by otardi on 2007-07-01
Hi all,
I bought a ASUS wl-107g card (ralink2500 chipset), which is supposed to work right out of the box... and it does : it's detected by my laptop, the driver seems to be loading, it sees my wireless router. But then ping doesn't work. 
Here's the output of a few commands - ra0 is my wireless card. Sorry I have a french-speaking Ubuntu :

ifconfig (seems I can't get an IP address from the router):

```
eth0      Lien encap:Ethernet  HWaddr 00:90:F5:39:1A:42  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:3145 erreurs:0 :0 overruns:0 frame:0
          TX packets:2315 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:1884348 (1.7 MiB) Octets transmis:303867 (296.7 KiB)
          Interruption:11 Adresse de base:0x4000 

eth0:avah Lien encap:Ethernet  HWaddr 00:90:F5:39:1A:42  
          inet adr:169.254.4.216  Bcast:169.254.255.255  Masque:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interruption:11 Adresse de base:0x4000 

lo        Lien encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:433 erreurs:0 :0 overruns:0 frame:0
          TX packets:433 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:38238 (37.3 KiB) Octets transmis:38238 (37.3 KiB)

ra0       Lien encap:Ethernet  HWaddr 00:17:31:11:FE:47  
          adr inet6: fe80::217:31ff:fe11:fe47/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:94123 errors:0 dropped:0 overruns:0 carrier:0
          collisions:58 lg file transmission:1000 
          Octets reçus:0 (0.0 b) Octets transmis:3963862 (3.7 MiB)
          Interruption:5 Adresse de base:0x4000 

ra0:avahi Lien encap:Ethernet  HWaddr 00:17:31:11:FE:47  
          inet adr:169.254.6.8  Bcast:169.254.255.255  Masque:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interruption:5 Adresse de base:0x4000 

```

iwconfig:```

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"<my essid name>"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:54 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-35 dBm  Noise level:-204 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

iwlist ra0 scan:
```

ra0       Scan completed :
          Cell 01 - Address: 00:11:95:09:56:7A
                    Mode:Managed
                    ESSID:"<my essid name>"
                    Encryption key:on
                    Channel:1
                    Quality:0/100  Signal level:-25 dBm  Noise level:-204 dBm

```

Note there are no problems on my home PC which accesses the web via the same router in wireless mode, and I tried to enter similar network settings on both computers...

Any ideas ?

thx 
oliver

---

### Post by kevdog on 2007-07-01
I would grab the new rt2500 legacy drivers from the serialmonkey website and compile them from source.  They are the most recent version.  The version included in the kernel is old.  ra drivers dont really work well with network manager, so a lot of the configuration needs to be done editing the /etc/network/interfaces file.

This thread will help you with configuring the interfaces file:
[http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey)

This thread will help you with the installation/compilation of the serialmonkey drivers:
[http://ubuntuforums.org/showthread.php?t=417833&highlight=serialmonkey](http://ubuntuforums.org/showthread.php?t=417833&highlight=serialmonkey)

---

### Post by ugm6hr on 2007-07-01
This guy managed to get his RT2500 working with Wicd (unencrypted though):
[http://ubuntuforums.org/showthread.php?t=489287](http://ubuntuforums.org/showthread.php?t=489287)

---

### Post by otardi on 2007-07-02
I installed serialmonkey's drivers like it's described at [http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey]("http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey"), and I installed wicd... no results.
It seems I can't get a IP address from the router: when I try  sudo dhclient ra0 I get this :

```
Listening on LPF/ra0/00:17:31:11:fe:47
Sending on   LPF/ra0/00:17:31:11:fe:47
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

and I still can't ping the router, event though I see the wifi networks around me.

---

### Post by imdano on 2007-07-02
Try specifying a static ip and see if you're able to connect then.

---

### Post by kevdog on 2007-07-02
ra based chips dont really work to well with network manager, so all the connection has to take place either through the command line, or by adding the commands to the /etc/network/interfaces file so they can be run when the network bus is restarted.

Again it looks like you have may have consulted this post before, but I just want to make sure you are typing these lines as instructed:

sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid YOUR_NETWORK_NAME_HERE
sudo iwconfig wlan0 key YOUR_WEP_KEY_HERE_OR_"off"_FOR_NO_KEY
sudo dhclient wlan0

For you however, instead of using wlan0 you want to use ra0.

---

### Post by otardi on 2007-07-04
imdano, even with a static IP I can't connect.
kevdog, I did exactly like you said, to no avail...
But then I tried to turn off all security - now it works (yay!), but WEP is disabled and I have no authentication, leaving everything open for my evil neighbors to download like there's no tomorrow.
Is there any hope to make it work with at least shared key type security enabled ?

o.

---

### Post by imdano on 2007-07-04
Sometimes putting double quotes around your WEP key will allow it to connect when it normally hasn't.  If that doesn't work, trying asking your question at the [wicd forums](http://wicd.sourceforge.net/phpbb/index.php).

---

### Post by otardi on 2007-07-05
nope, double quotes won't change anything.
I'll check wicd forums.

Thank you guys!

o.

---

### Post by imdano on 2007-07-05
Some people were able to get things working manually with the commands on page 2 of this thread:
[http://ubuntuforums.org/showthread.php?t=417833](http://ubuntuforums.org/showthread.php?t=417833)

---

