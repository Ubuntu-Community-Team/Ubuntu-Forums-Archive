---
title: "Network/Internet Slow"
date: 2006-08-27
forum: Networking &amp; Wireless
---

### Post by Jim313 on 2006-08-27
I am experiencing very slow network connections with Ubuntu/Linux but it is OK in my MS Windows set up.  Reading all the posts I thought it was the browser but after making all suggested changes, I now believe it is a connection set up.  All browsers FF, Swiftox, Knoquerer, Opea, and e-mail are slow.  Even looking in at my router set up through the web interface is slow.  I have disabled IPV6 completely.  That helped ever so slightly but my connection is still 10 times slower than with Windows using IE and Firefox.

This seems to be either a configuration issue or driver issue although I do not have the experience to know for sure.  My network setup looks OK to me.  I tried setting up a static IP to see if that helped but it did not.  My MTU is set at 1492, IP 192.168.0.49, Gateway 192.168.0.1, Subnet mask 255.255.255.0, DNS Server 192.168.0.1, local host 127.0.1.1.  I have not manually loaded any drivers but allowed Ubuntu to do so.  

Does anyone have any ideas?  Please help!!!  Thanks:(

---

### Post by Jim313 on 2006-08-27
I would like to add I just tested my internet speed at dslreports. It is 4700  down and 357 up.  Pretty fast so why do images load so slow?  Please help.

I also ran an if config below:
eth0      Link encap:Ethernet  HWaddr 00:0C:76:96:59:07
          inet addr:192.168.0.49  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8153 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5753 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8106701 (7.7 MiB)  TX bytes:1320164 (1.2 MiB)
          Interrupt:209 Base address:0x4700

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22028 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22028 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:17918758 (17.0 MiB)  TX bytes:17918758 (17.0 MiB)

---

### Post by Jim313 on 2006-08-28
Just thought I would pass along a surprising solution. My router was not playing well with Ubuntu (or vice versa).  When I direct connected to the modem instead of router, my speeds took off and my pages loaaded quickly, even images.  I never would have thought this could be the issue but apparently it is.  I guess I will have to invest in another router.  

FYI - my current router is a 2+ year old Netgear MR814.  It has been a good router but I guess Ubuntu doesn't like it.

---

### Post by funchords on 2006-08-28
Your ifconfig indicates that your MTU is set to 1500.  This is correct if you have a cablemodem.  1492 may work better if you're on DSL.

I'm not sure a new router is going to help.  Your speedtest was not slow.

If you buy a new router, buy it locally so that you can return it without a hassle.

---

### Post by Jim313 on 2006-08-28
Good advise Funchords.  I agree with you my internet speed is good.  I am still playing with settings thinking that the router shouldn't be the issue.  BTW - I do have a cable connection.

---

### Post by pclogic on 2006-08-28
Does your router have any Quality of Service (QoS) features?  I have a Linksys Wireless-G router that allows me to prioritize network traffic based on the physical port of the built-in switch and/or the TCP port the traffic is coming on upon.  After I set the  switch port to which my server is connected to highest priority and  set TCP ports 80, 21, and 22 to highest priority, my server ran considerably faster.

---

### Post by wiraone on 2006-08-29
I'm having the same problem last week and I still have the same problem. I have no idea what I have done wrong, no changes done on my router setting as far as I remember.. it was sudden change and everything went crawling. As the original poster, my WinXP runs great on the same machine. I've no idea if I did an package update before I experienced this .. Currently booting WinXP as default since I couldn't find what caused the problem.

---

### Post by funchords on 2006-08-29
Can you both do this command and post the top 10-15 lines of the output?

**sudo top -b -n 1**

The part I want looks like this:  

[FONT="Courier New"]
top - 11:37:44 up  1:21,  1 user,  load average: 0.19, 0.26, 0.31
Tasks:  88 total,   2 running,  86 sleeping,   0 stopped,   0 zombie
Cpu(s): 15.9% us,  3.0% sy,  0.1% ni, 77.2% id,  3.7% wa,  0.1% hi,  0.0% si
Mem:    256248k total,   249220k used,     7028k free,     5904k buffers
Swap:   746980k total,    29084k used,   717896k free,   107780k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 7065 root      15   0  2192  988  756 R  1.9  0.4   0:00.04 top
    1 root      16   0  1564  512  448 S  0.0  0.2   0:01.59 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.29 events/0[/FONT]

---

### Post by vip8439 on 2006-08-29
I'm having the same problem.  My internet connection reminds me of the days of 14.4 modems.  I just installed Ubuntu a few days ago and so far I love it!  It recognized my wireless card right off the bat.  It took me 7 hours to get it to work in Fedora Core 5 and even then I couldn't get an ip address.  I can get a valid wpa connection to my router but the internet and software updates are crawling.  I've already tried disabling IPv6 but that didn't do anything.  If I run a tracert to google i get a few hops that take 15000ms and 30000ms, but when a tracert on my laptop or the same machine using windows, the latency is considerably less i.e. 15ms.  I've searched through many forums but all of them only seem to mention the IPv6 thing.

Also, I forgot to mention.  If I do an ifconfig on ra0, line 5 states (TX packets:777 errors:8 dropped:8 overruns:0 carrier:0 collisions:15 txqueuelen:1000) and of course as more packets are sent the number of errors/dropped packets increases.  Is this a driver issue?  In windows I have no errors/dropped packets/collisions on this card.

---

### Post by edhogan on 2006-08-29
Jim,

Do you have both a network card and a wireless adapter?

Here's why I ask.  When I installed Ubuntu on my laptop, I had only the wireless PCMCIA card plugged in.  The installation went smooth, internet browsing was very fast etc... 

After a few weeks of fiddling with Ubuntu, I decided to remove the the wireles card and install a network PCMCIA card along with an external wireless access point.  That too went smooth, quick internet response etc...

Satisfied that I could use either the PCMCIA wireless adapter, or the PCMCIA network card and an external accesss point, I went back to the wireless adapter.  However I left the network card plugged in its PCMCIA slot, even though nothing was hooked up to it.  The wireless performance went down hill, very slow and at times totally unresponsive.  

So I removed the network card, leaving only the wireless adapter in place and all is well. It seems as if I cn have only one device plugged in at a time.

Perhaps this is your problem?

Ed

---

### Post by Robopop on 2006-09-02
> **funchords said:**
> Your ifconfig indicates that your MTU is set to 1500.  This is correct if you have a cablemodem.  1492 may work better if you're on DSL.

I'm not sure a new router is going to help.  Your speedtest was not slow.

If you buy a new router, buy it locally so that you can return it without a hassle.

I have the same problem as everybody else and is currently using MS Windows. I'm on DSL and before switching over to Dapper I just wanted to know how to change MTU and what it is.

Thanks in advance for any help.

---

### Post by hermesrules on 2006-09-02
I've been having the same internet slow down in Kubuntu since I moved to a different place, where I get the internet over a LAN cable, with my own IP address, which albeit seemingly static, is a router-assigned. I also have a router at home, since it is one cable, but with two computers with two different IPs, which I use as a switch (if anyone is able to tell me how to configure it as a router with two static IP addresses, I'd greatly appreciate it! It's a 2-year old Linksys, which I've used before for the wireless capabilities, it has NAT too).

