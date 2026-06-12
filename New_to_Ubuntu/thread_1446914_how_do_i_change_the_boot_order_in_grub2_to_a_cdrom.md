---
title: "how do i change the boot order in grub2 to a cdrom with windows vista on it?"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by arayastarshine on 2010-04-04
i need to uninstall linux because i need to run some windows programs and i'm pretty much a linux noob, so i'm not really sure how to do this. i've done days of research and have come up with hardly any answers.

i am running the newest version of ubuntu and i have need to boot from a windows vista cd and i can't enter my computer's BIOS to change boot order. when i press any buttons before grub2 loads, it only opens the grub menu and there is no option to boot from a cdrom. how do i change this? please remember i am a linux noob and any help would be greatly appreciated :)

---

### Post by s_ø on 2010-04-04
why cant you enter your bios? just press delete (or F1) during post.

---

### Post by arayastarshine on 2010-04-04
i do, i've tried pressing many buttons to enter BIOS and it only opens the grub menu with a list of different versions of the operating systems to boot. i guess i need to know how to add the option to boot from the cdrom and i'm not sure how to go about doing that.

---

### Post by s_ø on 2010-04-04
Strange.
Try pressing F2 after restart. this should give you a boot menu where you can choose boot device.
Which bios are you using?

---

### Post by arayastarshine on 2010-04-04
i've already tried doing that.

i'm not sure what BIOS i'm using, or how to tell really. i'm using a sony vaio laptop with a brand new hard drive that never had windows or anything else on it if that makes a difference, linux was the first OS to be installed on it.

---

### Post by coffeecat on 2010-04-04
You need to enter the BIOS, and if you don't know the key to press for this (it could be a lot of things), then post the model/make of your motherboard and/or computer. A google search should tell us what key you need.

By the way, if the BIOS is not set to boot from CD, how did you install Ubuntu? From a bootable USB pendrive?

---

### Post by JKyleOKC on 2010-04-04
What kind of computer are you using? If you tell us the make and model we'll be much more able to help you change the boot order. Many recent machines have a function key to press immediately after powering up that will bring up a "boot device" menu -- and if you installed Ubuntu from a CD the chances are that your BIOS boot order still calls for looking at the CD first, before the hard disk...

---

### Post by drs305 on 2010-04-04
arayastarshine,

Welcome to the Ubuntu forums. 

As was mentioned, booting first from a CD is usually set in the BIOS.

1. Are you sure you are pressing the 'BIOS' setup key early enough? Usually it is just after the first beep.

2. Do you know for sure which key to press? There are web sites that list the BIOS setup keys for different machines, and sometimes different versions of machines. If you tell us what type of computer you are using we may be able to ensure you are pressing the correct key.  (Edit: Answered).

I'd like to be able to tell you how boot your Windows CD from Grub2, but I don't know that it is possible.

---

### Post by coffeecat on 2010-04-04
> **arayastarshine said:**
> i'm using a sony vaio laptop

For my Vaio laptop you use F2. From the handbook:

> Press the **F2** key.
The BIOS setup screen appears. If not, restart the computer and press the F2 key several times when the VAIO logo appears.

---

### Post by mick222 on 2010-04-04
ON SOME COMPUTERS F11 gives boot options .

---

### Post by s_ø on 2010-04-04
If there is a splash screen instead of normal boot screen during boot press and hold **esc**. This should tell you the key to press. If it goes to fast press **pause/break**

---

### Post by arayastarshine on 2010-04-04
i believe for the sony vaio the key is f2 or f3. i've restarted my computer bunches of times trying out different keys and they all seem to only open the grub menu.

it was installed from a cd by a friend and when he did it, he mentioned that he had problems entering the BIOS as well but wasn't sure what the fix was. 

i feel like there is an easy solution the problem that i'm just overlooking, but i have no idea what that could be.

---

### Post by coffeecat on 2010-04-04
> **arayastarshine said:**
> it was installed from a cd by a friend and when he did it, he mentioned that he had problems entering the BIOS as well but wasn't sure what the fix was. 

If your friend had difficulty entering the BIOS, then hopefully he did not change the boot order back again. I set all my machines to boot from CD - it makes no difference if there is no disc in the drive. Have you tried booting from the Vista DVD?

I should think you are not pressing F2 early enough.

---

### Post by arayastarshine on 2010-04-04
alright, so i finally got into the BIOS and i changed the boot order to the cdrom, however the cd still doesn't boot, when i restart the computer the grub menu comes up automatically now and there is no way to choose the cdrom to boot with.

