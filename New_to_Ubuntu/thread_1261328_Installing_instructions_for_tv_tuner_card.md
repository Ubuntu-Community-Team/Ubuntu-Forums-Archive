---
title: "Installing instructions for tv tuner card"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by maximusam2391 on 2009-09-08
Okay, I'm pretty new to Linux, but I found a website where I can install drivers for my Hauppauge Win-TV PVR 150MCE card. I went to IVTVdriver.org, and did a little reading. I'm running Ubuntu 9.04 and my kernel is 2.6.28, so I've downloaded "ivtv-utils version 1.3.0", and I've also downloaded the firmware package, but to be honest, I don't really know what to do with these files after downloading. I know some sort of installation has to occur, I just don't know how. __Can someone point me in the right direction, or let me know if I'm doing something wrong/missing a step? [U]
[/U]

---

### Post by Excedio on 2009-09-08
How are the files packaged? Can you open the directory and see if there is a readme?

---

### Post by maximusam2391 on 2009-09-08
There is a readme, but I don't understand what it is saying. In the Readme.install file, it says "If you are using udev or devfs then devices should be created automatically." It does give another option, but I don't follow that either.

Edit: It also says 
"Config needed: 
1. unpack the tarball 
2. cd ivtv 
3. make 
4. make install (as root) 
5. unload any old drivers 
6. depmod 
7. modprobe ivtv"
Perhaps I need that translated, or maybe I'm missing a big part. Thanks in advance for your help.

---

### Post by LowSky on 2009-09-08
you do realize this card is only analog right?

No HDTV or basic digital TV either.

Also it should just work, as its quite an old card/

