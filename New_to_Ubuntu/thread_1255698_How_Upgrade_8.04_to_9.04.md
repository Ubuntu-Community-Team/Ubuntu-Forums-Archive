---
title: "How Upgrade 8.04 to 9.04"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by L33Tsauce on 2009-09-01
HOW DO I DO THIS. I have searched the interwebs and there is no good tutorials I am a newbie and i can not program so please list in steps!

---

### Post by zkriesse on 2009-09-01
[http://ubuntuforums.org/showthread.php?t=1189030](http://ubuntuforums.org/showthread.php?t=1189030)

Actually just press ALT+F2 then enter update-manager -d. It should bring up the next distro for you...since you're on 8.04 you'll have to do it twice though...

---

### Post by slakkie on 2009-09-01
```


# Install something so we can upgrade via the command line
# Can be skipped on 8.10 to 9.04
$ sudo aptitude install update-manager-core

# Get everything up2date
sudo aptitude update && sudo aptitude safe-upgrade

# The actual upgrade
sudo do-release-upgrade

# reboot due to kernel update

```

Do this one time for 8.04 to 8.10 and one time for 8.10 to 9.04.

---

### Post by Paqman on 2009-09-01
The upgrade path is 8.04 > 8.10 > 9.04, so yes you'd have to upgrade twice. It'd probably be quicker to just back up your data and home folder and reinstall from the 9.04 LiveCD. 

Personally i'd hold off doing that since the next version will be released in about 8 weeks.

---

### Post by zkriesse on 2009-09-01
That soon? I thought it was a little longer...how's the Karmic Koala? I'm asking because I noticed that you have it as your distro

---

### Post by vincent_est on 2009-09-01
you can also download an ISO file to install from CD at
[http://www.ubuntu.com/getubuntu,]("http://www.ubuntu.com/getubuntu")

I do that...

---

### Post by zkriesse on 2009-09-01
I think he's got enough answers now! LOL not that is was a hard question.

---

### Post by Paqman on 2009-09-01
> **Zachk18 said:**
> That soon? I thought it was a little longer...how's the Karmic Koala? I'm asking because I noticed that you have it as your distro

When it's finished, it'll be great. New bootloader, new (sexy) login screens, Ext4 by default, Empathy/Gwibber/UbuntuOne all integrated into the desktop, the new Software Store. Lots going on in Karmic. Still a fair bit of rough around the edges though, my machine won't suspend or print right now, and there's ongoing weirdness with Devicekit.

---

### Post by R_W322 on 2009-09-01
Honestly, My advice back-up your important files go to [www.ubuntu.com]("http://www.ubuntu.com") and download 9.04 Jaunty Jackalope upgrading can get sketchy at times and might not preform as well as clean install I dunno thats just what I'd do or stick with Hardy 8.04 still Whatever 10.4 

RYAN.WDZIECZNY

I'm honestly still undecided if I want to stick with 9.04 or 8.04 until 10.4 comes out. In my opinion I think you should stick with Hardy Heron just my opinion though.

---

### Post by zkriesse on 2009-09-04
> **Paqman said:**
> When it's finished, it'll be great. New bootloader, new (sexy) login screens, Ext4 by default, Empathy/Gwibber/UbuntuOne all integrated into the desktop, the new Software Store. Lots going on in Karmic. Still a fair bit of rough around the edges though, my machine won't suspend or print right now, and there's ongoing weirdness with Devicekit.
I had tried the Alpha version and within 5 minutes I had three cups errors just by editing my clock/weather in the taskbar...I could edit it just fine but closing it cause serious issues. Plus firefox wouldn't start right....but hey, it's still in development so I completely understand.

---

