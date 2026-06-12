---
title: "So I Just Started... [i.e; Help]"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by Von-Dyke on 2009-03-04
Literally. About 4 hours ago i threw in the 8.10 cd, partitioned and went ahead with my forte into Linux (loving it so far). Following this i allowed the OS to download updates (I imagine they were necessary? I have no idea what they all meant/were) and now i am at your doorstep, oh thou of UbuntuForums.
So i have a couple of questions, one that bugs me the most. 

When i boot my pc i see about 5/6 Ubuntu Choices (Kernel 11 * 2, Kernal 7 * 2, another choice [i think, one was a safe mode equivelant]) and then my old XP OS, how do i make it so that there is only one Ubuntu option, or only 2 (The one i use + its safe mode)?

How do i check which version of software i'm currently running? I had a Linux DVD (That turned out to be scratched beyond repair) that had Open Office 3.0 and i wish to have it also, but im unsure of what i already have. Did the updates at the beginning give me 3.0 by any chance like it did to my Firefox?

Thats all for now, but i don't doubt i will be here at a later date. Please help me to the best of your ability, and if theres somewhere else i should be going please give me a roadmap to said place.

Thankyou

---

### Post by jaminux on 2009-03-04
[QUOTE]When i boot my pc i see about 5/6 Ubuntu Choices (Kernel 11 * 2, Kernal 7 * 2, another choice [i think, one was a safe mode equivelant]) and then my old XP OS, how do i make it so that there is only one Ubuntu option, or only 2 (The one i use + its safe mode)?[QUOTE/]

This involves editing a (critical) text file. Maybe not the easiest thing to do for first timers, I don't want you to break your boot loader when you have just started and put yourself off. But Linux is all about choice so I will tell you anyway, the decision is yours. It is easily restored though even if you do break it, if you know how.

1) Applications > Accessories > Terminal

2) Type 

sudo cp /boot/grub/menu.1st /boot/grub/menu.1st.backup 

and then press enter (enter password)

3) Type 

sudo gedit /boot/grub/menu.1st 

and scroll down to the bottom of the file    

4) So here are your entries in the menu. 

One for Windows and one for the rest.

Leave everything with #s (comments).

Above the entry about other operating systems are some more entries with names like Ubuntu 8.10 blah blah blah...

To keep the most recent normal and the safe mode simply delete the whole paragraph for the bottom 3 entries (saying Ubuntu blah blah).

If you get this wrong you might break your boot loader.

Restoring it however is simple.

Just boot to the live cd using "try ubuntu..."

Use firefox and read the instructions on [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by jaminux on 2009-03-04
You already have OO 2.4 btw. Open Office 3.0 is coming soon, not quite yet though. You can get it if you want but it will be slightly harder than installing software the default way.

I recommend just waiting. The next release is due in April, and it will just be a case of updating then.

---

### Post by billgoldberg on 2009-03-04
> When i boot my pc i see about 5/6 Ubuntu Choices (Kernel 11 * 2, Kernal 7 * 2, another choice [i think, one was a safe mode equivelant]) and then my old XP OS, how do i make it so that there is only one Ubuntu option, or only 2 (The one i use + its safe mode)?

You can do it the text way like the previous poster mentioned but there is a GUI program available that can do this for you, it's called BUM (boot up manager?).

> How do i check which version of software i'm currently running? I had a Linux DVD (That turned out to be scratched beyond repair) that had Open Office 3.0 and i wish to have it also, but im unsure of what i already have. Did the updates at the beginning give me 3.0 by any chance like it did to my Firefox?

Open up you package manager (system -> administration -> synaptic) and search for the program. The version number will be mentioned.

Open Office will not be updated to 3.0. Firefox was an exception because when 8.10 was shipped it was using the FF 3 beta.

You only get security updates for programs installed. 

There is nothing stopping you from removing the version you have and going to the OOo site and downloading the newest version.
lace.

--

About the updates, yes they are necessary.

Just install everything you get.

Those are security updates most of the time.

---

### Post by The Cog on 2009-03-04
Just to expand on that, the file /boot/grub/menu.lst is the file that controls what the boot manager displays. Lines starting with a "#" are comments for the benifit of human readers and get ignored by the bootloader. The lines that define the menu are towards the bottom of the file, and are in groups separated by blank lines. Typically a group will have a title, uuid, initrd and kernel line and maybe a quiet flag.

Rather than deleting a group, I always just put "#" at the beginning of every line in the group. You can expect the file to get re-written occasionally when a new update changes the name of the kernel but it doesn't happen too often. Just go back and comment the unwanted groups out again.

---

### Post by konqueror7 on 2009-03-04
welcome to the forums and to linux! just follow **jaminux** said, and will be alright... but then, those extra kernels or options you see during boot-up can be your "restore point" so to speak, in case there occurs a problem after an update anything else, you can just select the last kernel/option that worked for you...:D

also you can install *Start-Up Manager* from the Add/Remove or synaptic, this will enable you to customize your boot..

---

### Post by Von-Dyke on 2009-03-04
Wow, you guys..Are amazing, really. Theres so much..help available.. I had been planning on posting and checking back in a couple of days, but after what, 15minutes?, ive already got answers to my problems.
Thanks guys, you are gods among men.

---

### Post by konqueror7 on 2009-03-04
> **Von-Dyke said:**
> 
Thanks guys, you are gods among men.

it just so happen that your post was the one we first found:D...and also, that's blasphemy...hehe...

---

### Post by Von-Dyke on 2009-03-05
> **jaminux said:**
> [QUOTE]When i boot my pc i see about 5/6 Ubuntu Choices (Kernel 11 * 2, Kernal 7 * 2, another choice [i think, one was a safe mode equivelant]) and then my old XP OS, how do i make it so that there is only one Ubuntu option, or only 2 (The one i use + its safe mode)?[QUOTE/]

This involves editing a (critical) text file. Maybe not the easiest thing to do for first timers, I don't want you to break your boot loader when you have just started and put yourself off. But Linux is all about choice so I will tell you anyway, the decision is yours. It is easily restored though even if you do break it, if you know how.

1) Applications > Accessories > Terminal

2) Type 

sudo cp /boot/grub/menu.1st /boot/grub/menu.1st.backup 

[/url]

Got this far and the Terminal tells me that:

cp: cannot stat `/boot/grub/menu.1st': No such file or directory

---

### Post by lindsay7 on 2009-03-05
I used this last night.

From within Ubuntu, open a Terminal. then:

sudo gedit /boot/grub/menu.lst

This is the file containing the boot order. Any line begiining with a hash (#) is a comment.

Towards the bottom, you will see the Windows boot instructions. Cut and past so that those instructions precede the boot instructions for your ubuntu. I don't mean put them at the top of the file, I mean relative to the other boot instructions.

Just keep in mind that there are several "sample" boot instructions, commented out.

Save the file, then you can reboot.

What if you made a terrible mistake, and bungled the editing? All is not lost. You can edit that file using something such as a live Linux distribution on a USB stick. Just keep in mind that you need to edit the menu.lst file on your hard drive, not the one within the live Linux distro.

---

