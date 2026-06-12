---
title: "Having Wifi Problems, connecting, re-connecting, timing-out.."
date: 2015-03-05
forum: Networking &amp; Wireless
---

### Post by essxiv on 2015-03-05
Hello all, i'm fairly new to Ubuntu Linux OS, from Windows.

None of these problems are problems i'm having with Ubuntu/Linux:

- Wifi will connect when computer is first started, then times out after awhile (10minutes - 2 hours). Then I cannot get back on.. (keeps saying "you're disconnected").
This is for home and for when i'm out at a Starbucks/Library (I do most of my work outside home).

It's becoming a real pain, having to restart my computer every time I want to use the internet. And sometimes when i'm outside of home, I can't even connect in the first place..

Any suggestions? Thanks!

---

### Post by essxiv on 2015-03-08
Still having this problem..

I did try the Sticky:
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by chili555 on 2015-03-08
You gave us a link to the sticky; we need to see the data it produced.> ########## wireless info START ##########

Report from: 08 Mar 2015 22:10 EDT -0400

Booted last: 05 Mar 2015 10:44 EST -0500

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID: Ubuntu
Description:    Ubuntu 14.10
Release:        14.10
Codename:       utopic

##### kernel ############################

Linux 3.13.11-03131111-generic #201411111336 SMP Tue Nov 11 18:37:52 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7
<snip>

---

### Post by essxiv on 2015-03-10
########## wireless info START ##########


Report from: 10 Mar 2015 15:13 EDT -0400


Booted last: 10 Mar 2015 15:08 EDT -0400


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.16.0-31-generic #41~14.04.1-Ubuntu SMP Wed Feb 11 19:30:13 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:b730]
	Kernel driver in use: rtl8723be


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 04f3:2044 Elan Microelectronics Corp. 
Bus 001 Device 006: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 005: ID 048d:8350 Integrated Technology Express, Inc. 
Bus 001 Device 004: ID 058f:6259 Alcor Micro Corp. 
Bus 001 Device 003: ID 04f2:b446 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0930:0222 Toshiba Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



Is this what you need? I can't paste the whole wireless_info.txt file, it gives me an error for too many something.

And what programming language is the script in? Java or Python?

---

### Post by chili555 on 2015-03-10
> **essxiv said:**
> 

Is this what you need? I can't paste the whole wireless_info.txt file, it gives me an error for too many something.

And what programming language is the script in? Java or Python?I believe it is simply a shell script; a long and complicated one for sure!

