---
title: "Encore ENUWI-G or SMC2862W-G"
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by Hendrick on 2007-05-13
Hello.

I'm newer to linux.  I tried a different version of it, and none of my cards were supported.  I tried here, and my laptop works out of the box.  However, the same cannot be said for either of my two wireless cards, Encore ENUWI-G or my SMC2862W-G.

I'm having an issue even installing the NDIS Wrapper using the Terminal.  Everytime I type:
```
sudo ndiswrapper -i 'linktodriver.info'
```
It always prompts me for a password.  However, it won't let me type it.  I hit the button on my keyboard, but nothing happened.

Any ideas?

Thanks so much!

---

### Post by chili555 on 2007-05-13
Your sudo password is not displayed, not even as ***** so, as a security measure, no one even knows the length of your password ("Six characters, it could be his last name.") Just type it in and press enter. It will take if it's correct or tell you if it's not.

---

### Post by Hendrick on 2007-05-14
Wow, I feel a little stupid.  Thanks.

But now after I type my password, I get this:

> sudo: ndiswrapper: command not found

---

### Post by chili555 on 2007-05-14
How did you install ndiswrapper? From Synaptic or apt-get? Did you follow a how-to? Could you give us the link to the guide you followed? Thanks.

---

### Post by Hendrick on 2007-05-14
Congratulations on your 1000th post.

[https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless)

Step one...  :D

---

### Post by chili555 on 2007-05-14
Thanks! My keyboard is all shiny and my fingers are hurtin'!

