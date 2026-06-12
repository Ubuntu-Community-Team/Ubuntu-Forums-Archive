---
title: "Final hurdles before making the switch"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by Bert69 on 2010-10-08
I am about to buy a new computer this weekend and my current Windows 7 is OEM so I cannot transfer it to the new one.
I have been looking at linux for years now, trying it now and again. I am slowely approaching an age where learning new things become harder, but luckily I have a long history of computers and even some programming. In many ways linux reminds me of my old, beloved Amiga.
Since I already switched to open source software (gimp, openoffice, etc.) the last (logical?) step would be to switch to ubuntu now. But I after playing with it for a few weeks now, I still have some questions which I hope someone can answer me.

1) I use a Wacom Intuos 4 mainly because of bad RSI. The pen is my best friend. I use it heavilly everywhere. It seems to work ok and I can see improvements in support since the last time I tried Ubuntu (Dapper Drake it was I think). But it still doesn't "feel" as smooth and solid as it does in Windows. Does anyone have prolonged experience with the Intuos 4 on Ubuntu to be able to tell me if it woks without hickups? Also, what does the improvement curve look like for the drivers, are major improvements being made quickly these days or is it slowely progressing and reaching an endpoint?

2) I like my software to be of the latest version. As I understand it, you cannot just download the latest version and install it, but have to wait for the version to be updated in the package right? For example, I have been test driving Firefox 4 for a while now and am avidly learning Blender 2.5x neither of which is in the package manager?
Now I understand I can somehow install them manually, but I have yet to find easy to follow tutorials for that? Which also brings me to the next question:

3) I am a bit of an obsessive purist when it comes to my files and programs. I have a very clean directory structure where documents, data and programs are all separate. In fact I would like my files and data to be on a separate disk all together if possible? In fact I suspect I have a personality disorder when it come to this, since I can get really upset when some program just creates a directory or file somewhere I don't want it. Over the years I found Windows has improved very much in that regard, how is Ubuntu in that area?

4) My spouse has a laptop with windows 7 on it, we share a printer which is connected to my computer. Can we still share this printer when I switch to Ubuntu?

5) Also, it is a Samsung SCX-4521 with a scanner built in. Will that still work?

6) I don't game much but I do have an account on Second Life. I am still not sure if I should get an ATI or an nVidia card? Which is better supported in Ubuntu?

Ok, sorry for the mountain of questions ;-)

---

### Post by Andy06 on 2010-10-08
1) Some drivers for peripherals (especially niche ones) do not have full fledged support if the manufacturer itself does not supply its own drivers. Even touchpad and mouse behaviour is better in Windows for a lot of peripherals.

2) Installing and updating commonly used apps is a pain. Sadly, there is no easy way around it. No solution. Update management is just a pain
[Unless you consider Terminal/PPAs/custom adding repositories etc easy]

3) The internal directory structure of most OSes is a nightmare (it has to be, there's a whole OS in there :P). I find Mac OS X the cleanest by far. Windows and Linux are quite ugly when you dig down (go into Appdata in Windows and you'll know what I mean). I would say Windows has depreciated over the years actually. Apps in Vista/7 install files in MORE places than they did under XP. Linux apps too install things in a gazillion places (and also leave behind a lot upon uninstalling). Install a program and you will probably find related files in like 12 different locations (similar to Windows).

Just make another parition and put all your personal files (Docs, Pics, Music, Downloads, Videos) there. The native tools in Ubuntu allow very easy partitioning and disk management. 

4) Probably

5) Possibly :P

6) If you don't game (or have other specialist needs), why go for a discrete card at all? AMD (ATI) and Intel's integrated solutions are perfectly adequate for ALL non specialist tasks. Compiz will work out of the box smoothly with Intel integrated graphics. Re: Nvidia, it is fully supported and drivers are updated. AMD/ATI, I am not sure but I think they are supported too.

---

### Post by slooksterpsv on 2010-10-08
4) If it doesn't, there's a program called iscan that will allow you to scan using that scanner.

---

### Post by beew on 2010-10-08
> **Andy06 said:**
> 

2) Installing and updating commonly used apps is a pain. Sadly, there is no easy way around it. No solution. Update management is just a pain
[Unless you consider Terminal/PPAs/custom adding repositories etc easy]

