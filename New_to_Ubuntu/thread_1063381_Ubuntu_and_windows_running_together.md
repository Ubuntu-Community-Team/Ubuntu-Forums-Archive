---
title: "Ubuntu and windows running together"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by Peterfc on 2009-02-07
I need to run an accounts package on windows at the same time as i run Ubuntu 8.10. I use Ubuntu for email, design and web surfing etc. 

Is it possable to run Ubuntu and windows at the same time on two drives or two partitions and being able to flip between the two. I wish to create one machine to give me the means to switch task from system to system instead of having to reboot as often as i do now. Is this possable?

Thanks to all for reading this thread

---

### Post by HotShotDJ on 2009-02-07
VirtualBox -- You can install the Open Source Edition directly from System --> Administration --> Synaptic Package Manager.  If you want USB support for Windows, you'll need the PUEL version.  See [http://ubuntuforums.org/showpost.php?p=6398716&postcount=1](http://ubuntuforums.org/showpost.php?p=6398716&postcount=1) for help installing it.

---

### Post by deleyd on 2009-02-07
There's a package called CodeWeavers CrossOver which allows you to run Windows programs on Linux. ([www.codeweavers.com](www.codeweavers.com)) CrossOver is built on top of Wine, which is a free program. (I'm still not clear on what CrossOver adds to the existing free Wine program.  ) Of course theory isn't quite reality. Some programs work quite well and are actually supported, other programs don't quite work all the way--you may find some little thing that doesn't work quite right. Only real way to know is to try it out, or have a look at their list of programs and see if your program is listed, and find out what it says about it. ([http://www.codeweavers.com/compatibility/browse/name/](http://www.codeweavers.com/compatibility/browse/name/))

You can also do things the other way, run Windows and in Windows run a virtual Ubuntu window. I tried it once but it was a bit slow. Too slow to be useful, even though it technically worked.

---

### Post by howefield on 2009-02-07
> **deleyd said:**
> ..(I'm still not clear on what CrossOver adds to the existing free Wine program.  )

A bill for 34.99 pounds to be exact. (Pro version)

---

### Post by Sorivenul on 2009-02-07
My vote goes to XP in VirtualBox in "seamless mode".
See the following links:
[VirtualBox in Seamless Mode]("http://www.raiden.net/?cat=2&aid=373") - 
Note: This uses "rpm" as opposed to Ubuntu's dpkg/apt. No big deal. Download the package from the VirtualBox website, install it, and proceed as instructed.
[Seamless Mode in action (YouTube)]("http://www.youtube.com/watch?v=vMkUgA8s900")
[Another short article (Screenshot included)]("http://talkingincircles.net/2008/11/03/virtualbox-seamless-mode-windows-xp-in-ubuntu-810-compiz-fusion/")

Good luck!

---

### Post by Peterfc on 2009-02-08
Hi Guys

The machine i wish to use for both purposes has Ubuntu Intrepid on a two hundred Gb hard drive and windows sits on it's own machine. The windows machine is now old and is at the end of it's life. 

It seems that Virtualbox is the way to go Ok.

I can install Virtualbox onto my Ubuntu machine and then how do i install windows into the Virtualbox. I have found how to install virtualbox etc but it's the installing windows bit that need help with. 

[http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html) 

It's my Account and Payroll packages that are so important that makes this something i need to do. Wine is not an option as their are very little said about the packages i use so i think it's easier to go this route. 

Thanks Guys

---

### Post by howefield on 2009-02-08
> **Peterfc said:**
> ...I can install Virtualbox onto my Ubuntu machine and then how do i install windows into the Virtualbox.

[http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html)

What part are you stuck at ?

The url you reference is pretty old given that it refers to hardy heron and virtualbox 1.6 and you have updated versions of both.

Basically, load up Virtualbox and select "New" then create your virtual machine, (give it a name and set the memory footprint, then create the hard disk space, (it can be beneficial to put the virtual disk on a seperate drive if you have one, to improve performance). 

Once you have finished that wizard, select Settings from the virtualbox window, and set the parameters that you need, then press ok.

Place your windows setup disk in the cd drive and press Start on the Virtualbox window, all being well, you should now start to see the Windows setup begin. Follow the instructions as per a normal Windows install.

---

### Post by Peterfc on 2009-02-08
Hi howefield

It was the how and where do i put windows that was the problem. But thanks it now seems clear. 


Thanks to all for your help.

---

### Post by howefield on 2009-02-08
Once you have your virtual machine setup, a tip is to create a backup using the clonevdi command,..

VBoxManage clonevdi ~/.VirtualBox/VDI/WindowsXP.vdi ~/WindowsXP_Backup.vdi

change the .vdi name and path to whatever you need. Good way of backing up your nice new pristine xp.

---

