---
title: "How do I dual Boot?"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by plentymoon on 2010-01-07
How do you dual boot from ubuntu do I need to download something on to Ubuntu and Windows to get them to work side by side?

sorry I should of figured this out by now. but yeah if ya can help me please post.
:popcorn:

---

### Post by Twitch6000 on 2010-01-07
Start windows,pop in the ubuntu disc and click the install button.

---

### Post by plentymoon on 2010-01-07
Alright I will see if this works.:popcorn:

---

### Post by Chilli Bob on 2010-01-07
> **Twitch6000 said:**
> Start windows,pop in the ubuntu disc and click the install button.


Won't that be installing Wubi, not dual-booting?

For dual booting see this.....

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

Check the related links for other combinations of windows and ubuntu.

---

### Post by plentymoon on 2010-01-07
Yeah that didn't work if their is another way please tell me some one. I want to dual boot so I can still do work and have fun. Playing my windows games without having to really leave either one of the OS's doing nothing.

---

### Post by ssulaco on 2010-01-07
[try this]("http://lmgtfy.com/?q=how+to+dual+boot+linux+and+windows")

---

### Post by stoogiebuncho on 2010-01-08
> **plentymoon said:**
> Yeah that didn't work if their is another way please tell me some one. I want to dual boot so I can still do work and have fun. Playing my windows games without having to really leave either one of the OS's doing nothing.

Are you talking about running a virtual machine?  Do you want to be able to run Windows from inside of Ubuntu, or vice versa?

---

### Post by zine92 on 2010-01-08
If dual booting always remember to install windows first then the rest of the oses you need because of windblow's not very good [compared to grub] bootloader. This will prevent grub being removed when windows bootloader is being installed. And what specific problem do you faced. Care to explain because i am dual booting am is fine. And another word od advice is to backup before attempting anything. Then if you don't mind a clean install, use gparted (i did that to remove all partitions and repartition) but if you do that, you need not specify the space for ubuntu, i.e. you got a 320 gb just specify it as ntfs/fat whichever you use. Then after windows install then pop in the ubuntu install and specify the space needed by ubuntu. Anything more i am willing to help but some may be too troublesome. But hope it helps.

---

### Post by baha'a on 2010-01-08
Hi

[zine92]("http://ubuntuforums.org/member.php?u=736942") said some good stuff

I once had both windows and ubuntu 9.04 on my computer

just you need to install windows first and when you do this leave space for ubuntu as a separated partition like make C for windows and make D but leave it empty

then boot from the ubuntu live CD and hit the install

when the partitioner opens chose the D partition and format it so the file system in it becomes ext3

and go on
that's it.

PS: after I had the two systems I formated windows and reinstalled it so ubuntu disappeared so I formatted again the whole disk and installed windows first(and made the hard three paces one for ubuntu) then I tried to install ubuntu 9.10 and it saw the hard as one pace so I let it to format and installed it alone on the hard and it keeps telling me the I have too many bad sectors consedering that windows didn't tell me that
so I'm know enjoying a windows free computer.
good luck

---

### Post by Twitch6000 on 2010-01-09
> **Chilli Bob said:**
> Won't that be installing Wubi, not dual-booting?

For dual booting see this.....

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

Check the related links for other combinations of windows and ubuntu.

Well I still find it dual booting just in the easiest manner.

---

### Post by michy99 on 2010-01-09
What we have here is a failure to communicate.

A careful reading of the OP will reveal that he wants to run Windows and Ubuntu at the same time. That is not the same thing as dual booting. The only way to do that is to run Ubuntu on a virtual machine in Windows, or run Windows on a virtual machine in Ubuntu.

Dual booting means that you can boot to either system, but not both at the same time.

---

### Post by Perturbed Penguin on 2010-01-09
As the previous poster said, if you want to run them side by side then you will need to run one or the other in a virtual machine. One way to do this is to install Ubuntu and then install the 'VirtualBox' software from the software center onto Ubuntu. Using this software you can create a virtual Windows installation that you can run on top of Ubuntu. Keep in mind this will not be a perfect, normal sort of installation of Windows - running any OS through virtualization software has its drawbacks.

... otherwise if you do in fact want to just dualboot, so that on startup you can select which OS to boot into, all you have to do is install Windows first and then make sure you don't overwrite the Windows partition when you install Ubuntu. If after the Ubuntu installation Windows does not show up on the GRUB boot list use this command in the terminal:

sudo update-grub

---

### Post by Yappy on 2010-01-13
..

While in ubuntu/windows must I reboot to get into Ubuntu/Window or is that a better way to do it?

Thank you

---

### Post by lisati on 2010-01-13
> **Yappy said:**
> ..

While in ubuntu/windows must I reboot to get into Ubuntu/Window or is that a better way to do it?

Thank you

If you're not using something like a virtual machine, the short answer is: yes! 
Slightly longer answer: there's usually only one OS running your computer at a time.

---

