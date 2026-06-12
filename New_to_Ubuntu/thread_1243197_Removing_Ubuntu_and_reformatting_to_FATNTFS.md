---
title: "Removing Ubuntu and reformatting to FAT/NTFS"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by John Macnab on 2009-08-18
Hi everyone :)
I would like to ask a newbie question, if it has already been answered(which is more than likely), please just direct me to the thread.
I would like to remove Ubuntu from my HDD and reformat the Linux partitions to ntfs/fat so that my Windows XP can access them.I have no idea as to how to go about it, so could someone kindly take the time to post the steps I need to follow so as to remove Ubuntu and repartition/reformat the Ubuntu partitions into a Windows readable partition please.

---

### Post by MelDJ on 2009-08-18
do you have windows? if yes, just go to computer management and reformat drive in ntfs or fat.

---

### Post by John Macnab on 2009-08-18
Oh yes sir I do have Windows. That is all it takes? Wow tyvm for your reply sir.If I may, I would like to ask what the procedure would be in case no Windows was available? Boot using Windows boot disk and use Fdisk?

---

### Post by MelDJ on 2009-08-18
yeah. That basically removes everything on your disk. so u will lose ubuntu and everything in it:popcorn:

---

### Post by amsum on 2009-08-18
First make sure you have Gparted installed. If not, then install it using Synaptic. Now goto System->Administration->Partition Editor (gparted). From there you can reformat the partitions in FAT32/NTFS file systems.

WARNING: take the backup of data stored in partition you intend to format.

---

### Post by amsum on 2009-08-18
well, here I suggest you to do the following.
suppose you have no windows and in ubuntu you have the following partition: Root, Swap, Home, Partition1, Partition2

you just go to gparted and delete the partition1 & 2 (NOTE: move all data of 1 & 2 to Home partition) and reformat it in FAT32/NTFS. Now reboot using windows bootable CD and install it in either Partition 1 or 2. Now from windows you can format the remaining drives in FAT32/NTFS.

---

### Post by John Macnab on 2009-08-18
Ty for the replies, both of you :)
amsum, sir, can I reformat my Linux partition while logged in into Ubuntu? What I meant was to get rid of the whole Linux partitions and make those freed up space  available to Windows as a new partition.

MelDJ, I assume that you meant I could use Fdisk to delete and repartition/reformat the Linux partitions- by booting into Windows disk and choosing Fdisk.

Sorry amsum, I was typing while you made your statement, my apologies sir. If I just have root, home and swap partitions, I wont be able to install Windows without first deleting Linux, right?

---

### Post by MelDJ on 2009-08-18
No. not the fdisk in cmd. but in control panel-administrative tools- computer management- under disk management

---

### Post by amsum on 2009-08-18
well, can you give me your partition details. how many partitions and of what size?

---

### Post by Wim Sturkenboom on 2009-08-18
> **MelDJ said:**
> do you have windows? if yes, just go to computer management and reformat drive in ntfs or fat.Don't do that! You will have to fix your MBR after that.

I strongly suggest that you run fixmbr from within Windows and next use windows tools to reformat the partition.

---

### Post by John Macnab on 2009-08-18
TY everyone, for the replies. I fooled around with disk management and got rid of the Ubuntu partitions but I forgot to write down what I did, now the puter works well but I dunno what I did *sheepish look*. Sorry for annoying all you nice folks.

---

### Post by lkraemer on 2009-08-18
You first need to tell us the exact way that Ubuntu was installed.
If you shrank the original Windows partition with software like
Gparted while using the LiveCD, then I's suggest trying to correct
your MBR (Master Boot Record) first by running SurerGrub.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

Then when you have the MBR repaired boot into Windows and make sure
it boots up correctly, meaning that you correctly removed GRUB.

Next, Boot from the Ubuntu LiveCD, and locate the EXT2 or EXT3 and Swap
Partitions.  Turn off using Swap, then double check that you know 100%
which partitions you want to delete.  Delete them and resize the Windows
partition to use all that new space.

