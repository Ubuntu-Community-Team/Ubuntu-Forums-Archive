---
title: "Install XP Pro on a Linux machine?"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by sanubie on 2008-12-21
Okay, here is a newbie question. I'm about to start college soon. I'll be going for my associates in Computer Science. And I have a problem. I'm somewhat broke. Wachovia approved me for 3500$ but I'll only get half (1750) until half the year is over. That leaves me with 1750 to buy a notebook AND I still need money for books and living expenses. 

That means I have to be cheap as hell. This is where I need you guys advice. I like Dell computers. Never had a problem with my DT. But I need a notebook for class, and lets face it... my DT is old, and I'm surprised it is still breathing. 

Anyway... 

I need a laptop, but I need to save money-- as much as possible. So then I started thinking, *Why even bother with Vista right now?* I'll need loads of extra RAM and HDD space just to support it. Maybe I should go with a stocked Linux computer instead. [www.dell.com/linux](www.dell.com/linux) has Ubuntu machines, and they are WAY cheaper, and I wouldn't need all the extra RAM or HDD space associated with Vista. 

However, there is one problem. I'm afraid I'll hit some compatibility issues and need Windows for something. For example, what if I have to write Visual Basic code or something, then I'd need Windows to take the class. 

Hopefully they will give me a choice between Java and VB. Then no problem! I'll just choose Java and write it in Ubuntu. But what if I'm required to take VB? Sure VB is easy, but I'd have to have Windows to run it. 

How hard is it to install Windows XP on a Ubuntu only system? And what advice can you guys give me? Should I just go with a cheaper Vista computer and throw Ubuntu on it? I can't spend over a thousand. Advice, Advice... I need advice! =D>

---

### Post by jimmy the saint on 2008-12-21
Even if you buy a notebook with linux pre-installed, you would need to by xp, which may not even be possible anymore.  These days, $700 or so can get you a fine laptop for school.  I would say get a laptop with windows and then turn it into a dual boot machine only because you will likely need a copy of windows on the machine for work related to your computer science classes.  Personally, I would go with a dell or lenovo refurb, but thats just because I'm a student who is cheap like that.

---

### Post by theozzlives on 2008-12-21
it's easy, just go to: [http://www.virtualbox.org/]("http://www.virtualbox.org/")

---

### Post by tuxxy on 2008-12-21
> **sanubie said:**
> 
I need a laptop, but I need to save money-- as much as possible. So then I started thinking, *Why even bother with Vista right now?* I'll need loads of extra RAM and HDD space just to support it. Maybe I should go with a stocked Linux computer instead. [www.dell.com/linux](www.dell.com/linux) has Ubuntu machines, and they are WAY cheaper, and I wouldn't need all the extra RAM or HDD space associated with Vista. 

However, there is one problem. I'm afraid I'll hit some compatibility issues and need Windows for something. For example, what if I have to write Visual Basic code or something, then I'd need Windows to take the class. 

Hopefully they will give me a choice between Java and VB. Then no problem! I'll just choose Java and write it in Ubuntu. But what if I'm required to take VB? Sure VB is easy, but I'd have to have Windows to run it. 

How hard is it to install Windows XP on a Ubuntu only system? And what advice can you guys give me? Should I just go with a cheaper Vista computer and throw Ubuntu on it? I can't spend over a thousand. Advice, Advice... I need advice! =D>

Its very simple, download Virtualbox and create a virtual XP drive that you can boot into from Ubuntu.  You will want a reasonable amount of RAM for this so you can assign XP 512MB or over heh mine has 2GB but that much is not essential.  Theres a good guide on creating a virtual drive below;

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by tad1073 on 2008-12-21
buy the ubuntu dell notebook and xp pro.  Make sure you have an extra ubuntu disk, install xp pro, partition your hdd the install/reinstall ubuntu.

---

