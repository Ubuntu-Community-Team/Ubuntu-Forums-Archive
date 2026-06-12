---
title: "Wanting to try Ubuntu"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by Bob6249 on 2010-05-25
[FONT=Times New Roman][SIZE=3]Hi[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I’ve downloaded and burned Ubuntu 10.04 for desktops to a CD, and my questions are as follows.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] Should I have checked the file integrity of the download before burning a copy, if so what should I have checked it with?[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] I have partition of 20GB that has Windows XP on it, and the rest of the disk is a logical drive of 180GB.[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] Would I have to format the 180GB, to reduce its size to create some unallocated space for Ubuntu? [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]The computer that I want to try it on is an Advent T9101 Pentium 4[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]661FM2 series MS 7060 micro atx main board[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]SIS 661X chipset[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Audio AC97[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Realtek ALC655 S/W audio codec[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]The CD DVD drive is a Sony DVD RW DW-D18A[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Belkin F5D8053N wireless USB adapter.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Would it have any problem with this system?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Finally can you run Office 2003 on it?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]If it’s yes to all, then I might as well replace XP with Ubuntu.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]

---

### Post by ShawnLane on 2010-05-25
If you insert the installation disk there is an option that will let you check the cd for defects.

---

### Post by SlickRick on 2010-05-25
you can just run Ubuntu from the CD and try it without installing but that's a bit slower than running from a drive. You can also install it as an application for windows using wubi. That has its limitations too but is good for testing. As far as office goes, if you don't need anything fancy(like complex databases or scripting in spreadsheets), you can use open office which is compatible with MS office file formats and comes with ubuntu.

If you want to reduce the 180GB to something smaller, you would only have to format the bit you use for ubuntu. For example, if you have 140gb used and 40 free on that 180Gb partition, then you could shrink it to 140 and use the 40 for ubuntu. Btw, shrinking a drive would take a long time.

---

### Post by halitech on 2010-05-25
> **Bob6249 said:**
> [FONT=Times New Roman][SIZE=3]Hi[/SIZE][/FONT]
I’ve downloaded and burned Ubuntu 10.04 for desktops to a CD, and my questions are as follows.
1. Should I have checked the file integrity of the download before burning a copy, if so what should I have checked it with?
Yes and you would use the md5sum but I've never checked it before burning and never had a problem. Since you have it burned, boot from it and select the Check for defects option.
> 2. I have partition of 20GB that has Windows XP on it, and the rest of the disk is a logical drive of 180GB. Would I have to format the 180GB, to reduce its size to create some unallocated space for Ubuntu?
Yes but I would use the XP tools to do so
> 3. The computer that I want to try it on is an Advent T9101 Pentium 4
661FM2 series MS 7060 micro atx main board]
SIS 661X chipset
Audio AC97
Realtek ALC655 S/W audio codec
The CD DVD drive is a Sony DVD RW DW-D18A
Belkin F5D8053N wireless USB adapter.

Would it have any problem with this system?
the wireless might be an issue but nothing that we can't work around.
> 4. Finally can you run Office 2003 on it?
yes and no. it should run with WINE but it won't run natively.
> 
If it’s yes to all, then I might as well replace XP with Ubuntu.

I would suggest dual booting for a bit unless you have a second machine to use in case something happens.

---

### Post by ranch hand on 2010-05-25
If you are using 10.04 you will get a purple screen with a couple of cryptic symbols at the bottom of it.  Have a finger cocked to hit any key when that shows up and hit any key.  Then you will get the normal menu with the option to check the disk.

Do you mean that the 180Gb is an "extended" partition?

You can have only 4 Primary partitions on a drive.  An extended partition is a type of primary that allows you to have any number of "logical" partitions within it.

If it is an extended partition I would choose the manual option when you get to the partitioner in the install process and create a / (root) partition of 15 to 20Gb at the beginning of that extended partition, a swap partition twice the size of your ram at the end of the extended, and leave the rest of it for your /home partition.

---

