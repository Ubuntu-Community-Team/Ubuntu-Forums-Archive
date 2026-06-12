---
title: "Yet another dual boot question - looking for a yes or no answer"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by thedemonlibrarian on 2010-06-13
Hello, 

I'm getting ready to set up my desktop PC to dual boot Windows XP and Ubuntu 10.04. My machine has two physical hard drives, each of which is partitioned into two logical drives. Windows resides on c:\, and all of the junk I store - photos, iTunes library, etc. - are on d:\. The second physical drive is empty, so I plan to install Ubuntu on f:\ and use g:\ to store things associated with it. I also plan to create a small partition on this drive for swapping. I will be installing from a thumb drive. 

Before I start, though I'm hoping to get a straight yes or no answer to the following question: 

**Is it possible to install Ubuntu AND Grub2 on f:\, and choose which OS to boot to through the F12 option just before Windows starts? **

I've read a lot of forum posts about dual booting, and I still don't really have a definitive answer. I read some old posts that that indicated that when installing 9.04 and earlier, users had the option of choosing where to install Grub - but other posts note differences between Grub and Grub2, raising the question of whether the option to choose where to install Grub2 still exists. 

I'm trying to avoid taking any action that would change the Windows MBR because I've read that this will cause problems if I decide to remove Ubuntu from my system, and that Grub2 can be rendered non-working if Windows updates itself in any way that alters its MBR. 

Can anyone tell me if what I'd like to do is possible?

---

### Post by howefield on 2010-06-13
Yes.

---

### Post by 5BallJuggler on 2010-06-13
Yes. (Probably)

If you install 2 different OS's on two different drives you will be able to boot each of them independantly by modding the bios options. 

also you should be able to select at start up.

I'm pretty sure you can do this with the F12 button.

You just need to change the BIOS to auto boot the one that you will use more often.

Best to wait though, someone who understands BIOS better than me may have a different slant on this.

Hope this helps.

---

### Post by howefield on 2010-06-13
> **5BallJuggler said:**
> Yes. (Probably)

Yes (Definately)


:lolflag:

---

### Post by vandorjw on 2010-06-13
yes - as long as your computer allows you to specify which hard disk to book from.

---

### Post by thedemonlibrarian on 2010-06-13
Wow, thanks for the fast replies! Sounds like I'm ready to give it a try. 

I was pretty sure it should work, because I have the ability to change the boot order in BIOS, or to hit F12 during start up and choose an alternate device to boot from without changing the preference in the BIOS. But some posts I read had me freaked out that Grub2 would install itself on c:\ whether I liked it or not. 

Well, I'm going to back up some of my stuff just in case, and then install. I'll post again afterward to say how it went, so that hopefully the next fellow to come along with the same question will find this and get his answer. 

Thanks again for the quick replies! That was like half a dozen in less than 10 minutes! You don't get that kind of anywhere else. 
:KS

---

### Post by howefield on 2010-06-13
You asked for a one word answer and got it.

However, before you rush off, be warned it will be very easy for you to install grub to the wrong disk negating the reason why you want to do your install this way.

The fact that you are asking the question and also the way you describe your current partition set up makes me think you may run into trouble.

Apologies if I underestimate your talents ;)

---

### Post by wilee-nilee on 2010-06-13
Your contention is correct with a true dual boot which means booting the live cd and installing to the other HD. But you have to point grub at that HD with checking the advanced  button in the final install gui, it will default to the main HD otherwise. Make sure that the external MBR is chosen and it will be something like sdb no partition numbers, Linux doesn't use letters.

I bring this up as your using letters to name partitions so I think you will figure out that the install to the HD of Ubuntu will have no letter and will not be accessible from Windows, if it is ext4. But you can use a share ntfs partition to hold stuff that can be accessed, from either OS.

Also if you run sudo update-grub in the Ubuntu install it will see XP and you can boot XP from there as well. In the end you will probably figure out that installing both OS on the same HD is probably a better option. Loading the bootloaders is very easy in case you decide to remove Ubuntu in this scenario. The 2nd HD would be better for backups really.

---

### Post by wilee-nilee on 2010-06-13
> **howefield said:**
> You asked for a one word answer and got it.

However, before you rush off, be warned it will be very easy for you to install grub to the wrong disk negating the reason why you want to do your install this way.

The fact that you are asking the question and also the way you describe your current partition set up makes me think you may run into trouble.

Apologies if I underestimate your talents ;)

Exactly.;) but hey you started the yes parade.

---

### Post by oldfred on 2010-06-13
You need to be sure to install the grub boot loader to your second drive probably sdb (not sdb1). If often defaults to the one with windows. It is not the end of the world as reinstalling the windows boot loader or grub is relatively easy.

