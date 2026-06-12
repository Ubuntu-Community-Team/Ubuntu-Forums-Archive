---
title: "Change from ubuntu to Windows XP"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by Kayrosh on 2009-07-20
I have ubuntu installed on my computer. This is a good operating system only there are some disadvantages about it. Only every time i try to change it back to windows it gives an error. I am using the operating system disk from xp that came with the computer. It should work, only it stops working after the has scanned the disc. Is there any one here who knows how to fix this error. I have tried the many times, and i am absolutely sure my computer has no viruses. Thnx:popcorn:

---

### Post by muteXe on 2009-07-20
So you're completely writing over your ubuntu?
You could try formatting your hard drive first, and then installing xp (only if you want completely get rid of any data on the drive though, i could have interpreted your post incorrectly).

---

### Post by komputes on 2009-07-20
Yeah, if you're saying what I think you're saying, this is a common problem.

I recommend you install Windows first, then Ubuntu. This way Ubuntu's bootloader (GRUB) takes care of giving you the "dual boot" choice between ubuntu and windows. If windows is the last installed operating system, your Master Boot Record is written over and it no longer point to GRUB, but to the windows bootloader, which sadly does not give you a choice to boot into ubuntu. You can fix this but you have to be careful to identify the correct drive/device names.

=================================
 How to Restore the MBR after installing Windows
=================================
When you install ubuntu it will install the MBR, usually on the hd0 MBR 512 bytes of the drive. This is a pointer to a device which has a bootable operating system. grub-install will help you reset that MBR. You will need to boot from the Live CD.

Mount the disk with /boot in its root (in this case it will be mounted to /media/disk) and know which device you would like to install the MBR onto (in this case /dev/sda). After this command the BIOS will boot and pass controll over to the "master disk" /dev/sda which will read the pointer in the first 512 bytes which points it to /boot on /media/disk (/dev/sda1)

```
sudo mount /dev/sda1 /media/disk # check /media/disk to assure that it contains /boot

```
When booting, into grub you may need to edit the root disk in /boot/grub/menu.lst of the disk to get it to boot well. this is due to the disk thinking it is the second disk loaded, but when the bios boots from it it is now seen as the first disk for this you need to change (hd1,0) to (hd0,0)

Once you are sure that your ubuntu installation is on /dev/sda and that you have mounted it to /media/disk you can run the following command to reinstall grub. Afterwards, if you do not see windows in the list you can boot into recovery mode and run the grub-update script.

```

sudo grub-install --root-directory=/media/disk/ /dev/sda
```

---

### Post by muteXe on 2009-07-20
I just assumed he wanted to get rid of ubuntu completely?
Sorry if I got the wrong end of the stick :)

---

### Post by ~sHyLoCk~ on 2009-07-20
Reinstalling grub using Live Cd hould fix this.

---

### Post by presence1960 on 2009-07-20
there is absolutely no reason to install windows before ubuntu! If you have Ubuntu and want to add windows all you need to do is free up some space and create a **_primary partition_** for windows, or leave the space unallocated. Either way should work because when you boot the windows CD/DVD it will recognize either and you can choose to install windows there.

Now we are at the part that strikes fear into people and perpetuates the myth that you should install windows before Ubuntu. When you install windows after Ubuntu Windows writes it's bootloader to MBR. So after you boot your rig after installing windows it goes right to windows. All you need to do is restore GRUB to MBR by doing this which takes all of 5 minutes:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

**In #6 use setup (hd0) to put GRUB in MBR** 

This will put GRUB back on MBR. You may or may not have to edit your windows entry in menu.lst but again that takes all of 2 minutes!

Why would we make someone remove a perfectly good OS to install windows first? What if they had a working dual boot and windows went south? Should they uninstall Ubuntu too and have to install 2 OS's? I think not.

---

### Post by zerhacke on 2009-07-20
You guys keep giving him advice on how to use GRUB when he obviously wants to get rid of Ubuntu altogether.

> **Kayrosh said:**
> I am using the operating system disk from xp that came with the computer.

More often than not the OS disc you are using is a recovery disc and not a full install disc.  They depend on a second partition on the HDA drive that contains all the installation information.  Since you installed Ubuntu and used the entire drive that partition is no longer there and therefore the recovery disc cannot find the information it needs to reinstall.

Generally it is frowned upon to suggest bittorrenting an OS but in this case it is perfectly legal for you to find a copy of your OS on a bittorrent site and use your own key when you install it.  Usually there is a sticker on the side of the case that has your CD Key on it.  Use that key when you install.

Unfortunately it also means that you'll have to find drivers on your own.

---

### Post by komputes on 2009-07-20
> **presence1960 said:**
> there is absolutely no reason to install windows before ubuntu!

Technically you are correct, there is nothing wrong with rewriting the MBR. Although there is a simple reason to install windows before ubuntu, simplicity and usability. Without touching the command line, ubiquity (the graphical ubuntu installer) will create a dual boot setup without needing to touch the command line. Therefore installing windows then ubuntu is usually the preferred choice for novice users.

---

### Post by raymondh on 2009-07-20
@ kayrosh ... kindly clarify this statement from your first post:

```
Only every time i try to change it back to windows it gives an error
```

Does it mean you are dual booting and are having problems booting into windows? If so, is this a regular side-by-side install or a WUBI install?  

Or..... does it mean that you plan to get rid of Ubuntu and just have windows as your sole OS and you are trying to re-install windows? Original XP install disc or recovery disc (supplied by manufacturer)?

---

