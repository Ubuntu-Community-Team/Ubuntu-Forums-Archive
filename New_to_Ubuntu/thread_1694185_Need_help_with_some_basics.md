---
title: "Need help with some basics"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by bruss01 on 2011-02-24
I am a longtime Microsoft XP user and a tech professional for nearly 30 years.

However, I am making my first foray into trying to become conversant in Linux.  A friend recently gave me an Acer Aspire One netbook ).  I have installed a Broadcom Crystal HD video accellerator.  Then I installed Ubuntu 10.10 (should be the most current version).  This is in dual boot with my XP install. The installation appeared to go allright, I was able to get my wireless card working ok.  But I am having difficulty with getting the broadcom card set up.

I'm looking for the equivalent of XP's device manager so I can see the card and whether the system thinks it is properly installed.  How would I check this on Ubuntu.

Also, I found some advice on a forum regarding editing a file located at \etc\adobe\mms.cfg
Here's the link:
[http://askubuntu.com/questions/24324/how-do-i-get-flash-10-2-rc-crystal-hd-for-hw-accelerated-video-to-work/25706#25706](http://askubuntu.com/questions/24324/how-do-i-get-flash-10-2-rc-crystal-hd-for-hw-accelerated-video-to-work/25706#25706)

First, I am 100% sure adobe is installed.  When I got to file manager and open \etc there is no \adobe folder there.  Following the advice of the post, I tried to create the folder.  Nothing happens, no error message or anything, and the folder is not created that I can see (bug, feature, what?).  It is no problem to create an adobe folder in the \documents folder, so I know I am able to create folders. but I cannot create it inn the \etc folder, just nothing happens when I try.  If there were an error message that popped up and said "hey you can't do that" or "you don't have permissions" etc I would at least understand.  It's frustrating not getting any kind of useful feedback on one's actions.  Is this typical of how failed operations are managed in Ubuntu?

I'm generally a very patient guy but I am starting to lose my temper a little with this.  I can understand needing to go to a vendor site and download an install executable and run it.  Heck, I could even deal with it if there was a raw file of some kind and some actual instructions on what to do with it to make it work.  But this "shrug, I dunno, it's you're computer, you figure it out" - turn, walk away... *FUME*.  Also, I heard that Linux was blinding fast on minimal hardware, and my experience so far is HA, maybe a teeny tad faster than XP, but no way is it twice as fast or 3 times as fast.  I was willing to make the investment in working to learn a new system, but unless I'm missing something pretty big, I'm not seeing a return on that investment to make it worth while, at least, not yet.

So, help a fella out... help me get a clue so I can start to understand instead of beating my head against the wall here.  I have some books but they're not terribly helpful.  So don't just say "get a book" unless you are saying "get THIS book, check out page 99 on "installing drivers" or some such.  If the attitude is "shrug, you're computer, YOU figure it out..." then please just don't evenn reply because my patience is getting a bit thin and I'm afraid I might not take that very well at this point.

Sincere thanks to anyone who is able to offer some real help.  I do appreciate it.

---

### Post by Old *ix Geek on 2011-02-24
First of all, backslashes in path names are an idiotic windoze thing; Linux, being a UNIX-like operating system, uses slashes in its path names.

Second--and I'm speaking as someone whose computing experience started with UNIX 25+ years ago, and only later had the misfortune of having to occasionally touch a windoze box--*nix is, undoubtedly, not very verbose. :) It's not meant to be. It started out assuming that anyone using it would take responsibility for their own actions, hence no idiot prompts as in windoze. The moronic, annoying "are you SURE you want to do this? are you SURE you want to do that?" nonsense in windoze would drive me crazy if it were a normal part of using Linux! :eek:

> I was able to get my wireless card working ok. But I am having difficulty with getting the broadcom card set up.Unless I'm just being dense, this is contradictory. :confused: If your wireless card is working, what's the problem?

> First, I am 100% sure adobe is installed.Okay--but WHERE is it installed?
> When I got to file manager and open /etc there is no /adobe folder there.Because that's not where it's installed on YOUR computer.
> Following the advice of the post, I tried to create the folder.Right, because you don't have permission to create a directory in /etc.
> Nothing happens, no error message or anything, and the folder is not created that I can seeI don't know how you're attempting to create the directory (GUI?), but if you're doing it at a command line you should get a 'permission denied' error message.
> It is no problem to create an adobe folder in the /documents folderDo you mean in your home directory's "documents" subdirectory? If so, right, because you have permission to do that in your home directory. /etc is a system directory and unless you're root, you can't create things under it.

---

### Post by ankit singh on 2011-02-24
Hey you need a bit understanding of linux file and file system

The tree of the file system starts at the trunk or slash, indicated by a forward slash (/). This directory,
containing all underlying directories and files, is also called the root directory or "the root" of the file system.
Subdirectories of the root directory are as follows and what they are used for


/bin
Common programs, shared by the system, the system administrator and the users.

/boot
The startup files and the kernel, vmlinuz. In some recent distributions also grub data. Grub is
the GRand Unified Boot loader and is an attempt to get rid of the many different boot-loaders we
know today.

/dev
Contains references to all the CPU peripheral hardware, which are represented as files with special properties.

/etc
Most important system configuration files are in /etc, this directory contains data similar to those in the Control Panel in Windows

/home
Home directories of the common users.

/initrd
(on some distributions) Information for booting. Do not remove!

/lib
Library files, includes files for all kinds of programs needed by the system and the users.

/lost+found
Every partition has a lost+found in its upper directory. Files that were saved during failures are here.

/misc
For miscellaneous purposes.

/mnt
Standard mount point for external file systems, e.g. a CD-ROM or a digital camera.

/net
Standard mount point for entire remote file systems

/opt
Typically contains extra and third party software.


/proc
A virtual file system containing information about system resources. More information about the meaning of the files in proc is obtained by entering the command man proc in a terminal
window. The file proc.txt discusses the virtual file system in detail.

/root
The administrative user's home directory. Mind the difference between /, the root directory and
/root, the home directory of the root user.

/sbin
Programs for use by the system and the system administrator.

/tmp
Temporary space for use by the system, cleaned upon reboot, so don't use this for saving any work!

/usr
Programs, libraries, documentation etc. for all user-related programs.

/var
Storage for all variable files and temporary files created by users, such as log files, the mail
queue, the print spooler area, space for temporary storage of files downloaded from the Internet,or to keep an image of a CD before burning it.

[http://tldp.org/LDP/intro-linux/intro-linux.pdf](http://tldp.org/LDP/intro-linux/intro-linux.pdf)  this will help alot

---

### Post by piquat on 2011-02-24
Reguarding the lack of an error message.  Did that happen in the GUI?  Try the command in a terminal:
 
```
 
mkdir /etc/folder_name

```
 
You'll usually see an error message out of the terminal if the GUI doesn't give you one.

---

### Post by migs73 on 2011-02-24
Two ways to make the folder if it doesn't exist;

CLI (the *nix way!)

because the folder is 'owned' by root you need Super User privileges to edit it. To get this you type 'sudo' before your commands. Then you will be asked to type in your password (nothing will appear on screen as you type, this is normal);
Open a terminal (Ctrl+Alt+T or Applications-->Accessories--> Terminal)

```
sudo mkdir /etc/folder_name
```

OR

A more familiar way for you, using the GUI;

Go to the Ubuntu Software Centre (Applications--> Ubunutu Software Centre)
Type gksu into the search bar, from the list you get click on the listing called 'privilege granting extension for nautilus using gksu', now click on install. NB this will probably install other things with it, this is fine as they are dependencies for that program.
It will ask for your password, type it in and wait for it to install.

Once installed, if you browse to the /etc folder, right click on it and you now have the option to 'open as administrator', it'll than ask for your password (you will see blanks being added as you type here), then when in the folder right click and select 'create folder'.

If you want to have a list of your hardware open a terminal again and type;

```
lspci
```

List what is on your PCI bus.

```
lshw
```

To list all hardware (a big output)

OR

Ubuntu software centre and install Hardware Lister.


BTW the first two are better!

You will probably find your 30 yrs of windows experience will initially be a hindrance;
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Mike

---

### Post by Jouke S on 2011-02-24
Hey man. 
Just wanted to give you some advice, I do not know how to fix the problem with your network card. 

I think if you invest some time in getting to know Ubuntu, you will find that Ubuntu has one of the friendliest OS-communities out there. It probably isn't very wise approaching the people on this forum like they're know-all geeks who tell you to RTFM whenever you ask something. I've found that the people here are very helpful. 

On the topic of error messages; I've encountered this once or twice, too. However, usually you're greeted by an error message that tells you what you're doing wrong (which you can always Google if you don't understand it). 

I'm a long time Windows user myself, too. I recently finally took the time to get to know Ubuntu (after years of messing with dual boots and live-CDs) and I'm loving it.
Give it a chance. I'm sure you won't run in to too many problems in the future (hardware support is great, usually).

---

### Post by Clever_Username on 2011-02-24
> **bruss01 said:**
> I am a longtime Microsoft XP user and a tech professional for nearly 30 years.

However, I am making my first foray into trying to become conversant in Linux.  A friend recently gave me an Acer Aspire One netbook ).  I have installed a Broadcom Crystal HD video accellerator.  Then I installed Ubuntu 10.10 (should be the most current version).  This is in dual boot with my XP install. The installation appeared to go allright, I was able to get my wireless card working ok.  But I am having difficulty with getting the broadcom card set up.

