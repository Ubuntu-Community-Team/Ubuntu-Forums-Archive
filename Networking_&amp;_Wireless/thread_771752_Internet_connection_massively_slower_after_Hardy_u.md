---
title: "Internet connection massively slower after Hardy upgrade"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by NICU on 2008-04-27
Hi, I upgraded to Hardy a few days ago, and I've noticed my internet connection speeds have been massively reduced.  I have a ```
Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

```network card.  The few hours before upgrading I downloaded the torrents for Hardy iso's and they downloaded around 800kbps, after the upgrade my max download speed has been 30kbps.  Any clues?

---

### Post by NWcustomcode on 2008-04-27
> **NICU said:**
> Hi, I upgraded to Hardy a few days ago, and I've noticed my internet connection speeds have been massively reduced.  I have a ```
Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

```network card.  The few hours before upgrading I downloaded the torrents for Hardy iso's and they downloaded around 800kbps, after the upgrade my max download speed has been 30kbps.  Any clues?


Open firefox and type about:config type ipv in the filter box.

Try and set network.dns.disableIPv6 to TRUE

---

### Post by Keets on 2008-04-28
You can try this; it worked for me. 

"sudo iwconfig wlan0 rate 54M" 

* From my understanding, the Bit Rate on the rt2500 somehow defaults to 1Mb/s after upgrade. So, the 54M sets it to what it should be. Had the exact same problems you described. Good luck...

P.S. Unfortunately, it doesn't "stick", so you have to enter that command every time you boot up.

---

### Post by NICU on 2008-04-28
Thanks Keets that seemed to work for me.  It was always set to 1MB/s by default and manually setting the rate to 54M works great.

---

### Post by studentz on 2008-04-30
" sudo iwconfig wlan0 rate 54M "
works for me too.

Thanks

---

### Post by ushills on 2008-04-30
Also try adding the following to /etc/modprobe.d/blacklist

blacklist ipv6

this should speed think up nicely,

also test your actual speed at [www.speedtest.net](www.speedtest.net), although mine showed 1mbps in the settings i was actually getting 6Mbps when tested.

---

### Post by zdude on 2008-04-30
Anyone any ideas for me? I was getting about 6000kb/s and now I am getting 95kb/s my upload is 4 times faster @ 400kb/s which is a little closer to what I got before. I have an rt73 and used the new hardy driver and it was the same as a newly compiled serialmonkey driver. I disabled ivp6 - I tested a windows machine sitting next to mine, same driver and is getting about 6000+kb/s. 60 times SLOWER tells me something is amiss. This was on a clean install.
This is also slow with synaptics as well - where I first noticed it.

Anyone an idea?

---

### Post by ushills on 2008-05-01
Zdude, did you try blacklisting ipv6

also try adding the following to your /etc/networking/interfaces, under the wlan0 section

```
iwconfig wlan0 rate 54M
```

---

### Post by Greencoat1982 on 2008-05-01
Hello, I've just moved back to Ubuntu(hardy) and am looking for ways to optimize my connection to the internet. I'm running a 2wire 2701hg-b router, I know 2wire is notorious with Ubuntu, but its the hardware I have. I would greatly appreciate any suggestions.

---

### Post by zdude on 2008-05-01
> **ushills said:**
> Zdude, did you try blacklisting ipv6

also try adding the following to your /etc/networking/interfaces, under the wlan0 section

```
iwconfig wlan0 rate 54M
```

Yes, I tried all those and more! My iwconfig was showing 54Mb/s to begin with but I tried anyway. I tried standard install rt73usb driver - same speed, then I compiled the serialmoney rt73 - same speed. Biggest problem was my wireless was killing all the other wireless units as well! I finally restored up 7.10 backup and I am now running at 5000Kb/s down and 485Kb/s up. I was only able to get 95Kb/s down and 400Kb/s up while running Hardy. I don't think it is the serialmonkey drive, I recompiled it under 7.10 and it performs perfectly. What is strange is I can download at full speed with 7.10 and other users on my wireless are not affected at all. With Hardy, it would literally make the wireless net crawl for all the users and the best anyone could get is ~100Kb/s - weird! 
I am back to sitting out on 8.04 for awhile - looks like a kernel issues to me.
BTW, thanks for responding!

---

### Post by kevdog on 2008-05-01
Can you post your kernel version

uname -r

I think Hardy's kernel has been fixed with newer kernel upgrades (however this calls for compiling a new kernel).

---

### Post by zdude on 2008-05-01
> **kevdog said:**
> Can you post your kernel version

uname -r

I think Hardy's kernel has been fixed with newer kernel upgrades (however this calls for compiling a new kernel).

I was running 2.6.24-16-generic. I had thought it was a kernel issue but I wasn't sure which one to try. Plus, my download speed was so pathetic and it was causing other user's dnld speeds to be equally miserable I had to switch out. Do you know which version it might be fixed in?

---