i'm so confused :[

---

### Post by s_ø on 2010-04-04
Ok. How did you get into your bios?
Did you remember to save the settings? usually F10, but it might be different.

Edit: Are you sure there is a bootable cd/dvd in the drive? Does it try to boot the cd/dvd before booting grub?

---

### Post by bhmildy on 2010-04-04
perhaps your CD is not bootable.  Try a CD that you know is bootable, like your Ubutu CD (even though you don't want to install Ubuntu again) to see if it's really booting first to CD.
After you try that, type everything printed on the CD here so we can see what it is.

Sony used to give people system restore CDs instead of operating system install CDs, back 10 years ago, so it might not be bootable.  You might be able to skip all of this by checking if there's a hidden partition with an image of your hard drive with the brand new factory fresh state with original OS and all installed programs on there.  Your friend might have wiped that out in the Ubuntu install (it's easy enough to wipe out).  To find out, [COLOR=red][/COLOR] boot up ubuntu, and go to administrator menu, disk administrator. check out how many partitions you have.  hopefully you'll have at least 3 (linux, swap and some unreadable or NTFS/windows partition which will be at least 1.5 gigs or less than 10 gigs)

I'd try to do a restore, rather than an OS install, because it's easy and Vaios are a hornet's nest of persnickety drivers to install (or at least used to be).  my next step would be go go cruising through the vaio support website, searching for [model number] + "system restore"  Your restore might be as easy as hitting F12 (or F+ something) and putting in the Vaio CD.

---

### Post by arayastarshine on 2010-04-04
i'm pretty sure it's a bootable cd. i burned it myself actually. and when i open it i can view all the contents on the cd, one of the files is a setup.exe files, so i'm pretty sure it's okay.

is there any other type of cd i can use to check? i don't have access to the linux cd anymore.

---

### Post by coffeecat on 2010-04-04
> **arayastarshine said:**
> i'm pretty sure it's a bootable cd. i burned it myself actually. and when i open it i can view all the contents on the cd, one of the files is a setup.exe files, so i'm pretty sure it's okay.

A Vista CD? No. Vista comes on a DVD. And what exactly do you mean when you say you burnt it yourself? Did you burn it from an ISO image, or did you simply copy the contents of one disc to another? Because, if you did the latter, it won't be bootable.

---

### Post by bhmildy on 2010-04-04
"setup" doesn't mean anything.  CDs are bootable because they have an operating system on them, not setup files.

---

### Post by arayastarshine on 2010-04-04
the hard drive in my vaio is not the original one that came when i purchased it, if that makes a difference. perhaps i did burn it wrong, it was just an .iso file, and i believe i used brasero. the first time i did it asked me if i wanted to copy the contents or just burn it to a disc and i chose copy the contents, but when i tried to burn another copy that option didn't come up and it just started copying it automatically.

---

### Post by s_ø on 2010-04-04
Can you boot ubuntu? And do you have access to a cd/dvd burner? Then burn a new copy of vista and a new copy of ubuntu. Make sure you burn the .iso files to the disks and dont just make a copy. If in doubt ask.

---

### Post by arayastarshine on 2010-04-04
I'm pretty sure it has to do with the copy of vista that I have. I burned 2 copies of it different waysways and neither of them worked. unfortunately I don't have the funds to buy a copy of vista right now, so I settled for downloading one that's probably not legit.

---

### Post by s_ø on 2010-04-05
Ok. Cant really help you with that.
But as someone wrote in a previous post, your laptop probably came with a recovery partition. It might still be there.
Boot into ubuntu and open a terminal. Use fdisk to get a list of partitions.
```
sudo fdisk -l
``````

```
Post the output of the command.

If the recovery partition is gone and you really need windows you should buy a copy and get support from microsoft.

You havent written why you need to use windows, there is a good chance that whatever you need to do can be done with Ubuntu. You can post about your needs a see if someone knows how to do it on Ubuntu.

---

### Post by mullinsn2000 on 2010-04-05
He said that this is not the original HDD that came with the computer so the recovery partition will not be there.

The CD (should be a DVD as I do not think a bootable version of Vista would fit on a CD), is probably burned incorrectly and is not bootable.

OP:  You need to to burn the Vista disc to be bootable.  Copying files will not work, but you will probably not get too much instruction on here if you are using an illegal copy of Vista.  If you need Windows, you will probably have to buy a legit version.

---

