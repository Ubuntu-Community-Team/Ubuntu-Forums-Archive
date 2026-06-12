---
title: "I Have Trouble Installing Packages"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by wapotter on 2009-10-15
[FONT=Times New Roman][SIZE=3]I installed Ubuntu 9.04 (i386) for the first time on my computer last month, and I'm never switching back to windows. I'd like you to help me solve the following problems. [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][FONT=Nimbus Roman No9 L][SIZE=3]1.[/SIZE]      [/FONT][SIZE=3]How can I install/run a windows (.exe) application, add its (.dll) plug-ins and other add-ons?How can I use a windows (.exe) application which doesn't have an installer that can run from a folder, such as the Mame32 emulator and the Revolt game?[/SIZE][/FONT]
[FONT=Times New Roman][FONT=Nimbus Roman No9 L][SIZE=3]2.[/SIZE]      [/FONT][SIZE=3]How can I install a Linux application, or application patch, if its package (not the .deb packages) is stored inside a hard drive or a removable media as a tar.gz or tar.bz2? When I try to follow instructions it sounds too geeky for me.[/SIZE][/FONT]
[FONT=Times New Roman][FONT=Nimbus Roman No9 L][SIZE=3]3.[/SIZE]      [/FONT][SIZE=3]How can I install my computer's graphics card (GE FORCE FX5500) driver? I have the NVIDIA-Linux-x86-173.14.20-pkg1.run and nvidia-xconfig-1.0.tar.gz files stored in my hard drive, but I don't know what to do. I installed the NVIDIA X Server Settings application, what does it do?[/SIZE][/FONT]
[FONT=Times New Roman][FONT=Nimbus Roman No9 L][SIZE=3]4.[/SIZE]      [/FONT][SIZE=3]Whenever I insert a CD/DVD in the CD/DVD-ROM drive I can't access any item on the Places menu (even though the list appears when I click on the menu and items). Secondly, all drives, partitions and folders get automatically unmounted. Thirdly, the CD/DVD-ROM drive freezes when there is a CD/DVD inside, .i.e. when I press the eject button on the drive nothing happens unless I restart the computer. How can I browse content inside a CD/DVD with the default file manager like I do with a removable media?[/SIZE][/FONT]
[FONT=Times New Roman][FONT=Nimbus Roman No9 L][SIZE=3]5.[/SIZE]      [/FONT][SIZE=3]When I insert an audio-CD I get the message: Could not open location 'cdda://sro/' failed to execute child process “ sound juicer” (no such file or directory).  What does this mean?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Please help me out!!![/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Wapotter[/SIZE][/FONT]

---

### Post by halitech on 2009-10-15
1. Linux is not windows so some things just won't work. You can try installing WINE but I'm not sure how well things will work in regards to dll plugins and addons.

2. Depending on the package, it should have a readme file to explain how to install the package. Generally its extract the files, cd to the directory then run ./configure, then make and possibly make install.

3 Check in the Hardware drivers and see if it has a driver there you can enable, will be easier to do that if you can.

4. not sure on the first part but if there is an icon on the desktop for the drive, you can try Right-click - Eject to see if that will remove it first.

5. sounds like Sound Juicer is set as the default app for audio cds and and its not installed. try installing it from Add/Remove Programs

---

### Post by Niko Johnson on 2009-10-15
well first when you install a tar.gz package you have to extract the package eaither by right clicking > extract here or using this code ```
 tar -xzvf filename 
``` then a new folder will pop up... go into that folder and run the installer in the terminal. and to get your graphics driver you need to install one first use this code as root. ```
 apt-get install nvidia-glx-180 
apt-get install nvidia-settings
nvidia-xconfig
``` you have a lot of questions and i only have so many answers... please specifiy exactly what you are trying to do

---

### Post by clive littlewood on 2009-10-15
Hi

Welcome to the forums.

Firstly try to seperate your problems into different threads with the appropriate heading.This way you will get people interested in your problems.

To answer your first question remember Linux is not windows so windows type files .exe and the like will not run on linux.

There is a program called WINE in the repositories which will emulate windows on linux for some programs.Check out winehq for info on the various programs it will run.

Hope this helps

Edit: Dam hailtech pipped at the post

Clive

---

### Post by Niko Johnson on 2009-10-15
oh and by the way .exe files will never work in ubuntu, there made for windows and windows only.... that damn windows and there monopoly empire!!!  trying to keep us down.

---

### Post by philinux on 2009-10-15
Hi,

1. Wine, install it from synaptic or add/remove. For info go here. [http://www.winehq.org/](http://www.winehq.org/)

3. What does it say under system>admin>hardware drivers. Should let you install the correct nvidia driver.

---

### Post by Niko Johnson on 2009-10-15
I agree with Clive littlewood, you have to split up your questions in order for people to be interested in your questions... we are all here to help but you have to know that long boring posts are not very interesting...

---

### Post by Bölvaður on 2009-10-15
please make 5 threads each with it's own topic. compilations might be popular for music cds but not on a support forum.

This will be very compressed:

1. open the .exe with wine
2. untar it (extract the files from the tar). it doesnt sound too geeky to double click on it and drag it outside of it. at least it doesnt to me. (btw if you are trying to install latest verision or something, it is a very specialiced software or you are making code changes to the program.... then this is the correct way. if not then you are better of installing software from Applications&#8594; Add/Remove or System &#8594; Administration &#8594; Synaptic Package Manager)
3. System &#8594; Administration &#8594; Hardware Drivers
If that doesnt work use the search here on the forums and find what others have done, if you cannot find anyone that has solved it make a dedicated thread, there is no need to doublicate a how-to for doing this over and over again.
4.like with normal removable media. shouldnt be any difference. this sounds _extremely_ weird, make a dedicated thread about it and provide more detailed symptoms and information about your cd drive and if it may be broken or not
5. it means this: ubuntu couldnt find cdda://sro/ (what ever that is) and failed to start “sound juicer” which by using the search in add/remove looks like a cd ripper.

---

### Post by Hospadar on 2009-10-15
Here's a good brief overview of how to do things from the command line.

You can (and should) google the commands if you don't know what they do - I promise none of them are malicious though

[http://martin.ankerl.com/2007/04/19/how-to-install-anything-in-ubuntu-condensed/](http://martin.ankerl.com/2007/04/19/how-to-install-anything-in-ubuntu-condensed/)

Here's the full version (probably better for a beginner): [http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

---

