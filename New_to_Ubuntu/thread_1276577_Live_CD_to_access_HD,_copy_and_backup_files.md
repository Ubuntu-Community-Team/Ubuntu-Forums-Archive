---
title: "Live CD to access HD, copy and backup files?"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by carusoswi on 2009-09-27
So, I've posted this problem where I installed Ubuntu Studio from synaptic onto my son's laptop computer running Ubuntu 9.04.  Now, his desktop disappears whenever we boot into Ubuntu (Vista is still working normally).

In the event I don't find a solution to the disappearing desktop problem, I'd like to be able to just access his Ubuntu HD partition, copy any important files to another partition or an external drive, then simply reinstall Ubuntu 9.04.  

Is that possible with a live CD (accessing his HD to salvage files)?

Thanks.

Caruso

---

### Post by Merk42 on 2009-09-27
Yes, just get a LiveCD and choose "Try Ubuntu without making changes"

Once everything is up you'll be able access partitions like you would as if it were normally installed.

---

### Post by carusoswi on 2009-09-27
> **Merk42 said:**
> Yes, just get a LiveCD and choose "Try Ubuntu without making changes"

Once everything is up you'll be able access partitions like you would as if it were normally installed.

Thanks, Merk.  That's a bit of relief. Now I'm searching the forum to see just how to make a live CD (it's been a while).  I'm working from within Windows, and don't remember if I need to extract the Winrar archive or just burn it with a bootable switch as is to a CD.

It's amazing, when I first got into Ubuntu, I soon became fairly competent at installation chores, since that is mostly what I did.  Install, reinstall, etc.

It's been so long since I did any of this, I don't remember exactly how it's done.  No biggie, though.  I'll figure it out.

Thanks again for the reply.

Caruso

---

### Post by gradinaruvasile on 2009-09-27
Just d/l the cd image (.iso format) and burn it on a cd with nero or something similar (like [imgburn]("http://www.imgburn.com/index.php?act=download")).
Then boot from that cd. 
It is possible to make an usb stick image (there is an app for this included in ubuntu), but cannot say exactly how it is done from windows...

---

### Post by carusoswi on 2009-09-27
> **gradinaruvasile said:**
> Just d/l the cd image (.iso format) and burn it on a cd with nero or something similar (like [imgburn]("http://www.imgburn.com/index.php?act=download")).
Then boot from that cd. 
It is possible to make an usb stick image (there is an app for this included in ubuntu), but cannot say exactly how it is done from windows...

Hasn't worked so far.  Cd's won't boot for some reason.

---

### Post by carusoswi on 2009-09-27
So, I have booted up this problem laptop using an 8.10 live cd.  I can browse the drives, but, how do I gain permission to explore the home folder so I can get to the desktop where many of the data files are apparently stored?

Caruso

---

### Post by carusoswi on 2009-09-27
> **carusoswi said:**
> So, I have booted up this problem laptop using an 8.10 live cd.  I can browse the drives, but, how do I gain permission to explore the home folder so I can get to the desktop where many of the data files are apparently stored?

Caruso

Well, there may be easier ways to accomplish this, but what I did was boot into recovery mode, then drop to Root Shell Prompt (I think that's what it's called . . . something close), I then created a new directory high on the directory tree (as high as I could be which is where I reckoned booting with a live CD would put me.  Since in this shell I could navigate to all areas of the HD, I copied those directories (including the original Desktop) as folders into this newly created directory.  I then rebooted using the 8.10 Live CD which put me on a 'desktop' from where I could browse available media.  Sure enough, my created directory was available and accessible, and my external drives showed up as well, so I simply copied the new directory over to one of the external drives.

Now, I'm re-downloading 9.04 and plan on making a new live cd from which to re-install the OS (it was originally installed as an upgrade).

Not pretty, but, at least we saved the data.

Caruso

---

### Post by carusoswi on 2009-09-27
I would like to have marked this as SOLVED, but can't figure out how to do it.

In any event, files were saved, OS reinstalled.  Issue is solved.

Still can't figure out how things got so messy.

Caruso

---