I can't figure out what causes the terrible slow down, it really feels like the days with the 14.4 modems, and in Windows I can get up to 1 MB/sec download speed. It was for the first time today that I ever saw the ping command to report results in the 10s of ms, for foreign sites - even in the 100s.

I also don't believe it is IPv6-related since on my laptop, I have IPv6 disabled, but the situation is bad. When I used a live cd with the same version (sorry, I forgot to mention I am using Dapper), it has IPv6 enabled, and it is still slow. So it must be something else, however my searches turned out this and another thread as closest.

I do hope someone will suggest something soon, as I am far from being an expert in networking set ups.

What I did, was to set up manual IP in the KDE networking configuration box, I've entered everything, like subnet mask, default gateway, DNS servers, etc. The /etc/network/interfaces seems fine (I'd post it, but I had to boot back into Windows to access the forums, as otherwise it is sooooo slooooow), yet the internet is seriosuly cripled.

Thanks in advance!

---

### Post by funchords on 2006-09-03
If you want to try changing your mtu, see this:

[http://www.ubuntuforums.org/showpost.php?p=1448068&postcount=15](http://www.ubuntuforums.org/showpost.php?p=1448068&postcount=15)

---

### Post by hermesrules on 2006-09-03
I also tried changing the MTU, nothing changed. It was set to 1500 by default.

Interestingly, download speeds are high, it is web surfing that takes time, especially at the beginning, or if there are many small files (like small pictures to be downloaded). For example, when I type [www.google.com](www.google.com) in konqueror, it takes a while of "thinking", then the page shows without pictures, only with placeholders, and within probably 15-20 seconds pictures show up too.

When I issue a ping command, it takes a while for the first line of the command to show, then I get values around 10 ms for sites in my country, and more than 60 ms for [www.ubuntu.com](www.ubuntu.com)! This is ridiculous!

Also, the above happens on my installed Dapper. If I try the latest LiveCD, it is much, much WORSE!!! Any speed is crawling, and I can't really try disabling IPv6, because it seems like I would need to reboot, so I don't know if it is IPv6.

Even it is one of the problems, it is not the only one, as on my laptop IPv6 is already disabled.

What I don't understand here is 1) why Windows has no such issues?, and 2) why did it never happen before I changed locations. Hence, something in my internet setup seems to contradict the ISP's technology. But come on, Windows does a perfect job here, why can't Ubuntu?

Can anyone recommend a different Live CD distribution (not Gentoo), which I can try for comparison to see if other Linux-es do a better job?

Thanks!

---

### Post by funchords on 2006-09-03
In your case, this sounds like DNS problems.  60 ms. is okay.  If it's 300+ or so, I'd start wondering why.  

Try this:   

[FONT="Courier New"]robb@topol003:~$ **dig [www.ubuntu.com](www.ubuntu.com)**

; <<>> DiG 9.3.2 <<>> [www.ubuntu.com](www.ubuntu.com)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 20600
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;[www.ubuntu.com](www.ubuntu.com).                        IN      A

;; ANSWER SECTION:
[www.ubuntu.com](www.ubuntu.com).         600     IN      A       82.211.81.166

[COLOR="Red"];; Query time: **60 msec**[/COLOR]
;; SERVER: 68.87.69.146#53(68.87.69.146)
;; WHEN: Sun Sep  3 09:37:17 2006
;; MSG SIZE  rcvd: 48
[/FONT]

This will tell you if your DNS lookups are slow.  

> **hermesrules said:**
> When I issue a ping command, it takes a while for the first line of the command to show, then I get values around 10 ms for sites in my country, and more than 60 ms for [www.ubuntu.com](www.ubuntu.com)! This is ridiculous!

That sounds like you're doing better than average.  My ping times are twice that, regardless of the operating system.  

The initial delay sounds like a DNS problem, again.

> **hermesrules said:**
> Can anyone recommend a different Live CD distribution (not Gentoo), which I can try for comparison to see if other Linux-es do a better job?

Your browser slowness is on a LiveCD?  Do you have a lot of RAM?

A LiveCD is good at looking at features.  Performance testing on a LiveCD is obviously a bad idea.  You don't have any swapfile and much of your memory is used in making a ramdisk.

On a LiveCD, if the speeds are good, the pings are good, and the DNS lookups are fast, then you have some assurance that a web browser in an installed environment will do okay.  I don't know if the browser cache is working on a LiveCD since it would eat RAM instead of disk space.

My other LiveCD of choice is Knoppix, however it is also based on Debian and should not perform any differently.  Fedora Core 5 (released)/6 (pre-release) just announced a LiveCD, but I haven't tried it.  Fedora is based on RedHat.

---

### Post by hermesrules on 2006-09-04
The slowness is on both my laptop running Dapper, and on the Dapper LiveCD, it does not matter, I should say internet speed is even worse on the LiveCD. I didn't mean I wanted to test performance, I only wanted to see if it were my settings on the laptop that crawled things down, but since the LiveCD behaved even worse, I thought it is probably Kubuntu, not my settings.

I have never had any such issues before when I've used a Live CD. Internet has always been very responsive. Indeed, I have 1 GB of RAM, but don't think the browser cache has anything to do here. I do suspect, too, it is a DNS-related problem, but I am not knoweledagble enough on the issue to be able to solve it.

I think you are right about the ping of 60 ms being ok, I think I meant 600, but since I am now at work, there is no way of telling. I will need to double check it.

Does anyone know of a Windows command analogous to "host" in Linux, and how can I time it? Like typing "time host www.google.com", but make it work in Windows too? This way, perhaps, I can see if there is any difference due to DNS-related issues...

Thanks, everyone!

---

