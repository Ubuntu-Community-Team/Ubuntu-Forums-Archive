---
title: "A liittle bit lost"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by persil on 2010-02-14
I am new to Ubuntu, not to computer and played with Linux in 1996
but can't remember much. I have loaded the latest version of Ubunto ( not from a CD) all worked fine until the recent download of the latest update. I have to admit I did not pay much attention to rhe tick boxes.
I am running Linux at a second partition next to Vista( dualboot)

Problem: after the last update grup is comming up, don't know what to do with it, and don't know how to get to the OP.

Sorry if this question came up before.

Fred

---

### Post by mathfreak123 on 2010-02-14
I'm assuming the GRUB menu is coming up whenever you turn the computer on?

This is to be expected, since you updated your system completely; there have been a few versions of the kernel coming out, so every time you install a new one, the GRUB menu is updated with the new kernels. It'll also detect any other of your OS's installed.

All you have to do is select your latest kernel version to boot into Ubuntu (it'll say something like 2.6.31-19 with some other text). You select the Windows Vista option if you want to boot into Vista.

---

### Post by persil on 2010-02-14
Thanks you are correct, but  how do I know the kernel numbers and text. I my opinion an update should not destroy the simple GUI. When selecting the updates there was no warning or any indication about what will happen. However, I like to continue to find out what is going on. GRUB help is not a help at all. I assume I am not the first person who has this problem. 



Fred

---

### Post by themusicalduck on 2010-02-14
The kernels are usually left on the system so that if a new kernel doesn't work then you can use an older kernel as backup and at least be able to boot into Ubuntu.

There isn't an easy way to reduce the number of kernels listed in the grub menu, but if you really want, you could remove some of the older kernels if you know that the newer ones work fine. Really good software for doing this is Ubuntu Tweak - [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

If you select Package Cleaner on the menu and Clean Kernel, you can uninstall kernels from there. BUT it really is a good idea to leave at least one older kernel installed!

After you've done that, if you open a terminal (Applications > Accessories > Terminal) and run ```
sudo update-grub
``` it'll update your grub menu for you.

---

### Post by 3rdalbum on 2010-02-14
> **persil said:**
> Thanks you are correct, but  how do I know the kernel numbers and text. I my opinion an update should not destroy the simple GUI.

It shouldn't, and usually it doesn't. Unfortunately I haven't had this problem occur to me, so I don't know how to fix it.

To people trying to help: I think Persil is getting the "GRUB>" prompt, NOT the menu.

---

### Post by jken146 on 2010-02-14
[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)

---

### Post by persil on 2010-02-14
Gentlemen 
 I have not followed all the suggestion yet, but what I get after
choosing Ubuntu grom the Windows boot manager is
                             GNU GRUB Ver 1.97 beta
   followed by a three line text and the prompt
sh:grub>

back to the drawing board.

---

### Post by persil on 2010-02-15
this is an update about my ongoing problem. I have installed Ubuntu using the window option. I have contacted a few people around Brisbane who have run Linux for several years but no one where able to help. All GRUB commands will ask for the kernel but I have no information about the kernel. We have used several Grub commands no go. I assume the updates ignoring the windows installation option. This is very disappointing, I have found some postings in other forums about the same problem but never found an answer. Who knows Linux very well to answer my question.

---

### Post by Paddy Landau on 2010-02-15
> **persil said:**
> I have installed Ubuntu using the window option.
Do you mean that you installed Wubi? We need to be very clear as to what's happening, otherwise we are only guessing what is happening to you.

[LIST]
[*] What version of Ubuntu did you install?
[*] If you installed Wubi, what version of Windows do you have?
[*] When do you get the GRUB prompt -- immediately after turning on your computer? Are you able to boot into Windows?
[/LIST]
Please tell us exactly what is happening.

---

### Post by themusicalduck on 2010-02-15
I had this same problem when I installed Ubuntu onto a friend's laptop with WUBI. Not sure why this happens when you do something simple like an update, I agree it is pretty bad.

I followed the steps outlined in this post - [http://ubuntuforums.org/showpost.php?p=8444565&postcount=10](http://ubuntuforums.org/showpost.php?p=8444565&postcount=10) and was able to boot in. Only in the last step it says use command sudo update-grub2 but it should just be ```
sudo update-grub
``` which you run from the terminal like I described above. That will almost certainly fix the grub problem.

If you did all the updates recently, then you can assume that the latest kernel is 2.6.31-19-generic (which you'll need to follow the steps above) or you could just use an older one like it says in the post (2.6.31-14-generic)

This is only if you did install using WUBI, as in you installed Ubuntu inside of Windows.

---

### Post by persil on 2010-02-16
> **Paddy Landau said:**
> Do you mean that you installed Wubi? We need to be very clear as to what's happening, otherwise we are only guessing what is happening to you.

[LIST]
[*] What version of Ubuntu did you install?
[*] If you installed Wubi, what version of Windows do you have?
[*] When do you get the GRUB prompt -- immediately after turning on your computer? Are you able to boot into Windows?
[/LIST]
Please tell us exactly what is happening.

Thank you for the reply, first I have carried out the instruction given and suggested in the next following post. This has locked the computer completely and only after removing power a restart was possible.

Ubuntu 9.10 installed using Wubi out of VISTA Business . Yes I am able to boot into Vista. The Windows boot manager will give only two options VISTA and Ubuntu. No ubuntu version number or any other information. After selecting Ubuntu the promt is sh:grub> shows up. Meanwhile we have installed Ubuntu 9,10 on 5 different Laptops different brands all running Vista. Ubuntu runs fine until a complete update has been carried out  all computer have shown the same problem. It was no problem to remove Ubuntu.

---

### Post by persil on 2010-02-16
Paddy I will get back later, just followed the suggestion made in the next thread.

    I followed the instructions 2.6.13-19...... did not work however 2.6.13-14 showed some action but ended up in a different command driven menu  called BusyBox v1.13.3
Just the last line after the boot could be of interest
ALERT! /dev/sda2*[1] does not exist. dropping to a shell!


command prompt (initramfs)     ;) what now.............

 Meanwhile we have installed Ubuntu using the windows installer installing the latest version via download at five different laptops all running Vista. All went well until we carried out a complete update. All five have shown the same result. 

One personal remark I mentioned it before I played around  with Linux in 1995 and was able to solve some problems created by the hardware, it seems to me the problems are now the software :D

---

### Post by Paddy Landau on 2010-02-17
Persil, I'm no expert in Grub, so I can't answer your questions about this problem with Wubi.

But, if you are installing Ubuntu on a number of machines, and you are expecting to use Ubuntu indefinitely, then I would suggest that you do not use Wubi.

Why?

Because Wubi is great for experimenting and playing around with Ubuntu. But, it's not advised for long-term use, because it's less efficient; it's susceptible to errors and malware within Windows; it's more likely to suffer fatal file-system errors; and it's much harder to change sizes if you later need to increase the available space.

Here is what I suggest.

Learn how to install Ubuntu natively, i.e. on its own partition. It's a bit more fuss (initially) than installing Wubi, but less fuss thereafter. Also, once you've done it twice, you'll understand the process and find it easy.

You will need to...

[LIST=1]
[*]Uninstall Wubi.
[*]**Make a full backup of all your Windows data!** Step 5, while highly reliable, does occasionally lead to data loss.
[*]Optional (but *strongly recommended*): Back up your entire Windows partition onto an external USB hard drive using [CloneZilla]("http://clonezilla.org/"). In case of a fatal error, this will allow you to restore your entire Windows partition, without having to reinstall Windows (with all the problems that entails!).
[*]Clean up your Windows partition. I recommend using [CCleaner]("http://www.ccleaner.com/") followed by [Auslogics Disk Defrag]("http://www.auslogics.com/en/software/disk-defrag/").
[*]Shrink your Windows partition using Vista's built-in partition manager. (Don't use Ubuntu's GParted, because it occasionally leads to fatal errors with Windows boot partitions.)
[*]Install Ubuntu from the Live CD. If you get at all confused, read the forum for answers (or start a new thread if you don't understand). You will want Ubuntu to use the free space left after you had shrunk your Windows partition.
[/LIST]

---

### Post by audiomick on 2010-02-17
What Paddy said, with the following additions.

I have often read that, particularly on a windows install that has been running for a while, it isn't a bad idea to de-frag a couple of times, (after chucking out all the accumulated rubbish on the drive first, of course).

Having done the shrink on the windows partition, start Windows a couple of times and let it do any file check stuff it wants to do.

When installing Ubuntu, there are good reasons for installing it with /home on a separate partition. That way, if your Ubuntu install spits the dummy and you need to re-install, you can simply re-mount the /home partition and retain all your data and user settings.

Have a bit of a look here:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Paddy Landau on 2010-02-17
> **audiomick said:**
> Having done the shrink on the windows partition, start Windows a couple of times and let it do any file check stuff it wants to do.
Yes, good point.

> **audiomick said:**
> ... there are good reasons for installing it with /home on a separate partition ... you can simply re-mount the /home partition and retain all your data and user settings.
Unless you've used encryption, in which case the current set-up is near-impossible to figure out! I recommend that you don't use Ubuntu's /home encryption until Canonical has improved its usability.

---

### Post by 3rdalbum on 2010-02-17
I suggest you back up your data and install Ubuntu for real, by booting the Ubuntu CD. The error message you posted about /dev/sda2 indicates that the kernel is looking for an Ubuntu installation on a physical hard disk, rather than the one Wubi creates within a file.

Wubi has several inherent limitations that you would bump up against even if you didn't have this problem, so you should remove the Wubi and instead install Ubuntu by booting the CD.

---

### Post by themusicalduck on 2010-02-18
I think your problem is that you're including the footnote in the code..

/boot/vmlinuz-2.6.31-14-generic root=/dev/sda2*[1]

should be 

/boot/vmlinuz-2.6.31-14-generic root=/dev/sda2

because the *[1] just points you to a footnote in the thread post.

Although I agree that installing properly is a much better way than using WUBI.

---

### Post by persil on 2010-02-19
Gentlemen

    thanks for your recommendations. I will follow all by the dot.I have to explain why we have run Wubi on five different computer. I am teaching retired people basic computer and Internet. Some of those people got a little bit more curious and ask about Linux. The reason some are driven by virus and hacker fear away from Windows.I have used Suse, Fedora and Mandrake. All of those are not very easy to handle driver problems etc. This is the reason for using Wubi it was a quick way to get those people onto Ubuntu Linux. Naturally after this small disaster ending up in GRUB and not getting out two people wiped the Ubuntu area and got upset because the  loader stil remained with there computer. I had the pleasure to fix the MBR to get those people back to normal. I agree  a full installation is the right thing to do but because lacking the cd the download was the next best thing. I still stand by waht i said before if Linux is heading for a even wider acceptance, beta versions should not show up in Wubi installations and automatic updates without warnings.It looks to me that even people using Linux for several years don't know to much about the in and outs. Sorry no offense. I will keep you posted.

I will download the ISo image an make a cd/dvd

---

### Post by Paddy Landau on 2010-02-19
> **persil said:**
> I still stand by waht i said before if Linux is heading for a even wider acceptance, beta versions should not show up in Wubi installations and automatic updates without warnings.
I agree.

I think, if you are doing this for other people where you need low risk, that you should stick to the long-term stable (LTS) releases. The next one, due May, is Lucid 10.04.

If I were you, I'd wait until the end of May to give 10.04 a little time to settle in, and install only then.

Good luck.

---

### Post by persil on 2010-02-20
Thank you all

         yes I know now where the real problem is. Partly I have to blame myself because I put too much faith into Linux. After all the comments I have heard from people using Ubuntu and have used it for years I did not expect such problems. In hindsight we all a bit smarter. Meanwhile I have downloaded the ISO file and created my CD. Thanks Paddy for the link about the partition program. I have installed Ubuntu from the CD and will read and study the manuals available. 

   Fred

---

### Post by steveneddy on 2010-02-20
Ah - it not a dual boot - you used Wubi.

Wubi is not a stable way to install Ubuntu, only to try out Ubuntu without any major work partitioning.

Updates frequently break Wubi.

If you need a good way to use Ubuntu without the hassles, use VirtualBox in Windows and install Ubuntu into VB.

---

### Post by Paddy Landau on 2010-02-20
> **persil said:**
> yes I know now where the real problem is...
In my opinion, the real problem lies in the fact that computers are still so primitive. Unlike the technologies of, say, reading or driving a car, you can't "just do it". You have to fiddle and fuss to get them working. Ubuntu is hardly an exception in this regard.

---

### Post by Paddy Landau on 2010-02-20
> **steveneddy said:**
> If you need a good way to use Ubuntu without the hassles, use VirtualBox in Windows and install Ubuntu into VB.
You do need a high-spec computer, though.

---

### Post by HermanAB on 2010-02-20
So, to come back to your WUBI problem:
You probably have to re-install and then you have to disable the automatic screw-ups, a.k.a. automatic updates, otherwise the same thing will happen again.

Note that if you install Ubuntu with a separate /home partition, then you can easily re-install Linux in a few minutes, without losing your data.

---

### Post by persil on 2010-02-22
Well 
 the conversation  continues therefore a bit more. I have partitioned the hard disk, burnt my CD from the ISO image. No problem at all. All is well now, and what is new it still bugs me that I was unable at this stage to fix the problem. I pointed out earlier I had the feeling there was only a small bit of information missing. The information I needed was the Kernel versions. To proof if I am right or wrong I have created the same problem again but had written down the Kernel versions. Well I repeated the wubi setup made complete update and with the right Kernel numbers and Grub after a lot of mistakes and fiddling I was able to get back into the wubi installation.

     Thats it, but I will not recommend to someone to try Wubi.:)

---

### Post by Paddy Landau on 2010-02-22
> **persil said:**
> Thats it, but I will not recommend to someone to try Wubi.
No, Wubi is only to test Ubuntu to find whether you'd like to go further with it. It's definitely not for serious use!

I used Wubi before I made the decision to with Ubuntu. It gave me the peace of mind of knowing that Ubuntu would work on my machine and so was worth the bother of going through the learning curve.

---

