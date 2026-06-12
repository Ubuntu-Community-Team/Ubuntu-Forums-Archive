---
title: "DHCP server"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by fmpfmpf on 2008-05-20
i am using Ubuntu 7.10 and i need to create a DHCP server to allow other comps to connect to my laptop (wireless LAN)
Does anyone know any good websites which can teach me how to create a DHCP server?
TQ

---

### Post by helgman on 2008-05-20
A good website? [http://www.google.com](http://www.google.com/search?hl=sv&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=FD6&q=ubuntu+dhcp+server&btnG=S%C3%B6k&meta=) might do the trick.

Regards,
Helgman

PS. I'd go for [this one](http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s04.html) or [this one](http://myy.helia.fi/~karte/ubuntu_dhcp.html) DS.

---

### Post by BlueSkyNIS on 2008-05-20
> A good website? [http://www.google.com](http://www.google.com) might do the trick.
lol helgman that was mean :)


Cheers

---

### Post by fmpfmpf on 2008-05-20
i followed the isntruction in this website
[http://myy.helia.fi/~karte/ubuntu_dhcp.html](http://myy.helia.fi/~karte/ubuntu_dhcp.html)
and this is what i got at the end

* Stopping DHCP server dhcpd3     [fail]
* Starting DHCP server dhcpd3     [fail]

pls help

tq

---

### Post by pricetech on 2008-05-20
[https://help.ubuntu.com/8.04/serverguide/C/dhcp.html](https://help.ubuntu.com/8.04/serverguide/C/dhcp.html)
from the Ubuntu documentation site.
[https://help.ubuntu.com/](https://help.ubuntu.com/)
Main page thereof.

Haven't done it myself, so I don't know if there are any "gotchas" or not.

Hope that helps .

---

### Post by helgman on 2008-05-20
> **BlueSkyNIS said:**
> lol helgman that was mean :)

That it is in the eye of the beholder, isn't it? ;-)

But to my defense, the postscript was there from the beginning and the Google-link actually points to the search result for "ubuntu dhcp server" and fmpfmpf wanted a good website and that's where I started my search for the answer ...

... but the postscript also held two other links that might be good reads but also might be viewed as mean in this context. So I removed them.

> **fmpfmpf said:**
> i followed the isntruction in this website
[http://myy.helia.fi/~karte/ubuntu_dhcp.html](http://myy.helia.fi/~karte/ubuntu_dhcp.html)
and this is what i got at the end

* Stopping DHCP server dhcpd3     [fail]
* Starting DHCP server dhcpd3     [fail]

When a server don't start it is usually something in the configuration that's not quite right. Try to find search your logs, they might hold a clue as to what is wrong.

If you don't find it there maybe you could post your configuration file and we can have a look at it ... (but start with the logs).

Regards,
Helgman

---

### Post by helgman on 2008-05-20
> **pricetech said:**
> [https://help.ubuntu.com/8.04/serverguide/C/dhcp.html](https://help.ubuntu.com/8.04/serverguide/C/dhcp.html)
from the Ubuntu documentation site.

To bad that one didn't turn up at the top of my search, that one has a rather clear example of a configuration file.

---

### Post by fmpfmpf on 2008-05-21
oops, i actually followed this website, not the other
[http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s04.html](http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s04.html)

where can i find the log?

thank you

---

### Post by helgman on 2008-05-21
There might be some information in your syslog, or there might be a specific log for the server (not sure). Make a search through /var/log ...

Also found this thread with a similar problem: [http://ubuntuforums.org/showthread.php?t=84207](http://ubuntuforums.org/showthread.php?t=84207)

The problem there was that the interface hosting the DHCP server was set to get it's IP via DHCP ...

Regards,
Helgman

---

### Post by fmpfmpf on 2008-05-21
i have a problem choosing which eth to use
My WLAN is eth2
and my 2 ethernet ports are eth0 and eth1
whcih eth should i use?

tq

---

### Post by helgman on 2008-05-21
You should use the interface that the clients will connect to.

Example: if eth0 is your external interface and eth1 is your internal interface where the clients connect then eth1 should be the interface.

If you want the service on the wireless then I guess that is your interface of choice.

Helgman

---

### Post by fmpfmpf on 2008-05-21
i am a bit confused.
this is the scenario
laptop A is connected to the internet through eth1 and it's WLAN is eth2
i want another laptop to receive the signal through wireless.

so i should put INTERFACES="eth2" in laptop A configuration

is this correct?

tq

---

### Post by helgman on 2008-05-21
My guess is that eth2 is the interface to use in that scenario, yes ...

---

### Post by ispyisail on 2008-05-21
This howto might help

[https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint](https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint)

internet<-->router(dhcp server)<-->(eth0)ubuntu(eth1)<-->other PC's

or for wireless
internet<-->router(dhcp server)<-->(eth0)ubuntu(ath0)<-->other PC's

eth0 goes to the internet
eth1 goes to local LAN
ath0 wireless LAN

---

### Post by fmpfmpf on 2008-05-21
referring tho this website
[http://ubuntuforums.org/showthread.php?t=74925&highlight=dhcp3-server](http://ubuntuforums.org/showthread.php?t=74925&highlight=dhcp3-server)

Step 2
Once there, go into the properties for the network card you will use for your internal/routed network

What does it mean by internal/routed network?
is it my Ethernet or WLAN?

tq

---

### Post by ispyisail on 2008-05-21
Have a look at the diagram in the access point howto

Is this the setup you are trying to achieve?

---

### Post by fmpfmpf on 2008-05-21
> **ispyisail said:**
> Have a look at the diagram in the access point howto

Is this the setup you are trying to achive?

i dont think so
all i want is a simple setup
2 laptops (A and B)
A is connected to the internet with an ethernet cable.
Now i want to make A a DHCP server to enable B to hook up with A through wireless

---

### Post by helgman on 2008-05-21
> **fmpfmpf said:**
> What does it mean by internal/routed network?

The internal/routed network is the network where your clients will be connecting.

Take a piece of paper and in the center of the paper make a rectangle. That is the computer with all the interfaces (call it router or what you will). On one side you make a cloud that you connect to the router, you call this cloud the Internet and the connection is (in your mind) connected to your external interface that connects to your external network (the Internet). On the other side of the router you make another could that you call LAN. That is also connected to the router and the network interface that is connected to the LAN is your internal interface connected to the internal network.

All clients that connect to your router to get Internet access should be on the internal network or LAN (Local Area Network).

Now, back on the paper, you print the names of interfaces that is connected to each of the clouds and that should give you an idea about what goes where. The DHCP service should be running on the interface connected to the internal network and that interface should have a static IP address.

Regards,
Helgman

PS It's always a good idea to draw a quick picture of the network just to visualize things DS

---

### Post by helgman on 2008-05-21
> **fmpfmpf said:**
> Now i want to make A a DHCP server to enable B to hook up with A through wireless

If A and B always stays the same you don't really need a DHCP server ... you could go static on both.


I did a setup like that yesterday: [http://ubuntuforums.org/showpost.php?p=5001190&postcount=11](http://ubuntuforums.org/showpost.php?p=5001190&postcount=11)

---

### Post by fmpfmpf on 2008-05-21
A and B is just for testing. More will come in later =)

[http://ubuntuforums.org/showthread.php?t=74925&highlight=dhcp3-server](http://ubuntuforums.org/showthread.php?t=74925&highlight=dhcp3-server)
at step 5, it says "check the box for "Enable DHCP for local network"
However, that part is always grey in my screen and i cannot check it

what can be the problem?
tq

---

### Post by ispyisail on 2008-05-21
Hi helgman

Had a look at your post

> I did a setup like that yesterday: [http://ubuntuforums.org/showpost.php...0&postcount=11](http://ubuntuforums.org/showpost.php...0&postcount=11)

I like it!

Thats the solution.

The only pitfalls will be finding the correct ports eth0 eth1 ath0 etc depends on the hardware and the cables plugged into the correct cards

But i guess thats were this post is heading

---

### Post by Archmage on 2008-05-21
Maybe this didn't help your or you are not wating this solution, but I got DHCP + Internet Conection Sharing + A Firewall with the program Firestarter.

---

### Post by helgman on 2008-05-21
> **fmpfmpf said:**
> at step 5, it says "check the box for "Enable DHCP for local network"
However, that part is always grey in my screen and i cannot check it

what can be the problem?

That might be a problem, maybe. I followed the guide and got the same problem. Now ... just finish the wizard and when Firestarter is running, go to *Edit -> Preferences -> Network settings* and you should find the box there ... just edit them as you please.

Also, have you verified that your DHCP server is working? Mine failed to start and a quick look in the syslog (tail /var/log/syslog) showed that it wasn't configured properly. I just added the subnet settings and up it went like a rocket. I haven't tried my setup (and I'm not going to) but it looks OK.

Regards,
Helgman

---

### Post by fmpfmpf on 2008-05-21
this is my current setup in Network settings

Internet connected network device : eth0

Local network connected evice: eth2

ok, i have checked the "Enable DHCP for the loacl network"

now there is another problem
When i click "start firewall", it says:
Failed to start the firewall
The devide eth2 is not ready.
Please check your network device settings and make sure your internet conenction is active.

What should i do from here?
i am sure my eth2 (WLAN) is functioning

tqtqtq

---

### Post by helgman on 2008-05-21
I think you should break things down and take them one at a time. I've never worked with Firestarter but this is what I would do:

1) Make sure that the interfaces on COMP A is up and running. For example, ping [www.google.com](www.google.com) (or 66.249.93.99) and give COMP B a static IP address that you try to ping from COMP A. Make sure that this works.

2) Run Firestarter and make sure that you set the correct external (eth0) and internal (eth2) interfaces.

3) Enable Internet sharing and make sure to set a default route on COMP B (*route add default <IP of COMP A>*). Try to ping [www.google.com](www.google.com) or 66.249.93.99 from COMP B.

4) If everything has worked up to this point try to enable the DHCP function and make sure that COMP B gets an address from the DHCP server.

This might look like doing everything over once more but it might help to pin down at where the problem is. 

Regards,
Helgman

---

### Post by fmpfmpf on 2008-05-21
i tried this
eth2 connect to internet....meaning laptop A is now online using wireless instead of wired ethernet.
When i run Firestarter, it now says eth0 is not functioning.

so i think the eth that is not online is always not functioning.

How can i fix this?

thank you

---

### Post by fmpfmpf on 2008-05-21
> **helgman said:**
> I think you should break things down and take them one at a time. I've never worked with Firestarter but this is what I would do:

1) Make sure that the interfaces on COMP A is up and running. For example, ping [www.google.com](www.google.com) (or 66.249.93.99) and give COMP B a static IP address that you try to ping from COMP A. Make sure that this works.

i tried the ping.

Comp A
--- 66.249.93.99 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2010ms

Comp B is fine
it shows the amount of bytes and time used.

is anything wrong with comp A?

tq

---

### Post by helgman on 2008-05-21
> **fmpfmpf said:**
> laptop A is connected to the internet through eth1 and it's WLAN is eth2

> **fmpfmpf said:**
> this is my current setup in Network settings

Internet connected network device : eth0

Local network connected evice: eth2

> **fmpfmpf said:**
> eth2 connect to internet....meaning laptop A is now online using wireless instead of wired ethernet.
When i run Firestarter, it now says eth0 is not functioning.

There are a lot of interfaces floating around here having connected to different networks in different posts. Once again ... make sure you have a clear picture of what goes where and then configure Firestarter based on that picture.

From the beginning eth1 was connected to the Internet and now it's eth2, the interface that earlier was to be the gateway for clients on the LAN (I will now use LAN instead of internal network so as not to add to the confusion at possible misinterpretation of it as Internet).

From what I've gathered from earlier posts you configuration should be:

Internet: eth1
LAN (inside): eth2

Is this corret?

Helgman

---

### Post by helgman on 2008-05-21
> **fmpfmpf said:**
> Comp A
--- 66.249.93.99 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2010ms

Comp B is fine
it shows the amount of bytes and time used.

Hrm ... so COMP B, that should connect through COMP A can ping Google but COMP A can't? Or COMP B can ping COMP A?

---

### Post by fmpfmpf on 2008-05-21
my configuration is only eth0 and eth2

eth0 receives the signal from internet
eth2 releases the signals for laptop B to grasp

---

### Post by fmpfmpf on 2008-05-21
> **helgman said:**
> Hrm ... so COMP B, that should connect through COMP A can ping Google but COMP A can't? Or COMP B can ping COMP A?

yes, comp B can ping google,, but not comp A

the 2 laptops have not been connected yet
so they cannot ping each other

---

### Post by helgman on 2008-05-21
OK ... so you want COMP A to work as a gateway/access point for wireless clients that roam around the place that is the home of COMP A. You have a wired connection (eth0) that leads you straight to the Internet and you have a wireless connection (eth2) that is going to be part of an Ad Hoc wireless LAN.

Question A: Is the above statement correct? If not, what is wrong?

Step 1: Make sure that COMP A can communicate with the Internet, if it can't, computers connecting through it should not be able to either.

How do you do this?

Well ... it all depends on your network setup. My guess is that eth0 uses DHCP for assigning IP address and then that is what should be used. If you are using Firestarter then make sure that the DHCP option is enabled. If you are using static IP make sure that you have the correct address, the correct default gateway settings and the correct DNS settings.

If you are unsure about the settings, open a terminal and run the following commands, posting the output here:
```
ifconfig eth0
cat /etc/resolv.conf
route -n
```

When all this is checked and you are sure it should be working. Try to ping Google again (from COMP A).

(The rest will follow when we know that this is working.)

Helgman

---

### Post by fmpfmpf on 2008-05-21
> **helgman said:**
> OK ... so you want COMP A to work as a gateway/access point for wireless clients that roam around the place that is the home of COMP A. You have a wired connection (eth0) that leads you straight to the Internet and you have a wireless connection (eth2) that is going to be part of an Ad Hoc wireless LAN.

very close. Only that it wont b a Ad Hoc, but a DHCP server.
i did succed in using the Ad Hoc method. Both comps can ping each other. The problem i have with Ad Hoc is, when either comp is restarted, the entire configuration is deleted and has to be reconfigured again to enable the 2 comps to interact with each other.


> **helgman said:**
> Step 1: Make sure that COMP A can communicate with the Internet, if it can't, computers connecting through it should not be able to either.

How do you do this?

Well ... it all depends on your network setup. My guess is that eth0 uses DHCP for assigning IP address and then that is what should be used. If you are using Firestarter then make sure that the DHCP option is enabled. If you are using static IP make sure that you have the correct address, the correct default gateway settings and the correct DNS settings.

If you are unsure about the settings, open a terminal and run the following commands, posting the output here:
```
ifconfig eth0
cat /etc/reslov.conf
route -n
```

eth0      Link encap:Ethernet  HWaddr 00:03:E1:90:0E:07  
          inet addr:172.23.0.68  Bcast:172.23.3.255  Mask:255.255.252.0
          inet6 addr: fe80::203:e1ff:fe90:e07/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2755 errors:0 dropped:0 overruns:0 frame:0
          TX packets:115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:286919 (280.1 KB)  TX bytes:16830 (16.4 KB)
          Interrupt:16 Base address:0x6000 


Kernel IP routing table
Destination        Gateway            Genmask            Flags    Metric    Ref      Use    Iface
172.23.0.0   0.0.0.0            255.255.252.0      U        0         0           0    eth0
169.254.0.0        0.0.0.0            255.255.0.0        U        1000      0           0    eth0
0.0.0.0            172.23.3.254       0.0.0.0            UG       0         0           0    eth0


> **helgman said:**
> When all this is checked and you are sure it should be working. Try to ping Google again (from COMP A).

currently, comp A is connected to the internet through ethernet and comp B through WLAN from another host.
comp B can ping google and comp A cannot.
i then tried disconnecting the ethernet wire from comp A and put it into comp B, so comp B is now online (wired)
i now try to ping google with comp B, and it failed.

so i think i cannot ping google using wired connection.

---

### Post by helgman on 2008-05-21
> **fmpfmpf said:**
> currently, comp A is connected to the internet through ethernet and comp B through WLAN from another host.
comp B can ping google and comp A cannot.
i then tried disconnecting the ethernet wire from comp A and put it into comp B, so comp B is now online (wired)
i now try to ping google with comp B, and it failed.

so i think i cannot ping google using wired connection.

What is the output of **nslookup [www.google.com](www.google.com)**?

Can you **ping 66.249.93.147**?

What happens if you try a **tracepath 66.249.93.147**?

Regards,
Helgman

---

### Post by fmpfmpf on 2008-05-21
nslookup [www.google.com](www.google.com)
comp A
*** Can't find [www.google.com:](www.google.com:) No answer

comp B
(successful)


ping doesnt work on A

tracepath works on both A n B

---

### Post by helgman on 2008-05-21
> **fmpfmpf said:**
> nslookup [www.google.com](www.google.com)
comp A
*** Can't find [www.google.com:](www.google.com:) No answer

My guess is a) you don't have a connection or b) you don't have a DNS server configured. I noticed that you didn't give any output from cat /etc/resolv.conf above, that's the file that specifies your DNS servers.

> comp B
(successful)

Since this one is connected via some other connection we can leave it for now, but ...
> ping doesnt work on A

tracepath works on both A n B

... is exactly what we are after. Would you please post the output of the tracepath on COMP A. The reason for this is that it will tell us where the ping command fails (tracepath is just a series of pings sent to every "hop" along the path to the destination). So if tracepath "works", ping works ...

Regards,
Helgman

---

### Post by fmpfmpf on 2008-05-21
oh....it is cat /etc/resolv.conf
you wrote cat /etc/reslov.conf

yes, i did get an output with cat /etc/resolv.conf

#generated by NetworkManager, do not edit!

search xxxx.xxxx.com

nameserver 204.55.144.99
nameserver 204.55.144.107

---

### Post by helgman on 2008-05-21
> **fmpfmpf said:**
> oh....it is cat /etc/resolv.conf
you wrote cat /etc/reslov.conf

Ah ... my bad ... so you tried to cat Reslov? That would be the English version of the Swedish community of Reslöv.

(I'm gonna edit the original post if someone uses is in the future.)

Then we know that you have some kind of DNS settings, that's good.

Thank you,
Helgman

---

### Post by fmpfmpf on 2008-05-21
tracepath command


Comp A
root@fmp-desktop:~# tracepath 66.249.93.147
 1:  fmp-desktop.xxx.xxxx.com (172.23.0.68)             0.288ms pmtu 1500
 1:  172.23.3.253 (172.23.3.253)                            1.016ms 
 2:  172.23.101.65 (172.23.101.65)                          2.023ms 
 3:  192.168.52.166 (192.168.52.166)                        0.828ms 
 4:  172.23.101.26 (172.23.101.26)                          0.566ms 
 5:  192.43.59.50 (192.43.59.50)                          asymm  6   3.746ms 
 6:  


Comp B
root@layx:~# tracepath 66.249.93.147
 1:  wlayx.lan (192.168.16.127)                          0.190ms pmtu 1500
 1:  192.168.16.57 (192.168.16.57)                          2.836ms
 2:  192.168.0.254 (192.168.0.254)                          8.023ms
 3:  no reply
 4:  no reply
 5:  no reply
 6:  no reply

---

### Post by helgman on 2008-05-21
> **fmpfmpf said:**
> root@fmp-desktop:~# tracepath 66.249.93.147
 1:  fmp-desktop.xxx.xxxx.com (172.23.0.68)             0.288ms pmtu 1500
 1:  172.23.3.253 (172.23.3.253)                            1.016ms 
 2:  172.23.101.65 (172.23.101.65)                          2.023ms 
 3:  192.168.52.166 (192.168.52.166)                        0.828ms 
 4:  172.23.101.26 (172.23.101.26)                          0.566ms 
 5:  192.43.59.50 (192.43.59.50)                          asymm  6   3.746ms 
 6:  

It just keeps giving you blanks after this?

---

### Post by helgman on 2008-05-21
Well ... we don't know if COMP A is having a problem when it comes to connecting to the Internet or if there is something else. I can't reach the DNS servers but there might be a lot of reasons for that.

Anyway ... there are enough networks outside COMP A to verify that things are working here. So ...

Step 2: Set up the wireless Ad Hoc network between COMP A and COMP B. As soon as the network is up, make sure that COMP A can ping COMP B (or the other way around) using the IP address of the wireless interfaces that are connected to the Ad Hoc network.

Tell me when you are there ... ;-)

---

### Post by fmpfmpf on 2008-05-21
root@fmp-desktop:~# tracepath 66.249.93.147
 1:  fmp-desktop.xxx.xxxx.com (172.23.0.68)             0.299ms pmtu 1500
 1:  172.23.3.253 (172.23.3.253)                            1.003ms 
 2:  172.23.101.65 (172.23.101.65)                          0.630ms 
 3:  192.168.52.166 (192.168.52.166)                        0.801ms 
 4:  172.23.101.26 (172.23.101.26)                          0.584ms 
 5:  192.43.59.50 (192.43.59.50)                          asymm  6   3.714ms 
 6:  192.43.59.46 (192.43.59.46)                          asymm 14  91.690ms 
 7:  192.43.59.61 (192.43.59.61)                          asymm 14 131.574ms 
 8:  192.168.41.241 (192.168.41.241)                      asymm 14 131.445ms 
 9:  no reply
10:  no reply
11:  no reply

---

### Post by fmpfmpf on 2008-05-21
Ad-Hoc established.

Just in case, i will write down the codes used to make the Ad-Hoc

Laptop A
iwconfig eth2 mode ad-hoc
iwconfig eth2 essid "ABC"
iwconfig eth2 channel 6
ifconfig 10.10.10.1

Laptop B
ifconfig 10.10.10.2

(laptop B then connects to ABC)

Laptop A
ping 10.10.10.2

Laptop B
ping 10.10.10.1

ping successful on both laptops

---

### Post by helgman on 2008-05-21
Good.

Step 3: (Since you are using Firestarter we'll try it that way.) Enable Internet Sharing in Firestarter.

Step 4: Add a default route on COMP B via COMP A.
```
route add default gw 10.10.10.1
```

Step 5: Use COMP B and try to ping 192.168.52.166.

Does it work?

---

### Post by eurgain on 2008-05-21
> **fmpfmpf said:**
> i am using Ubuntu 7.10 and i need to create a DHCP server to allow other comps to connect to my laptop (wireless LAN)
Does anyone know any good websites which can teach me how to create a DHCP server?
TQ

I find that DNSMasq makes an excellent DHCP server for a LAN.  It is much easier to set up than a traditional DHCP server, and from reading your comments, I think that it is better suited to what you want to do.

It can also act as a name server, so that the hostnames of all local machines on the lan are resolved by it to the addresses it assigns using DHCP, and it forwards all non-local name requests to the DNS server address received from the ISP.

It is available in the Ubuntu repos, and there is lots of documentation at [http://www.thekelleys.org.uk/dnsmasq/doc.html](http://www.thekelleys.org.uk/dnsmasq/doc.html)

A

---

### Post by fmpfmpf on 2008-05-21
My Firestarted suddenly start running, is it because of the "route add default gw 10.10.10.1" command?

Step 4 failed
it says:-
connect: Network is unreachable

---

### Post by fmpfmpf on 2008-05-21
> **eurgain said:**
> I find that DNSMasq makes an excellent DHCP server for a LAN.  It is much easier to set up than a traditional DHCP server, and from reading your comments, I think that it is better suited to what you want to do.

It can also act as a name server, so that the hostnames of all local machines on the lan are resolved by it to the addresses it assigns using DHCP, and it forwards all non-local name requests to the DNS server address received from the ISP.

It is available in the Ubuntu repos, and there is lots of documentation at [http://www.thekelleys.org.uk/dnsmasq/doc.html](http://www.thekelleys.org.uk/dnsmasq/doc.html)

A

it works for WLAN too?
you said only LAN

---

### Post by helgman on 2008-05-21
> **fmpfmpf said:**
> Step 4 failed
it says:-
connect: Network is unreachable

(Changed the last Step 4 to Step 5.)

The route add command ... on what computer did you commit that one? (It should be on COMP B, sorry if that is unclear.)

Are you able to go through Step 5 on COMP A?

---

### Post by fmpfmpf on 2008-05-21
Are you able to go through Step 5 on COMP A? 
Yes :D
packets are being transmitted

---

### Post by helgman on 2008-05-21
Good.

Question B: Did you add the route on COMP B?

Question C: Can COMP B ping COMP A?

Question D: Can COMP B ping 192.168.52.166?

---

### Post by fmpfmpf on 2008-05-21
> **helgman said:**
> Question B: Did you add the route on COMP B?
yes

> **helgman said:**
> Question C: Can COMP B ping COMP A?
yes
command used: ping 10.10.10.1

> **helgman said:**
> Question D: Can COMP B ping 192.168.52.166?
no

---

### Post by helgman on 2008-05-21
This is where my lack of experience when it comes to Firestarter comes into play.

Try tracepath 192.168.52.166 on COMP B and post the output here.

Also try cat /proc/sys/net/ipv4/ip_forward on COMP A and please tell us the lucky number (we all hope it's '1').

---

### Post by fmpfmpf on 2008-05-21
> **helgman said:**
> Try tracepath 192.168.52.166 on COMP B and post the output here.
1: layx.local (10.10.10.2)       0.192ms pmtu 1500
1: no reply
2: no reply
3: no reply
(and so on)

> **helgman said:**
> Also try cat /proc/sys/net/ipv4/ip_forward on COMP A and please tell us the lucky number (we all hope it's '1').
it is 0 :(

---

### Post by helgman on 2008-05-21
OK ... to errors that don't make a right here.

> **fmpfmpf said:**
> 1: layx.local (10.10.10.2)       0.192ms pmtu 1500
1: no reply

It doesn't head for COMP A (or COMP A is not responding). Please post the output of *route -n* on COMP B.

> it is 0 :(

And that tells us that COMP A is not forwarding. Have you enabled sharing in Firestarter (*Preferences -> Network Settings*)? And while you are there, make sure that *Internet connected network device* and *Local network connected device* are correct.

I'm gonna set it up for me just to test it at my end ... but please post the output of the route command and make sure that you have sharing enabled.

---

### Post by fmpfmpf on 2008-05-21
> It doesn't head for COMP A (or COMP A is not responding). Please post the output of *route -n* on COMP B.
Kernel IP routing table
Destination   Gateway   Genmask   Flags   Metric   Ref      Use   Iface
10.0.0.0   0.0.0.0      255.0.0.0   U   0   0      0   eth1
0.0.0.0    10.10.10.1   0.0.0.0     UG  0   0      0   eth1

> And that tells us that COMP A is not forwarding. Have you enabled sharing in Firestarter (*Preferences -> Network Settings*)? And while you are there, make sure that *Internet connected network device* and *Local network connected device* are correct.

*Internet connected network device*: eth0
*Local network connected device*: eth2
so i guess it is correct

yes, both boxes have been checked.

When i on Firestarter, i get this message:-
Failed to start the firewall.
An unknown error has occured.
Please check your network device settings and make sure your internet connection is active.

Howver, my Firestarter is active

---

### Post by helgman on 2008-05-21
> **fmpfmpf said:**
> When i on Firestarter, i get this message:-
Failed to start the firewall.
An unknown error has occured.
Please check your network device settings and make sure your internet connection is active.

I get the same error when I try to enable DHCP on the LAN when I don't have the DHCP server installed or configured. Make sure that the "Enable DHCP for the local network" check-box is unchecked.

---

### Post by fmpfmpf on 2008-05-21
ok, done, what should i do next?

cat /proc/sys/net/ipv4/ip_forward now gives a "1"

---

### Post by helgman on 2008-05-21
Try ping and tracepath to 192.168.52.166 from COMP B.

---

### Post by fmpfmpf on 2008-05-21
ping
packets are being transferred

tracepath
1: layx.local (10.0.0.2)                 0.205ms pmtu 1500
1: 10.10.10.1 (10.10.10.1)               10.117ms
2: 172.23.3.253 (172.23.3.253)           8.877ms
3: 172.23.101.65 (172.23.101.65)         7.626ms
4: 192.168.52.166 (192.168.52.166)       160.588ms reached
   Resume: pmtu 1500 hops 4 back 4

---

### Post by helgman on 2008-05-21
OK ... so far so good.

The problem now is the DHCP server. You need to get the configuration right in order to make it work through Firestarter.

Question A: Did you do the symbolic-link from dhcp3-server to dhcpd as suggested in the guide?

Hint: ls /etc/init.d/dhcp* should show two files dhcpd and dhcp3-server.

Question B: Can you get your DHCP runner via the init script?

Hint: /etc/init.d/dhcp3-server start

If the answer to Question A is 'NO', please create the link *ln -s /etc/init.d/dhcp3-server /etc/init.d/dhcpd*.

If the answer to Question B is 'NO', please post any output and also post the output of *tail /var/log/syslog*.

Helgman

---

### Post by harrybazeegar on 2008-05-21
[http://sourceforge.net/project/showfiles.php?group_id=132995](http://sourceforge.net/project/showfiles.php?group_id=132995)

try this. DHCP and DNS server

---

### Post by fmpfmpf on 2008-05-21
> Question A: Did you do the symbolic-link from dhcp3-server to dhcpd as suggested in the guide?

Hint: ls /etc/init.d/dhcp* should show two files dhcpd and dhcp3-server.

yes, those 2 files are shown

> Question B: Can you get your DHCP runner via the init script?

Hint: /etc/init.d/dhcp3-server start

No

output of *tail /var/log/syslog*:-

root@fmp-desktop:~# /etc/init.d/dhcp3-server start
 * Starting DHCP server dhcpd3                                           [fail] 
root@fmp-desktop:~# tail /var/log/syslog May 21 15:00:39 fmp-desktop dhcpd: Wrote 0 leases to leases file.
May 21 15:00:39 fmp-desktop dhcpd: 
May 21 15:00:39 fmp-desktop dhcpd: No subnet declaration for eth2 (10.10.10.1).
May 21 15:00:39 fmp-desktop dhcpd: ** Ignoring requests on eth2.  If this is not what
May 21 15:00:39 fmp-desktop dhcpd:    you want, please write a subnet declaration
May 21 15:00:39 fmp-desktop dhcpd:    in your dhcpd.conf file for the network segment
May 21 15:00:39 fmp-desktop dhcpd:    to which interface eth2 is attached. **
May 21 15:00:39 fmp-desktop dhcpd: 
May 21 15:00:39 fmp-desktop dhcpd: 
May 21 15:00:39 fmp-desktop dhcpd: Not configured to listen on any interfaces!

---

### Post by helgman on 2008-05-21
> **fmpfmpf said:**
> May 21 15:00:39 fmp-desktop dhcpd: No subnet declaration for eth2 (10.10.10.1).

That is the answer to your problem! You need some sort of subnet statement in your server configuration. Now ... if I remember correctly the file is found in /etc/dhcp3 and is named dhcpd.conf.

You need a to make a subnet for it to lease addresses from, something like this:
```
subnet 10.0.0.0 netmask 255.0.0.0 {
  range 10.10.10.25 10.10.10.100;
  option domain-name-servers 204.55.144.99, 204.55.144.107;
  option routers 10.10.10.1;
}
```

So just squeeze that into your /etc/dhcp3/dhcpd.conf and then try to start the DHCP server again.

*fingers crossed*

---

### Post by fmpfmpf on 2008-05-21
almost there....but

dhcpd self-test failed. Please fix the config file.
The error was: 
/etc/dhcp3/dhcpd.conf line 117: semicolon expected.
  option domain-name-servers nameserver 204.


line 117 is:-
option domain-name-servers nameserver 204.55.144.99, 204.55.144.107;

where should i put the semicolon?

tq

---

### Post by fmpfmpf on 2008-05-21
```
subnet 10.0.0.0 netmask 255.0.0.0 {
  range 10.10.10.25 10.10.10.100;
  option domain-name-servers nameserver 204.55.144.99, 204.55.144.107;
  option routers 10.10.10.1;
}
```

i wrote this code at the bottom of the txt file
is this correct?

---

### Post by helgman on 2008-05-21
> **fmpfmpf said:**
> i wrote this code at the bottom of the txt file
is this correct?

No but it's my mistake, the line should be:
```
option domain-name-servers 204.55.144.99, 204.55.144.107;
```

Let's call it a copy-paste accident. ;-)

---

### Post by fmpfmpf on 2008-05-21
YEESSSSSSS!!!!!!!!! IT WORKS!!!

* Starting DHCP server dhcpd3

So....if i would turn off both comps, would the server start immediately?
both comps will link immediately?

TQTQTQTQ

---

### Post by helgman on 2008-05-21
> **fmpfmpf said:**
> YEESSSSSSS!!!!!!!!! IT WORKS!!!

Great!

> So....if i would turn off both comps, would the server start immediately?
both comps will link immediately?

Impossible to answer ... ;-)

The DHCP server should start immediately.

You need to set the IP address on eth2 (COMP A) static so that it always stays the same. You should also make sure that the wireless goes up and has the same settings every time.

As for COMP B, all you should have to worry about is the wireless. It should now be served the IP address from COMP A. To test this, try to run dhclient on the wireless interface on COMP B.

Do you get an OFFER?

Helgman

---

### Post by fmpfmpf on 2008-05-21
> You need to set the IP address on eth2 (COMP A) static so that it always stays the same. You should also make sure that the wireless goes up and has the same settings every time.

How do i set this?

> As for COMP B, all you should have to worry about is the wireless. It should now be served the IP address from COMP A. To test this, try to run dhclient on the wireless interface on COMP B.

Do you get an OFFER?

This is what i got:-
i think there is an offer

Internet Systems Consortium DHCP Client v3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:17:a4:d8:18:7b
Sending on   LPF/eth0/00:17:a4:d8:18:7b
Listening on LPF/eth1/00:19:d2:62:2b:d5
Sending on   LPF/eth1/00:19:d2:62:2b:d5
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 10.10.10.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 10.10.10.1
bound to 10.10.10.100 -- renewal in 275 seconds.

---

### Post by helgman on 2008-05-21
> **fmpfmpf said:**
> How do i set this?

I'm not friend with all the ins and outs of the Network Manger (see a pattern?) but ... 

For a simple static IP guide you can use [https://help.ubuntu.com/8.04/internet/C/internet-basic-procedure.html](https://help.ubuntu.com/8.04/internet/C/internet-basic-procedure.html). Other documentation states that "Currently Network Manager does not support static address settings and Network-Admin does not support ad hoc networks" ([source](https://help.ubuntu.com/community/WifiDocs/Adhoc)) but they also propose a fix.

For you, according to the above document, it would look something like this (on COMP A):
```
auto eth2
iface eth2 inet static
wireless-mode ad-hoc
wireless-channel 4
wireless-essid 'name'
address 10.10.10.1
netmask 255.0.0.0
```

I'm not sure it will work but it could be worth a try. For COMP B I'm not sure if it will work or if you will have to tweak it a bit. Since you are using DHCP all you need is the connection to the network.

> This is what i got:-
i think there is an offer

Yepp ... it's an OFFER. Great!

---

### Post by fmpfmpf on 2008-05-21
where am i suppose to write those codes?

so...comp B is now connected to comp A, but comp B cannot surf the internet. is this suppose to happen?

tq

---

### Post by helgman on 2008-05-21
> **fmpfmpf said:**
> so...comp B is now connected to comp A, but comp B cannot surf the internet. is this suppose to happen?

From what we've seen so far ... COMP A can't surf the Internet either, isn't that so?

The tracepath shows us that your packages get lost somewhere further out in the network so you'll have to talk to whom ever is in charge of the network to see what is going on. From the tracepath tests we could see that packages would go from COMP B through COMP A to destinations on the Internet side of COMP A. So COMP A is good to go as far as that's concerned. Just make sure that all DNS settings are OK and so on and then you should be just as fine as soon as COMP A can reach the Net.

Regards,
Helgman

---

### Post by helgman on 2008-05-21
> **fmpfmpf said:**
> where am i suppose to write those codes?

I missed that one.

/etc/network/interfaces

---

### Post by fmpfmpf on 2008-05-21
> **helgman said:**
> From what we've seen so far ... COMP A can't surf the Internet either, isn't that so?

The tracepath shows us that your packages get lost somewhere further out in the network so you'll have to talk to whom ever is in charge of the network to see what is going on. From the tracepath tests we could see that packages would go from COMP B through COMP A to destinations on the Internet side of COMP A. So COMP A is good to go as far as that's concerned. Just make sure that all DNS settings are OK and so on and then you should be just as fine as soon as COMP A can reach the Net.

Regards,
Helgman

comp A can surf the net using a proxy connection

---

### Post by helgman on 2008-05-21
> **fmpfmpf said:**
> comp A can surf the net using a proxy connection

Ah ...

OK ... sweet ... or not.

I have to run but you should research the Proxy thing then since that is what's keeping you from surfing the Net, as simple as that. I don't know how you serve proxy settings via the DHCP or how you set them in Ubuntu but please let me know your findings if you get it up and running, I'll be back in some 15 hours ... ;-)

Regards,
Helgman

---

### Post by fmpfmpf on 2008-05-21
ok, no problem
i will do some research on the proxy

i have to get going too and will be back only on Friday
i will be away tmrw.

thanks a lot for all your help:):)
really appreciate it

---

### Post by fmpfmpf on 2008-05-23
i am having trouble getting proper search results for DHCP + proxy
i will post a new thread in this forum

---

