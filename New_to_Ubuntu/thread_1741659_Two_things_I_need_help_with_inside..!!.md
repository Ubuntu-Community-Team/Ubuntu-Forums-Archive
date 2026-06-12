---
title: "Two things I need help with inside..!!"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by JDM_SOHC on 2011-04-28
Ok first thing's first.. 

I tried to run Ubuntu 10.10 before and I was having some issues, I believe they were related to my video card "nVidia Geforce 6500" there was a whole ordeal on why I should use 10.04 instead, and I did, and it works great..!! But, now Natty Narwhal has been released I want to give it a shot but I am wondering if anyone else that had the nVidia graphic's card issue is having that issue in 11.04 but not when using 10.04??

Ok next question, I want to upgrade to 11.04, but first I want to clean up my grub menu and I can't figure out how..!! I tried before and got lost in the directions because not everyones computers are the same so some rules had to be adjusted for me, and I couldn't figure it out so just gave up, and now I'm back @ it..!!

My grub menu looks like this..
[IMG]http://img705.imageshack.us/img705/6056/grub.jpg[/IMG]

And I just want it to give me 2 options, not allllll those.. Either A). Boot into Ubuntu or B). Boot into Windows..

Is this possible..?? Thanks in advance..

---

### Post by Hedgehog1 on 2011-04-28
Natty's grub menu put extra Linux Kernel choices in a sub menu, so Grub does not look so crowded (lost of other folks didn't like the menu all crowded, too).

I have found the NVidia install in Natty is very good.  I have installed Natty on 3 different NVidia GPU systems.

This may be helpful when the time comes: [**_Natty How To: Audio over HDMI for NVidia_**]("http://ubuntuforums.org/showthread.php?t=1741294")

Also - you can load Natty/11.04 and still use the 'Classic' UI: [**_Natty Info: Your UI options_**]("http://ubuntuforums.org/showthread.php?t=1741293")



***The Hedge***

:KS

---

### Post by leviathan8 on 2011-04-28
Hello.
To begin with cleaning up, please boot into your first entry "Ubuntu, with Linux 2.6.32-30-generic" and open up Synaptic. Be advised that this will only delete the old kernels on the current Ubuntu version you're booted in (to my understanding, Ubuntu 10.10?). To remove old kernels from the newly installed version, you have to boot in that one. This may seem overwhelming, but you'll get the grip in no time. 
So, once you're in Synaptic Package Manager, in the search field, type: 2.6.32 . Once searching is done, proceed with removing the following:

> linux-headers-2.6.32-29
linux-headers-2.6.32-28
linux-headers-2.6.32-29-generic
linux-headers-2.6.32-28-generic
linux-image-2.6.32-29-generic
linux-image-2.6.32-28-generic

In order to remove them, you simply right click on all of those entries listed earlier, and choose "Completely remove". Once marked, please select Apply from the upper toolbar and let the magic unleash. 
In addition, I would also install [FONT="System"]startupmanager[/FONT] and choose my default operating system at boot.
Good luck and have a nice day. If you have any uncertainties please post back. :popcorn:

---

### Post by _0R10N on 2011-04-28
> **JDM_SOHC said:**
> Ok first thing's first.. 

I tried to run Ubuntu 10.10 before and I was having some issues, I believe they were related to my video card "nVidia Geforce 6500" there was a whole ordeal on why I should use 10.04 instead, and I did, and it works great..!! But, now Natty Narwhal has been released I want to give it a shot but I am wondering if anyone else that had the nVidia graphic's card issue is having that issue in 11.04 but not when using 10.04??

Ok next question, I want to upgrade to 11.04, but first I want to clean up my grub menu and I can't figure out how..!! I tried before and got lost in the directions because not everyones computers are the same so some rules had to be adjusted for me, and I couldn't figure it out so just gave up, and now I'm back @ it..!!

My grub menu looks like this..
[IMG]http://img705.imageshack.us/img705/6056/grub.jpg[/IMG]

And I just want it to give me 2 options, not allllll those.. Either A). Boot into Ubuntu or B). Boot into Windows..

Is this possible..?? Thanks in advance..


An easy and quick way to clean up your system and updating your grub menu list at once is by executing

```
#aptitude purge 
```


for each of the entries that leviathan8 posted. This will delete de kernel versions you are not longer using and update the grub as well.

Kind regards!

---

### Post by madjr on 2011-04-28
install ubuntu-tweak in 10.04 and clean up the old kernels that you dont need

---

