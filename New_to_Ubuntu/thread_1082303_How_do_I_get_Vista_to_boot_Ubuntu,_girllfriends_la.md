---
title: "How do I get Vista to boot Ubuntu, girllfriends lappy"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by philinux on 2009-02-27
Installed ubuntu to free space 
sda5=/
sdz6=swap
sda7=/home

Clicked advanced and got the installer to load grub to /dev/sda5

How do I get vista to boot ubuntu.

Googling only got me grub booting vista.

---

### Post by Xiong Chiamiov on 2009-02-27
You can't make the Vista bootloader boot into Ubuntu, afaik.  The way to go is to install Grub to the MBR, then chainload into Vista.

---

### Post by easybake on 2009-02-27
If you are still using the windows boot loader and you don't see a grub menu screen. (if your bootup looks the same as it did before you installed ubuntu)
You are probably going to need use a program like [EasyBCD]("http://neosmart.net/dl.php?id=1") to edit the windows bootloader and add ubuntu to it.

---

### Post by kestrel1 on 2009-02-27
Not sure that Vista could handle that. 
you are normally better off letting Grub boot Windows. You could always look at a third party boot manager that could do both. Not tried it personally, but you could have a look at this one: [http://gag.sourceforge.net/](http://gag.sourceforge.net/)

---

### Post by philinux on 2009-02-27
> **easybake said:**
> If you are still using the windows boot loader and you don't see a grub menu screen. (if your bootup looks the same as it did before you installed ubuntu)
You are probably going to need use a program like [EasyBCD]("http://neosmart.net/dl.php?id=1") to edit the windows bootloader and add ubuntu to it.

Yes I need to edit the windows bootloader. I dont want grub on the mbr. It's not my pc. Are there any other hacks besides easybcd

---

### Post by kestrel1 on 2009-02-27
Good call easybake, looks like easyBCD should do the job.

---

### Post by philinux on 2009-02-27
Just downloaded easybcd and read through the ubuntu specific bit. Could not be simpler. Here we go....

---

### Post by Xiong Chiamiov on 2009-02-27
Is there any particular reason why you're ok with installing another OS, but not installing a different bootloader?

---

### Post by philinux on 2009-02-27
> **Xiong Chiamiov said:**
> Is there any particular reason why you're ok with installing another OS, but not installing a different bootloader?


All sorted with easybcd. On ubuntu now. 

In answer to your question it's **not my laptop** and I dont want grub. You know kernels in the menu etc. The two options now are windows or ubuntu. Simple.

---

### Post by stchman on 2009-02-27
> **philinux said:**
> Installed ubuntu to free space 
sda5=/
sdz6=swap
sda7=/home

Clicked advanced and got the installer to load grub to /dev/sda5

How do I get vista to boot ubuntu.

Googling only got me grub booting vista.

If you installed Ubuntu on a system that has Vista currently installed GRUB will make an entry with a Windows Vista.  Simply arrow down and hit enter.  You will boot Vista.

---

### Post by philinux on 2009-02-27
I used the advanced option and installed grub to the partition /dev/sda5 and not to the mbr.

Easybcd is that easy to use/edit the windows bootloader.

---

### Post by stchman on 2009-02-27
> **philinux said:**
> All sorted with easybcd. On ubuntu now. 

In answer to your question it's **not my laptop** and I dont want grub. You know kernels in the menu etc. The two options now are windows or ubuntu. Simple.

So the bootloader that easybcd installs is OK but not GRUB?  Makes no sense, but OK.....

You added another level to the install.  You can install StarUpManager and remove the recovery entries.  You can also make GRUB have a 1 sec time limit so the GRUB screen appears only briefly.

---

### Post by philinux on 2009-02-27
> **stchman said:**
> So the bootloader that easybcd installs is OK but not GRUB?  Makes no sense, but OK.....

You added another level to the install.  You can install StarUpManager and remove the recovery entries.  You can also make GRUB have a 1 sec time limit so the GRUB screen appears only briefly.

I don't think you read all my posts in this thread. It's also not my laptop.

Easy bcd is a windows bootload editor. It's also free with specific ubuntu documentation.
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by stchman on 2009-02-27
> **philinux said:**
> I don't think you read all my posts in this thread. It's also not my laptop.

Easy bcd is a windows bootload editor. It's also free with specific ubuntu documentation.
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

She is perfectly OK with you installing a completely different OS but not the boot loader?

---

### Post by philinux on 2009-02-27
> **stchman said:**
> She is perfectly OK with you installing a completely different OS but not the boot loader?

Look I'm not being funny but this is how I wanted it set up, grub is on the partition not the mbr. End of story. I do not wish to parp about with supergrub should we wish to remove ubuntu from this machine. My machine at home is purely ubuntu. This is my weekend play machine. We have 5 users for vista, her kids.

I must admit I did not think it would be that easy to use easybcd.

---

### Post by kestrel1 on 2009-02-27
I think what you have done is great, you must keep the ladies happy :-)
Easybake gave a real good link with eastBCD & it sounds like it did the trick for you.
As you say, it is not your machine.

---

### Post by blueridgedog on 2009-02-27
> **stchman said:**
> She is perfectly OK with you installing a completely different OS but not the boot loader?

Though I do not understand the logic as well, we (Easybake) came up with the answer for the problem at hand.  You could also consider the OP's request as "I want to dual boot without using grub...", so perhaps others will find the thread and maybe easyBCD will meet their needs.

---

### Post by philinux on 2009-02-28
Hi guys, 

Thanks for the help and "advice". Girlfriend and her kids very happy. They will be trying ubuntu I've no doubt.

Installing grub to the ubuntu **partition** and then using easybcd to modify the vista bootloader is a very neat solution to dual booting. The grub menu appears when ubuntu is selected and it gets updated just the same as if it were on the mbr.

---

### Post by Xiong Chiamiov on 2009-03-01
> **philinux said:**
> All sorted with easybcd. On ubuntu now. 

In answer to your question it's **not my laptop** and I dont want grub. You know kernels in the menu etc. The two options now are windows or ubuntu. Simple.
You can easily not have extra kernels in the list, have windows as the default, load it automatically after 1 second, and even hide grub altogether.  Do the last one and they won't even know you changed bootloaders on them.

Glad you got it working, though.  I just don't like misinformation.

---

### Post by stchman on 2009-03-02
> **Xiong Chiamiov said:**
> You can easily not have extra kernels in the list, have windows as the default, load it automatically after 1 second, and even hide grub altogether.  Do the last one and they won't even know you changed bootloaders on them.

Glad you got it working, though.  I just don't like misinformation.

I agree, I mentioned the same thing.

---

