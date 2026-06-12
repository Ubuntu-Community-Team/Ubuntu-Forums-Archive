---
title: "Dual boot menu question"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by critin on 2011-07-17
Hello.  I've searched google and this forum with key words 'dual booting linux with linux and found nothing.  Everything includes windows.  I've dual booted with windows in the past and the menu clearly shows 'Windows'--'Ubuntu'.  No mention of kernel.   I'm triple booting on two HD now and the menu shows kernel numbers with the names ubuntu and mint at the line beginning.  The thing is, there are at least 3 lines for each version and the screen will soon be full.  I won't know which version I'm getting without a more specific name.

It isn't a huge issue yet, and I could always write down what is where, but it would be simpler to have the names on the screen--is this possible?  Does the kernel info absolutely have to show?
If it's a big editing job I can't do it anyway, I'm just curious and it's on my list of 'things to learn today'.

Thanks!
critin

---

### Post by Cybie257 on 2011-07-17
Try looking at this link:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)


(STEP PULLED FROM PAGE/LINK)
The user can create a custom file in which the user can place his own menu entries. This file will not be overwritten. By default, a custom file named 40_custom is available for use in the /etc/grub.d folder. 

Be sure to read about 1/4 - 1/3 way down page as it explains how to write the Custom Menu....


I think this is something you might be after. If this works or not, please reply back so we know what happened. 

-Cybie

---

### Post by critin on 2011-07-18
Thanks a lot, Cybie.    I've been studying your link since you posted and it's just too complicated for me at this point.  I'm afraid I'll mess up and not be able to boot.  I'll keep studying though and one day I will be able to do it.   
Thanks for your help.  At least now I have a place to start.

critin

---

### Post by beew on 2011-07-18
You can just delete the old kernels and their headers from Synaptic if you don't need them any more. That way they won't be cluttering up the boot menu. But it is advisable to keep the previous kernel around so in case there are regressions in the new one you have something to fall back to.

---

### Post by critin on 2011-07-18
Thanks beew, but I think I need them all.  The kernel, the failsafe mode and the testmemory?  Since I'm triple booting I have 9/10 lines now, and plan on adding a couple more versions.  My screen will soon be full.  What would be the consequences if I did remove the safemode and test memory lines?  Could I still boot?

Thanks
critin

---

### Post by beew on 2011-07-18
> **critin said:**
> Thanks beew, but I think I need them all.  The kernel, the failsafe mode and the testmemory?  Since I'm triple booting I have 9/10 lines now, and plan on adding a couple more versions.  My screen will soon be full.  What would be the consequences if I did remove the safemode and test memory lines?  Could I still boot?

Thanks
critin

I don't mean removing those. For each kernel you have 2 lines (the kernel and recovery mode). But as times go on and you get kernel updates you will have more: two lines for each kernel version. So for example I am now on Ubuntu 10.10 and I have kernels 2.6.38 and 2.6.36 and 2.6.35.10 Each of these have 2 lines. I am saying you can remove say, 2.6.35.10 and keep only the latest (2.6.38 in my case ) and a previous version (2.6.36) I am keeping one more because I install 2.6.38 and 2.6.36 manually and 2.6.35.10 is the one that has been updated "naturally". 

If the screen get full you can simply scroll down, that is not a problem. I have an external drive with 6 Linux OSes and each has at least two kernels. :)

---

### Post by critin on 2011-07-18
[I]beew: I don't mean removing those.


[/I]Yeah, I know you didn't mean those, I was just asking.  lol  Do I really need the test memory for each one?[I]  Do  kernel updates come pretty often?  I could delete the older ones and it  would definitely help keep my mind straight at least.  I see a lot of note taking in my future.
thanks again,

critin
[/I]

---

### Post by Cybie257 on 2011-07-18
Hey, I think I found a GUI Tool for ya! :)

I haven't checked it out totally, but I see the screen shot and it's GUI based. Always a good thing in my opinion when your not wanting to kill your boot up.

Anyhow, the link is:

[http://ubuntuguide.net/manager-grub2-boot-loader-using-grub-customizergui](http://ubuntuguide.net/manager-grub2-boot-loader-using-grub-customizergui)

If you find this to work, please be sure to reply back as to your experience with it. :)

Ok, I'm updating this even though I haven't sent it. I couldn't hold off testing this baby out and making sure it still was available via the repository from the link/site.

After adding the repository and updating, I was able to install it via Synaptics (was going to through terminal, but I needed to close synaptics to install and just went with that when I went to the window)...

It looks like it's exactly what you need and something most of us can use that want to customize the Startup Menu without having to deal with all the step by step instructions. It installed and loaded up perfectly fine win Ubuntu 11.04 64bit. Haven't tested the save/usage of it as I don't need to make any changes on the computer I was testing on, plus, it's late and I am falling asleep (my excuse for any typos, lol, so I hope this all made sense...

-Cybie

---

### Post by centaurusa on 2011-07-18
> **critin said:**
> 
It isn't a huge issue yet, and I could always write down what is where, but it would be simpler to have the names on the screen--is this possible?  Does the kernel info absolutely have to show?
If it's a big editing job I can't do it anyway, I'm just curious and it's on my list of 'things to learn today'.
critin

Editing GRUB2 menus to create custom boot setups is described in a blog posting at:  [http://linuxnorth.wordpress.com/2011/03/09/grub2-revisited/](http://linuxnorth.wordpress.com/2011/03/09/grub2-revisited/)  Other postings on the blog, in category "GRUB", relate to different aspects of the same issue.  There is also a link to a very good tutorial at [http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)  These should help you edit your particular configuration.

---

### Post by critin on 2011-07-18
Hey, thanks for going to all this trouble!  I'm at the link and reading it now.
Appreciate it!
critin

---

### Post by critin on 2011-07-18
By following a link from a link I found this.  It looks like the easiest so far to do just what I want to do.  I've got to read more and make sure it's still up-to-date.
[http://ubuntu-install.blogspot.com/2009/11/grub2-title-tweaks.html](http://ubuntu-install.blogspot.com/2009/11/grub2-title-tweaks.html)

There is a section on simple change of the title--sounds interesting.

critin

---

### Post by critin on 2011-07-18
edit to add this:  [http://ubuntu-install.blogspot.com/2011/05/beautiful-burg-boot-loader-gets-ubuntu.html](http://ubuntu-install.blogspot.com/2011/05/beautiful-burg-boot-loader-gets-ubuntu.html)

Anyone know how easy Burg is?  It looks amazing.

critin

---

