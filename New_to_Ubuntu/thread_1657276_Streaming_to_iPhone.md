---
title: "Streaming to iPhone"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by MjK3II on 2011-01-01
Hello, all I currently have a minor dilemma. I have a 16 gig iPhone 4 and I have 200 gigs of media. I am running Ubuntu 10.10 that is 64 bit and IOS 4.1 (IF thats even relevant). 
I would LOVE to set up a system to stream to my iPhone for free seeing as I am currently unemployed. There are two requirements to the needed solution:
1) It MUST work on Ubuntu 10.10 64 bit and
2) It has to work on the iPhone.

I am willing to stream through Safari, an App Store, or Cydia application. The only obstacle is money if the service is a little buggy or slow I will deal. Please keep it simple as possible seeing as I am new to Ubuntu (But I learn fast XD) If it works on Windows as well that would be a bonus!

---

### Post by PatchesTheCaveman on 2011-01-01
If you just want to stream across your local network, using the WiFi feature of your iPhone, you can use uPnP.  I'm afraid if you want use the 3G feature to stream when you're away from home, it will be far more complicated.

For local wi-fi streaming, install the MediaTomb server on your Ubuntu machine to share media on your local network.  It is available in the Ubuntu Software Center, Synaptic, or can be installed from a terminal by running:
```
sudo apt-get install mediatomb
```

For information on how to set it up, visit [http://mediatomb.cc/pages/documentation#id2855459](http://mediatomb.cc/pages/documentation#id2855459)

There are at least two applications for the iPhone that will be able to play the streams:  PlugPlayer and AirPlayer.  They are both available from the App Store.  Any app that can play uPnP streams will work.

If you want to stream away from home with 3G, another user on this forum is trying to use a service called Tonido:  [http://ubuntuforums.org/showthread.php?t=1654098](http://ubuntuforums.org/showthread.php?t=1654098)

Unfortunately, he's having trouble with 64-bit Ubuntu at the moment.  If he figures out his problem, you might be able to use that service as well.

---

### Post by abramsh on 2011-01-01
You can get PlugPlayer to work over 3G. Just discover the device on you LAN, then edit the device configuration and set the base URL to http://<LAN IP>:<PORT>

---

