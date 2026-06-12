---
title: "Problems with Startup Manager and Ubuntu 10.04"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by hierogrammate on 2010-05-31
> **ranch hand said:**
> SUM is not real good with the new grub.  You may want to purge it and look at this link to 
edit your /etc/default/grub file the right way.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

I searched for my topic in the forum and found this thread:

[http://ubuntuforums.org/showthread.php?p=9304416](http://ubuntuforums.org/showthread.php?p=9304416)

too late, and installed SUM in Ubuntu 10.04 (following the advice in yet another thread that didn't say anything about  potential problems with the SUM). Anyway, the thread linked above didn't address my particular problem, but it was nonetheless very informative.

In my case, the SUM works OK as far as I can tell (I wanted Windows XP to be the default selection, and it did the job). 

Here's my problem: I also, out of curiosity, used the option that allowed me to increase the resolution of the GRUB boot menu (changing it from 640x480 8bit to 1280x1024 16bit). The GRUB menu looks fine, however, after I made that change, Ubuntu's startup/shutdown text now appears distorted and unreadable (not the GUI, which is 100% fine, I mean the terminal-like  textual info that scrolls up during Ubuntu's startup and shutdown). It was crunched up at the top with multi-colored pixels (at first I thought it was a problem with the graphics gard). 

Changing back the SUM setup to 640x480 and 8bit color didn't help to restore it completely: it looks like the  size was restored, but the text is still unreadable and multi colored.

I am still a bit of an Ubuntu n00b, so I'm not certain how to uninstall (purge?) the SUM, and I am even less certain whether doing that will be enough to restore Ubuntu's boot-up/shutdown text the way it was (or if I will damage something else by doing that).

If I manage to fix that, I'll make the changes manually after reading the link suggested by Ranch Hand above... as I should have done from the start. :-P

---

### Post by wilee-nilee on 2010-05-31
It is good that your trying to learn more and customize your setup so that it works the way you want. I would suggest though as far as screen resolution on booting matters and a default boot to operating systems; you are going to have a more stable system if you don't mess with it. Startup manager works fine with Grub2 if used within its limits, which is basically setting the default to a actual OS rather then the last. Having it set to the last I suspect would require a rewrite  the grub.cfg file every time you shutdown, common sense will tell you that this might not be a good idea.

I would support ranch hands premise that learning how to modify grub in a correct manner will at the least get you where you want. Just be careful, as this is an area that has a lot of people who can help but many choose not to for various reasons, #1 for me would be making sure you don't lose what you already have.

---

### Post by hierogrammate on 2010-05-31
Thanks for your reply. I see what your mean :). I should have limited myself with what I needed and not experiment with something I didn't really need. 

Well, apart from the pixelated boot/shutdown fonts, my Ubuntu installation works fine (well apart from the headaches of trying to make my nVidia video card to work, argh,  but that's another story), so I may just bite the bullet and live with that...or go kamikaze and reinstall everything again, and use the SUM to ONLY set up the primary OS... after all, its a brand new install with nothing vital to lose, so I can take that luxury. :)

---

### Post by Somberlain on 2010-08-15
there is solution

echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u

---

### Post by JKyleOKC on 2010-08-15
> **hierogrammate said:**
> 
Here's my problem: I also, out of curiosity, used the option that allowed me to increase the resolution of the GRUB boot menu (changing it from 640x480 8bit to 1280x1024 16bit). The GRUB menu looks fine, however, after I made that change, Ubuntu's startup/shutdown text now appears distorted and unreadable (not the GUI, which is 100% fine, I mean the terminal-like  textual info that scrolls up during Ubuntu's startup and shutdown). It was crunched up at the top with multi-colored pixels (at first I thought it was a problem with the graphics gard). 

Changing back the SUM setup to 640x480 and 8bit color didn't help to restore it completely: it looks like the  size was restored, but the text is still unreadable and multi colored.This is an old thread and you may not see this reply, but here's what happened:

When you changed the resolution via SUM, the program added a VGA code to the Grub2 defaults -- but the newer kernels don't process that code correctly. Instead, they put the monitor into a state that give you the unreadable text. A bug report has been on file about this for a year or more, but last time I checked it only three people (two besides myself) had chimed in to say they were affected by it! You can go to launchpad, search for bugs in SUM, and add yourself to the roster if you want to help get it fixed eventually.

The cure is to manually edit your /etc/defaults/grub file, looking for the words "VGA=771" (the number may vary depending on what resolution you had set via SUM) and removing them. Leave everything else unchanged, save the file, then run "sudo update-grub" and when you restart next time, your text will be readable again.

---

### Post by hierogrammate on 2010-08-15
I'm still subscribed to this thread (though I forgot, heh), so I appreciate everyone's help anyway (thanks Somberlain and JKyleOKC). 

Like I said in my last post, since the install was very recent, I just reinstalled everything once again. Not a classy way of solving things, but I needed to go on with my life :)

Regardless, I'll go to Launchpad asap to add my voice there.

Have a great day. 

Ed

---

### Post by JKyleOKC on 2010-08-15
The link to the report is [https://bugs.launchpad.net/ubuntu/+source/startupmanager/+bug/495436](https://bugs.launchpad.net/ubuntu/+source/startupmanager/+bug/495436) and I think you'll need to register at launchpad to add yourself as being affected. It's fascinating to browse the bug reports and see just how complex everything is behind the scenes!

BTW, if you go to the top of the page, select "Thread Tools," and mark the thread as solved, that may help others who encounter the problem to locate it.

---

### Post by hierogrammate on 2010-08-15
> **JKyleOKC said:**
> 
BTW, if you go to the top of the page, select "Thread Tools," and mark the thread as solved, that may help others who encounter the problem to locate it.

Oops, thanks for pointing that out to me. Thread marked as solved :).

---

### Post by hierogrammate on 2010-08-15
> **JKyleOKC said:**
> The link to the report is [https://bugs.launchpad.net/ubuntu/+source/startupmanager/+bug/495436](https://bugs.launchpad.net/ubuntu/+source/startupmanager/+bug/495436) and I think you'll need to register at launchpad to add yourself as being affected.

Thanks for the link. I had no problem registering, but I had problems posting there using Firefox... probably because one of the add-ons I have installed. Ach, I'll figure out later which one it is... I simply logged in with Opera and posted my message easily. :)

---

