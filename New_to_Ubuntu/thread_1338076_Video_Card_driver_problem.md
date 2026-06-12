---
title: "Video Card driver problem"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by Itzamna36 on 2009-11-26
Recently I installed the radeonhd drivers for my ATI X1650 card in 9.10.  I had a couple problems in the process which I'll outline later, but once it was installed the performance on my computer was up overall.  

I restarted my PC today, something I rarely do, and suddenly I was back to the radeon default driver.  Now I can't seem to switch back to the radeonhd driver.

I'm thinking part of this might be why.

When I installed the radeonhd driver, I found I had no xorg.conf.  I followed the instructions [here]("http://www.linuxquestions.org/questions/linux-newbie-8/xorg.conf-empty-710113/page2.html#post3636467") and messed up slightly.  I made a typo and directed the file to corg.conf instead of xorg.conf.  Everything seemed to work fine though and I changed the driver line in xorg.conf, or in my case corg.conf and everything was good other than flash for some reason but that's a whole different problem.

After the restart the corg.conf file now had the default radeon driver listed.  I changed it back to radeonhd and nothing happened.  Thinking my typo earlier was possibly messing something up I went back and used those same instructions to properly have a xorg.conf file.  Changing the driver line in this one seems to do nothing as well.  

I do have the corg.conf file still and I have no idea if this could be causing problems.  

One other note, after I restarted, xserver-xorg-video-radeonhd was no longer installed which I found quite strange.  I reinstalled that along with reinstalling the radeonhd per instructions at [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

I'd appreciate any help with this problem.  It's the first one since my switch to Ubuntu I haven't been able to find the answer searching.  Just let me know if you need more info.

Thanks.

---

### Post by Itzamna36 on 2009-11-27
Anyone able to help?

---

### Post by sandyd on 2009-11-27
> **Itzamna36 said:**
> Recently I installed the radeonhd drivers for my ATI X1650 card in 9.10.  I had a couple problems in the process which I'll outline later, but once it was installed the performance on my computer was up overall.  

I restarted my PC today, something I rarely do, and suddenly I was back to the radeon default driver.  Now I can't seem to switch back to the radeonhd driver.

I'm thinking part of this might be why.

When I installed the radeonhd driver, I found I had no xorg.conf.  I followed the instructions [here]("http://www.linuxquestions.org/questions/linux-newbie-8/xorg.conf-empty-710113/page2.html#post3636467") and messed up slightly.  I made a typo and directed the file to corg.conf instead of xorg.conf.  Everything seemed to work fine though and I changed the driver line in xorg.conf, or in my case corg.conf and everything was good other than flash for some reason but that's a whole different problem.

After the restart the corg.conf file now had the default radeon driver listed.  I changed it back to radeonhd and nothing happened.  Thinking my typo earlier was possibly messing something up I went back and used those same instructions to properly have a xorg.conf file.  Changing the driver line in this one seems to do nothing as well.  

I do have the corg.conf file still and I have no idea if this could be causing problems.  

One other note, after I restarted, xserver-xorg-video-radeonhd was no longer installed which I found quite strange.  I reinstalled that along with reinstalling the radeonhd per instructions at [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

I'd appreciate any help with this problem.  It's the first one since my switch to Ubuntu I haven't been able to find the answer searching.  Just let me know if you need more info.

Thanks.
```

sudo mv /etc/X11/corg.conf /etc/X11/xorg.conf

```then edit xorg.conf again.
p.s. there is no xserver-xorg-video-radeonhd by default
you have to add this PPA [https://launchpad.net/~tormodvolden/+archive/ppa]("https://launchpad.net/%7Etormodvolden/+archive/ppa")
to get that package.

oh, and if your using karmic, you use this PPA [https://launchpad.net/~xorg-edgers/+archive/drivers-only](https://launchpad.net/~xorg-edgers/+archive/drivers-only)

---

### Post by Itzamna36 on 2009-11-27
Thanks a bunch carlee. :) 

I was going to use that code but I wasn't 100% sure if that was correct use of the mv command and figured I'd better ask.  Didn't want to dig a deeper hole without direction.    

Now flash is working with radeonhd so even a second plus.  Thanks again.

---

### Post by Itzamna36 on 2009-11-28
Well this happened again after another restart.  I'm back to having radeonhd as the driver listed in xorg.conf, but I'm running on the radeon driver instead.  

There no longer is a corg.conf file, but is the computer possibly still looking there first since I had it set up that way the first time around?

*Edit*
After messing around a bit, I found it's reverting to using /root/xorg.conf.new after a restart.  When I move it to /etc/X11/xorg.conf I can restart it and it will be using the xorg.conf file.  After a second restart it'll be configuring off of /root/xorg.conf.new again.  How do I make this stick?

---

