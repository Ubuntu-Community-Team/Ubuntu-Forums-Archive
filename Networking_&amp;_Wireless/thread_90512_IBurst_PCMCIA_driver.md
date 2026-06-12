---
title: "IBurst PCMCIA driver"
date: 2005-11-15
forum: Networking &amp; Wireless
---

### Post by Gimli on 2005-11-15
Hi all, I am currently using a wireless internet network service (IBurst pcmcia card). I know that some people have been working on drivers for this at [http://sourceforge.net/projects/ibdriver/](http://sourceforge.net/projects/ibdriver/)

My problem is that I am not a Linux expert and I am using Ubuntu, not some of the other distros that these guys are working on or writing their text on. Do you guys know of a proper How To based on Ubuntu, or even better a repository you can add to install this driver.

Thanks for the help

---

### Post by mips on 2005-11-15
Maybe contact Screwdriver from the thread below and ask him how the HOWTO is coming along...

[http://ubuntuforums.org/showthread.php?t=54382&highlight=iburst](http://ubuntuforums.org/showthread.php?t=54382&highlight=iburst)

---

### Post by Skrewdriver on 2005-11-15
I still haven't written the iBurst HOWTO (uni exams, moving house etc) but will hopefully do it in the next few weeks. Meanwhile I will help you get your card up and running.

First, I need to know what version of Ubuntu you are using (it helps if you show this in your UbuntuForums profile). I will also need to know what version of the kernel you are running, so open a terminal and enter the following command and let me know the result:
```
uname -r
```
Then run Synaptic and install a package called "Build Essentials"
Then you need to download the iburst drivers source, and also the source for the Roaring Penguin dialer.
1. [ibdriver]("http://sourceforge.net/project/showfiles.php?group_id=138984") (ver 1.2.6)
2. [roaring penguin]("http://www.roaringpenguin.com/penguin/open_source_rp-pppoe.php")

The ibdriver archive file you download will have a file called README.
Read through that, and follow any steps for Debian (or Ubuntu if it gets a mention in the latest version).
Also have a look at the help forum for the ibdriver project .. you will see the problems that I had and the solutions to these problems. Most stemmed from incorrect info in the README

Let me know how it goes and I will help with any problems as they crop up and I will attempt to attend them ASAP.

---

### Post by Gimli on 2005-11-18
Thanks for helping.

I have installed linux-headers, linux-source and build-essencials. Have downloaded the driver and dialer. I am running kernal 2.6.12-9-386.

I extract ibdriver-2.0.0.tar.gz into the /tmp folder.

I 'make' as per the instruction in the readme and then get the following error:

clr@CLR:/tmp/ibdriver-2.0.0$ sudo make
Password:
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/tmp/ibdriver-2.0.0 modules
make: *** /lib/modules/2.6.12-9-386/build: No such file or directory.  Stop.
make: *** [default] Error 2

I have checked, the /lib/modules/2.6.12-9-386/build folder does not exist.

All help appreciated

---

### Post by Gimli on 2005-11-18
OK, 

I have now downloaded ibdriver-1.2.8 as a result of reading the project forum but still get the same message.

clr@CLR:/tmp/ibdriver-1.2.8$ sudo make
Password:
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/tmp/ibdriver-1.2.8 modules
make: *** /lib/modules/2.6.12-9-386/build: No such file or directory.  Stop.
make: *** [default] Error 2

If I create the /build directory I get the following message

clr@CLR:/tmp/ibdriver-1.2.8$ sudo make
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/tmp/ibdriver-1.2.8 modules
make[1]: Entering directory `/lib/modules/2.6.12-9-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.12-9-386/build'
make: *** [default] Error 2

As always help appreciated

---

### Post by Skrewdriver on 2005-11-19
Okay, first off you shouldn't be building anything in the /tmp directory - that is poor form. You should create a new directory in your home directory and do it there.

When you have sorted that out, you need to create a symbolic link for the build directory.
```
sudo ln -s /usr/src/linux-headers-$(uname -r) /lib/modules/$(uname -r)/build 
```

Then you can compile the drivers.
Make sure you are in the directory with the driver source (the one you created off your home directory, not /tmp!)
```
make
sudo make install
```

.. then follow the rest of the README, you should be okay!

---

### Post by Gimli on 2005-11-19
Ok, have followed the insructions and now get the following error.

clr@CLR:~/IBurst pcmcia/ibdriver-1.2.8$ make
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/clr/IBurst pcmcia/ibdriver -1.2.8 modules
make[1]: Entering directory `/lib/modules/2.6.12-9-386/build'
make[1]: *** No rule to make target `pcmcia/ibdriver-1.2.8'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.12-9-386/build'
make: *** [default] Error 2

Any suggestions?

---

### Post by Skrewdriver on 2005-11-19
hmmm .. I'm a bit stumped.

can you please paste (to this thread) the output of the following commands:
```
ls -l /lib/modules/$(uname -r)
ls /lib/modules/$(uname -r)/build
ls /usr/src/linux-headers-$(uname -r)
```

.. see if that offers any clues.

---

### Post by Gimli on 2005-11-20
clr@CLR:~$ ls -l /lib/modules/$(uname -r)
total 1264
drwxr-xr-x   2 root root   4096 2005-11-19 12:03 build
drwxr-xr-x   2 root root   4096 2005-10-29 18:08 initrd
drwxr-xr-x  11 root root   4096 2005-10-29 18:08 kernel
drwxr-xr-x   2 root root   4096 2005-10-29 18:09 madwifi
-rw-r--r--   1 root root 244192 2005-11-20 09:11 modules.alias
-rw-r--r--   1 root root     69 2005-11-20 09:11 modules.ccwmap
-rw-r--r--   1 root root 293696 2005-11-20 09:11 modules.dep
-rw-r--r--   1 root root    813 2005-11-20 09:11 modules.ieee1394map
-rw-r--r--   1 root root   1141 2005-11-20 09:11 modules.inputmap
-rw-r--r--   1 root root  21256 2005-11-20 09:11 modules.isapnpmap
-rw-r--r--   1 root root 226052 2005-11-20 09:11 modules.pcimap
-rw-r--r--   1 root root   1135 2005-11-20 09:11 modules.seriomap
-rw-r--r--   1 root root 123227 2005-11-20 09:11 modules.symbols
-rw-r--r--   1 root root 315491 2005-11-20 09:11 modules.usbmap
drwxr-xr-x   2 root root    360 2005-11-20 09:11 volatile


clr@CLR:~$ ls /lib/modules/$(uname -r)/build
linux-headers-2.6.12-9-386


clr@CLR:~$ ls /usr/src/linux-headers-$(uname -r)
ls: /usr/src/linux-headers-2.6.12-9-386: No such file or directory

---

### Post by Skrewdriver on 2005-11-20
First problem I see is that the symbolic link for the build directory was not created properly. The result of "ls -l" should show the sym link, but it doesn't, so it looks like your "build" directory is an actual directory, and not a link (to another directory). For example, it should look like this:
```
mark@T21:~$ ls -l /lib/modules/$(uname -r)
total 1260
lrwxrwxrwx   1 root root     35 2005-10-20 23:42 build -> /usr/src/linux-headers-2.6.12-9-686
drwxr-xr-x   2 root root   4096 2005-10-20 10:59 initrd
drwxr-xr-x  11 root root   4096 2005-10-20 10:59 kernel
drwxr-xr-x   2 root root   4096 2005-10-20 10:59 madwifi
-rw-r--r--   1 root root 244284 2005-11-21 01:44 modules.alias
-rw-r--r--   1 root root     69 2005-11-21 01:44 modules.ccwmap
-rw-r--r--   1 root root 291854 2005-11-21 01:44 modules.dep
-rw-r--r--   1 root root    813 2005-11-21 01:44 modules.ieee1394map
-rw-r--r--   1 root root   1141 2005-11-21 01:44 modules.inputmap
-rw-r--r--   1 root root  21256 2005-11-21 01:44 modules.isapnpmap
-rw-r--r--   1 root root 226052 2005-11-21 01:44 modules.pcimap
-rw-r--r--   1 root root   1135 2005-11-21 01:44 modules.seriomap
-rw-r--r--   1 root root 123329 2005-11-21 01:44 modules.symbols
-rw-r--r--   1 root root 315491 2005-11-21 01:44 modules.usbmap
drwxr-xr-x   2 root root    360 2005-11-21 01:44 volatile

```
.. in my directory listing the attributes for build are "lrwxrwxrwx". That first 
"l" identifies "build" as a sym link, whereas your "build" has a "d", so it is a plain old directory. So you will have to delete build, and create the sym link. But first there is another problem.

I can't see that you have installed the right linux-headers package.
Enter this command:
```
sudo apt-get install linux-headers-$(uname -r)
```

.. once that is done, go back to my previous post and follow the instructions for creating the symbolic link  for "build". Don't forget to remove the incorrect "build" directory referred to earlier in this post before you attempt to create the sym link.

*(Handy Hint: the best way for copying code from these threads is to highlight the code you want to copy, click with the left button in your terminal window and press the middle mouse button. Otherwise copy & paste as normal)*

---

### Post by Gimli on 2005-11-20
Have done that, feels like we are getting somewhere step by step. Now I get the following error which I have not had before.

clr@CLR:~/IBurst pcmcia/ibdriver-1.2.8$ make
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/clr/IBurst pcmcia/ibdriver -1.2.8 modules
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: co mmand not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: co mmand not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
make[1]: *** No rule to make target `pcmcia/ibdriver-1.2.8'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [default] Error 2

I have checked, gcc-4.0 is installed, could that make a difference?

Els this is the contents of that folder

clr@CLR:/usr/src/linux-headers-2.6.12-9-386/scripts$ ls -l
total 312
drwxr-xr-x  2 root root  4096 2005-11-20 17:59 basic
-rw-r--r--  1 root root   702 2005-06-17 21:48 bin2c.c
-rw-r--r--  1 root root  4036 2005-06-17 21:48 binoffset.c
-rwxr-xr-x  1 root root  1726 2005-06-17 21:48 checkconfig.pl
-rwxr-xr-x  1 root root   529 2005-06-17 21:48 checkincludes.pl
-rw-r--r--  1 root root  3541 2005-06-17 21:48 checkstack.pl
-rwxr-xr-x  1 root root  1905 2005-06-17 21:48 checkversion.pl
-rwxr-xr-x  1 root root 11544 2005-10-10 14:12 conmakehash
-rw-r--r--  1 root root  6130 2005-06-17 21:48 conmakehash.c
-rwxr-xr-x  1 root root  1613 2005-06-17 21:48 extract-ikconfig
-rw-r--r--  1 root root   338 2005-06-17 21:48 gcc-version.sh
-rw-r--r--  1 root root  4796 2005-06-17 21:48 gen_initramfs_list.sh
drwxr-xr-x  2 root root  4096 2005-11-20 17:59 genksyms
-rwxr-xr-x  1 root root 15492 2005-10-10 14:12 kallsyms
-rw-r--r--  1 root root 18105 2005-06-17 21:48 kallsyms.c
drwxr-xr-x  2 root root  4096 2005-11-20 17:59 kconfig
-rwxr-xr-x  1 root root 50916 2005-06-17 21:48 kernel-doc
drwxr-xr-x  2 root root  4096 2005-11-20 17:59 ksymoops
-rwxr-xr-x  1 root root    54 2005-06-17 21:48 Lindent
drwxr-xr-x  2 root root  4096 2005-11-20 17:59 lxdialog
-rw-r--r--  1 root root   801 2005-06-17 21:48 Makefile
-rw-r--r--  1 root root 10017 2005-06-17 21:48 Makefile.build
-rw-r--r--  1 root root  2940 2005-06-17 21:48 Makefile.clean
-rw-r--r--  1 root root  5892 2005-06-17 21:48 Makefile.host
-rw-r--r--  1 root root 10122 2005-06-17 21:48 Makefile.lib
-rw-r--r--  1 root root   825 2005-06-17 21:48 Makefile.modinst
-rw-r--r--  1 root root  3470 2005-06-17 21:48 Makefile.modpost
-rwxr-xr-x  1 root root   941 2005-06-17 21:48 makelst
-rwxr-xr-x  1 root root  2143 2005-06-17 21:48 mkcompile_h
-rw-r--r--  1 root root   563 2005-06-17 21:48 mkmakefile
-rw-r--r--  1 root root  1323 2005-06-17 21:48 mksysmap
-rwxr-xr-x  1 root root   293 2005-06-17 21:48 mkuboot.sh
-rw-r--r--  1 root root    74 2005-06-17 21:48 mkversion
drwxr-xr-x  2 root root  4096 2005-11-20 17:59 mod
-rw-r--r--  1 root root 13375 2005-06-17 21:48 namespace.pl
drwxr-xr-x  2 root root  4096 2005-11-20 17:59 package
-rwxr-xr-x  1 root root  9934 2005-06-17 21:48 patch-kernel
-rw-r--r--  1 root root 11935 2005-06-17 21:48 pnmtologo.c
-rw-r--r--  1 root root  3245 2005-06-17 21:48 reference_discarded.pl
-rw-r--r--  1 root root  3376 2005-06-17 21:48 reference_init.pl
-rw-r--r--  1 root root  3057 2005-06-17 21:48 show_delta
-rwxr-xr-x  1 root root  3051 2005-06-17 21:48 ver_linux
clr@CLR:/usr/src/linux-headers-2.6.12-9-386/scripts$

---

### Post by Skrewdriver on 2005-11-20
You are right on two things, we are getting slowly somewhere (yay!) and the version of GCC is causing a problem. I'm sure if we were both tech wizards we could change the source code so it isn't a problem, but the easy way is just install the earlier verion of GCC. You can do this with Synaptic, or the following command:
```
sudo apt-get install gcc-3.4 gcc-3.4-base
```

.. and have another crack at the compile. I had the same problem when I upgraded to Breezy, and ended up having to go to an internet cafe (at 4am) and download the packages onto a USB stick. I also had to download a few libraries, but I think apt-get should automatically take care of this for you. If not, and you can't work out what they are from the errors, then let me know.

Good luck mate!

---

### Post by Skrewdriver on 2005-11-21
I'll jump ahead here and assume that the make works for the drivers.
Follow the rest of the ibdriver README, but ignore the bit about configuring the Debian dialer. The Roaring Penguin dialer is much easier.

So after [downloading]("http://www.roaringpenguin.com/penguin/open_source_rp-pppoe.php") and extracting the RP dialer source, setup is pretty simple, as they have written scripts to make it so.
First set up the command-line dialer. (make sure you are in the directory with the source and scripts)
```
sudo ./go
```
Follow the prompts, the questions are pretty straightforward.
Then try and connect to the iBurst network..```
pppoe-start
```
If it is up and running, you can check the status with ```
pppoe-status
```
... and when you want to disconnect ```
pppoe-stop
```

An alternate method is to use the RP GUI dialler. I prefer this method.
Set up the GUI dialer...
```
sudo ./go-gui
```
Make sure you allow all users to use it.
Next test the GUI dialler (make sure iBurst is not already connected)
```
tkpppoe &
```
Have a fiddle with it, make sure it works. If you are satisfied it is working, then have it start with every gnome session. From the desktop menus go to **Sytem -> Preferences -> Sessions** , click on the tab for **Startup Programs** , and add tkpppoe. You can also add an icon to the panel if you want. Right click on the panel, select **Add To Panel** and then **Custom Application Launcher**. Call it whatever you want, pick whatever icon you want, but make sure the command is tkppoe

:KS Here endeth the lesson :D . Good luck!


:confused: *(Note: I'm not sure if dialler is spelt with two Ls or one, so I have used both spellings!)*

---

### Post by Gimli on 2005-11-21
Before we get to the dialer, I have to make the drivers first... still errors but thanks for the help sofar. Now the following

clr@CLR:~/IBurst pcmcia/ibdriver-1.2.8$ make
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/clr/IBurst pcmcia/ibdriver -1.2.8 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
make[1]: *** No rule to make target `pcmcia/ibdriver-1.2.8'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [default] Error 2


I installed gcc3.4 that is what was in the error, or does it have to be gcc 3.3 like in your mail.

---

### Post by Skrewdriver on 2005-11-21
You were right to install gcc-3.4 (I edited my earlier post to reflect this).

Can't work out why you would still be getting this error...
Did you set up the symbolic link correctly? *(see the 2nd post in this thread)*
Can you post the results of the following commands:
```
dpkg -l linux-headers*
```
```
ls -l /lib/modules/$(uname -r)
```

---

### Post by Gimli on 2005-11-21
clr@CLR:/$ dpkg -l linux-headers*

Desired=Unknown/Install/Remove/Purge/Hold

| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed

|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: 

uppercase=bad)

||/ Name           Version        Description

+++-==============-==============-============================================

un  linux-headers  <none>         (no description available)

un  linux-headers- <none>         (no description available)

ii  linux-headers- 2.6.12-9.23    Header files related to Linux kernel 

version

ii  linux-headers- 2.6.12-9.23    Linux kernel headers 2.6.12 on 386


clr@CLR:/$ ls -l /lib/modules/$(uname -r)

total 1260

lrwxrwxrwx   1 root root     35 2005-11-20 18:28 build -> 

/usr/src/linux-headers -2.6.12-9-386

drwxr-xr-x   2 root root   4096 2005-10-29 18:08 initrd

drwxr-xr-x  11 root root   4096 2005-10-29 18:08 kernel

drwxr-xr-x   2 root root   4096 2005-10-29 18:09 madwifi

-rw-r--r--   1 root root 244192 2005-11-21 13:50 modules.alias

-rw-r--r--   1 root root     69 2005-11-21 13:50 modules.ccwmap

-rw-r--r--   1 root root 293696 2005-11-21 13:50 modules.dep

-rw-r--r--   1 root root    813 2005-11-21 13:50 modules.ieee1394map
-rw-r--r--   1 root root   1141 2005-11-21 13:50 modules.inputmap

-rw-r--r--   1 root root  21256 2005-11-21 13:50 modules.isapnpmap

-rw-r--r--   1 root root 226052 2005-11-21 13:50 modules.pcimap

-rw-r--r--   1 root root   1135 2005-11-21 13:50 modules.seriomap

-rw-r--r--   1 root root 123227 2005-11-21 13:50 modules.symbols

-rw-r--r--   1 root root 315491 2005-11-21 13:50 modules.usbmap

drwxr-xr-x   2 root root    360 2005-11-21 13:50 volatile

clr@CLR:/$

---

### Post by Skrewdriver on 2005-11-21
I'm stumped. It's the same error you had before, and I'm pretty sure it means some source code is not installed. Try installing the package **linux-kernel-headers** , we'll see if that fixes it.

Also, when you are posting the output from commands can you please format them as code (use the **#** icon on the forum message entry panel) - it uses a monospaced font so it is a bit easier to read long tables of output.

Cheers
- Mark

---

### Post by Gimli on 2005-11-21
I am sorry for this being such a pain but no joy. I have reeinstalled everything from linux-headers, linux source, gcc-3.4 and build-essencial. No luck, still the same message.... no rule to build.....

I would understand if you have had enough

```
clr@CLR:~/IBurst pcmcia/ibdriver-1.2.8$ make
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/clr/IBurst pcmcia/ibdriver-1.2.8 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
make[1]: *** No rule to make target `pcmcia/ibdriver-1.2.8'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [default] Error 2
clr@CLR:~/IBurst pcmcia/ibdriver-1.2.8$

```

I suppose it looks like it is not going to happen

---

### Post by Gimli on 2005-11-21
Oh my word... I suppose this shows just how much of a novice I am with linux.:o 

Just before I gave up I tried something... a long shot hehehe.

I extracted the files to /home/clr/IBurst pcmcia/ibdriver-1.2.8 and the make never worked so I took the space out of the one folder's name like in:
/home/clr/IBurst_pcmcia/ibdriver-1.2.8

and it worked.

So now for the rest.:D

---

### Post by Gimli on 2005-11-21
:)  I am glad to report that thanks to your help I have been able to get it up and running, in fact I am posting this while connected on my UTC.

I do however have another problem, the connection is very slow, about dial-up speed.. 56kbps.  This is a 1Mbps service so do you know how to tweek this think to get the speed up?

Chiao

---

### Post by Skrewdriver on 2005-11-21
I'm stoked that it is working. Just when you were about to give up!

[COLOR="Red"][SIZE="4"]GIVING UP IS NOT THE UBUNTU WAY![/SIZE][/COLOR]
*Sometimes it can be like banging your head against a rock, but if we pull together as a community and bang even more heads against more rocks, eventually something will give. That is the Ubuntu way.*

I find that with iBurst the speed varies considerably, depending on a few factors:
[LIST=1]
[*]your location
[*]signal strength at that location
[*]atmospheric conditions
[*]if a plane (or UFO) is flying overhead (serious!)
[*]mobile phones and other interference generators
[/LIST]

One little tweak that did work for me is I changed the options in **/etc/modprobe.d/iburst** to the following:
```
options ib-pcmcia debug=0 interval=10
```
The interval option is the important bit, in early versions of the driver it was set too high. Otherwise, there may be some esoteric network setting you can tweak, but networking is not my forte.

I see that in the ibdriver tar file there is some Python code for a sensor or something. I might have a look at it and see if I can do something with it utilising my (currently non-existant) Python skills. I might get around to it after I finish the iBurst HOW-TO. Yeah right! ;)

---

### Post by Gimli on 2005-11-22
The only line I have in that file is 

```
options ib-net ifname="eth"
```

Have I missed something?

---

### Post by Skrewdriver on 2005-11-22
No, you should be fine. I think the default value is set low enough in the version of the driver that you installed. I haven't changed my configuration since version 1.2.1

To quote the README:

> [ibdriver >= 1.2.6]
      In the initial release of ibdriver, the pcmcia poll period was defaulted
      to a value which limited throughput. The fix was to manually set the
      pcmcia 'interval' option to 20 (or less).

      As of ibdriver 1.2.6, the default value is sufficiently small (it is 10),
      so the option should not need to be changed until iBurst is capable of
      throughput over 1.5 Mbps.      
   [ibdriver >= 1.2.6]

---

### Post by Gimli on 2005-11-22
Thanks a lot those who developed the driver. A special thanks to Screwdriver that stuck to it and helped me get this thing working on my notebook.

Viva Ubuntu Viva!

---

### Post by z4pp4 on 2006-02-13
Hi There
I've done everything in this thread and a few others, but could still not get iburst working.
I can see the PCMCIA card, can dial a PPPoE session and can do all this automatically when the card is plugged in. I've loaded ibdriver and also all the pppoe software that is included in the Ubuntu breezy repository. 

When I ping the local IP address on the ppp tunnel, it responds. But when I try to ping the far end, or the DNS, or even google.com I get the following message:

```
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
...(more)

```
I suspect it might be a firewalling issue, since I've loaded both firestarter and bastille (in the past).

When I look in the syslog (the whole dialup procedure), I've got the following relevant items:

During the card insertion and dialup:
```
Feb 12 19:09:30 localhost pppd[7717]: Plugin rp-pppoe.so loaded.
Feb 12 19:09:30 localhost pppd[7724]: pppd 2.4.3 started by root, uid 0
Feb 12 19:09:31 localhost pppd[7724]: PPP session is 1
Feb 12 19:09:31 localhost pppd[7724]: Using interface ppp0
Feb 12 19:09:31 localhost pppd[7724]: Connect: ppp0 <--> eth1
Feb 12 19:09:31 localhost pppd[7724]: Couldn't increase MTU to 1500
Feb 12 19:09:31 localhost pppd[7724]: Couldn't increase MRU to 1500
Feb 12 19:09:35 localhost pppd[7724]: PAP authentication succeeded
Feb 12 19:09:35 localhost pppd[7724]: peer from calling number 02:C0:EE:01:10:BB authorized
Feb 12 19:09:35 localhost pppd[7724]: not replacing default route to eth0 [10.7.146.1]
Feb 12 19:09:35 localhost pppd[7724]: Cannot determine ethernet address for proxy ARP
Feb 12 19:09:35 localhost pppd[7724]: local  IP address 196.2.103.251
Feb 12 19:09:35 localhost pppd[7724]: remote IP address 196.2.120.1
Feb 12 19:09:35 localhost pppd[7724]: primary   DNS address 196.30.31.193
Feb 12 19:09:35 localhost pppd[7724]: secondary DNS address 196.46.70.1
```

During the ping:
```
Feb 12 19:17:11 localhost kernel: [4295249.171000] Unknown OutputIN= OUT=ppp0 SRC=196.2.103.251 DST=196.2.120.1 LEN=84 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=ICMP TYPE=8 CODE=0 ID=1056 SEQ=1 
Feb 12 19:17:12 localhost kernel: [4295250.171000] Unknown OutputIN= OUT=ppp0 SRC=196.2.103.251 DST=196.2.120.1 LEN=84 TOS=0x00 PREC=0x00 TTL=64 ID=1 DF PROTO=ICMP TYPE=8 CODE=0 ID=1056 SEQ=2 
```

The relevant ifconfigs looks like this:
```
eth1      Link encap:Ethernet  HWaddr 02:C0:EE:01:10:BA  
          inet6 addr: fe80::c0:eeff:fe01:10ba/64 Scope:Link
          UP BROADCAST RUNNING NOARP DYNAMIC  MTU:1500  Metric:1
          RX packets:356 errors:0 dropped:0 overruns:0 frame:0
          TX packets:296 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12126 (11.8 KiB)  TX bytes:7524 (7.3 KiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:196.2.103.251  P-t-P:196.2.120.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1392  Metric:1
          RX packets:51 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:3820 (3.7 KiB)  TX bytes:54 (54.0 b)

```

And when I do an iptables --list, it looks like this:
```
Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LSI        all  --  anywhere             anywhere            

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             10.255.255.255      
DROP       all  --  224.0.0.0/8          anywhere            
DROP       all  --  anywhere             224.0.0.0/8         
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level warning prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN tcpmss match 1400:1536 TCPMSS clamp to PMTU 
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level warning prefix `Unknown Forward' 

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level warning prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level warning prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level warning prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level warning prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level warning prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  224.0.0.0/8          anywhere            
DROP       all  --  anywhere             224.0.0.0/8         
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level warning prefix `Unknown Output'

```

Anybody got any good places to look for a solutions?
It would be much appreciated, since I wanna dump Win for ubuntu, and the only thing still stopping me is the iburst connectivity...

---

### Post by mips on 2006-02-13
Start by disabling Firstarter/Bastille and see what happens.

---

### Post by z4pp4 on 2006-02-13
Thanks, in the mean time I've figured that one out.

To recap others on the problem (I think the Wi-Fi guys might have the same problems here):

I used the Firestarter firewall software. *Unfortunately* it seems that this software was written with the most basic single connection scenario where the user has 1 internet connection, and not the more complicated laptop scenario. Thus, I had to set the "internet facing" connection every time I started iburst (which is not automated enough.)

This does not gel well with what I needed, so I removed firestarter and resorted to iptables rules. I basically created a script by asking a few guys in the office what would be good settings. The following is a snippet of the shell script that does the job:
```

# IPTABLE rules

/sbin/iptables -F
/sbin/iptables -X
/sbin/iptables -P INPUT DROP
/sbin/iptables -P OUTPUT DROP
/sbin/iptables -P FORWARD DROP
/sbin/iptables -N LOGGING

#Kill invalid packets (illegal combinations of flags)
/sbin/iptables -A INPUT -m state --state INVALID -j DROP
/sbin/iptables -A FORWARD -m state --state INVALID -j DROP
# First send everything to logging
/sbin/iptables -A INPUT -s 0.0.0.0/0 -d 0.0.0.0/0 -j LOGGING
/sbin/iptables -A OUTPUT -s 0.0.0.0/0 -d 0.0.0.0/0 -j LOGGING

# Disallow and log Fragmented Packets
/sbin/iptables -A LOGGING -f -i eth0 -j LOG --log-prefix "Fragmented Packet"
/sbin/iptables -A INPUT -f -i eth0 -j DROP

# Refuse spoofed packets pretending to be from the external interface's IP address

# Loopback
# Refuse packets claiming to be to the loopback interface
/sbin/iptables -A INPUT -i eth0 -s 127.0.0.0/8 -j DROP
/sbin/iptables -A LOGGING -i eth0 -s 127.0.0.0/8 -j LOG --log-prefix "Loopback packets from ExtInt"
/sbin/iptables -A OUTPUT -o eth0 -s 127.0.0.0/8 -j DROP

# Accept local packets
/sbin/iptables -A INPUT -i lo -j ACCEPT
/sbin/iptables -A OUTPUT -o lo -j ACCEPT

# ping flood protection
/sbin/iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -j ACCEPT

#Allow established connections
/sbin/iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
/sbin/iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow ze connections....
iptables -A OUTPUT -j ACCEPT
```

This can be saved under */etc/init.d/yourname*. Just remember to do **update-rc.d yourname defaults**.
When this script is run, it should clean out your firewalling rules and implement its own.  

The connection works flawlessly now, even with an additional Ethernet connection.

As an additional homework assignment, I want to multi-home this connection with my office ethernet connection and get 2x the internet speed...

Side note: Do you think this setup is secure, or do you think there may be some worthwhile additions to the iptables rules?

---

### Post by mips on 2006-02-13
To use both links you will have to implement some form of routing which might not work that well.

Look at Section 4.2  [http://www.tldp.org/HOWTO/Adv-Routing-HOWTO/index.html](http://www.tldp.org/HOWTO/Adv-Routing-HOWTO/index.html)

btw. multi-homing refers to IP Aliases or subinterfacing in Linux. Multihoming would be the correct terminology.

I have very little experience with IP tables and usually entrust that function to a GUI like firestarter or Guarddog etc. Coming from a cisco environment I just find them hard to read after you have become accustomed to cisco access-lists.

---

### Post by Skrewdriver on 2006-02-23
I finally got around to writing the iBurst PCMCIA how-to :) .
Check the thread out [here]("http://ubuntuforums.org/showthread.php?p=763148")

---

