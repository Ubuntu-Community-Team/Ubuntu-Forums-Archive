---
title: "MUCH slower internet connection on Ubuntu then Windows"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by aireq on 2009-01-16
My internet has been reliably for the past week or so. .. which I just realized is also about as long as I've been using Ubuntu. I've tested my connection on speakeasy's site and speedtest.net and I get around 3 mbps down and 9mbps UP (no I do not have that backwards. I should be getting at least 6 down. I've been on the phone with tech support and they make me jump through the regular hoops and reseting the modem, reset computer, clear cache etc etc.. etc.. but then my cell dropped the call.

What makes this even weirder is a couple weeks ago when the guy installed my internet (I just moved to SF) speakeasy's test pegged at 20 mbps. 

So I figured I'd see if it was an OS issue. So I plugged in my Windows Work laptop and tested the connection and BAM 34mbps (no I am not missing a decimal point, or mean kbps).


Now i'm back on ubuntu, and once again 3mbps down 10 mbps up.

Anyone got any ideas?

---

### Post by aireq on 2009-01-16
Oh and this might help:

```
aireq@aireq-ubuntu-desktop:~$ sudo lshw -C network
[sudo] password for aireq: 
  *-network               
       description: Ethernet interface
       product: nForce2 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: a1
       serial: 00:10:dc:de:4f:66
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=67.180.180.82 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: fe:16:3f:76:84:13
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

### Post by any.linux12 on 2009-01-16
Maybe your network card is not fully supported by your linux version. That is life and that's why I preffer windows, couse there network grafic cards and bla bla bla are always fully supported and run as they should (at their best)

Anyway do you have you drivers activated?

---

### Post by Michael.Godawski on 2009-01-16
hi, can you please post the result of 
```
iwconfig
```

---

### Post by aireq on 2009-01-16
I'm using the onboard NIC on my MSI-K7N2G motherboard. It has an Nvidia BIOS. I didn't install any kind of drivers for it though it just worked when I installed ubuntu until I noticed the speed problem

```
aireq@aireq-ubuntu-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
```

---

### Post by halovivek on 2009-01-16
Hi 
i am also facing the same problem. if i connect the torrent in windows i could get Max 10Mbps/sec to 18Mbps and normally i will get around 1Mbps. I have tested with the same torrent and having lot of seeds. i used linux torrent since we can get lot of seeds for that one. But if i use the Ubuntu i am not getting more than 600Kpbs to 800 Kbps. I use Transmission control bit torrent. 
Could you please tell me how to solve this?

---

### Post by superprash2003 on 2009-01-16
are you using deluge? have you enabled port forwarding?

---

### Post by aireq on 2009-01-16
> **superprash2003 said:**
> are you using deluge? have you enabled port forwarding?

I don't know what either of those things are . .. so if I am it wasn't on purpose.

---

### Post by aireq on 2009-01-17
Here's screen shots. I cleared my firefox cache between each test just in case.

**XP Laptop**

[IMG]http://dl.getdropbox.com/u/113068/XP%20Laptop%20test%201.jpg[/IMG]

[IMG]http://dl.getdropbox.com/u/113068/XP%20Laptop%20test%202.jpg[/IMG]

[IMG]http://dl.getdropbox.com/u/113068/XP%20Laptop%20test%203.jpg[/IMG]

[IMG]http://dl.getdropbox.com/u/113068/XP%20Laptop%20test%204.jpg[/IMG]




**Ubuntu Desktop**

[IMG]http://dl.getdropbox.com/u/113068/ubuntu%201.png[/IMG]

[IMG]http://dl.getdropbox.com/u/113068/ubuntu%202.png[/IMG]

[IMG]http://dl.getdropbox.com/u/113068/ubuntu%203.png[/IMG]

[IMG]http://dl.getdropbox.com/u/113068/ubuntu%204.png[/IMG]

---

### Post by unused_bagels on 2009-01-17
I'm having the same problem with torrenting.  I've forwarded all my ports, have a static IP, just like I did with windows, and still download at a disappointing 3Kbps.  The same torrent I got at at least 60kbps (it's a stale torrent, but still good) in windows.  I'll give you any Terminal outputs you need, just please help! This is irritating enough to switch back to windows.

---

### Post by gogogo111 on 2009-01-17
I will agree to this...back in windows I would get 6 down/ 512 up..

But in Ubuntu I am getting 3 down/ and what seems like 128 up, its really slow.

---

### Post by Ben Page on 2009-01-17
I had similar probs with my 8.10. When it was installed via WUBI, but when I installed it in its own partition in ext3 filesystem it worked fine (like Win). My speed is just 256kbps but it works in full speed. If you are running Live CD or WUBI install this is probably the issue. If not, try updating your installation, use Opera browser and Ktorrent or monsoon, maybe itll help.

---

### Post by unused_bagels on 2009-01-17
> **Ben Page said:**
> I had similar probs with my 8.10. When it was installed via WUBI, but when I installed it in its own partition in ext3 filesystem it worked fine (like Win). My speed is just 256kbps but it works in full speed. If you are running Live CD or WUBI install this is probably the issue. If not, try updating your installation, use Opera browser and Ktorrent or monsoon, maybe itll help.
wait, what did you do? wubi?  Also, I've tried Ktorrent, and it worked just as slow.  Every time I test my ports, it says port closed, even though I know they're open. i know my problem's in the OS, cos i've tried different programs, and if I were to boot into windows, it would be fast as heck.

---

### Post by superprash2003 on 2009-01-18
post output of ifconfig from the terminal

---

### Post by unused_bagels on 2009-01-18
```
eth0      Link encap:Ethernet  HWaddr 00:1d:60:c1:69:eb  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:60ff:fec1:69eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1846047 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1994707 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1205394385 (1.1 GB)  TX bytes:1312206186 (1.2 GB)
          Interrupt:253 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19212 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19212 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2252970 (2.1 MB)  TX bytes:2252970 (2.1 MB)

