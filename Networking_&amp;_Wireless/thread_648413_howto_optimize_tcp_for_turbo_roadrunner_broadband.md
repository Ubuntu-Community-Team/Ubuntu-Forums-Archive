---
title: "howto optimize tcp for turbo roadrunner broadband"
date: 2007-12-23
forum: Networking &amp; Wireless
---

### Post by s.mcclatchie on 2007-12-23
Hello

I am finding that my cabled connection on turbo roadrunner in San Diego is half the speed on my setup with ubuntu 7.1 gutsy compared to my setup on windows XP. I'm getting about 7 MB/s on linux and up to 14 MB/s on windows (no complaints there, it's just that I can't stand microsoft trashing the penguin). My guess is that Times Warner use some optimization routines on windows when the service is activated but I could not take advantage of these on linux. So I assume (tell if I'm wrong) that I need to do some TCP-IP optimization on my ubuntu system. Can someone tell me how to do this, please? I'm cautious because I don't want to break my network interface. 

I've run netstat and tcpdump to give some information. The text files of the output are attached.

Best fishes

Sam
-- 
Sam McClatchie (Fisheries oceanographer, SWFSC, NOAA)
& Elena Turin (Internal controls accountant, UCSD)
work: SWFSC, 8604 La Jolla Shores Drive, La Jolla, CA 92037-1508, USA
home: 12723 Salmon River Rd, San Diego, CA 92129, USA
web: <http://www.fishocean.info>
Sam's cell: 858 752 8495

---

### Post by guyvertoon on 2007-12-24
Try this, worked for me on FIOS...

[http://ubuntuforums.org/showthread.php?t=640720](http://ubuntuforums.org/showthread.php?t=640720)

HTH

---

### Post by s.mcclatchie on 2007-12-24
Thanks, that was very helpful. I've tried both the recommended methods, editing /etc/rc.local or editing /etc/sysctl.conf. The main improvement so far seems to be in upload speed. It doesn't seems to matter which of these files you edit.

I also tried adjusted RWIN values in each of the files from 256960 to 513920. At the moment I have the same upload speed on ubuntu and the windows machines (1510 kb/s) but still only half the download speed on ubuntu (around 7000 kb/s) compared to windows (around 14000 kb/s). This tweaking has improved upload speed by 50%, but not changed the download speeds yet.

Probably I have to optimize these values
rmem_default = Default Receive Window
rmem_max = Maximum Receive Window
for roadrunner broadband, since the speed problem is with the download. I guess 256960 or 513920 are not the optimal values. I'll try and see what I can find.

---

### Post by s.mcclatchie on 2007-12-29
Now I am distrustful of the speed test results because I had a service tech from Times Warner here and he ran an his own speed check on the windows machine. He got 7.5 MB/s download not 14.5 MB/s which was the result from <http://www.speedtest.net/>. I am wondering how to get a reliable speed test that will give a true comparison of the linux and windows machines.

---

### Post by s.mcclatchie on 2008-01-02
I have tried quite a variety of speed test sites and don't really trust the results. However, this site has a lot more technical information <http://www.dslreports.com/speedtest>. Apparently java based tests can give higher speeds on high speed connections than flash-based tests. So I made sure the Java runtime environment was installed (see Ubuntu package lists), and ran a java-based speed test. I got a 3457 download/ 1470 Kbps upload result from Los Angeles. Since the advertised speed for my cable connection is 7500 kB/s I'm still not happy. 

The same site has information on the optimal receive window (RWIN) setting <http://www.dslreports.com/faq/tweaks/5._RWIN>. They give a formula which is latency in ms X 1.5 X advertised speed in kB/s / 8 as the optimal RWIN. I haven't got a result for latency yet, but if I assume 50 ms, the formula gives 50 X 1.5 X 7500 / 8 = 70,312 for the RWIN setting. This is only about a third of the RWIN = 256960 I'm currently using.

---

### Post by guyvertoon on 2008-01-02
Be sure that the speed test that you are doing will cover the speed that you are supposed to have. I know it sounds obvious, but I feel into the trap the first time I checked my broadband connection.

HTH

---

### Post by s.mcclatchie on 2008-01-06
I decided to copy guyvertoon's /etc/sysctl.conf lines below:
 
net.core.rmem_max = 16777216
net.core.wmem_max = 16777216
net.ipv4.tcp_rmem = 4096 87380 16777216
net.ipv4.tcp_wmem = 4096 65536 16777216
net.ipv4.tcp_no_metrics_save = 1
net.core.netdev_max_backlog = 2500

even though the numbers don't seem to fit the RWIN calculation.
My speed test results improved from 2562/1454 Kbps to Download: 4445 (Kbps)
Upload: 1815 (Kbps) using the Java-based test on <http://www.dslreports.com/speedtest>.

This is the best result so far.

---

### Post by s.mcclatchie on 2008-05-31
Looks like much of the problem may have been with my hardware. I'm now running an emperor linux 64-bit laptop under Ubuntu 8.04 heron and the speed is much improved:

download 14,589 kb/s
upload 1,856 kb/s

So much for optimization of roadrunner in San Diego. Optimize your hardware.

---

