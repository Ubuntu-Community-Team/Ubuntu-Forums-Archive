---
title: "Package Dependencies cannot be resolved: gnome"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by Xapati on 2010-09-22
Hello

I'm using Ubuntu 10.04 and GNOME 2.30.2 

I'm completely new to Ubuntu. Anyway, I recently installed get things gnome from the ubuntu software center and then deinstalled it via the software center. After that I installed korganizer and then deinstalled that. Now however I try to install get things gnome via the software center i get the following error message:

[IMG]http://i7.photobucket.com/albums/y251/Ethanon/gnomedependency.jpg[/IMG]









How do I resolve this? And how do I figure out which packages are messed up?

---

### Post by Xapati on 2010-09-22
I fixed this, after trying everything, I rebooted my system and I could install without a problem.

---

### Post by madmax75 on 2010-09-22
Hi!

You might have some broken software packages.

Package Dependencies are other pieces of software that the programs you installed rely upon to function properly (like library files and such).

I usually install stuff through the Synaptic package manager (System -> Administration -> Synaptic Package Manager), because I do not entirely trust the Ubuntu Software Center. I think it does not handle package dependencies as well as Synaptic.

You can check if you have any broken packages:

System -> Administration -> Synaptic

Look ate the bottom of the Synaptic window. You should see there info about available packages, how many packages have been installed, and also info about possible broken packages.

If you find that there are broken packages, choose the "Other filters" tab from the left-hand column in your Synaptic window. This should list the broken packages in the right-hand column.

Now, choose "Edit" from the top menu in your Synaptic window. There should be an option for fixing broken packages. Try that one.

**If you want to try the Terminal instead of Synaptic:**

You should find the Terminal in your Applications menu (it's in the first sub-menu there, but it's English-language name escapes me - I don't use the English-language version of Ubuntu). Fire it up from there.

Now, in the Terminal window, give these commands:

> sudo apt-get updateThis above command will update your software package list. You will be prompted for your user password by "sudo", mind you - you need root privileges for this.

Then this one:

> sudo apt-get -f installThis command will try to repair the broken packages.

You can also try these ones:

> sudo dpkg --configure --pending> sudo dpkg --configure -aThese will (to my understanding) try to reconfigure the software packages.

If I'm in error with these (it's possible), feel free to correct me :)

EDIT:

So Ubuntu sorted itself out after rebooting? That's cool, glad you got it solved!

---

### Post by Xapati on 2010-09-22
> **madmax75 said:**
> Hi!

You might have some broken software packages.

Package Dependencies are other pieces of software that the programs you installed rely upon to function properly (like library files and such).

I usually install stuff through the Synaptic package manager (System -> Administration -> Synaptic Package Manager), because I do not entirely trust the Ubuntu Software Center. I think it does not handle package dependencies as well as Synaptic.

You can check if you have any broken packages:

System -> Administration -> Synaptic

Look ate the bottom of the Synaptic window. You should see there info about available packages, how many packages have been installed, and also info about possible broken packages.

If you find that there are broken packages, choose the "Other filters" tab from the left-hand column in your Synaptic window. This should list the broken packages in the right-hand column.

Now, choose "Edit" from the top menu in your Synaptic window. There should be an option for fixing broken packages. Try that one.

**If you want to try the Terminal instead of Synaptic:**

You should find the Terminal in your Applications menu (it's in the first sub-menu there, but it's English-language name escapes me - I don't use the English-language version of Ubuntu). Fire it up from there.

Now, in the Terminal window, give these commands:



This above command will update your software package list. You will be prompted for your user password by "sudo", mind you - you need root privileges for this.

Then this one:



This command will try to repair the broken packages.

You can also try these ones:




These will (to my understanding) try to reconfigure the software packages.

If I'm in error with these (it's possible), feel free to correct me :)

I fixed the issue, but this is nice to know anyway. Thanks :)

---

### Post by kurt3rd on 2010-12-16
I have this same problem from time to time and sometimes rebooting works but other times it doesn't.  I tried Madmax75's solution but it doesn't work.  

In synaptic under missing recommends I had numerous packages. But one package transmission-gtk will not let me select install. It comes up with an error that says 'Could not mark all packages for installation or upgrade'
transmission-gtk:
 Depends: libappindicator1 (>=0.0.19) but it is not installable
  Depends: libdbus-glib-1-2 (>=0.88) but 0.84-1 is to be installed
  Depends: libgconf2-4 (>=2.31.1) but 2.28.1-0ubuntu1 is to be installed
 Depends: libgdk-pixbuf2.0-0 (>=2.21.6) but it is not installable
  Depends: libnotify1 (>=0.5.0) but 0.4.5-1ubuntu4 is to be installed
  Depends: libssl0.9.8 (>=0.9.8m-1) but 0.9.8k-7ubuntu8.5 is to be installed

Can anyone help?

---

### Post by bartman08 on 2011-10-23
My openoffice tool simply vanished! Tried numerous times to install (tar file) from openoffice website. Then tried removing all existing openoffice files using synaptic manager, then trying the tar file install (install completes but no applications can be found). Tried installing using ubuntu software center, but get the 'package dependencies cannot be solved'. Tried fixing broken packages as per the earlier threads but no resolve. Any ideas?

---

