---
title: "Problems with Synaptic and Software Center"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by SirsMonkey42 on 2010-06-21
I decided to load Ubuntu 10.04 onto an older laptop of mine to try to put a little more life into it. I had no problems with the install or loading the wireless drivers or anything. However, I started getting some problems I believe when I installed Ubuntu Tweak.

It worked fine to start, but a short while later I got the red circle with the minus in it.

The error it gives me tells me to open Synaptic, and when I do it gives me this.


E: Malformed line 1 in source list /etc/apt/sources.list.d/ubuntu-tweak-stable.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


It gives me a similar error when I try to open Ubuntu Tweak. I've tried deleting the sources list and reloading it, and when I do the circle disappears and I can open Tweak once, but when I close it the error circle comes back.


Also, I'm not sure if it is related, but when I go to Ubuntu Software Center and select a category everything goes blank. I was going to try to remove Tweak through the Software Center, but I'm not able to.

I'm still a newbie when it comes to Ubuntu, so any help anyone can give me will be much appreciated.

---

### Post by wojox on 2010-06-21
Ubuntu tweak is awful. Post this form the terminal:

cat /etc/apt/sources.list.d/

---

### Post by -humanaut- on 2010-06-21
> **wojox said:**
> Ubuntu tweak is awful. Post this form the terminal:

cat /etc/apt/sources.list.d/

+1 I agree Ubuntu tweek causes more problems then its worth.

---

### Post by SirsMonkey42 on 2010-06-21
Thanks for the response.  etc/apt/sources.list.d/ is just the directory that the ubuntu tweak file is in, so i assumed you meant the actual file, which this is the return.

```


cat /etc/apt/sources.list.d/ubuntu-tweak-stable.list
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu main #Ubuntu Tweak Stable Source


```

Also, aside from the obvious, why is tweak aweful?  Thanks again for the help.

---

### Post by SirsMonkey42 on 2010-06-21
I just decided to solve the problem by deleting the source file long enough to do an uninstall of tweak through synaptic.

Probably the easiest fix for the problem available.  Thanks for the info about Tweak not being worth it!

---

### Post by wilee-nilee on 2010-06-21
Ubuntu tweak is fine if you know what it does. Any borked insatll of any problem will be a problem if this is the case.

You experienced users should know the difference between a personal opinion and a program that is widely used with hardly any problems. I never see the problems people are having on the forums associated with Ubuntu Tweak.

---

