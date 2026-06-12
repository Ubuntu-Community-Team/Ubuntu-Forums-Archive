---
title: "[SOLVED] Weird problem connecting to internet"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by tanndo on 2007-11-21
Hi,

I've just installed ubuntu-7.10-desktop-i386.iso
and am running a dual boot system with XP.

Basically the only site I can get to is google!

Everything else times out. Spent many hours trying to
fix this and am almost ready to give up :(


I have a Linksys ADSL2MUE modem which works fine in 
windows XP. Configured via 
	192.168.1.1 
My ISP is plusnet.

But from ubuntu I can't even get to 192.168.1.1 to configure modem/router

I also had a DNS problem which I think is fixed.

What I've done so far:

1) tried static IP : made no difference so went back to DHCP

2) switched off ipv6 by editing 
	/etc/modprobe.d/blacklist
and added
	blacklist ipv6 

3) Forced ubuntu to to use static DNS by editing
	/etc/dhcp3/dhclient.conf
to have:
	prepend domain-name-servers DNS-server-IP, another-DNS-server-IP;
	request subnet-mask, broadcast-address, time-offset, routers,
	        domain-name, host-name,
	        netbios-name-servers, netbios-scope;


4) Tried to turn off tcp window scaling:
	sudo echo 0 > /proc/sys/net/ipv4/tcp_window_scaling
but failed with permission denied !
So reconfigured as also suggested on forums by editing
	/etc/sysctl.conf 
and added
	net.ipv4.tcp_rmem = 4096 65536 65536
	net.ipv4.tcp_wmem = 4096 65536 65536

5) Managed to turn off windows scaling (?) by editing
	/etc/sysctl.conf 
and added
	net.ipv4.tcp_window_scaling = 0

Note tabs in above just there for readability and did numerous
reboots and network restarts via
	sudo invoke-rc.d networking restart
	
All to no avail.


Proof that I can access google but not other sites e.g. bbc:

