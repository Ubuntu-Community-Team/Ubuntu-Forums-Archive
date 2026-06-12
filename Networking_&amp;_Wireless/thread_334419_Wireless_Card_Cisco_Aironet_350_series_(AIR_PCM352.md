---
title: "Wireless Card Cisco Aironet 350 series (AIR_PCM352)"
date: 2007-01-08
forum: Networking &amp; Wireless
---

### Post by stroopwafel on 2007-01-08
I can't connect to my wireless router with my Wireless Card Cisco Aironet 350 series (AIR_PCM352). I can see my card in the network-settings window. It is trying to activate the network interface after changing the settings.

The terminal gives me this info:
```
maarten@maarten-laptop:~$ sudo lshw -C network
  *-network               
       description: Cisco Systems
       physical id: 0
       version: 350 Series Wireless LAN Adapter
       slot: Socket 0
       resources: irq:3
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:0f:f8:4f:99:7c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11-DS

maarten@maarten-laptop:~$ iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"EMI Bus Center"  
          Mode:Managed  Frequency: 2.437 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-125 dBm  Noise level=-95 dBm
          Rx invalid nwid:182  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:340   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:"EMI Bus Center"  
          Mode:Managed  Frequency: 2.437 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-125 dBm  Noise level=-95 dBm
          Rx invalid nwid:182  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:340   Missed beacon:0

```

I have some questions:
1. Did the native linux driver install correctly?
2. Does it look like the card is configured correctly?
3. How can I "scan" for available public networks?

---

### Post by stroopwafel on 2007-01-09
Question 3. (see first post in this thread) has been answered. I installed Network Manager.

Network Manager tells me now that: "No Network Devices have been found"

Please look over the terminal output in my first post to tell me where I need to go from here?

Do I need to install the driver:
[INDENT]
[http://linux-wless.passys.nl/query_part.php?brandname=Cisco](http://linux-wless.passys.nl/query_part.php?brandname=Cisco) says that the driver I need is part of the kernel. lshw doesn't show a driver though.

How do I install the airo_cs driver?[/INDENT]

---

### Post by chili555 on 2007-01-09
To see if a module (or "driver" to you recovering Windows-aholics) is loaded, do sudo lsmod. Specifically, you can look for airo by doing sudo lsmod | grep airo.

To see if a network is nearby, you can do sudo iwlist eth1 scan.

If you see your router when you scan, try sudo dhclient eth1. Let us know the outcome.

---

### Post by axcairns on 2007-03-07
I appear to have the same problem as the original poster, right down to the almost exactly the same output from lshw and iwconfig.

Here is what I see in my fresh feisty herd 5 install -

```
allan@vaio:~$ sudo lsmod | grep airo
airo_cs                 7168  1 
airo                   74400  1 airo_cs
pcmcia                 39212  1 airo_cs
pcmcia_core            40852  4 airo_cs,pcmcia,yenta_socket,rsrc_nonstatic
```

```
allan@vaio:~$ sudo iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:40:96:33:0F:62
                    ESSID:"home"
                    Mode:Master
                    Frequency:2.427 GHz (Channel 4)
                    Quality=90/100  Signal level=-50 dBm  Noise level:-103 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:13:D3:79:B6:E2
                    ESSID:"home2"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=100/100  Signal level=-38 dBm  Noise level:-103 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
```

```
allan@vaio:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 5631
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth1/00:07:0e:b3:60:d7
Sending on   LPF/eth1/00:07:0e:b3:60:d7
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

This card was working up until a few days ago in edgy but then just stopped working. I did the feisty install in the hope of fixing it.

Any ideas?

Thanks,


Allan

---

### Post by chili555 on 2007-03-07
You have the native drivers loaded. I would sudo gedit /etc/network/interfaces to be sure your wireless-essid and wireless-key are properly shown. I notice you have an interface and an alias, that is eth1 and wifi0. I'm not certain which is the preferred interface, so I would amend both, if they are not correct, in ../interfaces.

Restart networking sudo /etc/init.d/networking restart and let us know.

---

### Post by axcairns on 2007-03-07
/etc/network/interfaces -

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface


iface eth0 inet dhcp



auto eth0

iface eth1 inet dhcp
wireless-essid home
wireless-key s:MYWEPPASSPHRASE

auto eth1
```

```
allan@vaio:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth1.pid with pid 20696
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth1/00:07:0e:b3:60:d7
Sending on   LPF/eth1/00:07:0e:b3:60:d7
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 20654
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/08:00:46:4c:d5:ed
Sending on   LPF/eth0/08:00:46:4c:d5:ed
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.202 -- renewal in 17983 seconds.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth1/00:07:0e:b3:60:d7
Sending on   LPF/eth1/00:07:0e:b3:60:d7
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.                          [ OK ]
```

Cheers,



Allan

---

### Post by Mr. C. on 2007-03-07
Is the firmware on those aironet's up to date?  I recall when I had mine, there was an update to the firmware/software for Window's that indicated from that point forward, Linux was no longer supported.

Please check card's firmware against the latest available and release notes at Cisco.

MrC

---

### Post by axcairns on 2007-03-08
> **Mr. C. said:**
> Is the firmware on those aironet's up to date?  I recall when I had mine, there was an update to the firmware/software for Window's that indicated from that point forward, Linux was no longer supported.

Please check card's firmware against the latest available and release notes at Cisco.

MrC

This card was working under edgy until a few days ago. No firmware upgrades have been applied in several years.

Cheers,

Allan

---

### Post by nickrout on 2007-03-10
I am having a similar problem with an airo pcmcia card and 6.06. I installed ubuntu on an IBM T20 yesterday. After first boot I used the ubuntu network setup program (the gui) to set the ESSID and the WEP key and it worked. after a reboot the settings were gone and I spent 3 or 4 hours (until 3:30 am dammit) trying and trying to get it to go.

what i have concluded is that if you set the wep key right straight after boot it works, if you get it wrong, you seem to be stuck until after a reboot.

When inputting the wep key into the GUI it seems to need to be entered in upper case with the - character in the right places, like:

ABCD-1234-CD

not ABCD1234CD
not abcd-1234-cd
not abcd1234cd

I understand some drivers are fussier than others about the precise format. My AP (which runs a cut down deb/ubuntu called voyage) uses a different driver (different card), which is happy to accept variants that the cisco card won't seem to work with.

Also, where does the ubuntu gui configurer store it's settings? Nothing is set in /etc/networking/interfaces. Is this a bug?

Presently upgrading to 6.10 and will post if there is any change of behaviour.

---

### Post by chili555 on 2007-03-10
nickrout-

/etc/network/interfaces is the place to put all these settings.(not network**ing**) You can sudo gedit /etc/network/interfaces and put them all in. Here is an obscured, abbreviated version of mine, for an example:
```
auto eth1
iface eth1 inet dhcp
wireless-essid GBR1
wireless-key 096c7fxxxyyyzzz
```

When you reboot, all should be good. As you can see, lower case letters work fine here. 

WARNING, Will Robinson: under no circumstance should you mess with lo. Don't even look at it.

---

### Post by nickrout on 2007-03-15
oops yes I did make a typo on the directory name, it certainly should be /etc/network/interfaces.

And by way of update, an update to edgy seems to have fixed the problem. network-admin now seems to save the wireless details properly to /etc/network/interfaces and it comes up every time.

Cheers. Nick.

---

### Post by laszlo on 2007-03-25
I'm also having problems with a PCMCIA Cisco 350 on an IBM T20. Having only installed/used Linux for the first time last week (having  put Ubuntu on my desktop) I was so pleased I decided to install it on my laptop (network install of edgy). All went well until I enabled WEP on the Cisco card and it stopped working, works fine without it! I think I have followed every thread that I have managed to google about it but no luck! I get the message "No DHCPOFFERS received" when i restart the device. Any advice would be gratefully recieved!!

---

### Post by chili555 on 2007-03-25
Here is a post that may help. [http://www.ubuntuforums.org/showthread.php?t=172810&page=2](http://www.ubuntuforums.org/showthread.php?t=172810&page=2) Post back if you need more help.

---

### Post by laszlo on 2007-03-27
Oh Dear. I thought I would put a fresh install on before carrying out the suggestions in your post as I had tinkered excessively and now I can't connect even without WEP. I'm beginning to think maybe i'd left the cable in the back when I thought it had worked !  The drivers (native) are loaded and an iwconfig returns a valid access point but a very large Invalid misc. eth1 scan gives me no scan results. Any ideas?

---

### Post by laszlo on 2007-03-27
whoops. forgot the sudo with the scan - picks up the AP. - Mode:Master ?

---

### Post by chili555 on 2007-03-28
If you have disabled encryption for now, just to get it to connect, you should be able to take the scan results and put the relevant data in and connect immediately. Here is an example, using my own data, thinly disguised. I do *sudo iwlist eth1 scan*; I get:```
eth1      Scan completed :
          Cell 01 - Address: 99:13:19:62:8D:F7
                    ESSID:"myrouter1"
                    Protocol:IEEE 802.11bg
                    Mode:Master
etc., etc.

```Then, with the ESSID and the MAC address of the router I wish to connect to, I command eth1 to connect:```
sudo iwconfig eth1 essid "myrouter1"
sudo iwconfig eth1 ap 99:13:19:62:8D:F7
sudo dhclient eth1
```Let us know how it goes and we'll get WEP set up.

---

### Post by laszlo on 2007-03-28
Thanks for getting back so quick!  Still having problems. I entered the details but to no avail! 

laz@ubuntu:~$ sudo iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:12:BF:0F:8E:4D
                    ESSID:"lazRouter"
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality=86/100  Signal level=-52 dBm  Noise level:-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s

laz@ubuntu:~$ 


laz@ubuntu:~$ sudo iwconfig eth1 essid "lazRouter"
laz@ubuntu:~$ sudo iwconfig eth1 ap 00:12:BF:0F:8E:4D
laz@ubuntu:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth1/00:0c:30:1f:16:d2
Sending on   LPF/eth1/00:0c:30:1f:16:d2
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
laz@ubuntu:~$ 
laz@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"lazRouter"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:12:BF:0F:8E:4D   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-42 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5342   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:"lazRouter"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:12:BF:0F:8E:4D   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-42 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5342   Missed beacon:0

laz@ubuntu:~$ 

What is also quite weird is if I start the laptop with the router on, it does not say it has seen it. If I reboot, the router says it has assigned an IP but no difference in the laptop  settings!!

---

### Post by Mooie on 2007-03-29
I have a friend whos laptop i am trying to get set up wireless so he can get online.  He is getting this too, he uses a prism 2.5 miniPCI card, and i think its recognized now, but it wont pick up his router. when he runs "sudo dhclient eth0" it returns this:
> Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:0e:35:b5:26:53
Sending on LPF/eth1/00:0e:35:b5:26:53
Sending on Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in  persistent database - sleeping.


any help would be great

---

### Post by shdawson on 2008-03-11
Hi,


I have been using this card on my laptop with XP, with the Cisco Aironet Desktop Utility.  This box now has UBUNTU!!!

So, is there an application I can put on this box that will get the data from the card, so I can send it to my customers in the format they need it in?  They use the XP version of this software to read data that is collected, and I send them the data files.


Thanks......

---

