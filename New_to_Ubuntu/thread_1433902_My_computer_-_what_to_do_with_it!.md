---
title: "My computer - what to do with it!"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by tazz4vr on 2010-03-19
I think I need to modify my puter.  I need her running faster with less freezing.

That would be the ultimate, however, as she is running considerably slower and freezing on me frequently, is it possible that there are programs installed that I don't need?  How would I know if I need more memory and/or what stuff to remove?

I need help!  I don't want to do a complete over-haul if it's not needed.  I have looked for the information per my puter support site, all I found where additional questions from the information I was reading.

Does anyone have a good support site for eMachines that they could point me too?

---

### Post by halitech on 2010-03-19
what kind of computer? how much ram do you have now? what is the procesor speed? what OS are you running? We need more details in order to help you out.

---

### Post by tom.swartz07 on 2010-03-19
If its an older machine, it might be wise to switch to a lighter desktop manager. Xubuntu (and in about a month, Lubuntu) are extremely light-weight programs that wont tax your system as much as straight on Gnome Ubuntu.

Once we get some more info about your system, we could make more specific suggestions though.

---

### Post by ayenack on 2010-03-19
+1 to the above.

You need to tell us a bit more about you set up.

Strange for it to freeze have you got more than one USB devices (wireless card, HD) connected? If so try taking them out and see if this helps with the freezing. Also NVIDIA Graphic Cards can cause freeze ups as well when running the propriety drivers.

If it's just running slooooow change to a Xubuntu or another less resource hungry distro.

---

### Post by NightwishFan on 2010-03-19
Post specs if you will. I would say Ubuntu 32-bit should run on nearly any machine. My advice would be to pick which desktop you like. Gnome, KDE, XFCE anything. Download the Ubuntu alternate installer and pick the option to install a command line only system. Then install whatever packages you want. Such as:

gnome-core (installs minimal gnome, add what you need)
xfce4 (xfce4 desktop, no gnome services)
kde-miminal (kde minimal desktop, add what you need)

That way you have the core ubuntu os fully installed, and a light GUI. Your choice of any of the above. Even perhaps install somethng like fluxbox or icewm.

---

### Post by Easy Limits on 2010-03-19
eMachines aren't known for their top notch hardware inside the computer.  They are known for being a cheap computer with cheap parts.  This could be very well part of the reason why you are having issues now.  Just my experience.

---

### Post by tazz4vr on 2010-03-19
> **halitech said:**
> what kind of computer? how much ram do you have now? what is the procesor speed? what OS are you running? We need more details in order to help you out.

I apologize for not including the important info with original post.

Computer - eMachine Desktop

Ram, processor speed - not a clue, but will get the info.

Os - Windows Vista (ughhhhh, I know, I know!)

At the time of purchase, I was in immediate need for a computer.  Replacing it, or lack thereof is purely on my part, laziness and not overflowing in the finance department just yet!

---

### Post by lyall on 2010-03-19
install **sysinfo** if you have not
it is in Synaptic Package Manager

if you have it already it is under
Application > System Tools > Sysinfo

System will tell you the Release you have and the Gnome
CPU  look at Model name
Memory it will tell you your total memory
Storage will show you how among Device (drives you have)

this will get you started on how to find out what your system is

good luck and have fun learning

---

### Post by tazz4vr on 2010-03-19
Okay, first off, NO laughing at me if I got a totally messed up computer!  

Here are the spec's per system stuff.

Model - EL1200-07w
Processor - AMD Athlon Processor 2650e 1.60 GHz
Memory (RAM) - 2.00 GB
System type - 32-bit Operating System

---

### Post by tom.swartz07 on 2010-03-19
> **tazz4vr said:**
> Okay, first off, NO laughing at me if I got a totally messed up computer!  

Here are the spec's per system stuff.

Model - EL1200-07w
Processor - AMD Athlon Processor 2650e 1.60 GHz
Memory (RAM) - 2.00 GB
System type - 32-bit Operating System

Actually, thats not too bad. The processor is a bit slow, but other than that, its fairly good.


Because of your slightly 'simple' CPU, I would go back to my suggestion that you use a lighter Desktop manager. Either Xubuntu or Lubuntu would be best. Try installing those and you should be set! 

Dont forget to back up your stuff!

---

### Post by NightwishFan on 2010-03-20
From my experience the processor is rarely the bottleneck, it should run fine.

---