It is only a pain if you install from a source tarball. I find it quite easy if you get .deb files (like windows installers except it will pull in the dependencies if they are not already installed). There are also other tar packages which may require you to run an install script or something like that, they are more complicated than the .deb files but they aren't that bad either. But my choice of keeping up to date would be to use PPAs because of their seamless integration into the software manager, which I think is one of the greatest thing in Ubuntu, the catch is that the contents in the official repo may get old and outdated because they don't get feature updates, but this is remedied by PPAs (I install most of my apps through ppas) Now even in PPAs you still won't get the latest because it takes time to package, but I can wait for a few weeks, that is no biggy. Adding PPAs to your source list is very easy.

> 


3) The internal directory structure of most OSes is a nightmare (it has to be, there's a whole OS in there :P). I find Mac OS X the cleanest by far. Windows and Linux are quite ugly when you dig down (go into Appdata in Windows and you'll know what I mean). I would say Windows has depreciated over the years actually. Apps in Vista/7 install files in MORE places than they did under XP. Linux apps too install things in a gazillion places (and also leave behind a lot upon uninstalling). Install a program and you will probably find related files in like 12 different locations (similar to Windows).

It did seem so in the beginning but once I get used to it I realized there is certain logic to how files are organized. In Linux the programs are very tightly fit together (that's why it is so much leaner than Windows) and there are "pieces" which are shared by many programs and you only need one copy so it wouldn't make sense to keep a folder for each program separately with many overlaps like in Windows. 

So yes, the pieces are installed in different places because the files are grouped by functions rather than which programs they come from.

There are clean up tools one can use to remove left over such as bleachbit and Ubuntu tweak, you can also use the command line or Synaptic for cleaning if you choose.
  
The only things that don't get cleaned in the ways described above are things you install in your home directory, but usually you can simply delete them.

---

### Post by Bert69 on 2010-10-08
Thank you all for the quick replies...wow.

So far, not very promising though :-(

As for the programs dumping files all over the place. Yes, I think this is true for most (if not all) OSes. I don't really care if a program installs files in many different directories, as long as it makes sense. In that respect I hope Linux will do better than Windows (Which just dumps dll's all over the place).

Truth be told, I could live with a "messy" hard disk though, but I could never live without my Wacom, so I am really hoping someone can give me a more definitive answer on that.

As for the videodriver, I guess I will go with nVidia then. It seems Second life like nVidia better than ATI as well, so that is an advantage.

I guess my two remaining main questions are the one about the Wacom and the ability to share a printer with a windows computer.

---

### Post by beew on 2010-10-08
> **Bert69 said:**
> 

I guess my two remaining main questions are the one about the Wacom and the ability to share a printer with a windows computer.


Apparently Wacom would work but it may take a bit of work. :)

[http://ubuntuforums.org/showthread.php?t=1120029&page=24](http://ubuntuforums.org/showthread.php?t=1120029&page=24)

---

### Post by TCHebb on 2010-10-08
3) You can make a second partition for your files and mount it to /home. Linux file structures are quite confusing at first, but there is a [standard]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") that all (I think) Ubuntu packages follow. User-specific program data is stored in hidden folders in your home folder, but other than that, a separate home partition will keep your programs and data seperate.

---

### Post by roger_1960 on 2010-10-08
Hi

Assuming both computers are connected to the same LAN, you should be able to share any printer.  Need to check that its supported by linux though.  A few quick enquiries suggest that it probably is although you may need to dig to find the right drivers.  Could it be connected to your wifes Win7 PC and be shared to your Ubuntu PC to save messing around with drivers?

---

### Post by Favux on 2010-10-08
Hi Bert69,

You can definitely get your Intuos4 working, including the OLED's.

---

### Post by Bert69 on 2010-10-08
> Apparently Wacom would work but it may take a bit of work. :)

I know it works :), it just doesn't work as well as I am used to. I am mainly wondering how fast and how effective the development of the drivers are.

> Could it be connected to your wifes Win7 PC and be shared to your Ubuntu PC to save messing around with drivers? 	

Unfortunatly not. But I have found some info on this printer as well stating it can be used, so I am going to assume I will get it to work.

However, in my search for info i found another possible problem which scares me more:

I live in an area of the world where power outages are not uncommon. On avarge we get an unannounced power outage about 30 times a year. In Windows it is hardly a problem and when it does corrupt something (happened once so far) it just runs the "repair OS" thingy.
I have read however that linux (esp. ext4) drives are not as sturdy in those situations? Any experiences/advice in that area? I must say this scares me a lot.

---

### Post by Bert69 on 2010-10-08
> **Favux said:**
> Hi Bert69,

You can definitely get your Intuos4 working, including the OLED's.

Ah, thank you.

---

