---
title: "I need to uninstall Ubunto and possibly reinstall"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by hhh222 on 2009-12-29
Howdy....FYI...I'm a fairly low level computer user and am not that up on the lingo. Today I installed ubunto 9.10 on my pc with vista [ this will soon be used as an HTPC and I won't really need Ubunto on it}. I would really like to completely uninstall ubunto on this computer but, from what I've seen so far, this does not seem to be possible. I wouldn't mind reinstalling it within windows [I believe I've read that's possible]

As it stands now, Vista is still on the pc and I can choose to boot from vista in startup but I'll eventually want this pc to auto boot up in vista as I won't be using it to surf the web and such and need the easy access the windows media and hp media. This pc has blu-ray and will be mainly connected to a projector.

I installed ubunto from a cd I downloaded  and let it do the auto partition thing.

Eventually I'll want to install ubunto within windows 7 on my new pc so that I can easily go from one to the other, but I really don't need or want it on the pc I just installed it on to test out.  

Thanks.

---

### Post by warfacegod on 2009-12-29
Did you install ubuntu on it's own partition or hard drive? If so, then use Windows to erase that partition or drive. Be careful you choose the correct one!

---

### Post by 3rdalbum on 2009-12-29
Ubuntu.

It's easy enough to remove Ubuntu from your computer. If you installed Ubuntu by booting your computer from the CD and doing the partitioning (which you say you've done), then use the GParted utility from the live CD to remove the Ubuntu partitions. Then boot up a Windows CD and run a recovery console, and run the "fixmbr" command on that. For more details, look up "fixmbr" on Google.

If you had used the Wubi utility (installing Ubuntu from within Windows), you would go to Add/Remove Programs on Windows and remove Ubuntu that way.

Yes you can install Ubuntu within Windows in one of two ways. You can use the Wubi utility on the Ubuntu CD to install Ubuntu into a file on your Windows partition, or you can install some virtualisation software like Virtualbox and install Ubuntu within the virtual machine. With the former, it works like a dual-boot system. With the latter, Ubuntu runs inside a window on Windows.

---

### Post by hhh222 on 2009-12-29
Thanks for the reply. I think it's on it's own partition. I'll have to study up or partitions and see what I can figure out.

---

### Post by PRC09 on 2009-12-29
If you are removing Ubuntu from your computer you will need an original Vista install disk to restore your boot sector.If you dont have the original disk (not the restore disks as that will wipe the whole drive) it is available at the following link....

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)


Or you can use Super Grub Disk from the following.....

