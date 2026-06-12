---
title: "Nvidia Drivers"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by Rloewen on 2009-07-09
Ok, i must be a total noob but here is what i get from the lspci terminal command

00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)

Ok now what do i do next to get the correct driver installed?

---

### Post by Daniel1994 on 2009-07-09
Have you tried System>Administration>Hardware Drivers?

---

### Post by Rloewen on 2009-07-09
I tried the version 180 and that caused a blank screen on boot.  which version should i use?
173 or 96?

---

### Post by random turnip on 2009-07-09
Before trying to instal drivers manually, do an update, this will often instal the drivers it's self if you have only recently started using Ubuntu, restart the system after to check though.

---

### Post by Rloewen on 2009-07-09
my system is up to date and i will try to reboot again.

---

### Post by Rloewen on 2009-07-09
and i get a blank screen

---

### Post by alexlafreniere on 2009-07-09
What is each driver marked as? Is 180 an experimental driver? If so, try 173.

---

### Post by Short__Error on 2009-07-09
Go to Applications> add/remove  and serach for nvidia install the nvidua xserver settings and then the latest driver that it offers there it will either be 177, 180

---

### Post by Rloewen on 2009-07-09
i already installed the driver.  seems that 173 is the version i needed but i had to go through the syanptic package manager

---

### Post by Rloewen on 2009-07-09
this is just not working

---

### Post by Rloewen on 2009-07-09
now it says i am not using the Nvidia X Driver for the control panel

---

### Post by Rloewen on 2009-07-09
how can i do this manually?

---

### Post by Trophy on 2009-07-09
I have been trying to solve this very same issue for a while. Third party driver installation throught the interface left me with a blank screen as well. Tried the manual installation process but also ended up with a blank screen. It is very frustrating. I'll keep an eye on your post, hopefully someone can find a solution here.

---

### Post by Rloewen on 2009-07-09
all i want is a screen res of 1280X1024.  thats it.  i dont care about games.  I got a mac for that.

---

### Post by Trophy on 2009-07-09
Good luck with it. I found 2 guides.

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

