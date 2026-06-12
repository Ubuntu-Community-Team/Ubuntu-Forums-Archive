---
title: "Lubuntu 17.04 - No internet connection, ethernet and wifi cards on PCI"
date: 2017-06-09
forum: Networking &amp; Wireless
---

### Post by yenice on 2017-06-09
I have installed Lubuntu from optical drive to a modest hardware system. My hardware details and wireless-info.sql script output are attached. So far I have no internet connection from that Lubuntu system.

What should I do next please?

The hardware PCI ethernet and PCI wifi cards have been tested working in pardus-linux. But I wanted to use a Lubuntu this time.

I have also uploaded Hardware report of "System Profiler and Benchmark Report" program to the following address in txt format.
[https://we.tl/e7XqHnNRh5](https://we.tl/e7XqHnNRh5)

---

### Post by pqwoerituytrueiwoq on 2017-06-09
Can you view your router via its ip address? (i could)
 I had this issues on the live iso Wednesday
this fixed it on the live usb boot for me
[http://www.hecticgeek.com/2017/04/ubuntu-17-04-systemd-dns-issues/](http://www.hecticgeek.com/2017/04/ubuntu-17-04-systemd-dns-issues/)

oddly it worked just fine in virtualbox...

---

### Post by yenice on 2017-06-09
Thank you [**[COLOR=#000000]pqwoerituytrueiwoq[/COLOR]**[COLOR=#000000] for this instant help[/COLOR]]("https://ubuntuforums.org/member.php?u=865458")
I checked my router configuration screens. Ethernet mac or wifi mac is not present. All other devices in my local network are present there. I know the mac IDs of my PCI ethernet and wifi cards for sure.

I also tried the hecticgeek site proposals without success :-(

I did 
sudo iwlist scanning 

and returned:
lo   Interface doesn't support scanning

---

### Post by marc-guay on 2017-06-09
> **pqwoerituytrueiwoq said:**
> 
this fixed it on the live usb boot for me
[http://www.hecticgeek.com/2017/04/ubuntu-17-04-systemd-dns-issues/](http://www.hecticgeek.com/2017/04/ubuntu-17-04-systemd-dns-issues/)

Just had this problem with Lubuntu 17.04 on an Acer Aspire One D250 and the simple solution in that blog post solved the Ethernet connectivity problem.  Now onto the wireless...:)  Thanks!

Marc

---

### Post by pqwoerituytrueiwoq on 2017-06-09
I found this on the wifi chip that OP has
[https://askubuntu.com/questions/225858/how-do-i-get-a-texas-instruments-acx-111-wireless-card-working](https://askubuntu.com/questions/225858/how-do-i-get-a-texas-instruments-acx-111-wireless-card-working)

---

### Post by yenice on 2017-06-13
Thank you again pqwoerituytrueiwoq

I will try this when I have some free time for it. :-)

---

