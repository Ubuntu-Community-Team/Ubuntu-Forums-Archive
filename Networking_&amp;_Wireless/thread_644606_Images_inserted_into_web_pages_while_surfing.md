---
title: "Images inserted into web pages while surfing"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by OriginalSpaz on 2007-12-19
I have been having a very frustrating problem lately.

About 3 weeks ago I was developing websites on my local Windows server when I started noticing that many of my images were being replaced by a very crude image I had never seen before. I checked my source code locally and found it to be fine but when I looked at the source code through my browser I noticed that in many places a link to an outside image had been inserted into the IMG tag like this "IMG SRC="http://URL.TO.NEW/OFFENDING/IMAGE" PATH.TO.MY/ORIGINAL/IMAGE". It seems that somehow this new link was inserting itself before my own image link and breaking my pages at the same time.

I tried restarting my browser, checked the Windows server for viruses, trojans, etc. and even restarted my own system with no luck. My pages were still being manipulated. At first it was only occurring when I was surfing locally using 192.168.1.XX on our own server but eventually it started happening on a few outside web addresses as well. Seeing as how I was pretty sure not all of these sites could have been hacked with this image I at first figured it must be a problem on our internal server. However, when I surfed the same pages from 3 other computers on the network they all looked fine. So it was my system only.

I did a rootkit check and checked my logs for suspicious behavior with no results. My Ubuntu 7.10 system appeared clean. Then suddenly the image issues stopped.

A day or so later they returned worse than before. Now quite a few sites about the web were being affected and our local ones as well. Only on my system using FireFox. This continued for a while and then I finally decided to change my computer's IP (we use a Linksys router with DHCP turned off). The image hijacking immediately stopped.

A week or so goes by and out of the blue it starts again. Only this time it is a different image (from the same website) and the method has changed a bit. The link is still inserted in front of the original image link but now a TITLE tag has been added after the new image link so as not to break the page - like this "IMG SRC="http://URL.TO.NEW/OFFENDING/IMAGE" Title="PATH.TO.MY/ORIGINAL/IMAGE".

After some checking around I change my IP again and it fixes it but a short time later it is back. I then change my Ethernet connection from my card to my onboard slot and that takes care of it again. It hasn't come back yet but I'm just waiting. I'm really hoping someone out there has an idea as to what could be happening. I've been scouring Google for days and can't find anything like it.

To recap...

1. My system is Ubuntu 7.10.
2. We have 3 systems with Ubuntu 6.10 and 1 Windows XP box on the network.
3. We are behind a cable modem and a Linksys router (not wireless).
4. My system is the only one that seems to be affected.
5. I am using Firefox 2.0.0.11
6. Websites viewed both on the web and locally are both affected.
7. The first time I was affected I was using 6.10 and since upgraded to 7.10.
8. Changing my computer's IP seems to at least temporarily stop the injections.
9. Nothing else seems to be affected except crude images replacing other images on web pages.

---

### Post by heindsight on 2007-12-19
Does this only happen with firefox? what happens if you use say wget tor retrieve an affected
web page? What firefox plugins/add-ons/extensions/themes/etc do you have installed? Are they all from trusted sources? If the problem only occurs with firefox then you might have some sort of malicious firefox extension installed.

Perhaps you should try to run a packet trace while loading an affected site. That might just point you to the source of your problem.

---

### Post by lswest on 2007-12-19
is the page online? might be that you're being hacked...check the security of your code for rfi's (remote file includes) or other common hacks.

---

### Post by OriginalSpaz on 2007-12-19
Hi heindsight.

I have not tried an alternative to Firefox but I have suspected that it could be something with the browser itself. I really don't have many extensions installed. I have...

1. Adblock Plus
2. Download Statusbar
3. Download Helper
4. DownThemAll!
5. MediaPlayerConnectivity
6. ubufox
7. Web Developer

If the problem reoccurs I will using wget and see what happens.

The packet trace is also a good idea.

---

### Post by OriginalSpaz on 2007-12-19
Hi lswest.

It is not actually a web page that is being hacked or changed but rather the code is being changed between the server and my browser. Images are being injected into the pages so it appears my transfer is being hijacked somehow. The most curious part is that it occurs both locally and out on the web.

---

### Post by lswest on 2007-12-19
hacking can include injecting different image sources in the actual file, or during the time it loads.  if you have a web developer toolbar in firefox, try loading the page with all functions disabled that you can disable, might help you figure out if someone has hooked that site up with some shell or extra function.  Also...i don't honestly think anyone would bother "hack" a page through transfers, playing around with packets is just too much work.  otherwise i say grab AVG AV and let it run, or Spybot S&D (or try going to the site from linux first, to see if it has to do with your computer?)

---

### Post by OriginalSpaz on 2007-12-19
> **lswest said:**
> hacking can include injecting different image sources in the actual file, or during the time it loads.  if you have a web developer toolbar in firefox, try loading the page with all functions disabled that you can disable, might help you figure out if someone has hooked that site up with some shell or extra function.  Also...i don't honestly think anyone would bother "hack" a page through transfers, playing around with packets is just too much work.  otherwise i say grab AVG AV and let it run, or Spybot S&D (or try going to the site from linux first, to see if it has to do with your computer?)
Thanks for continuing to try and help out lswest but I'm not sure if you read my previous posts (or perhaps I just wasn't clear enough).

I am already surfing from a linux box (Ubuntu 7.10) and it is not happening on only one website or one web page. The injections are happening on a variety of web pages and not always the same ones. The pages are both hosted on our own internal server and out on the Internet in general (the Google website) for instance. I think that this behaviour pretty much rules out any specific website being hijacked with a "shell" or "extra function".

This only leaves the fact that somehow, somewhere between my computer and the source website image links are being injected into the page code before I view the page. Only on my system, not on any of the others in my office which share the same router and cable modem.

I have checked all my logs for suspicious behaviour and checked for rootkits with no results. I am inclined to believe that it could be a compromised Firefox but still can't understand why changing my IP or my ethernet port would stop the injections.

Also, on my Windows box I would much prefer to run NOD32 from Eset than AVG AV.

---

### Post by lswest on 2007-12-19
i was only naming 2 AV/Spybot scans, didn't say there were others, it's just the 2 that i use.  Also...i honestly can't think of any simple ways to compromise your firefox or your packets as you are suggesting (i have some experience in the field of hacking and penetration testing, as i do it for both my own sites, those of my friends, and sometimes for the IT guys at my school).   Try deleting your cache of cookies in firefox, might be some rather eccentric tracking cookie or so (unreasonable, but it can't hurt for sure).  (do so under edit-->preferences-->privacy-->show cookies and choose "remove all cookies").  Don't honestly know if it will help, but give it a shot

---

