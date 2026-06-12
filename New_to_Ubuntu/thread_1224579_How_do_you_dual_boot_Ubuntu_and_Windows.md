---
title: "How do you dual boot Ubuntu and Windows"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by RJ12 on 2009-07-27
Ok so I wanna know the best way to dualboot Windows XP Pro and Ubuntu 9.04 I heard in the installer you use the Guided install with the slider or to go into Partition Editor or GParted and shrink the windows partition make a ext3 or something with a 3 partition then a swap I think I am completey new to this and want to know step by step how to do this.

---

### Post by arochester on 2009-07-27
Look at "How to dual boot Windows XP and Linux (XP installed first) -- the step-by-step guide with screenshots" on [http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

---

### Post by Michael.Godawski on 2009-07-27
I would suggest going with 

[LIST]
[*][http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)
[/LIST]
meaning installing windows first then ubuntu.

Edit: I am getting slow and old. ;)

---

### Post by Ratscallion on 2009-07-27
> **Michael.Godawski said:**
> [U]
[/U]meaning installing windows first then ubuntu.



That's what I'd to anyway!

---

### Post by RJ12 on 2009-07-27
So I go with the "Guided Option"?

---

### Post by blazemore on 2009-07-27
Yes guided resizes existing partitions and installs Ubuntu alongside.
When you start the computer you can choose between them. You can change the order from within Ubuntu.
It's recommended to install Windows first, as installing Windows after will nuke Ubuntu's bootloader.

---

### Post by Michael.Godawski on 2009-07-27
> **RJ12 said:**
> So I go with the "Guided Option"?

Yes Guided-resize... not guided use entire disk space.


[LIST]
[*]As shown here:[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=3](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=3)
[/LIST]

---

### Post by RJ12 on 2009-07-27
Okay I will do Guided since I already have XP

---

### Post by halitech on 2009-07-27
just make sure you give it more then the default amount of space which seems to be 2.3gig. also, before you resize windows, make sure you defrag at least twice.

---

### Post by philcamlin on 2009-07-27
> **halitech said:**
> just make sure you give it more then the default amount of space which seems to be 2.3gig. also, before you resize windows, make sure you defrag at least twice.

min 4gb on the box to install updates etc
20 gb is plenty unless you save music ectc...

i have 40 gig and ill never fill it up im 53% full and i have a ton of apps installed and 15.3 gb of music

---

### Post by Ratscallion on 2009-07-27
> **blazemore said:**
>  You can change the order from within Ubuntu.


And from within Windows too.

---

### Post by RJ12 on 2009-07-27
Well of to go install but for Ubuntu 9.04 just to note for anybody instead of guided it says install side by side wach other

---

### Post by RJ12 on 2009-07-27
Okay its been at 0 percent at resizing partitons for 15 mins is this normal I dont want to power off the computer its to risky

---

### Post by necromonger on 2009-07-27
i installed on second sata drive work's great

---

### Post by RJ12 on 2009-07-27
Never Mind it partitioned Now i am waiting for the install *waits and is very hyper for it to install*:):):):):KS

---

### Post by Ratscallion on 2009-07-27
> **RJ12 said:**
> Never Mind it partitioned Now i am waiting for the install *waits and is very hyper for it to install*:):):):):KS

Good luck!

---

### Post by Michael.Godawski on 2009-07-27
> **RJ12 said:**
> Never Mind it partitioned Now i am waiting for the install *waits and is very hyper for it to install*:):):):):KS

Glad to hear, you had **not** to power off your machine. This would cause serious fun for all of us. ;)

---

### Post by RJ12 on 2009-07-27
It installed and I made sure I could boot back into Windows this is my first Dual Boot but only one more question but will post in a new topic which is my blue tooth adapter was detected in the live cd but now not in my real install *Unsubscribes to this topic* THANK YOU EVERYONE FOR YOUR help you have just proudly earned yourself a New Ubuntu User!

---

### Post by Ratscallion on 2009-07-28
Welcome to the asylum! Nah, I'm kidding!

---

### Post by blazemore on 2009-07-29
> **Ratscallion said:**
> And from within Windows too.

How?

---

### Post by Grenage on 2009-07-29
> **blazemore said:**
> How?

You 'can' do it by installing ext3 tools, reading the drive and manually changing the files...

...although it's a hell of a way to do things.

---

