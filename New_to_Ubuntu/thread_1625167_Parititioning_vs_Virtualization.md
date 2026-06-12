---
title: "Parititioning vs Virtualization"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by echo314 on 2010-11-18
Hello,

I use computers for lots of things. The problem is, I tend to move quickly from program to program, version to version, and quick-fix to ugly-hack. The only way I hold down the same planner over time is using a paper one, with no digital involvement. That is the only way I've found I can commit to a particular way of doing things. 

My problem being, I very quickly muddy up the OS I'm using. I see two solutions. 

1. Use separate partitions for different OS's. This is how I manage now, but it gets frustrating when I need to reinstall Windows, or install an OS I'm completely unfamiliar with (BSD for example). I usually manage to bork the boot loader, MBR, or something related, which can be a pain to fix (It is hard for me to keep track between Windows, Linux and BSD partitioning schemes and jargon). 

2. Virtualization. I'm less familiar with this, but it seems that there are some technical limitations that could get annoying (Netflix being choppy, or some games not working). Also, I worry that if I start using the base OS to get something done that won't work on the virtual OS, I am back to square one, messing up the base OS. However, reverting to clean installs seems very, very easy here, which I would LOVE. 

Anyone here in the same situation I am in (compulsively trying new ways of doing things)? How did you address the situations so you could revert to clean installs, with minimal pain (and using different OSs where required, as I need to keep Windows for school related work).

---

### Post by Blivia on 2010-11-18
Honestly Virtual Machines are the way to go, If you're worried about gaming, you can use XP as your main installation, and set up multiple virtual machines. That way, if you want to game you can simply close your virtual machine, and game on Windows XP. (That is assuming you do heavier gaming, like first person shooters, etc.) For someone like you, I'd HIGHLY suggest running a virtual pc. You can simply backup your Virtual harddrives, and mess around with the system all day long, and a re-install of the system only takes a couple of minutes. You even get to keep your personal settings.

I use a virtual machine on my computer, it's a no-risk way of doing things. The software might take a little bit to learn, but otherwise it's just like running another operating system as a program via windows (Or linux if you choose that path.)

Whatever you end up doing, I wish you the best of luck. ^_^

---

### Post by snowpine on 2010-11-18
Why not choose one distro (Ubuntu LTS, maybe) and stick with it? :)

---

### Post by echo314 on 2010-11-18
Thanks for your thoughts. Would you recommend Ubuntu as my base OS, or should I try for something more lean? I could see maybe an Windows partition for when I need it, plus a separate partition with a base OS, virtualizing Linux and Windows. Although, I don't want to make this more complicated that it has to be. Having Windows as my base just seems like a bad idea, as its soo much harder to keep secure.

---

### Post by Blivia on 2010-11-18
Well Snow, even a newbie like myself knows the answer to that. How do you know what you'll like without trying it? Sometimes for people one operating system doesn't cut it, or they just want to try, and mess with new operating systems without having to completely re-install the OS when they break it. A virtual machine is probably the best way to go- It's what I've been doing most of my Ubuntu testing on, so I don't kill my real install.

If I haven't tested something in my VM, odds are my real install isn't going to be a test machine. It's so much more of a pain to install a full O/s, then to simply replace a virtual harddrive. ^_^

---

### Post by echo314 on 2010-11-18
> **snowpine said:**
> Why not choose one distro (Ubuntu LTS, maybe) and stick with it? :)

I don't stick with software long enough. For example, even though I currently am more familiar with Windows, but also use Linux, I've been curious about how BSD works (not just OS level, but design philosophy and such). If I tried to install that on my HD in a partition (or slice, or w/e they call it) I would probably overwrite the whole disk somehow. Not that I'm clueless, I always partition manually with Ubuntu, but I don't know lots of things.. After a few months, I need to hit the reset button to regain my sanity!

---

### Post by asmoore82 on 2010-11-18
Obviously that last statement about *needing* Window$ is bollocks.

But notwithstanding that, desktop virtualization is totally awesome.
I highly recommend VirtualBox OSE - as long as your Real "base OS" is a Real OS, of course!

---

### Post by echo314 on 2010-11-18
> **asmoore82 said:**
> Obviously that last statement about *needing* Window$ is bollocks.


If Windows is required to run software required for my coursework, how is my need untrue?

EDIT: Scratch that, I don't want to derail this thread. I want to focus on solutions. 

So, does virtualizing Ubuntu on top of a base OS of Ubuntu sound crazy, or is this a good way to approach this?

---

### Post by Blivia on 2010-11-18
> **echo314 said:**
> If Windows is required to run software required for my coursework, how is my need untrue?

EDIT: Scratch that, I don't want to derail this thread. I want to focus on solutions. 

So, does virtualizing Ubuntu on top of a base OS of Ubuntu sound crazy, or is this a good way to approach this?


I believe that's the best way to approach this situation. Windows is secure if you know how to use it, and Linux runs nice, and snappy in a Virtual Machine. As suggested, VirtualBox will get the job done, and it's pretty safe. You can set up multiple virtual drives, with multiple operating systems, so you don't need to worry about "Dual booting" them, and such, as they'll all be loaded as different hard drives. It's worth looking into, and it's fairly safe- I sometimes brows the web through a Virtual machine. Can't get much safer then that. ^_^

---

### Post by echo314 on 2010-11-18
I was particularly concerned about overhead that is used to run Ubuntu, as its not a particularly light distributon, and I have 4 GB of RAM to work with.

If you think its suitable, then I shall try that out.

---

### Post by nlsthzn on 2010-11-18
The limitations in Virtualization are more often than not graphical in nature (3D acceleration etc. doesn't work and you always get performance hits in 2D)... so ensure the base install can satisfy any graphical needs you may have and then have fun with all the virtual machines your heart desires...

Oh, 4GB is overkill for any GNU/Linux installation currently, you can easily run 2 to 3 virtual machines in that... but for best performance limit it to 1 at a time :)

---

### Post by Blivia on 2010-11-18
I run it on a 2GB system, on an old Pentium D system. I give it 512 MB of RAM, and it doesn't even use half of it. Your machine should run it like a champ, it's a little -Slow- sometimes on my computer, but I'm obviously out of date. I think you'll be happy with what you find- If not then hey, blame me. XD

---

