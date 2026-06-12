---
title: "Trying to Establish Static IP Addresses Not Working"
date: 2016-07-08
forum: Networking &amp; Wireless
---

### Post by Alcidious on 2016-07-08
I stretched ethernet cables to both ends of my house, in order to create a wired LAN instead of relying on wifi signals. I then attempted to edit /etc/network/interfaces to reflect:

auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.2.11
netmask 255.255.255.0
gateway 192.168.1.251 auto eth0 

Can anyone assist? I'm not sure what the issue is. It worked at first, with the ethernet cable plugged in, and ordered the wifi stopped. But upon shutting down the computers, I can't connect to the ethernet..

FYI, I"m running 16.04 Ubuntu LTS on a laptop, and Kubuntu 16.04 LTS on a PC tower.

---

### Post by chili555 on 2016-07-08
First, I recommend that you remove these settings, except, of course, the loopback interface lo, and allow Network Manager do the work.

Why do you require static IP addresses? Your router should smoothly assign addresses by DHCP with no effort on your part.

I doubt that your router (gateway) address is 192.168.1.251. Even if it is, a static address of 192.168.[COLOR="#FF0000"]2[/COLOR].11 won't ever connect. Finally, you have set no DNS addresses.

Have you verified these numbers on other devices on the same network; phones, 'Pads, 'Pods, etc.?

Please tell us what you are trying to do and we'll be happy to help.

PS - I see you are in Charlotte. Maybe I should drive over and fix it!!!

---

### Post by SeijiSensei on 2016-07-09
```

auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.2.11
netmask 255.255.255.0
gateway 192.168.1.251 auto eth0 

```
The "auto eth0" directive should appear before "iface eth0" like this:

```

auto lo
iface lo inet loopback

auto eth0 
iface eth0 inet static
address 192.168.2.11
netmask 255.255.255.0
gateway 192.168.1.251

```

Worse, you have the computer itself in 192.168.2.0/24 while the router is in 192.168.1.0/24.  That won't work.  The computer needs to have an address in the same network subnet as the router, e.g, 192.168.1.11.

Still, I agree with chili that you should just let your router assign the addresses via DHCP unless this machine is intended for use as a server.  Use this stanza instead:
```

auto eth0
iface eth0 inet dhcp

```
and things should work fine.

---

### Post by Alcidious on 2016-07-09
I appreciate the response ... I took a networking class years ago, but have clearly forgotten most of it.

I'm trying to create a wired LAN. My main PC quit working very well when I switched ISP's because the wifi signal didn't extend to it (I think because the adapter is 6 or 7 years old -- and AT&T U-verse has two protocols, one of which is not supported on that adapter). Additionally, I've created a home media/file server, and I want all my files to play as fast possible on any of my computers. After talking with some friends I decided a wired connection was the way to go. 

After doing plenty of reading, all the tutorials suggested static IP's ... I'm guessing I could get around that and just use DHCP, but my working assumption is that my file server, at least, needs a static address so that I can find it from each computer. A couple of the tutorials I'm using are posted below ...

