---
title: "OS list question"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by olabaz on 2008-12-16
I installed ubuntu a while ago and I've always had this issue that when I turn on my computer I see the list of OS to boot.  There are several Ubuntu ones and I don't know why.  I only installed one.  I think they're kernels or something I'm not sure.  How do I get rid of the ones I'm not using?

---

### Post by drs305 on 2008-12-16
I recommend StartUp-Manager. It's a gui-based app that will let you make a variety of changes to grub's menu list without having to manually edit it. You can control how many kernels you see (your concern), how long the menu displays, the default kernel to run, and lots more.

[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

StartUp-Manager only effects what you see, it doesn't actually remove the kernels from your system. That is discussed in the tutorial as well.

By default, each time a new kernel is installed during an upgrade it is added to the grub menu. That is why you are seeing additional choices during boot. This behavior is configurable in grub and SUM can easily make the changes for you.

---

### Post by Paqman on 2008-12-16
> **olabaz said:**
> How do I get rid of the ones I'm not using?

There's a few different ways:
[LIST=1]
[*]Uninstall the old kernels. Search in Synaptic for "linux-image". Make sure you don't uninstall the one your normally use!
[*]Install startupmanager and tell it to restrict the number of kernels shown.
[*]Edit /boot/grub/menu.lst manually. Comment out or delete lines referring to unwanted kernels.
[/LIST]

---

### Post by jerome1232 on 2008-12-16
Yes startup manager is great for that but keep in mind it is good to keep at least 2 good known working kernels in that list (yes you were right they are kernels) 

Basicaly the Linux Kernel is the core of the system, it's good to have older ones in the list in case a newer one causes your system to lock up or become otherwise unusable, this way you can just boot to an older kernel then use startup manager to make that older kernel the default.

---

### Post by olabaz on 2008-12-16
K thanks everyone.  And which one should I use, the latest one?  And what's the difference between the kernels?

---

### Post by yellowaeroplane on 2008-12-16
Yes, always use the latest one unless you're experiencing major hardware issues... it's safer that way.

If you're comfortable editing plain text and would like to keep the old kernels but not have to see them in your boot menu do this:

```
sudo gedit /boot/grub/menu.lst
```

Scroll to the bottom and you'll see the list of kernels... be careful, but you can add "#" in front of the lines pertaining to the old kernels, thus commenting them out. If you need to use an old kernel for some reason, just remove your "#" comment markers.

---

### Post by OutOfReach on 2008-12-16
> **olabaz said:**
> And what's the difference between the kernels?

New features, bug fixes, and yes sometimes even new bugs.
But it is recommended to use the latest kernel.

---

### Post by Paqman on 2008-12-17
> **yellowaeroplane said:**
> 
```
sudo gedit /boot/grub/menu.lst
```


Please [don't use sudo for graphical apps]("http://www.psychocats.net/ubuntu/graphicalsudo") like gedit.

Instead use gksu for Ubuntu & Xubuntu, kdesu for Kubuntu.

---

### Post by olabaz on 2008-12-17
K thanks again.  And I just finished updating to ubuntu 8.10 and when I open FF it takes up the whole screen.  There is no title bar or the userbar thing.

---

### Post by xjcannonx on 2008-12-17
F11 but if the problem persists either read one of the many posts on this topic or post a new one

---

### Post by olabaz on 2008-12-17
Wow, you guys are good thanks again for that one and my last question before I mark the thread solved.  When I was done upgrading it said do I want to delete the files and put No because I didn't have time.  Now I want to delete them.  What do I do?

---

### Post by olabaz on 2008-12-20
Bump!

---

### Post by drs305 on 2008-12-20
olabaz,

I read your request but didn't respond because I wasn't sure what upgrade you were talking about (the kernel upgrade or perhaps from Hardy to Intrepid) and which *old files* you were referring to. I can think of two things. 

First is the old kernel. I don't believe it asks if you want to keep the old kernel, but it might have. That has been mentioned in earlier posts. I think more people keep at least one older kernel than don't, but it's personal choice. To remove older kernels, review Paqman's item #1.

Second, it may have asked if you wanted to keep your old grub settings and continue to boot with the old kernel. If you elected to keep booting the old kernel, you would just change the setting by manually editing menu.lst or using StartUp-Manager to change the default kernel or OS.

If these don't cover what you mean just explain further which process generated the files and we can probably help you out.

---

### Post by olabaz on 2008-12-20
Oh, I upgraded from 8.04 to 8.10 I think and near the end it asked do you want to keep the upgrade files that you downloaded.

---