### Post by nebileix on 2011-04-28
Or u can check out [http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")

Its a nice program.

go package cleaner and clean up

---

### Post by JDM_SOHC on 2011-04-28
> **leviathan8 said:**
> Hello.
To begin with cleaning up, please boot into your first entry "Ubuntu, with Linux 2.6.32-30-generic" and open up Synaptic. Be advised that this will only delete the old kernels on the current Ubuntu version you're booted in (to my understanding, Ubuntu 10.10?). To remove old kernels from the newly installed version, you have to boot in that one. This may seem overwhelming, but you'll get the grip in no time. 
So, once you're in Synaptic Package Manager, in the search field, type: 2.6.32 . Once searching is done, proceed with removing the following:



In order to remove them, you simply right click on all of those entries listed earlier, and choose "Completely remove". Once marked, please select Apply from the upper toolbar and let the magic unleash. 
In addition, I would also install [FONT=System]startupmanager[/FONT] and choose my default operating system at boot.
Good luck and have a nice day. If you have any uncertainties please post back. :popcorn:

I'm actually on Ubuntu 10.04, because 10.10 kept giving me that error about my video card. Would these rules still apply, and thank you guys all for responding so quickly lol... I'm a member of dozens of forums and this one by far ranks among the top in respond time to a post =)

---

### Post by JDM_SOHC on 2011-04-28
> **nebileix said:**
> Or u can check out [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Its a nice program.

go package cleaner and clean up

Sweeeet..!! Thank you for that one, program seems to do it all pretty much.. Now I don't remove all the kernels right, only the ones I'm not using..??

---

### Post by Fedz on 2011-04-28
Consider investing in a separate hd for ubuntu it's what I have done & it's a dream :)

Ubuntu on 1st boot drive & Windows on the second boot drive then no worries :)

---

### Post by JDM_SOHC on 2011-04-28
> **Fedz said:**
> Consider investing in a separate hd for ubuntu it's what I have done & it's a dream :)

Ubuntu on 1st boot drive & Windows on the second boot drive then no worries :)

I have an external hard drive but I heard you can't boost O/S's off them..?? Did you mean internal hard drive..??

---

### Post by JDM_SOHC on 2011-04-28
I did the Ubuntu Tweak app's version of removing the kernels, they all were removed from U.T., but when I rebooted my computer into grub they are still there..??

---

### Post by Dutch70 on 2011-04-28
From a terminal, run...
```
sudo update-grub
```

If there still after you do that, then it didn't delete them.

You can also delete them from synaptic by searching for "linux-image-2" without the quotes. Be sure not to delete the wrong one.

---

### Post by JDM_SOHC on 2011-04-28
> **Dutch70 said:**
> From a terminal, run...
```
sudo update-grub
```If there still after you do that, then it didn't delete them.

You can also delete them from synaptic by searching for "linux-image-2" without the quotes. Be sure not to delete the wrong one.

Awesome that did the trick.. On all but one image/kernel.. The Very bottom one, it's Ubuntu 10.10 according to the sudo update-grub results.. I don't even use 10.10, so I wonder if it's possible to remove that one as well.. I checked U.T. and Synaptic and it's not marked as installed on either program.. Also, what is that memtest86 all about, anyone have a clue..?? Thanks again...

it says as follows..

Found linux image
Found initrd image
Found memtest86+ image
Found Windows 7 (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda3
Found Ubuntu 10.10 (10.10) on /dev/sda6

And I never even used 10.10 after I couldn't get it to work, only used it to be able to get 10.04 again and once I got 10.04 working, never went back.. Anyway to permanently remove it, or since I used it to downgrade to 10.04 I can not remove it..??

---

### Post by Dutch70 on 2011-04-28
Memtest86 is used to test your memory. It needs to run a minimum of 8 hrs. overnight is best.

Open Gparted & take a screenshot of it. Attach it to your next post with the paper clip in the toolbar.
ps, you can get a good sized pic by choosing "select area of screen to grab".

---

### Post by JDM_SOHC on 2011-04-28
> **Dutch70 said:**
> Memtest86 is used to test your memory. It needs to run a minimum of 8 hrs. overnight is best.

Open Gparted & take a screenshot of it. Attach it to your next post with the paper clip in the toolbar.
ps, you can get a good sized pic by choosing "select area of screen to grab".

I don't have gparted but i used the screenshot app... This is what I get..

---

### Post by Dutch70 on 2011-04-28
It looks like you're using 10.10. Open system monitor & click the system tab. What does it say you're using?

---

### Post by JDM_SOHC on 2011-04-28
> **Dutch70 said:**
> It looks like you're using 10.10. Open system monitor & click the system tab. What does it say you're using?

Release 10.04 (lucid)

Also, what my plan is, I want to update to 11.04 but I want to keep 10.04 just incase 11.04 doesn't work properly, than remove 10.04 and expand the space available on 11.04 if it does work right.. Right now I'm only giving Ubuntu 21gb of my 320gb hdd, and I only have 5.8gb free so I'd like to increase total to about 40-50gb if possible...

---

### Post by madjr on 2011-04-28
> **JDM_SOHC said:**
> Release 10.04 (lucid)

Also, what my plan is, I want to update to 11.04 but I want to keep 10.04 just incase 11.04 doesn't work properly, than remove 10.04 and expand the space available on 11.04 if it does work right.. Right now I'm only giving Ubuntu 21gb of my 320gb hdd, and I only have 5.8gb free so I'd like to increase total to about 40-50gb if possible...


well we need a pic of gparted to further guide you.

if its not installed, can you please look for it in the software center :)

