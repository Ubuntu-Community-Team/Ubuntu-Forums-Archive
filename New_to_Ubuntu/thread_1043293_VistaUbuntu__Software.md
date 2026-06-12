---
title: "Vista/Ubuntu  Software?"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by Just Plain Fred on 2009-01-18
Hello All,
 I have a 2 drive, vista / Ubuntu dual boot install.(HP Desk top) Iv'e read somewhere that there is a software that will allow vista and ubuntu to play nice together, but can't seem to find this again! Can anyone lead me to this or did i just misread something? Regards Plain Fred

---

### Post by jrusso2 on 2009-01-18
It would be helpful if you could be more specific.  Like define what you mean by play nice together.

---

### Post by taurus on 2009-01-18
You can mount your vista partition in Ubuntu with ntfs-3g driver.  Just install ntfs-config and use it to config your windows partition.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

And if you want to access your Ubuntu partition while in windows, then use fs-driver, [http://www.fs-driver.org/](http://www.fs-driver.org/).

---

### Post by CLomax on 2009-01-18
I have a feeling you mean that there's software which allows one to see his Linux partition from within Windows. That exists and is here:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Vaedrah on 2009-01-18
Perhaps you could try VirtualBox Just Plain Fred. I have been experimenting with it lately - this free software lets you run one OS on top of another so that both operate at the same time. At the moment I have XP running on Ubunbtu 8.04 and also Fedora. I'm about to add Ubuntu 8.10 to try it out.

One advantage is that you can try upgrades out without having to update your machine and if you don't like the outcome you can just remove the new OS without affecting your main OS.

Here is a link FYI

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

There are other applications e.g. vmware that I have yet to try. Also I have tried Wine and Winetricks (there is a section on these forums) that allows windows s/w to run on Linux. (Sort of a translation layer I guess). Wine however is more limited in the s/w that it will run, VirtualBox etc lets the new OS run as if it was installed on a real hard drive, as opposed to a virtual one.

The only hassle I have found is USB connectivity - the forums here are full of people expressing problems. However everything else seems to run easily (e.g. installing the OS, connecting to the Internet, file sharing etc)

I am guessing this may be what you were looking for, if not though, no worries.

---

### Post by Just Plain Fred on 2009-01-18
Hello All,
Sorry that i didn't make myself clear in that post,"play nice together" I meant that Vista and linux could somehow talk to each other( Read files etc.) Thanks for the links i will explore them now. Regards PlainFred

---

### Post by Vaedrah on 2009-01-18
Hi Just Plain Fred

FYI; I suggest VirtualBox for cross operating system (OS) file sharing. The setup is easy (even I could do it!) and both OS's operate in parallel. Unlike dual boot, where you have **either** one OS or the other and then, after a long reboot sequence, using a Virtual Machine (VM) lets both OS's run at the same time on the screen.

With this, you can send files from one to the other using a shared folder. This communication is very fast - also fairly easy to set up. For example, this notebook has 150 GB of Ubuntu 8.04 on sda2 and sda3 and I left 10 GB of FAT32 at sda1. I can share sda1 with XP, Fedora and Ubuntu 8.10 running as guests on top of the host (base OS) Ubuntu 8.04. IN other words, the shared folder can be anywhere on your PC or notebook.

Also, if you get bored with one guest OS you just remove it and release hard drive memory to the host OS.

One thing I am planning to try is to run a dual boot OS as a composite guest on top of the host OS. I think this should work. My interest is to see if the VM technology could be used to allow people an opportunity to try dual boot experiments out without upsetting their main OS - once the bugs are ironed out then perhaps such people would have greater confidence with the actual dual boot implementation.

---

### Post by Just Plain Fred on 2009-01-19
taurus,
Hello, sorry in advance for asking such a "noob" question! Here goes Having been an exclusive vista user, i have no idea how to do what your suggesting. (command prompt challenged)I can open the "terminal" now do i type in "Code: and a long line of what you stated, or 3 separate lines? or no "Code:" and then the code? tried some but received "command not recognized" This is "Absolute Beginner Talk" so i don't feel too bad! Regards PlainFred

---

### Post by taurus on 2009-01-19
You type one line at a time.  So, type the first line and hit the Return key.  Wait for it to complete and then type in the second command and hit the Return key.  When you type in the third line and hit the Return key, you would see a new window pop up, letting you configure your ntfs partition/drive.

---

### Post by Miljet on 2009-01-19
When you type in the first line and hit enter, it will ask for your sudo password. That is your normal log-in password. It will not show on the screen as you type it in, but it is being accepted. Just type it in and hit enter again. You should not be asked for the sudo password for the next two lines.

---

### Post by Just Plain Fred on 2009-01-19
taurus,
Thank you for your response. First where can i learn these command's? that worked and i now can view my "windows drives" (except for usb) Question: how do you "un-mount" to remove them (icons) from the desktop? Regards PlainFred

---

### Post by Miljet on 2009-01-20
There are many tutorials covering bash commands. One is [http://www.tuxfiles.org/linuxhelp/theshell.html](http://www.tuxfiles.org/linuxhelp/theshell.html). You can Google for "Linux Commands" or "bash commands" and find lots more.

As for un-mounting partitions or drives, simply right click on the icon and select un-mount from the menu.

---

### Post by arikshtiv on 2009-01-20
can't he just copy and paste all the 3 command lines at once?
I pasted even 5 or 10 command lines.

---

### Post by handydan918 on 2009-01-20
> **arikshtiv said:**
> can't he just copy and paste all the 3 command lines at once?
I pasted even 5 or 10 command lines.

It depends. If the commands are not dependent on the successful exit of the prior command, you can get away with that. Otherwise, it's best to put  && between the commands, but all on the same line, so that each command will run only if the prior command completes successfully.

---

### Post by ugm6hr on 2009-01-20
> **Just Plain Fred said:**
> taurus,
Thank you for your response. First where can i learn these command's? that worked and i now can view my "windows drives" (except for usb) Question: how do you "un-mount" to remove them (icons) from the desktop? Regards PlainFred

Just right-click the icons - it offers to unmount.

If you want to configure whether they mount at startup - just run the ntfs-config program (I think it appears as Configure NTFS drives in the menu) and select the drives you want.

---

### Post by Just Plain Fred on 2009-01-20
Hello All,
Well after about 2weeks and pulling out what little hair (that i still have left) out, I GIVE! "ubuntu" is not for a new PC user (  15 months) you guys seem to be masochistic! If this is (forum)"Absolute Beginner Talk" i would hate to see what problems the rest of the forums have! I have had nothing but problems with ubuntu  Firefox, WWAN, Bookmarks, (crash when i would try to move them around) Even reached back into my Vista WWAN! Good thing i have backed up both of my hard disks ( TI- 11 8101 Acronis).If this is what saving a few hundred dollars (for os etc.)i don't have the time or energy to "slug through" the learning curve. And how about the hundreds of "Updates" and you think windows is bad!One more thing you should try some new names for you various OS's (Really Goofy!) Good luck with linux red flamingo whatever! Regards Fred

---

### Post by handydan918 on 2009-01-20
> **Just Plain Fred said:**
> Hello All,
Well after about 2weeks and pulling out what little hair (that i still have left) out, I GIVE! "ubuntu" is not for a new PC user (  15 months) you guys seem to be masochistic! If this is (forum)"Absolute Beginner Talk" i would hate to see what problems the rest of the forums have! I have had nothing but problems with ubuntu  Firefox, WWAN, Bookmarks, (crash when i would try to move them around) Even reached back into my Vista WWAN! Good thing i have backed up both of my hard disks ( TI- 11 8101 Acronis).If this is what saving a few hundred dollars (for os etc.)i don't have the time or energy to "slug through" the learning curve. And how about the hundreds of "Updates" and you think windows is bad!One more thing you should try some new names for you various OS's (Really Goofy!) Good luck with linux red flamingo whatever! Regards Fred
Sorry it didn't work out for ya fred. Check back in a few years, when they release "Retching Rabbit"!

And in the mean time, try installing a few non-linux operating systems. That will change your perspective....

In my experience, the only people who think Linux is tough have never tried to install Windows. (And I'm not talking about a 'restore cd".)


):P

---

### Post by ugm6hr on 2009-01-20
> **Just Plain Fred said:**
> Hello All,
Well after about 2weeks and pulling out what little hair (that i still have left) out, I GIVE! "ubuntu" is not for a new PC user (  15 months)

Unfortunately, installing a new OS (even Vista) is not going to be an easy task for anyone with 15 months computing experience.  Additionally, 15 months of Windows experience is probably more hindrance than help in Ubuntu.

The difference is the support available to Ubuntu beginners here.

Out of interest: What changed in the 20 hours since your last post?

---

### Post by Just Plain Fred on 2009-01-20
umg6hr,
Hello, and thank you for your question. What has happened is i couldn't deal with everything that iv'e tried has ended in a failure of some sort (over the last week or so) or if i got whatever  to work it had more problems than i managed to  correct.  The word "buggy" comes to mind sort of reminds me of Acronis 2009!  Look I do not mind at all spending a few bucks $ to have a system that does exactly what i want,(and actually works) without having to learn some sort of Geeky  "command Prompt" screen!If this is your idea of a "great leap forward " then lots of luck with it.I do not want to have to become proficient in some sort of "Geek Speak" At 62 years of age i just want a system that is intuitive and actually works without having to jump through a lot of hoops just to get the "basics" Ie : internet connection that works (all the time) a browser that doesn't freeze my system, being actually able to view my files and "unmount" without error messages etc etc etc etc! and NO COMMAND SCREEN BS! Hope that answers your question. Regards Plain FRED.

---

### Post by taurus on 2009-01-20
Maybe windows is all you want.

---

### Post by Just Plain Fred on 2009-01-20
taurus, 
Hello, It's not that i am "locked in to windows" ubuntu doesn't work! (for me and what i want to do) It seems to be geared to those who love pages of "command prompt" screens, and thinking through how to get something that Vista or XP has done for years. Don't get it! And what about the HUNDREDS OF UPDATES? Have never had that happen with Vista (SP-1) Does not inspire me! Like i said at 62 don't have the time or energy to play around with nonsense!Maybe when i have nothing better to do i'll check out intrepid turtle or something again. Anyway thank you and every one who has tried to help me you have a good forum Still can't believe that for the "absolute beginner" forum you have to learn the "Command prompt"  lingo seems that your missing the point of "Absolute Beginner" Regards and good bye Fred

---

### Post by floatingpoint on 2009-01-20
I think what Taurus meant was that perhaps Windows already does everything that you need. I can assure you that Ubuntu does work, even without much (or any) use of the command prompt.

Why do you have Ubuntu installed? What do you use it for that you can't use Windows for?

---

### Post by ugm6hr on 2009-01-21
> **Just Plain Fred said:**
> Still can't believe that for the "absolute beginner" forum you have to learn the "Command prompt"  lingo seems that your missing the point of "Absolute Beginner" 

Actually, you don't.  The same things can generally be achieved with your mouse.

The reason why we advise the use of the "Command prompt" is that it takes 30 seconds to type a command for you to cut and paste; it can take over 5 mins to *describe* what to click on etc.

For an example of what I am talking about - read this thread (if you have time): [http://ubuntuforums.org/showthread.php?t=639201](http://ubuntuforums.org/showthread.php?t=639201)
You will see that the user was confused about what to do, but it was easier to exlain what to do with text.  Post #16 solved the issue, but took quite a bit of work from me to actually go through the motions of doing it while typing instructions to ensure that everything was exactly as described.

In any case, if Windows achieves your goals for your PC, and you have already paid for it, then you are perfectly entitled to use it.  But unless you have specific needs for your PC, I have no doubt Ubuntu would be as good, *provided that it was installed and configured for you by someone who knows how to do that* (as Windows was when you bought the computer).

As for the hundreds of updates - If you installed Vista (i.e. the original version), in addition to MS Office 2007, Paintshop, MSN Messenger (and equivalents of all the other software that Ubuntu comes with), you would probably find hundreds of updates *available* for the various applications and Vista if you looked on the web.  Ubuntu *automatically* looks for and offers to installs updates for every application you install; this is not compulsory (you can limit it to security updates which would be much fewer in number), but makes maintaining your computer with up-to-date and secure packages much easier.  I hope that makes sense (there are also other reasons for comparison - but I will leave it at that here).

One other point: if you installed Ubuntu from *within* Windows (using "Wubi"), that may explain why you are having difficulties.

Good luck with whatever you choose.

---

### Post by Just Plain Fred on 2009-01-21
ugm6hr,
Hello again.OK let me respond,First the ubuntu install was done with a a disk (CD) that i downloaded (and checked) so far so good.
did the "dual boot thing" separate HD. still good. Boot up ubuntu, and try to set up internet connection starts to go downhill from here! (by the way the welcome screen ,if you stand back from your screen looks like a profile of a "screaming skull" very creepy!) Problems with fireFox browser, PC locks up trying to move bookmarks around. That also "Pooched" my  broadband access could not re-establish connection. Also noticed that it "reached back into the Vista side, and did same. had to contact my verizon provider to download the program and install again. (getting Ticked off at this point) Then tried to set something up so i could "see" back into Vista enter, Command prompts! In the 15 months in Vista i have NEVER had to use any command prompt's!(and have done much fooling around system wise) After following the advice i could mount my vista drives but could not "un-mount" Error messages of some sort.All i can say is it's a good thing i backed up both of my hard drives. Bottom line: if ubuntu can't provide basic internet/ browser service out of the gate without problems I GIVE! Hope this clears up some of you questions  It does not make much sense to me to invest the time (to fix this) so that i can save a few "federal reserve notes" (Purchasing software) When you can get a OS that works out of the box is shear lunacy! Regards,PlainFred

---

