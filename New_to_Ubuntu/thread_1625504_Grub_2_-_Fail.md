---
title: "Grub 2 - Fail"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by mistypotato on 2010-11-19
After uprading my Ububtu 9.04 laptop to 9.10 I can no longer boot.

It seems the Grub bootloader has been changed from grub to grub2 ?

According to the wiki Grub2 has many "wonderful (lmao)" features including failsafes to protect against failed boots.

**[COLOR="Red"]FAIL[/COLOR]**

After upgrading, I can no longer boot...This is from the wiki....

> Rescue Mode [SIZE="2"](they have a great sense of humor :-)[/SIZE]

The rescue mode is a major GRUB 2 enhancement. If GRUB 2 fails to find a useable grub.cfg and is unable to transfer control to a kernel it will drop to a grub-rescue> prompt. From this prompt the user can investigate problems, make changes, and retry the boot. 

I repeat...**[COLOR="Red"].FAIL[/COLOR]**

I never get any such prompt...it simply stalls at....

"Cannot read file"........the end  :P

So, I'll try to use the Live CD to recover from this ...updates as they happen :D

Solution for others who encounter this will be posted after I find it.

---

### Post by mistypotato on 2010-11-19
I already have an update...ta dahhhhh

If you have previous versions of Ubuntu in the boot menu....try booting to the PREVIOUS version.

I was able to do that.  (Not sure if this means grub is NOT broken or if it's using an earlier version of grub?)

So, at least in my case, thee is something wrong with the update such that Grub2 cannot find a files or files that it is looking for.

I'll come back to this later as this morning I have a lot on my plate :p

---

### Post by Rubi1200 on 2010-11-19
Hi,
sorry to hear that things did not go so great.

But, and I cannot stress this point enough, the fact that GRUB _seemed_ to fail does not necessarily indicate that the problem originated there.

Upgrades can, and do, sometimes cause odd things to happen for any number of reasons.

If you would like us to take a closer look at the situation, post the results of the boot info script linked at the bottom of my post.

Thanks.

---

### Post by coffeecat on 2010-11-19
I think you're mistaken about a few points.

> **mistypotato said:**
> After uprading my Ububtu 9.04 laptop to 9.10 I can no longer boot.

It seems the Grub bootloader has been changed from grub to grub2 ?

If you did an insitu upgrade from 9.04 to 9.10, you would have retained legacy grub. If you did a fresh install of 9.10 you would have obtained grub 2.

> **mistypotato said:**
> If you have previous versions of Ubuntu in the boot menu....try booting to the PREVIOUS version.

I was able to do that.  (Not sure if this means grub is NOT broken or if it's using an earlier version of grub?)

A "previous version" of Ubuntu is an older kernel, nothing to do with grub. I suspect that the previous version is the 9.04 kernel which still allows you to boot and that you are having problems with the 9.10 kernel. If I am right, there is no problem at all with grub and it is in fact serving you well by allowing you to boot into the older kernel.

Perhaps you might like to describe exactly what the issues are you are experiencing together with any error message you get and then someone might be able to diagnose where the problem really is and help.

---

### Post by mistypotato on 2010-11-19
> **coffeecat said:**
> I think you're mistaken about a few points.

If you did an insitu upgrade from 9.04 to 9.10, you would have retained legacy grub. If you did a fresh install of 9.10 you would have obtained grub 2.

A "previous version" of Ubuntu is an older kernel, nothing to do with grub. I suspect that the previous version is the 9.04 kernel which still allows you to boot and that you are having problems with the 9.10 kernel. If I am right, there is no problem at all with grub and it is in fact serving you well by allowing you to boot into the older kernel.

Perhaps you might like to describe exactly what the issues are you are experiencing together with any error message you get and then someone might be able to diagnose where the problem really is and help.

Sounds reasonable.

Could it be a botched 9.04 to 9.10 upgrade?
If so, how would I roll back completely the 9.10 and try again fresh?

I tried doing the upgrade again (without rolling back) and it still didnt work.

thx

---

### Post by coffeecat on 2010-11-19
> **mistypotato said:**
> Could it be a botched 9.04 to 9.10 upgrade?

I have no idea. Apart from 'can no longer boot' you haven't described what your problem is. Have you tried booting with the problem kernel, but removing 'splash quiet' from the boot options so that you can see where the boot fails? The "cannot read file" message: when do you get that? Does your system work OK with the older kernel? Have you tried reinstalling the newer kernel?

> **mistypotato said:**
>  I tried doing the upgrade again (without rolling back) and it still didnt work.

How did you do that? Do you mean you did a system update while booted up with the older kernel?

> **mistypotato said:**
> If so, how would I roll back completely the 9.10 and try again fresh?

You mean 9.10 back to 9.04? Sorry, you can't.

---

### Post by T.J. on 2010-11-19
I realise that this probably isn't what you want to hear, but if a upgrade failed from one version to another, the best thing you can do is a fresh install, reformatting the partition where Ubuntu was located. Sorry to say, Ubuntu is not perfect, but not through lack of trying! =)

I can't stress enough how important it is to backup your data before doing anything major.  

If you can't reformat the partition because it has data like your /home directory, you should be able to boot from the LiveCD using the "Try" option. Then you can copy files to another disc before you do anything.

When I setup my machines, I place /home files and the OS on separate partitions. This is so when I upgrade, I can reformat the OS partition if I must. 

 
Good Luck! =)

---

### Post by cariboo on 2010-11-19
Why do a complete reinstall, when most grub2 problems are easily solved by using the Live CD. We haven't been able to help the op, because he really hasn't stated what his problem is other than it doesn't work.

---

### Post by mistypotato on 2010-11-20
The OP states exactly what the problem was.


> 
After uprading my Ububtu 9.04 laptop to 9.10 I can no longer boot.
I never get any such prompt...it simply stalls at....
"Cannot read file"........the end 

Please explain how that could be improved. :confused:
There's only one line involved here basically.

"Cannot Read File"....the end.

):P

---

### Post by mistypotato on 2010-11-21
> **T.J. said:**
> I realise that this probably isn't what you want to hear, but if a upgrade failed from one version to another, the best thing you can do is a fresh install, reformatting the partition where Ubuntu was located. Sorry to say, Ubuntu is not perfect, but not through lack of trying! =)

I can't stress enough how important it is to backup your data before doing anything major.  

If you can't reformat the partition because it has data like your /home directory, you should be able to boot from the LiveCD using the "Try" option. Then you can copy files to another disc before you do anything.

When I setup my machines, I place /home files and the OS on separate partitions. This is so when I upgrade, I can reformat the OS partition if I must. 
 
Good Luck! =)

I backup so often I need TB drives to hold all my backups :KS:KS:KS:KS:KS
I learned the importance of backups LONG ago ...."once bitten, twice shy".

The machine will still boot perfectly fine and work just as well so long as I select the PRIOR kernel during boot.....so I would imagine it is the updated kernel causing the problem.  I'll eventually sort it out.   

Can I just delete the img files for the kernel I want to delete from the root directory and then edit the grub menu to remove that kernel?

---

### Post by Rubi1200 on 2010-11-21
Please run the boot info script linked at the bottom of my post.

The information will tell us what is where, and make offering solutions a lot easier.

Thanks.

---

### Post by mistypotato on 2010-11-21
Excellent.

Everyone kept saying there was not enough information to help....little did they know I was unaware that you could use a script to get more info.

:popcorn:

At this rate I will master Ubuntu in 2061  :KS

---

