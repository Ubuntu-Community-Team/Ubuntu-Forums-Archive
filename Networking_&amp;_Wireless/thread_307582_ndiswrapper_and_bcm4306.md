---
title: "ndiswrapper and bcm4306"
date: 2006-11-26
forum: Networking &amp; Wireless
---

### Post by skale on 2006-11-26
I have a Dell Latitude D600, with a Broadcom 4306 wireless.  Great combo.

It ain't workin. Everything went well, all the way up to where it loaded the module. While the module did load, here is the funky parts of /var/log/messages:
```

Nov 26 19:05:46 localhost kernel: [4294776.938000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
Nov 26 19:05:46 localhost loadndisdriver: loadndisdriver: load_driver(361): couldn't load driver bcmwl5
```

I know the driver is good, it is the recommended one, and it did work on Arch Linux just fine. Arch Linux is too crabby for doing anything important.  For Arch, I built it from source, and it was version 1.28, instead of Ubuntu's 1.8.  Maybe if I build it from source it will work?  
Or have I done something stupid, like forgot something?  I followed the instructions exactly.  

Just to rant, this is the third broadcom chip I have played with.  I threw away the first one, and almost chucked the second as well.  Stupid corporation.

---

### Post by wmatlock on 2006-11-26
Skale,

I had similar problems on a box I built with a LinkSys Card. My solution was to follow the instructions in the following link. [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

I was trying to use Edgy at one point and went back to Dapper and got it working last night.

The main link to all of this info is: [https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

Good Luck

---