Did you take step zero first:> To install ndiswrapper, install the package ndiswrapper-utils (see Add Applications). This package is provided on the Ubuntu CD. If you have access to the Internet, you can also optionally install a graphical tool, ndisgtk from the Universe repository (see [https://help.ubuntu.com/7.04/add-applications/C/#extra-repositories]("https://help.ubuntu.com/7.04/add-applications/C/#extra-repositories"))...and 0 1/2:> In order to set up ndiswrapper, it is necessary to obtain the Windows driver for your wireless card. Generally, the best way to do this is from the CD supplied with your wireless card. You should copy two files to the same place on your computer, one ending in .SYS and one ending in .INF. If you find any files which end in .BIN, also copy those. If you are not able to find the right files, and have alternative access to the Internet, you may be able to obtain help from the ndiswrapper website.They often say 'step 1', but it may not be!

---

### Post by Floppyjoe on 2007-05-14
The Encore ENUWI-G works well in edgy and feisty with WPA encryption for me.

To install ndiswrapper just click on System/Administration/Synaptic Package Manager
Then Click on Edit/Add CD-rom and follow the directions using your Ubuntu Install Cd.
The click on reload.
Then search for ndiswrapper and install ndiswrapper-common and ndiswrapper-utils.


I have a howto in my signature for the Encore ENUWI-G 54 Mbps adapter.

---

### Post by Hendrick on 2007-05-14
Hi

Ok, I get lost a little early.

> If you don't have internet connectivity you can use the Ubuntu Edgy 6.10 Install disk to load ndiswrapper to your computer by clicking on System/Administration/Synaptic Package Manager. Next click on Edit/Add CD-ROM then use the Ubuntu Install disk to load the ndiswrapper utility to your system by clicking reload. Then search for ndiswrapper. 

So, here I would put in my Live CD.  Then I go to Edit, Add CD Rom.  I hit OK at the first popup, that tells me to insert a disc.  Then it ask me to insert another CD, and I click No.  Now what?  When I hit the reload button, it tried to download off of the internet.

I'm using 7.04

---

### Post by Floppyjoe on 2007-05-14
It's trying to see if it can access the online repositories which will fail but you should be able to do a search for ndiswrapper after you did the reload button and it would search the cdrom for it.

---

### Post by Hendrick on 2007-05-15
Ok, I did the search, but nothing comes up.  What is the exact name of the package?  Is it simply "ndiswrapper"?

And let's make sure I'm using the right CD.  I'm doing the search from the Ubuntu CD, not the CD that came with the driver, correct?

---

### Post by Hendrick on 2007-05-16
I know on one version of Linux, I can connect to the online respositories, using Windows and an FTP client.  Any way I can do that, and manually install the ndiswrapper?

---

### Post by chili555 on 2007-05-18
I believe you want *ndiswrapper-common* and *ndiswrapper-utils-1.9.*> I'm doing the search from the Ubuntu CDThat's correct.

---

### Post by Hendrick on 2007-05-18
I still don't see it.  Heres a screen shot if it helps.  (Maybe I'm looking in the wrong section?)

---

### Post by chili555 on 2007-05-18
With the CD in the tray, did you press Reload? This will populate Synaptic with, not only what is installed, but also what is installable from the CD.

Synaptic will complain when it cannot reach the internet repositories, but you can ignore it.

---

### Post by Hendrick on 2007-05-18
Yes, I've done that.  Is there any way I can download it from windows, put it on a flash, move it to my desktop with linux, and install it using the terminal?

---

### Post by chili555 on 2007-05-18
Yes, but first, let's put the CD in the tray and try:```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```

---

### Post by Hendrick on 2007-05-18
Sure, heres what happens.

> michael@Michael-Linux-Ubuntu:~$ sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-common
michael@Michael-Linux-Ubuntu:~$ 


I really appreciate the help.  Thanks.

---

### Post by chili555 on 2007-05-19
Let's try:```
sudo apt-get install ndisgtk
```Ndisgtk is a graphical front-end that handles all the details of installation for you. More importantly, when you try to install it, apt will pull in all the required dependencies for you.

When you run ndisgtk, it will ask for the Windows driver file and you should be good!

---

### Post by Hendrick on 2007-05-19
> michael@Michael-Linux-Ubuntu:~$ sudo apt-get install ndisgtk
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndisgtk
michael@Michael-Linux-Ubuntu:~$ 


At least the errors are consistent.  :tongue:

---

### Post by Hendrick on 2007-05-20
My guess would be that it is trying to find the package from the Internet, rather then from the CD.  I may be able to connect via a CAT cable.  However, that may not happen until this weekend.  Should we try moving the file from a Flash Drive, and install it via Terminal?

---

### Post by chili555 on 2007-05-20
Didi you install Feisty (7.04)? It will make a difference what we download and install. If you are not sure, do:```
cat /etc/issue
```
> it is trying to find the package from the Internet, rather then from the CDDoubtful. It would spew all kinds of errors.> chili@LAPTOP60:~$ sudo apt-get install ndisgtk
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ndiswrapper-common ndiswrapper-utils-1.9
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndisgtk ndiswrapper-common ndiswrapper-utils-1.9
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 63.3kB of archives.
After unpacking 348kB of additional disk space will be used.
Do you want to continue [Y/n]? y
0% [Connecting to us.archive.ubuntu.com]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main ndiswrapper-common 1.38-1ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main ndiswrapper-utils-1.9 1.38-1ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
0% [Connecting to us.archive.ubuntu.com]
etc., etc.


---

### Post by Hendrick on 2007-05-20
Well, I would really hate for it to be something so stupid like this that I forgot to do.

> michael@Michael-Linux-Ubuntu:~$ cat /ect/issues
cat: /ect/issues: No such file or directory
michael@Michael-Linux-Ubuntu:~$ 

I put in the CD, booted from that, proceeded with the install.  If there was something else I was suppose to do after that, I didn't do it.

---

### Post by Hendrick on 2007-05-21
*Solved via AIM.  Thanks so much chili555!*

---

### Post by thrashnbash on 2007-05-21
Great that you were able to solve your issue.  Any chance you could post that information here?

I boot to the live CD and I search Synaptic and I can see ndiswrapper.  I install Ubuntu local (no longer live CD) and ndiswrapper is reported as not installed.  I then check Synaptic and its not listed there either.  I have gone through countless forum threads, etc..  Tried hooking this thing up to the net using a regular CAT5 (worked fine).  No matter what I try I can't seem to get this damn ndiswrapper installed.  I have even gone so far as to go to sourceforge.net and download version 1.44 from there and perform the make distclean and make.   Of course that errors as well.  

I want Linux and I don't want Windows.  Tired of being a Windows admin and want to use Linux to help move forward.  Just really finding it difficult.  

Oh did I mention no matter what "sudo apt-get install" I do I get that E: Couldn't find package.  It doesn't matter  if it is ndisgtk, ndiswrapper-common or ndiswrapper-util-1.9.  

Fiesty 7.04 on a Dell D600 (yes I have tried the WIKI s and Ubuntu forums.  Really thought this link was going to do it for me  [http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)  Especially after it worked on my VM.  BLAH!!

---

### Post by chili555 on 2007-05-22
If you can hook up to a CAT5 and go on line, you are just about there! Once you are on line, open a terminal and do:```
sudo apt-get update
sudo apt-get install ndisgtk
```It will ask if you also want several dependencies; you do.

The key is 'update' which gets a newer list of available packages from the on-line repositories.

Then when you run *ndisgtk* it will ask for the .sys file. Point it to the location, /home/chili/Desktop, or wherever, that you have the .sys stored.

In the case of the Encore ENUWI-G, Hendrick used the XP .sys file he copied from the Encore CD.

---

### Post by Hendrick on 2007-05-22
Just incase you aren't able to connect to the internet via a CAT5 cable, or you don't really want to drag your computer down 2 flights of stairs to get to your CAT5 cable.  (Not that hard with a laptop, but a desktop is a new story.)

You are going to have to connect to the internet one way or another.  Since I accidentally deleted the 2nd hard drive I had which had my windows backup, that computer internet was out of the question.  So I used my laptop, downloaded the files, put them on a flash drive, and went from there.  Put them on your desktop in Linux

Anyways, get these files:

[http://commx.info/linux](http://commx.info/linux)

I can't remember for the life of me where at chili555 had me download these files, but I kept a backup, and I'll host them on my host for a few days so you can get them.

Then in Linux, go to Applications-->Accessories-->Terminal

First type:

> cd Desktop

Then type:

> sudo dpkg -i ndiswrapper-common_1.38-1ubuntu1_all

Then type:

> ndiswrapper-utils-1.9_1.38-1ubuntu1_i386

And lastly type:

> ndisgtk_0.6-0ubuntu3_all

Then go to System-->Administration-->Windows Wireless Drivers

Make sure that your USB internet is connected.

Then click "Install New Driver"

Click the browse.  Then select the .INF file for your Wireless Internet.  And you are basically done from there.

If you need the drivers for Encore ENUWI-G, either post here, or PM me with your IM account info.  (Since, at least for me, the driver was an extra fee.)  I'll send you the files from there if you need them.  I could also send you the SMC if you wish, but no guarantee as to its success.

Hope you get it.  Thanks again chili555.

---

### Post by thrashnbash on 2007-05-22
I actually found the darn application.  Drove me nuts!!  

So out of total desperation I went to Add/Remove Applications and did a search for ndiswrapper.  What I found was an app called Windows Wireless Drivers (which I guess is ndisgtk).  I did have to be connected up via cat5, but it installed everything and my wireless card is now correctly identified!!

Thank you very much for your help.  HUGE help.  

I messed with Red Hat back in the version 7 & 8 days.  Back then there wasn't nearly the amount of support/how-tos out there.  Linux has come a long way.  I hope I can help push it further in my environment and replace some Micro$oft machines.

Thanks again!

---