```

---

### Post by Ben Page on 2009-01-18
WUBI is Windows Based Installer, it installs Ubuntu IN windows like any other Win app, but since you haven't heard of it, its probably not the cause of your probs. My ports are also closed in Ubuntu, but work in Win (?), but since i've installed Ubuntu in ext3 partition my torrent speeds are same as those in Win, although my internet speed is only 256kbps (so maybe because its slow it manages to work in full speed). just letting the developers or gurus know that this is not an isolated issue and it is only Ubuntu exclusive.

---

### Post by unused_bagels on 2009-01-18
My ubuntu is already on an ext3 partition.  Do you mean a separate partition from everything else? O.o  Today my speed's gone up a bit, and I'm wondering if it's my seeds, or if it's me.  I'm downloading a fresh torrent with 5K seeders to test my speed.

UPDATE:
It seems my ports report closed,  but I just spiked a torrent at 85kbps, which is a decent speed for me.  However, with 5K seeds, I should have gotten closer to 1MBps.

---

### Post by Ben Page on 2009-01-18
Never mind that about the partitions.
It is not important how many seeds you have (as long as there are few). Sometimes speed of a torrent download can be slow even with 10K seeds because traffic is overloaded, or your ISP has a bad link to those seeds etc. But its important that you use the same torrent file to download content in Win and Linux - and then if speeds are much different there is a problem. I even used the same client microtorrent in both OS but Lin gave 40% slower speed...

---

### Post by blothian on 2009-01-18
Ihis is my windows laptop (wireless) Speed connected at 2.2Mb/sec with talktalk broadband = [IMG]http://www.speedtest.net/result/393021978.png[/IMG] I will post later from my Ubuntu.
Hope this helps!
Benjamin Lothian

---

### Post by unused_bagels on 2009-01-18
So ben, what can we do about it? :confused:

---

### Post by blothian on 2009-01-18
> **unused_bagels said:**
> So ben, what can we do about it? :confused:

I didnt make it clear i was just seeing if there is a difference beetween my Windows And ubuntu
Sorry:(

---

### Post by blothian on 2009-01-19
Ok this is my Ubuntu computer.[IMG]http://www.speedtest.net/result/393515962.png[/IMG]
Ben

---

### Post by mustard greens on 2009-01-19
I have been experiencing the same thing, regardless of running a p2p app.  when I speed test in ubuntu w/ firefox it is consistantly HALF the speed of windows w/firefox.  I had suspected port throttling, but found that these were my speeds whether I was file sharing or not.  I still get usable speed from ubuntu 10m and 5m, but with windows I was getting 25+.

---

### Post by aml on 2009-01-24
Just to lend weight to the body of people reporting slower transfer rates with Ubuntu than Windows, 

I'm using Ubuntu Ibex and when downloading a large file using wget I get approx. 300KB/s, when doing the same test in windows I get 1200KB/s. THis on a 2 meg cable line.

Alec

---

### Post by thegom on 2009-01-24
This is happening to me too - the main box I use dual boots ubuntu 8.10 and xp, torrent speeds crawl along when I'm using ubuntu but are zippy fast when I'm using xp. Port forwarding is enabled as is a static ip.

What makes this odder is that I have a second box running Intrepid, but the hardware is quite old. I was using it as a torrent box up until I, um, broke it slightly last week by fiddling with it too much (its fixable tho, just have to reconfigure a load of stuff). The thing with this box was that it could download torrents at the max speed my connection supports no problem.

This is leading me to believe that the slow connection may be being caused by a driver problem for my network card - I'm going to go find out what make/model it is and do some research and I'll post my findings here. (incidently, anyone know how to find this out from the terminal?)

---

### Post by unutbu on 2009-01-24
thegom, the following commands will tell you the make/model of your network adapter:

If you have a PCI card:
```