---

### Post by JDM_SOHC on 2011-04-28
> **madjr said:**
> well we need a pic of gparted to further guide you.

if its not installed, can you please look for it in the software center :)

n/m i did have it lol just never used it... Gnome Partition Editor = GParted haha, my bad..

That looks like a bit to much for my liking lol.. Looks super cluttered..

---

### Post by Dutch70 on 2011-04-28
You've got yourself a little bit of a mess going on there.

It appears that you still have 10.10 installed on sda6, and 10.04 is installed on sda8, which you're logged in to.

If you want to try 11.04, install it to sda6. When you decide which version of Ubuntu you want to use, you'll have to get this straghtened out.

You've also got 2 swap partitions, that's just wasted space. Don't jump to do anything, I'll keep looking it over to see what I can come up with. Just wanted to get this out there and see what you thought about it.

---

### Post by JDM_SOHC on 2011-04-28
> **Dutch70 said:**
> You've got yourself a little bit of a mess going on there.

It appears that you still have 10.10 installed on sda6, and 10.04 is installed on sda8, which you're logged in to.

If you want to try 11.04, install it to sda6. When you decide which version of Ubuntu you want to use, you'll have to get this straghtened out.

You've also got 2 swap partitions, that's just wasted space. Don't jump to do anything, I'll keep looking it over to see what I can come up with. Just wanted to get this out there and see what you thought about it.

Sounds like a plan.. An yes you're exactly right, this is 2 years worth of trying **** out and never removing my footprints lol.. Excuse my language =)

Also, I'm on 32bit Win7 and it's tellin me that 64bit Ubuntu 11.04 is the recommended version..?? Does that matter..??

---

### Post by Dutch70 on 2011-04-28
My answer is, if you can use 64-bit versions, use it. 

My computer came with 32-bit Vista, but I use 64-bit Ubuntu. 

When you install 11.04, point swap to sda9 which is the swap prtn you're using on 10.04. Then you'll be able to delete your other swap prtn and grow sda6 to gain that space. (about 2GB)

On 2nd thought, if you've got more than 1GB of physical RAM, that swap prtn is too small if you want to be able to hibernate successfully.

Edit: This method isn't really going to allow you to just increase the size of 11.04 if you decide to stick with it because you can only grow a prtn to the right. You'd have to move it first, but like I said, you should do a fresh install and get your partitioning in order when you do decide which to use. You may just want to try 11.04 from a live cd/usb and get that done today.

---

### Post by JDM_SOHC on 2011-04-28
> **Dutch70 said:**
> My answer is, if you can use 64-bit versions, use it. 

My computer came with 32-bit Vista, but I use 64-bit Ubuntu. 

When you install 11.04, point swap to sda9 which is the swap prtn you're using on 10.04. Then you'll be able to delete your other swap prtn and grow sda6 to gain that space. (about 2GB)

On 2nd thought, if you've got more than 1GB of physical RAM, that swap prtn is too small if you want to be able to hibernate successfully.

Thats exactly what I have for physical RAM, 1GB..

---

### Post by JDM_SOHC on 2011-04-28
> **Dutch70 said:**
> My answer is, if you can use 64-bit versions, use it. 

Edit: This method isn't really going to allow you to just increase the size of 11.04 if you decide to stick with it because you can only grow a prtn to the right. You'd have to move it first, but like I said, you should do a fresh install and get your partitioning in order when you do decide which to use. You may just want to try 11.04 from a live cd/usb and get that done today.

Yeah i'm downloading the live cd right now, but i think everyone else in the world is too lol..!! 80kb/sec WTFFFFFFF lol..

---

### Post by Dutch70 on 2011-04-28
Haa, partitioning is so confusing...that's why I love it. :P

You've got 1005MB for swap now, if you hibernate, you may want it to be slightly larger. So you've got some decisions to make.
You can choose to use the 1.92GB swap prtn, & delete the other one, you'd just have to edit fstab in 10.04.
That is easy enough to do.

