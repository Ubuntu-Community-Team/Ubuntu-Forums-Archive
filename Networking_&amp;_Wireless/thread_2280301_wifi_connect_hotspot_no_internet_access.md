---
title: "wifi connect hotspot no internet access"
date: 2015-05-29
forum: Networking &amp; Wireless
---

### Post by Pjevser on 2015-05-29
So i have a hotspot i connect to, normally (on windows) i connect to it and then goto [www.hotspot.local](www.hotspot.local) (in browser) and type in my user/pass and then the internet works.

But for some reason that doesn't work on ubuntu 15.04 (fresh installed), whenever i in firefox goto [www.hotspot.local](www.hotspot.local) takes a little while and just end up saying the page cannot be showed.

So what am i missing here to get it to work?

---

### Post by RobGoss on 2015-05-29
What browser are you normally using to connect to this hotspot? I would recommend using a different web browser maybe that will help.

---

### Post by Pjevser on 2015-05-29
> **robert159 said:**
> What browser are you normally using to connect to this hotspot? I would recommend using a different web browser maybe that will help.

Before i installed 15.04 i tried 14.04.2 LTS using firefox and Chromium and they both had same problem with timeout.

---

### Post by RobGoss on 2015-05-29
Have you try Google chrome I've never use a hotspot for my connection.

---

### Post by wildmanne39 on 2015-05-29
Have you tried other networks? can you connect to any at all? if not please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by Pjevser on 2015-05-29
> **Wild Man said:**
> Have you tried other networks? can you connect to any at all? if not please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks
Yes other networks works just fine without problems :) 

So i guess my problem is that i have to type user/pass on a page, but for some reason it wont access it from browser.

Edit: Also i have tried chrome now, with same results. Can't access the hotspot.local in browser to login.

---

### Post by Pjevser on 2015-05-29
Got it working now from help from this post: [http://ubuntuforums.org/showthread.php?t=797872&p=4982277#post4982277](http://ubuntuforums.org/showthread.php?t=797872&p=4982277#post4982277)
adding the ip and hotspot.local into hosts file seems to work :)

---

### Post by wildmanne39 on 2015-05-29
Glad you got it working!

---