### Post by uRock on 2010-03-20
You say it has Vista, you will be happier with the speed of any flavor of Ubuntu you want. My Netbook has a dual core 1.6GHz and it is really fast compared to what I expected when I bought it. I think you will be really happy when you get Ubuntu running on there.:popcorn:

---

### Post by cascade9 on 2010-03-20
> **tom.swartz07 said:**
> If its an older machine, it might be wise to switch to a lighter desktop manager. Xubuntu (and in about a month, Lubuntu) are extremely light-weight programs that wont tax your system as much as straight on Gnome Ubuntu.

I cant speak for lubuntu, but xubuntu is just as 'heavy' as ubuntu. Which is a pity. Dont install vanillia xubuntu, or xubuntu-desktop if you want a light system. 

If you want to get a light version of Xfce on ubnutu, use the alternate install disc, then install the xorg + xfce4 packges (and gdm or xdm if you dont want to do the 'startx' from a command line every time you start).

---

### Post by -kg- on 2010-03-20
There's something else I would be interested in:

What size of hard drive do you have installed and, more importantly, how much space do you have for your Ubuntu partitions?  Did you install Ubuntu in its own partitions, or did you install using WUBI (installing Linux under Windows)?

Everyone here knows (or should know) how difficult it is to shrink a Vista partition and not not render it unbootable.  The Vista partition does not like to shrink very much, even using it's own partitioning tool.

While your processor is a lower end processor, it doesn't seem to be *that* bad, and you have more than enough RAM, even if part of it is used for video processing.  Bottom line...if the machine runs Vista decently, it *surely* should run Ubuntu with no problems at all.  My desktop, while it does have a high end (at the time I built it) AMD 64 3200+ processor and has a dedicated video card, only has 1 GB RAM, and it runs great under Ubuntu.

I just don't think that it's your computer specs that are the problem.  There have been other computers with much lower specs than yours that are running Ubuntu, and so should yours, IMHO.  It might just be a case of needing a larger hard drive and/or installing Ubuntu in its own partitions, if you used WUBI.

---

### Post by egalvan on 2010-03-20
> **-kg- said:**
> 
While your processor is a lower end processor, it doesn't seem to be *that* bad, you have more than enough RAM, even if part of it is used for video processing. My desktop, it does have a high end AMD 64 3200+ processor and has a dedicated video card, only has 1 GB RAM, and it runs great under Ubuntu.

I just don't think that it's your computer specs that are the problem.  There have been other computers with much lower specs than yours that are running Ubuntu, and so should yours, IMHO.  It might just be a case of needing a larger hard drive and/or installing Ubuntu in its own partitions, if you used WUBI.

Absolutely +1 for the specs being OK, as a few others have stated.
I have also used CPU's in the 1.6GHz range with good results...
you have a goodly amount o RAM, which makes a world of difference.

I would recommend running 'memtest' at least overnite to see if you have any RAM "issues".
It should show up as an option on the GRUB boot menu.
Please, "MS runs great" is *not* a valid test for malfunctioning hardware.
Run 'memtest' to be sure.

Also, since it's an "aged" machine, it may want a good cleaning...
open it up and make sure any dust-bunnies are evicted...

I strongly believe there are other issues at work,
and not "insufficient CPU or such"

---

### Post by albert s on 2010-03-20
my wifes laptop (DELL inspiron about 6years old) has a 1.6G cpu,(single core celeron)
512ram, and 60G hdd and it runs standard Ubuntu like a rocket ship compared to the XP it replaced.
so I reckon your specs are more than up to the job.

---

### Post by uRock on 2010-03-20
> **egalvan said:**
> Absolutely +1 for the specs being OK, as a few others have stated.
I have also used CPU's in the 1.6GHz range with good results...
you have a goodly amount o RAM, which makes a world of difference.

I would recommend running 'memtest' at least overnite to see if you have any RAM "issues".
It should show up as an option on the GRUB boot menu.
Please, "MS runs great" is *not* a valid test for malfunctioning hardware.
Run 'memtest' to be sure.

Also, since it's an "aged" machine, it may want a good cleaning...
open it up and make sure any dust-bunnies are evicted...

I strongly believe there are other issues at work,
and not "insufficient CPU or such"

Yeah, the problem is Windows. The OP said his OS on this systme is Vista, no mention of installing Ubuntu, yet.

---

