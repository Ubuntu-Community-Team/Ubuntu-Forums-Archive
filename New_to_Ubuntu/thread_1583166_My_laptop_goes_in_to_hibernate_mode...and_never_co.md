---
title: "My laptop goes in to hibernate mode...and never comes back."
date: 2010-09-27
forum: New to Ubuntu
---

### Post by Zanderist on 2010-09-27
When ever I hibernate my laptop it freezes, and will only come back on after I shut it down.  I think this may have to do with built in graphics card not restarting. (nivida make by the way) On the other hand I also think the operating system just commits suicide.


Another issue I have:
Sometimes when I boot up Ubuntu I get this busy-box error (Ubuntu does not boot up) and I end up pressing ctrl-alt-delete to restart. Then I try recovery mode, and it starts up just fine. However, sometimes I can start up Ubuntu with out having to go through recovery mode.

---

### Post by andrewthomas on 2010-09-30
> **Zanderist said:**
> 
Sometimes when I boot up Ubuntu I get this busy-box error (Ubuntu does not boot up) and I end up pressing ctrl-alt-delete to restart. Then I try recovery mode, and it starts up just fine. However, sometimes I can start up Ubuntu with out having to go through recovery mode.

For this issue I would purge and reinstall grub2 from a liveCD

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by mastablasta on 2010-09-30
> **Zanderist said:**
> When ever I hibernate my laptop it freezes, and will only come back on after I shut it down. 
 
this is not logical. hibernate looks like computer has shut down. then you turn it on with the "on" button.
 
Do you mean suspend mode?

---

### Post by julio_cortez on 2010-09-30
Just a guess (because it happened to me): have you tried to modify Plymouth's resolution recently?
If so, using the uvesafb framebuffer might lead to having trouble when resuming from suspend (I didn't find an Ubuntu bug report, but it's described in [this Gentoo bug report]("http://bugs.gentoo.org/202756")).

---

### Post by Zanderist on 2011-02-07
Now I'm on a new laptop, and the same thing is still happening. Ubuntu 10.10 this time.

The only thing major I have done was activate the graphics driver.

I managed to catch what was printed on the screen while the lip was closed, and that was not enough swap space.

---

### Post by Zanderist on 2011-02-08
Anyone? Laptop either suspends or hibernates and never comes back, until force restart.


This is what I have.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/558973](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/558973)


Found this, will test:
[http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)

Report:
Nothing changed for me.

Found this, will test:

[http://ubuntuforums.org/showpost.php?p=10364339&postcount=16](http://ubuntuforums.org/showpost.php?p=10364339&postcount=16)

Report:
Failed, ended up taking battery out in order to boot into bios screen.

Testing: 
Removing ATI/AMD proprietary FGLRX graphics driver.

Report:
Was removed, suspend/hibernate now works.

Conclusion:
Looks as if ATI/AMD proprietary FGLRX graphics driver, causes the suspend/hibernate/resume script to fail.

---

### Post by throwback1718 on 2011-02-21
this hasnt happened to anyone else?

With my laptop when I go to suspend mode, the laptop would start back up but it seems that everything would come back aside from the monitor. 

with hibernate, it doesn't even go into hibernate at all, it acts as if I selected the "lock screen" option.

---

### Post by throwback1718 on 2011-02-21
any tips for my situation?

---

### Post by Zanderist on 2011-02-22
Now I get a failed to suspend dialogue box.

---

