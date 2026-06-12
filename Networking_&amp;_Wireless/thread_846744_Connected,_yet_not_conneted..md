---
title: "Connected, yet not conneted."
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by detroit/zero on 2008-07-01
Hi, all..

I have an odd problem that just popped up on me.

My networking ability just sort of crapped out on me. I'm using a Toshiba Satellite a135 with Hardy Heron and all current updates.

I was online reading news and whatnot, when out of nowhere I get the Firefox "can't load page" screen.

It seems I somehow got booted off my own network. After some doing, I managed to reconnect to my wireless router. I can check and manipulate my router config at address 192.168.1.1 in my browser, I can ping other computers on the network, and I even have access to samba shares on one of them.

Thing is, whenever I try to load a page off the WWW, I get the "can't load page" screen. It leads me to believe there's some kind of DNS error, but I have the corret DNS settings as per my routers' config page.  (192.168.1.1/primary, 0.0.00)

One thing I did notice is that in Network Managers DNS tab, my loopback address is being inserted into the DNS server list, and in the connection information it shows up as the primary DNS - no amount of doing will change this or stop it from happening.

Another thing I also notice is  that when I'm in a terminal and execute a sudo command, I get a quick message about "unable to resolve local host zero-laptop" or some such thing. What happened there?

Two questions: How do I make my computer able to see the WWW again? If it's not guaranteed to work, cn't I just delete all the network/keyring/connection information and re-connect to my network like it was the very first time?

I tried deleting all the DNS servers inside network manager, and I deleted my network from the keyring app to try and start over, but I must have missed something because it goes back the same way every time.

I did happen to check some things, and I notice that usually there is some kind of DHCP something running in my sessions/services tabs, but it's not currently there? What is this service? Where did it go? Is it a likely culprit? If so, how do I get it back?

I can post any info you may need to help, but I won't be back until after a good nights' rest.

Thanks in advance..

---

### Post by superprash2003 on 2008-07-01
pleas post ifconfig output.. and also iwconfig output. also type ping google.com in your terminal and post output

---

### Post by detroit/zero on 2008-07-02
As requested, here are the outputs of the commands:

```
zero@zero-laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:1b:9e:0f:69:bc  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:230 errors:0 dropped:0 overruns:0 frame:0
          TX packets:226 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:284091 (277.4 KB)  TX bytes:16358 (15.9 KB)

eth0      Link encap:Ethernet  HWaddr 00:16:d4:f7:f8:4d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4524 (4.4 KB)  TX bytes:4524 (4.4 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-1B-9E-0F-69-BC-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7113 errors:0 dropped:0 overruns:0 frame:13196
          TX packets:484 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:944322 (922.1 KB)  TX bytes:37983 (37.0 KB)
          Interrupt:16 
``````
zero@zero-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"XXXXX"  Nickname:"XXXXX"
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:1A:6B:CA:4D:C1   
          Bit Rate:54 Mb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-30 dBm  Noise level=-96 dBm
          Rx invalid nwid:5505  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
``````
zero@zero-laptop:~$ ping www.google.com
PING www.l.google.com (66.249.91.99) 56(84) bytes of data.
64 bytes from ik-in-f99.google.com (66.249.91.99): icmp_seq=1 ttl=242 time=42.5 ms
64 bytes from ik-in-f99.google.com (66.249.91.99): icmp_seq=2 ttl=242 time=41.9 ms
64 bytes from ik-in-f99.google.com (66.249.91.99): icmp_seq=3 ttl=242 time=40.9 ms
64 bytes from ik-in-f99.google.com (66.249.91.99): icmp_seq=4 ttl=242 time=43.0 ms
64 bytes from ik-in-f99.google.com (66.249.91.99): icmp_seq=5 ttl=242 time=40.6 ms

--- www.l.google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4006ms
rtt min/avg/max/mdev = 40.694/41.834/43.004/0.912 ms
```So, as you can see, I *am *connected to my wireless network. The google.com name was resolved for the ping, so I guess that blows that theory out of the water.

The problem isn't limited to just Firefox, though - Thunderbird can't connect to my mail servers, either. I haven't tried any other programs, but I assume it will have a similar outcome.

I see the "invalid network id" under iwconfig's transmit/receive tally - what's that all about? Is that the problem?

**EDIT: **I haven't tried a wired connection yet. I'll get to it before my next post and let you know what happens.

---

### Post by detroit/zero on 2008-07-02
I have to bump this in the hopes of getting a quick answer. I'm stuck using Vista (on the same laptop, btw) in the meantime and it's killing me.

Also - a wired connection doesn't work. I can still ping my other machine and browse my samba shares, but I have no access to the www.

So, to sum up: 

[LIST]
[*]Vista on the same laptop works;
[*]My other laptop works (wired *and *wireless) with access to WWW;
[*]I can connect to my wireless network, access my router config pages, ping other machines on the LAN, and even ping [www.google.com]("http://www.google.com") (results posted above);
[*]The eth0 and ath0 interfaces are recognized, configured, and functioning (see iwconfig and ifconfig above)
[*]I have no access from Ubuntu to the internet, either through Firefox, Thunderbird, instant messaging, or any other application I can think of to test.
[/LIST]
Can anybody tell me why?