[http://wiki.linuxmce.org/index.php/Hauppauge_WinTV-PVR-150_MCE](http://wiki.linuxmce.org/index.php/Hauppauge_WinTV-PVR-150_MCE)

---

### Post by Excedio on 2009-09-08
> **maximusam2391 said:**
> There is a readme, but I don't understand what it is saying. In the Readme.install file, it says "If you are using udev or devfs then devices should be created automatically." It does give another option, but I don't follow that either.
 
Edit: It also says 
"Config needed: 
1. unpack the tarball 
2. cd ivtv 
3. make 
4. make install (as root) 
5. unload any old drivers 
6. depmod 
7. modprobe ivtv"
Perhaps I need that translated, or maybe I'm missing a big part. Thanks in advance for your help.
 
Move the file you downloaded to your desktop. Right click and "Extract Here"
 
Open a terminal and type:
 
```
cd /home/yourusername/Desktop/ivtv (then press tab to fill in the rest of the folder name)
```
 
```
make
```
 
```
sudo make install
```
 
I can get you that far. Can someone else please help me out here for the rest?

---

### Post by maximusam2391 on 2009-09-08
Excedio, I did what you said but I have a feeling something went wrong, because I'm seeing "Error" in the output among a lot of other text. Do you think I missed something with the firmware? Am I missing the actual driver as well?

---

### Post by Excedio on 2009-09-08
Consulted my personal Linux Guru. Here are the last few commands:
 
```
lsmod | grep ivtv
```
 
```
rmmod ivtv
```
 
```
depmod -a
```
 
```
modprobe ivtv
```

---

### Post by Excedio on 2009-09-08
> **maximusam2391 said:**
> Excedio, I did what you said but I have a feeling something went wrong, because I'm seeing "Error" in the output among a lot of other text. Do you think I missed something with the firmware? Am I missing the actual driver as well?
 
What is the error message? Can you copy it over from the terminal window for me?

---

### Post by maximusam2391 on 2009-09-08
This is everything that happens after I change my directory and type 'make': 
```
make -C utils all
make[1]: Entering directory `/home/max/Desktop/ivtv-utils-1.3.0/utils'
make CFLAGS="-D_GNU_SOURCE -O2 -Wall -g -I." -C ivtv-tune
make[2]: Entering directory `/home/max/Desktop/ivtv-utils-1.3.0/utils/ivtv-tune'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/max/Desktop/ivtv-utils-1.3.0/utils/ivtv-tune'
make CFLAGS="-D_GNU_SOURCE -O2 -Wall -g -I." -C cx25840ctl
make[2]: Entering directory `/home/max/Desktop/ivtv-utils-1.3.0/utils/cx25840ctl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/max/Desktop/ivtv-utils-1.3.0/utils/cx25840ctl'
make[1]: Leaving directory `/home/max/Desktop/ivtv-utils-1.3.0/utils'
make -C test all
make[1]: Entering directory `/home/max/Desktop/ivtv-utils-1.3.0/test'
cc -I../utils -D_GNU_SOURCE -O2 -Wall  -lm  ivtv-osd-dma-test.c   -o ivtv-osd-dma-test
In file included from ivtv-osd-dma-test.c:9:
../utils/linux/ivtvfb.h:29: error: expected &#8216;:&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;}&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
ivtv-osd-dma-test.c: In function &#8216;main&#8217;:
ivtv-osd-dma-test.c:115: error: &#8216;struct ivtvfb_dma_frame&#8217; has no member named &#8216;source&#8217;
ivtv-osd-dma-test.c:116: error: &#8216;struct ivtvfb_dma_frame&#8217; has no member named &#8216;dest_offset&#8217;
ivtv-osd-dma-test.c:117: error: &#8216;struct ivtvfb_dma_frame&#8217; has no member named &#8216;count&#8217;
make[1]: *** [ivtv-osd-dma-test] Error 1
make[1]: Leaving directory `/home/max/Desktop/ivtv-utils-1.3.0/test'
make: *** [all] Error 2
```
Am I missing the driver/firmware?

---

### Post by Excedio on 2009-09-08
Sorry...this has officially gone beyond my knowledge base :???:
 
Little help from the crowd?

---

### Post by maximusam2391 on 2009-09-08
I went back to ivtvdriver.org and under the 'bleeding driver' section, downloaded the .gz file and unpacked it on the desktop. I ran make on that, and its currently in the middle of that. I'll keep you posted on how it goes. Thanks for your help.

Is there a way to see a list of all the hardware thats recognized/supported by my machine? I have a few things in there that I'm honestly not sure if Linux even sees. I've already had installation problems with my outdated video card, my Dell AIO printer, and this tv tuner card. I also have the receiver for a remote to run media center on windows plugged in; will Ubuntu support that?

---

### Post by Excedio on 2009-09-08
```
sudo lshw -short
```
[of course it leaves a lot of about the detail behind, but make it easier]

```
sudo apt-get install lshw-gtk
```
```
sudo lshw-gtk
```
[user-friendly GUI, more intuitive]

---

### Post by maximusam2391 on 2009-09-08
Alright, I ran the driver, the utils, and the firmware packages, but I highly doubt they are working. what's the best way to check if I've properly installed the TV tuner card? I guess what I'm asking is what program do I use to actually watch/record TV? I have VLC, will that work? 

Thanks for the lshw gui, I think this gives me a better understanding of what is recognized and what isn't, None of my USB devices are showing up, but I suppose that's to be expected.

---

### Post by Excedio on 2009-09-08
Try checking this out:
 
[http://tvtime.sourceforge.net/](http://tvtime.sourceforge.net/)
 
If you want to try this out...I suggest checking to see if you can install without downloading from the site first.
 
```
sudo apt-get install tvtime
```

---

### Post by maximusam2391 on 2009-09-08
I've installed tvtime, but clearly I'm having issues with the hardware. Tvtime says in the bottom left hand corner: ivtv: Invalid arguement. Cannot open capture device /dev/video0.

Edit: I just noticed from the link you just sent me that tvtime does not support drivers from ivtv. So regardless of the state of my driver, this program wouldn't work anyway. Any others you know of?

---

### Post by Excedio on 2009-09-08
You could try Me-Tv or MythTV. Both are in the Synaptic Package Manager. System > Administration > Synaptic Package Manager

---

