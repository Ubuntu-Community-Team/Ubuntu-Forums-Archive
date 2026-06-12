---
title: "Dual-boot with Vista - is it worth it?"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by osbeav on 2010-01-03
Newbie here, so I apologize if I misuse terminology...

I finally took the plunge to move to Linux... As a trial-run, I installed Ubuntu 9.10 to dual-boot with Win XP on my old Dell desktop. Allocated approx 30 GB to the Ubuntu partition. Works great, minus my outdated hardware!

My Question is:
Aside from all the pros for running Linux vs Windows, I would appreciate any suggestions and/or friendly advice for my next dilemma. I've read a few of the stickies and forum posts but hope to summarize my situation here and maybe someone(s) could ease my worries. 

I'm considering installing Ubuntu 9.10 to dual-boot on my 3-year old Dell Inspiron E1505 laptop, but I ran across a few concerns via other forum posts that has me hesitant. I'm wondering if I already have a few things working against me, specifically:

1) Vista Home Premium is installed and I have no recovery discs. From other posts, I have followed how to use Perfect Disk and Vista's Disk Management utility to defrag, consolidate, and shrink the volume size (though I haven't actually shrunk it yet) prior to installing Ubuntu. I'd just like to avoid installing Ubuntu then having to use recovery discs when I don't have them.

2) ATI Radeon X1300 driver is installed. Sounds like the proprietary driver support is gone, but there is an open-source equivalent. If I install Ubuntu 9.10, are there extra steps involved to get this driver working or will it automatically find it for me? I read the following wiki, but couldn't figure it out.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

3) I have ~50GB of free-space, of which I would allocate maybe ~20GB for the Ubuntu install. Is this enough? I plan to dual-boot since I'm (unfortunately) still dependent on a few MS products.

Anyway, just looking for any helpful suggestions/advice for this newbie. I do support the Linux/open-source philosophy and would like to continue this quest.

Much appreciated!

---

### Post by J V on 2010-01-03
Drivers are easy, open source drivers are installed by default, which means out of the box linux supports more hardware than mac and windows put together, always nice :) and the proprietary drivers take 3 clicks to install...

ubuntu can quite easily be run on 8 gigs, but for things like flash videos, I suggest a bit more... 20 gigs is plenty, I ran a wubi install without ever going over 20 gigs...

See my sig for open source alternatives (afaik there is not one microsoft product you will still need, open source alternatives for everything... and then theres wine)

I would suggest twice your ram for swap, 10 gigs for / and whatever else you can spare for /home...

You will be expanding to full install any month now if you've had vista on it for 3 years :)

welcome to ubuntu!

---

### Post by gabo.cr on 2010-01-03
20 GB for Ubuntu should be enough, it all depends if you will be using Ubuntu more or not.
You could make an extra partition to share files between Win and Ubuntu.

---

### Post by running_rabbit07 on 2010-01-03
In your Vista Menu, there should be the option to back p to DVD's That would be your best bet. 

You should be able to shrink the C drive with the Vista tool, but be ready for disappointment when it says it can only give you 10 gigs of free space. Before installing Windows 7 on my wife's machine I defragged, then tried to shrink the volume and it was only going to give me a little over 8 gigs, while there was more 100 gigs in the C drive that was not being used. I ended up copying all of her files to disks and reformatting the hard drive, then making a smaller NTFS for Windows 7 and left a nice sized area to install either Zenix or Ubuntu, we haven't decided yet.

---

### Post by theozzlives on 2010-01-03
Vista period is a bad idea. I'd suggest 7 or, if you want to go backward, XP. In all reality, I've seen succesful Vista dual boots. Just resize IN VISTA and you should be okay.

---

### Post by Mark Phelps on 2010-01-03
> **running_rabbit07 said:**
> In your Vista Menu, there should be the option to back p to DVD's That would be your best bet. 

Not really ... Vista Home Premium does not provide the full image backup capability of Business or Ultimate.  All you can do is back up some files.  So, if the OS gets corrupted during the shrink operation, you will not be able to restore a working image from THAT backup.
> You should be able to shrink the C drive with the Vista tool, but be ready for disappointment when it says it can only ive you 10 gigs of free space...
Here's a link to some things you can do to help get more shrinkage using the Vista tool:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

