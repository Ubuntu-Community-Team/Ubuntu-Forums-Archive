---
title: "Networking won't work! Immediate help required!"
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by djbon2112 on 2008-01-10
For For no reason at all my networking in Ubuntu went down. No programs will connect to the internet, but the network configuration says nothing is wrong. Netstat gives results. It is not hardware related because I can access the internet in Windows XP and off my Ubuntu LiveCD on the computer. I changed no settings or programs, and the latest update was an hour ago, to the Deskbar applet. 

Does anyone know what to do!? I need to get my PC working again!

---

### Post by tatster on 2008-01-10
Hi,

You may need to give some more information before anyone can really offer useful help.
For example, does your machine have a static or DHCP assigned IP address?   Is your Ubuntu machine behind a router?  If so, can you ping your router's IP address?

If you can describe your setup in a bit more detail, hopefully someone will be able to offer guidance.

Tatster.

---

### Post by djbon2112 on 2008-01-10
Sorry 'bout that.

Alright, it's all DHCP assigned, and the network connection has just been on "roaming" since I set up Ubuntu and it's worked fine. I'm on a university Resnet so I have no idea how the routing scheme works. I can't ping anything from Ubuntu (it just sits there).

Here's the output of ifconfig:

```
joshua@JMB-Laptop-001:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx
          inet addr:xxx.xxx.xxx.xxx  Bcast:xxx.xxx.xxx.xxx  Mask:255.255.255.128
          inet6 addr: fe80::21c:23ff:fe8a:f27c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:393 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:70793 (69.1 KB)  TX bytes:1182 (1.1 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

---

### Post by losmurfs on 2008-01-10
I have a Dell XPS 400.  It has a Dual Core Pentium D.  I installed Kubuntu 7.10 64-bit.  In Windows XP Pro, the internet access is fast and responsive and downloads download quickly.  In Kubuntu 7.10, any download from Adobe.com, webpage, flash plugin, what ever, downloads 5400 bytes and then stops and never finishes downloading the page/file.  In google.com I can get half the google.com logo.  Installs via aptitude get between 200B/s and 7KB/s but if left long enough eventually download completely.  I compiled/installed a newer version of the e1000 module, but that did not help.  I installed a brand new 10/100 ethernet NIC that uses the Realtek driver but got the same results.  I disabled the second CPU core but got the same results.  I tried both NICs off a 32-bit Kubuntu 7.10 Live CD and got the same results.  ifconfig and ethtool report that there are no errors of any kind and no dropped packets. HHHHHHHHHHHEeeeeeeeeeeeeeLLLLlp!!!!!!!!!.

Thank you.

Please let me know if there is anything I can do to start diagnosing the problem or if you are curious or would like to help please let me know if there are any more details you would like me to provide.

---

### Post by BLTicklemonster on 2008-01-10
sudo /etc/init.d/dbus restart

may or may not work. I suddenly have a hal error when I boot, and have to run this when I get to the desktop (after closing the hal error, of course).

---

### Post by djbon2112 on 2008-01-11
This didn't work for me.

As I mentioned in my original post, this issue just started today, out of the blue. The only update/thing I did to the system was install an update for the Deskbar Applet, and about half an hour later (no restart or anything) BAM no internet at all, but only in my installed copy of Ubuntu (my dual-booted XP and liveCD/USB versions of Ubuntu work fine). Has this ever happened to anyone else? Is there some way/command to just restart all network settings back to the defaults (since they obviously work)?

EDIT: I forgot to mention, I tried using other DNS servers (specifically the FreeDNS ones) but this didn't help at all. No pings get out, and looking at that ifconfig report, I see a lot of errors. Anyone know anything about that?

---

### Post by djbon2112 on 2008-01-11
Sorry to bump, but my computer is useless without a network connection! Anyone have any ideas?

---

### Post by BLTicklemonster on 2008-01-11
Have you tried going to system, administration, network, then go to your wired connection, disable it, then enable it? My connectivity went down one a year or so ago, and I did that and it brought it back up. Just trying to help.

---

### Post by djbon2112 on 2008-01-11
No dice. I think I've just given up, and I'm going to do a fresh reinstall of Ubuntu; I needed to fix my screwed up partition table anyways. I'm just going to leave this thread open though in case anyone has other ideas, and for losmurf's question.

---

### Post by Lord Banshee on 2008-01-11
Just to bring this issue up again as i have the same issue.

My network was doing fine last night, then when trying to use it in the morning it would not work. I can get ubuntu to find an Ip address if i keep restarting the network manager but it still will not connect to anything. Then the IP goes away.... I am not sure if there was an update that was downloaded before this started but i am using a via network card (via-rhine drivers) tried enabling/disabling roaming, setting a static ip, and even  setting it as dhcp, nothing works right :( .  I even reinstalled and removed the network manager completely and still no connections. 

i guess i am going to reinstall ubuntu also and watch what updates install as i really think that was the issue. :popcorn:

---

