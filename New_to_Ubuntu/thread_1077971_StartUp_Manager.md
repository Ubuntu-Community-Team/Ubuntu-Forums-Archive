---
title: "StartUp Manager"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by Testrum on 2009-02-22
I'm having problems with StartUp Manager. I downloaded the package and installed and it perfectly fine, I went to the StartUp Manager icon in my System->Administration->StartUp Manager and run it and all it says is "Preforming pre-configuration tasks" and that's it. I've tried restarting to see if that would help and I get the same thing :???:

---

### Post by Locke_99GS on 2009-02-22
Make sure it's running as root. In *alacarte*, make sure the entry is preceded with *gksu*, or run from cli with *gksu*.

---

### Post by Testrum on 2009-02-22
> **Locke_99GS said:**
> Make sure it's running as root. In *alacarte*, make sure the entry is preceded with *gksu*, or run from cli with *gksu*.
Do what? I'm a noob when it comes commands lol.

---

### Post by taurus on 2009-02-22
Applications -> Accessories -> Terminal
```
gksudo startupmanager
```

---

### Post by dinofex@gmail.com on 2009-03-03
I have the same problem in Ubuntu Intrepid Ibex (8.10) Testrum has: "I downloaded the package and installed and it perfectly fine, I went to the StartUp Manager icon in my System->Administration->StartUp Manager and run it and all it says is 'Preforming pre-configuration tasks' and that's it."  

StartUp Manager started up for me when I first installed it.  It hasn't started since I attempted to configure it.  I've tried starting it from the GUI, 'System > Administration > StartUp-Manager', which temporarily shows an icon for it while it does the 'Preforming pre-configuration tasks' thing, then the 'Preforming pre-configuration tasks' box disappears and so does the icon.  When I try opening it from the terminal I get the following:

"username@computername:~$ gksu -k startupmanager
Grub2 not detected
Searching for GRUB installation directory ...  GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... found: /boot/grub/splashimages/Mac4Lin_1.0_GRUB3.xpm.gz

Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Grub Legacy detected
Usplash not detected
Splashy detected
Splashy ERROR: Cannot read XML File <</etc/splashy/config.xml>>. Exiting...
Splashy ERROR: Error occured while starting Splashy
Make sure that you can read Splashy's configuration file

Traceback (most recent call last):
  File "/usr/sbin/startupmanager", line 37, in <module>
    main()
  File "/usr/sbin/startupmanager", line 34, in main
    SumGui()
  File "/usr/share/startupmanager/gtk_frontend.py", line 190, in __init__
    self.setup_widgets()
  File "/usr/share/startupmanager/gtk_frontend.py", line 206, in setup_widgets
    self.set_splashy_widgets()
  File "/usr/share/startupmanager/gtk_frontend.py", line 360, in set_splashy_widgets
    for theme in splashy_themes:
TypeError: 'int' object is not iterable"

and StartUp Manager still does not start.  I have uninstalled StartUp Manager, rebooted and reinstalled StartUp Manager and it still doesn't launch.  Obviously I corrupted a file I would like to restore, the file controlling StartUp Manager.  What I need to know is what its called, how to open it so I may edit it and what its vanilla version should say.  I would appreciate any information that would allow me to proceed.

---

### Post by LowSky on 2009-03-03
why not try QGRUBEditor

```
sudo apt-get install qgrubeditor
```

its built for KDE, but will work in gnome just fine.


EDIT, it may have changed names

```
sudo apt-get install kgrubeditor
```

---

### Post by dinofex@gmail.com on 2009-03-03
BTW, Testrum, what they were suggesting was that you try to start StartUp Manager from the Terminal command line with "gksu startupmanager" once you get yourself to the 'root' prompt, which should read "username@computername:~$ ", where 'username' should be the user name you assigned yourself during installation of Ubuntu Interpid Ibex (8.10), and 'computername' the name you or the installation chose for the computer or virtual machine you installed Ubuntu Interpid Ibex (8.10) on.

---

### Post by dinofex@gmail.com on 2009-03-03
Will kgrubeditor run in Ubuntu 8.10?  

'$: sudo apt-get install qgrubeditor' just returned this: 

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kgrubeditor is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source"

---