### Post by tazz4vr on 2010-03-20
> **iRock said:**
> Yeah, the problem is Windows. The OP said his OS on this systme is Vista, no mention of installing Ubuntu, yet.

I'm with iRock on this one.  I have not yet installed Ubuntu, it is still under Windows.  Heck, I can barely handle one OS, I fear that once I install another type I am not techie enough to work with it, but it is something that I truly have an interest in.

Sooooooo, recommendations welcomed here.  Computer genius I am not.  What would be a good version of ubuntu for me to try out?  I already backed up the puter.  Is it better to do a download install or get a cd and install from that?  Upon an install of ubuntu, does it completely remove the current OS?  How do I put it, the new install into a different partition?  Is my computer capable of even doing this?  Oh my goodness... questions, questions, but really want to try this!

---

### Post by uRock on 2010-03-20
> **tazz4vr said:**
> I'm with iRock on this one.  I have not yet installed Ubuntu, it is still under Windows.  Heck, I can barely handle one OS, I fear that once I install another type I am not techie enough to work with it, but it is something that I truly have an interest in.

Sooooooo, recommendations welcomed here.  Computer genius I am not.  What would be a good version of ubuntu for me to try out?  I already backed up the puter.  Is it better to do a download install or get a cd and install from that?  Upon an install of ubuntu, does it completely remove the current OS?  How do I put it, the new install into a different partition?  Is my computer capable of even doing this?  Oh my goodness... questions, questions, but really want to try this!

Well, if your hard drive has enough space you could dual boot.

I would recommend using regular Ubuntu. You can download it, then burn to disk and install from there.

If you prefer to keep Windows and install Ubuntu in a separate partition, let us know and we can help you set up your partitions.

I would first recommend downloading and burning the LiveCD, which is the desktop version, and booting the disk in the first option which makes no changes to your system. This way you can see how you like the OS and make sure your hardware works well with it before wiping out Windows. The LiveCD will boot a bit slower and take a little longer to start the programs, but you have plenty enough RAM for it to run.

---

### Post by Tikkyca on 2010-03-20
I need to see your computer specs so i can help you more,uninstall programs that you don't use a lot,programs that YOU installed.

---

### Post by tazz4vr on 2010-03-20
> **Tikkyca said:**
> I need to see your computer specs so i can help you more,uninstall programs that you don't use a lot,programs that YOU installed.

see post #9.

---

### Post by tazz4vr on 2010-03-20
> **iRock said:**
> Well, if your hard drive has enough space you could dual boot.

I would recommend using regular Ubuntu. You can download it, then burn to disk and install from there.

If you prefer to keep Windows and install Ubuntu in a separate partition, let us know and we can help you set up your partitions.

I would first recommend downloading and burning the LiveCD, which is the desktop version, and booting the disk in the first option which makes no changes to your system. This way you can see how you like the OS and make sure your hardware works well with it before wiping out Windows. The LiveCD will boot a bit slower and take a little longer to start the programs, but you have plenty enough RAM for it to run.

Partitions - not a clue, but going to wait on that for now.

In regards to the version of Ubuntu - via ubuntu.com found Ubuntu 9.10.  Although I was able to see what it offers via screenshots, I was unable to find anything about the compatibility with Vista.  At this time I am considering keeping Vista and trying Ubuntu.  Is the above version good or would it be considered too advanced/complicated?

---

### Post by uRock on 2010-03-20
9.10 is great. I would recommend playing with the LiveCD and getting the feel of how Ubuntu works before installing it. As far as compatibility is concerned, the hardest part will be the shrinking of the Vista partition.

---

### Post by tazz4vr on 2010-03-20
> **iRock said:**
> 9.10 is great. I would recommend playing with the LiveCD and getting the feel of how Ubuntu works before installing it. As far as compatibility is concerned, the hardest part will be the shrinking of the Vista partition.

Although it specified downloading an installer, InfraRecorder, is this something that I have to do, or will Windows Player provide the same results for burning this cd?

---

### Post by uRock on 2010-03-20
> **tazz4vr said:**
> Although it specified downloading an installer, InfraRecorder, is this something that I have to do, or will Windows Player provide the same results for burning this cd?

Windows Media isn't capable of burning an ISO.  InfrRecorder is a decent program for Windows

---

### Post by tazz4vr on 2010-03-20
> **iRock said:**
> Windows Media isn't capable of burning an ISO.  InfrRecorder is a decent program for Windows

