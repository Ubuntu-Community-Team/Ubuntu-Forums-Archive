---
title: "New HP Deskjet 1000 J110 printer won't print"
date: 2011-07-10
forum: New to Ubuntu
---

### Post by lucyi on 2011-07-10
Jaunty 9.02, I know, not supported, was loaded onto my desktop PC April 2011 by a friend with Gnome, Debian.  I have spent many hours reading forums, reading Keir Thomas  Ubuntu Pocket Guide,  looking at lists at HPLIP, and haven't figured out what to do.  HP Deskjet 1000 J110 series bought yesterday to replace my trusty HP 722C which was okay with Jaunty but started to crap out.  I don't have wireless, don't want an all in one.  Ubuntu tells me the jobs have printed. Nothing has printed, test page or document.  I unplugged power and connection to computer, rebooted computer, plugged all back in, reinstalled the printer.  Still no printing.  If you reply, I need VERY simple  instructions.  New to Linux. Not an IT person.  I have tried writing in the terminal but am not comfortable learning to write code. Thank you to anyone who can help me.Troubleshoot text files attached .

---

### Post by jtarin on 2011-07-10
HP Linux Imaging and Printing System .......what version are you using? Your printer had been added in version 3.10.9. You will probably have to install an updated version from [here]("http://hplipopensource.com/hplip-web/index.html"). At that link is a menu on the left that tells you how to proceed through each step. Have a problem post back.

---

### Post by jtarin on 2011-07-10
> Not an IT person. I have tried writing in the terminal but am not comfortable learning to write code.Unless your a programmer you won't write code in the terminal, but you should learn to write commands. Your not going to break anything.

---

### Post by lucyi on 2011-07-10
Thank you JTarin.  Currently installed is HPLIP 3.9.2.  I need 3.10.9, which is fully supported, according to the HPLIP pages.  How do I get this?  They recommend going through my Synaptic Program Manager.  I am not sure how to get this newer version.

---

### Post by lucyi on 2011-07-10
> **jtarin said:**
> Unless your a programmer you won't write code in the terminal, but you should learn to write commands. Your not going to break anything.
Yes, thank you.  I didn't mean writing code, I meant learning all the commands and syntax.  For instance I went in to terminal thinking I would try to upgrade to Ubuntu 9.10 and successful go through all the upgrades.    Then I got a "Are you root?"  That threw me for  a loop. I have the Ubuntu Pocket Guide and also read some other technical stuff about writing in the terminal.  I am so glad you responded and seem to be able to help.

---

### Post by jtarin on 2011-07-10
> **lucyi said:**
>  I need 3.10.9, which is fully supported, according to the HPLIP pages.  How do I get this?  They recommend going through my Synaptic Program Manager.  I am not sure how to get this newer version.As I said.....**You will probably have to install an updated version from [here]("http://hplipopensource.com/hplip-web/index.html"). _At that link is a menu on the left that tells you how to proceed through each step._**
Install the newest version....Version: 3.11.5

---

### Post by lucyi on 2011-07-11
I am now trying to install a download from HPLIP using the terminal. It is telling me this: Enable the universe/multiverse repositories. Also be sure you are using the Ubuntu "Main" Repositories. See: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) for more information.  Disable the CD-ROM/DVD source if you do not have the Ubuntu installation media inserted in the drive.

What does this mean and how do I accomplish it?  I have read the Ubuntu repositories manual and can't find how to do the above instructions.  I do not have the Ubuntu installation media inserted in the drive.  I don't have it at all, a friend installed it to my computer.

---

### Post by jtarin on 2011-07-11
GUI-based repository management is normally accomplished via "Software Sources". This interface can be accessed via several methods. For the latest versions of Ubuntu, the easiest way is to go through the "Ubuntu Software Center". Open the software center, then from the Edit menu select "Software Sources". You will have to enter your password to change settings in this window.

For older versions of ubuntu, there are several options: 

Main Menu: System > Administration > Software Sources.

Synaptic : System > Administration > Synaptic Package Manager : >> Settings >> Repositories.

