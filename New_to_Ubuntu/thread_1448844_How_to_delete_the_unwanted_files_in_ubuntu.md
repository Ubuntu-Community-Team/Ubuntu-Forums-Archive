---
title: "How to delete the unwanted files in ubuntu"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by karthick87 on 2010-04-07
I would like to delete the unwanted files in ubuntu to speed up my system..Like in windows we used to delete the temporary files etc..So can anyone list me the unnecessary files in ubuntu..?

---

### Post by johngreth on 2010-04-07
I don't think that that really applies to Linux...

You could try clearing the recent history in Firefox.

---

### Post by Calash on 2010-04-07
Speed impact such as that is much more a Windows issue than on Linux.

You can do a couple of commands to clean some things up.  Really does not help speed at all but it never hurts.

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

For information on what they do type

man apt-get


All are typed in the terminal.

---

### Post by J V on 2010-04-07
Also, check your ram usage, files aren't a problem (Especially as there is no fragmentation. [Before you reply to this]("http://www.flamewarriors.com/warriorshtm/nitpick.htm"))

The easiest ways to speed up ubuntu are installing preload, openbox, and checking your "Startup programs" to remove unnecessary apps

---

### Post by Steven_S on 2010-04-07
> **J V said:**
> ... [Before you reply to this]("http://www.flamewarriors.com/warriorshtm/nitpick.htm") ...

:lol:

---

### Post by vijayshukla on 2010-04-07
You need not worry about necessary files in ubuntu.  For simply deleating unwanted files
System--> Administration-->Computer Janitor
It will itself find unnecessary files and delete it.
But beware to delete some third party packages. You will be notified for this.

---

### Post by J V on 2010-04-07
Don't use the janitor, last time I checked it wanted to delete my entire GUI... Just leave it alone...

---

### Post by manoriax on 2010-04-07
I'm pretty unsure about the question if deleting files has the same effect on Ubuntu as it has on Windows. I've never had performance issues though.

---

### Post by J V on 2010-04-07
On windows deleting files decreases fragmentation, on linux it doesn't.

