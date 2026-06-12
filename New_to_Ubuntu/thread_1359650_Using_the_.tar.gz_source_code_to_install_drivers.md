---
title: "Using the .tar.gz source code to install drivers"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by aaron_the_dude on 2009-12-19
I know there are guides on how to do this sort of thing with just a simple google search, but they usually say around bout the same thing and i get stuck on a few steps.
1.  I installed the build essentials
2.  I put in the terminal, tar zxf file.tar.gz
3.  I go into the new file with the extracted stuff in it with cd ~/Directoryplacewithdrivers
4.  But when I get type in, ./configure        I get, bash: ./configure: No such file or directory

So, what do I do here and get this driver installed, it's for a webcam.

---

### Post by Temposs on 2009-12-19
Please show the output of this command:

```
ls ~/Directoryplacewithdrivers
```

---

### Post by orlox on 2009-12-19
Not all tar.gz archives are meant to be compiled like that. What webcam do you have?

---

### Post by aaron_the_dude on 2009-12-20
The driver is for a cheap digital camera which is a Radioshack Kid's Camera, but I found the documentation and it says it could be used as web cam with windows.  I found the drivers with a google search for linux with the product code listed in the driver info.

Oh, and before I forget.

> aaron@aaron-desktop:~$ ls ~/pencam2-0.67
AUTHORS    demosaic_sharpen.c  pencam2.c       pensnap2.c      sharpen.c
bayer.c    demosaic_sharpen.h  pencam2.h       README.pencam2  unsharp.c
ChangeLog  font_6x11.h         pencam2-misc.c  saturate.c      unsharp.h
COPYING    Makefile            pencam-share.c  saturate.h


---

### Post by 3rdalbum on 2009-12-20
Kernel modules don't usually have a configure script, as you've demonstrated by posting the file list.

Also you should make sure that you have the "linux-headers-generic" package so you have the headers for your kernel.

Just run "make" and "sudo make install" and you should be okay.

Don't forget that you'll need to "make clean", "make" and "sudo make install" whenever you upgrade your kernel.

---

### Post by aaron_the_dude on 2009-12-20
Yeah, that's where I get stuck at.

