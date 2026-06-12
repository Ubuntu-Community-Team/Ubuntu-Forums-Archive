---
title: "Newbie needs help please"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by c.oke on 2009-07-27
Hello Everyone, my names Carol and I'm very new to computers and Ubuntu.
I think I'm going to need lots of advice but here goes for the 1st bit,
When I try to install anything from a cd this is what comes up.[ATTACH]122585[/ATTACH]
can anyone help me with this.
fank u fank u fank u :confused:

---

### Post by Nburnes on 2009-07-27
That's a Windows executable which can only be run in Wine and a few other software's.

What is it that you are trying to install? There is a good possibility that there is an open source software that will get the job done the same if not better?:D

---

### Post by khelben1979 on 2009-07-27
It looks like you are trying to install Windows software using the [Synaptic Package Manager]("http://en.wikipedia.org/wiki/Synaptic_package_manager"). If that's true, it won't work.

In order to install Windows software you'll just open up the setup file from the disc and then let Wine take care of it. The Wine application makes this possible.

If you intend to install the Nero software for Linux, you need a Linux version of this program which do exist.

---

### Post by Bucky Ball on 2009-07-27
You need to look for open-source software alternatives. Windows programs will not work (unless you use another application called Wine to run it which has varying results). If you need to run those programs advisable to dual-boot with Windows.

About the only CD you will ever use in Ubuntu is the installation CD. Everything else will happen online; printers, scanners, etc. If it doesn't 'just work' there is usually (but not always) a work-around or driver you will be able to download.

So, save the install disks for windows and have a look around. 

Applications->Add/Remove

or

System->Administration->Synaptics Package Manager

That is where you will get your applications, not from CD. 

Have fun. :)


* As mentioned in the previous post, yes you will need Nero Linux version and it is available. But there are plenty of alternatives. Try Brasero (Applications->Sound & Video (or whatever yours says)) for fast and easy disk copy or burn. Sound-juicer can be set up to open when you insert a CD and this is a great, simple ripper.

---

### Post by wojox on 2009-07-27
Here is a wine doc:

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by theozzlives on 2009-07-27
I personally like to use Nero Linux. The CDs you get with hardware (ie: CD Burners) is normally Windows software, and useless to Linux users.

---

### Post by Claus7 on 2009-07-27
Hello,

so as all the people here mentioned to you, you are trying to install a windows application (exe file) in linux. This can be accomplished via two similar ways:
either via wine (windows emulator) [which you can install easily via synaptic package manager] 
or via crossover (windows emulator too) which does more or less the same thing.

The latter is better for office applications, whereas the first is ideal exempli gratia for games.

Now, you can install such packages and amulate them, yet when you are able to find a nice and open source alternative, my advice would be: go for it!

My proposal to the subject would be the program k3b (System -> Administration -> Synaptic Package Manager) and type in the box the string I just gave you. This program can work both in gnome and kde and it is simply amazing (at least to write cds and dvds that will play both in windows and linux).

Welcome aboard,
Regards!

---

### Post by Bucky Ball on 2009-07-27
One problem with k3b for me is it doesn't handle FLAC files and my library is 80% FLAC. Has there been a change or work-around in that?

---

### Post by Claus7 on 2009-07-27
Hello,

> **Bucky Ball said:**
> One problem with k3b for me is it doesn't handle FLAC files and my library is 80% FLAC. Has there been a change or work-around in that?

