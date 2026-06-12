---
title: "Windows Equivolent on Ubuntu."
date: 2009-01-24
forum: New to Ubuntu
---

### Post by rroze002 on 2009-01-24
Hi all,
I recently switched from Win XP to Ubuntu, and so far only minor problems have arisen.  For example, the during audio playback I'll get some errors causing the player to skip tracks. Once I installed VLC player the playback error stopped, but on certain occasions I'm not able to add tracks to the play list.  In general what I'm looking for is a good reference on how to do the following things:

-Use system tools, for example Defragmenting in Windows
-Navigating the File System
-Setting default programs
-Using the terminal for configuration

Thanks.

---

### Post by sully101 on 2009-01-24
> **rroze002 said:**
> 
-Use system tools, for example Defragmenting in Windows
-Navigating the File System
-Setting default programs
-Using the terminal for configuration

Thanks.

Defragmentation - Well I never have. If your drive has 25% free space you probably wont need to.

The rest are probably answered here [https://help.ubuntu.com/8.10/index.html]("https://help.ubuntu.com/8.10/index.html")

---

### Post by Paqman on 2009-01-24
> **rroze002 said:**
> 
-Use system tools, for example Defragmenting in Windows


Defragging isn't required, and neither are antivirus scans. Cleaning up junk onn your system is about the only useful maintenance task on Linux. Otherwise your system should require very little maintenance.

[How to clean up junk files]("http://ubuntuforums.org/showthread.php?t=140920")

> 
-Navigating the File System


The file browser Nautilus works just the same as Windows Explorer. Was there something in particular you wanted to do?

> 
-Setting default programs


Right click on the file type > Properties > Open With

> 
-Using the terminal for configuration


All depends on what you're configuring. The best way to get used to the terminal is to use it lots.

---

### Post by jimmy the saint on 2009-01-24
There is a good explanation of why you don't need to defrag here
[https://answers.launchpad.net/ubuntu/+question/12588](https://answers.launchpad.net/ubuntu/+question/12588)

A good primer for ther teminal can be found here
[http://endor.hsutx.edu/cmdintro.htm](http://endor.hsutx.edu/cmdintro.htm)

---

### Post by blackened on 2009-01-24
> **rroze002 said:**
> -Navigating the File System

There are small variations in the default filesystem layout between different distributions, but here is a basic overview:

[http://www.freeos.com/articles/3102/]("http://www.freeos.com/articles/3102/")

---

### Post by Frak on 2009-01-24
> **rroze002 said:**
> -Use system tools, for example Defragmenting in Windows
-Navigating the File System
-Setting default programs
-Using the terminal for configuration

1. You don't need to
2. Nautilus, Places -> Home
3. System -> Preferences -> Preferred Applications
4. Applications -> Accessories -> Terminal

---

### Post by rroze002 on 2009-01-25
In reference to navigating the file system, what I mean is that unlike Windows where I know exactly the directories of all my files and programs, in Linux I do not.  As some of you suggested in the post, when doing right click > open with > specific program, I have trouble finding the exact directory where the applications are installed.  In a Windows environment the user is able to choose the location for the installation to use, but in Ubuntu that process is automated.

Also when choosing the Preferred Application, if the application does not appear in the drop down menu, choosing Custom would the only other option.  Once custom is selected the Command line appears, which I still havent figured out how to use.  Lets say I want to set VLC as the default player, in the Command field, do I type in the same thing I would use to bring up VLC from the terminal?  If so, what is the right command?

---

### Post by llamabr on 2009-01-25
You said:
In a Windows environment the user is able to choose the location for the installation to use, but in Ubuntu that process is automated.

I'm sorry, I think you have that exactly backward.  Ubuntu does a nice job of associating applications file filetypes or mime's, but linux is infinitely configurable.

That said, nearly all of the applications you're looking for will be in /usr/bin/  

If you know what it is you're looking for, but don't know where it is, you can do 'which':

brock@vader:~$ which xpdf
/usr/bin/xpdf
brock@vader:~$ 

and it'll tell you the full path.

hope that helps.

---

### Post by oldos2er on 2009-01-25
"Lets say I want to set VLC as the default player, in the Command field, do I type in the same thing I would use to bring up VLC from the terminal?"

 Yes, it's the same command: vlc

 Most user-installed executables are in /usr/bin.

---

### Post by blackened on 2009-01-25
> **rroze002 said:**
> In reference to navigating the file system, what I mean is that unlike Windows where I know exactly the directories of all my files and programs, in Linux I do not.  As some of you suggested in the post, when doing right click > open with > specific program, I have trouble finding the exact directory where the applications are installed.  In a Windows environment the user is able to choose the location for the installation to use, but in Ubuntu that process is automated.

What you're talking about is not meant to keep the files hidden from you, but is a security feature of Linux. When you install a program you are temporarily elevated to superuser status, and the files that were installed (other than those placed in your user directory) belong to the superuser. Since those files do not belong to you, you are not able to edit them without becoming superuser. The benefit of this policy is that not just anyone can alter essential files (which is the standard setup of XP, though they made an attempt at fixing this promblem in Vista, poorly as far as I'm concerned) unless explicitly given permission. This is why Linux does not suffer from the problems of malware, spyware, viruses, etc. Even if such programs got onto the system, you would have to give them permission before they could do any damage, which is why you always hear people advise against downloading from untrusted sources.

---

### Post by UbuntuNerd on 2009-01-25
check out this guide to clean junk files and other things:
[http://my.opera.com/ubuntunerd1/blog/2008/12/26/keeping-ubuntu-clean]("http://my.opera.com/ubuntunerd1/blog/2008/12/26/keeping-ubuntu-clean")

---

### Post by rroze002 on 2009-01-25
Thank you all, all this info should keep me sated for some time.

---

