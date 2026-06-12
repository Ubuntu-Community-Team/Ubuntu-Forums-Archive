---
title: "Intel Proset Wireless .conf file"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by Matthew Spinks on 2009-07-23
My intel proset wireless wasn't working when I upgraded to 9.04, so I read a lot of other threads and installed some drivers and stuff and after a lot of frustration realized that the driver is already in the kernel. It's just not turned on for some reason. So I used a command from another thread "sudo modprobe iwl3945" and my wireless card works perfectly without any problems, but I have to type it in every time it boots.

So how do I make it work on boot? I've browsed around modprobe.d and made a .conf for it. It works kind of, but ubuntu halts halfway through the startup process.

Here's the .conf file I copied from a different thread:
alias wlan0 iwl3945 
options iwl3945 antenna=1

---

### Post by Matthew Spinks on 2009-07-27
anyone?

---

### Post by Matthew Spinks on 2009-07-28
well, I removed the dell restore partition from my hard drive on my laptop, so I made a live cd for jaunty to run gparted. When I ran it, I noticed the wireless was able to connect without any problems, so I decided to do a fresh reinstall and everything works beautifully now. I guess the problems could have been caused by earlier updates (I had a lot of trouble with 8.10) and drivers like ndiswrapper or something. Also I'm having no issues with my sound card like I was before, and the network manager is working again. so I gotta say I'm even happier with linux now than ever. Guess I will never really know what the problem was. :)

---

