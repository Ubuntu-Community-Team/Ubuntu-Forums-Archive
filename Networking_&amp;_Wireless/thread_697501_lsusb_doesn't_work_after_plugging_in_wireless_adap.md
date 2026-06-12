---
title: "lsusb doesn't work after plugging in wireless adapter"
date: 2008-02-15
forum: Networking &amp; Wireless
---

### Post by larcar on 2008-02-15
I have Xubuntu 7.04 installed on an old system with 128MB RAM.  It works well as far as the basic fuctions go but I'm trying to set up a wireless network (I know, it is a huge problem for many of us!).  I do not have internet access on that computer because there are no phone lines nearby.  While it is not an absolute necessity to have internet on that computer it would be nice for updating programs and for transferring files to other computers.

What is happening now is that whenever I plug in my Belkin USB wireless adapter lsusb seems to hang.  What I mean is this: before plugging it in lsusb responds by showing other usb devices but after plugging it in there is no response from lsusb.  Nothing shows.  To get it to respond again I have to reboot the computer.

I noticed this because after installing ndiswrapper the command "ndiswrapper -l" was returning the message about the driver being installed but nothing about the device being present.  I then went to the terminal to take a look at lsusb.  Anyone have any ideas I can try?  Thanks ahead of time for your input.

By the way, I later uninstalled ndiswrapper following the directions for doing so.  After installing it again I get the message in the terminal that the command "ndiswrapper" is not found and that I need to install the program.  However, when I try to install it now it says that it is already installed.  Ideas anyone?

---

### Post by dannyboy79 on 2008-02-15
what belkin usb wifi adpater do you have? if it's the F5D7050 (the one with the rt2571wf chip in it) than you should be following this thread and using native linux drivers.