[http://tuxtweaks.com/2008/10/how-to-set-up-a-home-network-with-ubuntu-part-1/](http://tuxtweaks.com/2008/10/how-to-set-up-a-home-network-with-ubuntu-part-1/)
[http://chrome-extension://klbibkeccnjlkjkiokjodocebajanakg/suspended.html#uri=http://www.cio.com/article/2901051/create-a-home-server-with-raspberry-pi-2.html](http://chrome-extension://klbibkeccnjlkjkiokjodocebajanakg/suspended.html#uri=http://www.cio.com/article/2901051/create-a-home-server-with-raspberry-pi-2.html)

I kind of jumped the gun and made changes before verifying anything ... so I haven't verified any other devices. My Chromebook and my TV are the only two devices that will actually hop on the internet at the moment. I will do some research and try to verify the Chromebook's settings, some other devices, and my previous settings this afternoon, and also see if adding DNS does anything.

My ultimate goal is to have my most up to date files (spreadsheets, documents, etc.) on ALL of my computers instead of constantly saving iterated versions on thumb drives, through email, etc., AND be able to stream music & movies from my home server (although this is a secondary goal).

Thanks a lot! I really want to succeed in getting my LAN to work on my own, but maybe I'll have to have my new CLT friend stop over if I can't cut it! LOL

---

### Post by steeldriver on 2016-07-09
Most consumer routers these days support IP reservations - basically all the convenience of DHCP, plus the ability to assign the same IP everytime to particular machines** (e.g. your server) making it "static" in all but name

That's how I'd do it in this situation - it means the configuration is centralized (on the router) and easy to manage (you don't need to go around each PC making sure its settings are consistent / non-conflicting)

Open up the manual for your router and check out how to do that

** strictly speaking, to particular interfaces based on their MAC addresses

---

### Post by chili555 on 2016-07-09
> I haven't verified any other devices. My Chromebook and my TV are the only two devices that will actually hop on the internet at the moment. I will do some research and try to verify the Chromebook's settingsPlease do so. Let's start with the IP address and gateway address. We can figure out a workable configuration for the server from there.

It is likely that the router has a pool of IP addresses reserved for DHCP. We'll pick an address likely to be outside the DHCP pool. 

As an example, my (AT&T!) device uses a pool from 192.168.0.2 to 192.168.0.51 for DHCP. My laptop that uses a static IP, just because I can, therefore uses an address of 192.168.0.125.> maybe I'll have to have my new CLT friend stop over if I can't cut it! LOLI'm actually just across the lake in the tax haven known as South Carolina.

---

### Post by Alcidious on 2016-07-13
Hey y'all,

I apologize for the delay in responding. My sweet/dumb pit bull barreled in to my knee this past weekend, I can finally walk. Also, I tried to research all the points that were made in the threads: 

a)[SIZE=1] @ [/SIZE][COLOR=#000000]chili555's, I checked in to the the addresses, the gateways, etc. on my router, on my smartphone, and chromebook. The gateway is correct. But still can't figure out to set or find the proper dns.
b) @ steeldriver, I looked in to IP Reservations on my router. But just kind of fiddled with it, need to find instructions for a Pace PLC 5268AC (on a different page it said 5268AC FXN). Tried AT&T forums ... not nearly as helpful as y'all.
c) @ [/COLOR][COLOR=#000000]SeijiSensei, I fixed the problems you mentioned, but can't pull my wireless up... and made a few more changes, suggested by a an article below. 

Here is what I've done. I made the following edits:

```

auto lo
iface lo inet loopback
#iface eth0 inet dhcp

auto [/COLOR][COLOR=#000000]eth0[/COLOR][COLOR=#000000] inet static
address 192.168.1.112 #changed from 1.12 b/c I attempted to make changes to the router and set dhcp 1.22 - 1.30
netmask 255.255.255.0
gateway 192.168.1.254[/COLOR][COLOR=#000000]
#since working on my laptop, which I wanted static, I found another article posted below to attempt
wpa - ssid XXXXXXXXXXXX
wpa - psk XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
# after running sudo wpa-passphrase XXX XXXX


```

When that didn't work, I went back to DHCP for my laptop using the commented lines above.

I like the idea of DHCP, but how often does it reconfigure itself? Honestly, I would really like to accomplish limiting the DHCP pool, and then leaving others static. I'm trying to learn as much as possible and push my envelope...It's why I drilled into my floors and stretched the cables. Ultimately, would DHCP server better when I'm trying for a media/file server, or even having separate media and file servers?


[/COLOR]

---

### Post by chili555 on 2016-07-13
A static IP address is certainly preferable for any kind of server. You always know where it is and how to ssh and ftp into it. As well, it is eminently suitable in this instance:>  I'm trying to learn as much as possible and push my envelope.I suggest a file like this:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.112 
netmask 255.255.255.0
gateway 192.168.1.254
dns-nameservers 192.168.1.254 8.8.8.8
```The wpa-ssid and password lines are for wireless and aren't needed here.

If you set a static IP, gateway, etc., you are responsible, as well, for DNS. Usually the gateway (router) address is satisfactory; after all, that's where you get DNS information with DHCP! I usually set a backup DNS namesever; in this case, Googles.

Get the system to re-read and use the file:```
sudo ifdown eth0 && sudo ifup -v eth0
```The -v for verbose will produce some output that will give us some clues as to what went right and wrong, if any.

Did you get the desired address?```
ifconfig
```Can you reach the internet and world?```
ping -c3 www.ubuntu.com
```If you get ping returns, you are all set!```
--- www.ubuntu.com ping statistics ---
3 packets transmitted, [COLOR="#FF0000"]3 received, 0% packet loss[/COLOR], time 2002ms
```Woo hoo!!

Next I suggest you start a journal and note that the media server in the upstairs closet is at x.112 or any other reference.

---

### Post by Alcidious on 2016-07-13
So the good news is I'm connected to the internet on my laptop! I'm going to see what happens to my PC tower...

Anyway, here's a post of results for each of the commands you suggested:

```

#notes from "sudo ifdown eth0 && sudo ifup -v eth0" command


~$ sudo ifdown eth0 && sudo ifup -v eth0
ifdown: interface eth0 not configured
Configuring interface eth0=eth0 (inet)
/bin/run-parts --exit-on-error --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
/bin/ip addr add 192.168.1.112 #changed from 12 bc/255.255.255.0 broadcast + 	  dev eth0 label eth0
Not enough information: "dev" argument is required.
Failed to bring up eth0.




# And results of ifconfig


$ ifconfig
e2s0    Link encap:Ethernet  HWaddr e8:11:32:c2:c0:82  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1297 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1297 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:129766 (129.7 KB)  TX bytes:129766 (129.7 KB)


eth0    Link encap:Ethernet  HWaddr dc:a9:74:dd:2f:g9  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2602:306:3ada:ec70:5303:4c4e:387a:7509/64 Scope:Global
          inet6 addr: fe80::c538:6eef:c238:dc2c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:361391 errors:0 dropped:0 overruns:0 frame:0
          TX packets:233853 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:419114226 (419.1 MB)  TX bytes:43097564 (43.0 MB)




# and the ping results


PING www.ubuntu.com (91.189.89.110) 56(84) bytes of data.
64 bytes from www-ubuntu-com.nuno.canonical.com (91.189.89.110): icmp_seq=1 ttl=46 time=117 ms
64 bytes from www-ubuntu-com.nuno.canonical.com (91.189.89.110): icmp_seq=2 ttl=46 time=257 ms
64 bytes from www-ubuntu-com.nuno.canonical.com (91.189.89.110): icmp_seq=3 ttl=46 time=233 ms


--- www.ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 117.697/202.764/257.274/60.941 ms



```

So, my question is what happened? While connecting it's not choosing the static address I ordered? 

I played around last evening and got the laptop working. I'm going to fully restart and make sure can still hop on, and then try my wired PC.
Thanks for all your help!

FYI - if some of the addresses and such don't quite match up, I'm making a half-assed attempt to hide my stuff.

---

### Post by chili555 on 2016-07-13
> Failed to bring up eth0.May we see your *exact* file /etc/network/interfaces? 

There is no need to disguise private IP addresses like 192.168.x.xx. Most of the world has the same.

---

### Post by Alcidious on 2016-07-13
Here you sir!

```
#notes from "sudo ifdown eth0 && sudo ifup -v eth0" command

~$ sudo ifdown wlp1s0 && sudo ifup -v wlp1s0
ifdown: interface wlp1s0 not configured
Configuring interface wlp1s0=wlp1s0 (inet)
/bin/run-parts --exit-on-error --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
/bin/ip addr add 192.168.1.112 #changed from 12 bc/255.255.255.0 broadcast + 	  dev wlp1s0 label wlp1s0
Not enough information: "dev" argument is required.
Failed to bring up wlp1s0.




# And results of ifconfig


$ ifconfig
enp2s0    Link encap:Ethernet  HWaddr e8:11:32:c2:c0:82  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1297 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1297 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:129766 (129.7 KB)  TX bytes:129766 (129.7 KB)


wlp1s0    Link encap:Ethernet  HWaddr dc:a9:71:2d:2f:f8  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2602:306:3ada:ec70:6603:4c4e:387a:7509/64 Scope:Global
          inet6 addr: fe80::c538:6eef:c892:dc2c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:361391 errors:0 dropped:0 overruns:0 frame:0
          TX packets:233853 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:419114226 (419.1 MB)  TX bytes:43097564 (43.0 MB)




# and the ping results


PING [www.ubuntu.com](www.ubuntu.com) (91.189.89.110) 56(84) bytes of data.
64 bytes from www-ubuntu-com.nuno.canonical.com (91.189.89.110): icmp_seq=1 ttl=46 time=117 ms
64 bytes from www-ubuntu-com.nuno.canonical.com (91.189.89.110): icmp_seq=2 ttl=46 time=257 ms
64 bytes from www-ubuntu-com.nuno.canonical.com (91.189.89.110): icmp_seq=3 ttl=46 time=233 ms


--- [www.ubuntu.com](www.ubuntu.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 117.697/202.764/257.274/60.941 ms

```

---

### Post by chili555 on 2016-07-13
Isn't wlp1s0 your wireless device and not ethernet? Again, may I see your exact /etc/network/interfaces file?

---

### Post by Alcidious on 2016-07-13
Also, just got back from the store, and ran each step of the procedure on my wired tower (and am posting similar report below). I changed the address in my /etc/network/interfaces list (as per static ip protocol) but I didn't get a signal on this ping at all.  Much help is appreciated!

```

#~$ sudo ifdown enp0s25 && sudo ifup -v enp0s25


ifdown: interface enp0s25 not configured
Configuring interface enp0s25=enp0s25 (inet)
/bin/run-parts --exit-on-error --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
/bin/ip addr add 192.168.1.110/255.255.255.0 broadcast 192.168.1.255      dev enp0s25 label enp0s25
/bin/ip link set dev enp0s25   up
 /bin/ip route add default via 192.168.1.254 8.8.8.8  dev enp0s25 onlink 
Error: either "to" is duplicate, or "8.8.8.8" is a garbage.
Failed to bring up enp0s25.


#:~$ ifconfig


enp0s25   Link encap:Ethernet  HWaddr 00:1c:c0:b1:98:d6  
          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:feb1:98d6/64 Scope:Link
          inet6 addr: 2602:306:3ada:ec70:21c:c0ff:feb1:98d6/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3236 (3.2 KB)  TX bytes:10631 (10.6 KB)
          Interrupt:20 Memory:d0300000-d0320000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:7292 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:570408 (570.4 KB)  TX bytes:570408 (570.4 KB)


wlp7s2    Link encap:Ethernet  HWaddr f8:d1:11:3d:cb:0f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)




#:~$ ping -c3 [www.ubuntu.com]("http://www.ubuntu.com")


ping: unknown host [www.ubuntu.com]("http://www.ubuntu.com")

```

Grazie!

---

### Post by Alcidious on 2016-07-13
For the laptop:
```

# og line: interfaces(5) file used by ifup(8) and ifdown(8)
# updated file 7.13.16 on forum-fix attempt 1


auto lo
iface lo inet loopback


#in case go with dhcp
#auto wlp1s0
#iface wlp1s0 inet dhcp


auto wlp1s0
iface wlp1s0 inet static
address 192.168.1.112 #changed from 12 bc set dhcp 1.22 - 1.30
netmask 255.255.255.0
gateway 192.168.1.254
dns-nameservers 192.168.1.254 8.8.8.8


# google DNS servers - worked but changed
# dns-nameservers 8.8.8.8 8.8.4.4 


#told unneccessary --- look into why and when
#wpa-ssid ATT3prj299
#wpa-psk b8bb7bcfe7e788d1feaa68e14a3f1730b966851052d0652ea7ed186da92bb65e
```


For the PC:
```

# interfaces(5) file used by ifup(8) and ifdown(8)


#changes made 7/13/16 during forums chat


auto lo
iface lo inet loopback


auto enp0s25
iface enp0s25 inet static
address 192.168.1.110
netmask 255.255.255.0
gateway 192.168.1.254 8.8.8.8

```

---

### Post by chili555 on 2016-07-13
```
# og line: interfaces(5) file used by ifup(8) and ifdown(8)
# updated file 7.13.16 on forum-fix attempt 1


auto lo
iface lo inet loopback


#in case go with dhcp
#auto wlp1s0
#iface wlp1s0 inet dhcp


auto wlp1s0
iface wlp1s0 inet static
address 192.168.1.112 [COLOR="#FF0000"]#changed from 12 bc set dhcp 1.22 - 1.30[/COLOR]
netmask 255.255.255.0
gateway 192.168.1.254
dns-nameservers 192.168.1.254 8.8.8.8


# google DNS servers - worked but changed
# dns-nameservers 8.8.8.8 8.8.4.4 


#told unneccessary --- look into why and when
#wpa-ssid ATT3prj299
#wpa-psk b8bb7bcfe7e788d1feaa68e14a3f1730b966851052d0652ea7 ed186da92bb65e
```The highlighted part is wrong and must be removed. If you want to leave comments, they must be on their own new line. And, again, isn't wlp1s0 a wireless interface? Don't you want ethernet?```
# interfaces(5) file used by ifup(8) and ifdown(8)


#changes made 7/13/16 during forums chat


auto lo
iface lo inet loopback


auto enp0s25
iface enp0s25 inet static
address 192.168.1.110
netmask 255.255.255.0
gateway 192.168.1.254 8.8.8.8
```This should be:```
# interfaces(5) file used by ifup(8) and ifdown(8)


#changes made 7/13/16 during forums chat


auto lo
iface lo inet loopback


auto enp0s25
iface enp0s25 inet static
address 192.168.1.110
netmask 255.255.255.0
gateway 192.168.1.254 
dns-nameservers 192.168.1.254 8.8.8.8
```Please try again.

I will be away for a few hours.

---

### Post by Alcidious on 2016-07-19
@Chili555,

Thanks for the help, and sorry for the delay. I was working on everything when the forums got taken down.

I've managed to set up my network... at least my PC Towers, and my homemade file server. The LAN needs some tweaking, but it's doing what I need it to do. I decided to just ignore my laptop, since I rarely connect it via ethernet.

I did, however, isolate a particular issue on the PC Towers: The static IP's were receiving packets, but they would not connect to the internet. I realized my wireless connections, which are due to PCI-Express adapters in the mobo, were interfering somehow. My solution was to just shutdown my two PCs and remove the adapters. Now the static ip's work great!

What happens when a computer switches from a wired to a wireless connection? Can that same computer have a static ip when wired, yet have a dynamic ip when wirelessly connected? If so, do you just add lines for both connections in /etc/network/interfaces or other file?

If I don't see a response I will go ahead and mark the thread as solved.

Thanks a million!

---

### Post by chili555 on 2016-07-19
Network Manager is supposed to disallow two connections and give priority to the faster, more secure wired ethernet. Sadly, NM is imperfect but does quite well considering all that we ask of it.

Rather than remove the wireless cards, you could have blacklisted their drivers and had them available later if needed.

In any event, glad it's all working!

---

### Post by wildmanne39 on 2016-07-19
Please use code tags when posting code.
Thanks

---

