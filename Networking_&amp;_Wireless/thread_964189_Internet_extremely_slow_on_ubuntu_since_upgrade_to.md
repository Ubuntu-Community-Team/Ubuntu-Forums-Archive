---
title: "Internet extremely slow on ubuntu since upgrade to 8.10"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by Amarsingh0793 on 2008-10-30
Hi. Before (Ubuntu 8.04/Vista), I had speeds of 900kb per second. Now, ever since I upgraded to 8.10, I am getting ridiculous speeds like 1.2kb per second. The internet works as it should work in Windows - so what's wrong in Ubuntu? I have Sky Broadband and I have an Ethernet connection. Please Help me - it's really urgent!

---

### Post by coolbrook on 2008-10-30
I've noticed a slow down as well too.  I have a Netgear WG111v2 that's working out of the box on Intrepid (RTL8187 driver) but there's a lot of lag and slow transfer.  I tried ndiswrapper and Netgear's Win 98 driver, but that won't even connect to my LAN.  The network configuration has changed from the Roaming vs. Manual options I'm accustomed to seeing.  Mine's a clean install.

---

### Post by Amarsingh0793 on 2008-10-30
Synaptic downloads at 0.2kb per second - it's shocking! Worse than Dial-Up! Try disabling IPV6 - it sort of speeded it up a bit.

---

### Post by Amarsingh0793 on 2008-10-30
Now it's moving down to Bytes!!! Someone help please! #-o

---

### Post by benign on 2008-10-30
Perhaps you are misattributing the cause of the slow down. It doesn't necessarily have to be the upgrade. Try doing a broadband speed test here: [http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/)

---

### Post by liveB on 2008-10-30
Thanks for the test link.  It confirms that my internet connection "should" run at almost 700kbps down and 1.5MBps up (test results).  Actual throughput speeds currently in the single bytes per second (makes video REAL boring to watch).  Note that this really degraded this week and I suspect it's an update to Ubuntu conflicting internally.

System: ASUS P5NE-SLI, Intell C2 Quad with 4GB 800 MHZ OCZ memory.  NVidia 8600XXX vid. on-board sound and Ethernet connected to cable modem through router.

I'm a medium-rare when it comes to Linux so am watching this thread for ideas and more info...

---

### Post by lisati on 2008-10-30
> **benign said:**
> Perhaps you are misattributing the cause of the slow down. It doesn't necessarily have to be the upgrade. Try doing a broadband speed test here: [http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/)

Interesting.... I tried it and found the results from the Seattle server similar to the results from [http://www.consumerspeedtest.org.nz/](http://www.consumerspeedtest.org.nz/) which also uses a test from Ookla

---

### Post by dhlee528 on 2008-10-30
I have same problem I just install 8.10 using Wubi
Actual web browsing speed isn't too bad but 
synaptic manager and other things are extremely slow

---

### Post by lostpunisher on 2008-11-03
Yeah same problem here. This was honestly the worst time for ubuntu to do this to me, as my desktop just died. (Motherboard) and all I have left is my Linux dedicated laptop. Browsing the web sucks. I think I'm going to upgrade to vista until the next release, at least I can watch youTube then. :(

---

### Post by jasonbrisbane on 2008-11-03
Upghrading will play with the /etc/hosts file so you'll need to comment out the IPv6 info and restart try again.

I found the same delay when openning a terminal window... (same issue)

---

### Post by jasonbrisbane on 2008-11-03
Upgrading will play with the /etc/hosts file so you'll need to comment out the IPv6 info and restart try again.

I found the same delay when openning a terminal window... (same issue)

---

### Post by imageek on 2008-11-03
Helping my buddy out, we noticed his MTU kept being set at some drastically low number. sudo ifconfig eth0 mtu 1500 worked to fix it. Needs to be applied at each reboot

---

### Post by Gilanel on 2008-11-04
Same problem here
I have rtl8185 based card.
On hardy I've used drivers form this page
[http://www.willdaniels.co.uk/articles/10-howto/12-r8180-hardy]("http://www.willdaniels.co.uk/articles/10-howto/12-r8180-hardy")
It worked perfectly 
But now drivers are already but they practically ain't working.

Don't know if they will work in Intrepid, kernel is 2.6.27 and driver is for 2.6.24.

And how I should do 'blacklist' existing driver

---

### Post by Amarsingh0793 on 2008-11-04
Well, my connection seems to be much better than before ever since an update. I haveto say -ubuntu is amazing! The updates are very effective :). And the new wireless support is awesome. Keep it up canonical!

---

### Post by Kyront on 2008-11-18
Concerning onboard-wireless running with RTL8187, the following seems to have improved my connection dramatically:
```
$ sudo iwconfig wlan0 rate 5.5M
```

Also note the following links:
Kernel bugs: [http://bugzilla.kernel.org/show_bug.cgi?id=9143](http://bugzilla.kernel.org/show_bug.cgi?id=9143)
Ubuntu bugs: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/182473](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/182473)
Taken from the latter (not tested): [http://zenzike.blogspot.com/2008/11/wireless-woes.html](http://zenzike.blogspot.com/2008/11/wireless-woes.html)

and taken from the a former a script that is reported to reset the chip on failure without restarting:
```
#!/bin/bash
sudo iwconfig wlan0 ap off
sudo ifconfig wlan0 down
sleep 2
sudo ifconfig wlan0 up
sudo iwconfig wlan0 rate 11M fixed
sudo iwconfig wlan0 essid "MyNetworkEssid"
sudo iwconfig wlan0 ap auto
sleep 5
sudo dhcpcd wlan0

```

---