Main Menu: Ubuntu Software Center : >> Edit, Software Sources. 

 The window I have attached will open. Check all that you see checked, except "source code" and uncheck the CD Rom selection.It will ask you to update when you try to close. Update.

[IMG]https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=SoftwareSources-UbuntuSoftware.png[/IMG]

---

### Post by lucyi on 2011-07-11
:) Got it, thanks so much.  My knowledge base is ever expanding!

---

### Post by jtarin on 2011-07-11
> **lucyi said:**
> :) Got it, thanks so much.  My knowledge base is ever expanding!And my image linking base is growing.:lolflag:

---

### Post by lucyi on 2011-07-11
New problem.

 warning: HPLIP removal failed. The previous install may have been installed using a tarball or this installer.
warning: Continuing to run installer - this installation should overwrite the previous one.


RUNNING POST-PACKAGE COMMANDS
-----------------------------
OK


RE-CHECKING DEPENDENCIES
------------------------
error: A required dependency 'gcc (gcc - GNU Project C and C++ Compiler)' is still missing.
error: A required dependency 'python-devel (Python devel - Python development files)' is still missing.
error: A required dependency 'cups-devel (CUPS devel- Common Unix Printing System development files)' is still missing.
error: A required dependency 'libtool (libtool - Library building support services)' is still missing.
error: A required dependency 'cups-image (CUPS image - CUPS image development files)' is still missing.
error: Installation cannot continue without these dependencies.
error: Please manually install this dependency and re-run this installer.

Do you think I can successfully acquire these packages?  How to manually install, using the terminal, I guess, but which commands to use? sudo get apt cups-image?  Is that the correct command?

---

### Post by jtarin on 2011-07-11
Use the Synaptic Package Manager and the search function within and search for each one.....then when you find right-click on the check box and select install......when you have found all you can then hit the "apply" button on the menu above. I will warn you that the versions that are available might not be new enough for what you need to do, but taking a cursory glance I think most will. These are packages (tools) that are needed to compile programs correctly for installation.After you have downloaded and installed try installing your application again. Any errors post back.
Learn to use Synaptic Package Manager for now.....it is very dependable. It is the frontend GUI for "apt".

---

### Post by lucyi on 2011-07-11
I'll try this and get back to you either way.  You are so generous!  Thank you.

I tried the first one (gcc) and got a warning about security and someone being able to invade my system.  Is it worth the risk?

---

### Post by jtarin on 2011-07-11
Ignore the warnings. Keep a list of all you install and you can remove most of them later if you want.

---

### Post by lucyi on 2011-07-11
python-devel  not found
cups-devel   not found but libcups2-dev is in the list and has the same description, use it?
libtool  not found
cups-image not found but libcupsimage2-dev is in the list and has the same description, use it?

---

### Post by jtarin on 2011-07-11
Try them...just keep a list.

---

### Post by lucyi on 2011-07-11
@Jtarin

What good to get alternative packets when all are not available?  Got an error message trying to get the gcc reinstalled.  Not a warning, an error. I've about given up.  Posted a new thread about work-arounds.  Will try new printer with old laptop w/ WinXP to see if it will work.  Friend may be getting me into Linux Mint if my elderly computer (Gateway year 2002) meets sys requirements.  Thanks for your support.:KS

---

### Post by jtarin on 2011-07-11
> **lucyi said:**
> @Jtarin

What good to get alternative packets when all are not available?  Got an error message trying to get the gcc reinstalled.  Not a warning, an error.The good is....you asked "How To", because you didn't want to reinstall a newer version. I never said it would be easy, but it is not impossible.Packages are available but maybe not as we would like them. :P

---

### Post by lucyi on 2011-07-12
I'm giving up on the whole thing.  It's too much for my brain to handle.  I'll wait until I get enough saved to buy a new 'puter and start fresh.    Thanks so much for your suggestions.

---

### Post by jtarin on 2011-07-12
When I started with Linux over 13 years ago I had a video card that was supposed to work with Linux, but back then their was nothing like this Ubuntu experience.....it took me a week of working by myself searching the internet for solutions then making a custom xorg.conf file and driver for my card......I got a new card the next week and started the same process over again. There is always a way to get it to work. Perseverance is the key.:P

---

