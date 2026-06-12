---
title: "Super slow Internet connection for only Chrome &amp; Firefox in Xubuntu 10.04"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by adamsiddhi on 2010-06-08
Hello. 

**Bad News**
I just installed Xubuntu 10.04 yestarday and all is well except that my wired Ethernet connection is super ultra slow. It is so slow that high traffic sites will not even load and low traffic sites will take 5 minutes or longer to load. I guess any page with lots of CSS styling and scripting will have a hard time loading or not load at all. 

**Good News**
Text based pages seem to load up fairly quickly though. Google & Gmail seem to load fairly fast. Running a search is fast too. 

Xchat seems to work just fine as well as software downloading from the updater. Yesterday it wanted to download an over 80MB package of software updates. I accepted it and it downloaded the updates fairly fast. Well as fast as I am used to on my other machine with a healthy connection. 

**Solution Search**
I first tried to make my connection faster by following [[COLOR="Indigo"]**this tutorial**[/COLOR]]("http://wojox.homelinux.org/?p=46") to Disable IPv6 in GRUB. This did not help at all. 

I have read elsewhere and discovered that maybe I need to reinstall my Ethernet device driver so I ran the **dmesg |grep eth0** command in Terminal (to see info on my Ethernet connection & device) and this is what I got back:

[INDENT][    4.696577] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:c0:9f:65:4e:45
[   20.816185] b44: eth0: Link is up at 100 Mbps, full duplex.
[   20.816190] b44: eth0: Flow control is off for TX and off for RX.
[ 4575.499137] b44: eth0: powering down PHY
[ 4602.000202] b44: eth0: Link is up at 100 Mbps, full duplex.
[ 4602.000207] b44: eth0: Flow control is off for TX and off for RX.
[/INDENT]
So a few questions....

[LIST]
[*]What should I do now? 
[*]Does the above info about my Ethernet device & connection look right and healthy?
[*]If I have to update my Ethernet driver, how would I do that?
[/LIST]

**[COLOR="Red"]UPDATE[/COLOR]**
[COLOR="Red"]I decided to run a internet connection speed test from Chrome. First though, I had to download Flash Player. Actually I never got to downloading Flash Player since Adobe's website is not loading properly. All the CSS is missing and I do not see a download link. But while I was waiting I decided to fire up **Transmission **(torrent client) and download some audio books from ClearBits. At the same time I fired up **System Monitor** to see what was going on with my connection. 

So it turns out that as I was waiting for Adobe and three Internet speed test sites to finish loading, **System Monitor** was showing that I was only receiving around **1** to **2** KiB/s at any given moment. Then when I started downloading audio books with **Transmission**, the **Network History** section with in **System Monito**r was showing that I was downloading at a healthy speed in between **120** to **230** KiB/s. And like I said before there was no problem for **Update Manager** to quickly download that 80mb package yesterday and Xchat runs fast too. So whatever the issue is has to do with browsers in general: Firefox and Chrome.

I was able to download and install Flash Player via Terminal and test my connection speed from speedtest.com.  The results are:

DOWNLOAD: **1.95Mb/S**
UPLOAD: **0.25Mb/S**

These results are healthy and the same as my other computer's connection but Chrome and Firefox refuse to download websites at that speed. Also, when I run the speed test, the **Network History** graph shows that I have downloaded at 1.95Mb/s. Still, when I try to go to Twitter, Engadget, Facebook or any other high traffic site, I **Network History** shows that I am receiving under 1 KiB/s. Very strange.
[/COLOR] 



Thank you,
:adam

---

### Post by XubuRoxMySox on 2010-06-08
First of all, there's no need to go to a web site to download most software! Use the Software Center and get it from the repositories!

Second, ipv6 really slows Firefox down. You can disable it right in Firefox by typing **about:config** in the location bar (the little window where you would type in a URL). Click on the "I'll be careful, I promise" button and scroll down the list of stuff until you find the entry for **network.dns.disableIpv6**. Double-click on that line of text. It will turn it **bold** and change the value from "false" to "true."

That should hugely speed things up in Firefox for you.

Let us know... and don't forget to mark your post as SOLVED if it works!

Hoping I've helped,
Robin

---

### Post by adamsiddhi on 2010-06-08
> **dixiedancer said:**
> First of all, there's no need to go to a web site to download most software! Use the Software Center and get it from the repositories!

Second, ipv6 really slows Firefox down. You can disable it right in Firefox by typing **about:config** in the location bar (the little window where you would type in a URL). Click on the "I'll be careful, I promise" button and scroll down the list of stuff until you find the entry for **network.dns.disableIpv6**. Double-click on that line of text. It will turn it **bold** and change the value from "false" to "true."

That should hugely speed things up in Firefox for you.

Let us know... and don't forget to mark your post as SOLVED if it works!

Hoping I've helped,
Robin

Hi Robin, 

