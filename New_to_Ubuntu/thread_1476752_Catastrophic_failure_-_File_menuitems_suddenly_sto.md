---
title: "Catastrophic failure - File menuitems suddenly stopped working..."
date: 2010-05-08
forum: New to Ubuntu
---

### Post by resander on 2010-05-08
Have only had Ubuntu 10.04 for a couple of days and had planned to install applications this morning (Saturday 8 May). At present only the codeblocks IDE and GPS Ada IDE are installed. 

So, turned the PC on and read email and online newspapers for 30 minutes as I always do. On completion the Update manager dialog popped up or maybe I clicked the Update icon on the top taskbar (don't remember). The dialog said there were about 5 updates available and I clicked the 'Install these' choice as I always do when there are updates. The update took 3-4 minutes. On completion there was a red stop sign on the top bar and when hovering over it the toolbar text  'an error occurred when checking for updates' showed.
I right-clicked the stop sign but none of the menu choices 'show updates, install updates, check for updates' worked. Nothing happened, nothing popped up.

When clicking any menu item with a Folder icon on the Places menu the taskbar at the bottom showed the message 'Opening so-and-so' superimposed on a folder  icon. This stays up for about 20-30 seconds and then it disappears. The folder is not opening. Same happens when I click the 'Computer' entry on the Places menu except the text is 'Starting Computer'.

This happens for the super-user and all three normal users that I added.

Some entries on the Administration menu have stopped working too: Language support, Software Sources, Synaptic manager, System Monitor.
Ubuntu Software Centre fails in the same way, but all the other items on the Application menu seem to work, Internet, Office, Brasero and so on.
 

The disk is working. I can see the files and navigate between directories from the command line and when I start from the 10.04 Live CD I can see the files and folders in root partition and home partition of my newly installed 10.04 when I click on Places of the Live CD.

The PC was working last night and I turned it off in an orderly fashion as I always do.     

I don't know where to start. 
How can I fix this?

---

### Post by dracayr on 2010-05-08
are there error messages when you try to start these applications from command line? (to open the currend directory, type 'nautilus .' in a command line

---

### Post by resander on 2010-05-08
dracayr:
Many thanks for the tip.

Calling nautilus shows there is a problem.

meijin@meijin-desktop:~$ nautilus
nautilus: /usr/local/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/lib/libexempi.so.3)

I actually installed build-essentials from synaptic on day one. This contains compiler libraries, most likely also libstdc++.so.6 the version above. Then installed codeblocks IDE build 6181. That worked fine. 

Also needed to install GNAT GPL Ada IDE system, which is not in synaptic. Obtained it from Libre [www.adacore.com](www.adacore.com) as a tar file. Unpacked this and ran the doinstall script provided, but I had problems and it did not work properly when installed in the suggested directory /usr/gnat. Googled and found that other people installed into /usr/local, so I tried that and it installed and ran ok. But doinstall may have overwritten libstc++.so.6 GLIBCXX_3.4.11 with a different version (how do I find out the version?) and possibly other files too. 

Here is info about the current libstd*: (meijin is the superusername I gave when I installed 10.04)

meijin@meijin-desktop:/usr/local/lib$ ls -l libstd*

-rw-r--r-- 1 meijin meijin 2256168 2009-05-19 23:52 libstdc++.a
-rwxr-xr-x 1 meijin meijin     964 2009-05-19 23:52 libstdc++.la
lrwxrwxrwx 1 meijin meijin      19 2010-05-07 12:02 libstdc++.so -> libstdc++.so.6.0.10
lrwxrwxrwx 1 meijin meijin      19 2010-05-07 12:02 libstdc++.so.6 -> libstdc++.so.6.0.10
-rwxr-xr-x 1 meijin meijin 1246162 2010-05-06 10:01 libstdc++.so.6.0.10

I want to delete all libstd++ entries above and remove build-essentials package and then reinstall it. The Synaptic does not work now.

What commandline APT commands do I need to use to remove previous build-essentials and reinstall build-essentials?

---

### Post by resander on 2010-05-08
I tried sudo apt-get --reinstall install build-essentials and it also complains about the same missing libcstd++ file.

Snookered!

I think I have to reinstall Ubuntu 10.04.

---

