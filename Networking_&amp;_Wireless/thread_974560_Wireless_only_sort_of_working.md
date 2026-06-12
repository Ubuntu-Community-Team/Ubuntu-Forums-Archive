---
title: "Wireless only sort of working"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by viergeame on 2008-11-07
I upgraded to Intrepid a couple of days ago because my wireless wasn't working at all and I was having a lot of issues with everything freezing.  

When I first finished the upgrade everything appeared to be working perfectly, it recognized all my hardware right away and my connection was awesome.  This was for the first 15 minutes or so.  Ever since then I will occasionally be able to be online but it's very sporadic and usually doesn't last long.  At first I thought it was just because the connection at my apartment isn't always reliable.  Then I noticed that my roommates weren't having any problems connecting.  What I find to be strange about this problem is that my network manager shows that I am connected, and even shows that my signal strength is very good (usually at least 90%).  This problem seems to apply to every program that accesses the internet (Pidgin, Firefox, even Synaptic).

---

### Post by rhcm123 on 2008-11-07
> **viergeame said:**
> I upgraded to Intrepid a couple of days ago because my wireless wasn't working at all and I was having a lot of issues with everything freezing.  

When I first finished the upgrade everything appeared to be working perfectly, it recognized all my hardware right away and my connection was awesome.  This was for the first 15 minutes or so.  Ever since then I will occasionally be able to be online but it's very sporadic and usually doesn't last long.  At first I thought it was just because the connection at my apartment isn't always reliable.  Then I noticed that my roommates weren't having any problems connecting.  What I find to be strange about this problem is that my network manager shows that I am connected, and even shows that my signal strength is very good (usually at least 90%).  This problem seems to apply to every program that accesses the internet (Pidgin, Firefox, even Synaptic).

Can you ping your router?
Open up a terminal and type:
```
ping -c 3 (ip of router here)
```
If you can, then it is probably a problem with the programs/your config.
If you can't then your connection has a problem.

---

### Post by viergeame on 2008-11-07
When I tried that I got 100% packet loss.  I tried that last night too and ended up with the same result.  It transmits (or at least says it does) but doesn't recieve anything.

---

### Post by rhcm123 on 2008-11-07
Alright, that means it's a connection problem. In someways, that's good, in others, bad.

I've heard a rumor on the interweb that network-manager and Intrepid don't play well togther. So, I'm going to static conf your system.

Please post your router address here, and I will get back to you with the correct settings.

---

### Post by viergeame on 2008-11-07
I'll PM it to you, I don't really want it here on the forum for everyone to see.  I know there there are unfortunately some people that would use it for more harm than good, but I'm sure you understand that.

---

### Post by rhcm123 on 2008-11-07
If it's a 192.168.X.X address, i woulden't be worried. But go ahead, i send the settings back to you. Post any problems back on the thread.

---

### Post by viergeame on 2008-11-07
I used the settings you gave me and things are a bit more confusing.  I still can't use Pidgin or anything like that, but I don't get any packet loss from pinging anymore.  It still shows that I'm connected and all that, but it still isn't doing anything.  I can't imagine that it would be a problem with my programs, as it seems incredibly unlikely that so many programs would have the same problem all at once.  I think my computer just hates me, lol.

---

### Post by rhcm123 on 2008-11-07
> **viergeame said:**
> I used the settings you gave me and things are a bit more confusing.  I still can't use Pidgin or anything like that, but I don't get any packet loss from pinging anymore.  It still shows that I'm connected and all that, but it still isn't doing anything.  I can't imagine that it would be a problem with my programs, as it seems incredibly unlikely that so many programs would have the same problem all at once.  I think my computer just hates me, lol.

Are you sure you can ping? Test it again, and, if you get no packet loss, then restart and try and access the interweb again. If you can, congrats. If not, then perhaps you are having difficulties on your router.

---

### Post by viergeame on 2008-11-07
I tried the ping again, and it worked exactly like it was supposed to.  I restarted, because everyone knows that magically fixes all sorts of things and still no go.  Hopefully it's not the router as I don't really have access to that.  It's in my landlord's office.  Maybe I messed something up putting in the settings.

---

### Post by rhcm123 on 2008-11-07
Would you mind if i post you IP here? There isn't and malicious things one could do with a 192.168 address only, as all small home-use routers have the same address.