You're right about the Radeon drivers -- you're stuck with the open source versions.  ATI's not making updates to the Linux drivers.

If you don't have a Vista install DVD, then go to the NeoSmart Technology forums, download the Vista repair CD ISO and burn it to disk.  That way, you will have a repair CD should you need to boot back into Vista to do boot repair.

---

### Post by seenthelite on 2010-01-03
I have the same Dell Laptop Dual booting with Vista and I used  Vista to shrink the existing partition which left 21 GB for Ubuntu and that is fine for me. On my Dell Ubuntu works perfectly out of the box with 9.10 other than the wireless. I have Intel (R) Pro/wireless 3945 Dual Band 802.11a/g 54 Mbps wireless mini card. Network Manager did not work at all for me but WICD works perfectly for this card if you have the same problem.

---

### Post by stalkier on 2010-01-03
> **osbeav said:**
> Newbie here, so I apologize if I misuse terminology...

I finally took the plunge to move to Linux... As a trial-run, I installed Ubuntu 9.10 to dual-boot with Win XP on my old Dell desktop. Allocated approx 30 GB to the Ubuntu partition. Works great, minus my outdated hardware!

My Question is:
Aside from all the pros for running Linux vs Windows, I would appreciate any suggestions and/or friendly advice for my next dilemma. I've read a few of the stickies and forum posts but hope to summarize my situation here and maybe someone(s) could ease my worries. 

I'm considering installing Ubuntu 9.10 to dual-boot on my 3-year old Dell Inspiron E1505 laptop, but I ran across a few concerns via other forum posts that has me hesitant. I'm wondering if I already have a few things working against me, specifically:

1) Vista Home Premium is installed and I have no recovery discs. From other posts, I have followed how to use Perfect Disk and Vista's Disk Management utility to defrag, consolidate, and shrink the volume size (though I haven't actually shrunk it yet) prior to installing Ubuntu. I'd just like to avoid installing Ubuntu then having to use recovery discs when I don't have them.

2) ATI Radeon X1300 driver is installed. Sounds like the proprietary driver support is gone, but there is an open-source equivalent. If I install Ubuntu 9.10, are there extra steps involved to get this driver working or will it automatically find it for me? I read the following wiki, but couldn't figure it out.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

3) I have ~50GB of free-space, of which I would allocate maybe ~20GB for the Ubuntu install. Is this enough? I plan to dual-boot since I'm (unfortunately) still dependent on a few MS products.

Anyway, just looking for any helpful suggestions/advice for this newbie. I do support the Linux/open-source philosophy and would like to continue this quest.

Much appreciated!

My experience with a dual boot is that the learning is much longer. I would suggest just jumping straight in to Ubuntu. It can be intimidating and seem like it is a bad idea but believe me it is MUCH faster for you to learn. I dual booted with XP/Ubuntu and Vista/Ubuntu both with success. I have been Windows free on ALL my systems now for almost a year. I have had NO trouble with any system since then. WINE is great for running games and apps that you might need or want. For me I had to downgrade a Win app (Dreamweaver) so that it would run in WINE. What apps are you wanting to run? Most likely you will be able to get them to run in linux. It just might take a bit of tweaking which we will be happy to help you with.

I would suggest using Ubuntu 9.10 and make sure the laptop is hardwired via Cat5 to acquire additional updates upon installation.

---

### Post by osbeav on 2010-01-03
Hi everyone. Thanks for the welcome and quick replies.

Mark-> I should give you credit for the Vista shrinking... I learned that from one of your previous posts. Thanks! (I gave it a shot last night with Perfect Disk, and went from 900 MB free space to ~50 GB!)

Follow-up question then: if I were to shrink the existing Vista partition then run the Ubuntu installer, what do I have to do to get Ubuntu to "see" the newly-free space? Does it do it automatically? Do I create a new volume? I guess I'm not connecting together the steps to (1) shrink the space to (2) installing Ubuntu. Seems like this would apply to anyone wanting to dual-boot with Vista and trying to install any Linux distro.

