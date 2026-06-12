---
title: "streaming live video to server"
date: 2016-09-20
forum: Networking &amp; Wireless
---

### Post by bobby24 on 2016-09-20
I have a webcam connected to my system running ubuntu and a 3g dongle connected to it. I am currently using motion software to record the video and also to stream the video locally. But I want to stream the video to my webserver (static IP). I have a UI running on my webserver and I want to be able to view the live stream on the UI when I click a particular tab on the UI. Any suggestions on how to do this ? I was reading some posts of reverse ssh for doing this but I'm not very clear on how to use it for this purpose .

---

### Post by TheFu on 2016-09-20
Few years old, but [https://wiki.videolan.org/Simple_Stream_VLC_to_Website/](https://wiki.videolan.org/Simple_Stream_VLC_to_Website/)  I never did this, though I have posted images every 20 sec to a website from a webcam.  The webcam burned out after about a year of 24/7 use.

I don't know that ssh does anything other than provide a tunnel - for "pushing video out" from the house don't think that is needed. Just lock the source port in the router down to only allow the external server's static IP. That would be sufficient in my mind. Especially if the video will be on a hosted webserver somewhere outside your physical control.

There are probably 500 other ways to do it too.

---

