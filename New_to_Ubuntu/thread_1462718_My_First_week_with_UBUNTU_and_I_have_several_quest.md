---
title: "My First week with UBUNTU and I have several questions"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by xgtyca on 2010-04-26
Dear All, 
Thank for this great effort in this forums. I am using ubuntu for a week now and I have few questions
1- I am using 9.1 version and the guide available in this forum is for earlier releases and I am having a problem that many things are different. How I can find a guide for release 9.1

2- When I try to add any software from ubuntu software center, I select the software from a list then it is showing to me the following reply (Not available in the current data) why this happening and how I can add or remove any software.

3- when I start the computer it is showing me a black screen and asking me select ubuntu or windows, and there are other options. What are these options and how can I modify this screen to look more beautiful

4- My last question is about the open source philosophy. Is it fare to wast some body's effort? I mean when some body or company spending a lot of time and money developing a program, how they will benefit if it will be free and open source?:confused::confused::confused:

Thanks for every body for their great effort in this amazing forum:popcorn:

---

### Post by lisati on 2010-04-26
Have a look here for recent documentation: [https://help.ubuntu.com/9.10/index.html](https://help.ubuntu.com/9.10/index.html)
By the way, it's 9.1**0** - the numbering scheme for Ubuntu releases is based on the year and the month, usually x.04 (April) and x.10 (October)

---

### Post by Drenriza on 2010-04-26
> **xgtyca said:**
> 
 
3- when I start the computer it is showing me a black screen and asking me select ubuntu or windows, and there are other options. What are these options and how can I modify this screen to look more beautiful
 
4- My last question is about the open source philosophy. Is it fare to wast some body's effort? I mean when some body or company spending a lot of time and money developing a program, how they will benefit if it will be free and open source?:confused::confused::confused:
 
Thanks for every body for their great effort in this amazing forum:popcorn:
#3 This is where you can sellect, which kernel to boot-up-on. Or if you have more then 1 OS installed. You can sellect wich one you want to boot-up-on here. You cannot change this screen to a more "beatiful" screen.
 
But you can tell your linux filesystem to directly start up on a spefific kernel, not showing you the black sellection screen.
(adding how later)
 
#4 Support contracts, courses fee (to lern how to use a program, if its extensive), x-tra goods. (clothes, t-shirts, mouse-pads, and that sourt of stuff), donations.

---

### Post by xgtyca on 2010-04-26
> **lisati said:**
> Have a look here for recent documentation: [https://help.ubuntu.com/9.10/index.html](https://help.ubuntu.com/9.10/index.html)
By the way, it's 9.1**0** - the numbering scheme for Ubuntu releases is based on the year and the month, usually x.04 (April) and x.10 (October)



Thank for your quick reply, but that's exactly what I did and still having the problem
Even when I use the other way mentioned in the help teps. It is showing only the installed softwares and I cannot find any new software to mark it for installation.

thank again

---

### Post by 3rdalbum on 2010-04-26
> **xgtyca said:**
> 
1- I am using 9.1 version and the guide available in this forum is for earlier releases and I am having a problem that many things are different. How I can find a guide for release 9.1

Generally I do a Google search for what I want to do, plus the words "Ubuntu 9.10" or "Karmic" (which is the codename for Ubuntu 9.10). For instance: "Install nvidia driver ubuntu 9.10".

> 2- When I try to add any software from ubuntu software center, I select the software from a list then it is showing to me the following reply (Not available in the current data) why this happening and how I can add or remove any software.

Check that you have the first four checkboxes ticked in the System > Administration > Software Sources program. If you do, then go to System > Administration > Synaptic Package Manager and hit the Reload button.

> 3- when I start the computer it is showing me a black screen and asking me select ubuntu or windows, and there are other options. What are these options and how can I modify this screen to look more beautiful

The other options are probably Memtest86+ and your Ubuntu recovery mode. Memtest is a memory test program; if you start getting unexplained freezes then try running Memtest overnight. The Ubuntu recovery mode sometimes lets you into your system after you break it (depends exactly how you've broken it, but it's useful anyway).

You might also have another Windows option that corresponds to the recovery partition on your hard disk (it's usually identified as an earlier version of Windows). Don't select this unless you want to erase your hard disk back to how it was when you bought the computer.

> 4- My last question is about the open source philosophy. Is it fare to wast some body's effort? I mean when some body or company spending a lot of time and money developing a program, how they will benefit if it will be free and open source?:confused::confused::confused:

Often, people will develop software to "scratch an itch" - they want a particular program, and it doesn't exist, so they write it. They open-source it because other people can benefit from it as well. It's not a wasted effort, because everybody benefits from open-source software, and writing more of it is a good way to give back to the community.

Some companies develop software and then open-source it, or sponsor an open-source project like Canonical does with Ubuntu. For some companies, writing open-source software is indeed a case of "we need a program to our specifications" so they write it, and then when they open-source it the community starts contributing to the program as well; fixing bugs and adding features.

A lot of companies that sponsor an open-source project do so for profit. For instance, Canonical provides paid support to businesses and individuals who want to use Ubuntu and want to be able to contact someone for assistance; this is especially important in business as any downtime costs the business money.

Canonical also sells cloud-based storage (Ubuntu One), music (Ubuntu One Music Store) and merchandise (hats, t-shirts, mugs etc with the Ubuntu logo on them). One of Canonical's first contracts was to customize Ubuntu for a particular client who had a specific set of needs.

And finally, you can release a piece of software as open-source to create interest and get people using the software; but have supporting products as closed-source and paid-for. For instance, Ubuntu is open-source; but Canonical's Landscape software which helps you administer a large number of Ubuntu machines is paid-for software.

I hope this helps! And welcome to Ubuntu.

---

### Post by Drenriza on 2010-04-26
Try these
 
[http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)
[https://help.ubuntu.com/9.10/serverguide/C/index.html](https://help.ubuntu.com/9.10/serverguide/C/index.html)
[http://www.linbrary.com/ubuntu/910/ebooks/Ubuntu_910_Packaging_Guide.pdf](http://www.linbrary.com/ubuntu/910/ebooks/Ubuntu_910_Packaging_Guide.pdf)

---

### Post by Penguin Guy on 2010-04-26
#2: Your package database appears to have somehow came out of sync. Try running the command [FONT="Courier New"]sudo apt-get update[/FONT] in [the terminal]("http://www.psychocats.net/ubuntu/terminal").

#3: You have safe modes, previous versions, and memory tests. To make it look more beautiful, I'm afraid you'll have to learn a lot more about Linux.

#4: People do not benefit from releasing something as open source, they just do it to be nice.

---

### Post by Drenriza on 2010-04-26
> **Penguin Guy said:**
> 
#4: People do not benefit from releasing something as open source, they just do it to be nice.

 
 
Linux is not 100% open-source. But it is to some extend open-source. And Canonical, earn money of it. So it arnt 100% just to be nice. But as i sayd in #3
 
> #4 Support contracts, courses fee (to lern how to use a program, if its extensive), x-tra goods. (clothes, t-shirts, mouse-pads, and that sourt of stuff), donations.

---

### Post by dsnettleton on 2010-04-26
I haven't personally had the trouble you have had with the Ubuntu software center, and I'm not sure about the update guide, but I can at least answer your third and fourth questions.

> 3- when I start the computer it is showing me a black screen and asking me select ubuntu or windows, and there are other options. What are these options and how can I modify this screen to look more beautiful

The black screen you see is a program called GRUB. It's a boot-loader, which means it's built to do exactly what you've observed; it loads partitions, or operating system installations, based on your preferences. GRUB can be easily configured with a program called "Startup Manager." You can locate, download, and install this program in several ways. Since you are experiencing problems with Ubuntu Software Center, I recommend a program called Synaptic, which is another (though somewhat less browse-able) graphical user interface for installing software. You can find it in the top menu bar under System->Administration->Synaptic Package Manager. Click it and enter your administrative password. If this is your first time using this program, go ahead and read the notification box, then close it. There is a box in the toolbar at the top labeled "Quick Search." Type into it: startupmanager without any spaces. This should narrow your options to one item. Click the checkbox next to that item and select "Mark for installation." Click the Mark button in the notification window that pops up, then click the Apply button in the top toolbar. Synaptic will give you an overview of any programs and prerequisites or dependencies for those programs that you are about to install. Click the Apply button to begin the installation.
Once the installation has completed, you can find your new program under System->Administration->StartUp-Manager. Notice the menu options are listed alphabetically, so it should be easy to find; it has a picture of a wrench next to it. When you open the startup manager, it will take some time to look at your current GRUB configuration, then allow you to edit it. You will be able to decide your default operating system and how long of a countdown you want before that OS boots; I think ten seconds is way too long, and I've shortened mine to three. But I almost always boot into the same operating system, so it really depends a bit more on what you're comfortable with. Other options are also available, and the manager auto-detects what you're able to modify.

To answer your original question, the other options available to you are most likely CPU memory tests and other kernels. The linux kernel is actually what makes an operating system Linux, and all else is variable according to different distributions. But the kernel is often adjusted and updated, either to support new hardware, to remove bugs, or to improve performance. When you upgrade your kernel (which Ubuntu does through its automated update manager), GRUB keeps the old kernels so that you can still boot into them, in case something goes wrong; most likely you won't notice a difference from one kernel to the next as the changes are mostly "under the hood," so to speak.

So that was a lot of typing, but I hoped it helped and didn't bore you too much.

As for your final question:
> 4- My last question is about the open source philosophy. Is it fare to wast some body's effort? I mean when some body or company spending a lot of time and money developing a program, how they will benefit if it will be free and open source?

The open source philosophy is that nobody's effort is actually wasted. A lot of talented people produce a lot of high-quality software, simply out of the passion for doing so. Almost everyone who contributes to open source has a passion for their project. Say I really wanted some database software, but didn't want to pay two hundred dollars to buy it. If I'm a talented programmer, I might just decide to make my own. That way I can be sure that it will do what I need it to anyways; I'd hate to spend a lot of money on software that doesn't suit my needs. But it can be time-consuming to write a program by myself, from start to finish, so I'd probably want to get together with other programmers who also wanted database software. Together we'd build the software, use it, and continue to improve upon it, and it wouldn't cost us anything but time. Open source programmers almost always design and build software that they actually plan on using. This can be a double-edged sword sometimes, as you'll probably notice. While it usually means that the software is as complete and convenient to use as the programmers can make it, it also means that it's sometimes a little time-consuming for people who didn't actually work on building the software to learn how to use it. This isn't a gap in the design all the time; sometimes it's just in the documentation. But that's why we have forums and IRC channels. Which leads into the broader point of open source philosophy. We are a community. Not just users of open source, but humanity in general. I'm not trying to sound like a hippie or anything, but the point is that for an open source programmer, the benefit is in having other people use something that you've created, and having them help you to improve upon it. Not all compensation is monetary, and the open source philosophy is not one that believes in individual corporations owning ideas or setting standards that the rest of us have to follow. In short, open source is about freedom.  I shouldn't have to use Windows just because I have a PC. I've used Windows most of my life. I've used Mac. I like it. But I prefer Ubuntu. Some people take the philosophy to the extreme anti-corporate level and only use open source software. But for me, it's merely about having a choice; find what's comfortable for you and stick with it.
And lest you feel bad for open source developers, many of them do manage to make money, including Canonical, the company that distributes Ubuntu. Usually they do this by offering paid support services to corporations that use their distributions; Linux is just about the standard for servers. Canonical, however, may have found another option; Ubuntu 10.04, which releases Wed. April 29th, will have the Ubuntu One music store built in to the Rhythmbox media player. I'm not sure about the exact specifics, but I think that if you use that service to purchase and download MP3's, you'll also be making a monetary contribution to the company that makes the software you know and love. I hope so anyways.

Sorry for writing a novel, and I hope I was able to answer your questions.
--D. Scott Nettleton

---

### Post by Scunnered on 2010-04-26
Penguin Guy seems to have hit things on the head. If you follow his advice that will open up all the software available to you.

I would also suggest that you install the restricted extras via System > Administration > Synaptic and the multimedia codecs from medibuntu [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu).  Having done this it will get you moving along the way with Karmic.

Hope this assists

---

### Post by boxcorner on 2010-04-26
> **xgtyca said:**
>  ... philosophy ... free ... 
Freedom of choice, like democracy.

---

### Post by xgtyca on 2010-04-28
[SIZE=5][COLOR=Magenta]I would like to thank every body for all their contributions which were very helpful and usefull. Your replies solved my problems and answered my questions.:KS:KS:KS:KS:KS
Just one note that the Grub screen in Mandriva looks very beautiful. It there any way to improve the beauty of the one in Ubuntu in easy way
P.S. I still dont know how to use terminal

Thank again for all of you):P):P):P
[/COLOR][/SIZE]

---