I've backed up my files to an external WD hard drive. I haven't imaged the laptop yet. In short, can I part with Vista? More than likely yes. Wasn't a fan of it from the beginning. It won't be pretty, but I could re-install and run the MS applications from other (less "powerful") computers I have. If something were to go wrong during Ubuntu install is it worth the pain to recover or just wipe it clean and install Ubuntu on the entire drive. As J V mentioned, I could possibly go Ubuntu completely! If I misread your reply, what, if anything, would it take to install the ATI open-source driver?

seenthelite-> great info! Not sure if I'm reading my laptop info correctly, under Network Adapters it lists a "Dell Wireless 1390 WLAN Mini-Card". I'm such a newbie... what's WICD?

Again, I really appreciate everyone's help. It's communities like this that embrace us newbies which is all the more encouraging to stick with Linux!

Thanks in advance for the suggestions.

---

### Post by M1ke on 2010-01-04
Hi from a fellow Ubuntu newbie! A good piece of advice I found somewhere here on shrinking was to make sure you run the "disk cleanup" utility within Windows first, and defragment the drive. Once you've done that and shrunk the partition, reboot Windows before installing Ubuntu so that everything within your newly-shrunk partition is properly set out. Makes sense I guess.
 
If partition shrinking in Vista is anything like Windows 7, it's surprisingly straightforward. To answer your question about "seeing" the newly-freed up space, when I did it the Ubuntu installer recognised the unallocated drive space with no extra fiddling.

---

### Post by adelphos on 2010-01-04
If you're afraid about the partitioning process (since there is a risk of data loss on the Windows partition), make sure that partitioning is actually necessary. Have you looked at [Wubi]("http://wubi-installer.org/")? I had success using it on Windows Vista... For cases like this, I think it might be better to use that method, since you can still boot into Ubuntu, but you don't have to mess with partition sizing.

---

### Post by ST3ALTHPSYCH0 on 2010-01-04
As far as Ubuntu "seeing" your free space, There's an option in step 4 (I believe. It's the partitioning step) to install Ubuntu side by side. That's the one you'll want. Well ideally you'd choose to manually specify, it's a little more involved, but we'd be happy to help. Then you can create a system partition and a separate home partition (which is where your files will be saved).

EDIT:
As far as WUBI goes, I wouldn't recommend it right now, because there's a bug with the 9.10 WUBI where it tries to install GRUB when it updates and causes the system not to boot.

---

### Post by landy rover on 2010-01-04
Hi 

My suggestion is keep to vista because it is More user friendly than ubuntu...
and all those driver cd's for windows that can be installed easily.:lolflag:
I dual boot vista and ubuntu 8.10 bit old but still.and my main purpose for windows is gaming because my oponion is ati drivers on windows is just that bit better than resticted or properiatry drivers.
but UBUNTU is excellent because no paying,open source and better, faster,safer browsing on the NET.NO hackers no spyware no viruses etc

but there is loads of drivers pre installed on ubuntu that you don't need to install like windows.And if u get stuck with a driver just download it!!!

2)coming back to installation and partioning 8gb is fine to run ubuntu. i used to use 8gb allocation on my 40gb hard drive LOL

but this is only my suggestions vista for gaming and ubuntu for fooling around

regards

landy rovers

---

### Post by marco123 on 2010-01-04
1. When you get to the partitioning stage of the Ubuntu installation there is an option to "Use largest continuous free space" which will install Ubuntu to the free space you just created in the Vista disk management tool.

2. The open source drivers require nothing.  They are up and running as soon as you boot into the freshly installed installation. 

Also to setup Flash, Java and all the codecs you may want to run:

> sudo apt-get install ubuntu-restricted-extras

Commands are run in Applications>Accessories>Terminal in the Main Menu. (Top Left.)

Enjoy Ubuntu.:)

---

### Post by osbeav on 2010-01-05
Hi again everyone and thanks for the great suggestions -- my worries to take the leap-of-faith to Ubuntu are fading!