[http://www.supergrubdisk.org/index.php?pid=12](http://www.supergrubdisk.org/index.php?pid=12)

---

### Post by barnaclebill18 on 2009-12-29
You might want to just leave Ubuntu on the HD and edit grub to have Vista load first.

If you remove Ubuntu, you will not be able to boot the computer, your Master Boot Record has been overwritten by grub and you will need a Vista installation disc to fix it.

There is a tool called EasyBCD, that I hear will fix the MBR, but I have not used it.

---

### Post by presence1960 on 2009-12-29
Or you can boot into ubuntu and use lilo to restore the windows MBR. Open a terminal and run

```
sudo apt-get install lilo
```

Then once installed run this in terminal:

```
sudo lilo -M /dev/sda mbr
```

assuming you only have one internal hard disk, if you have multiple hard disks replace sda with the proper designation with windows & ubuntu on it. Reboot and make sure you can boot to windows.

Now you can boot the ubuntu Live CD & choose "try ubuntu without any changes". When the desktop loads open a terminal (Applications > Accessories > Terminal) and run gksu gparted.

Right click on your Ubuntu partitions one by one and choose Delete. Click Apply (green check mark) on top toobar and let it do it's job. When done reboot into Vista and use the disk management utility to create a new NTFS partition or merge the unallocated space with your Vista partition.

---

### Post by gletob on 2009-12-30
> **presence1960 said:**
> Or you can boot into ubuntu and use lilo to restore the windows MBR. Open a terminal and run

```
sudo apt-get install lilo
```Then once installed run this in terminal:

```
sudo lilo -M /dev/sda mbr
```assuming you only have one internal hard disk, if you have multiple hard disks replace sda with the proper designation with windows & ubuntu on it. Reboot and make sure you can boot to windows.

Now you can boot the ubuntu Live CD & choose "try ubuntu without any changes". When the desktop loads open a terminal (Applications > Accessories > Terminal) and run gksu gparted.

Right click on your Ubuntu partitions one by one and choose Delete. Click Apply (green check mark) on top toobar and let it do it's job. When done reboot into Vista and use the disk management utility to create a new NTFS partition or merge the unallocated space with your Vista partition.

This is the best solution in the thread IMO.

---

### Post by barnaclebill18 on 2009-12-30
Except that the OP claims to be a low level computer user and would surely have problems with the best solution.

---

### Post by presence1960 on 2009-12-30
Not a difficult solution for even a novice. The alternative is to boot from a windows install CD/DVD to restore the windows bootloader, which involves terminal commands anyway or download an Super GRUB disk iso and burn that to CD and boot from it. Did you ever see the menu options on Super GRUB disk?  Then removing the linux partitions. Unfortunately there is no way to restore the windows bootloader to MBR from a GUI so windows can boot .

Even for a novice that is a fairly straightforward how to and the commands can be copied from the code boxes and pasted into the terminal.

Why do "we" assume people new to Linux are not capable of doing things? They ask for help and we try to help them. Sometimes the only way to accomplish certain tasks are through the terminal. That is just the way it is. As experienced users we should be ready to teach these newbies the way to do things in Linux so that they learn also.

If you have a simpler way that will restore windows bootloader to MBR of that internal disk please inform me.

---

### Post by barnaclebill18 on 2009-12-30
I have not used this tool, but it seems to be able to fix the Vista MBR.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by presence1960 on 2009-12-30
> **barnaclebill18 said:**
> I have not used this tool, but it seems to be able to fix the Vista MBR.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

I know how to use that and it is more complex than the solution I proposed. maybe you should try out your solutions before recommending them to people for use on their machines. You don't even know if it will actually work in this situation. **_Actually it won't work because his windows bootloader is not present since Ubuntu overwrote it on MBR with GRUB._**

Easy BCD is a tool to tweak the Vista MBR, allowing you to use the Vista bootloader to boot other OSs such as Linux. More complicated than GRUB to set up, but you must have a Vista bootloader in place which the OP does not have.

---

### Post by barnaclebill18 on 2009-12-30
> **presence1960 said:**
> Not a difficult solution for even a novice. The alternative is to boot from a windows install CD/DVD to restore the windows bootloader, which involves terminal commands anyway or download an Super GRUB disk iso and burn that to CD and boot from it. Did you ever see the menu options on Super GRUB disk?  Then removing the linux partitions. Unfortunately there is no way to restore the windows bootloader to MBR so windows can boot from a GUI.

Even for a novice that is a fairly straightforward how to and the commands can be copied from the code boxes and pasted into the terminal.

Why do "we" assume people new to Linux are not capable of doing things? They ask for help and we try to help them. Sometimes the only way to accomplish certain tasks are through the terminal. That is just the way it is. As experienced users we should be ready to teach these newbies the way to do things in Linux so that they learn also.

If you have a simpler way that will restore windows bootloader to MBR of that internal disk please inform me.

I agree, but I have been using Ubuntu about a year now, and I still need exact instructions and a brand new user would have a hard time with the instructions provided, I think.

I was proposing an easy solution.

---

### Post by presence1960 on 2009-12-30
> **barnaclebill18 said:**
> I agree, but I have been using Ubuntu about a year now, and I still need exact instructions and a brand new user would have a hard time with the instructions provided, I think.

I was proposing an easy solution.

Your solution is easy? How do you know if you never used it?

Don't arbitrarily decide who is capable of anything just because you have a hard time with it. That is BS!! I am glad you weren't helping me when I was new to Linux.

P.S. The OP was given **_EXACT INSTRUCTIONS_**

---

### Post by barnaclebill18 on 2009-12-30
By my solution I meant editing grub and leaving Ubuntu intact, the EasyBCD was something I just added for information.

---

### Post by presence1960 on 2009-12-30
> **barnaclebill18 said:**
> By my solution I meant editing grub and leaving Ubuntu intact, the EasyBCD was something I just added for information.

Did you read what the OP wants to do. He does not want Linux on this machine. He wants it a Windows only machine! He wants to install Ubuntu on another machine.

**Case closed...goodnight barnaclebill!**

---

### Post by barnaclebill18 on 2009-12-30
I read the post, and taking everything he said into account, I was just making a suggestion that it might be easier to just leave it on, since the problem seems to be Ubuntu loading first.

I was just trying to be helpful, sorry if I did something you did not like.

---

### Post by presence1960 on 2009-12-30
> **barnaclebill18 said:**
> I read the post, and taking everything he said into account, I was just making a suggestion that it might be easier to just leave it on, since the problem seems to be Ubuntu loading first.

I was just trying to be helpful, sorry if I did something you did not like.

> Today I installed ubunto 9.10 on my pc with vista **_[ this will soon be used as an HTPC and I won't really need Ubunto on it}_**. **_I would really like to completely uninstall ubunto on this computer but, from what I've seen so far, this does not seem to be possible_**. I wouldn't mind reinstalling it within windows [I believe I've read that's possible]

_**As it stands now, Vista is still on the pc and I can choose to boot from vista in startup but I'll eventually want this pc to auto boot up in vista as I won't be using it to surf the web and such and need the easy access the windows media and hp media.**_ This pc has blu-ray and will be mainly connected to a projector.

The above is cut from the OP's original request for help. It is irrelevant whether I like what you propose. You offered nothing to help the OP achieve what he wants to do & then you want to debate the point.

---

### Post by barnaclebill18 on 2009-12-30
but I'll eventually want this pc to auto boot up in vista 

This is the part that made me think that this was the thing that concerned him.

Hey, I was born in Philly, give me a break.

---

### Post by hhh222 on 2009-12-30
Thanks all. I'll be studying up and see what I can do. I really appreciate everyone's help.

---

### Post by hhh222 on 2009-12-31
Alrighty....I'm at the point that I've run  gksu gparted and I'n not sure what I'm looking at and should delete. 

In a block at the top right it says   /dev/sda5    This block is highlighted
                                                  227.57 GiB

The block to the left in     /dev/sda1
                                     454.456 GiB

Below are listed      /dev/sda1   ntsf      HP[my pc is an HP]                                    boot
                             /dev/sda3   extended
                             /dev/sda5   ext4
                             /dev/sda6   linux-swap
                             /dev/sda2   ntsf FACTORY_IMAGE

I'm not sure which or if all should be deleted.

---

### Post by louieb on 2009-12-31
Did you get the Vista boot loader restored?
Don't delete a thing until you do that 1st

---

### Post by danastasio on 2009-12-31
> **presence1960 said:**
> The above is cut from the OP's original request for help. It is irrelevant whether I like what you propose. You offered nothing to help the OP achieve what he wants to do & then you want to debate the point.

Please do not be rude on the forum. I realize that I am not a moderator, but I will report you if you do not stop.

---

### Post by PRC09 on 2009-12-31
How to repair your bootloader....


[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Once you are booting Vista again I believe you can use the disk management tools within vista to re-size your hard drive......

---

### Post by presence1960 on 2009-12-31
> **danastasio said:**
> Please do not be rude on the forum. I realize that I am not a moderator, but I will report you if you do not stop.

I was not rude and I will not stop because there is nothing to stop. So I suggest you go ahead and report me. Sometimes the truth hurts. I am only interested in helping the OP achieve what he wants to do with his machine, which really a newbie can do with some guidance. The OP asked how to remove Linux and someone else keeps insisting that he keep linux on his rig. Sorry if I am sticking to what the OP wants to achieve. Now if what he wanted to do was unachievable I would then agree with barnaclebill. But since removing Linux is a simple task and very doable I will stand my ground on this. So go ahead and press the report button.I want you to do so.

---

### Post by presence1960 on 2009-12-31
> **louieb said:**
> Did you get the Vista boot loader restored?
Don't delete a thing until you do that 1st

**+1**

You can use lilo the way I described or boot your windows install CD/DVD and follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=1014708") for your version of windows. Then remove sda5 & sda6 which are your Linux partitions. That will leave all that space unallocated in sda3 which is an extended partition. If you want to keep an extended partition you can  or if you want to make another primary NTFS partition for windows or add the space to your existing Windows partition delete the extended partition also.

---

### Post by hhh222 on 2010-01-02
Well, I finally got it with a kink here and there.

As far as the extended partition, is there any advantage to doing one thing or the other with it?

Thanks Guys.
__

---

### Post by presence1960 on 2010-01-02
> **hhh222 said:**
> Well, I finally got it with a kink here and there.

As far as the extended partition, is there any advantage to doing one thing or the other with it?

Thanks Guys.
__

[https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics](https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics)

An extended partition has the advantage in that you can create as many logical partitions as you wish inside the extended partition. The only limit on that is how much space you allotted to the extended partition. Example: you created a 120 GB extended partition. You can create ten 12 GB logical partitions, or two 60 GB logical partitions, or one 118 GB logical partition and a 2 GB swap partition (forgot to  mention swap partitions can be inside an extended partition)...I think you can see what I mean now.

This becomes very useful because the limit on hard disks using MBR is 4 partitions. Either you can have on each hard disk up to 4 primary partitions or up to 3 primary and an extended partition.

---

### Post by Dr Belka on 2010-01-02
> **presence1960 said:**
> i was not rude and i will not stop because there is nothing to stop. So i suggest you go ahead and report me. Sometimes the truth hurts. I am only interested in helping the op achieve what he wants to do with his machine, which really a newbie can do with some guidance. The op asked how to remove linux and someone else keeps insisting that he keep linux on his rig. Sorry if i am sticking to what the op wants to achieve. Now if what he wanted to do was unachievable i would then agree with barnaclebill. But since removing linux is a simple task and very doable i will stand my ground on this. So go ahead and press the report button.i want you to do so.

+1

---

### Post by J V on 2010-01-02
> **barnaclebill18 said:**
> You might want to just leave Ubuntu on the HD and edit grub to have Vista load first.+1

Install startupmanager for an easy selection between ubuntu and windows default...

---

### Post by Melee Antoinette on 2010-01-02
keep windows, uninstall u. then reinstall. am i missing somethin here, it does not need to be more complicated does it?

---

