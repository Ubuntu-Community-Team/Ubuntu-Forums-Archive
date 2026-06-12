---
title: "don't understand. need simpler terms"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by pleasantashes on 2009-08-01
i don't understand how to do this

[http://www.palmix.org/r5u870-en.html](http://www.palmix.org/r5u870-en.html)

can someone translate it into simpler terms and steps

---

### Post by f37u5g0d on 2009-08-01
Be very specific.  What don't you understand?

---

### Post by wojox on 2009-08-01
OK it depends on where you downloaded it. Open a terminal:

Untar it:

```
tar xvfz r5u870-0.10.1.tar.gz
```

Go into that new directory:

```
cd r5u870-0.10.1
```

Then:

```
sudo make
```
 
and 

```
sudo make install
```

Finally:

```
modprobe r5u870 
```

---

### Post by pleasantashes on 2009-08-01
> **wojox said:**
> OK it depends on where you downloaded it. [/code]

downloaded to Desktop

did step one... got

tar: r5u870-0.10.1.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
ashley@ashley-laptop:~$

---

### Post by birdwin on 2009-08-01
You've got to change to the Desktop directory. So before the tar command, type:

cd Desktop

---

### Post by f37u5g0d on 2009-08-01
silly pleasantashes.  You have to navigate the terminal!  When you start a terminal it is in "/home/you" (shorthand = ~) It is at a place in the file system always similar to nautilus.  You can use "ls" to "list" the files in the current directory and you can use "cd" to change directory (as in "cd /home/you/Desktop").  Then you can untar the file there! :)

BTW IRC channels have a much quicker reponse time than forums :)

---

### Post by Buce on 2009-08-01
Before you do any of those things, type 'cd Desktop'.

Also, when typing long filenames, just type the first couple characters, then hit 'Tab', and see if autocompletion works for it.

---

### Post by pleasantashes on 2009-08-01
> **Buce said:**
> Before you do any of those things, type 'cd Desktop'.

did that
step 1 worked
went to do step 2
got

bash: cd: r5u870-0.10.1: No such file or directory


do i need to re-navigate
and if so to where

---

### Post by pleasantashes on 2009-08-01
nvm. that was renavigating. ahhh confused

---

### Post by pleasantashes on 2009-08-01
still can't figure it out

---

### Post by birdwin on 2009-08-01
> **pleasantashes said:**
> still can't figure it out
Download the tar to your desktop. Open a shell, and type the following:

cd Desktop
tar xvfz r5u870-0.10.1.tar.gz

Now type 'ls'. You should see a folder called r5u870-0.10.1. Now type:

cd r5

and hit [TAB]. It should complete the folder name. Hit enter. Now type:

sudo make
sudo make install
modprobe r5u870

and let us know what happens.

---

### Post by pleasantashes on 2009-08-01
> **birdwin said:**
> Download the tar to your desktop. Open a shell, and type the following:

cd Desktop
tar xvfz r5u870-0.10.1.tar.gz

Now type 'ls'. You should see a folder called r5u870-0.10.1. Now type:

cd r5

and hit [TAB]. It should complete the folder name. Hit enter. Now type:

sudo make
sudo make install
modprobe r5u870

and let us know what happens.

close...really close...but didnt work.
heres the last bit from terminal

ashley@ashley-laptop:~/Desktop/r5u870$ sudo make install
make -C /lib/modules/2.6.28-14-generic/build M=/home/ashley/Desktop/r5u870 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-14-generic'
  CC [M]  /home/ashley/Desktop/r5u870/r5u870_md.o
In file included from /home/ashley/Desktop/r5u870/r5u870_md.c:55:
/home/ashley/Desktop/r5u870/usbcam.h:36:29: error: media/video-buf.h: No such file or directory
make[2]: *** [/home/ashley/Desktop/r5u870/r5u870_md.o] Error 1
make[1]: *** [_module_/home/ashley/Desktop/r5u870] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-14-generic'
make: *** [all] Error 2
ashley@ashley-laptop:~/Desktop/r5u870$ modprobe r5u870
FATAL: Module r5u870 not found.

---

### Post by donkyhotay on 2009-08-01
Your missing some dependencies, probably the linux headers since that was the last directory used. Try:
```

sudo apt-get install linux-headers-2.6.28-14-generic

```
then try doing the 
```

sudo make install

```
again


