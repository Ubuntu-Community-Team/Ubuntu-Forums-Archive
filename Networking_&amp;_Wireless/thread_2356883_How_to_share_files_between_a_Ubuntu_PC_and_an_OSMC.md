---
title: "How to share files between a Ubuntu PC and an OSMC Raspberry Pi?"
date: 2017-03-27
forum: Networking &amp; Wireless
---

### Post by Arminius on 2017-03-27
My Ubuntu PC is connected to the internet with Ethernet, Raspberry Pi is connected with WiFi, I've played around with the many options on the Raspberry Pi but there are so many I'm unsure which one I should persue, anyone sharing their media files with their Raspberry Pi? Point me in the right direction please.

---

### Post by TheFu on 2017-03-27
Load up OSMC (a r-pi variant of Kodi) on the pi.
Load up Plex Media server on the "server" or desktop.
Use DLNA and/or NFS to access the media.

You'll want all the video to be h.264/aac (or ogg)/mkv (or mp4) encoded and containered. Sure, other codecs and containers will work, but most just aren't a well-supported. For example, h.265 may work, but my pi stutters on the 1080i/p stuff. h.264 video is supported in the GPU and plays extremely well.  

If you use Plex and your plex system has enough CPU power, then it can transcode the video in real-time to whatever any current client devices might require.  That is absolutely necessary for a Chromecast, Roku, Fire-Stick, and Apple video devices.

Wifi will be problematic. Most wifi connections aren't really very stable. Go wired if you can - even powerline is better than wifi.  WiFi often will result in stuttering with few options to solve it for most people. Apartments with lots of neighbors also using wifi will mostly be difficult.  Wired. Whenever. Possible.

---

### Post by Bucky Ball on 2017-03-28
With a static IP on the Ubuntu box, you can go to 'Files' on the Kodi (OSMC) desktop (from memory) and add the directory as a network directory. Not near my Pi at the moment, but will check later. That's one way we connect with the other computers in our set up.

The other way, and the one I find easiest, is to use Filezilla on the Ubuntu box (there may be a Filezilla add-on for OSMC also) and dump things on the hard drive connected to the Pi that way. Again, static IP on the PI makes life much easier. Without one, you'll need to check the IP the Pi has been served and then input that in Filezilla. Filezilla is in the repositories.

The main thing is that both the Pi and the Ubuntu box are able to ping the router rather than whether one is using wireless and the other wired (it really doesn't matter). If they can, they're both on your local area network and therefore should be able to connect with each other. 

I suggest setting up static IP addresses on both the Pi and the computer and then see if you can ping the Pi from the computer. We can help you with that.

---

