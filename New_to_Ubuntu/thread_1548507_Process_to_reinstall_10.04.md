---
title: "Process to reinstall 10.04?"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by Mike Krall on 2010-08-08
Got 10.04 installed yesterday and it worked fine enough. Messed up some things and can't figure how to get out of them. Want to start fresh and try again and not finding process in searches. 

Would someone link me to or describe the process of reinstalling 10.04, please?

All I need to do is get the OS "/" back to original... have partitions sized and formatted as needed for "/", "/home", "swap", "unallocated" already.

Mike

---

### Post by bprins on 2010-08-08
reinstall from CD is the easiest option, but i assume you realise that? whats holding you back?

---

### Post by Mike Krall on 2010-08-08
Clueless... 

Best guess is, spin up, dump primary holding "/" and reenter it and see if only "/" installs. Don't know anything for sure.

Mike

---

### Post by teh603 on 2010-08-08
I haven't messed with manually assigning partitions like that, but it would make sense to just follow the default installation, and then assign your partitions in manual mode when you get to the partitioner screen. Might help to format your "/" partition if something's badly fritzed, but you'll need to make sure that it isn't going to format /home.

At least that's the theory of it.

---

### Post by Mike Krall on 2010-08-09
Yup... "in theory"...  =]  

Seems like guarantying it has a procedure and if I can learn that, it will maybe let me mess around more than I do, for "the fears".

Mike

---

### Post by john newbuntu on 2010-08-09
Just to add to what others have stated, install ubuntu using the liveCD.  In the "prepare disk space" screen use the "specify partitions manually" option.  You do not have to create any partitions.  However, you will have to assign them to the appropriate mount points.

Check the format checkbox in the "Prepare partitions" screen(I am assuming here that you need a brand new install of everything including /home).  Here are 2 good guides to follow(the second might be slightly older though):

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

[http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide](http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide)  (section 7 onward.  Choose the partition, click edit and assign mount point)

---

