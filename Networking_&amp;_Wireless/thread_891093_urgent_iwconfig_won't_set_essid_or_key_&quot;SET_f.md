---
title: "urgent: iwconfig won't set essid or key &quot;SET failed on device eth0&quot;"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by NHansen on 2008-08-15
Ok, so I don't know much about all this wireless stuff, but my internet has been working fine for about a year

I usually connect by using:
sudo ifconfig eth0 up
sudo iwconfig eth0 essid Motorola
sudo iwconfig eth0 key off
sudo dhclient eth0

and it works everytime.
For some reason, when I try to set the essid or key with iwconfig it gives me:
Error for wireless request "Set ESSID" (8B1A) :
SET failed on device eth0 ; Operation not supported.

Then I run sudo iwconfig and under eth0 it says:
no wireless extensions.

What gives? I didn't do anything different! This just came out of the blue. I really know nothing about all this so please help.. I need the internet back up ASAP for work (PS this is my girlfriends laptop connected to the same WiFi connection, so it's working fine)
Please help, I've read the other threads.
I tried killall dhclient and to set it back up, but nothing.
Thanks

P.S. This is Ubuntu 7.10

---

### Post by NHansen on 2008-08-15
I installed wifiradar (USB stick) and it says I am connected to my network (it shows up and everything) but I am not. There is also a question mark on the wifi icon next to the name in wifiRadar...
what is going on here?
And it won't disconnect when I hit the button to. Weird..

---

