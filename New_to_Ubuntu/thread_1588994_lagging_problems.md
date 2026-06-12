---
title: "lagging problems"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by crystal_ssc on 2010-10-05
hello to everyone i have a lag prob with my ubuntu....everytime i play a video or an audio my pc starts making glitches...i tried everything i could find related to graphics,sound i 've spent hours of typing codes to my terminal but the prob is still on....i would appreciate any help from everyone...thanx very much and sorry if my english is not so good....love from greece

---

### Post by NightwishFan on 2010-10-05
First best option is to post your graphic card model and Ubuntu version.

---

### Post by crystal_ssc on 2010-10-05
> **NightwishFan said:**
> First best option is to post your graphic card model and Ubuntu version.i am not sure what card i have i cant remember...although its a new series i got it last year....also i have the 10.04.version

---

### Post by NightwishFan on 2010-10-05
It is simple to find out, just open a terminal and run this command:
```
lshw -C display
```

---

### Post by crystal_ssc on 2010-10-05
ati radeon hd 4670....yeap thats it i rememberd...thanx

---

### Post by NightwishFan on 2010-10-05
Try using the proprietary driver from System -> Administration -> Hardware Drivers. On the other hand if you are using it now, try disabling it.

---

### Post by crystal_ssc on 2010-10-05
i disable it and i got a crash report that said : fglrx 2:8.723.1-oubuntu5 failed to install or upgrade....

---

### Post by NightwishFan on 2010-10-05
Thats fine, open a terminal and run this command:
```
sudo apt-get -f install
```

Post any error messages here. Using CODE tags. (The # symbol in the posting toolbar)

---

### Post by crystal_ssc on 2010-10-05
it sais that the fglrx package will be removed...do i want to continue Y N ? :P

---

### Post by NightwishFan on 2010-10-05
Yes, of course. By all means. :)

---

### Post by crystal_ssc on 2010-10-05
theres a bunch of thing i dont understand...so take a look

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  sdparm dkms
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  fglrx
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 60.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 178476 files and directories currently installed.)
Removing fglrx ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--remove):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for ureadahead ...
Errors were encountered while processing:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by NightwishFan on 2010-10-05
Sounds iffy, like someone manually did something. Ok, try this:
```
sudo apt-get install fglrx && sudo apt-get purge fglrx
```

---

### Post by crystal_ssc on 2010-10-05
a bunch of things i dont uderstand 
```

```Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  sdparm dkms
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  fglrx
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 60.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 178476 files and directories currently installed.)
Removing fglrx ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--remove):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for ureadahead ...
Errors were encountered while processing:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)```

```

---

### Post by crystal_ssc on 2010-10-05
sorry for the last one it was a mistake

---

### Post by NightwishFan on 2010-10-05
Did you run my second command or was that the output of it?

---

### Post by crystal_ssc on 2010-10-05
```

``` Errors were encountered while processing:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by crystal_ssc on 2010-10-05
there a lot of things right now want me to post all o f them?

---

### Post by crystal_ssc on 2010-10-05
yes i run ```
 sudo apt-get install fglrx && sudo apt-get purge fglrx
``` 
and now there are a lot of stuff going on...want to post them all?

---

### Post by NightwishFan on 2010-10-05
Yes please. I am wondering what happened to get the system in this state. :/

---

