---
title: "problem wifi"
date: 2014-06-19
forum: Networking &amp; Wireless
---

### Post by flashkoo on 2014-06-19
Hi 
iam new user i nstall ubuntu amd 64 with win 7 on my laptop toshipa i7 
after that i cant hear any sound in speaker and i cant share wifi to another devices 


thanx

---

### Post by flashkoo on 2014-06-20
any help pleas :(

---

### Post by Mvrius on 2014-06-20
You might want to consider being slightly more elaborate, people can't really help you out right now. Proper grammar and sentences would go a long way!

---

### Post by slickymaster on 2014-06-20
@flashkoo

Please take a look at [Suggestions on how to get your support questions answered as quickly as possible]("http://ubuntuforums.org/showthread.php?t=1422475&p=8920811#post8920811")

---

### Post by flashkoo on 2014-06-20
Thank you brother on it 
I am a new user 
Maybe you need this

> root@mohamed--P855:~# uname -r
3.13.0-29-generic




> root@mohamed--P855:~# lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)



> mohamed@mohamed--P855:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC280 Analog [ALC280 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
    Subsystem: Toshiba America Info Systems Device fb30
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at f7f10000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel



> root@mohamed--P855:~# lspci | grep Wireless
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 2200 (rev c4)



---

### Post by flashkoo on 2014-06-21
any help

---

### Post by Vladlenin5000 on 2014-06-21
Thank you for your system information. Now please tell us what the problem(s) is/are in understandable english.

---

### Post by flashkoo on 2014-06-21
> **Vladlenin5000 said:**
> Thank you for your system information. Now please tell us what the problem(s) is/are in understandable english.



HI
u welcome 
first one I can not hear any sound from the speaker
and i can't share Internet via wifi
and evrey time login i see that
> ubuntu 14.4 request for firmware file iwiwifi-2000-5 failed
ubuntu 14.4 request for firmware file iwiwifi-2000-6 failed


and in system setting just i see language support and security printer software & updates and landscape no more

---

### Post by Vladlenin5000 on 2014-06-21
1. Are you sure the correct audio output is selected? In case you haven't noticed yet you have two, the traditional onboard audio plus the one that outputs via HDMI, sitting along with your graphics chip. So, first of all, make sure the internal one is selected (you can test it from within the sound configuration dialog).

2. The WiFi issue is completely different and unrelated (that means you should open different thread in a the appropriate sections of this forum should you need further help for one or the other).
You WiFi device is already supported however the error message seems to indicate it need some proprietary firmware. You might be able to find it, download & install it in one go at System Settings > Software & Updates > Additional Drivers (tab) provided you have an active internet connection, let's say by cable (Ethernet). You need to do this only once.

---

### Post by flashkoo on 2014-06-21
no I don't know how that sorry Iam new user
I do not see the audio icon next to the clock
 and i cant see anything in system setting just language and printer, security,  and softwear & updates
In Additional Drivers no Additional Drivers available

---

### Post by flashkoo on 2014-06-21
Please help experts

---

### Post by Vladlenin5000 on 2014-06-21
Check the audio icon > settings or at System Settings. This ISN'T network related. I suggest you open a a new thread in 'Absolute Beginners' (or Hardware) for the sound issue alone.

Regarding your WiFi issue... Have you checked with an active internet connection (not WiFi, obvioulsy, for the moment)?

---

### Post by flashkoo on 2014-06-21
OK 
about sound I Can't found Sound setting in system setting

no wifi ant i cant enable hotspot

---

### Post by Vladlenin5000 on 2014-06-21
Please follow the forum rules. Namely, DO NOT bump your thread before 24 hours.

I already told you about the audio: Open a new thread in the proper section. This one is called "Network & Wireless" for a reason.

Regarding the WiFi: O B V I O U S L Y you can't enable hotspot if your WiFi isn't working. That's what should be troubleshooted first. Have you already tested whether or not there's additional firmware/drivers offered in the additional drivers tab **when connect by cable (ethernet)?** I already mentioned it and this is the THIRD time I'm asking...

---

### Post by flashkoo on 2014-06-21
Sorry for the inconvenience  
I am now of cable connected (ethernet) but I can not share the network over Wi-Fi by access point 
But she was working after updating something i don't remmber it

---

### Post by Vladlenin5000 on 2014-06-21
The thing you can't remember is EXACTLY what I told you that *could* happen... Is the WiFi working now? No error message after login? If so, now... What do you want to do exactly? Please don't repeat yourself or provide useless information. Instead - after making sure the WiFi is actually working - inform what network connection you want to share and what were the steps you already tried?

---

### Post by flashkoo on 2014-06-21
I trying to creat access point in the laptop to share internet to my iphone
but i cant find network in panel

look to photos

[http://store2.up-00.com/2014-06/1403407023092.png](http://store2.up-00.com/2014-06/1403407023092.png)
[URL="http://store2.up-00.com/2014-06/1403407022841.png"]http://store2.up-00.com/2014-06/1403407022841.png


[https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1308348](https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1308348)
[/URL]

---

### Post by Vladlenin5000 on 2014-06-22
Actually there's a LOT of things missing. Your seems to be incomplete or something happened after.
What Ubuntu version have you installed?

---

### Post by flashkoo on 2014-06-22
Ubuntu 14.04 LTS

Have I reinstall it
Or can be fixed

---

### Post by Vladlenin5000 on 2014-06-22
If there isn't much data and/or software you installed, I strongly suggest you spare 20-30 minutes to reinstall it and then take the necessary precautions if you intend to tweak it like changing themes, etc. Some aren't working properly in newer versions.

---

