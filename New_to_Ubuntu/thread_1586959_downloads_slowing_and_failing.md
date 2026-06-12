---
title: "downloads slowing and failing"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by kitcarson61 on 2010-10-02
Hey all,  I've been having trouble with download speeds for the last couple of weeks.  It just kinda happened all-of-a-sudden.  I usually start up and go get a refreshing adult beverage while the computer boots and Firefox starts so it wasn't that big a deal, but I was trying to download some different distributions to try out this and last weekend and the download speed wouldn't get above 150kps using standard downloads or torrents.  The worst part is that the downloads would completely stop after a few minutes (timing varied).  I got Ubuntu 10.10 all the way to 63% last night before it stopped completely and dropped.  One thing that seemed weird was that if one download stopped downloading and I would start another one of a different distro, the first would start up again and they'd both start downloading faster than before, then slow to a stop again.  That was using standard downloading, not bit torrents.  I don't know where to go from here.  I've reset the cable router and network router, etc., removed other computers from the routers, removed the wifi router in every conceivable combination...   HELP, I'm going mad.  It even takes "snotmail" about two minutes to completely load.

---

### Post by jtarin on 2010-10-02
Try pinging different host like google,yahoo etc; and see what the results are.
Execute the command ```
ifconfig
``` in the terminal and post the output.
Have you done any changes to anything network related before this time?

---

### Post by kitcarson61 on 2010-10-02
Ok, here's what came up from  ifconfig -

 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:76:8c:5f:b9  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:76ff:fe8c:5fb9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1647 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1890 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1002274 (1.0 MB)  TX bytes:514562 (514.5 KB)
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

I have no idea what any of that means.
No changes to the network.  Hadn't set up the network again after the last installs.
Thanks for your prompt reply.  Sorry this is so late.  Had to step out for a while.

So, what time is it there in Vladivostok?

---

### Post by jtarin on 2010-10-02
It's 1:50pm Sunday.
How do you connect to the internet? Adsl modem,router etc;

---

### Post by kitcarson61 on 2010-10-02
8:10pm Saturday here in Jackson, California.
I connect via cable modem then through a Linksys 4 port router.

---

### Post by jtarin on 2010-10-02
So then you more than likely have a static connection (same IP address all the time). Do you have a Windows installation on the same machine? What kind of performance do you have on it? There is a possibility your ISP has throttled down your connection if your downloading a lot.

---

### Post by Dustin2128 on 2010-10-02
> **jtarin said:**
> There is a possibility your ISP has throttled down your connection if your downloading a lot.
that, and unfortunatley there's plenty of ISPs that try and break bit torrent. Both are particularly common with cable ISPs because of shared bandwidth.

---

### Post by kitcarson61 on 2010-10-02
Ya, that's it, a static connection and yes, Windows XP is on this same computer.  I had the same problem with slow and failing downloads with XP when I checked it yesterday, also.  As far as the ISP (Comcast), they'd better not be controlling my download and upload speeds, I pay them for their fastest unlimited plan and haven't had a problem until recently.  I upload a lot of photos and videos to web albums for family and friends.  
     Do I need to check with them?

---

### Post by Dustin2128 on 2010-10-02
> **kitcarson61 said:**
> Ya, that's it, a static connection and yes, Windows XP is on this same computer.  I had the same problem with slow and failing downloads with XP when I checked it yesterday, also.  As far as the ISP (Comcast), they'd better not be controlling my download and upload speeds, I pay them for their fastest unlimited plan and haven't had a problem until recently.  I upload a lot of photos and videos to web albums for family and friends.  
     Do I need to check with them?
ah, comcast, that explains it. They're the most draconian ISP (as far as I know) when it comes to controlling what you download/upload and capping speeds. I would still check with them though, unlimited must mean *something.*

---

### Post by kitcarson61 on 2010-10-02
From what you guys are saying, it does sound like (and due to the circumstances, seem like) Comcast may be the problem.  I'll look into it with them.
Thank you so much for your time and trouble.  I'll leave this post open until I find out from them.

---

### Post by jtarin on 2010-10-02
Do you have any other machines on this same connection? If they don't have any problems yet, you might try spoofing your machine address. Which essentially changes your hardware address as a different machine.You would need to disconnect as you do it then reconnect. I have a Dynamic IP and use jDownloader which reconnects with a new IP when I need it. Won't do you any good with a static though.

---

### Post by kitcarson61 on 2010-10-03
I just realized that this thread went on to a second page.  Sorry.
Checked my son's machine running 10.04 and it had the same problem.  Rebooted using Puppy live cd and the problem persisted.  Gotta be the ISP?

---

### Post by jtarin on 2010-10-03
Don't apologize for a second page....we can use all the pages that are needed. We recycle. :)

---

### Post by kitcarson61 on 2010-10-03
Go Big Green!

---

### Post by kitcarson61 on 2010-10-08
Yup, it's Comcast.  Since they've added another higher level of service recently (I didn't know about that) they've started limiting the other accounts.  
Thanks for the time and help everyone.

---

