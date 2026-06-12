---
title: "I don't have the foggiest"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by IrishEddieOHara on 2008-12-17
clue of what I am doing.  I have heard so many things wonderful about Linux that I wanted to try the system.   Now I am up to my ears in trouble and need some help.

1.  Have Linux installed on a disc that formerly had Windows XP on it.  Is Windows still in the hard drive?  I didn't use any sort of dual boot.  I am trying to build a computer for my daughter to keep her the heck off mine all the time.

2.  I bought a blank hard drive at my local computer store.  I put Linux on it as my first install.  Then I realized that nothing which is Windows compatible will run on Linux.  I learned this by trying to install Corel Word Perfect on the drive.  So now what do I do?  Can I install Windows on top of Linux?   How?  

3.  I tried to install Windows on the hard drive in question # 2.  Wouldn't go.  Got the "blue screen of death about 10 minutes into file writing.  So how can I reformat the hard drive and get Linux out so I can start all over again?  Or is that even necessary?

4.  I was scanning the site and noticed people mentioning about making a boot disc for DOS.  I can download an executable file to my computer, but when I go to open it, I get a warning that opening the file to transfer it to C might screw everything up.  Will it? 

5.  Firefox keeps dropping my downloads onto its own page.  How do I open the download to my CDROM without messing up everything that is running?   In other words, since it is an executable file, if I hit the "open" button, will it try to execute a boot to DOS?

Thanks for any help/advice you can give.  I am real, REAL new to Linux, but I would like to learn about the system.  Everyone I have ever talked to about it just LOVES it.

Irish

---

### Post by aheckler on 2008-12-17
> **IrishEddieOHara said:**
> I have Linux installed on a disc that formerly had Windows XP on it.  Is Windows still in the hard drive?

No, it's been overwritten by Ubuntu. It's possible that you could recover some files if anything important was on there, but it's hit-or-miss.

---

### Post by aheckler on 2008-12-17
> **IrishEddieOHara said:**
> I bought a blank hard drive at my local computer store.  I put Linux on it as my first install.  Then I realized that nothing which is Windows compatible will run on Linux.  I learned this by trying to install Corel Word Perfect on the drive.  So now what do I do?  Can I install Windows on top of Linux?   How?

Windows applications are not compatible with Linux. You can run a few of them under WINE, but that might be above your level as of now. Try searching for programs you need in Add/Remove Programs.

---

### Post by starcannon on 2008-12-17
> **IrishEddieOHara said:**
> clue of what I am doing.  I have heard so many things wonderful about Linux that I wanted to try the system.   Now I am up to my ears in trouble and need some help.
No worries, its new to you, so be sure to give yourself time to learn the linux way of doing things. You chose a great distribution as it has in my opinion the friendliest forums on the web(breaks own arm)
> 
1.  Have Linux installed on a disc that formerly had Windows XP on it.  Is Windows still in the hard drive?  I didn't use any sort of dual boot.  I am trying to build a computer for my daughter to keep her the heck off mine all the time.
If you selected "use entire disc" during the partition manager portion of the install, or just blindly clicked through it, then windows is likely no more.
> 
2.  I bought a blank hard drive at my local computer store.  I put Linux on it as my first install.  Then I realized that nothing which is Windows compatible will run on Linux.  I learned this by trying to install Corel Word Perfect on the drive.  So now what do I do?  Can I install Windows on top of Linux?   How?  
Linux has its own set of softwares (look in System>Administration>Synaptic Package Manager; think of that as the worlds largest free software outlet), almost all of which are cost free. Open Office is our word processor; give it a try, if it won't work out for your needs then we can move on to a "how to run windows programs on linux"(there are a few methods)
> 
3.  I tried to install Windows on the hard drive in question # 2.  Wouldn't go.  Got the "blue screen of death about 10 minutes into file writing.  So how can I reformat the hard drive and get Linux out so I can start all over again?  Or is that even necessary?
If you want to dual boot, it is a good idea to install windows first, then install linux second; it is possible to do it in the reverse order, but is much more complicated. Unless one needs 3d intensive windows only video games(even some of these will run on linux, for instance World of Warcraft works fine under a windows compatibility layer called WINE), then I would recommend virtualization and just let linux have the whole hard drive.
> 
4.  I was scanning the site and noticed people mentioning about making a boot disc for DOS.  I can download an executable file to my computer, but when I go to open it, I get a warning that opening the file to transfer it to C might screw everything up.  Will it? 
I'll have to pass on this one, not sure what you mean, or what your trying to do, more information please?
> 
5.  Firefox keeps dropping my downloads onto its own page.  How do I open the download to my CDROM without messing up everything that is running?   In other words, since it is an executable file, if I hit the "open" button, will it try to execute a boot to DOS?
I don't follow please describe in more detail what your doing.
> 
Thanks for any help/advice you can give.  I am real, REAL new to Linux, but I would like to learn about the system.  Everyone I have ever talked to about it just LOVES it.
You will love these forums; its a great community, friendly people, and once you get over the installation blues and have your sense of direction again, I think you'll love it too.

