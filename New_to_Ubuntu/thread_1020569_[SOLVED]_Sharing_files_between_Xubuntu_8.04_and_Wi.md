---
title: "[SOLVED] Sharing files between Xubuntu 8.04 and Windows XP"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by valtemar on 2008-12-24
I have two computers, one with Xubuntu 8.04 Hardy Heron, the other with Windows XP. I am trying to get them "see" each other in the local network in order to **give Windows access to music files on Xubuntu hard drive**.

Both computers are connected to a Telewell ADSL modem via Ethernet cable and can access the internet. Windows XP has an F-Secure firewall.

I have installed Samba on Xubuntu and set a folder called **/home/username/Music** to be shared through Windows networks SMB. When I connect my Linux computer to the internet and type *ifconfig* in terminal, this is what I see:

```
eth0      Link encap:Ethernet  HWaddr 00:10:a7:1c:bb:19  
          inet6 addr: fe80::210:a7ff:fe1c:bb19/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:99558 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124893 errors:0 dropped:0 overruns:20 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29250566 (27.8 MB)  TX bytes:122136546 (116.4 MB)
          Interrupt:11 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:534 errors:0 dropped:0 overruns:0 frame:0
          TX packets:534 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:32696 (31.9 KB)  TX bytes:32696 (31.9 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:85.217.22.18  P-t-P:212.50.222.24  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:66288 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76039 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:17933784 (17.1 MB)  TX bytes:60747869 (57.9 MB)
```

When I type the IP address visible in the section "ppp0" (inet addr; it changes every time I connect) to the address bar in Windows XP I can see /home/username/Music being shared via the network. So far things look good.

The issue here is that **transferring files from the share to Windows hard drive is inhumanely slow**. 80 MB takes 50 minutes. Also, both computers must be connected to the internet to "talk". Disconnecting either of the two will also cancel file transfer.

So obviously something's not right. I have found many threads related to this topic on the web, but so far none of them has solved my problem. Please help.


And Merry Christmas, people.

---

### Post by ibuclaw on 2008-12-24
Have you ever considered getting an ADSL router to connect the two computers to their own private LAN?

Not sure on exact speeds that you'll get from implementing one (my ethernet router operates at 108mbps), but the link between your two computers will be **direct**, not "through the internet" as it currently looks like at the moment.

Regards
Iain

---

### Post by LowSky on 2008-12-24
you really need a router so the PC's can work better on a network

---

### Post by generic_idea_machine on 2008-12-24
Myself I would either:
[LIST]
[*]Option # 1 - Get a router. Hook up the two machines to the router and go from there.
[*]Option # 2  - Run a crossover cable between the two machines, and then map the samba mounts to the pertinent crossover cable interface
[/LIST]

Personally I have tried both these options. Data transmission rates over a cross-over cable are super fast (But then again that could be due to the fact that I've had a crappy netgear router for as long as I can remember and I was comparing the data transmission rates to that). 

Also if you are going to go with a router and hook up the machines as such + Plus all you are really trying to do is stream your music, then I would suggest you try a) gnump3d or b) [ampache]("http://ampache.org/")

---

### Post by mapes12 on 2008-12-24
This may help: [http://ubuntuforums.org/showthread.php?t=500734](http://ubuntuforums.org/showthread.php?t=500734)

Check your Telewell manual to see if it provides router services. If it doesn't then a cross over cable connection will do the trick (as previously posted).

To troubleshoot your network try this: [http://www.aboutdebian.com/network.htm](http://www.aboutdebian.com/network.htm)

---

### Post by gn2 on 2008-12-24
As well as PyNeighborhood option, there's the Network Browsing with Thunar link in my sig which might be useful.

---

### Post by valtemar on 2008-12-24
> **tinivole said:**
> Have you ever considered getting an ADSL router to connect the two computers to their own private LAN?

Not sure on exact speeds that you'll get from implementing one (my ethernet router operates at 108mbps), but the link between your two computers will be **direct**, not "through the internet" as it currently looks like at the moment.

Regards
Iain


Yes. I forgot to mention that my ADSL modem *is* also a router. What you have described in your post, connecting the two computers to their own private LAN, is exactly what I'm trying to do.

Your suggestion that at the moment the computers are linked somehow "through the internet" kind of makes sense to me, as it explains both the slow speed and why the transfer is canceled when I shut the internet connection.

So here's the question: **How do I get my Xubuntu 8.04 and Windows XP computers, neither of which is connected to the internet, to "talk" to each other in the local network?** Both of them are connected to the router. I already have Samba configured. What I need to know is how to access the Xubuntu machine through my LAN using the Windows machine.

I can't see my Xubuntu machine by browsing the network folders in Windows. When I type "\\the-name-of-my-xubuntu-computer" in Windows Explorer, it's not found. When I try to find out what is the IP of the Xubuntu box by typing the command *ifconfig*, this is what I get (when the internet connection is disconnected):

```
eth0      Link encap:Ethernet  HWaddr 00:10:a7:1c:bb:19  
          inet6 addr: fe80::210:a7ff:fe1c:bb19/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:99558 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124893 errors:0 dropped:0 overruns:20 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29250566 (27.8 MB)  TX bytes:122136546 (116.4 MB)
          Interrupt:11 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:534 errors:0 dropped:0 overruns:0 frame:0
          TX packets:534 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:32696 (31.9 KB)  TX bytes:32696 (31.9 KB)
```

Any help is welcome.

---

### Post by valtemar on 2008-12-24
**[COLOR="Red"]The problem is solved![/COLOR]**

I modified settings for my Xubuntu's Ethernet connection (labeled "eth0") in System > Network. Basically I disabled "roaming mode" (I don't have a clue what "roaming mode" is, but it appears I've used it since time immemorial) and switched to **automatic configuration (dhcp)**.

Now *ifconfig eth0* gives me this:

```
eth0      Link encap:Ethernet  HWaddr 00:10:a7:1c:bb:19  
          **inet addr:192.168.0.114  Bcast:255.255.255.255  Mask:255.255.255.0**
          inet6 addr: fe80::210:a7ff:fe1c:bb19/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:254819 errors:1 dropped:1 overruns:1 frame:0
          TX packets:361191 errors:0 dropped:0 overruns:20 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:63945037 (60.9 MB)  TX bytes:414236610 (395.0 MB)
          Interrupt:11 Base address:0xec00
```

So now my router (which also has a DHCP) gives me the IP address I was desperately looking for and I can "see" my Xubuntu box and the shared music folder in Windows. Also the transfer speed problem got fixed. So now everything works as it should.

Hope this helps those who are struggling with similar problems and come across this thread.

---

