---
title: "Crackling sound with bluetooth"
date: 2013-09-17
forum: Networking &amp; Wireless
---

### Post by jacsv832 on 2013-09-17
Hi! I'm streaming audio from my ubuntu laptop (HP Folio 13-2000) with Ubuntu 13.04 to a bluetooth reciever (Zeniq btr 100). The mode is set to A2DP and the streaming works good most of the time. But when I simultanelously use the wifi to download files or load heavy websites the sound starts crackling. I've tried to find a soulution on forums and google without success. Any ideas how to solve this problem?

Thank you!

---

### Post by tgalati4 on 2013-09-17
It's possible that you are getting interference from the WiFi antenna with your bluetooth antenna.  Streaming A2DP uses a lot of bluetooth bandwidth and any dropouts you will hear.  WiFi dropouts you don't hear, the packets are just resent quietly.  You can't find a solution because it is probably one that can't be fixed.  Use wired headphones while browsing or downloading or don't download while listening with bluetooth.

You could get a USB bluetooth adapter and use that over the internal bluetooth and see if it is more robust to interference.

Turn off WiFi and use an ethernet cable connect to your laptop and see if the dropouts go away.  If they do, then you know you have an interference problem.

If you have narrowed it down to WiFi/Bluetooth interference, then send an email to HP about your experience and see what they say.  Oh, and please share their response.

---

### Post by jacsv832 on 2013-09-18
Thanks, yeh it's probably interference. I tried to turn off the wifi and used an ethernet cable and the crackling sound disapeared. I'm going to try a few more things this evening, but I guess the placement of the bluetooth reciever is to close to the router. :)

---

