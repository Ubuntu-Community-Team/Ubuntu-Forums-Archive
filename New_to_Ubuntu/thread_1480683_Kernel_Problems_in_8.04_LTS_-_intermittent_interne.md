---
title: "Kernel Problems in 8.04 LTS? - intermittent internet"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by anothernewuser on 2010-05-11
Last week-ish ... I got an update for 8.04 LTS and the 2.6.24-27-generic kernel was replaced by 2.6.24.27-386.

Ever since I've had some real oddities.

The new kernel ... sometimes works fine and sometimes has no internet connectivity at all ... it's like the internet isn't even there.  The internet is there though because it still works through Windows and perhaps more oddly it still works through the old (generic) kernel.

I would consider going back to the generic kernel I suppose(if i knew how) or maybe reinstalling the new one except I'm a bit put off trying by two things:

1) The dire warning from Synaptic when I click on the kernel which I don't entirely understand: 
"You likely do not want to install this package directly. Instead, install
the linux-generic meta-package, which will ensure that upgrades work
correctly, and that supporting packages are also installed."

2) When I do boot into the generic kernel now (which I do because it still has internet access - I'm using it now) there are now video issues. It starts in an 800x600 resolution and during the boot I am offered a chance to configure the video card (GE Force fx 5500) but none of the options seem to work so I just cancel and go with the lower resolution.

Sometimes when I'm done with the generic kernel I'm able to then restart and use the internet through the new kernel.  It's all a bit - odd.

I suppose what I'm asking is ... Is there some way to make either of these kernels fully functional or should I just limp through it hoping a future update (or upgrade!) fixes this?  

I can only imagine that the generic kernel is going to keep getting updated and replaced if I do put it back in place and it now has video issues the newer kernel doesn't... so I guess the best option is to make the new one work?

I'm happily mystified by all this and would appreciate any and all advice.

Thankee kindly :)

---

### Post by Ozymandias_117 on 2010-05-11
The only suggestion I can offer, is stick with the old one, and reinstall your graphics drivers, that should fix your resolution problems. I have no idea about the internet issues with the new kernel.

---

### Post by anothernewuser on 2010-05-11
Hmmm ... that particular option hadn't even occurred to me.

It is good to have access to other people's brains through here.

Alrighty, that goes on my to do list. Will give it a go when I'm not in such dire need of this connection ;)

Thanks so much for that idea :)

---

### Post by anothernewuser on 2010-05-13
Scoured old threads and found this nifty little workaround:

sudo dhclient -r eth0
sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient eth0

It restores internet access for me. Not sure why it works, not even entirely sure what it means.. but it works.  It's not a permanent solution but when I turn on the computer and find I have no internet this gets it back up and running quickly and easily.  I'd prefer a more permanent solution and will seek one out someday but if you have similar trouble I like this one.  It's simple and doesn't require poking around at the root level(scares me a bit to do that to be honest), installing/uninstalling software or changing hardware.


Going to try to figure out how to mark this thread [Solved].

Yay! Figured out how to do that too!

Enjoy.

---

