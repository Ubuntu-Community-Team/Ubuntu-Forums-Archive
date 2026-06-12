---
title: "Networking Issues, Possibly DNS"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by Anonymvs on 2007-06-28
I have a fresh installation of Ubuntu, but unfortunately also some network issues:  When trying to go to a website, it takes very long periods of time for the page to load (sounds like DNS), and many times, it doesn't connect at all.

On my other computer, I figured out this is because the router's DNS server (192.168.0.1) is put before my ISP's in resolv.conf (and network manager).  So...I fixed my /etc/dhcp3/dhclient.conf file to prepend my resolv.conf so that it now reads:

ISP DNS server
192.168.0.1

...like my other (working) computers resolv.conf.  I did some research and also disabled ipv6 in firefox and took these steps to stop it from running: [http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798)

After all of this, my internet works for about 5 seconds after startup (enough to open 1.5 pages) and then stops completely (pages don't load, bottom left corner of Firefox reads : "Connecting to [www.[something].com](www.[something].com).  What shall I do?

---

### Post by PurplePenguin on 2007-06-29
Give OpenDNS a shot and see if it helps.  I prefer to use it, anyway.
The following is stolen from [http://www.opendns.com/start/ubuntu.php](http://www.opendns.com/start/ubuntu.php)


1. Open a terminal window and type the following:

    $ sudo network-admin 

Note: Root access is required for this step.
2. Change to the DNS tab and enter the following two addresses in the top of the first field labeled DNS Servers:

    208.67.222.222
    208.67.220.220 

You may leave your ISP's DNS addresses underneath the OpenDNS addressses as backup.

If your settings get revoked after reboots, or after periods of inactivity, you can try this:

    $ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
    $ sudo gedit /etc/dhcp3/dhclient.conf
    # append the following line to the document
    prepend domain-name-servers 208.67.222.222,208.67.220.220;
    # save and exit
    $ sudo ifdown eth0 && sudo ifup eth0 

You may be required to change eth0 to your own network device's name if it uses a non-standard name.
Visit [http://welcome.opendns.com/](http://welcome.opendns.com/) to test your new settings.

---

### Post by kevdog on 2007-06-29
Try OpenDNS and you can unblacklist the IPV6

Just be forewarned however.  I was running OpenDNS, had no problems, until I later realized it can not resolve computer names on the LAN.  It was giving me major problems with SAMBA and winbind, since I want to browse the samba shares via computer name rather than IP address.  I wrote OpenDNS about this problem, and the only way it would be fixed is if I signed up for an account.  I thought this was rather a useless step, so I just went back to using Comcast's DNS servers.

---

### Post by Anonymvs on 2007-06-29
I tried open DNS, it worked for maybe 10-15 seconds or so (really nice and fast) and then stopped.  Something is messing up the computer's internet after 10-15 seconds no matter what DNS server I use...any suggestions?

---

### Post by byunique on 2007-06-29
I would verify whether you have a connectivity problem or not. Go to a terminal window and do a test ping and watch the output for a bit. ie. ping [www.yahoo.com](www.yahoo.com)

You should have a consistent replies, and if you have a network issue, you will see some sort of time out.

If there is no missing packets, then maybe it is related to DNS.

---

### Post by Anonymvs on 2007-06-29
After the first 10-15 seconds of the internet working, when the internet halts, pinging yahoo does nothing.

ping [www.yahoo.com](www.yahoo.com)
ping: unknown host [www.yahoo.com](www.yahoo.com)

Same with google and other sites.  What I have also noticed is that I can't browse to my router's homepage by putting 192.168.0.1 into the address bar, neither can I successfully ping it:

ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.4 (Me) icmp_seq=2 Destination Host Unreachable
From 192.168.0.4 icmp seq=3 Destination Host Unreachable
etc...

---

### Post by byunique on 2007-06-29
Hmm, sounds like a networking issue allright. You should be able to ping your router.

Can you post your output of "ifconfig" and netstat -nr. I'd bet there is some missmatch of your IP and your gateway or something is not setup.

You can check how your network card is setup via, System, Administration, Network. You should see your network card listed and whether dchp is on.

---

### Post by Anonymvs on 2007-06-29
silvamethod@alpha:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:11:06:E3:32  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:760 (760.0 b)  TX bytes:760 (760.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:14:6C:6C:7D:26  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:6cff:fe6c:7d26/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:376 errors:0 dropped:0 overruns:0 frame:0
          TX packets:518 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:334276 (326.4 KiB)  TX bytes:103486 (101.0 KiB)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-6C-6C-7D-26-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

silvamethod@alpha:~$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 wlan0

That 192.168.0.0 sounds as if it should be 192.168.0.1....

My Network Setting Says Roaming Mode is Enabled for wlan 0 (wireless card), I also have a wmaster0 with roaming mode, an unchecked wired connection (DHCP) and an unconfigured modem connection.

---

### Post by byunique on 2007-06-29
Hmm, that output looks fine.

>That 192.168.0.0 sounds as if it should be 192.168.0.1....

That setting is Ok since it denotes a route to your subnet 192.168.0.0. The correct gateway is shown there, 192.168.0.1

I assume the 192.168.0.4 is defintely getting it's address via dhcp? Can you ping your other workstations, assuming you know the ip address...

If you can't it sounds like its making some kind of partial connection to the router. Maybe some authentication issue, security related? mac filtering, etc.... Might want to login to your router from the other pc and verify settings on the router.

---

### Post by byunique on 2007-06-29
oh, one more thing, post the output of "iwconfig"

---

### Post by Anonymvs on 2007-06-29
Hmmm....I can't ping any of my workstations, and there is no MAC address based blocking or such, what I did find is the error logs on my router, here you go:

    0:07:37 Elapsed Time udhcpd: SENDING OFFER to alpha   
    0:07:37 Elapsed Time udhcpd: ADD 00:14:6c:6c:7d:26 192.168.0.4 60l alpha  
    0:07:37 Elapsed Time udhcpd: sending OFFER of 192.168.0.4  
    0:07:37 Elapsed Time udhcpd: SENDING ACK to alpha   
    0:07:37 Elapsed Time udhcpd: sending ACK to 192.168.0.4  
    0:07:37 Elapsed Time udhcpd: ADD 00:14:6c:6c:7d:26 192.168.0.4 86400l alpha  
    0:07:38 Elapsed Time syslog: failed dns request len=126,srcip=216.165.129.157, url=local   
    0:20:00 Elapsed Time -- MARK --  
    0:22:45 Elapsed Time udhcpd: SENDING ACK to alpha   
    0:22:45 Elapsed Time udhcpd: sending ACK to 192.168.0.4  
    0:22:45 Elapsed Time udhcpd: ADD 00:14:6c:6c:7d:26 192.168.0.4 86400l alpha  
    0:22:46 Elapsed Time syslog: failed dns request len=126,srcip=216.165.129.157, url=local   
    0:40:00 Elapsed Time -- MARK --  
    1:00:00 Elapsed Time -- MARK --  
    1:01:56 Elapsed Time udhcpd: SENDING OFFER to alpha   
    1:01:56 Elapsed Time udhcpd: ADD 00:14:6c:6c:7d:26 192.168.0.4 60l alpha  
    1:01:56 Elapsed Time udhcpd: sending OFFER of 192.168.0.4  
    1:01:56 Elapsed Time udhcpd: SENDING ACK to alpha   
    1:01:56 Elapsed Time udhcpd: sending ACK to 192.168.0.4  
    1:01:56 Elapsed Time udhcpd: ADD 00:14:6c:6c:7d:26 192.168.0.4 86400l alpha  
    1:01:58 Elapsed Time syslog: failed dns request len=126,srcip=216.165.129.157, url=local   
    1:07:38 Elapsed Time udhcpd: SENDING ACK to alpha   
    1:07:38 Elapsed Time udhcpd: sending ACK to 192.168.0.4  
    1:07:38 Elapsed Time udhcpd: ADD 00:14:6c:6c:7d:26 192.168.0.4 86400l alpha  
    1:07:40 Elapsed Time syslog: failed dns request len=126,srcip=216.165.129.157, url=local   
    1:20:00 Elapsed Time -- MARK --  
    1:25:39 Elapsed Time udhcpd: SENDING ACK to alpha   
    1:25:39 Elapsed Time udhcpd: sending ACK to 192.168.0.4  
    1:25:39 Elapsed Time udhcpd: ADD 00:14:6c:6c:7d:26 192.168.0.4 86400l alpha  
    1:25:41 Elapsed Time syslog: failed dns request len=126,srcip=216.165.129.157, url=local   
    1:40:00 Elapsed Time -- MARK --  
    1:41:48 Elapsed Time udhcpd: SENDING OFFER to alpha   
    1:41:48 Elapsed Time udhcpd: ADD 00:14:6c:6c:7d:26 192.168.0.4 60l alpha  
    1:41:48 Elapsed Time udhcpd: sending OFFER of 192.168.0.4  
    1:41:48 Elapsed Time udhcpd: SENDING ACK to alpha   
    1:41:48 Elapsed Time udhcpd: sending ACK to 192.168.0.4  
    1:41:48 Elapsed Time udhcpd: ADD 00:14:6c:6c:7d:26 192.168.0.4 86400l alpha  
    1:41:50 Elapsed Time syslog: failed dns request len=126,srcip=216.165.129.157, url=local

---

### Post by Anonymvs on 2007-06-29
Here's the iwconfig:

silvamethod@alpha:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr: off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"Picasso"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0F:B3:9F:C5: DD   
          RTS thr: off   Fragment thr=2346 B   
          Link Quality=48/64  Signal level=22/65  
          Rx invalid nwid: 0  Rx invalid crypt:0  Rx invalid frag: 0
          Tx excessive retries:0  Invalid misc:0   Missed beacon: 0

---

### Post by byunique on 2007-06-29
Your iwconfig output looks good, you are assocated with access point, so mush be authenticating correctly. I purposely broke mine, and the Access Point shows "Not-Associated"


>1:41:50 Elapsed Time syslog: failed dns request len=126,srcip=216.165.129.157, url=local

From your router's logs seems that every time the laptop is given a IP, it then has this error. Don't know whether this is a problem or not. If you rebooted your other PC, wonder if the router would also post a similar output once the PC is given its DCHPed IP address. If the error is the same, then perhaps nothing to worry about. This ip is listed with ns6.dns.tds.net., perhaps your ISP's name server? 

I guess another thing to try is assign a static IP address, to make sure its not DHCP related.

IP: 192.168.0.5 (or one that is not used)
subnet mask: 255.255.255.0
gateway: 192.168.0.1

---

### Post by Anonymvs on 2007-06-29
Static gave me the same results as of internet surfing, but in the router's error log, instead of just dns errors with the URL "local" I also had ones with the URL "domain-not-set.invalid."  I'm guessing it's something with the way my computer is trying to resolve its DNS issues

---

### Post by byunique on 2007-06-29
Ok, if static IP had the same results, then dhcp should be OK. 

If you can't ping your router or other PC then, don't I wouldn't worry about DNS. If you could ping [www.yahoo.com](www.yahoo.com) directly "209.131.36.158", then I would say its DNS related. Can you ping the same IP from your PC?

Can you do a traceroute from your PC? Lets see if the routing is what you expect.

DOS Prompt, then "tracert www.yahoo.com"

---

### Post by Anonymvs on 2007-06-29
Pinging [www.yahoo.com](www.yahoo.com) or pinging yahoo directly through it's IP address doesn't work (unless done in first 10-15 seconds of "network activity"), same as other pings.

Same with traceroute, it works right as I log in and the internet is fine, but once it's off:

traceroute: unknown host [www.yahoo.com](www.yahoo.com)

---

### Post by byunique on 2007-06-29
So, in summary, everything works the first 10-15 seconds after you login to the laptop. Then it seems you lose connectivity. Is this true for the other PC as well? I am assuming its a Windows box.

Wondering if perhaps the roaming mode is interfering, and maybe its picking up a another wireless connection in your neighborhood, causing you to lose your initial connection.

---

### Post by Anonymvs on 2007-06-29
It's a pc, not a laptop, and yes, it works for about 10-15 seconds very well, then stops working all together.  I've checked my router and it says that the computer is on the network (according to IP and MAC address) so I'm connected to the right thing.

---

### Post by byunique on 2007-06-29
that some pretty bad instability, unless it's happening to your other machines, I would say that the network card you are using has some crappy drivers or something. It sounds pretty much isolated to the machine and not the network.

---

### Post by Anonymvs on 2007-06-29
Yes, I just found some bugs supposedly related to my network card, I'll try to use some different drivers, I'll keep you posted on the outcome.

---