### Post by sanubie on 2008-12-21
Okay, I did a Google search and you can still buy XP Pro [http://cdsfu.com/index.php?categoryID=87](http://cdsfu.com/index.php?categoryID=87)

I don't know too much about Virtual Box yet. I'll have to check it out. Can anyone describe what the benefits are vs partitioning the hard drive to dual boot? Is Virtual Box easier?

---

### Post by jrusso2 on 2008-12-21
I would look for a good used on like a year old or so could probably get one pretty cheap. Just make sure everything works then install Linux on it and Virtual Box and XP.

---

### Post by theozzlives on 2008-12-21
> **sanubie said:**
> Okay, I did a Google search and you can still buy XP Pro [http://cdsfu.com/index.php?categoryID=87](http://cdsfu.com/index.php?categoryID=87)

I don't know too much about Virtual Box yet. I'll have to check it out. Can anyone describe what the benefits are vs partitioning the hard drive to dual boot? Is Virtual Box easier?

Since you're buying an Ubuntu box, Virtual Box is best. If you were buying a Windows XP machine, I'd say WUBI

---

### Post by SentientFluid on 2008-12-21
> **sanubie said:**
> Okay, I did a Google search and you can still buy XP Pro [http://cdsfu.com/index.php?categoryID=87](http://cdsfu.com/index.php?categoryID=87)

I don't know too much about Virtual Box yet. I'll have to check it out. Can anyone describe what the benefits are vs partitioning the hard drive to dual boot? Is Virtual Box easier?

The main benefit of VB (and other virtual machine software) is that you can run both Ubuntu and XP at the same time.  XP would run in a window within Ubuntu.  You can also save the state of a VM. This comes in handy if you're testing various configurations in the OS. Drawbacks are that (since OSes run concurrently) they share CPU and RAM, and virtual machines are notorious for compatibility issues with certain devices (3D graphics being a common complaint, as well as some USB devices like iPods not being recognized in the VM).  I haven't used VB in awhile so they may have improved those, I'm not sure.

Benefits of Dual-boot are that you have full compatibility as per the OS you're running, and only one OS using CPU and RAM.  Drawback is that if you need to go from Ubuntu to XP (or vice versa) then you need to restart your computer.

---

### Post by sanubie on 2008-12-21
Both options sound good. I'm just wondering about developing. And that certainly depends a lot on what I develop, of course, but it still raises the question, "What about developing Windows software in Ubuntu within a VM?" 

Wouldn't that get kind of hairy? Maybe I should do both... partition a small amount for Windows, maybe 40-50GB and leave the rest for Linux. And only switch out when necessary. 

One thing, though, I've never done it in reverse. I installed Linux Ubuntu over Windows, but I've never installed Windows over Ubuntu. I assume that by installing XP Windows it would overwrite Ubuntu, right? Then I'd have to, like the one guy said, reinstall Ubuntu and then partition the drive to leave Windows intact. Is that what you meant, tad1073? :confused:

---

### Post by abn91c on 2008-12-21
if you must, go to [http://www.geeks.com](http://www.geeks.com), you can find a windows laptop cheap for under $400. you can get MS Office at your school bookstore probably for $20.00

---

### Post by sanubie on 2008-12-21
Thanks a lot for your help, everyone!

Okay lets say I buy the Dell, Ubuntu Linux box, then I go buy an XP Pro disk, and then I'm ready to get going with Virtual Box. 

I'm looking at this tutorial -- [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox) 

And I'm wondering, I would have the XP install CD in the drive while going through this setup, right? 

Also, would that void the disk and keep me from installing it on the drive itself? I think I want to do both... if that makes sense. Maybe keep 10-15GB for the VM Windows emulator, and 30-40GB for the Windows Partition-- just in case I run into compatibility issues. 

That being the case, I think I should install XP over Ubuntu first and then reinstall Ubuntu, partition the drives and then go through VirtualBox and create the VM for XP so I can jump back and forth quickly without having to restart, etc.. What do you guys think?

---

### Post by jerome1232 on 2008-12-21
> **sanubie said:**
> 
Also, would that void the disk and keep me from installing it on the drive itself? 

I have had XP installed on this machine and in a VM (Virtual Machine) on this machine at the same time(currently VM only), I was able to get both activated. I had to call them to activate the second install and I even told the dude that gives me an installation code it was installed twice on the same machine. He said that's fine and let me activate the second install as well.

The only draw back with a VM I've seen is no 3d accelerated graphics but I only use the VM to sync up with a mp3 player that refuses to work with Ubuntu.

---

### Post by sanubie on 2008-12-21
> **abn91c said:**
> if you must, go to [http://www.geeks.com](http://www.geeks.com), you can find a windows laptop cheap for under $400. you can get MS Office at your school bookstore probably for $20.00

Okay, not a bad idea. Thanks! But if I go that route, since it has Vista, and I'm not too familiar with Vista yet. How difficult would it be to install Linux on a Vista machine?  

Can anyone think of a reason that I would need Microsoft Office? Couldn't I get by with Open Office instead? 

Dang, there are so many options. Thank God I have another couple weeks before school start to think about this.

---

### Post by sanubie on 2008-12-21
> **jerome1232 said:**
> I have had XP installed on this machine and in a VM (Virtual Machine) on this machine at the same time(currently VM only), I was able to get both activated. I had to call them to activate the second install and I even told the dude that gives me an installation code it was installed twice on the same machine. He said that's fine and let me activate the second install as well.

The only draw back with a VM I've seen is no 3d accelerated graphics but I only use the VM to sync up with a mp3 player that refuses to work with Ubuntu.

I still like the idea of buy the Ubuntu Dell. Something about buying a used machine doesn't set right with me, especially when they're about the same exact price. 

But about installing XP into the VM. Dose it just install normally into the VM itself? In other words, do I just boot into Ubuntu, open up virtualbox, and then insert the XP disk and follow the tutorial outlined at the site provided?

---

### Post by abn91c on 2008-12-21
> **sanubie said:**
> Okay, not a bad idea. Thanks! But if I go that route, since it has Vista, and I'm not too familiar with Vista yet. How difficult would it be to install Linux on a Vista machine?  

Can anyone think of a reason that I would need Microsoft Office? Couldn't I get by with Open Office instead? 

Dang, there are so many options. Thank God I have another couple weeks before school start to think about this.
most of the refurbished laptops on geeks.com have XP
Also most big colleges have licenses with software companies where you can get their programs at a fraction of the cost, for example Indiana University  $20 for MSO 2007, or free if you download it from their websites with student ID. same with windowx XP and vista.

---

### Post by jerome1232 on 2008-12-21
> **sanubie said:**
> 
But about installing XP into the VM. Dose it just install normally into the VM itself? In other words, do I just boot into Ubuntu, open up virtualbox, and then insert the XP disk and follow the tutorial outlined at the site provided?

Yes it's very straight forward, you create a virtual disk, pick a few hardware options you want for your virtual machine (ram size and etc...) then insert the xp disc, start the vm and go through the regular XP install process. It's just like another computer but it's running inside a Window.

Virtual box even has this nifty seamless mode where the programs aren't even in their separate window, feels like your running programs natively in Linux rather than in your virtual machine.

My computer is modest specs (1GB ram, 2.4ghz single core) and it handles virtual box well.

---

### Post by LordVeovis on 2008-12-21
If you are looking at the dell ubuntu box, and then going to buy the XP on top of that, I would highly recomend to buy the xp box and get linux for free.  Its easier if win is pre installed.  Also if they only offer vista boxes... then no get ubuntu.  Last I had checked there was only like a $10-$20 difference between them and windows cost more than $20 :(

---

### Post by sanubie on 2008-12-21
> **LordVeovis said:**
> If you are looking at the dell ubuntu box, and then going to buy the XP on top of that, I would highly recomend to buy the xp box and get linux for free.  Its easier if win is pre installed.  Also if they only offer vista boxes... then no get ubuntu.  Last I had checked there was only like a $10-$20 difference between them and windows cost more than $20 :(

Yea, I thought about that. But compare the processor, RAM, and storage space on those XP machines. Most have way under 100GB, most the processors are single core, in some cases RAM is under 768, and so on. I want the computer to be cheaper, but I don't want it to be worse than what I'm using right now or else what's the point?  

If I had to upgrade all those components I'd end up spending a lot more than 50$ for an XP disk. And it all seems to fall into my budget too. I'm still not too sure, but I'm leaning towards a Dell. I need a minimum of 2 to 3GB RAM, a dual core processor, 250 GB of storage, and a decent video card.

---