lspci -nnv
```

If you have a USB device:
```

lsusb
```

Finally, type
```

sudo lshw -C network
```
to see what driver you are using.

It might also be helpful to you to search this page for notes on your hardware.
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
Posting a note concerning your problem on this page may also help warn others if your hardware is not fully compatible with Ubuntu.

---

### Post by thegom on 2009-01-24
> **unutbu said:**
> thegom, the following commands will tell you the make/model of your network adapter:

If you have a PCI card:
```

lspci -nnv
```

If you have a USB device:
```

lsusb
```

Finally, type
```

sudo lshw -C network
```
to see what driver you are using.

It might also be helpful to you to search this page for notes on your hardware.
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
Posting a note concerning your problem on this page may also help warn others if your hardware is not fully compatible with Ubuntu.

Thanks unutbu, I'll be making a note of that for future use!

I actually just followed the instructions for opening ports in ubuntu (NOT in your router) in this thread:

[http://ubuntuforums.org/showthread.php?t=331161&highlight=transmission](http://ubuntuforums.org/showthread.php?t=331161&highlight=transmission)

And now torrents seem to be working a lot faster - I'll have to do some proper testing but I think it may have solved my problem.

---

### Post by unused_bagels on 2009-01-24
wow, I had no idea ubuntu had to have ITS ports forwarded as well.... Is there a specific port that FF uses (esp. for http:/ downloads), so I can forward that one too?

---

### Post by ajcham on 2009-01-24
> **unused_bagels said:**
> wow, I had no idea ubuntu had to have ITS ports forwarded as well.... Is there a specific port that FF uses (esp. for http:/ downloads), so I can forward that one too?

Almost all HTTP traffic uses port 80 - occasionally another port may be explicitly specified, but I don't recall ever encountering such a scenario.  HTTPS uses port 443.  You don't need to enable forwarding of these ports - they will be enabled by default.  (If port 80 was blocked, you wouldn't be reading this!)

---

### Post by unused_bagels on 2009-01-24
lol ok
;)

---

### Post by Ben Page on 2009-01-24
> **thegom said:**
> Thanks unutbu, I'll be making a note of that for future use!

I actually just followed the instructions for opening ports in ubuntu (NOT in your router) in this thread:

[http://ubuntuforums.org/showthread.php?t=331161&highlight=transmission](http://ubuntuforums.org/showthread.php?t=331161&highlight=transmission)

And now torrents seem to be working a lot faster - I'll have to do some proper testing but I think it may have solved my problem.

**This thread solves the speed issues in torrents** (kTorrent for me particularly on 768Kbps connection).

---

