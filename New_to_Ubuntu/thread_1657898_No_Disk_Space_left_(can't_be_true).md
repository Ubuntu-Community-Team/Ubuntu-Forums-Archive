---
title: "No Disk Space left (can't be true)"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by winjeel on 2011-01-01
On my other computer (my main computer) I've tried to post this message but it couldn't work, also I've had this problem before, but I don't remember how it was fixed. It has a 12Gb partiton for Ubuntu 10.10, and I store all of my files and documents on external drives (except for UbuntuOne, which currently uses 1.4Gb of space). I only have MS Office 2000 installed via Wine, otherwise those two things are the only significant things that use disk space, other than 10.10. However, my computer has now run out of disk space (in part because of the DropBox updating service which seems to need some disk space as it updates; the DropBox destination folder is on an external drive. In all, I've got over 1Tb of external disk space spare.

In any case, the white elephant is that the Ubuntu OS seems to use nearly 10Gb of disk space. How can I fix this (without expanding my partition)? And how can I prevent this from happening again, and again, and again, ... ?

---

### Post by A_M_S on 2011-01-01
You can recover some free space running the following commands in the terminal:

```

sudo apt-get clean 
sudo apt-get autoclean 
sudo apt-get autoremove 

```

for more information about these commands type in the terminal
```

man apt-get

```

To analyse the disk memory used by your files you can run the Disk Usage Analyzer (Applications->Accessories->Disk Usage Analyzer)

---

### Post by drs305 on 2011-01-01
This guide can help you find out where your lost space has wandered off to:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

It's often undeleted trash or backups made to the system partition (/) instead of a data partition by apps such as sbackup.

---

### Post by winjeel on 2011-01-01
> **A_M_S said:**
> You can recover some free space running the following commands in the terminal:

```

sudo apt-get clean 
sudo apt-get autoclean 
sudo apt-get autoremove 

```for more information about these commands type in the terminal
```

man apt-get

```To analyse the disk memory used by your files you can run the Disk Usage Analyzer (Applications->Accessories->Disk Usage Analyzer)

Thanks for this, it freed up 90mb of space. I tried gtkorphan from the page suggested by drs305, which seemed to give me another 20mb of space (and caused a little hassle for XP in another partition). now I have 670mb of free space, once DropBox finished updating. I installed cruft, but couldn't find away to open it to use it, so that got uninstalled. What else can be done?

---

### Post by Ravenshade on 2011-01-02
> **winjeel said:**
> Thanks for this, it freed up 90mb of space. I tried gtkorphan from the page suggested by drs305, which seemed to give me another 20mb of space (and caused a little hassle for XP in another partition). now I have 670mb of free space, once DropBox finished updating. I installed cruft, but couldn't find away to open it to use it, so that got uninstalled. What else can be done?

have you tried Open Office instead of Windows Office.

---

### Post by winjeel on 2011-01-02
> **Ravenshade said:**
> have you tried Open Office instead of Windows Office.

Yes I have. I've had some lengthy and detailed discussions about the quality of OO, and generally for my work and study purposes OO is too annoying to be my main program for use. Thanks for the thought, though.

I just thought, when I make a DVD it needs a temp folder to help in the burning process, and I need a little more an 1Gb of space for updating to 11.04 and other future releases. So how else can I clean up 10.10 without needing to do a clean install?

---

### Post by alaukikyo on 2011-01-02
Try [Bleachbit]("apt://bleachbit").

---

### Post by fabricator4 on 2011-01-02
> **winjeel said:**
>  So how else can I clean up 10.10 without needing to do a clean install?

Every time a new release is installed by update manager, it goes in alongside the previous ones in /boot.  For some netbooks like my Eee pc this is a problem as the HDD is an 8Gb SSD.

The solutions is to go into Synaptic Package Manager and delete all the old kernels.  When space was getting tight I did this (search for linux-image-2.6) and was amazed that I had recovered a few Gb of disk space.

Make sure you do not delete the current kernel otherwise you'll break your OS, obviously.

You can see what the current release is by opening system monitor and looking on the "system" page.  It will probably be something like:

```
Kernel Linux: 2.6.32-27-generic 
```

for Lucid Lynx which is what I am using. You can also open a terminal and type:

```
uname -r
```

to get the same information.  The smart money says to also leave the previous known working kernal there as well, but with such a small SSD I don't really have the room for such safety measures.  Lucid works very well on my 900SD, but it would be nice if it cleaned up it's kernels occasionally.  Apart from that I have plenty of space for my ebooks, documents, and even a compressed dvd or two.

Chris.

---

### Post by fabricator4 on 2011-01-02
I should have also said; to see how much disk space is left to the file system, open "computer" on the "Places" menu and right click on "file system" then select "properties"

Ubuntu/Linux will start complaining when it gets down to about half a Gig or so...

Chris.

---

### Post by winjeel on 2011-01-02
Thanks for the help so far. I went from 0bytes this morning, to having 960Mb of space freed up. So, still there's 11Gb of disk space for Ubuntu, MS Office on Wine, and some disk cleaning utilities. Considering 4Gb minimum is needed for Ubuntu, it's hard to believe that the other 6-7Gb is for MS Office, Wine, and disk cleaning utilities. There's got to be more that can be cleaned up. I did remove some previous Linux-images (freeing up 100mb), and Bleachbit clearned up another 100Mb. Now, only a couple more Gb's cleaning up and I'll be satisfied.

---

### Post by Paqman on 2011-01-02
> **drs305 said:**
> 
It's often undeleted trash or backups made to the system partition (/) instead of a data partition by apps such as sbackup.

I've been bitten by this. You may have files owned by root that are taking up lots of space and won't show up when you run Disk Usage Analyser as a normal user. To run it as root hit Alt-F2 and type:
```
gksu baobab
```

It might find some junk that you can delete. If nothing else it'll show what's using so much space.

---

### Post by fabricator4 on 2011-01-02
> **winjeel said:**
> Thanks for the help so far. 
[..]
Considering 4Gb minimum is needed for Ubuntu, it's hard to believe that the other 6-7Gb is for MS Office, Wine, and disk cleaning utilities. There's got to be more that can be cleaned up. I did remove some previous Linux-images (freeing up 100mb), and Bleachbit clearned up another 100Mb. Now, only a couple more Gb's cleaning up and I'll be satisfied.

You're welcome.  Wine doesn't use that much, I think.  Certainly the ~/.wine directory (== /home/username/.wine) on a clean install of wine is less than 40Mb.  Have a look at this directory and see how much yours is with Office installed.  You'll have to go to View in Nautilus and select "Show hidden files" (shortcut <ctrl>h) because anything that starts with . (dot) is a hidden file.

A couple more suggestions, though you've probably already addressed them:

Un-install any components of Office that you don't really need.  If all you use is Word and Excel you don't need all the other junk. Un-install Open Office if you really don't use it, though I've found it a valid replacement for everything I use it for.  Some re-learning is required: I do understand why you prefer sticking with Office. (But what a resource pig!)

Un-install anything else in the Ubuntu distribution that you don't use.  On my machine I un-installed practically all the games and several other programs.  Unfortunately I can't remember which ones.  Others may have some suggestions.  I just trolled through the installed programs on Synaptic and got rid of the bits I didn't need.  Anything you don't understand the purpose of you can Google.  Be careful as I changed my mind about some selections when it told me what other dependencies would also be removed. There was a lot of stuff installed that I simply did not need - not a big issue if you have a 200Gb hard drive, but when you're playing with an 8GB SSD every 100Mb counts for a lot.

Simply by doing this I have 3.5 gb of an 8 Gb SSD available even after loading some other games, DVD ripping software, mplayer, and goodness know what else.  I kind of got a little bit ambitous when I saw how much space I had after the cleanup.  I never thought I'd be playing and even ripping DVD's on this machine.

I love Ubuntu on my little Eee-PC.  With the addition of an 8Mb SD card in the slot I can cram a lot onto the machine.  If I could get it to point the /home directory to the SD card (/dev/sdb1) I'd be most happy, but unfortunately the OS refuses to do this even if I put the mount command in the stab file.

Chris

---

### Post by winjeel on 2011-01-02
Again thanks. It seems that somehow UbuntuOne support programs (not the basic files) takes up a lot of space, where the bookmarks database is over 200mb, for instance. In all, the UbuntuOne support programs account for 1.4Gb. To me, it seems that DropBox is much more space efficient. Hmm... gotta think a little more about this.

Again, thanks all for the help, it's really appreciated.

---

### Post by winjeel on 2011-01-29
It's happening again. I'm down to 480mb of space left. This is *ridiculous*. The only thing that I have done with my computer in the last three weeks is download updates and receive e-mails. Even then, three weeks ago I deleted 4 years worth of accumulated e-mails to help free up space. The only cause of the excessive use of space that I can think of is all of the Ubuntu updates. I will try to free up some space, but really, once 11.04 comes out, I'll do a clean install, and *never* use updates again, except for OS updates. :icon_frown:

---

### Post by JKyleOKC on 2011-01-29
Take a look at the /var/log directory. Most all of the files there that end in ".gz" can be deleted with no harm to your system. Ubuntu writes multiple copies of many log messages to several files; however only the files that end in ".log" or have no particular ending string are the current copies. The others are all older logs being kept for historical purposes just in case you want to see them. Also cast a critical eye at the content of each of the subdirectories there; you might gain a full gigabyte of space!

Nore that you will have to use "sudo" to remove files in this area, and in some cases even to view them, so be extremely careful.

---

### Post by Darkness Des on 2011-01-29
If you got Emails through the POP protocol, they've been downloaded to your computer. Those can take a truckload of space.

---

### Post by winjeel on 2011-01-29
Bookmarks.couch in .local/share/desktop-couch is 804mb. Does this seem like a reasonable size? If not, how can it be put on a diet?

Also /usr is at 2.7Gb. Should this file get any special attention?

---

### Post by JKyleOKC on 2011-01-29
The /usr directory is where most of your executable programs are located, so it is quite likely to occupy a large percentage of the total space.

I don't know anything about "couch" so can't help with that question.

---

### Post by winjeel on 2011-01-30
> **JKyleOKC said:**
> The /usr directory is where most of your executable programs are located, so it is quite likely to occupy a large percentage of the total space.

I don't know anything about "couch" so can't help with that question.

Thanks.

---

### Post by fabricator4 on 2011-01-30
> **winjeel said:**
> Bookmarks.couch in .local/share/desktop-couch is 804mb. Does this seem like a reasonable size? If not, how can it be put on a diet?

Also /usr is at 2.7Gb. Should this file get any special attention?

/usr is where most of the installed programs will be.  Trimming it is up to you, if you can uninstall any more programs...

804 MB seems inordinately large for a "Bookmarks" file, but I don't know what couch is either.  A google search didn't show anything useful and I can't find in the normal repositories.  My entire .local directory is 1.8 MB so I'd say I'm not infected with it whatever it is.

The problem will not be updates - there simply haven't been any significant ones since the last time you fixed this up.

I still think you need to look at your hidden C drive under wine and see how much space it is using.  It's got to be using half your drive. Maybe it's Office that's chomping away at your disk space, plus other programs you may have installed.

I have and 8 GB SSD in this Eee-PC.  Currently I have 1.5 GB free but that is mainly because I currently have two ISO file in the downloads directory - one each for Ubuntu 10.10 and 11.04 A1 which I've playing with.

What are the sizes of your /home directory and the hidden .cdrive directory which is used by WINE?

Chris

---

### Post by clockworkpc on 2011-03-03
I came across this thread because I was also being alerted to diminishing disk space in /.

I eventually discovered that it was due to my having deleted a large amount of data whilst using sudo nautilus, which wasn't showing up.  The following may be of help:

1) gksudo baobab -- it will tell you if you have anything in the root trash folder

IF SO:

2) gksudo nautilus /root/.local/share/Trash

3) SHIFT+DELETE the files.   If you simply try DELETE, they refuse to go.  (At least in my experience)

That solved it for me.

---

### Post by freacert on 2012-04-24
> **winjeel said:**
> Bookmarks.couch in .local/share/desktop-couch is 804mb. Does this seem like a reasonable size? If not, how can it be put on a diet?

Also /usr is at 2.7Gb. Should this file get any special attention?


Another way to clean up the bookmarks.couch file is
(worked for me!)

[https://answers.launchpad.net/ubuntu...uestion/162623]("https://answers.launchpad.net/ubuntu/+source/bindwood/+question/162623")

You can reduce the size of bindwood's database by:
 * Connecting to your local desktopcouch database (by browsing to /home/USERNAME/.local/share/desktop-couch/couchdb.html)
* Opening the bookmarks database
* Clicking the Compact & Cleanup link, selecting Compact Database,   and clicking Run (this can take a while - you can keep track of its   progress via the Status link to the right)
 Same process works for any other desktopcouch database (e.g. gwibber-messages...)

---

### Post by oldos2er on 2012-04-24
Old thread closed.

---

