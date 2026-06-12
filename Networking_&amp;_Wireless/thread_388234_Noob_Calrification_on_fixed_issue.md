---
title: "Noob: Calrification on fixed issue"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by doddi on 2007-03-19
Hi Peeps,

I was just after some clarification on an issue I have already managed to solve.

I was having the usual wireless issues with my bradcomm chipset and I finally managed to get it working after reading some of the threads on here. I used the ndiswrapper built from source. After I finally got my wireless working and onto the net Ubuntu popped up with all the security updates required. I proceeded and it took my kernel up to the latest version (from.10 to .11 I think), after rebooting I found that I had lost my wireless again.

I could still boot the old kernel and my wireless would work fine.
To fix the issue I removed the ndiswrapper and rebuilt from source (using the latest kernel headers) and followed the same steps, at the end of it I had my wireless was once again back up and running.

My question is:
1. Is there a more elegant approach I could have taken?
2. Did it not work simply because the source was built using the old linux headers?
3. Each time I upgrade to a new kernel will I have to repeat this exercise?
4. Is there a way to make the ndiswrapper work with both kernels? or can I install ndiswrapper twice? so if one kernel failed I could still rescue my data without needing to go through this problem


Sorry for the noob question(s) but at least I managed to resolve the issue. Any help would be appreciated

Regards,
doddi

---

### Post by spd106 on 2007-03-19
1. Not really
2. Yes
3. Yes
4a. No
4b. Yes, it's the kernel module that needs building, the user space tools should stay the same. Check out /lib/modules/`uname -r`/kernel/drivers/net for each kernel.

Sadly the in kernel ndiswrapper version was always going to get old quickly as the pace of development doesn't slow down, even in just a few months totally new versions are released with better support for more devices. The flexibility of being able to build new versions is a great asset. It's certainly better than not working at all.

If you have a card that works well with the supported version then you won't have to worry as it will always work after a kernel update (except for a major bug).

It's unlikely that you will ever be unable to access your data, just remember to keep a live/desktop cd handy (if Ubuntu is too big then damn small linux can be useful). If a kernel really did fail, I think you would have bigger problems than getting the wireless working.

---

### Post by doddi on 2007-03-20
Thanks for the informative replay spd106 I really appreciate it.

I am just happy that at least I understood the reasons behind it..linux is finally starting to make some sense :) 

cheers

---

