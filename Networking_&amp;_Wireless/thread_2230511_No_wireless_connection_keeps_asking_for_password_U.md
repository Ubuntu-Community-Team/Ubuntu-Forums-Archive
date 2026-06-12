---
title: "No wireless connection keeps asking for password Ubuntu 14.04"
date: 2014-06-19
forum: Networking &amp; Wireless
---

### Post by mcfardo907 on 2014-06-19
I'll stick with 12.04 until this bug gets fixed.
:mad:
I cannot get my wifi to connect on my Samsung NB30 plus netbook. It keeps asking me for a password everytime I try to connect. I put in the proper password and then it asks me for the password again. I am able to connect to my wifi with my other devices. I've been banging my head against the wall since yesterday. My wireless router is a Netgear WTG24v3. It has the latest firmware on it. I did manage to connect to an unsecured Time Warner router. My theory is that 14.04 or the kernel that comes with it has broken WPA or does not act and play well with older Netgear routers. Heres the infor the wireless adapter.

Here the wireless script info

[http://grizzly907la.tumblr.com/post/89294981028/wireless-info-start](http://grizzly907la.tumblr.com/post/89294981028/wireless-info-start)


```
 description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: 78:e4:00:5d:84:4b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.13.0-29-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:f0100000-f010ffff
```

I know that my wireless card has worked with previous versions on Ubuntu.

---

### Post by squakie on 2014-06-21
All it takes is one failed attempt with a mistyped password and for me it always does this until I do the following:

- open network manager
- edit connections
- remove the entry for the network you are trying to connect to

I don't know if that will help you or not.  It may also be a driver issue.  Have you let addiional drivers do it's thing and see if a different driver appears?

I also found this in a thread about your adapter on askubuntu - don't know if it would help or not:

> 
Create a new file /etc/modprobe.d/ath9k.conf:
sudo nano /etc/modprobe.d/ath9k.conf
Add the following line to it:
options ath9k nohwcrypt=1

Save the file and reboot.

---

### Post by mcfardo907 on 2014-06-21
I'll go ahead and it give it a try. Thanks for replying. I appreciate it!!

---

### Post by mcfardo907 on 2014-06-21
It didn't work. Its still asking me for a password. I think the people that develop the Linux kernel broke 802.11 or WPA. Bad Tux, bad Tux, bad!!!!! Regression sucks. I love Linux but this kind of crap keeps average users from wanting to make the switch. Thank again. At least you replied and for that I a greatful.

---

### Post by squakie on 2014-06-21
Myself and thousands more are running 802.11 b, g or n and with WPA2. 

I don't know why you think it's a kernel problem.  A driver problem?  Possibly.

Not playing well with the router?  How???  If the router supports 802.11 in whatever speed you are using, and the router supports WPA, it should work.  There are a few things that can cause problems, one of those being mixed mode.  Set your router to WPA2 TKIP  *only* - don't allow WEP, etc., just WPA2.  You may also want to set it to a single channel like 11.  None of these are Ubuntu or driver problems.

Making comments like that are not a good way to expect help.

---

### Post by mcfardo907 on 2014-06-22
I understand what you're saying however I and others have observed that this latest kernel has broken wireless for many people. If people don't want to respond then that's their problem. I've been building and fixing computers for 21 years. I worked professionally for seven of those years. I know how to draw correlations and put two and two together.

I've done everything you have suggested. I've updated the firmware on the router. I've used those various settings to no avail. I've even tried other Linux distro's that have this current kernel and all have had the same problem in regards to the wifi on my netbook. My smartphone and tablet connect to my wifi network without a hitch. My netbook connected to my wifi network when I had ubuntu 12.04 on it with no problem. I'll reinstall 12.04 on it. Thanks again for helping out.

---

### Post by squakie on 2014-06-22
If that's how you feel, nobody here will able to convince you otherwise.  My suggestions have been made.  And BTW - try almost 30 years as a systems programmer, building PC's on the side during the last 30 years for countless people - as have many, many, many people here.

---

### Post by QIII on 2014-06-22
If you would stop wetting on each other's shoes, it would be greatly appreciated.

I'll not close the thread just yet, since the problem has not been resolved.  However, if a more polite approach is not taken, the thread will be closed.

mcfardo907:  Please remember that this is a forum comprised of volunteers who come here as they have time.  That there have not been more responses is not a measure of the community's willingness to help so much as an indication that the person(s) with just the right answer have not seen the thread yet.

Please don't bang your head against a wall for a day before asking for help.  And if there has been no answer to your query in 24 hours, feel free to bump the thread (add a response with the word "bump").

Did you mean to mark the thread "Solved"?  If the problem is not solved, a sure way to make sure nobody responds is to mark it solved.

---

### Post by jeremy31 on 2014-06-22
Does ```
iw reg get
``` and the REGDOMAIN from ```
cat /etc/default/crda | grep REGDOMAIN=
``` match?  Have you tried a newer kernel?

---

### Post by mcfardo907 on 2014-06-22
I am not upset with you and I do appreciate your help. I did as you suggested. It didn't work. I've talk to other people outside of this forum and they are having similar problems with distro's that are using this latest kernel. I don't have a beef with you. Why is it such a big deal to say that there might be a problem with this latex Kernel as it pertains to wifi? I just want the problem fixed.

---

### Post by mcfardo907 on 2014-06-22
Don't get me wrong I appreciate the help and I am not upset with the people othering it. How I am wetting other peoples shoes though? I didn't insult anyone, and I don't mean to insult anyone. I am frustrated. I tried to figure this out on my own by browsing similar topics. I came here as a last resort. I like to try to find a solution on my own before asking for help. Why do people get upset when I say "it might be a problem with the kernel?" I apologize if I offended anyone and misinterpreted myself. I'll go ahead and leave the topic open.

---

### Post by mcfardo907 on 2014-06-22
Thank you for helping me out. I got the following results.
```
iw reg get 
country US:    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)
```

```
 cat /etc/default/crda | grep REGDOMAIN=
REGDOMAIN=
```

---

### Post by jeremy31 on 2014-06-22
> **mcfardo907 said:**
> Thank you for helping me out. I got the following results.
```
iw reg get 
country US:    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)
```

```
 cat /etc/default/crda | grep REGDOMAIN=
REGDOMAIN=
```

```
sudo gedit /etc/default/crda
``` and make it REGDOMAIN=US and save if you are in the US, close gedit and reboot

And here is another one I hope works on your machine ```
for parameter in /sys/module/ath9k/parameters/*; do echo $parameter; cat $parameter; done
```

---

### Post by mcfardo907 on 2014-06-22
I set the domain for US. That didn't work. I tried to edit the config files and the system wouldn't allow me to save the files, even as root. Thanks again for helping out. I know there has to be a solution out there.

---

### Post by jeremy31 on 2014-06-23
> **mcfardo907 said:**
> I set the domain for US. That didn't work. I tried to edit the config files and the system wouldn't allow me to save the files, even as root. Thanks again for helping out. I know there has to be a solution out there.

Have you checked to see if you have the latest version of linux-firmware installed.  Strange that it won't allow you to change the crda file as root.  Have you tried WPA2 on your router?

It just might be that the router is too old or needs its firmware updated.  I updated the OS on my android phone once and had similar issues until I switched routers

---

### Post by mcfardo907 on 2014-06-23
I don't think my router has WPA 2, but I can check and I did upgrade the firmware on my router to the most current version. I'll do a firmware upgrade on the wifi card itself, and get back to you. My android smartphone and kindle fire both connect without a hitch and I've had both of them less than a year.

---