Then once again boot into Windows and let it recognize the new added space.

But, Why the hurry to get rid of Ubuntu.  Give it some time because you
didn't know Windows when you started out, and if you had left Windows 
this fast you would still be using CP/M or some other DOS Based system.

Good Luck.

lkraemer

---

### Post by John Macnab on 2009-08-18
Ty for the reply sir. I did have Windows on my machine when I installed Ubuntu.I reorganized my HDD using Gparted (the one that came with the live cd I mean).As for going back to Windows, sir,Linux is too geeky for poor ole me- somehow Windows seems to be easier for me and I am not a puter wizard :( Plus,there are more games geared towards Windows than Linux hehe. I am just not smart enough for Ubuntu.*sighs* Just look at this topic, just a small question as to how to repartition or reformat Linux partitions and the answers are beyond me. *sorry for my bad english*.

---

### Post by lovejames on 2009-08-18
I have a similar issue. I am currently on karmic alpha 4. How do I remove this software? I have installed Karmic on D drive. At the time of installation also I chose this partition. But now when I log into windows, it shows me details of all other drives except D Drive. In such case, how do I reformat?

---

### Post by stinger30au on 2009-08-18
[http://www.ubcd4win.com/](http://www.ubcd4win.com/)

or

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

both totally free and will do what u want

---

### Post by riazrahaman on 2009-08-18
Boot from ubuntu live cd.

Open gparted from command line or from system-> administration

Delete all the partitions and click apply.

This should erase all partitions on the hard disk and update your MBR with the new partition table.

---

### Post by Wim Sturkenboom on 2009-08-18
> **lovejames said:**
> I have a similar issue. I am currently on karmic alpha 4. How do I remove this software? I have installed Karmic on D drive. At the time of installation also I chose this partition. But now when I log into windows, it shows me details of all other drives except D Drive. In such case, how do I reformat?
Run fixmbr from within Windows; this will remove Grub from the MBR). Next go to disk management in Windows and format the partition.

---

### Post by ymra on 2009-08-19
This question Just seems to require this link.  :D


[http://support.microsoft.com/kb/247804](http://support.microsoft.com/kb/247804)

---

### Post by John Macnab on 2009-08-19
Ty for the replies and links everyone :)

---

### Post by isee on 2009-08-19
Hey John!  Don't give up on Linux.  You have a dual boot system yes?  I do too, but rarely boot into Windows anymore.  I don't play games, just surf and e-mail, and Linux never seems to crash, grey-outs a little but I'd rather have that than having a slow system (mine are older) due to having to run an AV and Firewall.

Why don't you like Linux?

---

### Post by Chalfont on 2009-08-19
> **isee said:**
>  Why don't you like Linux?
I don't know what John's answer will be but for me it still seems to require too much programming knowledge.  My issue with the display in my HP2133 netbook - people in the past (on other forums) have told me to recompile a kernel!  For God's sake, I can't even find the configuration file that is supposed to be there.

I would dearly love to use a non MS OS (but cannot afford a Mac) but currently Linux is defeating me, sorry for all the supporters out there, but currently the learning curve looks too steep and too long to even get the thing working, let alone properly using it.  The awful trouble with Windows is that I switch it on, it works, albeit with all the slowness, bloat, viruses, root-kits and other negatives: But it works.

---

### Post by SuaSwe on 2009-08-19
Chalfront, I've replied to your original post regarding that res problem and it should be easy to resolve. :)

---

### Post by John Macnab on 2009-08-19
Ty everyone for the input :)
isee, well sir to me Linux seems to need a lot of puter knowledge which I dont have. I dont even know how to install programs in Linux (I mean those programs which arent in the repositories). I also had trouble trying to run Video CD's on Linux. I do go in for gaming with my puter and most games are for Windows. I frankly am unable to use Linux as I do Windows, for some reason Windows comes up as an easier way to get stuff done. As Chalfont said, the learning curve beats me. I tried to get video working in Linux which I did after coming in here and other forums but it took a lot of doing to get it done while in Windows Video CD's work by default. I ended up writing how to do stuff in a book and doing the steps I have written down without really knowing what I am doing. I ended up having to look up even the smallest thing in the book where as in Windows those things -like installing a program- seems to be easier. Well in a nutshell it is just that I am not intelligent enough to do things via Linux. I am in my 30's and feel that I am too old to learn Linux now- frankly it scares me stiff :p