---

### Post by viergeame on 2008-11-07
Go for it, I don't care quite so much, it's my roommates that are paranoid.  But what they don't know, they can't get mad at me for.

---

### Post by rhcm123 on 2008-11-07
> **viergeame said:**
> Go for it, I don't care quite so much, it's my roommates that are paranoid.  But what they don't know, they can't get mad at me for.

:)

Now, for the fancy-pantsy MANUAL NETWORK CONFIGUREATION!!! (I love saying that.) This will seem long, and confuzzling, bear with.

Go back to the network settings page (I think it's system, prefrences, network) and find the interface name of the wi-fi adapter. It's typically somthing like eth1 or ath0. Or type:
```
ifconfig
```
and find the one that isnt lo (the loopback interface) or your ethernet interface. I'm going to use eth5 in our code here, punch in what ever is appropriate for you..

Here we go, shell network configureation. Type this at a shell prompt (you can't use your mouse here, sorry about that):
```
sudo nano /etc/network/interfaces
```
If it asks you for your password, give it.
You should see a block of code(s) come up. Find this part:
```
#The primary network interface
auto eth0

```

This is the main network interfaces section. You should see a bunch of lines that look like this:
```

iface eth0 inet dhcp

```
These are the auto-configed interfaces. We don't want these. Scroll down until you find eth5 (the interface i'm using in my example), and you should see the settings you entered in earlier.
Make sure they look like this: (this is going to require modification and some paitence.) remember, the space from the side of the screen is very important and can be made with 1 tab key.

```

iface eth5 inet static
        address 192.168.1.123
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.0.255
        gateway 192.168.1.2

```

Now, hit ctrl-X. press y, then hit enter. You will be brought back to the shell prompt. Type this now:
```

sudo /etc/init.d/networking restart

```
That will restart the networking. Try to ping and connect again. If that doesn't work or this is too hard, write up another post with your problems. GOOD LUCK!:popcorn:

---

### Post by viergeame on 2008-11-07
It still doesn't seem to be working.  I'm wondering if something is wrong in the hardware setup or something.  When I typed ifconfig I got a longer list of results than I think I should have.  I could be wrong though.

---

### Post by rhcm123 on 2008-11-07
Please copypasta them here. To copy from a terminal, you have to use ctrl+shift+c. It could help me diagnose your problem.

---

### Post by viergeame on 2008-11-07
```
nikki@nikki-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:60:f2:31:36  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:131361 errors:0 dropped:0 overruns:0 frame:0
          TX packets:131361 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6590808 (6.5 MB)  TX bytes:6590808 (6.5 MB)

wlan2     Link encap:Ethernet  HWaddr 00:16:44:19:2d:b0  
          inet addr:192.168.1.134  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:44ff:fe19:2db0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:185 errors:0 dropped:0 overruns:0 frame:0
          TX packets:447 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18400 (18.4 KB)  TX bytes:82105 (82.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-44-19-2D-B0-64-62-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```


Thank goodness for flash drives, with the nature of my problem I've been doing all this posting from a friend's computer.  Without a flash drive it would have been pretty ridiculous to get all that code in this post.

---

### Post by rhcm123 on 2008-11-07
> **viergeame said:**
> ```
nikki@nikki-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:60:f2:31:36  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:131361 errors:0 dropped:0 overruns:0 frame:0
          TX packets:131361 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6590808 (6.5 MB)  TX bytes:6590808 (6.5 MB)

wlan2     Link encap:Ethernet  HWaddr 00:16:44:19:2d:b0  
          inet addr:192.168.1.134  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:44ff:fe19:2db0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:185 errors:0 dropped:0 overruns:0 frame:0
          TX packets:447 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18400 (18.4 KB)  TX bytes:82105 (82.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-44-19-2D-B0-64-62-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```


Thank goodness for flash drives, with the nature of my problem I've been doing all this posting from a friend's computer.  Without a flash drive it would have been pretty ridiculous to get all that code in this post.

Yes, flash drives are very good. A working network is even better.
:KS

Now, I read this output:
eth0 -your ethernet interface. It reads as disconnected, which is fine.
lo - loopback interface. It's working, so no probs. (don't worry about it)
wlan2 - That's the name. As far as i can tell, it's transmitting and it says there are no errors.
wmaster0 - I am suprised this wasn't hidden. It's not bad, though. the wmaster is what is called the master interface for the wi-fi programs. On older distros (such as pre 7.04) this was not hidden. I am suprised they are showing it again in 8.10.