> aaron@aaron-desktop:~$ sudo make /home/aaron/pencam2-0.67
make: Nothing to be done for `/home/aaron/pencam2-0.67'.


I looked and I have the linux-headers-generic package installed.

---

### Post by Temposs on 2009-12-20
You're not doing it right...Do these commands in this order:

```
cd /home/aaron/pencam2-0.67
```
```
make
```
```
sudo make install
```

---

### Post by aaron_the_dude on 2009-12-20
Ok, I did that exactly, and I'm not sure if it has worked right.

> aaron@aaron-desktop:~$ cd /home/aaron/pencam2-0.67
aaron@aaron-desktop:~/pencam2-0.67$ make
gcc -g -O2 -Wall -I/usr/include   -c pencam2.c -o pencam2.o 
pencam2.c:51:17: error: usb.h: No such file or directory
pencam2.c:59:21: error: pencam2.h: Permission denied
pencam2.c:60:21: error: unsharp.h: Permission denied
pencam2.c:68: error: expected ‘)’ before ‘*’ token
pencam2.c:158: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pencam2.c:183: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pencam2.c:210: error: expected ‘)’ before ‘*’ token
pencam2.c:220: error: expected ‘)’ before ‘*’ token
pencam2.c:254: error: expected ‘)’ before ‘*’ token
pencam2.c:334: error: expected declaration specifiers or ‘...’ before ‘usb_dev_handle’
pencam2.c: In function ‘pencam_vendor’:
pencam2.c:341: warning: implicit declaration of function ‘usb_control_msg’
pencam2.c:341: error: ‘pc’ undeclared (first use in this function)
pencam2.c:341: error: (Each undeclared identifier is reported only once
pencam2.c:341: error: for each function it appears in.)
pencam2.c:341: error: ‘USB_TYPE_VENDOR’ undeclared (first use in this function)
pencam2.c:341: error: ‘USB_RECIP_DEVICE’ undeclared (first use in this function)
pencam2.c:342: error: ‘PENCAM_TIMEOUT’ undeclared (first use in this function)
pencam2.c:348: error: ‘USB_RECIP_ENDPOINT’ undeclared (first use in this function)
pencam2.c: At top level:
pencam2.c:373: error: expected ‘)’ before ‘*’ token
pencam2.c:390: error: expected ‘)’ before ‘*’ token
pencam2.c:462: error: expected ‘)’ before ‘*’ token
pencam2.c:524: error: expected ‘)’ before ‘*’ token
pencam2.c:575: error: expected declaration specifiers or ‘...’ before ‘usb_dev_handle’
pencam2.c:575: error: expected declaration specifiers or ‘...’ before ‘usb_stv’
pencam2.c: In function ‘execute_script’:
pencam2.c:599: error: ‘stv680’ undeclared (first use in this function)
pencam2.c:599: warning: implicit declaration of function ‘pencam_get_num_pics’
pencam2.c:599: error: ‘pc’ undeclared (first use in this function)
pencam2.c:690: warning: implicit declaration of function ‘get_pictures’
pencam2.c:726: warning: implicit declaration of function ‘pencam_read_config’
pencam2.c:731: warning: implicit declaration of function ‘clear_all_images’
pencam2.c:736: warning: implicit declaration of function ‘get_snapshot’
pencam2.c:595: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
pencam2.c: In function ‘main’:
pencam2.c:830: error: ‘usb_stv’ undeclared (first use in this function)
pencam2.c:830: error: ‘stv680’ undeclared (first use in this function)
pencam2.c:831: error: ‘usb_dev_handle’ undeclared (first use in this function)
pencam2.c:831: error: ‘pc’ undeclared (first use in this function)
pencam2.c:832: error: ‘camera_count’ undeclared (first use in this function)
pencam2.c:832: error: ‘camera_addr’ undeclared (first use in this function)
pencam2.c:832: error: ‘orig_camera_addr’ undeclared (first use in this function)
pencam2.c:832: warning: left-hand operand of comma expression has no effect
pencam2.c:833: error: ‘stv’ undeclared (first use in this function)
pencam2.c:833: error: ‘MAX_CAMERAS’ undeclared (first use in this function)
pencam2.c:834: error: ‘pca’ undeclared (first use in this function)
pencam2.c:851: warning: implicit declaration of function ‘load_defaults’
pencam2.c:875: warning: implicit declaration of function ‘count_cameras’
pencam2.c:910: warning: implicit declaration of function ‘pencam_open_all’
pencam2.c:915: warning: implicit declaration of function ‘pencam_init’
pencam2.c:949: warning: implicit declaration of function ‘pencam_get_mode’
pencam2.c:953: error: too many arguments to function ‘execute_script’
pencam2.c:963: warning: implicit declaration of function ‘clr_lines’
pencam2.c:1026: warning: implicit declaration of function ‘usb_close’
pencam2.c:1038: warning: implicit declaration of function ‘menu_header’
pencam2.c:1073: warning: implicit declaration of function ‘get_key’
pencam2.c:1079: warning: implicit declaration of function ‘common_menu’
pencam2.c:1080: warning: implicit declaration of function ‘pencam_do_function’
pencam2.c:1089: warning: implicit declaration of function ‘pensnap_do_function’
pencam2.c:1098: warning: implicit declaration of function ‘pencam_write_config’
pencam2.c:1137: warning: implicit declaration of function ‘get_val’
make: *** [pencam2.o] Error 1
aaron@aaron-desktop:~/pencam2-0.67$ sudo make install
[sudo] password for aaron: 
make: *** No rule to make target `install'.  Stop.


---

### Post by Temposs on 2009-12-20
The following commands should take care of some of those errors:

```
cd /home/aaron/pencam2-0.67
```
```
chmod 777 *
```
```
make
```

But, I'm not sure you're going to get this working very easily, with all those errors.

---

### Post by Temposs on 2009-12-20
OK, you should also do this command:

```
sudo apt-get install libusb-dev
```

And then make again.

---

### Post by aaron_the_dude on 2009-12-21
Eh, I tried what you said and I tried make after the sudo apt-get install thing and still got an error trying to make it.  Screw it, I will fork the money for a decent webcam that can work with linux without too much trouble.  Thanks for your help and if nothing else, this will help me figure out how to install other .tar.gz files, so thank you.

---

### Post by Temposs on 2009-12-21
That's the spirit :-) Make sure the webcam you get is known to work on both Cheese **and** Skype. Those are the most common webcam test applications for Linux, and if the webcam works on both of those, it will probably work on any other application employs the webcam.

---