The more posts and associated links I read, I'm learning others like to create a separate partition for /home. In my original post for this thread, I mentioned I did a trial-run installation dual-boot on my old Dell desktop running XP with success. However, at that time, I didn't know about the /home partition suggestion but if I were to install Ubuntu for dual-booting on my Dell laptop, I'd like to pursue it.

Curious... Can I go backwards with my Dell desktop trial-run, i.e., re-install Ubuntu but this time add this /home partition? I've spent a couple of hours tonight looking at similar threads, and most just suggest to "create a /home partition" though I could use a little more guidance. Specifically at the Partition step of the install, I assume I create an extra partition to use for /home. I'm not connecting the step from completing installation to how Ubuntu recognizes this extra partition as /home to write user data there. I imagine there are numerous options to do this -- it's just practice on this old desktop of mine to get it correct for my laptop.

Please forgive the naive-ness of my newbie questions, maybe it's worth a good chuckle or two; I'm learning from my mistakes but I still think Linux is the way to go!

Thanks again!

---

### Post by running_rabbit07 on 2010-01-05
Yes, you can reinstall, but you will loose the programs you installed. If you know what you've installed, it'll be easy to get the programs back up and running after the reinstall.

Use about 10 gigs for the / partition, 2-3 gigs for swap, and the rest for home. You may want to create a Logical partition first to put them in. Windows doesn't support more than 4 primary partitions.

---

### Post by n97ua on 2010-01-05
I was on XP, and when Vista arrived I hated it.  I was always a DOS / Unix guy anyway.  I ran XP because work required me to.  This is no longer the case.  I guess if you like to live dangerously then trying to mess with anything from Misrosoft would fit the bill as far as my experience goes.

Dual boot is fine when systems play nice...  Like multiple Linux versions for instance.  As soon as you leave industrial OS's and go into playing with Microsoft software you are in effect mixing toys with real operating systems, and anything can happen.

It took me about three weeks of hammering Ubuntu before I was ready to give up my XP.   But I did it.  You can too.

I think the problem is that we are to use to things as being the same.  Change comes hard.  However !  I can say I would never ever load a Microsoft product again in my life.

I am so happy I left Microsoft, and found Ubuntu to be the most fantastic thing in the world.  In fact you are getting a taste of it here.  People from all over are helping you for free.  This is by far the best aspect of Ubuntu.

If I have a problem, I ask it and its solved.

Still - Its not an easy thing for most people to undergo.
Take the plunge.  Save your files to a jump drive.  
Buy a new hard drive and format it 100% Ubuntu, then unplug the one drive and plug the other one in.

you will always keep the original Vista in case you really need to.

You will soon find little need for it.

This new version is the best ever.  You need to force the change.  Its hard at first.  Nothing is where it use to be...  Then one day it hits you...

You are now FREE !

---

### Post by Sef on 2010-01-05
> 1) Vista Home Premium is installed and I have no recovery discs. From other posts, I have followed how to use Perfect Disk and Vista's Disk Management utility to defrag, consolidate, and shrink the volume size (though I haven't actually shrunk it yet) prior to installing Ubuntu. I'd just like to avoid installing Ubuntu then having to use recovery discs when I don't have them.

Read [GParted FAQ #9]("http://gparted.sourceforge.net/faq.php").  There is a link to the problem, and a link to a recovery disk.

---

### Post by la3875 on 2010-01-05
> **osbeav said:**
>  However, at that time, I didn't know about the /home partition suggestion but if I were to install Ubuntu for dual-booting on my Dell laptop, I'd like to pursue it.



I still consider myself a noob after playing with (and dual booting) Ubuntu since 5.10! A couple of great resources in addition to the forums that I always recommend are as follows:

[http://www.psychocats.net/](http://www.psychocats.net/)
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

Welcome and come on in - the water is fine!!!

---

### Post by ST3ALTHPSYCH0 on 2010-01-06
I would recommend that you do your partitioning in Gparted on the live CD and then go through the install process and just choose the partitions you've already created. This isn't strictly necessary, and most of us have probably partitioned from the installer's partitioning tool at one time or another, but Gparted gives you a nice graphical environment.

---