I also want to point out that you've got windows7 installed to a logical partition. If you ever get rid of XP, Vista whatever it is you have on sda1, windows7 will more than likely not boot anymore. 
Windows doesn't like being in a logical prtn, the only reason W7 is booting is because of your other windows install. Not a problem as long as you don't get rid of windows on sda1.

Edit: Yeah, I couldn't even update 11.04 a little while ago.

---

### Post by JDM_SOHC on 2011-04-28
> **Dutch70 said:**
> Haa, partitioning is so confusing...that's why I love it. :P

You've got 1005MB for swap now, if you hibernate, you may want it to be slightly larger. So you've got some decisions to make.
You can choose to use the 1.92GB swap prtn, & delete the other one, you'd just have to edit fstab in 10.04.
That is easy enough to do.

I also want to point out that you've got windows7 installed to a logical partition. If you ever get rid of XP, Vista whatever it is you have on sda1, windows7 will more than likely not boot anymore. 
Windows doesn't like being in a logical prtn, the only reason W7 is booting is because of your other windows install. Not a problem as long as you don't get rid of windows on sda1.

Yeah reason being, my computer is a Vista computer.. it's an HP Pavilion A1710N, and when I first put Windows 7 it was the RC version from microsoft's website.. Than I just used a pin to convert it to the full version, and my Vista remained on there since I never got rid of it in the first place.. Could I just install Windows 7 over Vista, an remove the other Windows 7.. I only use Ubuntu and Win 7, Vista was just kept as a backup... I'm not to bright on the logical partition side of things, infact I am not very good with partitions in general... I mean the basic allocate space thing I got down, but when it comes to editing and replacing/removing stuff I tend to ask for help a bit more.

---

### Post by Dutch70 on 2011-04-28
If you're going to do all of that, you may want to just back up all of your important files. Do a fresh install of W7 which I think it will take up the entire disk that way. So you'll have to shrink windows7 and then install your preferred version of Ubuntu. It would give you a nice set up.

Edit: Then you've got to consider the Vista recovery prtn. I'm not real good with windows installs. You may be able to just install it to the Vista prtn...like I said, I'm not sure.

---

### Post by JDM_SOHC on 2011-04-28
> **Dutch70 said:**
> If you're going to do all of that, you may want to just back up all of your important files. Do a fresh install of W7 which I think it will take up the entire disk that way. So you'll have to shrink windows7 and then install your preferred version of Ubuntu. It would give you a nice set up.

Edit: Then you've got to consider the Vista recovery prtn. I'm not real good with windows installs. You may be able to just install it to the Vista prtn...like I said, I'm not sure.

yeah I'll just do that, I hate doing restores but it does seem to make everything fresh and snappy (at least for a little while) lol...

---

### Post by anderson.fonseca on 2011-04-28
Check this link to remove old kernels and clean the grub [http://buildall.wordpress.com/2011/04/22/removing-automatically-old-kernels-in-the-ubuntu-10-10/](http://buildall.wordpress.com/2011/04/22/removing-automatically-old-kernels-in-the-ubuntu-10-10/)

Anderson Fonseca

> **JDM_SOHC said:**
> Ok first thing's first.. 

I tried to run Ubuntu 10.10 before and I was having some issues, I believe they were related to my video card "nVidia Geforce 6500" there was a whole ordeal on why I should use 10.04 instead, and I did, and it works great..!! But, now Natty Narwhal has been released I want to give it a shot but I am wondering if anyone else that had the nVidia graphic's card issue is having that issue in 11.04 but not when using 10.04??

Ok next question, I want to upgrade to 11.04, but first I want to clean up my grub menu and I can't figure out how..!! I tried before and got lost in the directions because not everyones computers are the same so some rules had to be adjusted for me, and I couldn't figure it out so just gave up, and now I'm back @ it..!!

My grub menu looks like this..
[IMG]http://img705.imageshack.us/img705/6056/grub.jpg[/IMG]

And I just want it to give me 2 options, not allllll those.. Either A). Boot into Ubuntu or B). Boot into Windows..

Is this possible..?? Thanks in advance..

---

### Post by JDM_SOHC on 2011-04-28
> **anderson.fonseca said:**
> Check this link to remove old kernels and clean the grub [http://buildall.wordpress.com/2011/04/22/removing-automatically-old-kernels-in-the-ubuntu-10-10/](http://buildall.wordpress.com/2011/04/22/removing-automatically-old-kernels-in-the-ubuntu-10-10/)

Anderson Fonseca

Got it figured out, thanks bro...

---

### Post by nebileix on 2011-04-29
> **JDM_SOHC said:**
> I did the Ubuntu Tweak app's version of removing the kernels, they all were removed from U.T., but when I rebooted my computer into grub they are still there..??

Did u do "clean config" after "clean kernels"? That should remove those entries from grub.

---

