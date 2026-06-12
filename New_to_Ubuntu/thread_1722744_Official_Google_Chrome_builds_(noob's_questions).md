---
title: "Official Google Chrome builds (noob's questions)"
date: 2011-04-06
forum: New to Ubuntu
---

### Post by nik0p01 on 2011-04-06
Hello,

I've been out of the Ubuntu world for quite some time, but I want to try to go back and install 11.04 on my next machine. My problem is that I'm very (VERY) dependant on Google Chrome. I tried to find more info about the linux build, but all I could see are problem/solution kind of threads. So my questions are rather basic:
1. Does Chrome come with flash built in like in Windows or do I need to install plugin like before?
2. What about 64bit nowadays? Is it okay for desktop use? And what about 64bit Chrome? Is it as stable as 32bit version?

P.S. I suppose it's common knowledge out here... What would YOU install 32bit or 64bit Ubuntu (taking in account the necessity of flash)?

Thans in advance,
Andrei

---

### Post by rudihawk on 2011-04-06
64bit flash's problems have mostly been resolved I think. :) 

Not too sure about your other questions though, I use chromium(from the repos) and it's pretty much the same as the Chrome on my Win 7 install.

---

### Post by nik0p01 on 2011-04-06
> **rudihawk said:**
> 64bit flash's problems have mostly been resolved I think. :) 

Not too sure about your other questions though, I use chromium(from the repos) and it's pretty much the same as the Chrome on my Win 7 install.

Thanks for your answer. How about installing flash then? Is it a hassle as it were before or they made it easier to install/update?

---

### Post by gandaran on 2011-04-06
> **nik0p01 said:**
> Thanks for your answer. How about installing flash then? Is it a hassle as it were before or they made it easier to install/update?
linux 32-bits chrome has built in flash just like in windows, linux 64-bits chrome uses the system installed flash, there are many ways to install 64-bits flash but the easiest it to use a firefox addon [flash-aid]("https://addons.mozilla.org/en-us/firefox/addon/flash-aid/") to install and keep it updated, once installed the chrome browser will pickup the flash in firefox plugins folder.
also there in nothing easier than to just copy or move the flash plugin (libflashplayer.so file, get it from adobe.com in the .tar archive format) and put it in chrome or any other browser plugins folder, it's not a hassle to install flash when you understand how the plugin works.

---

### Post by nik0p01 on 2011-04-06
> **gandaran said:**
> linux 32-bits chrome has built in flash just like in windows, linux 64-bits chrome uses the system installed flash, there are many ways to install 64-bits flash but the easiest it to use a firefox addon [flash-aid]("https://addons.mozilla.org/en-us/firefox/addon/flash-aid/") to install and keep it updated, once installed the chrome browser will pickup the flash in firefox plugins folder.
also there in nothing easier than to just copy or move the flash plugin (libflashplayer.so file, get it from adobe.com in the .tar archive format) and put it in chrome or any other browser plugins folder, it's not a hassle to install flash when you understand how the plugin works.

thanks :) It was exactly what I wanted to know. 
Btw I tried 11.04 on my laptop and it worked out of the box (wifi and all). Yeah, linux is way more friendly than before. All that left is to decide which way to go: 32bit or 64bit. I've 4GB in my system but some of it goes to Intel video card, so I won't win too much in the memory department. Is there are any other advantages from 64bit?

---

### Post by rudihawk on 2011-04-06
I think it would be fine to stick with 32bit in your case. 

64bit is handy if you do intensive stuff like video encoding. 

For day to day use their isn't much difference although most people are starting to slowly migrate to 64bit since it's the next logical step. I use 64bit Ubuntu on my desktop and there are no more problems/hassles than what I have on my 32bit Ubuntu netbook.

---

### Post by nik0p01 on 2011-04-06
Thank you for all your answers. Great forum with great people, just as I remember it :)
I'll think about 32bit/64bit until the official release of 11.04.
Superb support, thanks again.

---

### Post by JayD239 on 2011-04-20
For flash on 64bit you might want to try this ppa [https://launchpad.net/~sevenmachines/+archive/flash](https://launchpad.net/~sevenmachines/+archive/flash) ([see](http://www.omgubuntu.co.uk/2010/09/install-64bit-flash-from-a-ppa-or-deb/)). This enabled me to watch 1080p movies.

Chromium in the repositories (10.10) installed a 64bit version for me.

---

### Post by I2k4 on 2011-04-22
FWIW, I had a bunch of problems on my test installations using sites (e.g. GrooveShark) with the pre-installed Chromium (flash separate), that run perfectly with Google's Chrome (flash included).  32 bit.

---