okay, so, I am going to download the installer, cross your fingers, I am!

Although I am sure I will have more questions later, my think-tank is almost on overload, so I am going to do one task at a time.

Thank you very much for your assistance, advice and extreme patience.

---

### Post by uRock on 2010-03-20
Not a problem.:D

---

### Post by tazz4vr on 2010-03-20
wow... that was a fast download!  I thought i'd be downloading for endless minutes... woo hoo!

It Begins!!!!!  Now for the 9.10 version. 8-[

---

### Post by NightwishFan on 2010-03-20
I hope it goes well for you.

---

### Post by tazz4vr on 2010-03-20
Thank you.

1st Issue - what do I do with the attached?  Which one do I use?

[IMG]http://ubuntu-utah.ubuntuforums.org/picture.php?albumid=1740&pictureid=5815[/IMG]

---

### Post by seenthelite on 2010-03-20
If your Vista install is slow this can be fixed and should be before you install Ubuntu as a dual boot. I think you should consider reinstalling Vista as your first step then when you first boot the new install remove all the programs you will not be using because similar programs will be in your Ubuntu install. Then install all the available Vista updates and then defrag 2 or three times. Consider installing  Windows own anti virus program its free and adequate for most people. Install something like Advanced System Care its free and will help to keep Vista fast. Then install Ubuntu as a dual boot.

---

### Post by uRock on 2010-03-20
I have never used any of those. ISO buster should work.

---

### Post by tazz4vr on 2010-03-20
> **iRock said:**
> I have never used any of those. ISO buster should work.

I'm such a duh sometimes... told you the think-tank was full!  Let me click on the Frequently Asked Questions link!  If info makes no sense, will use the ISO buster as suggested.

@seenthelite - I have removed a lot of programs that are not in use, defraged several times, still no improvement.  To unistall/reinstall Vista, wouldn't I need the discs?  When I purchased this puter, she came with none.

---

### Post by tazz4vr on 2010-03-20
@iRock - kickass avatar - just noticed it, I'm so observant!

---

### Post by NightwishFan on 2010-03-20
Use Infrarecorder.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by tazz4vr on 2010-03-20
Since my last post, I have put Ubuntu 9.10 on a disc via InfraRecorder.  I will be having a peek-see later this evening.  

Thank you all for the support and information.

Phase 1 on switching to Ubuntu is complete.... woo hoo!

---

### Post by tazz4vr on 2010-03-21
Woo hoo!  I am officially using the Ubuntu 9.10 version.  Is the 9.10 version the same as Karmic Koala?

I will mess with it more tomorrow, but so far, it's totally totally cool!

One question though, the screen appears, how to put this... um, like it's shakey, flickering really really fast... Kind of like high school flashbacks!  Without having to relive and do-over my school days, how can I get that to stop?

This is so cool though, I love it.  All the stuff I use on a regular basis, is right here, on the desktop.  No more having to go in and out of folders, applications, etc... and the accessories, like the image stuff, totally cool.  I am so happy with this, it is cool.  I feel like a kid in a candy store, with nothing but Almond Roca for miles on end, and it's just mine.... woo hoo.....

Thank you all so much for the information and support, and especially you iRock for your extreme patience in all my questions.... :wink:

oh, oh, and the speed on this baby, holy you know what!!!!  oh oh, and no freezing... I am so going in and out of all these websites, normally used of course, the one's that were freezing my puter, and she's on fire!  Hasn't froze once yet...  I have found the next best thing to sex!  I am in heaven!

---

### Post by NightwishFan on 2010-03-21
Glad you like it, welcome!

Karmic Koala is the code name for the 9.10 release. 9.10 means October 2010.

To fix your screen issue, start a new thread and post what your graphics hardware is. Describe your problem in detail.

Happy Ubuntuing!

---

### Post by tazz4vr on 2010-03-21
That flickering thing though, making me feel woozie.

---

### Post by NightwishFan on 2010-03-21
I am assuming it is not a normal thing, so please post a new thread. That would lead to less confusion, perhaps since you have Ubuntu installed you can mark this one as solved. I hope you get it fixed.

---

### Post by tazz4vr on 2010-03-21
> **NightwishFan said:**
> Glad you like it, welcome!

Karmic Koala is the code name for the 9.10 release. 9.10 means October 2010.

To fix your screen issue, start a new thread and post what your graphics hardware is. Describe your problem in detail.

Happy Ubuntuing!

Where would I find that info?  My windows start button is gone.

---

### Post by NightwishFan on 2010-03-21
Click this link, and hit ok then install when prompted to install Hardinfo.
[apt://hardinfo]("apt://hardinfo")

When it is installed, press alt+f2, type **hardinfo** and then push enter.

You will want the display tab, on the left. Near the bottom, it says OpenGL.

---

### Post by uRock on 2010-03-21
I searched your model number and it says you have this graphics chipset. NVIDIA® GeForce[® 6150SE]("http://www.emachines.com/products/products.html?prod=EL1200-07w")

In your menus go to System> Administration> Hardware Drivers and see if it list any drivers, if it does, install the one with recommended by it.

---

### Post by NightwishFan on 2010-03-21
I have this exact GPU on my desktop and I will say it is excellently supported using the proprietary drivers. Although it is a low end integrated card, it functions well in Wine. It also offers comparative or even surpasses performance compared to Windows. Do as Irock suggests and install the hardware drivers.

---

### Post by Chris Edgell on 2010-03-21
> **NightwishFan said:**
> Click this link, and hit ok then install when prompted to install Hardinfo.
[apt://hardinfo]("apt://hardinfo")

When it is installed, press alt+f2, type **hardinfo** and then push enter.

You will want the display tab, on the left. Near the bottom, it says OpenGL.

This is so AWESOME!

In fact, as I have struggled over and over to learn to find some one of these stats about my computer, I just can't believe I have never heard this mentioned.

Thank you so much.

---

### Post by tazz4vr on 2010-03-21
> **iRock said:**
> I searched your model number and it says you have this graphics chipset. NVIDIA® GeForce[® 6150SE]("http://www.emachines.com/products/products.html?prod=EL1200-07w")

In your menus go to System> Administration> Hardware Drivers and see if it list any drivers, if it does, install the one with recommended by it.

Is this something that I do while in the 9.10 or in Windows?  At this time I am using the Windows version.  I am so much more partial to the Ubuntu now, it's an awesome system.

---

### Post by NightwishFan on 2010-03-21
What do you mean 'Windows version'? Wubi windows installer?

---

### Post by tazz4vr on 2010-03-21
I did a boot from the cd, did not fully install onto the computer as of yet.  Wanted to check it out first.  My current system in Windows Vista.

---

### Post by uRock on 2010-03-21
> **tazz4vr said:**
> Is this something that I do while in the 9.10 or in Windows?  At this time I am using the Windows version.  I am so much more partial to the Ubuntu now, it's an awesome system.

Yes, you have to do this in ubuntu.

---

### Post by tazz4vr on 2010-03-21
thank you... check it out, I am now able to add an Ubuntu flavor, finally!  Karmic, ah yeah!

---

### Post by NightwishFan on 2010-03-21
You can install the drivers from the live CD. They should work. You have to log out and back in though. Also, please note that Ubuntu is much slower running from the CD then installed.

---

### Post by tazz4vr on 2010-03-21
No way, that is cool, I feel like a female Tim Allen - modify modify modify!

I will definitely check into the graphic's issue as suggested by iRock.  Thank you all very much for your help, it's late and I need to get to bed before I head to my office and start messin on the puter.

Nite all.

---

### Post by tazz4vr on 2010-03-21
> **iRock said:**
> Yes, you have to do this in ubuntu.

Day # 2- okay, I have installed the recommended driver, but still have that flickering type screen display.

Is it due to using a disc and not having installed Karmic?

Can I continue to ask questions here within this thread or do I need to start a whole new one?

---

### Post by NightwishFan on 2010-03-21
Did you log out and log back in? Restarting erases all changes. If you restarted. then install the driver again, log out and back in.

---

### Post by tazz4vr on 2010-03-21
I did log out/log in, but will redo with installing driver again.

---

### Post by NightwishFan on 2010-03-21
I doubt that would help then. It is worth a try. Did you start a new thread on this issue?

---

### Post by tazz4vr on 2010-03-21
> **NightwishFan said:**
> I doubt that would help then. It is worth a try. Did you start a new thread on this issue?

I haven't been able to tear myself away to restart, this is so cool.  Also, no, I have not started a new thread.  For now I am okay with it, once I do a complete install, if the result is the same then I will start a new thread.

Thanks for the help.

---

### Post by NightwishFan on 2010-03-21
No problem. If you need any help installing I can point you to a few links.

---

### Post by tazz4vr on 2010-03-21
> **NightwishFan said:**
> No problem. If you need any help installing I can point you to a few links.

Per the cd and additional user info, I should be able to install from current cd right?  Or is there another form with better results?

---

### Post by NightwishFan on 2010-03-21
Yes, but please tell me how you want to install.

[LIST=1]
[*]Normal Install: Remove all data and use only Ubuntu
[*]Dualboot; Partition and full install with both Ubuntu and Windows
[*]Wubi: Safe install similar to dual boot only Ubuntu does not need it's own partition.
[/LIST]

I can advise you depending on your goals.

---

### Post by RedRat on 2010-03-21
> **-kg- said:**
> There's something else I would be interested in:

What size of hard drive do you have installed and, more importantly, how much space do you have for your Ubuntu partitions?  Did you install Ubuntu in its own partitions, or did you install using WUBI (installing Linux under Windows)?

...


Well that all depends on exactly what you use your computer for and how you use or manage your downloaded data--whatever that might be. If you are pretty good at cleaning up junk, you can get by with a small hard drive, but if you are like me and tend to hang on to stuff, like video (HD type stuff) and music, then you  will need a pretty large disk. Right now, hard drives are pretty cheap, so why short change yourself. I doubt that you can still find a hard drive now under 100 Gb and if you do find it, it will cost you quite a bit per GB  than just buying a large one. I have seen 1 Tb drives for around $100 or less. 

As to how to distribute the partitions, much has been written about that here. Buy a big enough drive and you can allocate several GB to the OS, a couple of GB to swap (usually on the order to the amount of your RAM memory), and the rest to programs and data.

---

### Post by tazz4vr on 2010-03-21
I am not sure at this time how I want to install.  As my work is primarily from home, I use various applications that I fear may not work properly for any number of reasons, so until then, I think it's best to have them both.

By doing this, will it be too much and cause further issue?

---

### Post by tazz4vr on 2010-03-21
I have been so busy messing around, in and out of sites, forgot important issue, how do I get to my stuff that is on Windows such as all my documents and other application shortcuts like skype....

---

### Post by NightwishFan on 2010-03-21
Windows applications are not meant to function on a Linux based operating system. However you can open documents and files by opening your Windows partition. Considering you are a beginner, perhaps you should take a look at this. It is the Wubi option that I suggested for the installation.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by tazz4vr on 2010-03-21
wow, checked out both links, thats alot of info to read on the first one... better get to it.  Thank you.

---

### Post by RedRat on 2010-03-21
> **tazz4vr said:**
> I have been so busy messing around, in and out of sites, forgot important issue, how do I get to my stuff that is on Windows such as all my documents and other application shortcuts like skype....

Well some of your data, i.e., Word Docs, Excel spreadsheets, PowerPoint presentations, etc. can be usually opened in Linux applications like Open Office. If you want to run Skype, you will have to download the Skype Linux version and install it in your Linux distro. 

It is possible to see and copy files from your Windows partition into your Ubuntu directories. The current versions of Ubuntu allow this to be done, earlier versions had difficulty doing this. I move my photos and videos to a large 1.5Gb Seagate disk attached to my Windows machine and it works quite well. I play my music from that disk (doing so right now).

---

### Post by coolcat20006 on 2010-03-21
ok i install wubi and it install ubuntu so i wanted too rever it all the way out of my pc so i went too add & remove program and remove it but it still in my pc how do i remove it all out of my pc without hurting my windows xp?

---

### Post by coolcat20006 on 2010-03-21
i met ok i install wubi and it install ubuntu so i wanted too removed it all the way out of my pc so i went too add & remove program and remove it but it still in my pc how do i remove it all out of my pc without hurting my windows xp?

---

### Post by NightwishFan on 2010-03-21
This question deserves its own thread, as this user has different issues and Wubi is not the topic to begin with. However, I advise you follow this procedure here. Not all of the steps need to be done, it might just remain an option in the boot list.

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?)

---

### Post by tazz4vr on 2010-03-21
Ah ha... I did see some of my info via OpenOffice, thank you for the info.  

This new system is definitely going to work for me, I love it.  I truly enjoy how all the applications are so easily accessible.

---

### Post by NightwishFan on 2010-03-21
Here is an excellent source for beginners.
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)
[http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/)

---

### Post by uRock on 2010-03-21
And here is another good one,

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

