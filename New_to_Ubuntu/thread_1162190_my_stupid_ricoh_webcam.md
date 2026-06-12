---
title: "my stupid ricoh webcam"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by syle102 on 2009-05-17
So I have the r5u870 driver, and I have run
make
make install
modprobe r5u870

this should load the driver according to the readme.
I have a dv1659us, and under the driver options section in the readme it says this:
[INDENT] Driver Options
==============

Below is a list of module parameters that may be used with the r5u870 module:

dv1000 -- HP Webcam handling mode
	HP has done it again and used ID 05ca:1870 for two distinct pieces
	of hardware: the HP Webcam 1000, found in HP Pavilion dv1000 series
	machines, and the HP Pavilion Webcam, found in other HP Pavilion
	machines that don't have Microdia cameras, and don't have the 
	05ca:1810 Ricoh UVC camera -- which is not actually any different 
	from the 05ca:1870 HP Pavilion webcam.  These two devices have
	different image sensors and require different microcode.
	0: Assume HP Pavilion Webcam
	1: Assume HP Webcam 1000
	2: Check DMI product name field (DEFAULT)

video_nr -- list of favored minor numbers
	A list of video capture minor numbers (/dev/videoX) to try to
	associate devices with, in order, before resorting to the first
	available minor number.

fixed_fbsize -- integer
	Sets the size in bytes of fixed-length frame buffers.  The default
	value is 1MB.  This is a compatibilty feature for buggy programs
	that use the V4L1 VIDIOCGMBUF call to allocate a frame buffer
	based on the current capture size, choose a larger capture size,
	and then attempt to capture frames.[/INDENT]

I think I need to choose the option to assume that my webcam is a HP Webcam 1000, but I don't quite understand how I am supposed to modify the module. How can I do this?
I've tried
```
sudo modprobe r5u870 dv1000
```
```
sudo modprobe r5u870 dv1000 1
```

And my webcam still does not work. Can anybody tell me what to do? 
thanks

---

### Post by albinootje on 2009-05-17
> **syle102 said:**
> So I have the r5u870 driver, and I have run
make
make install
modprobe r5u870

this should load the driver according to the readme.

Which Ubuntu release are you using ? (Jaunty ? Hardy ?)
And where did you get the source code from ? Please provide the link, so we can read that README file too.