Please paste it here and let us have the link in your reply: [http://paste.ubuntu.com](http://paste.ubuntu.com)

Thanks.

---

### Post by essxiv on 2015-03-10
[http://paste.ubuntu.com/10576692/](http://paste.ubuntu.com/10576692/)

---

### Post by chili555 on 2015-03-10
Wow! Where do I start?

First, this is the access point to which you are attached:> wlan0     Scan completed :
          Cell 01 - Address: <MAC 'attwifi' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:off
                    ESSID:"[COLOR="#FF0000"]attwifi[/COLOR]"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000133ecc43d876
                    Extra: Last beacon: 44ms agoDo you see what kind of encryption it has? No?? Neither do I!!! That means that key-strokes, passwords, banking transactions, etc. are going over the airwaves unencrypted! That is beyond dangerous. Please stop everything and change the encryption to WPA2-AES. Please do so now.

Second, there are *two * access points with the same name. I am quite confident that part of the problem is that your device is trying to roam among the two, disconnecting and reconnecting along the way. I suggest you change the ESSID on yours to something different, attwifi2 or essxiv-wifi or some such.

Then reboot the router and tell us if stability is improved.

In the meantime, please get encryption!

---

### Post by essxiv on 2015-03-10
> **chili555 said:**
> Wow! Where do I start?

First, this is the access point to which you are attached:Do you see what kind of encryption it has? No?? Neither do I!!! That means that key-strokes, passwords, banking transactions, etc. are going over the airwaves unencrypted! That is beyond dangerous. Please stop everything and change the encryption to WPA2-AES. Please do so now.

Second, there are *two * access points with the same name. I am quite confident that part of the problem is that your device is trying to roam among the two, disconnecting and reconnecting along the way. I suggest you change the ESSID on yours to something different, attwifi2 or essxiv-wifi or some such.

Then reboot the router and tell us if stability is improved.

In the meantime, please get encryption!

1. Could you give me a step-by-step process of using an encryption?

2. I'm not using a Router, i'm usually out at a local starbacks or library, so I can't do anything on that end. Suggestions?

---

### Post by chili555 on 2015-03-10
So *attwifi* is a public wireless? That's scary.

About the only thing you can try is to bind the wireless to a specific MAC address. Here is the process: [http://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](http://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)

---

### Post by essxiv on 2015-03-11
> **chili555 said:**
> So *attwifi* is a public wireless? That's scary.

About the only thing you can try is to bind the wireless to a specific MAC address. Here is the process: [http://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](http://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)

Yup, it's public for all starbuck customers lol.

Anyhow, the binding to the specific MAC address, I will use that every time i'm outside of home, and hopefully I don't disconnect! Seeing how you can save the BSSID and it applies for future connections to that wireless network!
Thanks for the help man, if I have any other problems, I will post in this topic.

---

### Post by essxiv on 2015-03-17
So now i'm actually traveling for work, and I still cannot seem to stay connected to one single Wi-Fi Network when i'm out and about (Starbucks, Public WiFi places). And Yes this is only happening on LINUX Ubuntu. 
I still can initially connect when I first start my computer, but after about 5-15 minutes, it times out, still says i'm connected, and my internet doesn't work at all, unless I restart my whole computer.
I've been using my Windows 8.1 OS, but I really need to start only using strictly Linux for my Programming purposes... the specific MAC address to "edit connections", doesn't seem to work..

Any other suggestions? I've tried binding the MAC address, but it doesn't seem to have any effect when i'm out and about.

---

### Post by essxiv on 2015-03-21
Bump a Hump.

---

### Post by chili555 on 2015-03-26
> **essxiv said:**
> Bump a Hump.Sorry for the delay; I was out of the country for a while.

Let's try a driver parameter or two. From a terminal:```
sudo -i
echo "options rtl8723be swenc=1 ips=N"  >  /etc/modprobe.d/rtl8723be.conf
exit
```Reboot and let us have a report.

---

### Post by essxiv on 2015-04-03
> **chili555 said:**
> Sorry for the delay; I was out of the country for a while.

Let's try a driver parameter or two. From a terminal:```
sudo -i
echo "options rtl8723be swenc=1 ips=N"  >  /etc/modprobe.d/rtl8723be.conf
exit
```Reboot and let us have a report.

Well, I first off wanna say thanks for all your help over the past 2 months.

I have found a solution to this problem. I think I also found the reason why its happening.

I initially tried to switch my Network Manager to a Network Manager called: WCID Network Manager. This was not the problem though.
I then tried to install/upgrade my Kernel of my machine, which had SOME type of effect, but not an entire fix.

My wireless still times out once in a awhile in both public locations and at home, but the solution I found around this problem is two things:



(1) When my connection times out, it will prompt me for the Password to the Network i'm trying to connect to. EVEN WHEN I put the password in, it will try to connect, time-out, then ask me for the Password again and again, like a never ending loop.

(1-Solution) What you need to do is open your Terminal and type:
~
sudo rfkill block all
sudo rfkill unblock all
rfkill list all
~
This will BLOCK, then UNBLOCK the wifi, and yes I did find this on one of your previous posts chili555!
This will fix the wifi, and allow it to re-connect until the error happens again, but it definitely is a lot more efficient than restarting your WHOLE system!!!!



(2) The other Wifi problem I am running into is usually in a public place (Starbucks). The Wifi will disconnect, and try to re-connect on it's own. Which it never does, but unlike the 1st problem, it doesn't prompt you for the password. Just a straight disconnect and trying to re-connect.

(2-Solution) I did try using the CODE above for this problem, but it seemed to have no effect, thus being a completely different problem! The solution to this without having to restart your computer is also inputting a CODE into your terminal:
~
rmmod rtl8723be
rmmod rtl_pci
rmmod btcoexist
rmmod rtlwifi
modprobe -a rtl8723be
~



This has been effective for me, at least. Even though i'm not too sure what this does, my instructor for programming created/researched and saved both of these pieces of CODE as aliases in my Terminal!

Hopefully this will help others with my same exactly problem in the future!
Also, chili555, if you wanna see anything on my system and you think you can make my life even easier, i'd be more than happy to send you whatever you'd like!

Cheers!

---

### Post by changingstate on 2015-04-04
You said you'd tried upgrading your kernel. Did you have a go with the bleeding edge drivers here?  [https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new)  There's a similar issue reported on stackexchange with your card where 3.16 and github repo driver fixed things: [http://unix.stackexchange.com/questions/170012/rtl8723be-realtek-wifi-card-driver-not-working-on-ubuntu-14-04](http://unix.stackexchange.com/questions/170012/rtl8723be-realtek-wifi-card-driver-not-working-on-ubuntu-14-04)

---