### Post by flyfishingphil on 2010-05-25
> **Bob6249 said:**
> [FONT=Times New Roman][SIZE=3]Hi[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I&#8217;ve downloaded and burned Ubuntu 10.04 for desktops to a CD, and my questions are as follows.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] Should I have checked the file integrity of the download before burning a copy, if so what should I have checked it with?[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] I have partition of 20GB that has Windows XP on it, and the rest of the disk is a logical drive of 180GB.[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] Would I have to format the 180GB, to reduce its size to create some unallocated space for Ubuntu? [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]The computer that I want to try it on is an Advent T9101 Pentium 4[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]661FM2 series MS 7060 micro atx main board[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]SIS 661X chipset[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Audio AC97[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Realtek ALC655 S/W audio codec[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]The CD DVD drive is a Sony DVD RW DW-D18A[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Belkin F5D8053N wireless USB adapter.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Would it have any problem with this system?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Finally can you run Office 2003 on it?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]If it&#8217;s yes to all, then I might as well replace XP with Ubuntu.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
I would recommend that, if you just want to check it out, put in the cd, restart, check the disc, then hit the install/run choice. You can "test drive" it for a while before installing, but that is limited in operation and fairly slow compared to the installed version.

If you want to install you have the choice of doing a total format of the HD before installation, or setting it up for dual boot. I would do the dual boot and test it for a while to make sure it's what I want to use. You can then do an external save of everything you have built in Ubuntu and just install the cd, reboot and do a total install if you decide that is what you want.

Regarding the XP, MS Office, and anything else that requires Windows to operate properly You can add VirtualBox to Ubuntu, install XP there, then add in anything else that requires Windows to operate properly. This seems to work much better than the WINE program I've tried. 

Another option, for MS Office, is the Open Office that comes with Ubuntu and is available on the net at[www.openoffice.org]("http://www.openoffice.org"). You can get that right now, it's free, and try it out. (I've used this for a few years now and prefer it over MSO. You can save everything you do in multiple formats so it can be opened by just about anybody.) You don't need Windows/VBox to use this in Ubuntu.

As you "play around" in Ubuntu you'll find just about everything you need to do just about anything you want.

Couple of pointers I wish I'd gotten to start with. If you are doing something and it calls for entering something like *"sudo apt-key get"* that is done by going to Application > Accessories > Terminal and type it in, hit enter and your info will show up with a blinking indicator at the end. Here you type in your password and hit enter. (You won't see it as you type it in.) It will then do as directed.

If you want to look around at what software is the "recommended" just click on Applications, scroll down to bottom of column to Ubuntu Software Center and start looking around.

Just FYI, I just went totally Ubuntu on my laptop, but will also be using the VBox and XP so I can do things like connect to the net using my cell phone, keep my Magellan GPS up to date. You can also build "shared folders" to "share" info between the Ubuntu and the XP in VBox.

Long winded but hope this helps you out some.

---

### Post by priley95 on 2010-05-25
hi there,
Unless you have driver problems, then there should be minimal problems.
You can't run Office 2003 as such, but there is an Open-Source Alternative, called OpenOffice

Thanks

---

### Post by dustinmarlowe56 on 2010-05-25
First run the live CD to see if everything works. It should.

Microsoft Office can be installed in Ubuntu. I work in an office where I have to handle .docx and such files often and I use Ubuntu so I had to install Office on my laptop. It works Flawlessly for me in Wine on 10.04. 

As far as functionality and replacing XP goes.....I say go for it. If you don't like it and dont' have your XP install disk then there are always XP isos floating around on the internet that you could use with your XP product key to reinstall the system. You will more than likely not lose any functionality but gain some and a lot of computing power. I can count a whole lot of stuff that is possible to do on Ubuntu that is either not supported or way too difficult to do in Windows while I have only run across two things that I cannot seem to do in Ubuntu: 1) stream stuff on Netflix (wine + firefox + microsoft silverlight = crash, apparently Netflix wants to put out the code for it to work with ubuntu as soon as they can get their contracts right) and 2) use POD Farm from Line6 to play guitar (Wine does not support drivers and Line6 doesnt have enough backing to support porting stuff to linux since the software is relatively new). However both of these issues can be dealt with by running a minimal XP install inside of a virtual box.

---

### Post by Bob6249 on 2010-05-25
[FONT=Times New Roman][SIZE=4]Thanks for the all replies.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4] I think I’ll try the dual boot for a while.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]Can’t format the logical drive, the misses won’t let me, because she’s filled 100GB with c - - - , I’m mean stuff that’s irreplaceable to the boss.  [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]Just notice that there are 2 options with the install CD to resize the partition.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]Automatic and manual, how do they work? [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]Would they resize the partition without formatting the logical drive?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]And more important are they safe to use?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]I wouldn’t want to loose any precious data.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]

---

### Post by musicman10489 on 2010-05-25
I personally had an issue with the Automatic. I told it to install Ubuntu side-by-side with windows...but unfortunately it ended up replacing windows instead. Keep in mind this was a couple releases ago at 9.04 and this is just MY experience. Everyone else may have had a perfect 'Automatic' experience. I personally prefer the manual option, but that is just one man's humble opinion :]

---