---

### Post by superprash2003 on 2008-07-02
try changing DNS servers to opendns [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by detroit/zero on 2008-07-02
Your blog posts are not helpful, and it seems like you're spamming the hell out of these forums. 

A quick search of your posts shows that your generic "please post ifconfig/iwconfig output" is always followed by "check out my blog posts at ..."

I need real help, not generic spam. You've been reported.

Can someone without a blog to drive traffic to offer me some advice?

Can I run off the livecd and re-install my network management software in a default state? Should I just re-install the entire OS?

Someone? Please?

---

### Post by DudsOne on 2008-07-02
I agree with detroit/zero.

superprash seems quite self-serving and generally
just waste our time adding to the frustration.

---

### Post by superprash2003 on 2008-07-02
im sorry to have hurt your feelings guys but you guys are misunderstanding me..in your case ping is successful but you are not able to access any website..this is a common DNS problem.. most isp's have overloaded dns servers causing this problem.. the solution happens to be in my blog which i have posted months back..i find it easy to link to my blog that manually typing the solution always as this is a common issue.. and "check out blog posts..." is my signature not in every post!!!
  and ifconfig and iwconfig outputs are very much required in networking questions.. how can i not ask for that output to proceed!!!

---

### Post by chili555 on 2008-07-02
> It leads me to believe there's some kind of DNS error, but I have the corret DNS settings as per my routers' config page. (192.168.1.1/primary, 0.0.00)I suspect it's a DNS error, as well. Does your router have static DNS servers, that is, numbers you fill in yourself, or does it get DNS servers from your ISP? Usually, the DHCP process on your computer will grab the DNS servers and use them in */etc/resolv.conf.* Even if your */etc/resolv.conf* generically points to the router, 192.168.1.1, if any of the DNS servers in the router are not working as expected, then the whole process breaks down.

I have issues with OpenDNS servers because it takes longer for pings to return from OpenDNS servers than it does from the DNS servers my ISP provides:> chili@LAPTOP60:~$ ping -c3 208.67.220.220
PING 208.67.220.220 (208.67.220.220) 56(84) bytes of data.
64 bytes from 208.67.220.220: icmp_seq=1 ttl=46 time=36.4 ms
64 bytes from 208.67.220.220: icmp_seq=2 ttl=46 time=36.7 ms
64 bytes from 208.67.220.220: icmp_seq=3 ttl=46 time=35.6 ms

--- 208.67.220.220 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 35.680/36.318/36.780/0.465 ms
chili@LAPTOP60:~$ ping -c3 205.152.37.23
PING 205.152.37.23 (205.152.37.23) 56(84) bytes of data.
64 bytes from 205.152.37.23: icmp_seq=1 ttl=55 time=21.1 ms
64 bytes from 205.152.37.23: icmp_seq=2 ttl=55 time=22.6 ms
64 bytes from 205.152.37.23: icmp_seq=3 ttl=55 time=17.8 ms

--- 205.152.37.23 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2005ms
rtt min/avg/max/mdev = 17.861/20.546/22.677/2.011 msThat suggests to me that it will take longer for OpenDNS servers to receive, process and return the IP number. My assumption may be peculiar to my remote, woodsy location.

If there are static DNS servers in your router, I suggest removing them, rebooting the router and setting up */etc/resolv.conf* as follows:```
nameserver 192.168.1.1
```

---

### Post by detroit/zero on 2008-07-03
Just to be fair, I did try using prash's opendns solution - it didn't work.

What the problem was is that somehow, and for reasons unbeknown to me, my primary DNS server was being changed to 127.0.0.1     I'm not sure what would cause that, and I tried like hell to remedy it, but no matter what I did it kept changing itself back to the loopback address.

Here are two screenshots. The first thumbnail is a shot of the nm-applet connection information window while running a live session off the 8.04 cd. The second is a shot of the same while running my normal, installed Hardy:

[CENTER][IMG]http://img379.imageshack.us/img379/8351/screenshotconnectioninfwk4.png[/IMG][IMG]http://img112.imageshack.us/img112/6241/screenshotconnectioninfxc9.png[/IMG]
[LEFT]
Like I said, I couldn't figure out what caused it. Maybe it's related to the file you suggest, but I did some thinking about it and I remember clicking on the Hosts tab in the Network Manager. After that is when my computer started acting squirrely. I went and opend my hosts file and it was all messed up - entries running into eachother, all the commented lines moved to the bottom, things like that. No matter what I did to the hosts file (even restoring the original, backed up version) didn't fix the problem.

All said and done, since I have /home on a separate partition, and since I was in a pinch and had to get moving on that problem fast, I just wiped my root partition and did a clean install. I used dpkg to create a list of all my installed packages, and once I had finished my fresh install I used dpkg again to reinstall everything. It took two hours, start to finish, which was already less time than I had invested in tracking down the cause of the problem. 

Overkill? Yeah. I'm reminded of an analogy about swatting flies with a bazooka.

It worked though.
[/LEFT]
[/CENTER]

---

### Post by superprash2003 on 2008-07-03
oh cool.. glad you got it working!!normally if you place the dns servers in the dhclient.conf file it should be using that first by default

---

