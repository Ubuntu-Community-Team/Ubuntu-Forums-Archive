---
title: "Dreamweaver help!!!"
date: 2011-08-24
forum: New to Ubuntu
---

### Post by kevinbeldreth on 2011-08-24
[FONT=System]I am still a N:confused::confused:B as far as Linux is concerned. I am running Kubuntu 10.04. I do not have it duel-booted with Windows and I am wanting to run Adobe Dreamweaver. I heard of Wine and I have installed that and run the winecfg command but I'm not sure how to make my disc work with my computer. I am not real familiar with much of anything. All I know is I need this program to run on this computer. I did find one thread that was very helpful, except she mentioned duel-booting, which I can't do. Is there a way to get the dependencies without jumping over to Windows? Any help with this is greatly, GREATLY appreciated. Thanks![/FONT]

---

### Post by androssofer on 2011-08-24
> **kevinbeldreth said:**
> [FONT=System]I am still a N:confused::confused:B as far as Linux is concerned. I am running Kubuntu 10.04. I do not have it duel-booted with Windows and I am wanting to run Adobe Dreamweaver. I heard of Wine and I have installed that and run the winecfg command but I'm not sure how to make my disc work with my computer. I am not real familiar with much of anything. All I know is I need this program to run on this computer. I did find one thread that was very helpful, except she mentioned duel-booting, which I can't do. Is there a way to get the dependencies without jumping over to Windows? Any help with this is greatly, GREATLY appreciated. Thanks![/FONT]

can u use a virtual machine?

you could use virtual box and run windows within that to run your dreamweaver on? i do it for uni work... (linux doesnt donate free stuff to the uni to brain wash students to use its software and get them dependent on its non-standard crap ***grumbles***).

---

### Post by kevinbeldreth on 2011-08-24
I hate to even admit this....but I'm not really sure what a virtual machine is...is it hardware that I need?

---

### Post by BlinkinCat on 2011-08-24
See here -

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by Nytram on 2011-08-24
There should be some kind of **Setup.exe** file on the Dreamweaver disk that you can double-click to install it.

---

### Post by androssofer on 2011-08-24
> **kevinbeldreth said:**
> I hate to even admit this....but I'm not really sure what a virtual machine is...is it hardware that I need?

fear not, thts y its called absolute beginner talk! a virtual machine is exactly how it sounds haha. it creates a "virtual computer" within your computer that u can install another operating system on. so a computer within a computer... like inception!

my computer has 4gb of ram and 2.6ghz dual core. when i create my virtual machine (VM) i allocate it some of these reasources. so say 2gb of ram and 1 of the cores of my processor. now it wont use them all at once, thts just the max its allowed.

i would then install windows on my VM, and it would think its on a computer with 2GB of ram and a 2.6ghz single core processor. it would then run windows on my VM, and i can access it like i would any other window. like ur browser. so u can run windows within ubuntu if u need be. 

it also has the advantage that if u break sumthing, its a virtual computer, its not real, so u can hit delete and start again, all sin forgiven..

the link posted above should explain more. mine is the easy to grasp version ;-)

---

### Post by 3rdalbum on 2011-08-24
> **kevinbeldreth said:**
> [FONT=System]I am still a N:confused::confused:B as far as Linux is concerned. I am running Kubuntu 10.04. I do not have it duel-booted with Windows and I am wanting to run Adobe Dreamweaver. I heard of Wine and I have installed that and run the winecfg command but I'm not sure how to make my disc work with my computer.[/FONT]

There are HOWTOs on the Internet for using Wine, unfortunately most of them don't actually work because they're assuming you're using an old version of Ubuntu. Or that you're using Ubuntu when you're actually using Kubuntu.

It's actually really simple to use Wine. Open a terminal, type *wine*, press the space bar to leave a space at the end. Drag the program you want to run (probably the "setup.exe" from the Dreamweaver CD) onto the terminal. It will put some other stuff (the file path) into the terminal line as well. Press Enter in the terminal and the Dreamweaver installer will run.

The process of installing Dreamweaver, from this point on, is exactly the same as Windows. After the installer has finished and quits, you can find a new link to Dreamweaver in the Wine category of your K menu (or Applications lense in Unity). Click it and Dreamweaver will open.

This is best-case scenario. In reality, Wine only works with probably 20% of Windows programs, and your version of Dreamweaver might not be one of them. If someone told you that Wine works for all Windows programs, sorry - they were a bit too enthusiastic and they misled you. I know there are people like that around.

Give it a try and see how it goes anyhow. Otherwise you can just reboot into Windows; you mentioned you are dual-booting.

---

### Post by kevinbeldreth on 2011-08-24
> **Nytram said:**
> There should be some kind of **Setup.exe** file on the Dreamweaver disk that you can double-click to install it.
 
There is a setup.exe file, and when I click it the little Wine icon pops up and acts like its going to open...but never does anything beyond that. I did try a restart, but nothing. Any suggestions? Do I need to go with the Virtual Box?

---

