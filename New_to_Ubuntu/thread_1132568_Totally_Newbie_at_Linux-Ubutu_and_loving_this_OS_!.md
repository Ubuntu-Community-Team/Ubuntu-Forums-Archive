---
title: "Totally Newbie at Linux-Ubutu and loving this OS !"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by aroha on 2009-04-22
Hi there !

I just want to say hello to everybody and ask these 2 questions :

1) I have got Ubuntu Intrepid installed on my PC and want to download smplayer from " smplayer.sourceforge.net "...Is there any tutorial to follow ? I am not familiar with Linux at all and do not know the proper steps to install such a program...
 Can you give me some advice or any links about it ? I would much appreciate it !

2) I read that changing the main user name must be done by adding a new one and using the same password, so that the first user can be deleted..If that was true. How would it be done..?..Any tutorials ?

:P

Cheers heaps !

---

### Post by pbpersson on 2009-04-22
GO to System-->Administration--->Synaptic Package Manager and search for smplayer

This is where you should install all software if at all possible - you will get the version that has been tested with your version of Ubuntu and you will get automatic updates when they are released

---

### Post by Ms_Angel_D on 2009-04-22
Hi aroha, glad your enjoying Ubuntu.

1) Download smplayer_0.6.7_i386.deb on their website and run it ;) that's the installer. .deb files are kinda like .exe files for Ubuntu

2) If you just want to change your name so it Appears properly formatted go to System -> Administration -> Users and Groups click unlock at the bottom of the window enter your password then you can change it.

Else if you actually want to change the account name, you can also create a new user from there. Be careful not to delete your current account until you have done so, and are logged into the new account.

Angel

---

### Post by lisati on 2009-04-22
> **aroha said:**
> 
2) I read that changing the main user name must be done by adding a new one and using the same password, so that the first user can be deleted..If that was true. How would it be done..?..Any tutorials ?


You might not need to change the password. Go to System->Administration->Add users/Group, add a user with Admin privileges.

---

### Post by nyk on 2009-04-22
To answer #1:
open up a terminal and type:

```
sudo apt-get install smplayer
```

Then type your password (it won't give you a visual clue).

#2:

Go into System > Administration > Users and Groups

Then edit away. There shouldn't be any reason to create a new user.

---

### Post by Alterax on 2009-04-22
Glad to hear you're enjoying it!  I've worked with Linux for several years now, and it's still my favorite O.S.

As far as smplayer goes, you may be in luck. smplayer is already in the software repositories--just go into administration > software sources and make sure you have the Universe and Multiverse repositories checked.  Then just search for it in the add/remove programs dialog.

Your second question is pretty easy too; look in the Administration tab for "Manage Users and Groups".  Just make your new user an administrator; you can switch to it and (if you want) delete your old account later.

If you have any trouble, just let us know.  If the forums has anything, it's a lot of eager volunteers willing to help out!

---

### Post by The Cog on 2009-04-22
Chuckle. He's just been told 4 different ways to install it. Here's a summary:

All the methods below install from the Ubuntu repositories.

**Menu Add/Remove...**
This is the broadest brush that lists the major applications that you might want to add or remove. It is not a complete list, and each option in there might actually install several "packages". I *think* it is a front-end to apt-get.

**Menu System, Administration, Synaptic Package Manager**
This allows you to search all the packages in the repositories. You can search by name or description. If you choose a package that needs other packages, those dependencies are also automatically installed. You get to see exactly which packages will be installed, which Add/Remove hides from you. This is a front-end to apt-get. It is the method I prefer to use.

**sudo apt-get install *package-name***
This command-line method works even without a GUI whereas the above methods are Gnome GUI specific (Kubuntu uses a different program to Synaptic for instance).

**sudo aptitude install *package-name***
Aptitude is allegedly a little better at handling dependencies than apt-get. I have never noticed a difference between the two though, so I tend the think of them as interchangeable.

The methods below are last-resort methods to be used when the repositories don't contain the software you want to install:

**sudo dpkg -i *whatever.deb***
For installing a .deb installer package that didn't come from the repositories. e.g. a download of the binary version of VirtualBox.

Beyond this, installation methods vary. Sometimes you will be given a binary .bin or .sh file that you have to make executable and then execute:
chmod +x whetever.bin
./whatever.bin
Suns JRE comes like this. And sometimes you get a tar.gz (equivalent of a .zip) that contains source code that needs compiling.

---

### Post by kramer65 on 2009-04-22
Can I just add to all the advices about installing smplayer:

The SIMPLEST WAY to install any sort of software is by first going to 
Applications > Add/Remove.. and typing the program that you want in the search box. You can then simply click the programs you want to be installed.

Good luck and have fun!

---

### Post by Gen2ly on 2009-04-22
smplayer is a good player but i prefer plan old mplayer - all done with keypresses with a nice interface that doesn't get in the way.  link below for dvd's if you'd like to try.

---

