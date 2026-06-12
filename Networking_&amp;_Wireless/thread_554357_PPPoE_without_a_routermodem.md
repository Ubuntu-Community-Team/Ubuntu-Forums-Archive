---
title: "PPPoE without a router/modem?"
date: 2007-09-18
forum: Networking &amp; Wireless
---

### Post by nobodie on 2007-09-18
I hate to make a new post but this one has me totally flummoxed. 
I'm here in China, and my apartment has what appears to be a PPPoE VPN setup that, according to the management, can only be accessed with Windoze. Needless to say I'm not going for it.

Now, the way I understand PPPoE is that you just run a modem/router to connect to the server and with proper config you are good to go. Seems simple to me, but this is China. 

What they appear to use, however, is an unsigned Windoze script that creates a virtual router/modem (or maybe reconfigs the winmodem, I really don't know) and then use this script to connect to their VPN. This would be cute if it worked of course, but naturally it doesn't for me, or for Linux, or even for the Windoze partition on my daughter's computer. The damn thing ate Windoze (well, actually it rewrote the config.msi file into Chinese which.... well it wasn't pretty and we don't have Windoze any more)

So, what the heck to do about this mess. The "IT specialist" is completely clueless (he told my daughter that her Wacom graphics pad was broken because the mouse didn't work on the table top, this was after a demo of the mouse and stylus-- he'd never seen a stylus before) He is able to give me a username and password and that is about all. 

I have installed rp-pppoe-3.8 and confed it, i have ethernet to my computer and run that connection through a small hub. The IT specialist connected the ethernet cable from the VPN into the hub and installed the two programs on the windoze partition (Jeez what a mess that was, my firewall went ape, my antivirus was totally confused as well and everytime the computer started up it had to reinstall the "new hardware" which apparently was this script. Then it started to blue screen constantly) 

So, is there a software equivalent to the windoze script, one that I assume actually works since it is FOSS. Or if not can I get a recommend for a router/Modem that might work here and be available here. Finally, a really complete run through of how to get it installed with all the possible things to cover screwups, because this system is screwed. 

Did I mention that Samba has connected me to about twenty computers in my "workgroup" and another 5 or 6 in "mshome" I have no idea who they are.

so I am in a network, which normally, or at least in my limited experience, would put me on line. But no. 

Oh technical stuff: Ubuntu, 7.04, Kernal 2.6.xx (up to date in July when we moved here) Intel P4 on one and C2duallie on the other, ethernet on the MB, the whole system was up and running in July (with a router that I left behind) no problems, but that was in Thailand. This is way different on the surface anyway.

I will check back as soon as I can, but a super typhoon is about to hit so it might be a day or so.

Thanks.

---

### Post by noob12 on 2007-09-19
OK.  So I have no clue about how you need to proceed, but when you're saying VPN, I think you mean just a private LAN for your building?  It sounds to me like you are already connected to  the local net and you probably just need to know the address of the gateway router to get onto the net at large.

If you can get friendly enough with one of the other tenants to see the output of **ipconfig /all** and **route print** from one of those windows boxes, that might give you enough to get online.

---

### Post by nobodie on 2007-09-19
I think I know where to input that, and I definitely already know an address or two actually, but they seem to change with every new login. I'm at the office right now so I will check this later and reply more when I have done this on the box

but thanks

---

### Post by nobodie on 2007-09-20
Oh dear. Here is what the situation looks like now. After restart this morning the pppoe-start returns a failure to connect. The reason is that the address of the router has changed I think. Checking the network admins program shows that pppoe is not running, even after reconfig. I found a file that shows the address which I input yesterday, but pinging that returns nothing, while yesterday it did return a reply. Still it didn't get me on line yesterday. 

I think you are right that there must be a router for the building or something like that, but are they using a dynamic process to change the address? that really sounds crazy to me, but this is not even close to my comfort area. tell me more!!!

thanks

---

### Post by noob12 on 2007-09-20
I don't know anything about your specific situation, but certainly getting on the local net is going to be prerequisite to getting outside.  I'm just hoping for your sake that once you do that, then there'll be a stable gateway router that will get you out the door.  I don't know that for sure, but it seems overly complicated to do something dynamic within the building.  Not out of the realm of possibility, but I can see your already somewhere near the Twilight Zone.

Added:

Once you're connected, look at your address, mask and routes using **ifconfig -a** and **route -n**.  You may be able to guess the outer gateway router by applying the following convention: typically the router is going to be at either the lowest address or  highest - 1 (highest non-broadcast) address on the subnet.  But you may be in a place where such conventions aren't used.

---

### Post by nobodie on 2007-09-21
SNAFU time:
OK, the daughter's box has started to crash and hang, in a big way. So... after she went to bed I loaded RP-pppoe 3.8 into my computer to work on this there. HMMMMM. Big difference. I used the gui but also cross checked to the conf files and everything was smooth as silk.

OK, today, while her box is hanging I manage to stop and restart my box while sniffing with hers. It says (it being pppoe-sniff) that I am connected to a standard PPPoE network and that everything is hunky dory. But it doesn't return any of the crucial DNS addresses for the server/router or whatever I need to connect to to get back on line. so while i might be hunky dory i'm not on the internet. 

I thought it was supposed to do that. But then again, I am an idiot as well.

So, tonight I carried my daughter's box to my office on the 5th floor of the teaching building here at the uni (elevators??? we ain't got no stinkin' elevators!!!) and started it up here. whoa, not an easy startup either. I had to return to my original kernal from the 7.04 install disc to be able to start it, even in recovery mode. it hung on everything else. 

What the heck is going on??????? I am baffled. 

right now I am running apt-get update, but it has already hung once on that. Coulkd this be hardware from teh trip here in a container from Thailand?? It certainly seems to reek of hardware considering all the various stuff that is happening. But which hardware? i will immediately check for the backup dates on the HDD of course, but could it be something else? HELP

and thanks as always

---

### Post by nobodie on 2007-09-21
Oh sorry, I got off topic a little: i did run ifconfig and route on my computer once it was set up. They returned 5 or 6 different IP addresses. I tried all of them: first I pinged them (all returned good) and then plugged them in to the Gui boxes for specific DNS servers and then stopped/started the interface (probably unnecessary I know) and checked for google.com. nothing. I also traced them and they sem to be only one step away from my box, or else they are my box, i'm a littlle unclear about that output (from network tools in the admins tab)

This is why I said up above that I still wasn't on line. It was after this also that I sniffed the connection. Now I am not sure that, since both my boxes go to the same hub in my apartment (even though I have two accounts for the pppoe ) whether to trust the sniff. So, that is the more correct answer to the main thrust of this thread. My apologies for getting off a bit but I am really getting tripped about this.

---

### Post by noob12 on 2007-09-21
Your router is not necessarily going to be a DNS proxy; don't count on that.  You can't necessarily set your router's address as a DNS server address.  

You need to know a router that joins the internal building net and the Internet at large, assuming the building is actually connected to the Internet.

Are you getting your address and routes automatically via DHCP?  or are you setting them manually?   Do you get DNS servers assigned by the DHCP as well?

Check these things
```

ifconfig -a

route -n

cat /etc/resolv.conf

```

Check that the ifconfig shows an IPV4 (x.y.z.w format) address assigned to the interface.  If not, you have a problem and won't get further.

Check that you have a row in the **route -n output** that says UG in the fourth column and 0.0.0.0 in the first column.  If so, the second column shows your default gateway, your gateway to the world.  If you don't have such a row, your DHCP did not tell you a default gateway and you will need to find that out or you will not be able to get out.

If you have that row, try pinging this OpenDNS server to see if you can get there: 
```

ping -c 4 208.67.222.222

```
If you get responses that is good.

Based on what you tell me from the above I can tell you how close you are to getting to the net at large.  If you get all the way through the ping successfully, you are very close and I can tell you how to setup the DNS server addresses to work.

---

### Post by fouadk on 2007-09-22
my friend "nobodie" i have the same situation that u have

try the following 

i use roaring penguin

edit /etc/ppp/pppoe.conf 

find DNSTYPE put it to SERVER so in /etc/ppp/pppoe.conf find the DNSTYPE and set it to DNSTYPE = SERVER



hope it works....

---

### Post by nobodie on 2007-09-25
hey noob, here is complete output from the various commands. (I finally got it together to carry my flashdrive back and forth and , you know, like be helpful thoughtful and all that

jim@dhcppc1:~$ gksudo ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:1A:92:04:B4:E0   
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::21a:92ff:fe04:b4e0/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:101618 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:93648 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:6392762 (6.0 MiB)  TX bytes:5671563 (5.4 MiB) 
          Interrupt:17 Base address:0x2000 
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:5204 (5.0 KiB)  TX bytes:5204 (5.0 KiB) 
 
ppp0      Link encap:Point-to-Point Protocol   
          inet addr:172.17.7.178  P-t-P:172.16.18.200  Mask:255.255.255.255 
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1 
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1065 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:3 
          RX bytes:54 (54.0 b)  TX bytes:69591 (67.9 KiB) 
 
ppp1      Link encap:Point-to-Point Protocol   
          inet addr:172.17.4.2  P-t-P:172.16.18.200  Mask:255.255.255.255 
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1 
          RX packets:92124 errors:92131 dropped:0 overruns:0 frame:0 
          TX packets:92150 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:3 
          RX bytes:3500628 (3.3 MiB)  TX bytes:369656 (360.9 KiB) 


 
jim@dhcppc1:~$ route -n 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
172.16.18.200   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0 
172.16.18.200   0.0.0.0         255.255.255.255 UH    0      0        0 ppp1 
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0 
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0 
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp1 
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0 


jim@dhcppc1:~$ cat /etc/resolv.conf 
nameserver 172.17.2.157 
nameserver 172.17.4.28 

********************************************************************************
Seeing the output from route -n lacked a UG flagged line I went to netadmin and changed back to dchp from static addresses. The DHCP messes up my nfs setup, but i can deal with that later. I route-n again and get the following
*********************************************************************************

jim@dhcppc1:~$ route -n 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
172.16.18.200   0.0.0.0         255.255.255.255 UH    0      0        0 ppp1 
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0 
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0 
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0 


jim@dhcppc1:~$ ping -c 4 208.67.222.222 
PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data. 
 
--- 208.67.222.222 ping statistics --- 
4 packets transmitted, 0 received, 100% packet loss, time 3017ms 


 looks like Abiword messed up the format a little, but I think you can puzzle it out. I hope that this tells you something, I feel like we are getting somewhere now, i hope we are anyway.

thanks

---

### Post by nobodie on 2007-09-26
ok, i have been a busy boy, but i haven't a clue how i have done all this really, divine intervention mostly i think. 

attached is the full output of ifconfig (2 times) route and cat of the resolv.conf file both two times.

here is the short version.: last night I restarted and reloaded roaring penguin. After some initial problems (my daughter had turned off the lan hub and then my box had a massive brain fart and refused to even load the BIOS) everything started up and i had not just pppoe but could ping out and get return. 

But still no internet, of course.

i tried everything i could think of (ok, that wasn't much-- see the attachment) and gave up and went to bed leaving everything on and running. 

this morning the eth0 addresses had changed as well as the nameserver addresses and i had no ping return. 

so, look over the attachment please and see what you think is up. It is very close to being there.

BTW: i have set eth0 to dhcp. i have set the dns in roaring penguin to "server". i have set ppp to asynchronous, also in RP. these things don't really show in the output given. all the mtu and other stuff looks right. i think it is definitely a dns issue of some kind. 

thanks folks

---

### Post by nobodie on 2007-09-30
still a ping but no internet, is anybody out there?

---