Anyways, it appears you have an all good connection on your end.

I am going to ask you to ping your router and google again. To ping google, type this:
```

ping -c 3 google.com

```
Also, please type the following at the shell prompt and copy up the results:
```

cat /etc/network/interfaces

```

I hope this isn't getting to complex. :)

---

### Post by viergeame on 2008-11-07
```
nikki@nikki-laptop:~$ ping -c 3 google.com
ping: unknown host google.com
nikki@nikki-laptop:~$ ping -c 3 192.168.1.134
PING 192.168.1.134 (192.168.1.134) 56(84) bytes of data.
64 bytes from 192.168.1.134: icmp_seq=1 ttl=64 time=0.040 ms
64 bytes from 192.168.1.134: icmp_seq=2 ttl=64 time=0.040 ms
64 bytes from 192.168.1.134: icmp_seq=3 ttl=64 time=0.048 ms

--- 192.168.1.134 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 0.040/0.042/0.048/0.008 ms
nikki@nikki-laptop:~$ ping -c 3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.134 icmp_seq=1 Destination Host Unreachable
From 192.168.1.134 icmp_seq=2 Destination Host Unreachable
From 192.168.1.134 icmp_seq=3 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 1999ms
, pipe 3
nikki@nikki-laptop:~$ ping -c 3 192.168.1.2
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
From 192.168.1.134 icmp_seq=1 Destination Host Unreachable
From 192.168.1.134 icmp_seq=2 Destination Host Unreachable
From 192.168.1.134 icmp_seq=3 Destination Host Unreachable

--- 192.168.1.2 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2011ms
, pipe 3
nikki@nikki-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback




iface eth0 inet static
	address 192.168.1.134
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.0.255
	gateway 192.168.1.2
wireless-essid NETGEAR

auto wlan0
```

Hopefully that is right.  If not... well I'm sorry it's been awhile since I've dealt with anything like this and I've pretty much forgotten everything.  Thanks a ton for being so patient with me.

---

### Post by rhcm123 on 2008-11-07
> **viergeame said:**
> ```
nikki@nikki-laptop:~$ ping -c 3 google.com
ping: unknown host google.com
nikki@nikki-laptop:~$ ping -c 3 192.168.1.134
PING 192.168.1.134 (192.168.1.134) 56(84) bytes of data.
64 bytes from 192.168.1.134: icmp_seq=1 ttl=64 time=0.040 ms
64 bytes from 192.168.1.134: icmp_seq=2 ttl=64 time=0.040 ms
64 bytes from 192.168.1.134: icmp_seq=3 ttl=64 time=0.048 ms

--- 192.168.1.134 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 0.040/0.042/0.048/0.008 ms
nikki@nikki-laptop:~$ ping -c 3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.134 icmp_seq=1 Destination Host Unreachable
From 192.168.1.134 icmp_seq=2 Destination Host Unreachable
From 192.168.1.134 icmp_seq=3 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 1999ms
, pipe 3
nikki@nikki-laptop:~$ ping -c 3 192.168.1.2
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
From 192.168.1.134 icmp_seq=1 Destination Host Unreachable
From 192.168.1.134 icmp_seq=2 Destination Host Unreachable
From 192.168.1.134 icmp_seq=3 Destination Host Unreachable

--- 192.168.1.2 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2011ms
, pipe 3
nikki@nikki-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback




iface eth0 inet static
	address 192.168.1.134
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.0.255
	gateway 192.168.1.2
wireless-essid NETGEAR

auto wlan0
```

Hopefully that is right.  If not... well I'm sorry it's been awhile since I've dealt with anything like this and I've pretty much forgotten everything.  Thanks a ton for being so patient with me.

No problem for being paitent with you.

Whoa, this is full of problems. I'll address them one at a time, hopefully solve this.
1: Google Ping. Ok, i see your still having connection problems.
2: 192.168.1.134. You pinged yourself! No wonder you were getting responses! Ping 192.168.1.2 (your router) next time and see what happens, after doing the below.)
3: 192.168.1.1. This isn't your router ip (that's what you said, correct?). Ping 192.168.1.2 next time.
4: 192.168.1.2. Wow, you read my thoughts. :) Ok, this means you aren't connected at all to the router.
5: You misconfiged the interfaces... Here we go again, manual conf.