On windows, most of the work done by applications like ccleaner is in the registry, linux has no such malware (Well, gconf wasn't supposed to be like this but all sorts of lazy-*** programmers started dumping their settings in there and now it defeats the purpose so meh)

The biggest improvement on windows is defragging, second biggest is getting a lean antivirus, and third biggest (But by all means important) is to use msconfig to disable startup services.

The last of the 3 can be accomplished on linux (update-rc.d and gnome startu preferences)

---

### Post by jaycee23 on 2010-04-07
If you are really keen try Bleachbit - it's in the repos.

It does a good job of cleaning up unwanted caches and such.

Warning be VERY careful if you use it as root - you could seriously bork your system

---

### Post by Cavsfan on 2010-04-07
Ubuntu Tweak safely removes unneeded packages and some other stuff a lot more safely than computer janitor.
You can get that with SPM.

However as others have stated, you do not have to worry about cleaning stuff up or defragmenting unless 
you are running out of room on your drive.

---

### Post by bodhi.zazen on 2010-04-07
In general all OS collect "junk" and all file systems fragment.

In general this is almost an non-issue in Linux.

Just as with Windows, you need to understand your system before you go deleting things, otherwise you may well delete things you should not.

See : 

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

[http://www.howtoforge.com/delete-unnecessary-files-from-your-desktop-with-bleachbit-on-ubuntu-9.04](http://www.howtoforge.com/delete-unnecessary-files-from-your-desktop-with-bleachbit-on-ubuntu-9.04)

Again, just as with windows, if you blindly run tools such as bleachbit and delete "everything" expect problems.

If you take the time to examine your system you should be fine. If in doubt, make a back up, delete the file(s) and if you have problems restore from back up or try it in a VM.

In terms of fragmentation, people often, IMO, discuss fragmentation without understanding the core issue. Linux file systems fragment, but typically fragmentation is low (compared to Windows) and as such does not affect performance. There can be exceptions, especially if the hard drive is almost full.

IMO this is a nice start :

[http://www.felipecruz.com/blog_linux-defrag-fix-fragmentation.php](http://www.felipecruz.com/blog_linux-defrag-fix-fragmentation.php)

So yes Linux file systems fragment, but not with typical use not enough to affect performance (fragmentation of often < 5% on Linux, but on Windows, especially with FAT it can be over 100 %).

If fragmentation occurs it is most often due to either a full HD or large files.

---

### Post by kukibird1 on 2010-04-07
> **jaycee23 said:**
> If you are really keen try Bleachbit - it's in the repos.

It does a good job of cleaning up unwanted caches and such.

Warning be VERY careful if you use it as root - you could seriously bork your system

+1

[http://bleachbit.sourceforge.net/]("http://bleachbit.sourceforge.net/")

---

### Post by bodhi.zazen on 2010-04-07
I screen my root partition for fragmentation (I only have root and swap on this particualr box)

My fragmentation is 0.127 %

As a comparison, my NTFS partition on Windows is 29 % fragmented (File fragmentation = 59 %).

Since you need at least 10 % fragmentation to affect performance there is no need to defragment the linux partition.

Linux is not Windows.

So the question is not do linux file systems fragment or not, the question is do they fragment enough to affect performance ? They can under unusual circumstances, but it is rare.

---

### Post by J V on 2010-04-07
> **J V said:**
> _***[Before you reply to this]("http://www.flamewarriors.com/warriorshtm/nitpick.htm")***_
Once more :D

Bhodi is right, fragmentation isn't a problem on linux... Seriously 0.127%? Oo

How did you find that out? Last time I remember I had to... actually the only way I remember to find fragmentation didn't work...

---

### Post by bodhi.zazen on 2010-04-07
> **J V said:**
> Once more :D

Bhodi is right, fragmentation isn't a problem on linux... Seriously 0.127%? Oo

How did you find that out? Last time I remember I had to... actually the only way I remember to find fragmentation didn't work...

You can boot a live CD and use fsck

```
sudo fsck -vn /dev/sda1
```

Or there is a script on the Gentoo forums

[http://forums.gentoo.org/viewtopic-p-3081971.html](http://forums.gentoo.org/viewtopic-p-3081971.html)

---

### Post by n1ght5t4lk3r on 2010-05-29
A quick query about Bleachbit, I normally ran this once every so often when i used Jaunty (and never as root) , mostly just cache, browsing history, thumbnails and trash and so on but after installing Lucid earlier I ran the preview and there was like 400+mb of files, mostly un-needed language files and a fair amount of .deb files, I assume the .debs were from the installation of lucid since I haven't manually installed anything from .deb yet. Is it safe to delete these language files and .debs? (at the very least all the language files)?
I know in this day and age 400mb is a relatively negligible amount but with a nice fresh install of the OS I would like it as clean as possible right from the outset, but of course don't wish to bork my system since these files require running bleachbit as root in order to delete.

---

### Post by bodhi.zazen on 2010-05-30
> **n1ght5t4lk3r said:**
> A quick query about Bleachbit, I normally ran this once every so often when i used Jaunty (and never as root) , mostly just cache, browsing history, thumbnails and trash and so on but after installing Lucid earlier I ran the preview and there was like 400+mb of files, mostly un-needed language files and a fair amount of .deb files, I assume the .debs were from the installation of lucid since I haven't manually installed anything from .deb yet. Is it safe to delete these language files and .debs? (at the very least all the language files)?
I know in this day and age 400mb is a relatively negligible amount but with a nice fresh install of the OS I would like it as clean as possible right from the outset, but of course don't wish to bork my system since these files require running bleachbit as root in order to delete.

If you would like to run a lean system, consider learning to perform a minimal install and from that base only install the applications you want.

Often people will use a lighter weight desktop environment such as Openbox , but you can install a minimal gnome or kde or xfce if you wish.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by n1ght5t4lk3r on 2010-05-30
Well, i never asked about 'lean', and I'm perfectly happy with Ubuntu the way it comes as the standard version, I would just like to remove all the language files (several thousand of them) that I personally do not need, everything else is fine in terms of amount of content (in fact, have had to add a lot more). 
Now, I asked a simple, genuine question...Is it safe to remove these?...and your "consider learning to...." response seems a little snide, I've seen similar mooded replies to others from you around the forums and its quite condescending when most of these people are new or fairly new users versus your X amount of years experience, not everyone is as pro as you and these queries are valid. (This is just a casual observation btw, not me being hostile....which is also usually your comeback when challenged over your reply)
OK a minimal install cd might be more streamlined for some but its still good for my own personal knowledge to know if doing something is safe or not, don't you think? Its all part of the learning a new system after many years of windows.

---

### Post by mkvnmtr on 2010-05-30
If you use synaptic to remove files that you think may be unneeded it will tell you if it plans to remove anything else. This gives you time to think about it and back out.

---

### Post by n1ght5t4lk3r on 2010-05-30
<sigh> OK, I'll ask in simpler terms.</sigh>

IS it safe for my system to allow bleachbit to delete all the language files that I do not require?

that's all I want to know

---

### Post by mikewhatever on 2010-05-30
What would be simple and precise is to post the list of packages you want removed. If there are indeed thousands, then post a few.

---

### Post by oldos2er on 2010-05-30
> **n1ght5t4lk3r said:**
> I would just like to remove all the language files (several thousand of them) that I personally do not need, everything else is fine in terms of amount of content (in fact, have had to add a lot more). 


Look into the program **localepurge**. 

You can check a given file's fragmentation with **filefrag**.

---

### Post by Cavsfan on 2010-05-30
> **n1ght5t4lk3r said:**
> <sigh> OK, I'll ask in simpler terms.</sigh>

IS it safe for my system to allow bleachbit to delete all the language files that I do not require?

that's all I want to know

Yes, it is safe! I have done it many times. I run Bleachbit as root - "sudo bleachbit" from a terminal and not 
Applications > System Tools > Bleashbit (as root). I have almost every option checked too. The only ones I do not 
have checked are **Deep scan** - **Backup files**, **Firefox** - **Passwords**, **Places** and **Session** **restore**, **System** - **Memory**.
And under **Edit** **Preferences** on the **Languages** tab, I only have **English** checked. So, I have no other languages and 
I have had no problems for quite a while.

I usually have 13.7GB used after cleaning my system! That is all and I believe that is a lean system by anyone's standards!

BTW, I dual boot Windows 7 and Ubuntu 10.04 and **Ubuntu boots to a usable state much faster than Windows 7 does. **
I hear my wife complain about it every time she gets on it. She doesn't like having to wait 2-3 minutes for anything to work. 
**Ubuntu boots up in approximately 20 seconds**.

I guess I am going to have to "learn her" how to use Ubuntu because it is a lot faster!

---

### Post by n1ght5t4lk3r on 2010-05-31
Thank you very much Cavsfan, 

...and your wife sounds exactly like mine, its Vista we have dual boot as the other OS (which is probably slower to boot than W7)  which she uses to play Sims and an assortment of other games, and like yours, moans about boot times. She's still a bit scared of trying Ubuntu herself, except for browsing if I happen to have left the computer on

---

### Post by Cavsfan on 2010-05-31
You are very welcome!

I ran Bleachbit last night and it cleared everything it was supposed to and left me with around 15GB used space.
I still consider that to be minuscule compared to any version of windows' bloated systems.
Windows 7 is much faster to boot than vista was, but slow is still slow...

I found bleachbit on page 1 of this thread posted by **jaycee23** and have been running it as I explained above ever since.
I like the fact that it wipes your free space and at first was alarmed by the message that I was running out of disk space,
but realized it was just writing over the free space on my file system. 

I believe it is a very good program and it's windows counterpart would be ccleaner.
The only weird thing I have noticed is that in SPM - Custom Filters - Missing Recommends, it shows that I am missing 
"TrueType font designed for Arabic language". But, since I do not speak Arabic, I don't worry! :)

---

### Post by n1ght5t4lk3r on 2010-05-31
> **Cavsfan said:**
> 
I believe it is a very good program and it's windows counterpart would be ccleaner.



Indeed, I have used Ccleaner (used to be Crapcleaner but I guess the name gave the wrong impression) for a few years on my windows boot.

As for bleachbit, I've been using it since I started using ububtu a year ago, but never as root, and since doing a fresh install of 10.04 a couple of days ago I saw it list over 400Mb of 'un-needed' files, mainly the localization files I didn't need along with some .debs in the apt cache, and of course requiring to be run as root to delete. Just wanted to know if it was safe to remove these and now I know and have removed them with zero issues arising.

Thanks again man

---

### Post by Cavsfan on 2010-06-01
> **n1ght5t4lk3r said:**
> Indeed, I have used Ccleaner (used to be Crapcleaner but I guess the name gave the wrong impression) for a few years on my windows boot.

As for bleachbit, I've been using it since I started using ububtu a year ago, but never as root, and since doing a fresh install of 10.04 a couple of days ago I saw it list over 400Mb of 'un-needed' files, mainly the localization files I didn't need along with some .debs in the apt cache, and of course requiring to be run as root to delete. Just wanted to know if it was safe to remove these and now I know and have removed them with zero issues arising.

Thanks again man

You are very welcome! Yea, I guess Crap Cleaner might have not gone over so well! LOL!
But, I am so glad I found Bleachbit and after running it a dozen or so times, I am confident that it is good!  
It does take it a little while to run, but I have a core 2 quad and since it deletes unneeded files and then 
writes zeros and ones over the unused disk space on the partition I think it is pretty fast.
I like how it says at the end how much it cleaned. I think 400MB was what it cleaned during the first run. 
Sure makes your system minimal and faster I think.
Bleachbit and Lucid both Rock! :guitar:

---

### Post by fishman35 on 2013-03-13
One thing I have noticed is that when choosing "send to trash", the trash can never recieves it, and even after running the command to empty the trash, the hard drive space is not given back. It appears that Bleachbit goes after temp files, cookies, dead links, etc. But these are GB files I am removing, and the space never comes back. If I continue to add, the hard drive will become full, then the dreaded "low resolution mode" happens when the disk space becomes too full. This one is a freakin nightmare!!!

Is there a way to just permenantly delete the file without having to dance around in the terminal trying to find what directories have large files or what is "in use" still, etc? I hate to say it, but deleting files in Windows is right-click, delete, empty recycle bin, space back again. 



Surely there must be a way?

---

### Post by coffeecat on 2013-03-13
Back to sleep, old thread.

@ fishman35, you would appear to have a specific problem with your system that is not common if you are unable to reclaim HD space after deleting files. I suggest you start your own support thread and someone may be able to help you to resolve this.

---