Highlights the advanced button
Dual boot 2 drives
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

Install karmic Screens shown with advanced button
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)
[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)

---

### Post by howefield on 2010-06-13
> **wilee-nilee said:**
> Exactly.;) but hey you started the yes parade.

Only on instruction from the OP :)

---

### Post by wilee-nilee on 2010-06-13
> **howefield said:**
> Only on instruction from the OP :)
Just giving you a hard time.;) You reiterated though that a yes only answer had missing information, and wanting to make sure the OP new what was up.

---

### Post by -kg- on 2010-06-13
Yes, and it would be good to heed howefield's advice.

If you have the "F12" boot option, you can install GRUB (of either variety) to the MBR of the drive of your choice...in this case, sdb.  You do not install it to a partition...you install it into the MBR portion of your primary hard drive.  Then when you want to boot into the non-default OS (probably Ubuntu, in this case), you just press F12 and select the second hard drive.

In this case, you referenced your C: drive...that's a Windows drive assignment used to indicate what in Linux is designated as sda1 (or sda2, if you have a recovery partition). Your "D:" drive is located on the same hard drive, sda.  The MBR is independent of either of these partitions and contains your partition table and the Windows boot segment.

You won't be installing Ubuntu into "F:" and "G:"...those are Windows drive designations, and Windows will not be able to access or read these partitions without special drivers.  You will instead be installing Ubuntu into sdb1 with a mount point as "/" (called the root partition) and have a swap partition as sdb2.  You won't be able to "access" this partition from Ubuntu, as such, just as you aren't able to directly access the "Paging File" in Windows.  It is used by the system in the same way that the Paging file is used by Windows.

The only difference that might occur in these drive designations is if you create other partitions (such as a separate "/home" partition or, as in your intention, a "storage" partition for Ubuntu, though this could easily be a separate "/home" partition), or create an Extended partition to contain Logical partitions in which to install Ubuntu (perfectly acceptable, for Linux).  In that case, the first Logical partition will always be sdb5, and subsequent partitions going up from there (sdb6, sdb7, etc.).

> I've read a lot of forum posts about dual booting, and I still don't really have a definitive answer. I read some old posts that that indicated that when installing 9.04 and earlier, users had the option of choosing where to install Grub - but other posts note differences between Grub and Grub2, raising the question of whether the option to choose where to install Grub2 still exists. 

Yes, it exists.  In the very last screen, where it lists what actions are going to be taken in the installation, there is a button at the bottom right of the screen entitled "Advanced."  Pressing that button will bring up a Window in which you can choose where to install GRUB.

The default is sda, and considering that is where you have the Windows Bootloader in the MBR, you don't want it to install there.  If the drive you're installing Ubuntu to is "sdb", you will want to choose "sdb" in that screen.  ***_DO NOT_*** choose any location that has a number in it, such as "sdb1", "sdb2", etc.!  Choosing any of these will install GRUB in that partition instead of the MBR of the drive, and you won't be able to boot to it.

There's one thing that will be invaluable for you to keep in mind:

*"Linux is not Windows; Windows is not Linux"*

They are two completely different Operating Systems, and though they might "look" like they operate the same, they don't.  Expect a learning curve, stick to it, and using Ubuntu will become easier and easier and easier, until it becomes so easy that you'll wonder how you ever were able to put up with Windows.  That's the way it happened with me, anyway! :p

---

### Post by -kg- on 2010-06-13
:lolflag:

I see there were "a few posts" since I started on the above; all conveying much the same information. :p

Good posts, with good information! [IMG]http://neo.brainformation.com/images/smilies/oldSite/coolthumb.gif[/IMG]

---

### Post by wilee-nilee on 2010-06-13
> **-kg- said:**
> :lolflag:

I see there were "a few posts" since I started on the above; all conveying much the same information. :p

Good posts, with good information! [IMG]http://neo.brainformation.com/images/smilies/oldSite/coolthumb.gif[/IMG]

oldfreds description and links and your very succinct description always help.;)

---

### Post by thedemonlibrarian on 2010-06-13
Hm, more good info. I had read somewhere that the option to install Grub2 somewhere other than the main HDD was in an advanced menu near the end of the installation, but I did not anticipate that the drive designations would be different. So, thank you for pointing out the cliff before I ran off it. 

I probably could have phrased my original post better; I didn't mean to give anyone the impression that I wouldn't appreciate additional detail. As I said earlier, I read a lot of old threads started by folks asking various questions related to dual booting. In a lot of these threads, people replied with advice like, "Why don't you try Wubi?" I'm not suggesting that Wubi isn't useful, but the response is kind of like when I ask my wife where the ice cream went and she tells me there are cookies in the cupboard. I was just trying to stress that I badly wanted to know whether my little plan would work. 

