---
title: "Did upgrade and Skype no longer functions"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by jburrell on 2010-06-12
Good morning all (depending on where you are...)
I recently performed a standard update detected by my computer.  I'm using Ubuntu 8.10 and when the upgrade was finished I went to use Skype (which previously functioned very well) and it will not open.
I click on Skype and get the "hour glass" for about 10 seconds and then nothing happens, Skype does not open.
I thought today I would download Skype for Linux again, run the install, and that would fix the problem - it didn't.
It tells me when I go to install that there is a dependency error: "Dependency not satisfiable, Libasound2."

I looked on the forums and a thread said a possible fix would be to go to the package manager and mark Libasound2 for installation/reinstallation.  I did this and Skype will still not install - same dependency error.

Do I even need to reinstall Skype or is there a simple fix to get the Skype currently on the pc to function again?

Thanks!
V/R,
J

---

### Post by TeoBigusGeekus on 2010-06-12
Run
```
skype
```
in terminal and post us any error messages.

---

### Post by jburrell on 2010-06-13
Here is the error message, it looks like there's no directory...


skype: error while loading shared libraries: libQtDBus.so.4: cannot open shared object file: No such file or directory

---

### Post by mikewhatever on 2010-06-13
By 'standard upgrade', do you mean you've upgraded from 8.10 to 9.04?

---

### Post by itsols on 2010-06-13
1. IF you've upgraded, what is your CURRENT Ubuntu version?

2. And after a reboot, try opening Skype before running any other program. No browser, nothing. And let us know what errors/issues you get.

While on my old 8.04 OS, I could not use skype correctly. It would start and I could text others but without sound. But then I realised that the sound problem was often when I had opened another sound app like YouTube, for example. So if I opened only skype, in the beginning, all was well.

Anyway, this is only for your reference. I have upgradedto Ubuntu 10.04 and Skype works just fine, except for some bad-looking menu items that aren't really readable until I move the mouse over them.

So back on your issue, let us know the answers to the two questions above (right on top).

Cheers!

---

### Post by itsols on 2010-06-13
Oh, one more thing... While I had 8.04, I tried getting help from the Skype folks and they asked me to install some library - sorry I don't recall which one. But that never worked. After upgrading Ubuntu I reinstalled Skype with the new version on their site, and now things seem fairly ok.

---

### Post by jburrell on 2010-09-17
I didn't upgrade the version of Ubuntu, I'm still running 8.04.  Every now and then my system tells me there are software updates available and I install them.  I've never had a problem until now.  Something I ran on one of the upgrades did something to delete that library for Skype and I can't re-add it for some reason.  The error message is still:

anna@anna:~$ skype
skype: error while loading shared libraries: libQtDBus.so.4: cannot open shared object file: No such file or directory
anna@anna:~$

---

### Post by jburrell on 2010-09-17
1. IF you've upgraded, what is your CURRENT Ubuntu version?  ---I'm still using 8.04. I caused confusion when I said "standard upgrade," by that I meant I ran one of the periodic updates the system prompts from time to time.----

2. And after a reboot, try opening Skype before running any other program. No browser, nothing. And let us know what errors/issues you get.  -----I've done this and when I click on the Skype icon it acts as if its loading for about 5sec and then it just quits before it ever does anything and its like I never clicked on the icon.  I've right clicked on the icon and tried to open it that way but same thing.  There are no error messages when I do this.---

---

### Post by dirghrabadia on 2010-09-17
> 
While on my old 8.04 OS, I could not use skype correctly. It would start  and I could text others but without sound. But then I realised that the  sound problem was often when I had opened another sound app like  YouTube, for example. So if I opened only skype, in the beginning, all  was well.

Anyway, this is only for your reference. I have upgradedto Ubuntu 10.04  and Skype works just fine, except for some bad-looking menu items that  aren't really readable until I move the mouse over them.



+1. 

In short, while I had sound problems in 8.04, it works me for on 10.04. I had to tweak some of the sound settings to make it work on 8.04, but not on 10.04. So try upgrading if you must use Skype. Alternative to Skype is Ekiga, which offers equally good service, plus being an open-source application :)

---

### Post by Lateralis on 2010-09-17
I'm guessing that you don't have the right version of libqt installed.  You could try 

```

sudo aptitude install libqt4-core

```

and see if that works.

---

### Post by jburrell on 2010-09-17
I ran the install and below is what the terminal gave me.  Do I reboot now?

-----------Terminal output
anna@anna:~$ sudo aptitude install libqt4-core
[sudo] password for anna: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  libclutter-0.6-0 libopal-2.2 libpt-1.10.10 libpt-1.10.10-plugins-alsa libsdl1.2debian libsdl1.2debian-alsa 
The following packages have been automatically kept back:
  libavcodec1d libavformat1d libavutil1d libc6-dev libglib2.0-0 libkpathsea4 libpostproc1d xserver-xorg-core 
The following packages have been kept back:
  libc6 libkrb53 linux-image-lpia network-manager-gnome 
The following NEW packages will be installed:
  libqt4-core 