I had mentioned in my post that I originally tried that method and it did not work. You must have overlooked it. Additionally, I had stated that I have an ultra slow connection with ***[COLOR="Red"]both[/COLOR]* ****Chrome** and **Firefox**. 

I will state again that **Transmission**, **Update Manager** and **Xchat** are all running at a quick and healthy speed. So I must conclude that there is something preventing both **Chrome** and **Firefox** from making a strong solid connection to the Internet. It's a complete mystery to me why this is happening to the browsers and not the other software I had mentioned.

Regards,
:adam

---

### Post by 4Orbs on 2010-06-08
It sounds like you only need to get your java, flash, multimedia stuff sorted out, and the best way to do that is to follow the steps [ON THIS HOW-TO]("http://ubuntuforums.org/showthread.php?t=766683").

EDIT: And you also might want to activate the proprietary driver for you graphics card (if there is one available for your card) by going to Applications>> System>> Hardware Drivers in the Xubuntu menu.

---

### Post by adamsiddhi on 2010-06-09
> **4Orbs said:**
> It sounds like you only need to get your java, flash, multimedia stuff sorted out, and the best way to do that is to follow the steps [ON THIS HOW-TO]("http://ubuntuforums.org/showthread.php?t=766683").

EDIT: And you also might want to activate the proprietary driver for you graphics card (if there is one available for your card) by going to Applications>> System>> Hardware Drivers in the Xubuntu menu.

The How-To link you sent me has soo much stuff in it. Which ones should I do? I do not want to install lots of unnecessary applications and bloat my system.

I went to Applications >> System >> Hardware Drivers and it says:
[COLOR="DarkGreen"][INDENT]**No proprietary drivers are in use on this system.**[/INDENT][/COLOR]
What does having a proprietery driver for my graphic card have naything to do with Firefox and Chrome's super slow connection speed? I can view PDFs and run GIMP fine so doesn't that mean my graphics card is recognized and fine?

Thanks,
:adam

---

### Post by 4Orbs on 2010-06-09
The websites on which you are experiencing slow loading pages all use java, flash and multimedia bits. The proprietary driver might not make pages load any faster, but it can help by making flash and video images render more smoothly. The flash and java plugins for the browsers can make a significant improvement in speedy loading of webpages. If you prefer not to mess with installing these things... that's ok.

---

### Post by adamsiddhi on 2010-06-09
> **4Orbs said:**
> The websites on which you are experiencing slow loading pages all use java, flash and multimedia bits. The proprietary driver might not make pages load any faster, but it can help by making flash and video images render more smoothly. The flash and java plugins for the browsers can make a significant improvement in speedy loading of webpages. If you prefer not to mess with installing these things... that's ok.

I see but I doubt that applies to what I am dealing with since Twitter (which does not use Java or Flash)does not even load. 

I found out that Chrome and Firefox both use port 80. Me and a friend both suspect that the issue is with port 80 but still have to search deeper. I think this is a deep issue, maybe even a bug with Ubuntu. We will see.

---

### Post by nishant.thomas on 2010-06-09
Have you tried opera web browser yet? Try if that works.

---

### Post by 4Orbs on 2010-06-09
Did you install the Chromium browser from the Ubuntu repository, or did you install the Chrome browser by downloading it from Google? I have installed Chromium and it runs better on Xubuntu than Chrome does on XP.

Also, how have you installed Xubuntu? Dual boot, Wubi, Virtual Machine, or only OS on the hdd?

---

### Post by adamsiddhi on 2010-06-09
> **4Orbs said:**
> Did you install the Chromium browser from the Ubuntu repository, or did you install the Chrome browser by downloading it from Google? I have installed Chromium and it runs better on Xubuntu than Chrome does on XP.

Also, how have you installed Xubuntu? Dual boot, Wubi, Virtual Machine, or only OS on the hdd?

i installed Xubuntu 10.04 over my old XP installation so it is the only OS on the HD. I found out that HTTP and HTTPS use Port 80 and 81. Since HTTP and HTTPS are the language of browsers, there must be an issue with my Port 80 and 81. How to fix that is another problem. 

So I doubt Chromium will solve the problem. Besides even if it does work faster than Chrome, I will still need to be able to use Firefox, Chrome and other browsers to check my web sites I plan on developing. So I really need a true fix to this problem.

---

### Post by adamsiddhi on 2010-06-09
> **nishant.thomas said:**
> Have you tried opera web browser yet? Try if that works.

Still I will need to use all browsers since I am a web designer. In any case I downloaded and extracted Opera from Terminal and it is just as slow as Firefox and Chrome. What ever port HTTP and HTTPS is running through is probably the problem. I heard it was Port 80 and 81 but now I just heard 443. I am very confused at this point.

---

### Post by adamsiddhi on 2010-06-09
I fixed my problem by following this tutorial:

[https://store.opendns.com/setup/device/ubuntu/](https://store.opendns.com/setup/device/ubuntu/)

YES!!:guitar:

---

