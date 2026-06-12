---
title: "Dual boot with 2 hard disks"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by luqmanmubin on 2011-06-17
Hello, i'm new here and new with ubuntu. I got some questions to ask, hope you guys could help :)
I got 2 hard disks on a computer. I'm thinking to dual boot it with ubuntu 10.10 and windows 7.

Question is :
Is it okay if i put ubuntu in 1 hard disk and windows 7 in another hard disk? 
Which one should i install first? And how does it work? 

My system is intel core 2 duo 2.33ghz with 2gb of rams. 250gb and 500gb hard disks.
Thanks in advance :p

---

### Post by mcduck on 2011-06-17
Sure, you can sue as many discs as you wish. :)

Install Windows first, as it doesn't play along nicely with others and would otherwise overwrite the bootloader with it's own.

Once Windows is installed, install Ubuntu. It will add a bootloader that allows you to choose which OS you wish to use when you power up the computer.

---

### Post by jmore9 on 2011-06-17
I usually use 2 drives when i dual boot.  The first one has windows on it and the second one has linux.  I usually put the grub on the 1st diak with windows , i am using winxp pro, but with windows 7 you should search around and see if that is the correct way to go.

If i decide to just go with windows only i just format the second hard drive and log into the repair console in windows and fix the boot and fix the mbr and its just like linux had never been installed.

But this only works for winxp.  I have heard that this will not work with Vista and later versions of windoes.

---

### Post by luqmanmubin on 2011-06-17
> **mcduck said:**
> Sure, you can sue as many discs as you wish. :)

Install Windows first, as it doesn't play along nicely with others and would otherwise overwrite the bootloader with it's own.

Once Windows is installed, install Ubuntu. It will add a bootloader that allows you to choose which OS you wish to use when you power up the computer.

Thanks! I'll give it a try. Wish me luck. lol.

---

### Post by User3k on 2011-06-17
> **luqmanmubin said:**
> Hello, i'm new here and new with ubuntu. I got some questions to ask, hope you guys could help :)
I got 2 hard disks on a computer. I'm thinking to dual boot it with ubuntu 10.10 and windows 7.

Question is :
Is it okay if i put ubuntu in 1 hard disk and windows 7 in another hard disk? 
Which one should i install first? And how does it work? 

My system is intel core 2 duo 2.33ghz with 2gb of rams. 250gb and 500gb hard disks.
Thanks in advance :p

Yes you can. I have four hard drives. And not one of them has Windows..... Sorry, forgot I just deleted Windows a few days ago. Ok let me try again. I have four hard drives and up until last week I had Windows on one hard drive and Ubuntu on the other. I made sure that Grub was installed on the partition that had Ubuntu, put that hard drive first in my bios so it would boot. That way the MBR on my windows hard drive wouldn't be touched at all and grub would list Windows so it would boot it. It will work fine.

---

### Post by YesWeCan on 2011-06-17
> **luqmanmubin said:**
> Hello, i'm new here and new with ubuntu. I got some questions to ask, hope you guys could help :)
I got 2 hard disks on a computer. I'm thinking to dual boot it with ubuntu 10.10 and windows 7.

Question is :
Is it okay if i put ubuntu in 1 hard disk and windows 7 in another hard disk? 
Which one should i install first? And how does it work? 

My system is intel core 2 duo 2.33ghz with 2gb of rams. 250gb and 500gb hard disks.
Thanks in advance :p
Excellent. Installing Windows and Ubuntu on separate drives is the best thing to do. :)

It does not matter which you do first BUT only have one disk connected at a time while you are doing the installations. This will avoid a common mistake which causes people to install Grub to the Windows drive MBR. This can cause all sorts of inconveniences which having separate drives avoids.

So put in one disk. Install one OS. Disconnect that disk and connect the other. Install the other OS. Then connect both drives and tell the bios to always boot the Ubuntu drive first.
Once booted, run 'sudo update-grub' in a terminal and then reboot. Now you will see a boot menu that offers you the choice of Windows and Ubuntu.

So normally you boot from the Ubuntu drive and get a boot menu and you choose Ubuntu or Windows. If you ever need to, you can still boot Windows directly on the Windows drive.

---

### Post by luqmanmubin on 2011-06-17
> **YesWeCan said:**
> Excellent. Installing Windows and Ubuntu on separate drives is the best thing to do. :)
 
It does not matter which you do first BUT only have one disk connected at the same time while you are doing the installations. This will avoid a common mistake which causes people to install Grub to the Windows drive MBR. This can cause all sorts of inconveniences which having separate drives avoids.
 
So put in one disk. Install one OS. Disconnect that disk and connect the other. Install the other OS. Then connect both drives and tell the bios to always boot the Ubuntu drive first.
Once booted, run 'sudo update-grub' in a terminal and then reboot. Now you will see a boot menu that offers you the choice of Windows and Ubuntu.
 
So normally you boot from the Ubuntu drive and get a boot menu and you choose Ubuntu or Windows. If you ever need to, you can still boot Windows directly on the Windows drive.
 
Ouch, I just finished installing windows 7. Nevermind, I'll do it again using your way. 
I'm pretty noob at that sudo-terminal-thing but I'll give it a try :guitar:
Thanks! Cheers! :P

---

### Post by YesWeCan on 2011-06-17
That's ok. No need to reinstall Windows. Just disconnect the Windows drive while you install Ubuntu.

---

### Post by Mark Phelps on 2011-06-17
> **YesWeCan said:**
> Just disconnect the Windows drive while you install Ubuntu.

STRONGLY support this advice!!

I've been doing it this way for years -- and have successfully avoided all the problems associated with GRUB overwriting the MS Windows MBR and vice versa.

It also leaves you in the useful position of having each drive bootable on its own.  So, updates or repairs to one of the OSs has no effect at all on the other.

---

### Post by luqmanmubin on 2011-06-17
> **Mark Phelps said:**
> STRONGLY support this advice!!

I've been doing it this way for years -- and have successfully avoided all the problems associated with GRUB overwriting the MS Windows MBR and vice versa.

It also leaves you in the useful position of having each drive bootable on its own.  So, updates or repairs to one of the OSs has no effect at all on the other.

I followed exactly what YesWeCan told. It works! Thanks alot mate :)
Now it's time to give my ubuntu 10.10 some cool finishing like desktop background, dock, icons \\:D/
I'm new with ubuntu stuff, you guys got any suggestion on where to find such thing?

---