0 packages upgraded, 1 newly installed, 6 to remove and 12 not upgraded.
Need to get 2035kB of archives. After unpacking 7754kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy/main libqt4-core 4.3.4-0ubuntu3 [2035kB]
Fetched 2035kB in 22s (92.3kB/s)                                                                                             
(Reading database ... 91443 files and directories currently installed.)
Removing libclutter-0.6-0 ...
Removing libopal-2.2 ...
Removing libpt-1.10.10 ...
Removing libpt-1.10.10-plugins-alsa ...
Removing libsdl1.2debian ...
Removing libsdl1.2debian-alsa ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Selecting previously deselected package libqt4-core.
(Reading database ... 91400 files and directories currently installed.)
Unpacking libqt4-core (from .../libqt4-core_4.3.4-0ubuntu3_lpia.deb) ...
Setting up libqt4-core (4.3.4-0ubuntu3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
anna@anna:~$

---

### Post by Lateralis on 2010-09-17
Does Skype work?  :)

---

### Post by jburrell on 2010-09-17
I rebooted and Skype still does not function.  The error message when I enter "SKYPE" in the terminal is: 
anna@anna:~$ skype
skype: error while loading shared libraries: libQtGui.so.4: cannot open shared object file: No such file or directory
anna@anna:~$

---

### Post by Lateralis on 2010-09-17
Yes, I just noticed that what you also probably need is:

```

sudo aptitude install libqt4-dbus

```

I thought some more of the libqt4 packages would be installed with the core, but thinking about it, they wouldn't be!  So give that a whirl.  I'll keep my fingers crossed!  

You also shouldn't need to reboot with these sorts of installations. =)

---

### Post by jburrell on 2010-09-17
I did the sudo aptitude install libqt4-dbus and below is the output. Skype still does not function as before.  Its almost as if there's nothing behind the icon...

Terminal output:
anna@anna:~$ sudo aptitude install libqt4-dbus
[sudo] password for anna: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "libqt4-dbus"
Couldn't find any package whose name or description matched "libqt4-dbus"
The following packages have been automatically kept back:
  libavcodec1d libavformat1d libavutil1d libc6-dev libglib2.0-0 libkpathsea4 libpostproc1d xserver-xorg-core 
The following packages have been kept back:
  libc6 libkrb53 linux-image-lpia network-manager-gnome 
0 packages upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done

---

### Post by Lateralis on 2010-09-17
Ah... that package doesn't seem to exist in the main Hardy repository.  You will have to enable the Hardy Universe repository if you want to install it.  

System -> Administration -> Software sources

Click the check box next to "Community maintained Open Source software (universe)".  You will asked if you want to reload your software package database - do so.  Then try installing that package again.  

```

sudo aptitude install libqt4-dbus

```

---

### Post by itsols on 2010-09-18
Here's what I think has happened to your installation...

With each automatic update, certain libraries are removed and newer ones installed. In the process, you've probably lost the QT libraries. QT is a graphics library used by Skype and some other programs.

So the first thing you should do is to check if your other QT apps work. For example, CodeBlocks or QuantaPlus. If they don't then your problem is not skype but the QT libraries. And the best way to install it is to use Synaptic Package manager from the System menu in Ubuntu. The reason being that there are 'other required files' known as dependencies and Synaptic takes care of it.

But if your other apps work, you had better consider first removing skype from synaptic, and download the Debian/Ubuntu version for Ubuntu 8.04 FROM THE SKYPE WEBSITE.

Install it. If it still does not work, it could mean that Skype is using a newer/different QT library.

The BEST way though is to upgrade Ubuntu itself. But be prepared to spend several hours getting things right. This version hasn't been the best in my honest, humble opinion to upgrade. But once you're done, you'll really love this version (despite the little issues that exist).

---

### Post by jburrell on 2010-10-08
Itsols:
Thank you for your response.  As I'm not too good with Ubuntu yet how do I:
1. "So the first thing you should do is to check if your other QT apps work."
2. "Remove Skype from the synaptic?"

---

### Post by itsols on 2010-10-08
jburrell:

Do you have a program like Quanta Plus? If you don't, you can use the Synaptic package manager (System > Administration > Synaptic Package Manager) and find 'Quanta Plus' in the software list. Then install it.

If you successfully install Quanta Plus, try running it (using the Application menu). If it works, then your QT libraries are good, and the problem lies with Skype. If Quanta doesn't work, your Ubuntu installation may be corrupt.

Now, if Skype still doesn't work, using the same package manager, uninstall and reinstall the skype software. Or even better, download the skype package from the skype website.

For the records, my Skype version is 2.1.0.81-1.

Having said all this, I still think it's best to move to Ubuntu 10.04. And since you've waited this long, it's about time you moved to version 10.10 straight.

Cheers!

---

### Post by jburrell on 2010-10-08
I uninstalled and reinstalled Skype and it works!  Thanks for the help!  
One question about upgrading though...I don't have anything to backup on this laptop in terms of files.  Can I just go get the latest version of Skype (10.10?) and install it right over the top of this 8.04 I'm running?  Is that how it works?

---

### Post by itsols on 2010-10-08
Glad you got it working. But it seems like Ubuntu 10.10 is not yet out. They still haven't come out of beta. So you have TWO options now.

1. If you have no problems with 8.04 and if you can work, it's best to wait for 10.10.

2. If you're not able to do any work with the current version, then better consider 10.04 at least.

And yes, if there's nothing to lose on your system, just download the installation, burn it to a CD, and install it over the existing one. Remember to format the hard disk in the process. You'll be guided through the steps.

After you've got 10.04 running, you can upgrade in the future without formatting or losing your files.

I've moved from version 7.10 > 8.04 > 10.04. But my worst experience was the current version. But since you're doing a new installation, I don't think there's any issue.

---

