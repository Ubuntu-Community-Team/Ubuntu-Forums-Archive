---
title: "3 Broadband, huawei E220"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by TDFlanders on 2008-08-21
Hi, I have tried to reply to my own message from 3 weeks ago since no one else did, but I don't have the admin privileges? Anyway, my problem is solved now. I have upgraded to Intrepid. I installed some new stuff, amongst which USBprog and D-feet D-bus debugger. I don't actually recall what I have done with them. I suspect though that you could get your modem to work by downloading USBprog and click on download all in cache, and a firmware installed message will appear. Also since I did not get a full upgrade to succeed with update-manager -d, I abused my terminal relentlessly with apt-get update upgrade dist-upgrade build-dep and so on so fort. Also USBprog is not available under hardy. But you can download it:

USBprog
[http://developer.berlios.de/projects/usbprog/](http://developer.berlios.de/projects/usbprog/)

and also:

D-Feet D-Bus Debugger
[http://hosted.fedoraproject.org/projects/d-feet](http://hosted.fedoraproject.org/projects/d-feet)

No warranty, but it worked for me. None of the shell scripts did.

---

### Post by TDFlanders on 2008-08-22
Come to think of it, this is probably the firmware that will be downloaded. So if you install it through Windows Wireless Drivers? I have no idea if it works, but that package is available on Hardy.

[http://www.huawei.com/mobileweb/en/doc/list.do?type=-1&id=736](http://www.huawei.com/mobileweb/en/doc/list.do?type=-1&id=736)

---

### Post by cpetercarter on 2008-08-22
You don't say whether you have looked at [this thread]("http://ubuntuforums.org/showthread.php?t=843973").

The method of connection using wvdial and the Gnome Dial-up Tool, explained in the first posting in the thread, seems to work well for many Hardy users. I found no problems in configuring my E220 using these instructions - I am in fact connected using my E220 at the moment.

The alternative, which I have not tried, is to use Network Manager 0.7. This is (I think) bundled with Intrepid, and using it the E220 should just work.

I trust you sorted out your passport, driving licence etc problems. Sorry, I did not see your original post at the time, or I would have tried to help.

---

### Post by TDFlanders on 2008-08-22
Hi there,

yes I certainly did check out that thread, as well as many others, from Germany, Austria and south Africa. They did not work unfortunately. They ask me to change the PIN of the SIM-card, but I was never told the PIN. Init string 2 is from a German or Austrian provider. I don't know where to put in the APN (3 internet), and should I leave this "" open or replace it with "guest"? Anyway, I followed the scripts in the thread you posted to the letter but it doesn't work. I don't know how to interpret all minicom, wvdial, gnome-ppp or telinit and such spit out and what to use as init string 2, should it be with or without spaces?

I do have network manager 0.7.0 installed at the moment, but I do not really think this was the problem. I upgraded several days earlier and it didn't work then. Maybe you need to install some libs or use build-dep nm or something? Now I have the option to click it on or off very easily, it's called auto GSM and I didn't configure it at all. The cool thing is that I am connected to my wireless at the same time. I don't know if that gives me double speed or my wireless just doesn't participate anymore? Anyway, I get 250 Kb/s now on updates on average, and it used to be around 100 Kb. 

Cheers,

Thomas

---