### Post by presence1960 on 2009-07-20
> **komputes said:**
> Technically you are correct, there is nothing wrong with rewriting the MBR. Although there is a simple reason to install windows before ubuntu, simplicity and usability. Without touching the command line, ubiquity (the graphical ubuntu installer) will create a dual boot setup without needing to touch the command line. Therefore installing windows then ubuntu is usually the preferred choice for novice users.

I can go along with that if they are installing to a clean hard disk, but if they already have ubuntu installed and are told to remove Ubuntu so they can install windows first...I just can't go along with that and sit silently by. That is a big bunch of bolderdash. I understand about being a novice, but there is nothing mysterious about the command line. The sooner someone learns it the better off they are. besides copy & paste into a terminal is only a couple mouse clicks/keystrokes anyway. It is better to be guided thru command line by someone who knows rather than going at it alone.
 I still stand by my words for this thread: do not remove Ubuntu to install windows whether a novice or not, there is a simpler, easier way.

P.S. it is an attitude like that about the command line that keeps people in fear & ignorance. I prefer to give enthusiastic support for one's ability to learn and execute simple command line functions such as restoring GRUB through CLI

---

### Post by komputes on 2009-07-20
I completely agree concerning ignorance of the command line. And you are right the Windows before Ubuntu thing would be for the initial setup, not for recovery.

---

### Post by presence1960 on 2009-07-20
Nothing personal. it is just that i have seen so many people being told that they **_must_** install windows before linux, that they have to remove a perfectly good Linux install to add/reinstall windows. Now for a novice that is a lot of work. I am no expert but i would not want to do that unless it was the only way possible. 

We need to make use of our community documentation such as this : [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

It exists for a reason. All the dirty work has been done and the groundwork is laid for us to use and be successful.

Sometimes we forget that our best learning came from a mistake(s). It will be that way too for our newbies, they don't need to be sheltered, they need to be taught how to use Linux. If the learning curve is too much then maybe they aren't ready or willing to make the switch. I am sure most of the newbies found themselves in the same predicament when they first started using Windows- they didn't know much. But they persevered and learned. it will be so with Linux.

---

### Post by mynameinc on 2009-07-20
Congratulations, you're the first person I've seen on these forums wanting to switch *to* Window$.

---

### Post by raymondh on 2009-07-20
> **presence1960 said:**
> nothing personal. It is just that i have seen so many people being told that they **_must_** install windows before linux, that they have to remove a perfectly good linux install to add/reinstall windows. 

+1 ...

---

### Post by presence1960 on 2009-07-21
> **mynameinc said:**
> Congratulations, you're the first person I've seen on these forums wanting to switch *to* Window$.

No need to be sarcastic. Open Source is about choice right? Then respect others choices as you wish your choice to be respected. There is no shame in using windows if one chooses to do so. That is each persons right to choose, including your right to choose linux!

P.S. Can you explain how your post was helpful in any way please, for the life of me I can't see that it is. Secondly you must not read the forum very often in here because there are quite a few posts of people wanting to switch back to windows.

---

### Post by philinux on 2009-07-21
Calm down guys the OP has not replied. After all it's his thread.

---

### Post by Paddy Landau on 2009-07-21
> **presence1960 said:**
> there is absolutely no reason to install windows before ubuntu!
Actually, there is. Sometimes.

Because...

You might have a system recovery disk provided by your computer manufacturer.

In many cases (including mine, which is Toshiba), the Windows reinstallation automatically, and without asking, wipes the entire drive regardless of what partitions are there.

---

### Post by presence1960 on 2009-07-21
> **Paddy Landau said:**
> Actually, there is. Sometimes.

Because...

You might have a system recovery disk provided by your computer manufacturer.

In many cases (including mine, which is Toshiba), the Windows reinstallation automatically, and without asking, wipes the entire drive regardless of what partitions are there.
Yes, but I believe that is taken out of context. I was commenting on the mentality by some on here who insist Windows **must** be installed first.

So I will bite the bullet here and say you are absolutely correct. I should have thought it out some more. In that situation you really have no choice. But that doesn't let those who insist windows must be installed first off the hook. Because the fact of the matter is except in the case of a recovery disk/partition you can install ubuntu first. 

Thanks Paddy!

---

### Post by HotShotDJ on 2009-07-21
> **presence1960 said:**
> No need to be sarcastic. Open Source is about choice right?No.  It is not.  It is about freedom.

Usually, freedom leads to greater choices... but those choices are a by-product of F/OSS, not the purpose of it. Freedom does require the possibility of having choices, but it does NOT require unlimited choices.  In fact, one can make choices that LIMIT their own freedom (such as using restricted formats, Digital Restrictions Management, proprietary software, etc.), all of which stand in opposition to F/OSS.

Choice, on the other hand, does not always lead to greater freedom.  For example, the OP is certainly under no obligation to exercise the freedoms granted to him/her under F/OSS.  He/She may even choose to sign away freedoms by agreeing to restrictive EULA's.  By making such a choice, one voluntarily restricts his/her freedom.

---

### Post by presence1960 on 2009-07-21
> **HotShotDJ said:**
> No.  It is not.  It is about freedom.

Usually, freedom leads to greater choices... but those choices are a by-product of F/OSS, not the purpose of it. Freedom does require the possibility of having choices, but it does NOT require unlimited choices.  In fact, one can make choices that LIMIT their own freedom (such as using restricted formats, Digital Restrictions Management, proprietary software, etc.), all of which stand in opposition to F/OSS.

Choice, on the other hand, does not always lead to greater freedom.  For example, the OP is certainly under no obligation to exercise the freedoms granted to him/her under F/OSS.  He/She may even choose to sign away freedoms by agreeing to restrictive EULA's.  By making such a choice, one voluntarily restricts his/her freedom.
I love semantics. Without freedom there can be no choice(s). But I think you know what I meant...LOL :D

---