What works, what doesn't work?
All that said, what is the brand/model of your computer?
Can we get a hardware list?
To get a detailed list of its hardware, open a terminal:
Applications>Accessories>Terminal
and enter:
```
sudo lshw > ~/Desktop/hardware.txt
```
You'll now find on your desktop a document with a detailed list of your hardware; please copy paste that list into a set of code tags if your in need of hardware device support.

GL and have fun !

Oh and let me say:
WELCOME TO UBUNTU!):P

---

### Post by abn91c on 2008-12-17
windows is probably gone, boot from the cdrom to the ubuntu live cd then install it. if you are not trying to recover XP then select use entire disk option during install
Linux have many windows equivalent programs, it comes with openoffice.org office suite by default, which is compatible to MS Office XP/2003/2007 so you wont need corel office.

---

### Post by mbsullivan on 2008-12-17
Hi IrishEddieOHara,

I'm glad to hear that you heard good things about Linux, and were open to trying it. 

> Have Linux installed on a disc that formerly had Windows XP on it.  Is Windows still in the hard drive?  I didn't use any sort of dual boot.  I am trying to build a computer for my daughter to keep her the heck off mine all the time.

No, Windows is not still on the disc. I think that Ubuntu should work perfectly for a child's computer. Also, children tend to be much quicker to learn new programs.

> I tried to install Windows on the hard drive in question # 2.  Wouldn't go.  Got the "blue screen of death about 10 minutes into file writing.  So how can I reformat the hard drive and get Linux out so I can start all over again?  Or is that even necessary?

What version of Windows are you trying to install? It should be possible to reformat the harddrive and install Windows onto it with just the Windows installation CD.

> Firefox keeps dropping my downloads onto its own page.  How do I open the download to my CDROM without messing up everything that is running?   

I'm confused. Are you running Ubuntu off of the Live CD? 

> In other words, since it is an executable file, if I hit the "open" button, will it try to execute a boot to DOS?

While I don't quite understand the situation, it would never try to boot to a boot disc if you try to "open" it from a browser. So, "no".

> Then I realized that nothing which is Windows compatible will run on Linux. 

As others have said, Linux (and, therefore, Ubuntu) is not Windows, and will not run any Windows programs. This being said, there are programs that run under Linux that will do just about everything you can do under Windows, and more.

If you need a specific program to run perfectly for some reason, then you are constrained to stay with Windows. There is a program, called Wine, that can be used to run some programs under Linux. However, I strongly urge you to not use it extensively or as a crutch for converting to Linux -- it does not run programs perfectly, and in general should only be used if there is a single Windows application that you cannot live without, and are okay with some bugs in the program.

In summary, Ubuntu should work well for your purposes, but would require you (or your daughter) to learn a whole new set of programs. These programs, for the most part, should be free of cost and tend to be easy to learn (at least those made for general purpose computing).

If you want to move back to Windows, this should be possible without using a DOS boot disc. Booting to the installation CD, reformatting the disc to NTFS or FAT (this part is importanat), and then installing Windows onto the freshly formatted disc should do the trick.

Let me know if you have any questions, or if anything in my response confuses you.

Mike

---

### Post by mrbiggbrain on 2008-12-17
you could use gparted live cd to reduce the size of your linux partition, then use the windows install cd to reinstall in that space by makeing a NTFS partition, then you could setup the xp/vista boot loader NTLDR to boot off the other partiton also, then youll get a nice prompt that asks you, windows or linux? everytime you boot

---