### Post by oldos2er on 2011-08-24
[http://wiki.winehq.org/AdobeDreamweaver](http://wiki.winehq.org/AdobeDreamweaver)

---

### Post by kevinbeldreth on 2011-08-24
@Androssofer Thank you for this post. I will download the virtual  emulator and see how it works and get back to you guys. Thank you so  much for this. I hope it works :D

---

### Post by Nytram on 2011-08-24
> **kevinbeldreth said:**
> There is a setup.exe file, and when I click it the little Wine icon pops up and acts like its going to open...but never does anything beyond that. I did try a restart, but nothing. Any suggestions? Do I need to go with the Virtual Box?

I'm surprised the installer didn't work, here on this web site is a list of the different versions of Dreamweaver, and how well they will work in Wine:

[http://appdb.winehq.org/appview.php?iAppId=183]("http://appdb.winehq.org/appview.php?iAppId=183")

Do you have DW already installed within Windows? You could try launching that version with Wine, and avoid the need to install it in Ubuntu. Navigate into the DW folder that is on your Windows partition and double-click on Dreamweaver.exe.

Check out that web site first though, as some versions of DW will just not run unfortunately.

EDIT: I'm not sure a virtual box will benefit you much as you're already dual-booting Windows (a VB also has to boot up.)

---

### Post by kevinbeldreth on 2011-08-26
Sorry it took so long to reply to this. Been busy. Ok, so I checked out the virtual box...and I'm not sure how to download this correctly :-k The list of OS' includes Ubuntu 10.04, but will that one work for my Kubuntu 10.04?? Sorry again for all the noob-ness..

---

### Post by kevinbeldreth on 2011-08-26
> **Nytram said:**
> I'm surprised the installer didn't work, here on this web site is a list of the different versions of Dreamweaver, and how well they will work in Wine:

[http://appdb.winehq.org/appview.php?iAppId=183](http://appdb.winehq.org/appview.php?iAppId=183)

Do you have DW already installed within Windows? You could try launching that version with Wine, and avoid the need to install it in Ubuntu. Navigate into the DW folder that is on your Windows partition and double-click on Dreamweaver.exe.

Check out that web site first though, as some versions of DW will just not run unfortunately.

EDIT: I'm not sure a virtual box will benefit you much as you're already dual-booting Windows (a VB also has to boot up.)

I'm actually not dual-booting...that's my issue. I've considered going back to Windows for this program, but I really don't want to if I can help it. I have DW-CS5 and I really need this version.

---

### Post by kellemes on 2011-08-26
Personally I'd go dual-boot.. Install Windows, free some space for Ubuntu and install Ubuntu.. The performance of a virtual machine highly depends on hardware and pure luck it seems.. Often it's performance simply sucks.
You need to right tool for the job, and for Dreamweaver you need Windows.

---

### Post by kevinbeldreth on 2011-08-26
> **kellemes said:**
> Personally I'd go dual-boot.. Install Windows, free some space for Ubuntu and install Ubuntu.. The performance of a virtual machine highly depends on hardware and pure luck it seems.. Often it's performance simply sucks.
You need to right tool for the job, and for Dreamweaver you need Windows.

I was afraid it would come to that. The only issue is losing my desktop setup. Its pretty sweet and Windows could never touch it. I'll have to start from scratch as far as Kubuntu is concerned. But would you recommend Ubuntu over Kubuntu?

---

### Post by kellemes on 2011-08-26
> **kevinbeldreth said:**
> I was afraid it would come to that. The only issue is losing my desktop setup. Its pretty sweet and Windows could never touch it. I'll have to start from scratch as far as Kubuntu is concerned. But would you recommend Ubuntu over Kubuntu?

No, I didn't read well.. sorry.. actually I'm using Kubuntu myself and it's just great.

You can backup your /home directory and simply copy it back when you have re-installed **K**ubuntu.
This way you'll have your settings back.
Search the docs for your preferred method of doing this..

---

### Post by kevinbeldreth on 2011-08-26
Thanks for answering that even though it wasn't the topic of this thread. Well...I'm gonna give it a shot. I have one last question however before I do all this. When installing Linux over Windows, I partitioned the hard drive to 100% for Linux. I did try to throw in a Windows disc and it gave me the error that Windows could not recognize a hard drive. I realize this is due to my partition...how do I give Windows back the room that it needs to install? I guess, how do I undo my partition?

---

### Post by kellemes on 2011-08-26
> **kevinbeldreth said:**
> Thanks for answering that even though it wasn't the topic of this thread. Well...I'm gonna give it a shot. I have one last question however before I do all this. When installing Linux over Windows, I partitioned the hard drive to 100% for Linux. I did try to throw in a Windows disc and it gave me the error that Windows could not recognize a hard drive. I realize this is due to my partition...how do I give Windows back the room that it needs to install? I guess, how do I undo my partition?

Assuming you have your important data backed up on some external device you can remove all partitions using you livedisk with gparted or some other partition-tool. This way Windows will ask to create a partition in the empty space..

---

### Post by androssofer on 2011-08-26
> **kevinbeldreth said:**
> Sorry it took so long to reply to this. Been busy. Ok, so I checked out the virtual box...and I'm not sure how to download this correctly :-k The list of OS' includes Ubuntu 10.04, but will that one work for my Kubuntu 10.04?? Sorry again for all the noob-ness..

fear not! open "ubuntu software center" and install virtualbox from ther. then open up virtual box and hit "new". will open up a wizard for u. then hit next... then it will ask for its name, call it "windows" then select the windows version you hav from the drop down..

then hit next

then select the amount of memory to give it. i Hav 4gb on my comp and usually giv vms between 2 and 3 gb... 

hit next

hard disc time, click "new" then it will ask what type and the size. i use dynamic size, and set it to about 20 or 30gb this means that its max size is the size u set it at, but it will only take up what it uses... so if u only install windows and dreamweaver it will only b a few gig.

hit next

will giv u a summary, then hit finish. thats your vm ready to go! 

then put the windows cd in ur disk drive and then hit start on virtual box to start the vm... it shud detect the windows cd and start the install for windows in your vm.. :-)

---

