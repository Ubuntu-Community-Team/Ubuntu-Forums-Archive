---
title: "youtube and hulu lag with ubuntu"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by dlion64 on 2009-01-10
I've tried ubuntu hardy and intrepid. I've tried kubuntu and xubuntu and they all lag when it comes to using youtube, hulu, and even some dvd's. How do i remedy this.

SPECS:
CPU: AMD 3000+ 2.16gig
RAM: 960MB
Video card: Not sure but its the one that came with the system. It's Nvidia GeForece4
Hardrive: 160gigs
I've tried using 2gigs of swap memory i've tried using 1gig of swap. I've tried deleting as much off the os as i can. I even tried opera and it would still lag. Can this be fixed?
Oh and I'm dual booting XP and have no problem with XP. But I would like to stay away from windows as possible and learn more about linux. Can some one help me.

---

### Post by JoshuaRL on 2009-01-10
What Ubuntu version are you running, 32bit or 64bit?  And what version of flash are you using?  Actual flash or gnash?

---

### Post by dlion64 on 2009-01-11
currently i have ubuntu 8.10 but it also lagged with ubuntu 8.04 and it's 32bit. i tried 64 bit but something in my system isn't 64bit so it won't boot up with the start up disk. the computer is about 5 years old.

---

### Post by dlion64 on 2009-01-11
oh and i'm using flash non free from the medibuntu repo.

---

### Post by kansasnoob on 2009-01-11
First run this command in Accesories > Terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

Then add Flashblock, not the one from the repos!

In Firefox go to Tools > Add-ons > Get Add-ons. Search for and install Flashblock 1.5.7.1.

Then restart Firefox by going to File > Quit!

---

### Post by dlion64 on 2009-01-11
I download ubuntu-restricted extras and flashblock from mozilla but it still lags. Maybe i need more memory or a better video card. What do you all think?

---

### Post by kansasnoob on 2009-01-11
> **dlion64 said:**
> I download ubuntu-restricted extras and flashblock from mozilla but it still lags. Maybe i need more memory or a better video card. What do you all think?

Did you restart Firefox?

Next go to System > Admin > System Monitor and click the Resource tab. That should give you an idea how much of your system resources are being used,

---

### Post by JoshuaRL on 2009-01-11
> **dlion64 said:**
> I download ubuntu-restricted extras and flashblock from mozilla but it still lags. Maybe i need more memory or a better video card. What do you all think?

Now that you mention it, what are your system specs?

---

### Post by dlion64 on 2009-01-11
SPECS:
CPU: AMD 3000+ 2.16gig
RAM: 960MB
Video card: Not sure but its the one that came with the system. It's Nvidia GeForece4
Hardrive: 160gigs

---

### Post by dlion64 on 2009-01-11
oh and i have an AU31 mother board. it read 333MHz

---

### Post by RonaldMcDollars on 2009-05-04
I think the DVD skipping is probably a separate issue. I'd say you might want to try investigating your network connectivity.  If you're wireless, try wired and vice versa to see if you can replicate the problem over different connections.  

I have a similar problem with streaming media (mostly hulu) on my home wireless network only, but my wired connection is fine and both wired and wireless at work are fine.  It may have something to do with the way that network-manager is attempting to communicate with your router.  If you're not on Jaunty you could try disabling IPv6.

---

### Post by Durden on 2009-05-05
Are you running compiz? If so disable it. I've had major problems with compiz and flash in 8.10.

---

### Post by jsprz8382 on 2009-05-19
I have the same problem someone please help bump.

---

### Post by LowSky on 2009-05-19
> **jsprz8382 said:**
> I have the same problem someone please help bump.

If you going to jack a thread please give us more info then "I have the same problem"

We need you computer specs, what version of ubuntu, and how you installed flash.

---

### Post by timcredible on 2009-05-19
flash inside of firefox is a major cpu hog.  try one of the firefox add-ons that allow you to save a flash video, then double-click it from the file browser, bet you money it plays flawlessly.  as a permanent fix, install 9.04, it's quicker for everything, including flash video, and it may give you enough of a performance boost so you can watch youtube.

---

### Post by mike555 on 2009-05-19
I wonder if this is just a Mozilla thing , I finally gave up and installed Opera for watching full screen movies ....

---

