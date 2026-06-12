---
title: "Complete noob looking for assistance"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by Gideon5 on 2009-05-16
Ok, I'm a complete noob to the entire Linux/Ubuntu system.  I was recently given a 9.04 Jaunty disk (i386 I think) to try out by someone that I work with.  I've poured through the forums for answers to the questions that I have.  They are rather elementary, although I'm going to need someone to big-bird/cookie monster explain this stuff to me.  The problem that I have is that I'd like to try out the cube desktop, but the CCSM is not installed on my version of Jaunty.  The other problem that I have is that I cannot under any circumstances connect my ubuntu computer to the internet, nor can I download programs such as aptoncd to the computer that I work on (I'm in the military and in Iraq currently).  I'm running Jaunty on an Acer Aspire 5500, with an AMD 2650e, 3.00 GB RAM, and an ATI Radeon x1200.  The easiest way for me to be able to get any updates is to download a .deb file, and move it to my personal computer via external hard drive or cd.  Any suggestions?

---

### Post by alexandari on 2009-05-16
well first how do you connect to the internet? have you tried setting up something?

---

### Post by s.fox on 2009-05-16
Hi,

[This]("http://www.futuredesktop.org/compiz_desktop_in_ubuntu9.04.html") guide should help you,  but would require internet access.

Maybe others will know of a way to get the required files in .deb format.

-Ash R

---

### Post by ugm6hr on 2009-05-16
The packages you need are:
compizconfig-settings-manager
python-compizconfig

If you go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and scroll down to the search box, just enter these in, and follow the links to the .deb

You do need to confirm whether you have the i386 or amd64 in order to ensure you have the right .debs

You can check in
```
uname -a
```

The end of that entry will be i686 if 32-bit.

PS: It is often helpful for you and us if you use more descriptive thread titles.

---

### Post by Gideon5 on 2009-05-16
Well, it's not that I'm unable to connect to the internet, it's that I'm prohibited from doing so.  I've already checked out the link provided, but doesn't help considering I can't use the synaptic package manager considering that I cannot connect to the internet.  I can download all the deb files that I'd need to get everything running, I'm just so unfamiliar with which ones to get that I'm lost in space.  Thanks for the quick answers though

---

### Post by Duskao on 2009-05-16
The "cube" desktop AKA compiz might not work on your computer all that well in ubuntu 9.04. I'm not saying it won't work, but it might not work well. You will have to use the open source drivers AKA Radeon/RadeonHD drivers and they have very limited 3d support at this point in time. As far as the internet issues, I'm sorry, it's not exactly my bag. Hope compiz works for you once you get the net up and running.

---

### Post by Gideon5 on 2009-05-16
ugm6hr, thank you for the assistance.  I'm looking into the python deb right now.  We'll see.  This is a "throw away" laptop considering the environment that I'm in right now.  When I get back home, I'll have something a bit more worthy.  I'll also keep the thread title tip in mind.  Duskao, thanks for the help, I was reading up on that, this is all greek to me right now, but eventually I'll get there.

---

