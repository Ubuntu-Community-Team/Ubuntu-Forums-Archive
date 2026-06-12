---
title: "which should I install first?"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by lil_kid1333 on 2009-03-24
Well im going to restart my Ubuntu but I wanted to install windows also for adobe photoshop

I was wondering which should I install first? windows or ubuntu? i'm only going to use like 30 gigs on windows :P just in case I want other stuff or games....

---

### Post by lisati on 2009-03-24
It's often easier to install Windows first, then Ubuntu. This is because Ubuntu's installer is friendlier to other OSes on the system than Windows.

---

### Post by kansasnoob on 2009-03-24
It's much easier to install Windows first!

Then look here:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

for Vista, or here:

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

for XP!

---

### Post by lil_kid1333 on 2009-03-24
how can I partition the hard drive? cause I lost my cd to make partitions i forgot the name of the prgram

---

### Post by SikEnCide on 2009-03-24
the Ubuntu Live cd has Gparted on it. Also the ubuntu installer can pretty much do it for you.

---

### Post by mhgsys on 2009-03-24
Yeah, 

It's easier to install windows first, 
Then Ubuntu 

In the install of ubuntu you could even shrink your windows partition and make it a dual boot.

I guess thats the easiest way there is.

You could also make a partition with the windows partitioner and format it later as ext3.

It's pretty easy to do, and you'll get there.

---

### Post by lil_kid1333 on 2009-03-25
thanks guys but umm I did something bad... :P

Well I installed Ubuntu 1st, I didn't have patience and was dying to install it lol

So can I use Gparted to make a partition for my Windows, install Windows, and then what's the next part to get the boot thing working?

Sorry just really wanted Ubuntu its addicting like a drug ;)

---