I'm looking for the equivalent of XP's device manager so I can see the card and whether the system thinks it is properly installed.  How would I check this on Ubuntu.

Also, I found some advice on a forum regarding editing a file located at \etc\adobe\mms.cfg
Here's the link:
[http://askubuntu.com/questions/24324/how-do-i-get-flash-10-2-rc-crystal-hd-for-hw-accelerated-video-to-work/25706#25706](http://askubuntu.com/questions/24324/how-do-i-get-flash-10-2-rc-crystal-hd-for-hw-accelerated-video-to-work/25706#25706)

First, I am 100% sure adobe is installed.  When I got to file manager and open \etc there is no \adobe folder there.  Following the advice of the post, I tried to create the folder.  Nothing happens, no error message or anything, and the folder is not created that I can see (bug, feature, what?).  It is no problem to create an adobe folder in the \documents folder, so I know I am able to create folders. but I cannot create it inn the \etc folder, just nothing happens when I try.  If there were an error message that popped up and said "hey you can't do that" or "you don't have permissions" etc I would at least understand.  It's frustrating not getting any kind of useful feedback on one's actions.  Is this typical of how failed operations are managed in Ubuntu?

I'm generally a very patient guy but I am starting to lose my temper a little with this.  I can understand needing to go to a vendor site and download an install executable and run it.  Heck, I could even deal with it if there was a raw file of some kind and some actual instructions on what to do with it to make it work.  But this "shrug, I dunno, it's you're computer, you figure it out" - turn, walk away... *FUME*.  Also, I heard that Linux was blinding fast on minimal hardware, and my experience so far is HA, maybe a teeny tad faster than XP, but no way is it twice as fast or 3 times as fast.  I was willing to make the investment in working to learn a new system, but unless I'm missing something pretty big, I'm not seeing a return on that investment to make it worth while, at least, not yet.

So, help a fella out... help me get a clue so I can start to understand instead of beating my head against the wall here.  I have some books but they're not terribly helpful.  So don't just say "get a book" unless you are saying "get THIS book, check out page 99 on "installing drivers" or some such.  If the attitude is "shrug, you're computer, YOU figure it out..." then please just don't evenn reply because my patience is getting a bit thin and I'm afraid I might not take that very well at this point.

Sincere thanks to anyone who is able to offer some real help.  I do appreciate it.



I just wanted to add that learning Linux takes time and effort. You're not going to get it all in one day. I imagine it took you quite a while to get to the level of proficiency that you're at with Windows. 
As I'm sure you've noticed, there are alot of *_extremely_* bright and helpful people on these forums. Hang around the forums for a while and I'm sure things will get easier for you.
Good luck to you!

---

### Post by Stephen Morgan on 2011-02-24
If there are special drivers available for your hardware they'll be available in the System menu in the top bar. System > Administration > Additional Drivers. Updating the system might help too, in System > Administration > Update Manager, assuming you haven't already.

---

### Post by bruss01 on 2011-03-13
First, I would like to thank everyone who cared to submit a thoughtful reply.  I do appreciate any constructive help.

Second - those who thought we were talking about a network card missed the fact that this is Broadcom's Crystal HD *VIDEO ACCELLERATOR* card that is at issue, not a network device.

Third - While those of you suggesting comm wand prompt use - sure, I learned DOS, BASIC etc but I have to question that if you cannot do a simple driver install without resorting to programmer-level contortions, then it is not really a mature GUI OS we are tblalking about.  I can take time to learn Linux, sure, but I don't have 3 months in my schedule something that I consider "recreational" and "nice to have" for my own personal growth.

I thought maybe it was something simple I was overlooking and that really it was a piece of cake to figure out how to install this.  Apparently the mfr provides the driver but no instructions for installation.  That's not the fault of anyone on this board.

Anyway, here's what I'm seeing from my experience with Ubuntu:

blinding speed - NOT
Ease of use - NOT
Vendor support - NOT
Knowlegeable user community - well intetioned and sympathetic, yes... full of instant answers, NOT. Some didn't even bother to draw distinction between a network card vs a video card, let alone help me research the issue.  Not meaning to be rude, just citing this particular experience.

I was pretty frustrated when I first posted, but have had a chance to breathe a bit and am calmer now and realizing "you get what you pay for" and Ubuntu is a free product so I should not complain too loudly.  Maybe at some point it will be suitable for mainstream use.  I'm a pretty sophisticated user, but I shouldn't have to learn a programming language to do simple things like create a folder or copy a file, or install a simple hardware driver.  

Again, thanks for the input, was hoping to hear from someone who had installed the Crystal HD video card with some tips on how they got it working... evidently this was not the right place for that.

---