---

### Post by Mark Phelps on 2009-08-19
> **John Macnab said:**
> I do go in for gaming with my puter and most games are for Windows. 
As you can see from my sig line, I use a variety of OSs; thus, my recommendation is simple -- use what works best for you.  If you're heavily into gaming and those games are MS Windows based, then MS Windows is the best solution.

>  .. for some reason Windows comes up as an easier way to get stuff done. 
It all boils down to what you're used to.  If you learned to use desktop PCs with MS Windows, that's naturally going to seem easier to use. 

> Well in a nutshell it is just that I am not intelligent enough to do things via Linux. I am in my 30's and feel that I am too old to learn Linux now- frankly it scares me stiff :p
Don't sell yourself short.  It's not a matter of intelligence; it's not a matter of age.  It's a matter of how much time you're willing to spend to learn something new.  I know people twice your age that have learned how to use Linux and are happy with it.

But as I said, use what works best for you.

---

### Post by SuaSwe on 2009-08-19
> 
It's a matter of how much time you're willing to spend to learn something new.


Indeed, I felt like the biggest pleb in the world during my first month (or two? :oops:) of using Ubuntu - it's only because I'm genuinely interested in learning more that I've grown comfortable with it. Definitely nothing to do with my superior intelligence! ;)

---

### Post by fooman on 2009-08-19
> **John Macnab said:**
> Well in a nutshell it is just that I am not intelligent enough to do things via Linux. I am in my 30's and feel that I am too old to learn Linux now- frankly it scares me stiff :p

lol....that part cracks me up!  :lolflag:

i did not start using linux until about 5 years ago...i am now 50,  so that made me around 45-ish.  that was after using various windows os for some 4-5 years previous.

and as far as intelligence goes....well, just check some of my posts and you will see that smarts are not really that big a necessity.   :P

linux is great,  but obviously not for everybody.  alls it requires is some time and effort.  comes easier for some then others,  but if you have the basic intelligence to use a computer in the first place...you can certainly learn to use linux with a little patience.  ;)

---

### Post by Don1500 on 2009-08-19
> **lovejames said:**
> I have a similar issue. I am currently on karmic alpha 4. How do I remove this software? I have installed Karmic on D drive. At the time of installation also I chose this partition. But now when I log into windows, it shows me details of all other drives except D Drive. In such case, how do I reformat?

You can't see the partition in Windows because it is formatted as either ext3 or ext4. Windows does not recognize these formats and just sees the partitions it does recognize. As far as Windows is concerned, there is no D Drive. To reformat your drive correctly you need G-parted. FIX YOUR MBR! Then delete the partition you have Karmic in, and the swap partition, resize your C drive (The one you have windows on)to recover that empty space, hit apply, wait for this to complete, reboot and your done.

BTW I started with Linux 2 years ago, I was 61 last month. Aside from "better", Linux is more fun, the computer is my hobbie I don't want it to be simple.
I still dual boot with Windows (in fact now it's triple boot with Kubuntu-Ubuntu-Windows) since most of the programs I run don't work in Wine.

---

### Post by John Macnab on 2009-08-21
Thank you, everyone for replying :) I will go with Windows for a while now and maybe try Ubuntu again laters. It is amazing (for me) to see that people who are older  than me have taken up Ubuntu and are good at it. Thank you everyone, for the kind words, I wish Windows had a support site like this one.

---