user@home:~$ wget  [www.google.co.uk](www.google.co.uk)
--19:55:26--  [http://www.google.co.uk/](http://www.google.co.uk/)
           => `index.html.1'
Resolving [www.google.co.uk](www.google.co.uk)... 66.249.93.104, 66.249.93.147, 66.249.93.99
Connecting to www.google.co.uk|66.249.93.104|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                                                                              ] 3,239         --.--K/s             

19:55:26 (505.12 KB/s) - `index.html.1' saved [3239]

user@home:~$ wget  [www.bbc.co.uk](www.bbc.co.uk)
--19:56:13--  [http://www.bbc.co.uk/](http://www.bbc.co.uk/)
           => `index.html.2'
Resolving [www.bbc.co.uk](www.bbc.co.uk)... 212.58.227.77
Connecting to www.bbc.co.uk|212.58.227.77|:80... connected.
HTTP request sent, awaiting response... 


Any gurus out there with any ideas would be much appreciated.

Thanks
T

---

### Post by mellowd on 2007-11-23
What happens if you ping bbc.co.uk?

Also, install traceroute if you haven't already got it, then tracertoute bbc.co.uk. How far do you get?

---

### Post by tanndo on 2007-11-23
Hi,

thanks for the reply, it means a lot. At least someone is out there!

Anyway traceroute is not found and can't install as internet not working but ping
seems ok and found a command called tracepath. Please see output below

  user@home:~$ ping -c3 [www.bbc.co.uk](www.bbc.co.uk)
  PING [www.bbc.net.uk](www.bbc.net.uk) (212.58.253.72) 56(84) bytes of data.
  64 bytes from www3.cwwtf.bbc.co.uk (212.58.253.72): icmp_seq=1 ttl=249 time=43.3 ms
  64 bytes from www3.cwwtf.bbc.co.uk (212.58.253.72): icmp_seq=2 ttl=249 time=36.9 ms
  64 bytes from www3.cwwtf.bbc.co.uk (212.58.253.72): icmp_seq=3 ttl=249 time=39.7 ms
  
  --- [www.bbc.net.uk](www.bbc.net.uk) ping statistics ---
  3 packets transmitted, 3 received, 0% packet loss, time 2002ms
  rtt min/avg/max/mdev = 36.913/39.999/43.358/2.638 ms
  user@home:~$ tracepath !$
  tracepath [www.bbc.co.uk](www.bbc.co.uk)
   1:  send failed
       Resume: pmtu 65535 


Also forgot to post links I used in my initial investigations. Heres some of them:

  [https://help.ubuntu.com/community/StaticDnsWithDhcp](https://help.ubuntu.com/community/StaticDnsWithDhcp)
  [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89160](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89160)
  [http://www.nabble.com/DNS-unreliable-with-a-Linksys-ADSL2MUE-adsl-modem-t806808.html](http://www.nabble.com/DNS-unreliable-with-a-Linksys-ADSL2MUE-adsl-modem-t806808.html)
  [https://bugs.launchpad.net/ubuntu/+bug/81057](https://bugs.launchpad.net/ubuntu/+bug/81057)
  [http://ubuntuforums.org/showthread.php?t=385094&page=2](http://ubuntuforums.org/showthread.php?t=385094&page=2)
  [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)


Heres hoping
T

---

### Post by Digger78 on 2007-11-23
post outputs from **iwconfig** and **route**

---

### Post by tanndo on 2007-11-25
Here you go:

user@home:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

user@home:~$ route
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local            *               255.255.0.0      U     1000   0        0 eth0
default       mygateway1.ar7  0.0.0.0         UG    100    0        0 eth0

The more I think about this the more I think something is fundamentally wrong esp. as
i can't connect to my modem/router on 192.168.1.1

---

### Post by mellowd on 2007-11-25
Your gateway should be 192.168.1.1 and not 192.168.1.0 as shown.

Are you trying to get an ip via dhcp?

---

### Post by Digger78 on 2007-11-25
If you have the **avahi-daemon** and **avahi-autoipd** packages installed try removing them, then reboot.

they are part of [Zeroconf]("http://en.wikipedia.org/wiki/Zeroconf") i recently had the same problem, removing them solved it.

when removed, **route** should no longer show - **link-local * 255.255.0.0 U 1000 0 0 eth0**

---

### Post by tanndo on 2007-11-25
found and removed via synaptic package manager
also said it needed to remove libnss-mdns and ubuntu-desktop

Still no change after reboot :(

[INDENT][FONT="Courier New"]tanndo@home:~$ route
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *                  255.255.255.0   U     0         0        0  eth0
link-local            *                  255.255.0.0       U     1000   0        0  eth0
default          192.168.1.1    0.0.0.0              UG    100     0        0  eth0[/FONT]

[/INDENT]So my default gateway is 192.168.1.1 (the linksys modem/router) which is correct I think ?

Here's my interfaces setup:

tanndo@home:~$ ifconfig -a
[INDENT]eth0      Link encap:Ethernet  HWaddr 00:17:31:88:77:AB  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17 errors:7 dropped:0 overruns:0 frame:7
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2115 (2.0 KB)  TX bytes:1585 (1.5 KB)
          Interrupt:21 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
[/INDENT]

Also the router is there:

[INDENT]tanndo@home:~$ telnet 192.168.1.1 
Trying 192.168.1.1...
Connected to 192.168.1.1.
Escape character is '^]'.

BusyBox on (none) login: Connection closed by foreign host.
[/INDENT]

And also on port 80:

[INDENT]tanndo@home:~$ telnet 192.168.1.1 80
Trying 192.168.1.1...
Connected to 192.168.1.1.
Escape character is '^]'.
[/INDENT]

Still can't get to router admin screen or indeed any other web site except google which works 
fine. Can even do searches from google, results page loads lightning fast but as soon as you click on
a link just says "waiting"

---

### Post by Digger78 on 2007-11-26
what is the result of **tracepath www.bbc.co.uk**

I dont know what else to say, maybe its a driver issue?

---

### Post by tanndo on 2007-11-26
Fixed I think ! 

Whilst browsing about (via XP) came across a post on linksys and MTU
Apparently another linksys "issue" on some of their kit.
Mine was set at 1500 which is too high.
I've now put it down to 1492 and everything has just started working :)

I had to change the MTU on the router (luckily I could do this from XP)
For my firmware (unoffical ADSL2MUE firmware Software Version:  	2.17-TI)
the setting was under Setup->Wan setup-> then a field under the plusnet connection I'd
set up.
Then I had to save the setting via Tools->System commands->save all
otherwise you get 1500 back when you switch it on and off :)

Then you have to set the mtu in ubuntu for the interface. How depends on wether you
have static or dhcp. I'm using dhcp, here's the deal:

[INDENT]tanndo@home:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
pre-up /sbin/ifconfig $IFACE mtu 1492
# only for static
#mtu 1492
[/INDENT]


Anyway I can now surf which is the main thing, though perhaps all is not perfect
as a tracepath to bbc still times out

[INDENT]tracepath [www.bbc.co.uk](www.bbc.co.uk)
 1:  192.168.1.2 (192.168.1.2)                              0.273ms pmtu 1492
 1:  no reply
 2:  lo0-plusnet.pte-ag2.plus.net (195.166.128.72)        asymm  3  73.430ms 
 3:  ge0-0-0-504.pte-gw2.plus.net (84.92.4.90)             74.435ms 
 4:  vl23.thn-gw2.plus.net (212.159.4.20)                  69.942ms 
 5:  rt0.thdo.bbc.co.uk (212.58.239.25)                    73.236ms 
 6:  212.58.238.133 (212.58.238.133)                       83.933ms 
 7:  fe0-0.rt0-frontpost.prodgw.bbc.co.uk (212.58.239.222)  75.436ms 
 8:  no reply
...etc
31:  no reply
     Too many hops: pmtu 1492
     Resume: pmtu 1492 
[/INDENT]

FYI I still believe it is necessary to disable ipv6 and reconfigure tcp window scaling and force static DNS lookup (see my first post for details) for the ADSL2MUE

Also I've found it necessary to switch modem on first before booting ubuntu.
When I booted first I think avahi kicked in then on starting firefox (which needed to update) my keyboard started blinking and mouse stopped responding. 

Brown screen of death anyone ?

Had to reach for the off switch ! Rebooted to "recovery mode" (?), which  dumped me to root prompt at terminal. Typed exit and windows GUI loaded, Another reboot and all seems well again

Thanks to those who replied. Your comments gave me the will to carry on
and find a solution!

One final comment, I thought ubuntu was supposed to be "easy" to set up.

Clearly from my limited experience its hardly plug and play. There's no way your average
windows user would have persevered with this to get it working.
Perhaps there should be a resource (maybe there is ?) e.g. a sticky in the forum or
a wiki. Something like 

"List of known working modem/router configurations for ubuntu ver xxx and how to setup"

Oh and how do I mark this solved ?

---

### Post by Digger78 on 2007-11-27
Glad you got it all sorted.

[How to mark your thread solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

I ain't been using linux very long, your right it does require more work than windows but i still wouldn't go back.

The more people use linux the better, Hardware manufacturers will need to provide driver packages just like they do for windows.

---

### Post by tanndo on 2007-11-28
yes you're right, 

it is harder but you do get a sense of satisfaction from working
it out, and a better understanding of the underlying technologies, and it's not
so hard on the bank balance. I for one won't be upgrading to vista :)

long live the linux community ! Rock on :guitar:

---