### Post by balloooza on 2009-03-25
Hi, GOOD FOR YOU FOR INSTALLING UBUNTU!, welcome to the comunity, and your first problem :(, but that is what this forum is for.

There is a problem now, the bootloader (grub, as in grub loading stage 1.5, press esc in 2,1 loading... etc.)
the bootloader grub will be overriten by the one on windows, so the best idea is to install windows, then instasll ubuntu again :(

BUT, if you do not have that capibility (have to borrow a xp disk) then you can tell me that and I will tell you how to install windows, with your existing ubuntu, but the other way is MUCH faster (and much more dissappointing)

---

### Post by JohnLM_the_Ghost on 2009-03-25
> **lil_kid1333 said:**
> thanks guys but umm I did something bad... :P

Well I installed Ubuntu 1st, I didn't have patience and was dying to install it lol

So can I use Gparted to make a partition for my Windows, install Windows, and then what's the next part to get the boot thing working?


the usual stuff

1. Install Windows

2. Boot up LiveCD

3. then in terminal
```
grub
find /boot/grub/stage1
root hd(*whatever find returned*)
setup hd(0)
quit
```

4. Reboot

5. Put a new entry in /boot/grub/menu.lst if needed

look [here]("http://ubuntuforums.org/showthread.php?t=224351") for more info about grub commands

---

### Post by balloooza on 2009-03-25
> the usual stuff

1. Boot up LiveCD

2. then in terminal
Code:

grub
find /boot/grub/stage1
root hd(whatever find returned)
setup hd(0)
quit

3. Reboot

look here for more info 
I am sory, but what are you responding to? (quote the post)

---

### Post by lil_kid1333 on 2009-03-25
> **balloooza said:**
> Hi, GOOD FOR YOU FOR INSTALLING UBUNTU!, welcome to the comunity, and your first problem :(, but that is what this forum is for.

There is a problem now, the bootloader (grub, as in grub loading stage 1.5, press esc in 2,1 loading... etc.)
the bootloader grub will be overriten by the one on windows, so the best idea is to install windows, then instasll ubuntu again :(

BUT, if you do not have that capibility (have to borrow a xp disk) then you can tell me that and I will tell you how to install windows, with your existing ubuntu, but the other way is MUCH faster (and much more dissappointing)

lol thanks but I had Ubuntu already just did a fresh install cause something went wrong with my audio for some reason :S thanks though :) ^^

Yeah I got the Windows xp cd ain't mine but it works :)

So do I install windows normally and it'll take over the grub thing right? that's where I get stuck how do I make it so I can choose which OS to choose...

---

### Post by sailthesea on 2009-03-25
If you can gut your own and your friends computers and get them working again (like you did last week;-)) You'll easily handle this! Just be patient and wait for a bit of help
  btw Did your friends computer ever recover?

---

### Post by theozzlives on 2009-03-25
> **balloooza said:**
> Hi, GOOD FOR YOU FOR INSTALLING UBUNTU!, welcome to the comunity, and your first problem :(, but that is what this forum is for.

There is a problem now, the bootloader (grub, as in grub loading stage 1.5, press esc in 2,1 loading... etc.)
the bootloader grub will be overriten by the one on windows, so the best idea is to install windows, then instasll ubuntu again :(

BUT, if you do not have that capibility (have to borrow a xp disk) then you can tell me that and I will tell you how to install windows, with your existing ubuntu, but the other way is MUCH faster (and much more dissappointing)

BORROW an XP CD??? That's a serious violation of Windows EULA and illegal!

---

### Post by JohnLM_the_Ghost on 2009-03-25
> **lil_kid1333 said:**
> So do I install windows normally and it'll take over the grub thing right? that's where I get stuck how do I make it so I can choose which OS to choose...

Well alternative to my previous suggestion, and what **balloooza** suggested is to install Windows and then Ubuntu once again.

Goes as this

1. Boot LiveCD

2. Delete all partitions with gparted (assuming there's only Ubuntu partitions and no other stuff)

3. Create New NTFS partition for Windows (of size you wish)

4. Boot Windows Disk and Install as usual into that NTFS partition

5. Boot LiveCD again and Install Ubuntu (make sure to use unallocated space)

should be pretty straight-forward....

---

### Post by balloooza on 2009-03-25
Is it me, or is this getting off topic,
lil_kid1333, just to make it clear you have two choices..
Install Windows(ITS A TRAP,DON'T DO IT)wipe the harddrive and make windows happy. Then install Ubuntu (give it a generous partition:))
--or--
Go through a painfull process of making a partition for yourwindows before the one for ubuntu, formating it with ntfs, then installing windows, then booting a live disk (the ubuntu live cd works great) and installing grub, after, of course, manuly compiling a grub configuration, with the proper formating to load the windows kernal, and the ubuntu one.

I just think that you should do the "easy" option, but if you want to learn somthing new, then go for the second option.

---

### Post by lil_kid1333 on 2009-03-25
> **sailthesea said:**
> If you can gut your own and your friends computers and get them working again (like you did last week;-)) You'll easily handle this! Just be patient and wait for a bit of help
  btw Did your friends computer ever recover?

Nah its a dead computer no way to recover from it :( he'll just have to install the hard drive somewhere else and get the files from their and hope it doesnt infect the pc :S

and yes I want to learn something new. option 1 sounds to easy I want to learn something complicated and feel proud ^^

btw I know it's off topic but which ones were the codecs to install for sound and movies?? FF something :s or Gstreamer wasn't it??

---

### Post by balloooza on 2009-03-25
first, the codecs, ff is for ffluendo... or somthing, gstreamer works great in gnome, so you want to install the gstreamer plugins.

next, it is getting late for me, so if you subscribe to this thread, then I will talk again later, and email myself a reminder to respond.
But... if you want to try an alternitive, if Windows is just for a few programs, and not for gaming, then you can install windows on virtualbox
intrepid
[http://download.virtualbox.org/virtualbox/2.1.4/virtualbox-2.1_2.1.4-42893_Ubuntu_intrepid_i386.deb](http://download.virtualbox.org/virtualbox/2.1.4/virtualbox-2.1_2.1.4-42893_Ubuntu_intrepid_i386.deb)
hardy
[http://download.virtualbox.org/virtualbox/2.1.4/virtualbox-2.1_2.1.4-42893_Ubuntu_hardy_i386.deb](http://download.virtualbox.org/virtualbox/2.1.4/virtualbox-2.1_2.1.4-42893_Ubuntu_hardy_i386.deb)
then install windows, and run ubuntu and windows side by side and you can use the applications together, in seemless mode, 
[http://www.virtualbox.org/attachment/wiki/Screenshots/VirtualBox_OSX_beta_3.png](http://www.virtualbox.org/attachment/wiki/Screenshots/VirtualBox_OSX_beta_3.png)
that is osx, but it is the same idea.
for full effect, remove the bottom panel on the desktop, and have windows taskbar at the bottom, and linux at the top.
Try virtualbox first, it sould work well.

---

### Post by lil_kid1333 on 2009-03-25
> **balloooza said:**
> first, the codecs, ff is for ffluendo... or somthing, gstreamer works great in gnome, so you want to install the gstreamer plugins.

next, it is getting late for me, so if you subscribe to this thread, then I will talk again later, and email myself a reminder to respond.
But... if you want to try an alternitive, if Windows is just for a few programs, and not for gaming, then you can install windows on virtualbox
intrepid
[http://download.virtualbox.org/virtualbox/2.1.4/virtualbox-2.1_2.1.4-42893_Ubuntu_intrepid_i386.deb](http://download.virtualbox.org/virtualbox/2.1.4/virtualbox-2.1_2.1.4-42893_Ubuntu_intrepid_i386.deb)
hardy
[http://download.virtualbox.org/virtualbox/2.1.4/virtualbox-2.1_2.1.4-42893_Ubuntu_hardy_i386.deb](http://download.virtualbox.org/virtualbox/2.1.4/virtualbox-2.1_2.1.4-42893_Ubuntu_hardy_i386.deb)
then install windows, and run ubuntu and windows side by side and you can use the applications together, in seemless mode, 
[http://www.virtualbox.org/attachment/wiki/Screenshots/VirtualBox_OSX_beta_3.png](http://www.virtualbox.org/attachment/wiki/Screenshots/VirtualBox_OSX_beta_3.png)
that is osx, but it is the same idea.
for full effect, remove the bottom panel on the desktop, and have windows taskbar at the bottom, and linux at the top.
Try virtualbox first, it sould work well.

yeah ill subscribe and nah I already tried virtual box I dont got enough RAM for it lol but not just that I want it for my printer which doesn't work with linux and for adobe photoshop and iTunes and maybe games if I have time i'm just going to install like 30 gigs on it :P

---