[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

follow the direction on post #1 but instead of using the tarball from serialmonkey website, use the tarball I uploaded here: [http://ubuntuforums.org/showthread.php?t=400236&page=88](http://ubuntuforums.org/showthread.php?t=400236&page=88)

it's an older version of the rt73 that definitely works with the F5D7050 that has the rt2571wf chipset in it. you can find out which chipset by carefully pulling apart the wifi adapter and reading the chip inside.

---

### Post by larcar on 2008-02-15
Thanks dannyboy79 for your quick reply.  It is a Belkin F5D7050 like you mentioned. However the chip inside says RT2571F (not "wf").  So do I go ahead with the instructions you sent?

Also, do you have any idea about the ndiswrapper problem I mentioned (says it's installed but it can't find the command)?

---

### Post by dannyboy79 on 2008-02-15
i don't know about ndiswrapper, i've been told to use linux native drivers before going the ndiswrapper route. According to that same thread, check out here:
[http://ubuntuforums.org/showthread.php?p=3172544&highlight=RT2571F#post3172544](http://ubuntuforums.org/showthread.php?p=3172544&highlight=RT2571F#post3172544)
and read post #527. according to that you should use the the rt2570 drivers from serialmonkey. again, good luck

---

### Post by larcar on 2008-02-15
Sorry about the question regarding ndiswrapper.  After reading the thread you mentioned in the first post I realized you were not using ndiswrapper at all.  In a little bit I'll try your instructions and will post the results later.  Hopefully they'll be good results.

---

### Post by larcar on 2008-02-15
I followed the instructions you mentioned at [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236).  Everything seemed to go fine until step 13: checking hardware detection with ifconfig -a.  It brought up lo which is to be expected but no wlan0.  Instead it had a rausb0.  Any idea where that came from and what I should do now?  By the way, I did use the rt2570 driver that you recommended since my chip is rt2571f.

Edit: Looking elsewhere on  that thread I see that some versions of the adapter are rausb0 instead of wlan0.  So evidently Xubuntu is reconizing the adapter.  I'm going back to that part of the instructions and trying again.

---

### Post by larcar on 2008-02-15
I'm so close!!!!!  The system is recognizing the Belkin adapter but I'm still not able to connect to the network.  ifconfig -a shows the rausb0.  One problem I had (I think so at least with my VERY limited linux knowledge) was the system was loading another driver (prism54usb) so I added that to the blacklist.  I realized that by looking at dmesg after plugging in the adapter.  Everything I'm looking at looks fine now EXCEPT there no connection to the internet or network.  :(

Tomorrow I'm going back through the instructions and trying again from the beginning since I now have a couple of things taken care of.

The instructions are for a WEP security network but I'm using WAP.  I saw the example of the interfaces file near the bottom and have set up the file exactly the same (substituting "rausb0" for "wlan0").  I don't know if using the WAP changes anything else.  I don't believe so but maybe tomorrow I'll turn off the security and give it a try.

---

### Post by dannyboy79 on 2008-02-15
i don't know if that driver supports WPA so you may want to change to WEP or just make your wifi router only accept your wifi MAC address if your router can do that. my netgear one can. good luck

you'd have to check the serialmonkey website to see if that driver supports WPA.

---

### Post by larcar on 2008-02-18
I've tried using both the rt73 and the rt2570 drivers but get the same results.  In other words, it's still not working.  I've turned off the security on my router to make sure that's not the issue.

Current status:
lsusb shows:
Bus 001 Device 003: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi

ifconfig -a shows (I'm just giving a summary since I'm typing this post on a different computer)
wlan0    UP BROADCAST RUNNING MULTICAST    MTU:1500    Metric:1
wlan0:ava   inet addr:169.254.9.235    Bcast:169.254.255.255     Mask:255.255.0.0
                    UP BROADCAST RUNNING MULTICAST   MTU:1500     Metric:1

iwconfig shows:
the driver and essid correctly
Mode:Managed    Frequency=2.412 GHz    Bit Rate=54 Mb/s
Link Quality=0/100    Signal level:-121 dBm   Noise level:-115 dBm

dmesg shows:
the correct driver and the MAC address being active

Any ideas anyone why I can't connect to the network?  By the way, dannyboy79, I appreciated your ideas and links.  I just still haven't been able to get it to work.

---

### Post by aeiah on 2008-02-18
i have the same card as you on my xubuntu installation (i also have the previous version, which uses the rt73 driver). for the one you have i used the rt2570 driver. is your card seeing your AP? you can do sudo iwlist rausb0 scan to see if its

i think the problem i had was with blacklisting. make sure you havent got the rt73 module and others loaded

---

### Post by larcar on 2008-02-18
> **aeiah said:**
> i have the same card as you on my xubuntu installation (i also have the previous version, which uses the rt73 driver). for the one you have i used the rt2570 driver. is your card seeing your AP? you can do sudo iwlist rausb0 scan to see if its

i think the problem i had was with blacklisting. make sure you havent got the rt73 module and others loaded

Thanks for your response.  Right now I was back to the rt73 driver but I had tried the rt2570 before.  I'll go back to that again and post the results of sudo iwlist rausb0.  Originally the system was loading another driver which I had to blacklist.  I'll be back shortly.

---

### Post by larcar on 2008-02-18
Here's the result from the scan:

rausb0    Scan completed :
                Cell 02 - Address: 00:14:7F:36:78:2B
                Mode:Managed
                ESSID:"SpeedTouchB05911"
                Encryption key:on
                Channel:1

Time to eat.  Afterwards I'll turn off the encryption on the router again and see.

---

### Post by larcar on 2008-02-18
I'm not sure what made the difference because I thoughr I had tried all this before but evidently something was different this time.  As the scan mentioned above shows the hardware is working.  That was great news!  Then I disabled (again) the security on my router and lo and behold, the Belkin adapter connected.:) :) :) :)

I have a question for you, aeiah:
Since you use the same adapter on Xubuntu, what encryption form do you use: WEP or WPA?
And, how is your /etc/network/interfaces file set up?

I've set it up like I've seen elsewhere for the WPA encryption but it is not working.  I don't know if it is supported by the rt2570 driver or not.  I couldn't find information on that on the serialmonkey site.  If I can't use WPA I'll try WEP again but I prefer the former.

---

### Post by aeiah on 2008-02-18
im not at my xubuntu box right now so i cant give you /interfaces info until im back at home, but FYI i just use WEP. the howtos do state that WPA is possible i believe but to be honest, i just cant be bothered to mess around.

you may find it easier to mess around with RutilT, a connection manager for RT cards. see if you can get wpa working in that. you can launch RutilT at startup so it connects automatically if you find you cant use wpa without it.

---

### Post by larcar on 2008-02-18
Fantastic news, at least for me!  I'm writing this post on the machine that's been giving me all the problems.  :)  The thing is I'm not sure what exactly has made the difference.  I appreciate your help dannyboy79 and aeiah.  While no one idea solved my problems somewhere in trying everything it worked.

I blacklisted several drivers as recommend in the forum and one that I found by dmesg that was loading automatically.

I followed instructions to completely uninstall ndiswrapper which I had been trying over and over again to use.

I followed the instrucions at [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236) that dannyboy79 sent me.  But even then things were not working totally.  But at each step it seemed that I was making progress.

The different ideas just led me to keep searching and trying things and finally I'm connected using WEP security.  I wanted to use WPA but that was proving a little too much for me.  I'm sure I'll be back soon with more problems but right now I'm feeling good.  Thanks again!

---

