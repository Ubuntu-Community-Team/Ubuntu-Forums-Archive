---
title: "new distro: synching and questions"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by noob.bot76 on 2011-03-24
hey all, 

I'm really new to linux and ubuntu and have some questions about adding different distros. 

I have 10.04 as my primary installed distro on my hardrive. I'm currently "trying out" xubuntu 10.10 by booting from a usb. 

My questions are: 
1. How can I organise these distros so that I can just select which one I want at start up (right now I have to re-prioritize my boot order), and can I do that before I burn xubuntu (or anything else) to my hard drive? 

2. I'm on a netbook, but have a fair bit of hard drive space -- does burning two or more distros effect performance other than taking up hard drive space? 

3. Can I synch apps and programs on different distros? So, e.g., I've downloaded Chrome on my Ubuntu desktop, but it is not available on my Xubuntu desktop. Do I need to re-download Chrome for every distro? What about things like Skype -- how can make it so I'm the same user on skype but from a different distro?

4. Can I  access documents from different distros? I was thinking of hooking both up to Ubuntuone, and then all files I select would be automatically synched. Good idea? If so, do I just add my Xubuntu desktop name to Ubuntuone as another computer, or....? 

Many thanks

---

### Post by mcduck on 2011-03-24
You would save yourself from plenty of extra problems simply by installing the different desktops (XFCE4, in this case) on the one and the same Ubuntu install. That way you can select which desktop to use from the login screen, and don't need to worry about syncing your files between all the installed Ubuntu versions. Plus you'll of course save laods of disk space, and extra work. :)

Just install the xubuntu-desktop package on your Ubuntu install.

