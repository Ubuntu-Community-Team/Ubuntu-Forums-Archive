---
title: "Cannot boot into older kernel after Nvidia driver update"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by beew on 2011-07-17
Hi,

I usually keep a few older kernels around just in case. My current kernel in my 11.04 install is 2.6.39. The other day I had an update for the Nvidia driver to 275.19 from the x-swat ppa using Synaptic while in kernel 2.6.39. After reboot everything works fine in 2.6.39 but I can no longer boot into older kernels. If I choose say, 2.6.38.10 I get the error

> mountall: plymouth command failed
mountall: disconnected from plymouthI don't necessary need to fix this as 2.6.39 is working flawlessly, but it bothers me that this happens because it shouldn't. I would appreciate any insight, thanks.

 In Maverick I have a similar but different situation. I didn't update to the latest Nvidia beta, but latest stable one from the one before it. In Maverick my current kernel is 2.6.38 (which I installed manually). I can still log into the earlier ones but without  the desktop. Running startx produces the error message that the Nvidia driver is not available and the fatal error that there is no screen. 

I then get an update for kernel 2.6.35.10 from the proposed repository and everything works again there too, but there is still no desktop for 2.6.35.09 and 2.6.36 (which I installed manually)

---

### Post by wildmanne39 on 2011-07-17
Hi, after the updates a couple of days ago many people can not boot into the 2.6.38.10 kernel, that is when the kernel was updated so that is probably the problem, it may not be the nvidia driver.

---

### Post by beew on 2011-07-17
> **wildmanne39 said:**
> Hi, after the updates a couple of days ago many people can not boot into the 2.6.38.10 kernel, that is when the kernel was updated so that is probably the problem, it may not be the nvidia driver.

Hi,

Thanks for the reply. 

However I don't think it is the kernel update because I can't log into 2.6.38.8 either (with the same error message re. plymouth), but 2.6.39 is ok (the kernel I was logged into when upgrading the Nvidia driver) To clarify, I am talking about the Natty problem here (the Maverick problem may be a bit different: see below)

On the other hand I have another test install of Natty  with only the nouveau driver installed from the xorg-edgers ppa (running on the same computer) and I can log into all previous kernels with no problem.

I have not had any kernel update for a while  but there have been two Nvidia updates in the last week or so. One update to 275.09 (same with Maverick) and the result is that I can only log into command line in previous kernels (current one is fine), and then another update to 275.19 (beta) and I can't even log into the old kernels at all (with plymouth error) 

With my Maverick install I only upgraded to 275.09 so I can still log into older kernels but cannot start x. But then after the Nvidia upgrade came another kernel upgrade for 2.6.35.10 and that one is now working.  I upgraded the Nvidia driver when logged into 2.6.38 which I installed manually, that has always been fine.

---

### Post by beew on 2011-07-18
Ok,

I logged into the current kernel and reinstalled the earlier ones (if they are available) and that solved the problem (for both Nvidia 275.09 and 275.19)  So in Natty I logged into kernel 2.6.39.0 and reinstalled 2.6.38.10 from Synaptic and now I can log into both without problem.

It is probably a bug with the Nvidia driver from the x-swat ppa.

---

### Post by beew on 2011-07-19
Don't know what happened, after the tinkering last night boot time for Maverick has some how improved tremendously. It used to take 25 to 30s to boot but now it takes only 10 -15! It was already quite fast and now it is super fast. :)

---

### Post by wildmanne39 on 2011-07-19
Hi, I do not know either but if you figure it out let me know.

---