change 
```

iface eth0 inet static

```
to
```

iface eth0 inet dhcp

```

And remove everything beneath it.

It looks like you setup your ethernet interface, not the wifi.
I'm going to reccomend you go back to the network conf tool (from system prefences) and be sure you configure your wifi. Then, do the cat test again, and post it up here. Thanks for being so helpful with the cod.

---

### Post by viergeame on 2008-11-07
```
auto lo
iface lo inet loopback




iface eth0 inet dhcp
```

Is that right?

---

### Post by rhcm123 on 2008-11-07
> **viergeame said:**
> ```
auto lo
iface lo inet loopback




iface eth0 inet dhcp
```

Is that right?

yes, it is. Input it, then do this:
```
sudo /etc/init.d/networking restart
```

---

### Post by viergeame on 2008-11-07
Still no go.  The planets must not be aligned correctly or something...

---

### Post by rhcm123 on 2008-11-07
> **viergeame said:**
> Still no go.  The planets must not be aligned correctly or something...

Ok, you did the input, yes, and reconfigured the wifi, yes?
I must say, this is quite odd. Try again reconfiguring it manually, but like this (beneath the wifi entry):

```

iface wifi0 inet static
     address 192.168.1.123
     netmask 255.255.255.0
     gateway 192.168.1.2

```

try that, and make sure you add the ssid tag of whatever it was (you had it in the entry earlier)

---

### Post by viergeame on 2008-11-07
After checking things over again it turns out I made a typo, so I corrected that.  Things worked for a couple minutes, then they stopped.

---

### Post by rhcm123 on 2008-11-07
> **viergeame said:**
> After checking things over again it turns out I made a typo, so I corrected that.  Things worked for a couple minutes, then they stopped.

Could you do the following, in this order, the post the outputs?
1. sudo /etc/init.d/networking force-reload
2. ifconfig
3. iwconfig
4. cat /etc/network/interfaces

---

### Post by viergeame on 2008-11-07
```
nikki@nikki-laptop:~$ sudo /etc/init.d/networking force-reload
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan2=wlan2.
                                                                         [ OK ]
nikki@nikki-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:60:f2:31:36  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:256 errors:0 dropped:0 overruns:0 frame:0
          TX packets:256 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16320 (16.3 KB)  TX bytes:16320 (16.3 KB)

wlan2     Link encap:Ethernet  HWaddr 00:16:44:19:2d:b0  
          inet addr:192.168.1.134  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:44ff:fe19:2db0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:164 errors:0 dropped:0 overruns:0 frame:0
          TX packets:129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21226 (21.2 KB)  TX bytes:13473 (13.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-44-19-2D-B0-64-62-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

nikki@nikki-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan2     IEEE 802.11bg  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1E:2A:4F:1F:A0   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=88/100  Signal level:-27 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

nikki@nikki-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback




iface wifi0 inet static
	address 192.168.1.123
	netmask 255.255.255.0
	gateway 192.168.1.2
wireless-essid NETGEAR

```

---

### Post by rhcm123 on 2008-11-07
Well, honestly, it's all working.
I'm begining to think this is a bug in 8.10. 8.10 is already infamusly buggy for wi-fi, and i think you were hit with it hard.
The system returned everything normal.
I would try and reboot, but I cant see anything wrong. Sorry.

EDIT:
Wait a tic, this is strange. I noticed on the ifconfig it said that wifi2's IP was 192.168.2.134
But your conf file says wifi0! Thats the problem!!! Change the conf file to wifi2 and restart networking. then try it again!

---

### Post by viergeame on 2008-11-08
I fixed that and it still isn't working.  Maybe I should just downgrade to 8.04.  I don't really want to go through the hassle, but it may be worth it so I could have interwebs.

---

### Post by rhcm123 on 2008-11-08
> **viergeame said:**
> I fixed that and it still isn't working.  Maybe I should just downgrade to 8.04.  I don't really want to go through the hassle, but it may be worth it so I could have interwebs.

It probably would be worth it. I am still using 8.04 LTS and am refusing to upgrade because of all the internet/networking problems. Considering i run a server, a well-functioning network is very important. Sorry about that.

---