//edit: I could be wrong about the 2.6.28-14 part, depends on exactly what kernel version you are using.

---

### Post by pleasantashes on 2009-08-01
> **donkyhotay said:**
> Your missing some dependencies, probably the linux headers since that was the last directory used. Try:
```

sudo apt-get install linux-headers-2.6.28-14-generic

```then try doing the 
```

sudo make install

```again
doing it over again before this i found error in the sudo make

will try this and post again

---

### Post by pleasantashes on 2009-08-01
nope didn't work

here is what I got with sudo make

ashley@ashley-laptop:~/Desktop/r5u870$ sudo make
[sudo] password for ashley:
make -C /lib/modules/2.6.28-14-generic/build M=/home/ashley/Desktop/r5u870 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-14-generic'
  CC [M]  /home/ashley/Desktop/r5u870/r5u870_md.o
In file included from /home/ashley/Desktop/r5u870/r5u870_md.c:55:
/home/ashley/Desktop/r5u870/usbcam.h:36:29: error: media/video-buf.h: No such file or directory
make[2]: *** [/home/ashley/Desktop/r5u870/r5u870_md.o] Error 1
make[1]: *** [_module_/home/ashley/Desktop/r5u870] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-14-generic'
make: *** [all] Error 2



this error would explain why the install didn't work so I probably need to fix this first

---

### Post by philinux on 2009-08-01
I think that maybe the build-essential package needs installing.

[apt:build-essential](apt:build-essential)

---

### Post by pleasantashes on 2009-08-01
> **philinux said:**
> I think that maybe the build-essential package needs installing.

[apt:build-essential](apt:build-essential)

and i do that how?

---

### Post by birdwin on 2009-08-01
sudo apt-get install build-essential

---

### Post by pleasantashes on 2009-08-01
> **pleasantashes said:**
> and i do that how?


got that....package installer

now i'll try again and see

---

### Post by pleasantashes on 2009-08-01
got

ashley@ashley-laptop:~/Desktop/r5u870$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

trying sudo make again

---

### Post by pleasantashes on 2009-08-01
> **pleasantashes said:**
> got

ashley@ashley-laptop:~/Desktop/r5u870$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

trying sudo make again

build-essential isn't it cuz i got the same error for sudo make

ashley@ashley-laptop:~/Desktop/r5u870$ sudo make
make -C /lib/modules/2.6.28-14-generic/build M=/home/ashley/Desktop/r5u870 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-14-generic'
  CC [M]  /home/ashley/Desktop/r5u870/r5u870_md.o
In file included from /home/ashley/Desktop/r5u870/r5u870_md.c:55:
/home/ashley/Desktop/r5u870/usbcam.h:36:29: error: media/video-buf.h: No such file or directory
make[2]: *** [/home/ashley/Desktop/r5u870/r5u870_md.o] Error 1
make[1]: *** [_module_/home/ashley/Desktop/r5u870] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-14-generic'
make: *** [all] Error 2

---

### Post by pleasantashes on 2009-08-01
can someone help me fix that error

---

### Post by Sealbhach on 2009-08-01
The problem is here:
```

/home/ashley/Desktop/r5u870/usbcam.h:36:29: error: media/video-buf.h: No such file or directory
```That driver is probably not up to date for Jaunty 9.04.

You've got a Ricoh webcam have you? I've tried that driver a number of times over the past few versions of Ubuntu and it's worked briefly for me but not for long, I've kind of given up on it.

There's a long thread here all about it.