### Post by crystal_ssc on 2010-10-05
```
 ~$ sudo apt-get install fglrx && sudo apt-get purge fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fglrx is already the newest version.
The following packages were automatically installed and are no longer required:
  sdparm
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/18.2MB of archives.
After this operation, 0B of additional disk space will be used.
Selecting previously deselected package fglrx.
(Reading database ... 178477 files and directories currently installed.)
Preparing to replace fglrx 2:8.723.1-0ubuntu5 (using .../fglrx_2%3a8.723.1-0ubuntu5_i386.deb) ...
Unpacking replacement fglrx ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up fglrx (2:8.723.1-0ubuntu5) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group gl_conf) doesn't exist.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.723.1 DKMS files...
Building only for 2.6.32-25-generic
Building for architecture i686
Building initial module for 2.6.32-25-generic
Done.

fglrx.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.32-25-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)

Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-25-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  sdparm dkms
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  fglrx*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 60.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 178628 files and directories currently installed.)
Removing fglrx ...
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/mesa/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--purge):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Processing triggers for python-support ...
Errors were encountered while processing:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by NightwishFan on 2010-10-05
I will do some research and get back to you.

---

### Post by NightwishFan on 2010-10-05
This seems to be a known bug. Did you by any chance add a ppa to do with graphics drivers?
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/555721](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/555721)

Here is a possible solution:
[http://www.khattam.info/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error-2009-08-04.html](http://www.khattam.info/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error-2009-08-04.html)

---

### Post by crystal_ssc on 2010-10-05
any luck?

---

### Post by crystal_ssc on 2010-10-05
no i didnt add any ppa...i dont even know what it is....

---

### Post by NightwishFan on 2010-10-05
Ok, try this for me:
```
sudo dpkg --force-all --remove fglrx
```

---

### Post by crystal_ssc on 2010-10-05
i put first ```
sudo aptitude update
``` and then ```
sudo aptitude -f install
``` and i think its kinda cool have a look ```
Writing extended state information... Done
Hit http://gr.archive.ubuntu.com lucid Release.gpg
Ign http://gr.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US           
Ign http://gr.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US     
Hit http://archive.canonical.com lucid Release.gpg                           
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US
Ign http://gr.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://gr.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://gr.archive.ubuntu.com lucid-updates Release.gpg
Hit http://archive.canonical.com lucid Release 
Ign http://gr.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US   
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release                          
Ign http://gr.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://gr.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://gr.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://archive.canonical.com lucid/partner Packages                         
Hit http://gr.archive.ubuntu.com lucid Release                                  
Hit http://security.ubuntu.com lucid-security/main Packages                     
Hit http://gr.archive.ubuntu.com lucid-updates Release                          
Hit http://gr.archive.ubuntu.com lucid/main Packages                            
Hit http://gr.archive.ubuntu.com lucid/restricted Packages                      
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources 
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources                  
Hit http://gr.archive.ubuntu.com lucid/main Sources                             
Hit http://gr.archive.ubuntu.com lucid/restricted Sources                       
Hit http://security.ubuntu.com lucid-security/multiverse Packages               
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://gr.archive.ubuntu.com lucid/universe Packages   
Hit http://gr.archive.ubuntu.com lucid/universe Sources    
Hit http://gr.archive.ubuntu.com lucid/multiverse Packages
Hit http://gr.archive.ubuntu.com lucid/multiverse Sources
Hit http://gr.archive.ubuntu.com lucid-updates/main Packages
Hit http://gr.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://gr.archive.ubuntu.com lucid-updates/main Sources
Hit http://gr.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://gr.archive.ubuntu.com lucid-updates/universe Packages
Hit http://gr.archive.ubuntu.com lucid-updates/universe Sources
Hit http://gr.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://gr.archive.ubuntu.com lucid-updates/multiverse Sources
Reading package lists... Done                              

crystal@crystal-desktop:~$ sudo aptitude -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  sdparm{u} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/18.2MB of archives. After unpacking 381kB will be freed.
Do you want to continue? [Y/n/?] y
Selecting previously deselected package fglrx.
(Reading database ... 178477 files and directories currently installed.)
Preparing to replace fglrx 2:8.723.1-0ubuntu5 (using .../fglrx_2%3a8.723.1-0ubuntu5_i386.deb) ...
Unpacking replacement fglrx ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
(Reading database ... 178628 files and directories currently installed.)
Removing sdparm ...
Processing triggers for man-db ...
Setting up fglrx (2:8.723.1-0ubuntu5) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group gl_conf) doesn't exist.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.723.1 DKMS files...
Building only for 2.6.32-25-generic
Building for architecture i686
Building initial module for 2.6.32-25-generic
Done.

fglrx.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.32-25-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)

Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-25-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
 
```

---

### Post by NightwishFan on 2010-10-05
Yes, it did the same thing as "sudo apt-get -f install" I mentioned earlier. The package still wont remove.

---

### Post by crystal_ssc on 2010-10-05
so now i try your last code u gave me?

---

### Post by NightwishFan on 2010-10-05
Yes, do so. I hope I can help you fix this.

---

### Post by crystal_ssc on 2010-10-05
i quess something not good....

```
~$ sudo dpkg --force-all --remove fglrx
(Reading database ... 178616 files and directories currently installed.)
Removing fglrx ...
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/mesa/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--remove):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Processing triggers for python-support ...
Errors were encountered while processing:
 fglrx

```

---

### Post by NightwishFan on 2010-10-05
Grr. It is being stubborn. We might have to do this the hard way. I will get back to you.

---

### Post by crystal_ssc on 2010-10-05
i hope too :P just kidding i know am a pain in the *** i just dont know what to do

---

### Post by NightwishFan on 2010-10-05
It is fine I think I got it. :D I looked up what a diversion was and came across this:

First:
```
sudo dpkg-divert --rename --remove /usr/lib/libGL.so.1.2
```
Then:
```
sudo dpkg-divert --rename --remove /usr/lib32/libGL.so.1.2
```
Last:
```
sudo dpkg --force-all --purge fglrx
```

Lets see how that goes.

---

### Post by crystal_ssc on 2010-10-05
```
 sudo dpkg-divert --rename --remove /usr/lib/libGL.so.1.2
Removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
crystal@crystal-desktop:~$ udo dpkg-divert --rename --remove /usr/lib32/libGL.so.1.2 sudo dpkg --force-all --purge fglrx
The program 'udo' is currently not installed.  You can install it by typing:
sudo apt-get install udo

```i just saw your last code

---

### Post by crystal_ssc on 2010-10-05
the whole thing 

```
sudo dpkg-divert --rename --remove /usr/lib/libGL.so.1.2
Removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
crystal@crystal-desktop:~$ udo dpkg-divert --rename --remove /usr/lib32/libGL.so.1.2 sudo dpkg --force-all --purge fglrx
The program 'udo' is currently not installed.  You can install it by typing:
sudo apt-get install udo
crystal@crystal-desktop:~$ sudo dpkg --force-all --purge fglrx
(Reading database ... 178462 files and directories currently installed.)
Removing fglrx ...
update-initramfs: deferring update (trigger activated)
Purging configuration files for fglrx ...
update-initramfs: deferring update (trigger activated)
dpkg: warning: while removing fglrx, directory '/usr/lib/fglrx/etc/ati' not empty so not removed.
dpkg: warning: while removing fglrx, directory '/usr/lib/fglrx/etc' not empty so not removed.
dpkg: warning: while removing fglrx, directory '/usr/lib/fglrx' not empty so not removed.
Processing triggers for ureadahead ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-25-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

---

### Post by NightwishFan on 2010-10-05
Sorry rerun the code above again. I made a mistake and edited. For the second line you forgot to add an s for sudo. It happens.

---

### Post by crystal_ssc on 2010-10-05
ok doing from the top is that ok?

---

### Post by NightwishFan on 2010-10-05
Yes, all three lines in order.

---

### Post by crystal_ssc on 2010-10-05
and th results are...


```
 crystal@crystal-desktop:~$ sudo dpkg-divert --rename --remove /usr/lib/libGL.so.1.2
No diversion `any diversion of /usr/lib/libGL.so.1.2', none removed
crystal@crystal-desktop:~$ sudo dpkg-divert --rename --remove /usr/lib32/libGL.so.1.2
No diversion `any diversion of /usr/lib32/libGL.so.1.2', none removed
crystal@crystal-desktop:~$ sudo dpkg --force-all --purge fglrx
dpkg: warning: ignoring request to remove fglrx which isn't installed.

```

out of the topic question should i activate my graphs card or leave it unactivated?

---

### Post by NightwishFan on 2010-10-05
Seems ok! No, do not activate. Now do one final thing for me.
```
sudo dpkg-reconfigure xserver-xorg
```

Then reboot.

---

### Post by crystal_ssc on 2010-10-05
i did it reboot it and before the log in screen there was a mesage that ubuntu are runniung on low graphs and that couldn load fglrx...and then there was was list on how i want to run my ubuntu and put on low graphs for just one session

---

### Post by NightwishFan on 2010-10-05
Ok, try this. (I kind of expected this as well, has to make things difficult).
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.nwbackup
```

Then reboot.

---

### Post by crystal_ssc on 2010-10-05
ok i did it...annd i think its fine...i ll tell you why....before today when my ubuntu was loading (you know when it says ubuntu and there are dots loading) my resolution was awful and know it got fixed...i think thats good right?????

---

### Post by NightwishFan on 2010-10-05
Should be good. Please tell me if you notice any problems. I will try to help. Sorry for any hassle (if any) all my codes caused. :)

---

### Post by crystal_ssc on 2010-10-05
i think its fine i started a video on my vlc and it was fine..no glitches...thank you very very very much...you are my messia....if there are any problems i ll let the forum know....thanx for everything and i hope get to help some time....but there are minimun odds for that happening....thanx again

---

### Post by alphacrucis2 on 2010-10-05
Try downloading the hot fix version of the Catalyst 10.9 driver from AMD/ATI. Make sure fglrx is removed via

```
sudo apt-get remove fglrx
```

AMD support website:

[QUOTE="AMD"]ATI Catalyst&#8482; Linux Driver broken after Linux kernel security update[/QUOTE]


[http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx]("http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx")

Create a folder called ati under your home dir. Then Download the hot fix archive and extract the installer to the ati folder you just created. Then from terminal:

```
cd ati
sudo sh ./<the name of the installer you extracted> --buildpkg Ubuntu/lucid
```

DON"T TYPE IN THE < > around the installer name.

If successful it will create a number of deb files. To install them type:

```
sudo dpkg -i *.deb
```


This fixed the problem for me.

---

