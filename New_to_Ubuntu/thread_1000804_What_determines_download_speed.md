---
title: "What determines download speed?"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by HarriSeldon on 2008-12-03
Here's my situation:

My mom is complaning of slow download speeds so I bring over my laptop to have something to compare it to. She has 3 meg DSL.

Her desktop is a dual core athlon (X2 5000 I think) with 2 gigs ddr2 800, gigabyte mobo w/ integrated ethernet, 250 gig hd, and an Nvidia graphics card. She's running Vista SP1 64.

My laptop is an HP Pavillion dv6000 with an intel core2duo, 3 gigs ram, and Ubuntu 64.

I go to speedtest.net to check each PC and the download speed from the nearest server is a lot faster on my laptop. She's getting around 900kbsp and I'm getting around 1700kbps. Upload speeds are pretty much the same.

Her main complaint is the studdering of Youtube videos.

If anyone has any suggestions, I'd appreciate it.

Thanks and have a good one,
H

---

### Post by w4ett on 2008-12-03
I'd go to [www.speedguide.net](www.speedguide.net) they have loads of registry tweaks to maximize the windows network settings (most of which are relatively painless) and also plenty of practical MS advice.

---

### Post by oilchangeguy on 2008-12-03
> **HarriSeldon said:**
> Here's my situation:

My mom is complaning of slow download speeds so I bring over my laptop to have something to compare it to. She has 3 meg DSL.

Her desktop is a dual core athlon (X2 5000 I think) with 2 gigs ddr2 800, gigabyte mobo w/ integrated ethernet, 250 gig hd, and an Nvidia graphics card. She's running Vista SP1 64.

My laptop is an HP Pavillion dv6000 with an intel core2duo, 3 gigs ram, and Ubuntu 64.

I go to speedtest.net to check each PC and the download speed from the nearest server is a lot faster on my laptop. She's getting around 900kbsp and I'm getting around 1700kbps. Upload speeds are pretty much the same.

Her main complaint is the studdering of Youtube videos.

If anyone has any suggestions, I'd appreciate it.

Thanks and have a good one,
H

you don't say how either are connected. i'm guessing the desktop is wired, and the laptop is wireless. first check all connections, and make sure everything is tight. from the cable out of the wall, to the modem/router, and to the computer.

---

### Post by Michael.Godawski on 2008-12-03
):PDesktop > Vista
       Laptop > Ubuntu


But I guess it cannot be that easy...
Perhaps there are some hidden applications in vista consuming the download capacities?

---

### Post by HarriSeldon on 2008-12-03
> **oilchangeguy said:**
> you don't say how either are connected. i'm guessing the desktop is wired, and the laptop is wireless. first check all connections, and make sure everything is tight. from the cable out of the wall, to the modem/router, and to the computer.

both are wired

---

### Post by DGortze380 on 2008-12-03
> **oilchangeguy said:**
> you don't say how either are connected. i'm guessing the desktop is wired, and the laptop is wireless. first check all connections, and make sure everything is tight. from the cable out of the wall, to the modem/router, and to the computer.

x2. Your Layer 1 Network has a lot to do with transfer speeds.

How are the computers physically connected?

---

### Post by HarriSeldon on 2008-12-03
> **DGortze380 said:**
> x2. Your Layer 1 Network has a lot to do with transfer speeds.

How are the computers physically connected?

Telephone cord from the wall to a "Speedstream" modem, ethernet cable to computer. I hook one up, do the speed test, disconnect it, hook the other one up, and do the test again.

---

### Post by chrisod on 2008-12-03
900 kbs ought to way more throughput then needed to watch a YouTube video without stuttering. I don't think download speed is the issue. It sounds like something is going on with her computer. Does she have something running in the background that is eating up her CPU cycles?

---

### Post by davidsrsb on 2008-12-03
MTU settings are likely to be different. The Vista machine may be fragmeting packets, which causes a big speed hit if there is any packet loss or reordering

Or this my be DRM obsessed Vista trying to determine if the download is pirate

---

### Post by HarriSeldon on 2008-12-03
> **chrisod said:**
> 900 kbs ought to way more throughput then needed to watch a YouTube video without stuttering. I don't think download speed is the issue. It sounds like something is going on with her computer. Does she have something running in the background that is eating up her CPU cycles?

mabey, I'll try to copy a screenshot of the registry.

Something else to consider: I just went to download.com and started to download AVG. The download window said the transfer rate was 42.1 KB/sec.

---

### Post by HarriSeldon on 2008-12-03
Here it is

---

### Post by oilchangeguy on 2008-12-03
that's the task manager, not the registry. if your copy shows the entire screen, it looks ok.

---

### Post by Sarmacid on 2008-12-03
I've had issues with XP and internet, getting laggy all of the sudden. Had me going mad for a good while before I found out it's the automatic updates, it didn't even ask me, it just downloaded them. Maybe the windows box is trying to download something in the background, or it could be possible that malicious code is using your connection.

---

### Post by Kellemora on 2008-12-03
Hi HS

Is she using Firefox to connect to the web sites?

Although Firefox is normally A-OK, on one machine here it hogs 100% of the CPU all the time.  On the other machines, about 5 to 15% is all.  So on that machine we use Safari and it's almost as fast as Opera at nearly everything.

If we try watching streaming video on that machine with Firefox, it stops and starts a hundred times.  On Safari, never a glitch.

Now on other machines, Firefox or Opera Rules and Safari is the problem child.  I have no idea why either!

Also, the machine with the MOST memory just happens to be the slowest at almost everything.  Makes no sense sometimes.

TTUL
Gary

---

### Post by handydan918 on 2008-12-03
> **chrisod said:**
>  Does she have something running in the background that is eating up her CPU cycles?
Yes! The OP said mama was running Vista...


:D

---

### Post by HittingSmoke on 2008-12-03
From the symptoms it sounds like some sort of malware might be eating up bandwidth. Try running it in Safe Mode with networking and see if it improves.

Also might wanna check for rootkits. Before I retired all my Windows PCs for good, I used Avira AV and if I remember right it had pretty good rootkit detection. Works great along side Comodo Firewall and both are free.

---

### Post by EdThaSlayer on 2008-12-03
It depends on quite a few factors:
a)your internet connection advertised speed
b)how busy your internet providers servers are
c)how fast a connection the website has to the outside world
d)distance from the server the website is located

---

### Post by sledge73 on 2008-12-03
I just switched from vista on my compaq laptop to run linux mint 6 & it seems to me that any linux distro has a faster connection on the net. I think that the combo of automatic updates & java wanting to check for updates every time you connect, your download speed slows greatly. IMO I would dissable all auto updates & try a test that way. you may be surprised!!!

---

