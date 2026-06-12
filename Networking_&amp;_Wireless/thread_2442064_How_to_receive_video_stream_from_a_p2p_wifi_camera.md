---
title: "How to receive video stream from a p2p wifi camera?"
date: 2020-04-29
forum: Networking &amp; Wireless
---

### Post by azad.panchi on 2020-04-29
I am integrating an embedded system (atom board) with a Wifi Camera for a DIY security project. The atom board has LUbuntu installed and camera functions well with an android phone through an android app. (links below). The camera is connected to the wifi router and I can verify its IP from within the android app. Now what I want to do is to be able to receive the video feed on the LUbuntu system. I have tried Xeoma however, it doesn't detect the camera. When I use 'Nmap' on the IP of the camera, I see that no TCP/http port is open. However, udp port 5000 is open which is a Upnp port. UDP port 554 opens occasionally, maybe when android app accesses the camera. I have tried using VLC player to obtain the video stream using rtsp protocol however, remained unsuccessful.


So, how can I get the video stream from the camera on LUbuntu?


[https://www.aliexpress.com/i/32824762255.html](https://www.aliexpress.com/i/32824762255.html)


[https://play.google.com/store/apps/details?id=x.p2p.cam&hl=en_US](https://play.google.com/store/apps/details?id=x.p2p.cam&hl=en_US)

---

### Post by guiverc on 2020-04-29
What release are you talking about ?

I also saw this question on [https://askubuntu.com/questions/1232839/how-to-view-video-stream-from-a-p2p-wifi-camera](https://askubuntu.com/questions/1232839/how-to-view-video-stream-from-a-p2p-wifi-camera)

---

### Post by azad.panchi on 2020-04-29
Lubuntu 16.04

---

### Post by CelticWarrior on 2020-04-29
Lubuntu as well as the other alternative Ubuntu flavor has only 3 years of support for LTS releases.
Lubuntu 16.04 is out of support for more than a year. Please install a supported release and troubleshoot from there.

---

### Post by azad.panchi on 2020-04-29
I only have 1GB RAM on the board and it is fairly slow system (1.5GHz). I don't want to overwhelm it. Besides, the problem is more to do with the networking and communication than it is with the kernel.

---

### Post by CelticWarrior on 2020-04-29
A supported release like Lubuntu 18.04 (supported until April 2021) isn't more demanding than 16.04.

---

### Post by azad.panchi on 2020-04-29
Camera is wireless and wifi on the ubuntu system is functioning so I don't see how changing OS version would do any good. As I said it is more of a networking/communication problem than it is driver/os-packages. I am not sure how to receive video feed on the ubuntu which works perfectly fine on an android app.

---

### Post by CelticWarrior on 2020-04-29
Fact #1: Lubuntu 16.04 is out of support.
Fact #2: Unsupported OSes shouldn't be used when connected to the internet due to increasing security risk both for the user and everyone potentially affect by, among many others, the usage of a given compromised system in an attack as part of, in layperson's terms, a "zombie attack".
Fact #3: Keeping an up-to-date, patched, OS is the foundation for running safely everything else.

The suggestion to upgrade is therefore unrelated to your question. I never said it had something to do with it, it just something that should be done regardless of any other issues or considerations

That said it's also true that the newer the OS/software, the better are the chances for having something of the sort you want to make work actually work. But it may not be possible even with the newest software/drivers, etc. I can be a case of some proprietary protocol that needs to be supported by the manufacturer and if they don't want/care to make it work in desktop Linux and only in mobile Android because of course they do, I'm afraid that nothing can be done.

---

### Post by azad.panchi on 2020-04-29
* It is a personal DIY project and it is not going to be on the internet - only within LAN.
* It is not a proprietary s/w issue, infact the app the manufacture has suggested is a general purpose one that works with more than one camera. It is indeed a standard way of processing the video stream. I guess it must be rtsp protocol but then again I see the port not open and I wasn't successful in getting it to work with VLC.

Sure, it is a kind of hacking but in that respect whole ubuntu is a hack!

---

