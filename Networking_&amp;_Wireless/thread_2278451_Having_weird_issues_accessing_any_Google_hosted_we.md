---
title: "Having weird issues accessing any Google hosted websites?"
date: 2015-05-16
forum: Networking &amp; Wireless
---

### Post by dorlow on 2015-05-16
I just switched from Windows to Ubuntu 15 a few days ago.  Everything is working great except I'm having weird issues accessing Google websites (google.com, Gmail, maps, anything google related.)  When clicking on e-mails, the wheel will just spn and not load the e-mail.  Yesterday, I was in google images trying to load a few images of grills.  It loaded about 5 or so then hung up the browser.  It's only Google websites.  Everything else is working great.  I've already erased my history, cookies, temp files, etc.  But that's not the problem anyways because Firefox and Chrome are both having the issue and those settings are separate.

---

### Post by tgalati4 on 2015-05-16
Try running *google-chrome* in a terminal and post any messages that show up.

```
free
google-chrome --debug
```

That is a strange problem, but both browsers are memory hogs.  And that makes me think of bbq.

---

### Post by dorlow on 2015-05-19
I tried running 
[COLOR=#000000][FONT=Ubuntu Mono]free[/FONT][/COLOR]google-chrome --debug

I did get the memory output.  

            total       used       free     shared    buffers     cached
Mem:       8072668    7457840     614828     363048      63804    1130724
-/+ buffers/cache:    6263312    1809356
Swap:      8284156      34376    8249780

But I didn't get any output at all from Chrome while browsing google sites.

---

### Post by dorlow on 2015-05-19
I just tried something else.  I opened an incognito window in Chrome.  At first glance, I seem to browse Gmail a lot better.  No issues at all.  (Which tells me that even though I deleted all temp files, cookies, etc., there still something being left behind.)  But even in incognito, I can't open Google Drive and create a new document.  It just locks up at a white page for a while then get the message.
[IMG]http://ubuntuforums.org/chrome-extension://apdfllckaahabafndbhieahigkjlhalf/128.png[/IMG][COLOR=#000000][FONT=Helvetica]**Google Drive**
The app is currently unreachable

A few days ago, I changed my DNS servers from using my local ISP DNS servers to 8.8.8.8 (which are owned by Google I believe).  I feel like I've swapped about everything out.  What else is there to troubleshoot?[/FONT][/COLOR]

---

### Post by kurt18947 on 2015-05-19
I'm not sure if my issue relates to dorlow's or not but thought I'd mention it. I have a problem with Chromium. It will freeze up for several seconds at a stretch but will eventually scroll or do whatever. I have htop installed (found in the repos) which I find more useful than top. I have it running in a small terminal window in one corner of my screen. I'm finding Chromium will peg one core of a dual core AMD Athlon II X2 processor for several seconds. I wonder if it'd be worth dorlow's time to install htop, run it from a terminal placed in a convenient spot and monitor memory and processor usage. htop also lists processes, the top one being current.  Another terminal tool which might be interesting is dmesg. See if there are any obvious errors reported there.

---

### Post by tgalati4 on 2015-05-20
It's possible that you have a bad firefox or google-chrome profile.  You can clear cache and create new user profiles in the User Tools of each browser.  Have you installed all the updates for 15.04?  Also, have you run a *memtest* overnight?  Bad RAM can cause strange issues.

---