### Post by teh603 on 2010-08-09
> **john newbuntu said:**
> [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Is it me, or is this guy really pessimistic about how much RAM a computer running Linux will have? My eeePC 2g Surf has half a gig, and I believe my AAO had a full gig. What's this 256 MB business?

---

### Post by aeiah on 2010-08-09
> **teh603 said:**
> Is it me, or is this guy really pessimistic about how much RAM a computer running Linux will have? My eeePC 2g Surf has half a gig, and I believe my AAO had a full gig. What's this 256 MB business?

256mb ram is the threshold for getting the livecd to run properly, because it loads a lot of stuff into ram. if you have less than this amount, you have to install using the alternate cd and not have the luxury of a fancypants gui, that's all. yes, all computers of the last few years have enough to run the livecd no problems, but some people own very old computers and might want ubuntu installed on them to breath new life into an old machine.

but yes. just go with manual partitioning and format the partitions you've already set up. if you have any data you want to keep in your home dir i suggest backing it up. there's no point trying to save your home partition if that ends up being one of the mis-configured issues that have meant you'd like to reinstall. i say this because it is quite possible to install ubuntu and not re-format your home partition, saving all of its data. in this case (and most others) it isn't wise to keep an existing home partition.

---

### Post by john newbuntu on 2010-08-09
> **teh603 said:**
> Is it me, or is this guy really pessimistic about how much RAM a computer running Linux will have?
Can't believe it eh, teh603.  I have only 512MB on one of my PC and things are just hunky dory.

---

### Post by QLee on 2010-08-09
> **teh603 said:**
> Is it me, or is this guy really pessimistic about how much RAM a computer running Linux will have? My eeePC 2g Surf has half a gig, and I believe my AAO had a full gig. What's this 256 MB business?

Sometimes people refer to this as "the real world". People use Ubuntu the world over, not just in places where there is access to a "mega-super-discount computer store" and many times people do not have enough disposable income to purchase the latest equipment. It's possible to run 10.04 on a 1GHz, 256MB RAM system with a 8MB video card. It won't run fast and it won't do the latest 3D effects or play top-end games but would allow them to have email and an Internet browser and many of the things a computer can do for us. Sometimes even people with low-spec systems have useful and correct answers in the forum too. It's a big world.

---

### Post by teh603 on 2010-08-09
> **QLee said:**
> Sometimes people refer to this as "the real world". People use Ubuntu the world over, not just in places where there is access to a "mega-super-discount computer store" and many times people do not have enough disposable income to purchase the latest equipment. It's possible to run 10.04 on a 1GHz, 256MB RAM system with a 8MB video card. It won't run fast and it won't do the latest 3D effects or play top-end games but would allow them to have email and an Internet browser and many of the things a computer can do for us. Sometimes even people with low-spec systems have useful and correct answers in the forum too. It's a big world.So basically, systems like that old Winbook M that I bough in '03 or so that I only bring out when I want to show off?

Just kidding. I honestly wasn't thinking about other countries.

---

### Post by Mike Krall on 2010-08-09
> **john newbuntu said:**
> Just to add to what others have stated, install ubuntu using the liveCD.  In the "prepare disk space" screen use the "specify partitions manually" option.  You do not have to create any partitions.  However, you will have to assign them to the appropriate mount points.

Check the format checkbox in the "Prepare partitions" screen(I am assuming here that you need a brand new install of everything including /home).  Here are 2 good guides to follow(the second might be slightly older though):

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

[http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide](http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide)  (section 7 onward.  Choose the partition, click edit and assign mount point)

Thanks for the links. I've used a lot of 'aysiu's' stuff, but hadn't seen the the other... nice version of the procedure.

I don't need to redo "/home". The only thing in it right now is bookmarks from Xmarks. 

In the end, what I'm trying to do is get "/" to LiveCD original, then add updates again. I don't know of another approach to this other than "clean reinstall". 

The mistakes I think I made are messing with GSynaptics, other than through synaptic package manager, and it's got a wrong marking in it (ElanTech touchpad problems). Also messed with repositories (and didn't document so I don't know what was original), as well as changed synaptic package manager to "Mark All Upgrades" in a fit of misunderstanding what that means to LTS versions (still not absolutely sure, but...). The upshot is, I'm trying to learn to do my own diapers and I'm on a steep part of the curve.

Somewhere I'd gotten the idea a "clean reinstall" took more than picking the "/" partition, marking a "mount point", format (ext4), and letting it fly... is why I asked.

Mike

---

### Post by Mike Krall on 2010-08-09
> **aeiah said:**
> but yes. just go with manual partitioning and format the partitions you've already set up. if you have any data you want to keep in your home dir i suggest backing it up. there's no point trying to save your home partition if that ends up being one of the mis-configured issues that have meant you'd like to reinstall. [COLOR="Blue"]i say this because it is quite possible to install ubuntu and not re-format your home partition, saving all of its data. in this case (and most others) it isn't wise to keep an existing home partition.[/COLOR]

Thanks for that...

As I said to Jon, I feel all I need to do is reinstall for "/"

I'm not getting your last sentence... "In this case (and most others), it isn't wise to keep an existing home partition."

Mike

---

### Post by john newbuntu on 2010-08-10
Since you need to redo / and retain /home, in the "prepare partitions" screen, identify the mount point for /home filesystem but DO NOT check the "format" checkbox for this row.
Make sure that the format checkbox for / is checked.  Continue with the install.

[http://www.basicconfig.com/ubuntu_desktop_manual_partition_finish_partition](http://www.basicconfig.com/ubuntu_desktop_manual_partition_finish_partition)

I would strongly suggest that you back up /home to a different disk prior to doing this just in case.

---

### Post by QLee on 2010-08-10
[QUOTE=Mike Krall]Got 10.04 installed yesterday and it worked fine enough. Messed up some things and can't figure how to get out of them. Want to start fresh and try again and not finding process in searches. 
[/QUOTE]

What might turn out to be important are the unspecified "things" that were "messed up". Everyone but aeiah seems to be assuming that it's going to be best to save /home in its current state. However, if some of the "things" that got "messed up" are things in userspace, then keeping the /home isn't going to change that, I'd guess that's the reason aeiah suggested this was a case for overwriting with a default home to get back to a default install. It doesn't appear that this install was working long enough to have much saved in home.

Mike, if you have the time, you would learn more about Ubuntu by fixing than reinstalling but this is a case where reinstalling would be faster and easier to get you back up and running.

---

### Post by Mike Krall on 2010-08-10
> **john newbuntu said:**
> Since you need to redo / and retain /home, in the "prepare partitions" screen, identify the mount point for /home filesystem but DO NOT check the "format" checkbox for this row.
Make sure that the format checkbox for / is checked.  Continue with the install.

Thanks, John... 

Mike

---

### Post by john newbuntu on 2010-08-10
You're welcome.  Now, did that help?

---

### Post by Mike Krall on 2010-08-10
> **QLee said:**
> What might turn out to be important are the unspecified "things" that were "messed up". Everyone but aeiah seems to be assuming that it's going to be best to save /home in its current state. However, if some of the "things" that got "messed up" are things in userspace, then keeping the /home isn't going to change that, I'd guess that's the reason aeiah suggested this was a case for overwriting with a default home to get back to a default install. It doesn't appear that this install was working long enough to have much saved in home.

Mike, if you have the time, you would learn more about Ubuntu by fixing than reinstalling but this is a case where reinstalling would be faster and easier to get you back up and running.

Well, maybe I will redo the whole thing then... make sure the format boxes are checked for what needs rewritten and leave all else the same.

I understand "fixing" would be a lot more educating and I'm not opposed to doing it, but I simply can't do it on my own... not at the level of understanding I have. I can't find/figure what the system is supposed to look like so it's darn hard to work back towards that.

From Post #12...

*The mistakes I think I made are messing with GSynaptics, other than through synaptic package manager, and it's got a wrong marking in it (ElanTech touchpad problems). Also messed with repositories (and didn't document so I don't know what was original), as well as changed synaptic package manager to "Mark All Upgrades" in a fit of misunderstanding what that means to LTS versions (still not absolutely sure, but...). The upshot is, I'm trying to learn to do my own diapers and I'm on a steep part of the curve.*

I should have added to that I checked to bring stuff in from Win7 with the original install, and didn't need to/don't want to... just another "wishful thinking" exercise of the type that got me to needing a reinstall.

Mike

Oh... the only thing in "/home" is a set of bookmarks I can easily replace from Xmarks. 

Sda1  "Recovery" (Fat32) 15GB
Sda2  "OS" (C)~Win7 (NTFS) 40GB
Sda3  "/" (ext4) 10GB
Sda5  "/home (ext4) 240GB
Sda6  "swap" 5GB
Free Space "Unallocated" 10GB

---

### Post by Mike Krall on 2010-08-10
> **john newbuntu said:**
> You're welcome.  Now, did that help?

Yes it did... simple, helpful, to the point...  =]

Mike

---

### Post by silverglade00 on 2010-08-10
> Oh... the only thing in "/home" is a set of bookmarks I can easily replace from Xmarks.


That is the part that everyone has hinted at, but nobody has come out and told you. There are lots of hidden files in your /home/mike (just an example) folder that can be part of the cause of your problems. The home folder contains hidden configurations for the preferences you choose in your applications. Since Ubuntu (and other Linux systems) were created with multiple users in mind, they needed a way for your Firefox bookmarks and preferred screen resolution (just examples) to be saved. They also can't interfere with my settings. The way this is done is by saving them to hidden files in your home folder. 

Depending on what problems you are having, those settings might be preserved in your home folder. If they are, then reinstalling the system will not help unless you also format your /home partition. The quickest way to check this is to create a new user and see if the problems still exist while logged in as that user.

Now about the problems in post 12... picking Mark All Upgrades just tells Synaptic Package Manager to update everything it can to the latest versions. This is the power and beauty of the package manager. It upgrades all of your programs and your operating system at the same time. Much better than having to scour the Internet looking for each program that you have to see if there are updates. All you have to do is click Apply after that and watch the progress bar. When it is done you might have to restart your computer. It will tell you if you do. 

If I read the part about GSynaptics correctly, you should just need to right click it in the package manager and choose remove or uninstall (I forget exactly what it is called). Then click Apply. This should get rid of it.

---

### Post by QLee on 2010-08-10
[QUOTE=silverglade00]
If I read the part about GSynaptics correctly, you should just need to right click it in the package manager and choose remove or uninstall (I forget exactly what it is called). Then click Apply. This should get rid of it.[/QUOTE]

He probably wants to mark it for complete removal (purge), to get rid of the configuration files too.


Is that the only "things" you meant were "messed up", Mike?

None of us expect you to fix by youreslf Mike, that's why there are people standing by here to answer your questions. However, it's not a bad thing if you choose to get get up and running now and wait until you've had more experience to stick with fixing (which can sometimes be slow and painful for a new user.

---

### Post by Mike Krall on 2010-08-10
> **silverglade00 said:**
> Now about the problems in post 12... picking Mark All Upgrades just tells Synaptic Package Manager to update everything it can to the latest versions. This is the power and beauty of the package manager. It upgrades all of your programs and your operating system at the same time. Much better than having to scour the Internet looking for each program that you have to see if there are updates. All you have to do is click Apply after that and watch the progress bar. When it is done you might have to restart your computer. It will tell you if you do. 

If I read the part about GSynaptics correctly, you should just need to right click it in the package manager and choose remove or uninstall (I forget exactly what it is called). Then click Apply. This should get rid of it.

The reason I figured I better undo "Mark All Upgrades" is I felt applying it would bring in "Upgrades" not specific to the LTS of 10.04... like those for the coming 10.10, etc. Staying with 10.04 LTS through to the next LTS is what I'd likely do... though I do understand there can be downsides to that. 

The "GSynaptics" thing is related specifically to the Asus ElanTech touch pad... I needed to shut it off and didn't deal with it either methodically or correctly enough to "fix" anything... now I don't know where I am with it and don't know how to find out. I did two things after getting into La-La-Land... through Synaptic... simultaneously removed gsynaptics and installed gpointing-device-settings ("It is a successor of GSynaptics"). Doing so got rid of "Touchpad" in System > Preferences and did not add "Touchpad" to "Mouse", or anything else I looked at. After which I separately uninstalled "Gpointing..." and reinstalled "GSynaptics". There is a "non-function" window-message when trying to bring up the new "Touchpad" out of "Preferences". I don't have any idea if it was there originally and don't know how to find out... therefore, I tend towards a reinstall.

A "standard procedure" question... Had a person ought to "restart" after every install/uninstall (which I have not done)?

Mike

---

### Post by residentbiker on 2010-08-10
> **teh603 said:**
> Is it me, or is this guy really pessimistic about how much RAM a computer running Linux will have? My eeePC 2g Surf has half a gig, and I believe my AAO had a full gig. What's this 256 MB business?
 
 
Don't be afraid of RAM, or adding it. As with any computer/OS, RAM makes the machine, it's just plain better, and faster. RAM is cheap and easy to install, but you know all this. I'd have 8 gigs if XP would 'see' it. Unfortunately, unless it's 64 bit, it will only see 4, which I have, on all my machines. Good day.

---

### Post by teh603 on 2010-08-10
> **residentbiker said:**
> Don't be afraid of RAM, or adding it. As with any computer/OS, RAM makes the machine, it's just plain better, and faster. RAM is cheap and easy to install, but you know all this. I'd have 8 gigs if XP would 'see' it. Unfortunately, unless it's 64 bit, it will only see 4, which I have, on all my machines. Good day.Depends on if the RAM is still available for your model. Some Macs (for example) used 8-chip non-parity 30 or 72-pin SIMMs, and good luck finding those in any size. Or worse, if you got one of the few Macs that did take parity RAM, but couldn't use PC parity RAM. Laptops are even worse; there's very little standard about their memory.

Just because RAM is cheap doesn't mean *your* RAM is cheap, lol.

---

### Post by silverglade00 on 2010-08-10
> **Mike Krall said:**
> The reason I figured I better undo "Mark All Upgrades" is I felt applying it would bring in "Upgrades" not specific to the LTS of 10.04... like those for the coming 10.10, etc. Staying with 10.04 LTS through to the next LTS is what I'd likely do... though I do understand there can be downsides to that. 

Fortunately, Ubuntu is set up to do just this by default. When there is a new version available, Update Manager will give you a notification that it is available. It will let you choose whether to install or not. There will also be plenty of help here when it is time for the new release. It is also set up already to stick to LTS releases, meaning that you will not be prompted to upgrade your version until the next LTS release. The upgrades that it refers to are the ones specific to your version. It is somewhat analagous to running updates to Office 2000 on your XP machine not updating your version of Windows or Office. It just updates that version of Office 2000. The best thing to do would be to check the forums here for lots of new topics like "Updates messed up my computer!!11!!" If there aren't very many (or any) then it is pretty safe to Mark All Upgrades and Apply. 

> The "GSynaptics" thing...
I do not have any experience with these, but you might get lucky and the updates reside in one of the updates waiting for you. I tend to use an external USB mouse on my laptops, so I don't spend much time configuring the touchpad.

> A "standard procedure" question... Had a person ought to "restart" after every install/uninstall (which I have not done)?

Mike

If you use Update Manager to check for updates, it shows an icon next to any updates that require a restart. It will also show a popup when those updates are complete that will make you choose to restart now or later. Examples would be a video driver update or certain main libs. If it is just upgrading firefox for instance, you just need to restart that application to get the new version running.

---

### Post by Mike Krall on 2010-08-10
> **QLee said:**
> He probably wants to mark it for complete removal (purge), to get rid of the configuration files too.


Is that the only "things" you meant were "messed up", Mike?

None of us expect you to fix by yourself Mike, that's why there are people standing by here to answer your questions. However, it's not a bad thing if you choose to get get up and running now and wait until you've had more experience to stick with fixing (which can sometimes be slow and painful for a new user.

QLee... I know there is help. If I try first, getting help when I need it seems proper. Not trying first is another matter... it is why I wanted to start over... try first, start over, and try again.

The "GSynaptics" and associated ElanTech touchpad, "Mark All Upgrades" (which turns out I got right), and "Repositories", that I did not note "original" form of before fussing with... intending to add all (with source, 'cause I don't know if it needs to be there for things to actually install completely) 'cause I wanted to download Opera and don't know what part of Repositories it is in. Lastly, marking something about bringing Win7 stuff to 10.04 when doing "manual partition"... I don't know anything actually happened with that but I shouldn't have checked it as I don't/won't use Win7... wouldn't have it in the machine if it didn't need to be there to support possible warranty diagnostics.  

Mike

---

### Post by Mike Krall on 2010-08-10
> **silverglade00 said:**
> Fortunately, Ubuntu is set up to do just this by default. When there is a new version available, Update Manager will give you a notification that it is available. It will let you choose whether to install or not. There will also be plenty of help here when it is time for the new release. It is also set up already to stick to LTS releases, meaning that you will not be prompted to upgrade your version until the next LTS release. The upgrades that it refers to are the ones specific to your version. It is somewhat analagous to running updates to Office 2000 on your XP machine not updating your version of Windows or Office. It just updates that version of Office 2000. The best thing to do would be to check the forums here for lots of new topics like "Updates messed up my computer!!11!!" If there aren't very many (or any) then it is pretty safe to Mark All Upgrades and Apply.

I get this... thanks for the full explanation.

Mike

---

