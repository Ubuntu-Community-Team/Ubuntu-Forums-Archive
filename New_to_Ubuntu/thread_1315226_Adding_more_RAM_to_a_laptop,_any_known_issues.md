---
title: "Adding more RAM to a laptop, any known issues?"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by Anuovis on 2009-11-05
Hello,
I just wanted to check if adding more RAM on a computer with already installed Ubuntu could cause any problems.

I am using Dell Inspiron laptop with Ubuntu 9.10. I currently have 512 MB of RAM and thinking about adding 1 GB more. 
Apart from regular Ubuntu software I also want to install Virtual Machine with Windows XP. 
My Swap partition is 3 GB.

I am just worried if a sudden change of the memory in the system can cause any odd things to these operating systems.

Any clarifications or links to possible issues would be appreciated.

---

### Post by wilee-nilee on 2009-11-05
shouldn't be a problem, just make sure your not installing more ram then the computer will use, your probably not but a Google search will get you the information.

---

### Post by Anuovis on 2009-11-05
No, my laptop can support up to 2 GB. Physically it is not a problem. Thank you.

---

### Post by NickJones on 2009-11-05
Ubuntu is *VERY *tolerant for changing  hardware, I had it installed on a USB and I would boot if off my sisters Dell Mini 9 whenever I was using it, with no hassles. You should be fine.

---

### Post by louieb on 2009-11-05
> **Anuovis said:**
> Apart from regular Ubuntu software I also want to install Virtual Machine with Windows XP. 
Have 1.5GB in my laptop running Jaunty. XP is installed inside [VirtualBox]("http://www.virtualbox.org/"). - Works without any noticeable slowdown.

---

### Post by wilee-nilee on 2009-11-06
> **Anuovis said:**
> No, my laptop can support up to 2 GB. Physically it is not a problem. Thank you.

Since this computer has 2 ram slots if it was me I would max it out then you could run a virtual quite easily as well.

---

### Post by SunnyRabbiera on 2009-11-06
Adding RAM in linux seems to be a non issue, cant say the same about windows.

---

### Post by Anuovis on 2009-11-06
Thank you all for the answers :)
Does not seem to be a complicated issue, so marking thread as solved.

---

### Post by mikechant on 2009-11-06
I know this is solved, but the following may be relevant for others reading it: If you upgrade your RAM so it is bigger than your swap partition (it isn't in this case), and you want to use the hibernate feature, you must increase your swap space to be at least as big as your RAM.

---

### Post by adempewolff on 2009-11-06
a couple months ago I upgraded the ram in my laptop and suspend to RAM (*not* suspend to disk, that continued to work fine because I had sized my swamp partition in anticipation of the larger amount of RAM) stopped working.  When I installed the Karmic beta on another partition suspend to RAM started working again.  I don't know whether upgrading the main one to Karmic will make it work again or if it needs a fresh install.  anyway, I think this was probably a pretty isolated issue so upgrading should go well for you!

---

### Post by Paqman on 2009-11-06
> **Anuovis said:**
> I currently have 512 MB of RAM and thinking about adding 1 GB more.

That will work fine, but you'll be missing out on the benefit of having dual-channel RAM. When you use RAM in identical pairs they work a lot faster.

---