### Post by lovinglinux on 2010-10-08
> **Bert69 said:**
> 2) I like my software to be of the latest version. As I understand it, you cannot just download the latest version and install it, but have to wait for the version to be updated in the package right? For example, I have been test driving Firefox 4 for a while now and am avidly learning Blender 2.5x neither of which is in the package manager?
Now I understand I can somehow install them manually, but I have yet to find easy to follow tutorials for that? Which also brings me to the next question:

The repositories are only updated with security patches. If you want the latest versions, then there are several ways of installing them, for example from the PPA repositories as already mentioned.

For Firefox you can simply download the binaries from Mozilla, extract and use. I use Firefox 4 since beta 1. See my [Firefox 4 tutorial]("http://firefox-tutorials.blogspot.com/2010/08/firefox-4-download-install-customize.html").

> **Bert69 said:**
> 3) I am a bit of an obsessive purist when it comes to my files and programs. I have a very clean directory structure where documents, data and programs are all separate. In fact I would like my files and data to be on a separate disk all together if possible? In fact I suspect I have a personality disorder when it come to this, since I can get really upset when some program just creates a directory or file somewhere I don't want it. Over the years I found Windows has improved very much in that regard, how is Ubuntu in that area?

Ubuntu is fantastic in that area. You have a separate partition for /home, in which will be saved all your personal files and configurations. If you need or want to reinstall Ubuntu, then you don't lose your personal files or personal configurations, since system files will be kept separate. So you don't need to reconfigure your theme, panels and other personal stuff. In fact, you can mount any folder on a different partitions and you can also use symlinks to organize your folder structure without actually moving the files physically.

> **Bert69 said:**
> However, in my search for info i found another possible problem which scares me more:

I live in an area of the world where power outages are not uncommon. On avarge we get an unannounced power outage about 30 times a year. In Windows it is hardly a problem and when it does corrupt something (happened once so far) it just runs the "repair OS" thingy.
I have read however that linux (esp. ext4) drives are not as sturdy in those situations? Any experiences/advice in that area? I must say this scares me a lot.

I live in an area where we also have many power outages, I guess more than 30 a year. I use ext4 and I never had any problems. I never lost anything due to corruption and never had to re-install or recover the OS. Nevertheless, if I need to do so, I can have my system back in a couple of hours, just like it was before, thanks to the /home partition separation.

---

### Post by Andy06 on 2010-10-08
> **beew said:**
> It is only a pain if you install from a source tarball. I find it quite easy if you get .deb files (like windows installers except it will pull in the dependencies if they are not already installed). There are also other tar packages which may require you to run an install script or something like that, they are more complicated than the .deb files but they aren't that bad either. But my choice of keeping up to date would be to use PPAs because of their seamless integration into the software manager, which I think is one of the greatest thing in Ubuntu, the catch is that the contents in the official repo may get old and outdated because they don't get feature updates, but this is remedied by PPAs (I install most of my apps through ppas) Now even in PPAs you still won't get the latest because it takes time to package, but I can wait for a few weeks, that is no biggy. Adding PPAs to your source list is very easy.

The problem with PPAs is that they are anything but seamless. I have a thread somewhere collecting all the various PPAs for all the common apps and it was a real pain. Many apps do not have an "official" PPA and you have to access someone's personal PPA and even then you have to go out and find them first. It is so much easier on Windows and Mac OS X where you just "Check for Updates" and it does everything by itself in most apps.

It is not so much the installing that is broken but the updating (specifically feature/new version updating). 

To be honest, I have absolutely no idea why feature updates are not implemented. I have read the reasons behind it and find them completely unconvincing. It is a major feature that is expected by users of any OS and I think the only reason it isn't a bigger issue is 
a)People don't notice because they take it for granted that updates are indeed provided
b)Ubuntu itself updates on a 6 month cycle so you don't fall multiple versions behind major apps

---

### Post by SuaSwe on 2010-10-08
Regarding the Wacom, maybe have a read on [http://linuxwacom.sourceforge.net/](http://linuxwacom.sourceforge.net/), the Linux project homepage, unless you haven't already. :) The drivers look to be updated a couple of times a year, judging from the download page.

---

### Post by Bert69 on 2010-10-09
I want to thank you all very very much. I guess it is time to make the switch. Esp. hearing from someone who also suffers power outages and not having issues sets my mind somewhat at ease. At least until I can find a shop that sells UPS's (you would think that in a country that has so many power problems they would be popular, but they aren't).

So expect a lot of stupid noob questions from me next week when I have made the switch ;-)

Thanks again.

---

