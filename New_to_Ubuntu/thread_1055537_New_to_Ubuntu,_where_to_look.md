---
title: "New to Ubuntu, where to look?"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by SimonHGR on 2009-01-30
Hi all,

I'm new to Ubuntu, but not new to Linux/Unix generally.

I have three problems at present that I'd greatly appreciate help with.

1) My screen, when scrolling, does not update properly. If I cycle windows, forcing a window refresh, I get to see the correct output.
  a) any suggestions?
  b) where is the configuration tool that would control things like graphics acceleration and the like?

2) I find that the default version of open office causes my machine to lock up at random (but frequent) intervals. I tried to download the latest from openoffice.org, but it comes as rpm files. So far as I can tell, these are not supported by Ubuntu. The system tells me to execute "apt-get install rpm" to get it. However, when I do that, it just waits forever claiming it's trying to access some remote site.
  a) Should I be able to use rpm with Ubuntu, or am I compelled to find other package formats?
  b) Should this "apt-get" tool work? And if so, any ideas why it's not playing ball with me?

Many thanks,
Simon

---

### Post by avtolle on 2009-01-30
Ubuntu is Debian based, so you should look for deb not rpm. That's the cause for the apt-get problem you are experiencing. 

What is your graphics card and, if nVidia or ATI, is the correct driver activated? This may help with the screen refresh issue. BTW, try turning off the desktop effects (IIRC, under System>Preferences>Appearance) and see if that helps as well.

---

### Post by yeats on 2009-01-30
I think you'll generally want to have a separate thread for each issue - it helps both you and the rest of us see what's what. :-)

For OpenOffice3 - you'll want to go to this link:

[http://download.openoffice.org/other.html#en-US]("http://download.openoffice.org/other.html#en-US")

And select the "Linux DEB" for your architecture (i386 or AMD64).

---

### Post by avtolle on 2009-01-30
It looks like the debs at [www.openoffice.org](www.openoffice.org) are for version 3.0.0 only at the moment. From the opening page, select Other platforms and languages, then scroll down to English, and select the correct deb for your architecture, i.e., 32 bit or 64 bit, and download from there. 

IIRC, there is a launchpad repository with the 3.0 debs for Ubuntu, which you can add to your software sources list (/etc/apt/sources.list). I've looked at that, but for sake of conformity within the office, haven't gone any farther, and at the moment, don't recall the name of the ppa to add.

---

### Post by SimonHGR on 2009-02-01
Many thanks all for input received so far, I'll start a new thread since the next questions may reasonably be considered to be different--kindof!

Cheers,
Simon

---

### Post by handydan918 on 2009-02-01
> **avtolle said:**
> Ubuntu is Debian based, so you should look for deb not rpm. That's the cause for the apt-get problem you are experiencing. 

What is your graphics card and, if nVidia or ATI, is the correct driver activated? This may help with the screen refresh issue. BTW, try turning off the desktop effects (IIRC, under System>Preferences>Appearance) and see if that helps as well.

+1 !
The video driver may also be responsible for the freezes...

---

