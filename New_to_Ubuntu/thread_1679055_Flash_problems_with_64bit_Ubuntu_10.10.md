---
title: "Flash problems with 64bit Ubuntu 10.10"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by DCarrollUSMC on 2011-01-31
I currently have 64 bit Ubuntu 10.10 installed on this machine and I'm running into some flash problems.  When I visit sites like youtube, megavideo, yidio etc. with streaming flash videos I am running into some trouble.  I have Adobe Flash 10 I believe.  My problem is that the videos will stop loading randomly and load very slow.  Occasionally flash has crashed completely and I've had to reload to get it back.  Is there any way to fix this?  Can I use a different player?  Is there a workaround for Flash?  I think that the 64-bit version is still not solid yet.

---

### Post by ben889 on 2011-01-31
aparently adobe only supports the 32 bit but if your using firefox use this addon
 
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by sydbat on 2011-01-31
> **ben889 said:**
> **aparently adobe only supports the 32 bit** but if your using firefox use this addon
 
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)Wrong. Flash comes in native 64bit. Just use the link you posted, and Flash-Aid (which is brilliant) will detect your architecture and install the correct version of Flash. It will also remove conflicting plugins.

---

### Post by TBABill on 2011-01-31
> **sydbat said:**
> Wrong. Flash comes in native 64bit. Just use the link you posted, and Flash-Aid (which is brilliant) will detect your architecture and install the correct version of Flash. It will also remove conflicting plugins.
 +1 64 bit flash is now working very well in Linux and the Ubuntu repo only installs 32 bit Flash if you download it from there or install ubuntu-restricted-extras. Using Flash Aid is a perfect answer to configuring the right version of flash for you in just a couple clicks.

---

### Post by sandyd on 2011-01-31
> **DCarrollUSMC said:**
> I currently have 64 bit Ubuntu 10.10 installed on this machine and I'm running into some flash problems.  When I visit sites like youtube, megavideo, yidio etc. with streaming flash videos I am running into some trouble.  I have Adobe Flash 10 I believe.  My problem is that the videos will stop loading randomly and load very slow.  Occasionally flash has crashed completely and I've had to reload to get it back.  Is there any way to fix this?  Can I use a different player?  Is there a workaround for Flash?  I think that the 64-bit version is still not solid yet.
See the "adobe tools" section in my signature.
and seeing that your having these issues, 64-bit flash will be more stable than what your experiencing.

---

### Post by DCarrollUSMC on 2011-01-31
I ran the terminal code given from Flash-Aid and I have flash installed now but I have not seen any improvement in performance.  Currently I can't even get a 2 minute youtube video to load without stalling multiple times and needing to be refreshed.  Trying to load the videos is bogging down just about everything as I'm having trouble loading some of the ubuntu forums pages at the same time.  Could this have something to do with my connection?  These videos loaded just fine in Windows, is that just a drawback of Linux?

---

### Post by uRock on 2011-01-31
> **DCarrollUSMC said:**
>   These videos loaded just fine in Windows, is that just a drawback of Linux?
No. Not sure how you installed Flash, I installed ubuntu-restricted-extras on this machine and the version of flash works perfectly.

I have used flash-aid twice and have a 50% fail rate with it.

I have used the Flash installer in sandyd's signature on one of my other 64bit machines and it worked flawlessly.

---

### Post by DCarrollUSMC on 2011-01-31
I don't know what I'm doing wrong.  I keep trying new things but adobe is either out of date and I can't figure out how to update it or there's no improvement to the download of flash videos.  Right now youtube seems to be loading videos fine and not stalling but often when I try to load a webpage it will just sit at load.  I don't know if it's just a flash problem.  

Also, I tried downloading the flash installer from sandy above but when i change the permissions to the file to make it executable it doesn't do anything.  Nothing that I can see at least.

Sorry for my ignorance I'm really just beginning to understand linux systems

---

### Post by DCarrollUSMC on 2011-01-31
bump

---

### Post by sandyd on 2011-01-31
> **DCarrollUSMC said:**
> I don't know what I'm doing wrong.  I keep trying new things but adobe is either out of date and I can't figure out how to update it or there's no improvement to the download of flash videos.  Right now youtube seems to be loading videos fine and not stalling but often when I try to load a webpage it will just sit at load.  I don't know if it's just a flash problem.  

Also, I tried downloading the flash installer from sandy above but when i change the permissions to the file to make it executable it doesn't do anything.  Nothing that I can see at least.

Sorry for my ignorance I'm really just beginning to understand linux systems
aint me this time.
that is, unless you have an ancient glibc.

wait.
post output of
```

uname -a
```

---

### Post by volaer on 2011-02-17
I have here a very quick solution! Hope this will work. It worked in my machine:
[http://www.brandbuildit.com/ubuntu/how-to-install-adobe-flash-player-10-on-ubuntu-64-bit-lucid-lynx/](http://www.brandbuildit.com/ubuntu/how-to-install-adobe-flash-player-10-on-ubuntu-64-bit-lucid-lynx/)

---