And I admit that having partitions on an empty drive is a little odd. It's left over from my old system, which crashed. I put it into my current system to recover the iTunes library, formatted both partitions, and then never took it back out. So, when I realized what it was going to cost me to put Windows 7 onto two desk tops (mine and my wife's) and a netbook, I thought, "Why not try Linux? 

Screenshots will be a big help. Thanks again to everyone who replied!

---

### Post by -kg- on 2010-06-14
OK. (BTW, I see you're in Champaign, not too far from me! 8) )

I like to point people in the direction of one particularly good set of tutorials, [Dedoimedo's site.]("http://www.dedoimedo.com/")  He has a very good collection of articles and tutorials on his site, and they're always very clear and concise (at least, to me).

His most recent [Ubuntu Installation Guide]("http://www.dedoimedo.com/computers/ubuntu-install.html"), while it is actually for 9.04/9.10, is very much applicable to 10.04.  I don't think you can go wrong with it. And it has screenshots showing the various steps in the process.

In the article, he offers a crash course on partitioning.  The link in my signature block leads to my Community Documentation page on the subject, and is a bit more comprehensive. While not going into absolute technical details, it will nevertheless give you a bit more knowledge in the partitioning process (with screenshots! :p ).  Dedoimedo offers a partitioning article, too.  I haven't checked it out yet, so I can't tell you how comprehensive it is (knowing Dedoimedo, it's good).

Good luck, and as always, if you have any more questions, feel free to ask!

):P

---

### Post by thedemonlibrarian on 2010-07-14
Hello, everyone! 

At long last, I found the time to install Ubuntu 10.04 on my unused hard drive. Thanks to all the advice and tutorials, everything went very smoothly, and I'm happily exploring every day. 

For those who might be considering a dual boot using two hard drives, here's my advice. 

ONE: Read all of the tutorials posted to this thread. You might also want to grab a book about Linux too. I read the first several chapters of *Linux for Dummies* (don't laugh) and gained a better understanding of how Linux differs from Windows. The chapters on prepping a machine for Linux and installing were also very helpful. 

TWO: Know your current set up. You'll want to make sure you're installing Linux on the correct drive, so you don't wipe the Windows drive and whatever data you have there. 

I already knew the larger and newer of my two hard drives was at the top of my boot priority. So, I went into the BIOS and looked at my boot priority. Here I found numbers identifying the two hard disks in my machine. Obviously, the drive where Windows was installed was at the top of the list. 

Also within the BIOS, I looked at standard CMOS features. This will tell you more about your setup. You'll also see those identification numbers again. 

THREE: Before you install Ubuntu, run it from the CD. In addition to getting a first look at the OS, you can also look at how Ubuntu sees your hard drives. In my case I found: 

   My first HD, where windows resides is designated as "/dev/sda"
   The partition where the OS resides is "/dev/sda1"
   The partition I used for storage is "/dev/sda2"
   My second HD, where I intended to install Ubuntu, is designated "/dev/sdb"

The second hard drives also had partitions, but I deleted them when I installed Ubuntu. 

FOUR: Don't install anything on "/dev/sda" or any of its partitions if you intend to keep Windows. 

FIVE: I wanted the OS and my files to be on separate partitions, as they are in Windows. Here's how I partitioned the second hard drive for Ubuntu. 

    I installed Ubuntu at the root directory ("/") and left 20gb of space for it. 
    I created a 2gb swap partition
    I created a "/home" partition, using all the remaining space, for file storage. 

SIX: If, like me, you want to leave the Windows MBR untouched and choose between Windows and Ubuntu by accessing your boot options (that is, hitting F12, if your system suppports it) on start up, install GRUB2 - the Linux boot loader - at "/dev/sdb". 

One last note. If you receive an error message stating: 

"The installer encountered an unrecoverable error. A desktop session will now be run so that you may investigate the problem or try installing again."

You can still install Ubuntu by restarting and pressing any key when you see the Ubuntu splash screen (the one with the keyboard at the bottom), and selecting "try Ubuntu without installing" on the next screen. When the Ubuntu desktop appears, click the "install Ubuntu 10.04 LTS" icon. 

Hope these notes prove helpful for someone in the future. Thanks again to everyone who replied to my OP!

-TDL

---

### Post by YesWeCan on 2010-07-14
Safer still, physically disconnect the Windows disk while you install Ubuntu and grub2. Then reconnect the Windows disk, reboot from the Ubuntu disk and run update-grub to add Windows to the grub menu. You cannot harm your Windows installation if it is disconnected.

---

