---
title: "Vista,Windows 7 and Ubuntu Lucid dual boot"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by webmist09 on 2010-05-13
Sorry if this is somewhere already,  I couldn't find it. I have a Vista/Win7 dual boot already working on a Dell 200 desktop. PC came with Vista and XP preinstalled. I had installed Vista (over XP as clean install) but earlier this year installed Windows 7. over everything, so only one OS.  Recently added Ubuntu Lucid in a dual boot and worked very well, but then realised I really needed to have Vista too  so....

Uninstalled Lucid, reformatted that partition and reinstalled Vista in its place . My question now is because I am not sure how the boot works. When I am in Vista it is "C" and when I am in Win 7 it is "C" if you get my meaning. So a bit nervous about installing Ubuntu. Have done a dual boot with Ubuntu before, I love it and would like to trash Windows but I need the three OS for testing websites, I am studying web development at the moment.

What do I need to do to install Lucid so that grub will give me three OS to choose from? is there anything I need to be aware of with the two Windows?

If this is already posted elsewhere, a link would be appreciated.

thanks in advance you wonderful Ubuntu people!:P

---

### Post by fuzzyworbles on 2010-05-13
just install ubuntu and grub will figure it all out for you. be sure to manually partition during setup. the result will be that either a) grub will let you select between 7, vista and linux, or b) same, but selecting the last installed MS OS will result in the MS OS selection menu - no problem, just a hassle for OCD types.

.. also, you're "C" worry is needless. windows will make everything relative. it's self-centric that way.

---

### Post by nhasian on 2010-05-13
you should stop thinking of your hard disk in letters and start thinking of them in partition numbers like sda1 for the first partition on your first hard disk sda2, etc.

windows 7 will need two partitions itself.  vista only needs one, and Ubuntu will need minimum 2, 3 if you would like a separate home or data partition.

I hope you have a big hard disk, or multiple hard disks in your machine.  since you need so many partitions for the different operating systems, you will need to create an extended partition for the logical partitions.  you are limited to only four primary partitions per hard disk

---

### Post by Meskarune on 2010-05-13
wouldn't it be easier to run vista in a virtual machine? Uless your computer doesn't have high specs.

On my desktop computer I have windows 7 installed and arch linux installed with a windows xp virtual machine and xubuntu 10.40 and opensuse. (I have 3 harddrives)

In the windows xp virtual machine I run dreamweaver and photoshop and other apps. I use windows 7 for games. 

But anyways, as long as you partition the drives beforehand, you shouldn't have any problems with multiple versions of windows on your computer.

---

### Post by Mark Phelps on 2010-05-13
Actually, so you won't be surprised when you see this, GRUB will really only give you two OS choices -- Vista(or Windows 7) Loader and Ubuntu.

That's because GRUB will hand off control to the MS loader resident in the partition you use.  If you're now getting an OS menu when you boot into Windows, you will still get that same menu when you select the MS loader from GRUB.  It doesn't provide you the capability to indicate WHICH MS Windows OS you want to boot.

---

### Post by walt.smith1960 on 2010-05-13
[QUOTE=nhasian;9291139
<snip>
I hope you have a big hard disk, or multiple hard disks in your machine.  since you need so many partitions for the different operating systems, you will need to create an extended partition for the logical partitions.  you are limited to only four primary partitions per hard disk[/QUOTE]

I use a piece of shareware for multiboot installations.  Yes i paid for it, the price was pretty reasonable, I thought.  [http://www.terabyteunlimited.com/bootit-next-generation.htm](http://www.terabyteunlimited.com/bootit-next-generation.htm). BootItNG will support in excess of 100 primary partitions.  I'm not sure about its support for ext4 but I suspect the support is there.  BootItNG isn't the most intuitive piece of software to use but once I got used to it it has worked okay.  Just have to be careful when using bootit NG  to put grub in the Linux partition, not in the MBR which overwrites BootIt NG's  EMBR.  This can be recovered but it ain't easy.

---

### Post by QLee on 2010-05-13
[QUOTE=walt.smith1960]I use a piece of shareware for multiboot installations.  Yes i paid for it, the price was pretty reasonable, I thought.  [http://www.terabyteunlimited.com/bootit-next-generation.htm](http://www.terabyteunlimited.com/bootit-next-generation.htm). BootItNG will support in excess of 100 primary partitions.  I'm not sure about its support for ext4 but I suspect the support is there.  BootItNG isn't the most intuitive piece of software to use but once I got used to it it has worked okay.  Just have to be careful when using bootit NG  to put grub in the Linux partition, not in the MBR which overwrites BootIt NG's  EMBR.  This can be recovered but it ain't easy.[/QUOTE]

There is nothing wrong with BootitNG, I've used it myself in the past. However, I don't like to recommend installing third party software to someone who is just starting out and that might be the case here since it is the OP's first post.

The biggest problem I see with your advice is that Ubuntu now uses GRUB-PC (GRUB2) and the recommendation is to not try to install GRUB2 to a partition in the manner that we used to do with legacy GRUB. And, all of this stuff is likely to be confusing for a new user, I prefer to try and help them with the avauilable software and so things conform to Ubuntu tutorials and guides. YMMV.

---

### Post by webmist09 on 2010-06-02
thanks everyone, I got them working together nicely. Just changed the Win 7 partition to active and boooted to make sure it was still working ok, checked out in diskk management, then deleted the Vista partition. Rebooted no probs with just one OS so was easy to install Lucid Lynx in the new empty partition.

Didn't want Vista at all so don't mind it being gone.

thanks for all the advice!

---

### Post by sandyd on 2010-06-02
hmm... I see that youve figured it out, but you can use some services such as browsershots.org and browsercam.com to see how your site looks in multiple browsers (my own site doesn't function properly in IE8.........)

---

### Post by webmist09 on 2010-06-17
well I am back, different and very annoying problem this time. After getting the dual boot to work, spent a couple of days in Lucid then switched to Windows where I needed to do some stuff and guess what, when I tried to log back into Lucid it wont let me. Note the boot options are fine, and it gives me the Lucid login but obviously working in Windows has mucked up something, cause now it is asking for login detals (which it won't authenticate anyway!) even though I had it set to log me in automatically. 
 
I have not seen this problem anywhere in anything I have read about Windows 7/Lucid dual boot - people have probs getting to the login screen, my problem is I cant get past it, I hope someone can help.
 
I am verrrrrrrrrrrrry close to ditching Windows altogether grrrrrrrrrrr

---

### Post by julio_cortez on 2010-06-18
> **webmist09 said:**
> well I am back, different and very annoying problem this time. After getting the dual boot to work, spent a couple of days in Lucid then switched to Windows where I needed to do some stuff and guess what, when I tried to log back into Lucid it wont let me. Note the boot options are fine, and it gives me the Lucid login but obviously working in Windows has mucked up something, cause now it is asking for login detals (which it won't authenticate anyway!) even though I had it set to log me in automatically. 
I have not seen this problem anywhere in anything I have read about Windows 7/Lucid dual boot - people have probs getting to the login screen, my problem is I cant get past it, I hope someone can help.
I am verrrrrrrrrrrrry close to ditching Windows altogether grrrrrrrrrrr
Sounds strange: as far as I know, Windows can't handle ext4 filesystems so you are relatively sure that it isn't Windows' fault..
Strange but similar to something that happened to me a couple of times where it loaded the boot screen but the "dots" were not moving at all and it stayed like that for, let me say, 5 minutes before I restarted it and lauched a failsafe session.

So, have you already tried booting a "failsafe" session (selecting "continue booting" when asked for a choice) and putting your credentials in that way, then running the "startx" command?

---