[http://ubuntuforums.org/showthread.php?t=968381](http://ubuntuforums.org/showthread.php?t=968381)


If Ricoh released the code for it then we could get a proper driver but there's no way they're going to do that.

---

### Post by pleasantashes on 2009-08-01
> **Sealbhach said:**
> 

You've got a Ricoh webcam have you? I've tried that driver a number of times over the past few versions of Ubuntu and it's worked briefly for me but not for long, I've kind of given up on it.

I don't know quite what it is.
It is attatched to my Vaio VGN-sz240

So is it impossible?

---

### Post by pleasantashes on 2009-08-01
nvm read more of the thread...I will try what it says

---

### Post by Sealbhach on 2009-08-01
> **pleasantashes said:**
> I don't know quite what it is.
It is attatched to my Vaio VGN-sz240

So is it impossible?

Copy this into a terminal and paste the result here:

```

 lsusb | grep 05ca
```

I don't know if it's impossible, some people on that thread seem say that they got it working fine. Anytime I've tried it, it's worked briefly but then stopped working after reboot. I'm not really bothered about a webcam so I haven't put much effort into solving it.

.

---

### Post by pleasantashes on 2009-08-01
lsusb | grep 05ca
Bus 001 Device 003: ID 05ca:1830 Ricoh Co., Ltd Visual Communication Camera VGP-VCC2

---

### Post by pleasantashes on 2009-08-01
i think i followed the directions right but the forum way didnt make it work

---

### Post by Sealbhach on 2009-08-01
> **pleasantashes said:**
> lsusb | grep 05ca
Bus 001 Device 003: ID 05ca:1830 Ricoh Co., Ltd Visual Communication Camera VGP-VCC2

Yup, that's the same camera as mine. I've got mine working again so follow these steps to see if it can work for you.

1. Grab the source package from here (click on the link): 

[http://bitbucket.org/ahixon/r5u87x/get/32a27008b8b9.bz2](http://bitbucket.org/ahixon/r5u87x/get/32a27008b8b9.bz2)

2. Once it's downloaded, stick it in your home folder (where Pictures, Documents, Videos are). Right-click on the package and select "Extract Here". This will extract a package called r5u87x-32a27008b8b9.

3. Right-click on that package. This will create a folder called r5u87x.

4. Install this: ```
sudo apt-get install nautilus-open-terminal
```

5. Right-click on the folder r5u87x and select Open in terminal.

6. type "make" and press enter.

7.  type "make rules" and press enter.

8. type "sudo make install" and press enter.

9. type "r5u87x-loader" and press enter.

10. Reboot.

To test the camera, install the program Cheese from Add/Remove. Once installed you'll find it in the Applications/Graphics menu.

Give it a try and see how you do.:)

.

---

### Post by pleasantashes on 2009-08-03
> **Sealbhach said:**
> 
6. type "make" and press enter.


got another error

ashley@ashley-laptop:~/r5u87x$ make
cc -g -Wall -DHAVE_CONFIG_H -DUCODE_PATH=\"/usr/lib/r5u87x/ucode/r5u87x-%vid%-%pid%.fw\"  `pkg-config --cflags glib-2.0 libusb` -c loader.c loader.h
Package glib-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `glib-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'glib-2.0' found
Package libusb was not found in the pkg-config search path.
Perhaps you should add the directory containing `libusb.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libusb' found
loader.c:28:18: error: glib.h: No such file or directory
loader.c:29:25: error: glib/gstdio.h: No such file or directory
loader.c:30:17: error: usb.h: No such file or directory
In file included from loader.c:32:
loader.h:42: error: expected declaration specifiers or ‘...’ before ‘gint’
loader.c:38: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
loader.c:39: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘force_clear’
loader.c:40: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘no_load’
loader.c:42: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
loader.c:43: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘dump_ucode’
loader.c:44: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘reload’
loader.c:46: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘entries’
loader.c:71: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
loader.c:89: error: expected declaration specifiers or ‘...’ before ‘gint’
loader.c: In function ‘find_device’:
loader.c:91: error: ‘gint’ undeclared (first use in this function)
loader.c:91: error: (Each undeclared identifier is reported only once
loader.c:91: error: for each function it appears in.)
loader.c:91: error: expected ‘;’ before ‘i’
loader.c:95: warning: implicit declaration of function ‘usb_get_busses’
loader.c:95: warning: assignment makes pointer from integer without a cast
loader.c:96: error: dereferencing pointer to incomplete type
loader.c:99: error: dereferencing pointer to incomplete type
loader.c:99: error: dereferencing pointer to incomplete type
loader.c:101: error: ‘i’ undeclared (first use in this function)
loader.c:102: error: dereferencing pointer to incomplete type
loader.c:103: error: dereferencing pointer to incomplete type
loader.c:104: error: dereferencing pointer to incomplete type
loader.c:106: error: ‘version’ undeclared (first use in this function)
loader.c: At top level:
loader.c:121: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_upload’
loader.c:203: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_status’
loader.c:220: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_version’
loader.c:239: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_enable’
loader.c:256: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_clear’
loader.c:277: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
loader.c:291: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘load_firmware’
loader.c:411: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘main’
loader.h:21:18: error: glib.h: No such file or directory
loader.h:42: error: expected declaration specifiers or ‘...’ before ‘gint’
make: *** [loader.o] Error 1

---

### Post by Sealbhach on 2009-08-03
OK, it's complaining that it's not finding certain libraries that it needs. Install this package and try again:
```

sudo apt-get install build-essential 
```

My webcam is still working fine after I did that the other day, even after a few reboots so it's good.

.

---

### Post by oldos2er on 2009-08-03
> **pleasantashes said:**
> 
Package glib-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `glib-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'glib-2.0' found
Package libusb was not found in the pkg-config search path.
Perhaps you should add the directory containing `libusb.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libusb' found


 This is telling you to install libglib2.0-dev and libusb-1.0-0-dev

---

### Post by pleasantashes on 2009-08-04
> **Sealbhach said:**
> OK, it's complaining that it's not finding certain libraries that it needs. Install this package and try again:
```

sudo apt-get install build-essential 
```
.

It says nothing needed to be done

```
ashley@ashley-laptop:~$ sudo apt-get install build-essential
[sudo] password for ashley: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by Sealbhach on 2009-08-04
OK, that's fine you've already installed a package that's needed to "make" your driver. As oldos2er pointed out, you also need to install these two packages:

libglib2.0-dev and libusb-1.0-0-dev     

So run this command to install them:

```
sudo apt-get install libglib2.0-dev libusb-1.0-0-dev     
```Then go back and go through the how-to that I showed you before and attempt step 6 again.

.

---

### Post by pleasantashes on 2009-08-06
> **Sealbhach said:**
> OK, that's fine you've already installed a package that's needed to "make" your driver. As oldos2er pointed out, you also need to install these two packages:

libglib2.0-dev and libusb-1.0-0-dev     

So run this command to install them:

```
sudo apt-get install libglib2.0-dev libusb-1.0-0-dev     
```Then go back and go through the how-to that I showed you before and attempt step 6 again.

.

installed them
reattempted step 6
got another error

```
ashley@ashley-laptop:~/r5u87x$ make
cc -g -Wall -DHAVE_CONFIG_H -DUCODE_PATH=\"/usr/lib/r5u87x/ucode/r5u87x-%vid%-%pid%.fw\"  `pkg-config --cflags glib-2.0 libusb` -c loader.c loader.h
Package libusb was not found in the pkg-config search path.
Perhaps you should add the directory containing `libusb.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libusb' found
loader.c:28:18: error: glib.h: No such file or directory
loader.c:29:25: error: glib/gstdio.h: No such file or directory
loader.c:30:17: error: usb.h: No such file or directory
In file included from loader.c:32:
loader.h:42: error: expected declaration specifiers or ‘...’ before ‘gint’
loader.c:38: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
loader.c:39: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘force_clear’
loader.c:40: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘no_load’
loader.c:42: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
loader.c:43: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘dump_ucode’
loader.c:44: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘reload’
loader.c:46: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘entries’
loader.c:71: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
loader.c:89: error: expected declaration specifiers or ‘...’ before ‘gint’
loader.c: In function ‘find_device’:
loader.c:91: error: ‘gint’ undeclared (first use in this function)
loader.c:91: error: (Each undeclared identifier is reported only once
loader.c:91: error: for each function it appears in.)
loader.c:91: error: expected ‘;’ before ‘i’
loader.c:95: warning: implicit declaration of function ‘usb_get_busses’
loader.c:95: warning: assignment makes pointer from integer without a cast
loader.c:96: error: dereferencing pointer to incomplete type
loader.c:99: error: dereferencing pointer to incomplete type
loader.c:99: error: dereferencing pointer to incomplete type
loader.c:101: error: ‘i’ undeclared (first use in this function)
loader.c:102: error: dereferencing pointer to incomplete type
loader.c:103: error: dereferencing pointer to incomplete type
loader.c:104: error: dereferencing pointer to incomplete type
loader.c:106: error: ‘version’ undeclared (first use in this function)
loader.c: At top level:
loader.c:121: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_upload’
loader.c:203: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_status’
loader.c:220: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_version’
loader.c:239: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_enable’
loader.c:256: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_clear’
loader.c:277: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
loader.c:291: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘load_firmware’
loader.c:411: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘main’
loader.h:21:18: error: glib.h: No such file or directory
loader.h:42: error: expected declaration specifiers or ‘...’ before ‘gint’
make: *** [loader.o] Error 1

```

---

### Post by oldos2er on 2009-08-06
"No package 'libusb' found"

```
 sudo apt-get install libusb-dev
```

---

### Post by pleasantashes on 2009-08-06
> **oldos2er said:**
> "No package 'libusb' found"

```
 sudo apt-get install libusb-dev
```

almost got it. got to last step but got

```
ashley@ashley-laptop:~/r5u87x$ r5u87x-loader
r5u87x firmware loader v0.2

Searching for device...
Found camera: 05ca:1830
Warning: Failed to get microcode status.

Error: Failed to upload firmware to device: Operation not permitted (code -1).
Try running as root?

```

---

### Post by wojox on 2009-08-06
```
sudo r5u87x-loader
```

---

### Post by pleasantashes on 2009-08-06
got through all steps successfully but cam is not opening in cheese

---

### Post by Sealbhach on 2009-08-06
> **pleasantashes said:**
> got through all steps successfully but cam is not opening in cheese

OK, to get more feedback on what's happening, open cheese in the terminal, just type 

```
cheese
```

and press enter. You will also need to reboot to make sure the driver has loaded OK.

.

---

### Post by pleasantashes on 2009-08-07
> **Sealbhach said:**
> OK, to get more feedback on what's happening, open cheese in the terminal, just type 

```
cheese
```and press enter. You will also need to reboot to make sure the driver has loaded OK.

.

did reboot and just did it again to check. when cheese opens I still just get the no camera found message

---

### Post by Sealbhach on 2009-08-07
> **pleasantashes said:**
> did reboot and just did it again to check. when cheese opens I still just get the no camera found message

Ok, all I can suggest is to run through this procedure again:

[http://ubuntuforums.org/showpost.php?p=7718181&postcount=29](http://ubuntuforums.org/showpost.php?p=7718181&postcount=29)

It worked for me and you have exactly the same camera so it should work for you. Mine is still working.

.

---

### Post by pleasantashes on 2009-08-08
> **Sealbhach said:**
> Ok, all I can suggest is to run through this procedure again:

[http://ubuntuforums.org/showpost.php?p=7718181&postcount=29](http://ubuntuforums.org/showpost.php?p=7718181&postcount=29)

It worked for me and you have exactly the same camera so it should work for you. Mine is still working.

.

did it again. cheese still isn't detecting it. could something need to be changed in cheese?

---

### Post by Sealbhach on 2009-08-08
> **pleasantashes said:**
> did it again. cheese still isn't detecting it. could something need to be changed in cheese?

It could be, open up Cheese and go to Edit/Preferences and see if your camera is listed.

Another thing to try is put this in a teminal:

```
gstreamer-properties
```

This will open a dialog box, select video and click Test in the Input Device section, hopefully this will show a working webcam.

Also install Skype and see if the webcam works there, it works for me.

.

---

### Post by pleasantashes on 2009-08-08
> **Sealbhach said:**
> It could be, open up Cheese and go to Edit/Preferences and see if your camera is listed.

Another thing to try is put this in a teminal:

```
gstreamer-properties
```This will open a dialog box, select video and click Test in the Input Device section, hopefully this will show a working webcam.

Also install Skype and see if the webcam works there, it works for me.

.

in edit/preferences my cam is not listed

---

### Post by Sealbhach on 2009-08-08
> **pleasantashes said:**
> in edit/preferences my cam is not listed

Anything happen with gstreamer-properties?

Also make sure you have all the gstreamer plugins installed:

```
sudo apt-get install gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-ffmpeg gstreamer0.10-gnomevfs gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse  gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pulseaudio gstreamer0.10-schroedinger gstreamer0.10-tools gstreamer0.10-x libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 phonon-backend-gstreamer totem-gstreamer
```

.

---

### Post by pleasantashes on 2009-08-09
> **Sealbhach said:**
> Anything happen with gstreamer-properties?

Also make sure you have all the gstreamer plugins installed:

```
sudo apt-get install gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-ffmpeg gstreamer0.10-gnomevfs gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse  gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pulseaudio gstreamer0.10-schroedinger gstreamer0.10-tools gstreamer0.10-x libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 phonon-backend-gstreamer totem-gstreamer
```.

right now it is installing more gstreamer plugins. after that i will try again and then check the gstreamer-properties

---

### Post by pleasantashes on 2009-08-09
> **Sealbhach said:**
> Anything happen with gstreamer-properties?

Also make sure you have all the gstreamer plugins installed:

```
sudo apt-get install gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-ffmpeg gstreamer0.10-gnomevfs gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse  gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pulseaudio gstreamer0.10-schroedinger gstreamer0.10-tools gstreamer0.10-x libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 phonon-backend-gstreamer totem-gstreamer
```.

with gstreamer-properties i got

```
ashley@ashley-laptop:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'

```

and when testing i got the multi-color bar screen you get when the cam is not detected

---

### Post by Sealbhach on 2009-08-09
Right. Let's just see if the firmware loaded OK, open a terminal (it doesn't matter what folder you're in) and run this command:

```
r5u87x-loader
```You should get feedback like ths:


> 
r5u87x firmware loader v0.2

Searching for device...
Found camera: 05ca:183b
Camera reports positive microcode state.
Camera reports microcode version 0x0131.
Not doing anything - camera already setup.

Successfully uploaded firmware to device 05ca:183b!Please post whatever response you get to this command.

.

---

### Post by pleasantashes on 2009-08-10
> **Sealbhach said:**
> Right. Let's just see if the firmware loaded OK, open a terminal (it doesn't matter what folder you're in) and run this command:

```
r5u87x-loader
```You should get feedback like ths:


Please post whatever response you get to this command.

.

yep. I got
```
ashley@ashley-laptop:~$ sudo r5u87x-loader
[sudo] password for ashley: 
r5u87x firmware loader v0.2

Searching for device...
Found camera: 05ca:1830
Camera reports positive microcode state.
Camera reports microcode version 0x0100.
Not doing anything - camera already setup.

Successfully uploaded firmware to device 05ca:1830!

```

---

### Post by Sealbhach on 2009-08-10
> **pleasantashes said:**
> yep. I got
```
ashley@ashley-laptop:~$ sudo r5u87x-loader
[sudo] password for ashley: 
r5u87x firmware loader v0.2

Searching for device...
Found camera: 05ca:1830
Camera reports positive microcode state.
Camera reports microcode version 0x0100.
Not doing anything - camera already setup.

Successfully uploaded firmware to device 05ca:1830!

```

Right, I don't know why it's not working then. Check in Synaptic that you have libv4l installed. It's just occurred to me that this might depend on a certain kernel version, the version I have is 2.6.28-15-generic.

Check what you've got using the command "uname -a".

Did you try Skype, see if it works in that?

Also check what modules you have loaded, these are mine using the command:

```
lsmod | grep uvcvideo
``````
uvcvideo               69640  0 
compat_ioctl32         18304  1 uvcvideo
videodev               45184  2 uvcvideo,compat_ioctl32
v4l1_compat            23940  2 uvcvideo,videodev
```Compare yours and see if any of them are different.

I'm just about out of ideas after that.:)

.

---

### Post by pleasantashes on 2009-08-10
> **Sealbhach said:**
> Right, I don't know why it's not working then. Check in Synaptic that you have libv4l installed. It's just occurred to me that this might depend on a certain kernel version, the version I have is 2.6.28-15-generic.

Check what you've got using the command "uname -a".

Did you try Skype, see if it works in that?

Also check what modules you have loaded, these are mine using the command:

```
lsmod | grep uvcvideo
``````
uvcvideo               69640  0 
compat_ioctl32         18304  1 uvcvideo
videodev               45184  2 uvcvideo,compat_ioctl32
v4l1_compat            23940  2 uvcvideo,videodev
```Compare yours and see if any of them are different.

I'm just about out of ideas after that.:)

.

for uname-a i got
```
ashley@ashley-laptop:~$ uname -a
Linux ashley-laptop 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686 GNU/Linux

```

for lsmod | grep uvcvideo i get
```

uvcvideo               63368  0 
compat_ioctl32          9344  1 uvcvideo
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev

```

will try skype now

---

### Post by Sealbhach on 2009-08-10
Ok, possibly the kernel version makes a different, as mine is 2.6.28.15. Also, the version of Cheese I'm using is 2.26.0.


.

---

### Post by pleasantashes on 2009-08-11
> **Sealbhach said:**
> Ok, possibly the kernel version makes a different, as mine is 2.6.28.15. Also, the version of Cheese I'm using is 2.26.0.


.
I have the same version of Cheese.

Can I update my kernel version?

---

### Post by Sealbhach on 2009-08-11
> **pleasantashes said:**
> I have the same version of Cheese.

Can I update my kernel version?

You can do that fairly easily by going into System/Administration/Software Sources, click on the Updates tab and tick the box "Pre-released updates (Jaunty proposed)".

Then run update manager and the newer kernel should show up as avaialble. 

Once you have it installed, you will need to rerun the loading of the firmware. Give it a go and see how you do. After that I don't know - any luck with Skype?

.

---

### Post by pleasantashes on 2009-08-19
skype also did not detect my cam.
just updated my kernel.
going to go through the process again.

---

### Post by pleasantashes on 2009-08-19
nope. still not working.

:frown:

---

### Post by Sealbhach on 2009-08-19
> **pleasantashes said:**
> nope. still not working.

:frown:

I dunno dude, it worked for me. Sorry. Now, you might be interested in this - I have been experimenting with Karmic Koala (next release of Ubuntu) and it detects and works with the camera automatically, without me having to do anything. Why not download an ISO of Karmic, load it up on a Live CD or USB and see if it works for you?

You can get an iso of Karmic here:

[http://cdimage.ubuntu.com/releases/karmic/alpha-4/](http://cdimage.ubuntu.com/releases/karmic/alpha-4/)

Give it a try and let me know if it works. If it does, then you need only wait until October to get a working webcam.

.

---

### Post by pleasantashes on 2009-08-19
i will try it out later

thanks for all of your help, despite it not working

<3 Ashley

---

### Post by Venlaar on 2009-08-21
I am having almost exactly the same problem. I have the Ricoh 05ca:1837 on the Sony VGN-FZ180E. I have gone through the steps you posted Sealbhach 
[http://ubuntuforums.org/showpost.php?p=7718181&postcount=29]("http://ubuntuforums.org/showpost.php?p=7718181&postcount=29")
but had slightly different results. I also had to install the gstreamer plugins, libglib2.0-dev, libusb-1.0-0-dev and libusb-dev.
Cheese looks as though it is looking for the cam but never finds it. When I close cheese I get the following:
```
david@david-laptop:~$ cheese

(cheese:4606): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(cheese:4606): GStreamer-CRITICAL **: gst_object_unref: assertion `object != NULL' failed

(cheese:4606): GStreamer-CRITICAL **: gst_object_unref: assertion `object != NULL' failed

```

I am running:
```
Linux david-laptop 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux
```
and have cheese version 2.26.0.

When I run gstreamer-properties I get a window with two images side by side from my camera at the top 1/3 and just green screen for the bottom 2/3rds. 

I ran xawtv /dev/video0 and get a picture but it is upside down and mirrored. It has no buttons to reverse horizontal or vertical.

As a side note prior to trying the exact steps as you have them Sealbhach I misunderstood how to get the file from [http://bitbucket.org/ahixon/r5u87x/get/32a27008b8b9.bz2]("http://bitbucket.org/ahixon/r5u87x/get/32a27008b8b9.bz2") and instead downloaded it from [http://www.palmix.org/download/r5u870_k2.6.27.tar.bz2]("http://www.palmix.org/download/r5u870_k2.6.27.tar.bz2")

After trying to make, make install and modprobe r5u870 from the folder r5u870_k2.6.27 after extracting, the camera worked under ekiga. That is until I rebooted. Then it wouldn't work under ekiga but was working successfully under xawtv /dev/video0. xawtv had buttons to reverse the horizontal and vertical so I was able to get an accurate image under it. But cheese didn't see it at all.

I don't know if any of this helps to see what might be preventing it from working but I thought it was interesting.

Anyone have any other thoughts on getting this camera working?

---

### Post by Venlaar on 2009-08-21
Oh and also after I just rebooted again the camera is working under ekiga but once again is upside down and mirrored.

---

### Post by Sealbhach on 2009-08-21
> **Venlaar said:**
> 

As a side note prior to trying the exact steps as you have them Sealbhach I misunderstood how to get the file from [http://bitbucket.org/ahixon/r5u87x/get/32a27008b8b9.bz2](http://bitbucket.org/ahixon/r5u87x/get/32a27008b8b9.bz2) and instead downloaded it from [http://www.palmix.org/download/r5u870_k2.6.27.tar.bz2](http://www.palmix.org/download/r5u870_k2.6.27.tar.bz2)


Well, maybe the version you got from palmix.org is outdated, you can see in the filename it is for kernel 2.6.27. If you just click on the link I gave it should just download for you. Did it not do that?

.

---

### Post by Venlaar on 2009-08-21
I think the 1st time I tried the link I was just being too impatient and so I thought it wasn't working. When I downloaded it yesterday I clicked on it and waited and then it did show up for download. The camera is now working in both Ekiga and xawtv but it's upside down and mirrored. I've seen in other threads mention of a patch to fix the inversion but I'm not sure of where to get it or how to apply it. Also still don't know why cheese is hanging so much. Any ideas about the patch?

---

### Post by Sealbhach on 2009-08-21
> **Venlaar said:**
> I I've seen in other threads mention of a patch to fix the inversion but I'm not sure of where to get it or how to apply it. Also still don't know why cheese is hanging so much. Any ideas about the patch?

I'm sorry I don't know about the patch. I updated my system yesterday and now Cheese is not working for me... ah well. 


There's a big thread [here]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=968381&page=13") about our webcams, have a look through some recent posts, you might get some clues.

.

---

### Post by Venlaar on 2009-08-23
Thanks. I'll give it a look through tomorrow if I get some free time.

---

### Post by pleasantashes on 2009-11-06
> **Sealbhach said:**
> Yup, that's the same camera as mine. I've got mine working again so follow these steps to see if it can work for you.

1. Grab the source package from here (click on the link): 

[http://bitbucket.org/ahixon/r5u87x/get/32a27008b8b9.bz2](http://bitbucket.org/ahixon/r5u87x/get/32a27008b8b9.bz2)

2. Once it's downloaded, stick it in your home folder (where Pictures, Documents, Videos are). Right-click on the package and select "Extract Here". This will extract a package called r5u87x-32a27008b8b9.

3. Right-click on that package. This will create a folder called r5u87x.

4. Install this: ```
sudo apt-get install nautilus-open-terminal
```5. Right-click on the folder r5u87x and select Open in terminal.

6. type "make" and press enter.

7.  type "make rules" and press enter.

8. type "sudo make install" and press enter.

9. type "r5u87x-loader" and press enter.

10. Reboot.

To test the camera, install the program Cheese from Add/Remove. Once installed you'll find it in the Applications/Graphics menu.

Give it a try and see how you do.:)

.
yay...am on 9.10 and got same old cheese error.
redid steps. rescanning the rest of the forum but i got to step 9 where i got ```
ashley@ashley-laptop:~/r5u87x$ r5u87x-loader 
r5u87x firmware loader v0.2

Searching for device...
Found camera: 05ca:1830
Warning: Failed to get microcode status.

Error: Failed to upload firmware to device: Operation not permitted (code -1).
Try running as root?

```
trying to figure out how to run as root and see if that works

---

### Post by pleasantashes on 2009-11-06
silly mistake. got through all 10. gonna try cheese again.

---

### Post by pleasantashes on 2009-11-06
checked everything. still epic fail. FML.

Anyone else got anything

---

### Post by forkandles on 2009-12-13
pleasantashes,
I have a Vaio VGN-FZ21e laptop with a built-in Ricoh webcam (05ca:183b).
For what it's worth, I just could not be bothered to flog though the driver installation procedure. I used to have an old Microdia webcam and that drove me up the wall trying to get it to work in Linux. 
I connected my trusty Logitech E3500 webcam and after adjusting sound preferences (top toolbar) for the E3500, both video and sound worked fine in Skype.
Try Plan B and save yourself a lot of heartache.
Good luck.

---

