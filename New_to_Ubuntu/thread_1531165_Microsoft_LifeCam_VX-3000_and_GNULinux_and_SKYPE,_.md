---
title: "Microsoft LifeCam VX-3000 and GNU/Linux and SKYPE, no green"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-07-14
skype 2 1 0 81 I have video cuz of this :

> Microsoft LifeCam VX-3000 and GNU/Linux

Posted by Locks Free on 15/03/2010

Here are some tips I have collected while trying to make my Microsoft LifeCam Vx3000 work under the latest Ubuntu. I have a 64 bits system and my aim was to make my camera work with Skype. The hardest part was to find the correct gspca module sources that worked with the latest kernels.
1. Check whether the web-cam is recognized at all

So first, I had to check if the camera was seen at all or not.
~$ lsusb
+ lsusb
Bus 002 Device 014: ID 045e:00f5 Microsoft Corp. LifeCam VX-3000.
One of the line returned by lsusb clearly indicates that my web-cam is recognized. If your web-cam does not appear, try to unload and reload ehci_hcd:
~$ sudo modprobe -r ehci_hcd
~$ sudo modprobe ehci_hcd
And then retry lsusb.
2. Make sure v4l1compat is loaded

Check whether the v4l1compat module is loaded or not by typing the following:
~$ sudo lsmod | grep v4l1_compat
If it not installed, you need to install it. If you have a 32 bits system, you need to install libv4l-0; if you have a 64 bits system like me, you need to install both libv4l-0 and lib32v4l-0:
~$ sudo apt-get install libv4l-0 lib32v4l-0
3. Install cheese

To do this first part, you will need to check progress using cheese:
~$ sudo apt-get install cheese
Startup cheese, click on Video and check whether you can see an image or just white noise. If you do see an image, you can jump to step 4. If like me you could not see anything, follow on..
4. Install GSPCA

Make sure your linux kernel sources are installed and accessible from /usr/src/linux.
Now, download and install the latest gspca module version:

    * Go to this page: [http://linuxtv.org/hg/~hgoede/gspca/](http://linuxtv.org/hg/~hgoede/gspca/) (used to be [http://linuxtv.org/hg/~jfrancois/gspca/](http://linuxtv.org/hg/~jfrancois/gspca/) but got merged back in)
    * Click on the bz2 link on the left side and save it under /tmp
    * Open a terminal and type the following (the compilation itself can take several minutes):
      ~$ cd /tmp
      ~$ tar xfvj gspca-<version>.bz2
      ~$ cd gspca-<version>
      ~$ make
      ~$ sudo make install && reboot

Now, try to run cheese once again and see if this work. If it does not, first check that the gspca module is loaded. If not load it.
~$ sudo lsmod | grep gspca
5. Make Skype work

If Skype still does not work, you need to help it to get there.

You need to force Skype to use the v4l1 compatibility layer, it is not yet compatible with v4l2 apparently. So you have to set the LC_PRELOAD environment variable to /usr/lib/libv4l/v4l1compat.so if you are on a 32 bits system or /usr/lib32/libv4l/v4l1compat.so if you are on a 64 bits system. To just try it, open a terminal and type:
~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype
Now, you should it be able to see your web-cam image in the Skype video options. If not… well then good luck continuing the search !
Finally, I made that change permanent (at least, until a future Skype upgrade):
~$ sudo mv /usr/bin/skype /usr/bin/skype_real
~$ sudo echo LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/bin/skype_real > /usr/bin/skype
~$ sudo chmod +x /usr/bin/skype
You could also just create an alias in your home for this. Overall, I hope this helps you as it can seem like a never-ending frustration to use some web-cams under Linux, while many other web-cams work out of the box !

If it was useful to you or if you found something I could add, please leave a comment !

---

### Post by junga on 2011-05-29
Late reply
first many thanks to the poster :D really nice work I followed the instructions with some tinkering, couple of pointers:
for the gspca driver I had to download it elsewhere with a google search to find the latest package, I found a working one at [http://moinejf.free.fr/](http://moinejf.free.fr/)
the untaring did not work from the terminal i just opened the tar and drag dropped the folder to the tmp folder, the commands that followed worked just fine.
Now I have a microsoft livecam show that just didn't want to display the photos or videos with cheese and skype  after I did all the steps,however i could take photos fine, without having the live stream showing.
BUT it worked fine with my kodak webcam go figure!
just to let you know.
Thanks

---

### Post by julio8a00 on 2012-06-03
My cam wasn't working and now it does thanks to you!  :)

---