I'm also interested in this because I had the webcam running with Hardy on a Sony Vaio of a colleague, but there's no binary available for that driver in Jaunty afaik, and I managed to get it work a few months ago, except that the webcam image was upside down :| :(

---

### Post by syle102 on 2009-05-17
[http://svn.mediati.org/svn/r5u870/trunk](http://svn.mediati.org/svn/r5u870/trunk) 

This is where I got the source code. 
I am using Intrepid right now. I had this problem on Hardy, but I didn't really try this hard to fix it until now, with Intrepid.

---

### Post by Nepherte on 2009-05-17
Try these instructions: [http://www.nepherte.be/arch-linux-on-a-sony-vaio-sz-6/#webcam](http://www.nepherte.be/arch-linux-on-a-sony-vaio-sz-6/#webcam)

That's how I made my webcam work. You'll have to adapt the instructions a bit.
[list]
[*]When asked to install mercurial, use this command instead:
```
sudo apt-get install mercurial
```
[*]When asked to load the driver, use the file for your model instead:
```
sudo ../loader -f <your-webcam-model-firmware-file>
```

To find out what model you have, use:
```
lsusb
```
There should be a entry with "Ricoh Co., Ltd" at the end. The value behind id, is your model.
[/list]

---

### Post by waldelis on 2009-08-15
> **Nepherte said:**
> Try these instructions: [http://www.nepherte.be/arch-linux-on-a-sony-vaio-sz-6/#webcam](http://www.nepherte.be/arch-linux-on-a-sony-vaio-sz-6/#webcam)

That's how I made my webcam work. You'll have to adapt the instructions a bit.
[LIST]
[*]When asked to install mercurial, use this command instead:
```
sudo apt-get install mercurial
```
[*]When asked to load the driver, use the file for your model instead:
```
sudo ../loader -f <your-webcam-model-firmware-file>
```To find out what model you have, use:
```
lsusb
```There should be a entry with "Ricoh Co., Ltd" at the end. The value behind id, is your model.
[/LIST]

  Didnt help me :( camera still not working... thats what got ---> 
sudo ../loader -f <05ca:183a>
[SIZE=2]bash: syntax error near unexpected token `newline'[/SIZE] any ideas ?oh and before that after i wrote 
cd r5u87x
make
i got the following:cc -g -Wall -DHAVE_CONFIG_H -DUCODE_PATH=\"/usr/lib/r5u87x/ucode/r5u87x-%vid%-%pid%.fw\"  `pkg-config --cflags glib-2.0 libusb` -c loader.c loader.h
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

thanks for help :)

---

### Post by Nepherte on 2009-08-16
As you may have suspected already, the installation of r5u87x failed and it also lists the reason why it failed:
```
No package 'libusb' found
...
make: *** [loader.o] Error 1
```

What you should do now is install the libusb package (and the libusb-dev package as well, not sure if this is the exact name of the packages. Try to look it up in synaptic). Btw since an error occured, there was no reason to continue with the next instructions. You should always solve an error before going on.

There's also a problem with your next command:
```
sudo ../loader -f <05ca:183a>
```
You were taking it a little too litteral. You should replace <your-webcam-model-firmware-file> with the full or relative path to the firmware file of your model. If your webcam model is 05ca:183a, you will find a file named r5u87x-05ca-183a.fw in the ucode directory. So the correct command would be:
```
sudo ../loader -f r5u87x-05ca-183a.fw
```

I suggest you redo the instructions starting from the make command.

---

### Post by waldelis on 2009-08-23
> **Nepherte said:**
> As you may have suspected already, the installation of r5u87x failed and it also lists the reason why it failed:
```
No package 'libusb' found
...
make: *** [loader.o] Error 1
```What you should do now is install the libusb package (and the libusb-dev package as well, not sure if this is the exact name of the packages. Try to look it up in synaptic). Btw since an error occured, there was no reason to continue with the next instructions. You should always solve an error before going on.

There's also a problem with your next command:
```
sudo ../loader -f <05ca:183a>
```You were taking it a little too litteral. You should replace <your-webcam-model-firmware-file> with the full or relative path to the firmware file of your model. If your webcam model is 05ca:183a, you will find a file named r5u87x-05ca-183a.fw in the ucode directory. So the correct command would be:
```
sudo ../loader -f r5u87x-05ca-183a.fw
```I suggest you redo the instructions starting from the make command.

Thanks so much i fixed the error thingy but than I type 
[SIZE=2]sudo ../loader -f r5u87x-05ca-183a.fw[/SIZE]
it says,[SIZE=2] sudo: ../loader: command not foun[/SIZE]d
any ideas ?

---

### Post by Nepherte on 2009-09-07
My apologies for answering this question so late. I didn't notice your post until now.

```
sudo: ../loader: command not found
```
means you gave the wrong path to the loader executable and hence couldn't find the command. What you're saying now is "*run loader, which is located in the directory above the one I'm currently in, with the firmware file r5u87x-05ca-183a.fw located in the current directory"*.

For this exact command to work, you have to be locatd in the udev directory of r5u87x. If you followed all the directions on [http://www.nepherte.be/arch-linux-on-a-sony-vaio-sz-6/#webcam](http://www.nepherte.be/arch-linux-on-a-sony-vaio-sz-6/#webcam) you wouldn't have had these issues ;)

---

### Post by waldelis on 2009-09-08
> **Nepherte said:**
> My apologies for answering this question so late. I didn't notice your post until now.

```
sudo: ../loader: command not found
```means you gave the wrong path to the loader executable and hence couldn't find the command. What you're saying now is &quot;*run loader, which is located in the directory above the one I'm currently in, with the firmware file r5u87x-05ca-183a.fw located in the current directory&quot;*.

For this exact command to work, you have to be locatd in the udev directory of r5u87x. If you followed all the directions on [http://www.nepherte.be/arch-linux-on-a-sony-vaio-sz-6/#webcam](http://www.nepherte.be/arch-linux-on-a-sony-vaio-sz-6/#webcam) you wouldn't have had these issues ;)

 Thanks for taking time to answer at all:) and i did all dat but camera still not working tried all different programs: SKYPE, Cheese,Camorama still not working. The output after commands u directed me to was:   
[B][SIZE=2]
r5u87x firmware loader v0.2

Searching for device...
Found camera: 05ca:183a
Camera reports negative microcode state.
Sending microcode to camera...
Enabled microcode.
Camera reports microcode version 0x0111.

Successfully uploaded firmware to device 05ca:183a![/SIZE][/B]


Still doesnt work tho

---

### Post by Nepherte on 2009-09-09
[QUOTE="waldelis"]r5u87x firmware loader v0.2

Searching for device...
Found camera: 05ca:183a
Camera reports negative microcode state.
Sending microcode to camera...
Enabled microcode.
Camera reports microcode version 0x0111.

Successfully uploaded firmware to device 05ca:183a![/QUOTE]
Aha, a success. We're slowly getting there.

Did you reload the modules? Try the loader command again for the firmware and then reload the modules
```
sudo rmmod uvcvideo &amp;&amp; sudo modprobe uvcvideo
```

I always try my webcam with cheese first. Skype has always been difficult to work with.

---

### Post by waldelis on 2009-09-09
> **Nepherte said:**
> Aha, a success. We're slowly getting there.

Did you reload the modules? Try the loader command again for the firmware and then reload the modules
```
sudo rmmod uvcvideo &amp;&amp; sudo modprobe uvcvideo
```I always try my webcam with cheese first. Skype has always been difficult to work with.

Stupid me, i forgot to tell u i did that and it gave me the following output: 
[B][SIZE=2]
sudo rmmod uvcvideo &amp;&amp; sudo modprobe uvcvideo
_bash: syntax error near unexpected token `&'_[/SIZE][/B]

---

### Post by Nepherte on 2009-09-10
My bad, &amp;&amp; is supposed to be &&. Somewhere during the copy/paste it must have gotten messed up. So here we go again:
```
sudo rmmod uvcvideo && sudo modprobe uvcvideo
```

---

### Post by chak8870 on 2009-09-11
@Nepherte
I am using ubuntu 9.04 on a Sony Vaio VGN-SZ 370P. I have followed all the instructions in this thread as well as this website [http://www.nepherte.be/arch-linux-on-a-sony-vaio-sz-6/#webcam](http://www.nepherte.be/arch-linux-on-a-sony-vaio-sz-6/#webcam). 
Kernel module: 2.6.28-15 generic.
Couple of library's were missing which I installed from the repositories. And everything seems to be alright. Then I installed XawTV which did not start. I installed Cheese which showed "no camera found" message. 

lsusb output:
Bus 001 Device 005: ID 05ca:1830 Ricoh Co., Ltd Visual Communication Camera VGP-VCC2
Bus 001 Device 003: ID 054c:0281 Sony Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 0fce:d019 Sony Ericsson Mobile Communications AB VDC EGPRS Modem
Bus 005 Device 002: ID 044e:300c Alps Electric Co., Ltd Bluetooth Controller (ALPS/UGPZ6)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Any help is appreciated.

---

### Post by waldelis on 2009-09-11
> **Nepherte said:**
> My bad, &amp;&amp; is supposed to be &&. Somewhere during the copy/paste it must have gotten messed up. So here we go again:
```
sudo rmmod uvcvideo && sudo modprobe uvcvideo
```

YAY!!! SUCCESS!!! Its working after all this time**[SIZE=4]. Thank you so much u'r the greatest, the best everrrrr !!!!![/SIZE]** Now the only problem is than i load camera on skype the image of me is transparent :D which is kinda funny looking :D :). Do you know anything about dat? Oh and its working perfectly fine on cheese

---

### Post by aljoriz on 2009-09-11
why not try the EASYCAM2?  google it, that software will check your webcam and will install the appropriate drivers.  Just be sure to get the easycam-qt version.

---

### Post by aljoriz on 2009-09-11
$ sudo gedit /usr/local/bin/skype 
and paste the following 2 line
 	Code:
 	#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype 
then make it executable
 	Code:
 	$ sudo chmod a+x /usr/local/bin/skype 

that might solve the problem about the video on skype.

---

### Post by Nepherte on 2009-09-12
> **chak8870 said:**
> 
I am using ubuntu 9.04 on a Sony Vaio VGN-SZ 370P. I have followed all the instructions in this thread as well as this website [http://www.nepherte.be/arch-linux-on-a-sony-vaio-sz-6/#webcam](http://www.nepherte.be/arch-linux-on-a-sony-vaio-sz-6/#webcam). 
Kernel module: 2.6.28-15 generic.
Couple of library's were missing which I installed from the repositories. And everything seems to be alright. Then I installed XawTV which did not start. I installed Cheese which showed "no camera found" message. 

lsusb output:
```
Bus 001 Device 005: ID 05ca:1830 Ricoh Co., Ltd Visual Communication Camera VGP-VCC2
```
Any help is appreciated.
Well, without any outputs and/or errors, it's pretty difficult to find out what's gone wrong. Did you load your firmware with the loader -f <firmwarefile> command? Since it doesn't load automatically on startup or upon launching a webcam program, you have to execute it everytime you want to use your webcam. It's either that or the installation of the ricoh driver somehow went wrong.

---

### Post by Nepherte on 2009-09-12
> **waldelis said:**
> YAY!!! SUCCESS!!! Its working after all this time**[SIZE=4]. Thank you so much u'r the greatest, the best everrrrr !!!!![/SIZE]** Now the only problem is than i load camera on skype the image of me is transparent :D which is kinda funny looking :D :). Do you know anything about dat? Oh and its working perfectly fine on cheese
I'm happy you got it working. I still have to look into skype, I have never used it before. Let us know if aljoriz' instuctions work.

---

### Post by chak8870 on 2009-09-12
> Did you load your firmware with the loader -f <firmwarefile> command? Since it doesn't load automatically on startup or upon launching a webcam program, you have to execute it everytime you want to use your webcam. It's either that or the installation of the ricoh driver somehow went wrongI used the code that was given in your website
> [COLOR=#7a0874]**alias**[/COLOR] [COLOR=#007800]webcam[/COLOR]=[COLOR=#ff0000]'sudo /home/user/.r5u870/r5u87x/loader --reload -f /home/user/.r5u870/r5u87x/ucode/r5u87x-05ca-183a.fw[/COLOR][COLOR=#ff0000]'
[COLOR=Black]I changed the user and put the code at the end of bashhrc file. I added #before the line, though I didn't know what it does in that file.[/COLOR]
[/COLOR]
There was a problem which I didn't pay to much attention to. 
> sudo rmmod uvcvideo && sudo modprobe uvcvideoI got this error when I used the above code: 
[COLOR=Red]ERROR: Module uvcvideo does not exist in /proc/modules[/COLOR]
I have deleted the last line in bashhrc and at a complete loss.

> why not try the EASYCAM2? google it, that software will check your webcam and will install the appropriate drivers. Just be sure to get the easycam-qt version.
Very neat aljoriz. I added the repositories and installed[COLOR=Red]** easycam2-qt**[/COLOR]. Installation without any problem. Started the program and it found my cam VGP-VCC2 alright. Installed the driver. 
[SIZE=3][COLOR=Red]Started Cheese. No camera found.[/COLOR][/SIZE] Rebooted. No luck. By the way everytime I start easycam2, it is asking me to install the driver.
Could it be a problem of Gstreamer?

Thanks in advance to nepherte and aljoriz,

---

### Post by Nepherte on 2009-09-13
> **chak8870 said:**
> I used the code that was given in your website

[COLOR=Black]I changed the user and put the code at the end of bashhrc file. I added #before the line, though I didn't know what it does in that file.[/COLOR]

Putting a # in front of it means you comment it (disable it). Anyways, the alias is just used as a short way to run a long command. The command
```
webcam
```
is a lot easier to type than
```
sudo /home/user/.r5u870/r5u87x/loader --reload -f /home/user/.r5u870/r5u87x/ucode/r5u87x-05ca-183a.fw
```

> **chak8870 said:**
> There was a problem which I didn't pay to much attention to. 
I got this error when I used the above code: 
```
sudo rmmod uvcvideo && sudo modprobe uvcvideo
```
[COLOR=Red]ERROR: Module uvcvideo does not exist in /proc/modules[/COLOR]
I have deleted the last line in bashhrc and at a complete loss.

Thanks in advance to nepherte and aljoriz,
That's the reason it doesn't work and I kinda have no clue how to fix that :s

---

