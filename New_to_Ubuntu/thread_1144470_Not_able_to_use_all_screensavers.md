---
title: "Not able to use all screensavers"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by raguru on 2009-04-30
Hi,

I am using Kubuntu 9.04.  I think back when I upgraded to Kubuntu 8.10, initially I was not able to find any screensavers.  Then I was able to get some to work, but I don't remember how I did it.  

Now, when I look under /usr/lib/xscreensaver, I find lots of screensavers, like cubestorm, flying toasters, gears, etc.  But when I go under System Settings and go to Screensaver, I can't find them.  I have choices only for a few of them.  Maybe a third of them.  I would love to get the others to work.

Can anyone tell me how I can get those screensavers to show up so that I can user them?  

Thanks in advance.

-Raghu

---

### Post by llamabr on 2009-04-30
You have to install them.  You can do so individually.  I thought I remembered a package that comes with a million of them, but I'm not seeing it.

Anyway, install with apt or synaptic.

---

### Post by Ubuntiac on 2009-04-30
I think you may need to install the kscreensaver-xsavers packages. You should be able to see them in System Settings -> Add / Remove Software / Software Management then search for kscreensavers.

---

### Post by raguru on 2009-04-30
Thanks to both for your replies.  I will try that and get back.

-Raghu

---

### Post by raguru on 2009-05-02
I finally got a chance to look at Synaptic and there were some installed under screensaver, but some were not.  I don't remember what were there before and what I added.  I also logged into GNOME and saw that all the screensavers were available there.  So, back in Kubuntu, I added some packages and now its all working well.  This is what I have now:

kscreensaver
screensaver-default-images
xscreensaver-data
xscreensaver-gl
xscreensaver
ktux
kscreensaver-xsavers-webcollage
kcometen4
xscreensaver-gl-extra
gnome-screensaver
xscreensaver-data-extra
kscreensaver-xsavers
kscreensaver-xsavers-extra
flowerattack-0.3
cmatrix
electricsheep

Thanks again for your help.

-Raghu

---