(Assuming you instead end doing separate install for each Ubtuunut verisons, then the answers would be these:

1. they'd appear in the Grub boot menu and you could select which one to boot from there.

2. Having multiple Linux distributions (or any other operating systems) installed won't affect performance, as only one OS is running at a time.

3. No, you can't. You'd have to install every program separately for each installed versions. And same goes for all updates as well.

4. Ubuntu one would work, and s would either sharing the home partition, or a separate data partition, between different installs.

But like I said, everything would be a lot simpler by just adding the different desktop environments to your Ubuntu install. Ubuntu, Xubuntu, Kubuntu, and Lubuntu aren't different distributions. The distro is Ubuntu, and the different variants just give you different desktop and programs from the install. All the same programs, desktops etc. can be installed on top of any variant, as in the end they all are just one and the same Ubuntu. And same goes for the netbook version and server version as well. Just different starting points to the same Ubuntu system.)

---

### Post by noob.bot76 on 2011-03-24
hey thanks mcduck, 

just to double check, i have a package "xubuntu-desktop 2.112" listed in my Synaptic Manager. I can just install that and then choose which desktop environment I want to use whenever I boot?

so i'm still getting these distinctions down, so my apologies if this is confusing. i knew xubuntu and ubuntu (etc...) where on the same OS, but i thought "distro" referred to the entire package -- the OS with desktop environmet, etc. My mistake. So, if i want to try out actually different distros -- like Fedora, Mint, or openSUSE -- I would have to follow the steps you listed.

1. How do I access my Grub menu, or do I have to install?
2. Does installing things like Chrome and Skype separately clutter up the HD and waste space? 
3. I'll look into sharing home partitions (not something I know about yet!); but in the mean time, do I just list my different desktop (e.g., a Mint distro) as a different computer on Ubuntuone? 

thanks

---

### Post by mcduck on 2011-03-25
Yes and no. Installing that package will add everything that you'd get by installing Xubuntu, but since it's installed in the one and the same Ubuntu setup you don't select which desktop to use at the boot menu, but at the *login screen*. Just click the "Session"-button near the bottom of the screen after selecting your user to choose between available desktop sessions.

1. What comes to installing other Linux distributions, they would be selected at Grub menu, and you can access the menu by holding down Shift key while starting the machine. Although the menu should appear automatically if you have more than one OS installed.

2. Well, yes it does. But when you install multiple operating systems, there's really no other option. (This of course has nothing to do with having multiple desktop environments installed on one Ubuntu system)

3. If you install different Linux distributions (like Mint) you shouldn't share your home partition between them. That would mess things up, as all your user's configuration files are in your home. If you install different Linux distributions I recommend using a shared storage partition instead of sharing the actual home.

---

### Post by noob.bot76 on 2011-03-25
Thanks for the detailed and helpful replies! I'm on Xubuntu right now and loving it. Everything seems faster, even web browsing. :confused:

Wasn't sure what happened at first, because at boot-up, it said "xubuntu" and I didn't know if I could get back to Ubuntu! But I found the login options. :rolleyes:

thanks again

---

### Post by Dutch70 on 2011-03-25
Just to help you understand what mcduck is talking about by using a shared storage partition. I've included a pic of my 2nd hdd. 

You'll notice that sda8 is formatted to ntfs, that's so I can access it from windows also, which is on my other hdd. If you're not using windows at all, you can just format it to ext4. 

The 2nd pic is of my files in my Data partition & how I access them. 
There is no separate /home for these particular systems.

---

### Post by noob.bot76 on 2011-03-25
Aha.....that actually clarifies a lot, thanks Dutch! So by partitioning storage one creates multiple "File Systems" each of which has their own Home folder, but they are all accessible from whatever distro/desktop environment one using.

That's very cool -- I'll have to try that out when my desktop arrives. 

Cheers

---

### Post by Dutch70 on 2011-03-25
Sounds like you've got it. 

The only downside AFAIK is upgrading when a new flavor comes out. I hear that you can just copy your .config folder to your Data partition and put it back when you get your new system installed, but I haven't tried it yet.

---

### Post by mcduck on 2011-03-25
> **Dutch70 said:**
> Sounds like you've got it. 

The only downside AFAIK is upgrading when a new flavor comes out. I hear that you can just copy your .config folder to your Data partition and put it back when you get your new system installed, but I haven't tried it yet.

That's pretty much what I usually do if I make a fresh install of the new Ubuntu version instead of upgrading.

I copy everything from my home directory into the storage partition, install the new Ubuntu version and then copy all my personal files and all the relevant setting files back from the storage partition.

It's fairly quick and easy to do, especially since my Music collection and all the other large files are already on the storage partition (I create links from all the directories from the storage into my home directory). And as I only copy back what I actually need I get a nice change to clean all the unnecessary stuff from my home directory. :)

---

### Post by Dutch70 on 2011-03-25
> **mcduck said:**
> 
It's fairly quick and easy to do, especially since my Music collection and all the other large files are already on the storage partition **(I create links from all the directories from the storage into my home directory)**. And as I only copy back what I actually need I get a nice change to clean all the unnecessary stuff from my home directory. :)

Nice!!! That's the part I don't quite understand yet. I've tried symlinking, I think it was...LOL. I never could get it to work correctly.
If you know of a good tutorial or something, I'd love to have it.

---

### Post by mcduck on 2011-03-25
I don't think I know any tutorial for it, but here's how I do it.

I have a Ext4 partition which I use for my storage. it's mounted into /mnt/storage and contains a bunch of directories (Music, Videos, Projects etc.)

Then to link them into my home I just open a terminal and run commands like this:
```

ln -s /mnt/storage/Music /home/mcduck/Music
ln -s /mnt/storage/Videos /home/mcduck/Videos
ln -s /mnt/storage/Projects /home/mcduck/Projects
```

Simple as that, really.

Or actually it *can* be even simpler, if you prefer doing this from a graphical file manager instead of terminal you can just drag a directory from the storage partition into your home using middle mouse button, and you'll get a popup menu that asks if you want to copy, move or create a link. Select link and you'll get a symbolic link. ;)

---

### Post by Dutch70 on 2011-03-27
Thanks a lot mcduck. That was really simple, I now have my folders linked & my data partition auto mounting. 
No idea why I couldn't find that before. :D

Cheers

---