and the NVIDIA one which gets very indepth: 
[http://us.download.nvidia.com/XFree86/Linux-x86/185.18.14/README/index.html](http://us.download.nvidia.com/XFree86/Linux-x86/185.18.14/README/index.html)

---

### Post by Short__Error on 2009-07-09
Go to your terminal and run the following ```
sudo nvidia-xconfig
``` and the reboot

---

### Post by Rloewen on 2009-07-09
> **Short__Error said:**
> Go to your terminal and run the following ```
sudo nvidia-xconfig
``` and the reboot
ok that failed several times. and trophy that crashed my system

---

### Post by Rloewen on 2009-07-09
i am using ubuntu 9.04 btw

I have an amd 64 Atholon but its the 32bit version not the 64bit

---

### Post by beastrace91 on 2009-07-09
I am decently sure the 18x.xx drivers are only from 7xxx series cards and newer, what you want is the latest 177.xx driver which as of today is 177.82.

[177.82 64bit Download](ftp://download.nvidia.com/XFree86/Linux-x86_64/177.82/NVIDIA-Linux-x86_64-177.82-pkg2.run)

[177.82 32bit Download](ftp://download.nvidia.com/XFree86/Linux-x86/177.82/NVIDIA-Linux-x86-177.82-pkg1.run)

You may want to pull these up on a separate computer or write them down as we have to kill X (the GUI) to manually install the drivers.

Installing them is decently simple, download the proper file from one of the above links to your home folder.

Then press ctrl+alt+f1 to drop down to a tty login. Log into your system.

Now run the following commands in order:
```
sudo /etc/init.d/gdm stop //Stop X, use kdm instead of gdm if you use KDE
sudo rmmod nvidia //Remove old drivers that you have installed
```

Now make your driver file you downloaded excutable by running ```
chmod +x MyNividaDrivers.run
``` You can find the exact name of the file by running ls if you do not remember it off hand.

Then install the drivers AS ROOT using the following: ```
sudo ./MyNividaDrivers.run
```

Follow the on screen instructions, they are decently straight forward.

Lastly start X again and you should be live with ```
sudo /etc/init.d/gdm start
```

Hope this helps,
~Jeff

---

### Post by Trophy on 2009-07-09
Did it crash or can you Ctr-Alt-F1 to the prompt. If this lets you to the prompt then the un-intsall and restore of your xorg.conf file will allow you back into the GUI

---

### Post by Rloewen on 2009-07-09
i am going to try this after i update a bunch of stuff.  also, i think the athalon i have is the 32bit version, but i am not sure how many flavors it came in.  the Common name for the proc is AMD 64 Athalon.  Can someone check that for me?  I could be using the entirely wrong version

---

### Post by Rloewen on 2009-07-09
> **Trophy said:**
> Did it crash or can you Ctr-Alt-F1 to the prompt. If this lets you to the prompt then the un-intsall and restore of your xorg.conf file will allow you back into the GUI
it crashed.  the tty interface barely worked after that

---

### Post by Rloewen on 2009-07-09
> **Rloewen said:**
> it crashed.  the tty interface barely worked after that
here is the proc info from emachines

AMD Athlon&#8482; 64 3500+ processor

can anyone tell me if thats the 32 or 64 bit version?

---

### Post by beastrace91 on 2009-07-09
The driver is determined by your OS install, you have a 64bit processor but if you installed 32bit Ubuntu then you want the 32bit driver.

~Jeff

---

### Post by Trophy on 2009-07-09
Sorry. I take it you managed to get the NVIDIA unstalled and restore the xorg.conf then?

---

### Post by Rloewen on 2009-07-09
nope.  It doesnt want to work

this is the output

```

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Thu Jul  9 06:47:52 2009
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 177.82.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.28-13-generic/build'
-> Kernel output path: '/lib/modules/2.6.28-13-generic/build'
ERROR: If you are using a Linux 2.4 kernel, please make sure
       you either have configured kernel sources matching your
       kernel or the correct set of kernel headers installed
       on your system.
       
       If you are using a Linux 2.6 kernel, please make sure
       you have configured kernel sources matching your kernel
       installed on your system. If you specified a separate
       output directory using either the "KBUILD_OUTPUT" or
       the "O" KBUILD parameter, make sure to specify this
       directory with the SYSOUT environment variable or with
       the equivalent nvidia-installer command line option.
       
       Depending on where and how the kernel sources (or the
       kernel headers) were installed, you may need to specify
       their location with the SYSSRC environment variable or
       the equivalent nvidia-installer command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.

```

---

### Post by beastrace91 on 2009-07-09
Does it say where it fails? I know it has to compile a custom kernel during the install process, do you have the build-essential package installed so it can do this?

~Jeff

---

### Post by Rloewen on 2009-07-09
> **beastrace91 said:**
> Does it say where it fails? I know it has to compile a custom kernel during the install process, do you have the build-essential package installed so it can do this?

~Jeff
you might want to give me instructions on how to do that

properly i might add

---

### Post by beastrace91 on 2009-07-09
Make sure you have an active internet connection on the system and then run ```
sudo apt-get install build-essential
``` The repeat the install instructions in my first post. Sorry I left this piece out before, must have slipped my mind.

~Jeff

---

### Post by Rloewen on 2009-07-09
np

---

### Post by Rloewen on 2009-07-09
> **beastrace91 said:**
> Make sure you have an active internet connection on the system and then run ```
sudo apt-get install build-essential
``` The repeat the install instructions in my first post. Sorry I left this piece out before, must have slipped my mind.

~Jeff
even with this it still failed.

```

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Thu Jul  9 07:05:03 2009
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 177.82.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.28-13-generic/build'
-> Kernel output path: '/lib/modules/2.6.28-13-generic/build'
ERROR: If you are using a Linux 2.4 kernel, please make sure
       you either have configured kernel sources matching your
       kernel or the correct set of kernel headers installed
       on your system.
       
       If you are using a Linux 2.6 kernel, please make sure
       you have configured kernel sources matching your kernel
       installed on your system. If you specified a separate
       output directory using either the "KBUILD_OUTPUT" or
       the "O" KBUILD parameter, make sure to specify this
       directory with the SYSOUT environment variable or with
       the equivalent nvidia-installer command line option.
       
       Depending on where and how the kernel sources (or the
       kernel headers) were installed, you may need to specify
       their location with the SYSSRC environment variable or
       the equivalent nvidia-installer command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.

```

---

### Post by Rloewen on 2009-07-09
ok i seem to be missing something obvious, but for the life of me i cant figure out what.

---

### Post by Rloewen on 2009-07-09
what about the 173 binary in the add remove area?  xorg?

---

### Post by beastrace91 on 2009-07-09
Ok just to clear a few things up, you are using an Nvidia 6100, you have tried the 177.82 drivers and the 180.xx drivers from the repositories and both get you a black screen?

Do the drivers actually say they install correctly or does the above error occur during the installation, if it occurs during the installation at what point does it occur (does it say it compiled the kernel successfully or does it not get this far, etc.)?

~Jeff

---

### Post by Rloewen on 2009-07-09
just the 180 gave me the black screen.  177 wont install

---

### Post by Rloewen on 2009-07-09
The error shows up before the compile occurs i think.  also its a geforce 6100

---

### Post by beastrace91 on 2009-07-09
Can you confirm that please? Also try running the following before installing the 177.82 drivers ```
sudo apt-get install build-essential linux-headers-`uname -r`
```

~Jeff

---

### Post by Rloewen on 2009-07-09
> **beastrace91 said:**
> Can you confirm that please? Also try running the following before installing the 177.82 drivers ```
sudo apt-get install build-essential linux-headers-`uname -r`
```~Jeff
huh?  in the tty terminal?

---

### Post by beastrace91 on 2009-07-09
Yes in terminal.

~Jeff

---

### Post by Rloewen on 2009-07-09
> **beastrace91 said:**
> Can you confirm that please? Also try running the following before installing the 177.82 drivers ```
sudo apt-get install build-essential linux-headers-`uname -r`
```~Jeff
output from terminal

pokesomi@server1:~$ lspci | grep VGA
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)

---

### Post by Rloewen on 2009-07-09
it says i have the latest version and could not find the linux-headers- 'uname -r'

---

### Post by beastrace91 on 2009-07-09
> **beastrace91 said:**
> does the above error occur during the installation, if it occurs during the installation at what point does it occur (does it say it compiled the kernel successfully or does it not get this far, etc.)?

~Jeff

---

### Post by Rloewen on 2009-07-09
the error occurs before it even tries to compile.

---

### Post by beastrace91 on 2009-07-09
And what does it say when it throws the error...

~Jeff

---

### Post by Rloewen on 2009-07-09
ERROR: If you are using a Linux 2.4 kernel, please make sure
       you either have configured kernel sources matching your
       kernel or the correct set of kernel headers installed
       on your system.
       
       If you are using a Linux 2.6 kernel, please make sure
       you have configured kernel sources matching your kernel
       installed on your system. If you specified a separate
       output directory using either the "KBUILD_OUTPUT" or
       the "O" KBUILD parameter, make sure to specify this
       directory with the SYSOUT environment variable or with
       the equivalent nvidia-installer command line option.
       
       Depending on where and how the kernel sources (or the
       kernel headers) were installed, you may need to specify
       their location with the SYSSRC environment variable or
       the equivalent nvidia-installer command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

That

---

### Post by Rloewen on 2009-07-09
so i am guessing i am missing something again.

---

### Post by Trophy on 2009-07-09
> **Rloewen said:**
> it says i have the latest version and could not find the linux-headers- 'uname -r'

II had the same error and the typed in  linux-headers-2.6.28-13-generic (being my kernel version which i check with cat /proc/version instead of the `uname` and it did something ... not sure if this correct through

---

### Post by beastrace91 on 2009-07-09
What kernel are you using? Run ```
uname -r
``` in terminal and post the output.

~Jeff

---

### Post by goldenbrown on 2009-07-09
> **Rloewen said:**
> Ok, i must be a total noob but here is what i get from the lspci terminal command

00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)

Ok now what do i do next to get the correct driver installed?

At blank screen press Ctrl Alt and F1

Login 

Password
 
Type the following cammand

sudo aptitude remove xserver-xorg

Then type

"sudo aptitude install xserver-xorg"

reboot after command finished

---

### Post by Rloewen on 2009-07-09
> **goldenbrown said:**
> At blank screen press Ctrl Alt and F1

Login 

Password
 
Type the following cammand

sudo aptitude remove xserver-xorg

Then type

"sudo aptitude install xserver-xorg"

reboot after command finished

Ok well be aware that i have dropped down to 8.10 but from what i have been told the procedure is still the same?

---

### Post by Rloewen on 2009-07-09
> **beastrace91 said:**
> What kernel are you using? Run ```
uname -r
``` in terminal and post the output.

~Jeff

for 8.10 2.6.27-14-genaric

---

