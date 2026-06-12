---
title: "Firefox in Jaunty, the bane of my linux existance"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by Crunchy the Headcrab on 2009-06-30
I keep having this problem.  Firefox will out of the blue shutdown and it is not possible to restart it without rebooting my pc.

The terminal gives this error:  Segmentation Fault

That is all.

I have no plugins (not even flash) installed.  I have the Adblock Plus addon installed but I am unwilling to remove that one.  It is basically the reason that I use Firefox in the first place.

This is a problem that I have had many times in the past.  This is a brand new install of Ubuntu 9.04.  I updated all the packages and then I manually installed the latest NVIDIA drivers for my 9800M GS.  Everything was going fine after messing around on the internet for several hours, and several shutdowns/boots, until I decided to change my theme to clearlooks.  At this time things started getting unstable and this is when Firefox started having the Segmentation Fault problem.  I changed it back to human (or whatever the default is) and I am still having these problems.

This for me is unforgivable.  I need a browser that works.  That is the one thing that I cannot do without.  I can't accept it dying suddenly and frequently.  This is the one thing that keeps me going back to Vista.  I never have errors on Vista.  I am trying very hard to entirely make the switch, but until I have a functional web browser, that will be quite impossible.

---

### Post by ibutho on 2009-06-30
Is this the version of Firefox shipped with Ubuntu? Have you tried the packages from mozilla.com?

---

### Post by Crunchy the Headcrab on 2009-06-30
Yeah, it is Firefox 3.0.11 which was whatever Ubuntu installed (automatically) through it's updates using the normal repositories.

I haven't ever tried using any Firefox besides what is in the Ubuntu Repositories because I'm pretty n00bish and wouldn't want to create dependency problems or whatever.

My Ubuntu is basically vanilla (untampered with) except for the NVIDIA drivers.  I haven't even installed any additional programs.

---

### Post by ibutho on 2009-06-30
You wouldn't create any dependency problems by using the packages from mozilla.com and they do not interfere with any packages shipped by the distro. Its worth checking them out and see if they resolve your problems. You actually don't install the packages from mozilla.com like you'd with Ubuntu packages. All you need to do is download the package you need, extract it, navigate to the extracted directory and click on the icon labeled "firefox" in order to run Firefox.

---

### Post by Crunchy the Headcrab on 2009-06-30
Thanks for the info.  The problem has been temporarily solved by deleting the configuration files in .mozilla.

I will definitely keep your advice in mind though, as this has been a recurring problem with Ubuntu and I.

---

### Post by bodhi.zazen on 2009-06-30
Also, FYI, in the future, when you are having a problem with an application, you may get additional information if you run the application frm the command line.

```
firefox
```

Although the error message may not mean much to you, post it here and see if anyone can offer assistance.

---

### Post by Crunchy the Headcrab on 2009-06-30
Thank you.  I tried that and all it said is "Segmentation Fault".   It appears to be working now though and I don't know how to replicate the error.  I'd rather not replicate it I suppose \\:D/

---