Forgive my ignorance, yet up to your post I wasn't aware about flac files. Yet, googling around a little this is what I have come accross:
[http://mandrivausers.org/index.php?/topic/38634-cant-burn-audio-cds-using-flac-files-in-k3b/](http://mandrivausers.org/index.php?/topic/38634-cant-burn-audio-cds-using-flac-files-in-k3b/)

Somewhere it sais about installing every package that has to do with flac files, yet in mandriva. It might be some kind of help.

edit: also take a look at this:
[http://ohioloco.ubuntuforums.org/showthread.php?t=1166771](http://ohioloco.ubuntuforums.org/showthread.php?t=1166771)

It might in newer versions that to be fixed. In k3b site it has optional support to flac files.

Regards!

---

### Post by Bucky Ball on 2009-07-27
> **Claus7 said:**
> Hello,



Forgive my ignorance, yet up to your post I wasn't aware about flac files. Yet, googling around a little this is what I have come accross:
[http://mandrivausers.org/index.php?/topic/38634-cant-burn-audio-cds-using-flac-files-in-k3b/](http://mandrivausers.org/index.php?/topic/38634-cant-burn-audio-cds-using-flac-files-in-k3b/)

Somewhere it sais about installing every package that has to do with flac files, yet in mandriva. It might be some kind of help.

Regards!

Thanks for that. I try and stick with the most lightweight I can get so quite happy with Gnome Player which handles them fine. Most OSS media software does (Free Lossless Audio Codec). (sorry, c oke, getting a little off topic! Welcome to Ubuntu and the forums ... ) :)

---

### Post by rannable on 2009-07-27
Hey Carol, if you go to the Nero website there is a linux version you can download for Ubuntu, here is the link [http://www.nero.com/eng/linux3.html](http://www.nero.com/eng/linux3.html)

Thanks
Rob

---

### Post by Ms_Angel_D on 2009-07-27
Hello c.oke, and welcome to the forums.


I notice you said you we're new to computers in general. Just to help you not feel so lost, Here's a bit of information.

To give your computer a friendly face for you to look at there are interfaces, between hardware(computer) and the end user(you). These are called Operating Systems. The operating system(OS) your using is a linux based OS. The Software your trying to install is intended to run on an Windows Based OS. This is why your running into problems when you try to load it.

As others have mentioned there does exist software, that attempts to close the gap and allow **SOME** but not all software that is intended for windows to run on linux. However your best bet is to look for linux based software which will accomplish the task you have in mind.

If you could list down some of the needs you have, myself (and others I'm sure) will help you to find the appropriate software.

---

### Post by c.oke on 2009-07-28
> **Ms_Angel_D said:**
> Hello c.oke, and welcome to the forums.


I notice you said you we're new to computers in general. Just to help you not feel so lost, Here's a bit of information.

To give your computer a friendly face for you to look at there are interfaces, between hardware(computer) and the end user(you). These are called Operating Systems. The operating system(OS) your using is a linux based OS. The Software your trying to install is intended to run on an Windows Based OS. This is why your running into problems when you try to load it.

As others have mentioned there does exist software, that attempts to close the gap and allow **SOME** but not all software that is intended for windows to run on linux. However your best bet is to look for linux based software which will accomplish the task you have in mind.

If you could list down some of the needs you have, myself (and others I'm sure) will help you to find the appropriate software.



Thanks to all who replied.Much appreciated, I'll get the hang of it eventually,( I hope :confused:,)

---

### Post by Bucky Ball on 2009-07-28
> **Ms_Angel_D said:**
> 
To give your computer a friendly face for you to look at there are interfaces, between hardware(computer) and the end user(you). These are called Operating Systems.

Linux will run quite happily without a friendly face as will DOS and others. The friendly bit between you and the hardware is called the Desktop Environment or Desktop Manager which is used to communicate with the OS then hardware. Ubuntu uses Gnome to do this, as you would know. Gnome is the desktop environment we use to communicate with the hardware through the OS (friendly). The other option for communication is the terminal (unfriendly at first but gets friendlier!).  

Just thought I'd mention it. :) ):P

In Windows I think there are two choices of environment - classic and the other one - and some tweaks.
In Ubuntu there are a cast of thousands (well, a lot of desktop environments to try anyways).

Good luck, have fun, explore, experiment!

---

### Post by nullmind on 2009-07-28
It really is a better option to find Open Source alternatives to older programs that you used in Windows. As you will also learn from experience, there are many things you can do in Linux that don't require a bulky application. For example, if you want to burn an audio CD you can open up **Rhythmbox**, make a playlist, and press Burn. If you want to burn an ISO (like you did if you downloaded the Ubuntu CD) you can just right-click the file and select "Write to Disc".

---

### Post by Ms_Angel_D on 2009-07-29
> **Bucky Ball said:**
> Linux will run quite happily without a friendly face as will DOS and others. The friendly bit between you and the hardware is called the Desktop Environment or Desktop Manager which is used to communicate with the OS then hardware. Ubuntu uses Gnome to do this, as you would know. Gnome is the desktop environment we use to communicate with the hardware through the OS (friendly). The other option for communication is the terminal (unfriendly at first but gets friendlier!).  

Just thought I'd mention it. :) ):P

In Windows I think there are two choices of environment - classic and the other one - and some tweaks.
In Ubuntu there are a cast of thousands (well, a lot of desktop environments to try anyways).

Good luck, have fun, explore, experiment!

I know that, but I was trying to make it as easy as possible for the uninitiated ;).

---