### Post by Orvar on 2009-03-10
Why always recomment the non-graphical way? This only keeps non-geeks from choosing Ubuntu as their default operating system. Most people are happy to click their way through menues to get things done, very few dare to use commands in the Terminal window. MS (sorry to swear) realised this many years ago, abandoned MS-dos and introduced Windows ("inspired" by Macintosh and DR-dos) and that is the main reason they have 95% of the market.

To the point:
Open the Package handler, Synaptic. System - Administration - Synaptic.
Fill in your password. Click on the "Search" button. Fill in kgrubeditor in the small windows that opens. Wait a few seconds. If it is in any of the repositories, it will show up. Click on the green square beside kgrubeditor. Choose Mark for installation. Click "Apply" and "Apply" also in the next windows to confirm. That´s it.

Oh, just one more thing: This particular package might not run properly on Ubuntu (no matter where you get it). They seem not to have set the dependencies right. At least on my machine, it tries to start, but won´t.

Typing commands may feel safe to those who know exactly what they mean. But for someone unfamiliar with code, writing code is simply intimidating. In Synaptic you can search for software and when you find it, you are just a few clicks away from success.
This is the only way to make the average Windows user to switch to Ubuntu.
Telling them to write code in the Terminal window gives them the impression that Linux is about 20 years behind Windows. 
If a car could be started both with a cranc (as on the Ford T-model) and with a modern electric motor, why recommend people to use the crank?

---

### Post by egalvan on 2009-03-10
> **Orvar said:**
> Why always recomment the non-graphical way? This only keeps non-geeks from choosing Ubuntu as their default operating system. Most people are happy to click their way through menues to get things done, very few dare to use commands in the Terminal window. MS (sorry to swear) realised this many years ago, abandoned MS-dos and introduced Windows ("inspired" by Macintosh and DR-dos) and that is the main reason they have 95% of the market.


One big reason is that the command line is fairly consistend across distros and releases, where-as GUI is very distro-release specific.
Command line code can be "copy and pasted" to eliminate errors.

such as the ones in your example below...
(used solely to illustrate the above point... the step-by-step is well-written otherwise)

> 
To the point:
Open the Package handler, Synaptic. System - Administration - Synaptic.
Fill in your password. Click on the "Search" button. Fill in kgrubeditor in the small windows that opens.

[COLOR="Red"]oops you forgot the "press the Search button"[/COLOR].
I'll be waiting far longer than a few seconds...

>  Wait a few seconds. If it is in any of the repositories, it will show up. Click on the green square beside kgrubeditor.
[COLOR="Red"]what green square?[/COLOR] there is only a black square with  a light gray inside...
> 
 Choose Mark for installation. Click "Apply" and "Apply" also in the next windows to confirm. That´s it.


and the above step-by-step may not work for Kubuntu or Xubuntu.

whereas 

```
sudo apt-get install qgrubeditor
```

will work on almost all Debian/Ubuntu installs.
and many packages will work across much wider range.

> 
Typing commands may feel safe to those who know exactly what they mean. But for someone unfamiliar with code, writing code is simply intimidating.

It's **useful**, but not **necessary**, to know what the code means.
some 99% is just copy and paste.

>  In Synaptic you can search for software and when you find it, you are just a few clicks away from success.
This is the only way to make the average Windows user to switch to Ubuntu.
Telling them to write code in the Terminal window gives them the impression that Linux is about 20 years behind Windows. 
If a car could be started both with a cranc (as on the Ford T-model) and with a modern electric motor, why recommend people to use the crank?

Again, one reason is the degree of control.

One does not need to write code... one can just copy and paste, with similar mouse movements as GUI.
 Highlight the line in one window, and paste it into another....
what is so "intimidating" about that?

You will find most all of the command line code given in the Absolute Beginner forum to be of the copy&paste variety, with emphasis placed on this simple way of executing commands.

---

### Post by dinofex@gmail.com on 2009-03-20
Folks, the issue at hand is the StartUp Manager screw up in our otherwise wonderful Ubuntu Linux, not the niceties of Linux, which are fading fast for me if I keep running into problems no one seems able to address.  Does anyone have a handle on StartUp Manager NOT STARTING UP?  In a previuos post I printed out the response I got from the OS.  My download managers also are screwing up so my options are limited.  I don't know about you, but I need to start solving issues so I can get to the obvious stuff, instead of having to reinstall Linux AGAIN!

---

