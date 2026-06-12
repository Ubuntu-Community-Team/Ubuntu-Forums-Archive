---
title: "How to install webcam Logitech quickcam e2500"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by channie2009 on 2009-01-18
Hello! my husband got me a webcam as a gift but we are having trouble installing it with Ubuntu 8.10 the make of the webcam is Logitech quickcam e2500 i am just learning how to use linux so i am not sure on how to install this webcam so any advice would be grate. Thanks!!:)

---

### Post by laurielegit on 2009-01-18
Hi,

Do you want this webcam for skype and other video messaging services? or do you want it for something else (can't think of anything at the moment)

Laurie

---

### Post by diablo75 on 2009-01-18
> **laurielegit said:**
> something else 



Cheese?

---

### Post by laurielegit on 2009-01-18
lol, ok then, skype it is. 

I found this in a guide here: [http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/](http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/)

> 
First, download the drivers and the patch:

```
wget http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz
wget http://forums.quickcamteam.net/attachment.php?aid=86 -O patch.tar.gz
```

Then extract and apply the patch:

(UPDATE: For Ubuntu 8.10 users, this patch may no longer work. Try downloading the patch here instead, and then extract it using gzip -d gspcapatch.gz. Apply the extracted file in the same was as below, just neglect the -p1 switch, (so do: patch < gspcapatch), you can just ignore the tar -xvf patch.tar.gz command).

```
tar -xvf gspcav1-20071224.tar.gz
tar -xvf patch.tar.gz
cd gspcav1-20071224
patch -p1 < ../quickcamE2500.diff
```

There’s a handy build script included with the drivers so just run that (requires root):

```
sudo ./gspca_build
```

This generates the file

```
gspca.ko
```

which we use to replace the old gspca module.
Check to see if the old module is loaded, you should see something like:

```
dave@baracus:~$ lsmod | grep gspca
gspca                 680656  0
videodev               29440  1 gspca
usbcore               146028  9 gspca,snd_usb_audio,snd_usb_lib,usb_storage,usbhid,libusual,ehci_hcd,ohci_hcd
```

We want to find out where it is, so do the following:

```
sudo rmmod gspca
sudo modprobe -v gspca
```

You should see something like:

```
insmod /lib/modules/2.6.24-20-generic/ubuntu/media/gspcav1/gspca.ko
```

That is the location of the file we’re looking for, so, replacing where appropriate with what was output for you above, type:

```
sudo rmmod gspca
sudo rm /lib/modules/2.6.24-20-generic/ubuntu/media/gspcav1/gspca.ko
sudo mv gspca.ko /lib/modules/2.6.24-20-generic/ubuntu/media/gspcav1/
sudo modprobe gspca
```

This should have loaded the new module in place of the old one. See if you have a video device:

```
dave@baracus:~$ ls /dev/video*
/dev/video0
```

You can try and run Skype now, and in fact, if you’re not using the camera for Skype, this may well be enough. But for the Skype users: see if you get any picture by testing in the video devices option menu (be warned, it can take a little while to show up there after skype loads, and a little while for the picture to show when you press the test button, so be patient). If anything show’s up at all that’s a plus. (UPDATE: If you’re using Ubuntu 8.10, and have used the alternative patch I posted in the other “UPDATE:” bracket above, the webcam may still not work in Skype at this point. There seems to be some issue with permissions in this version of the driver, so you may need to run skype as root if it doesn’t appear to be working. In a terminal type “sudo skype” and hit enter. It’ll ask for your root password, then launch skype. See if the webcam works now).

Originally, I had a black image, so I assumed the camera wasn’t working, but I soon realised that the image was there, just very dark - shining a light on it showed this was the case. I tried fiddling around with gstfakevideo for a while to try and alter the output, but there was a much simpler solution. The gspca driver itself can take options, and an autoexposure setting was ruining my lighting. To fix this, edit the file /etc/modprobe.d/options, and add a line at the bottom:

```
options gspca gamma=1 autoexpo=0
```

The gamma=1 may not be necessary, but if it still appears too dark or too light for your taste you can change this parameter as you like. Finally, reload the module:

```
sudo rmmod gspca
sudo modprobe gspca
```

and try out skype again. Hopefully it works!

I ran into quite a lot of other problems while I was trying this out, so if you come across any errors, drop a comment below and I’ll try and get back to you asap.

UPDATE: I found a large problem when using the camera in Skype was that CPU usage would shoot up to 100%, causing things to freeze up and conversations to crash after a while. I had played around with gstfakevideo a bit when trying to get the camera to work originally, and it seems using this when the camera already ‘works’ means it uses up far less CPU. I haven’t had a chance to test it for a long period yet but it seems like it should do the trick. Here’s what I did:

First, download gstfakevideo using subversion (you may need to install the subversion package, sudo apt-get subversion probably does the trick, and then the command below will make a directory called gstfakevideo in your current location, so make sure it’s somewhere nice), then compile and install it:

[/code]svn checkout [http://gstfakevideo.googlecode.com/svn/trunk/](http://gstfakevideo.googlecode.com/svn/trunk/) gstfakevideo
cd gstfakevideo
make
sudo make install[/code]

gstfakevideo creates a new video stream using your webcam, which is formatted differently and skype seems to get along with it more. The only problem is, it outputs its stream to /dev/video0 which is where our webcam currently lives. So we have to move the webcam, but this is easy enough:

```
sudo mv /dev/video0 /dev/video1
```

(Actually, gstfakevideo seems to work for me with lower CPU without moving this - but try it moved first anyway). Watch out though, every time you reboot, your webcam will probably go to /dev/video0 by default, assuming you have no other video devices, so you will have to move stuff about to make a space in video0 each time. Now we see if it works:

```
gstfakevideo v4lsrc device=/dev/video1 ! ffmpegcolorspace
```

What this does is runs gstfakevideo, telling it that the source we’re using is a v4l source, and its from /dev/video1. The ffmpegcolorspace argument seems to be for making the stream YUV instead of RGB for some cameras so may not be necessary. It then launches skype, with hopefully the output below:

```
dave@baracus:~$ gstfakevideo v4lsrc device=/dev/video1 ! ffmpegcolorspace
gst.c create_pipeline (155): pipeline created
gst.c create_pipeline (159): pipeline linked
```

If you look in the skype video options now there will be no camera listed. You have to wait a while (it can take 30s or so), until you get some output, ending with something like:

```
gst.c shim_ioctl (201): request=803c7601 nr 1
gst.c shim_ioctl (208): VIDIOCGCAP
gst.c shim_ioctl (313): result=0 error=0 Success
```

Now a camera should show up in the video menu in skype, with a name like GStreamer fake video (/dev/video0). Try it out, and compare your CPU performance to before. Also try exiting skype, and moving your video source from /dev/video1 back to video0, and running gstfakevideo again, only with device=/dev/video0, and see if it works (and let me know your findings below!).

Finally if gstfakevideo works, we can clean it up so the command isn’t so long to type. The script should be stored in:

```
/usr/local/bin/gstfakevideo
```

(Can check this using):

```
dave@baracus:~$ whereis gstfakevideo
gstfakevideo: /usr/local/bin/gstfakevideo
```

So we edit this file (requires root):

```
sudo gedit /usr/local/bin/gstfakevideo
```

Now, find the line that looks like this:

```
export GST_PIPE="videotestsrc is-live=true ! video/x-raw-yuv,width=640,height=480,framerate=10/1 ! videoscale ! ffmpegcolorspace ! vertigotv ! ffmpegcolorspace"
```

and change it to (remember where you put your webcam source - if you moved it back to /dev/video0, change the device parameter accordingly):

```
export GST_PIPE="v4lsrc device=/dev/video1 ! ffmpegcolorspace"
```

and finally look a bit further down, and delete the line:

```
export GST_PIPE="$*"
```

Now Skype will launch with your faked video stream, just from the command gstfakevideo. Good luck! Let me know how you get on.

Post here if you need any help with these instuctions.

Good luck,

Laurie

---

### Post by channie2009 on 2009-01-18
> **laurielegit said:**
> Hi,

Do you want this webcam for skype and other video messaging services? or do you want it for something else (can't think of anything at the moment)

Laurie

Yes i would like to use it for skype and other video messaging services i have family back home that have webcams but i can't use it as i have tried to install it but it won't see it i don't know why i have install some softwear from my ubuntu disc but even that does not help much with my webcam so if you can help i will be very grateful.:)

---

### Post by Bölvaður on 2009-01-18
> **channie2009 said:**
> Yes i would like to use it for skype and other video messaging services i have family back home that have webcams but i can't use it as i have tried to install it but it won't see it i don't know why i have install some softwear from my ubuntu disc but even that does not help much with my webcam so if you can help i will be very grateful.:)

look at the howto that was posted here above. It looks abnormally long but that may just because it is very careful and detailed.. which is a good thing :)

---

### Post by uru wolf on 2009-03-10
Hey there. I just followed the above tutorial, and all seemed to work fine. There is now a video device under /dev/video0 but, nothing picks it up. I have tried cheese and skype, but both say there is no cam present, even after restarting. Does anyone know any other tutorials or ways to fix this?

Thanks in advance.

UDATE:
By running
```
ls /dev/video*
```
I get /dev/video0, so something must be there. When I unplug the cam I get a no such file or directory message.

UPDATE2:
I ran gstreamer-properties to see if I could test the camera but I get an error that says:
```
Video for Linux 2 (v4l2): Could not open device "/dev/video0" for reading and writing.
```
I get this for video for linux and video for linux 2

Ok, I have fixed the above access error by running skype/gstreamer-properties as root, not best way but the best I can see.

---

### Post by Aviendha09 on 2009-03-25
How about how to install webcam logitech quickcam express plus ? I got it halfway working...that is, anywhere but Skype, using gstfakevideo......intrepid on a netvista P4

---

### Post by odinb on 2009-03-25
Are you sure you need to install any drivers for it? My logitech cams did not need any manually installed drivers as of Ubuntu 8.10 as they are part of the kernel.
It works out of the box, I just have to choose the webcam and microphone in Skype (or whatever app it is used for).

See also: [http://liquidat.wordpress.com/2008/08/08/linux-kernel-news-wlan-and-webcams-for-everyone/](http://liquidat.wordpress.com/2008/08/08/linux-kernel-news-wlan-and-webcams-for-everyone/)

---

### Post by Aviendha09 on 2009-03-25
Well, I just got it working. What a learning experience!\\:D/

I combined things from this thread:

> **JBotAlan said:**
> gstfakevideo did it for me.

I honestly cannot remember how I installed it. I may have gotten it through Synaptic Package Manager, but I vaguely recall downloading it and compiling it by hand. But I might be lying...don't quote me on this one.

However, I ran gstfakevideo (after poking around in the script for a bit to figure out how it works) as follows:
```
gstfakevideo v4l2src device=/dev/video1
```
I didn't even know v4l2src was an option until reading a lot. v4lsrc would never work properly, but v4l2src works great. Skype launched, I clicked "Test", and it is beautiful.

Note: my camera is on /dev/video1. I did that by executing
```
sudo mv /dev/video0 /dev/video1
```
Since apparently gstfakevideo cannot work with any other device than /dev/video0.

Hopefully that works for others. And hopefully at some point Skype will fix this so it works natively.

Oi! Linux is fun! ;-)
JBot

Now I need to get my webcam to STAY on /dev/video1 AND I need to close my terminal. Do I create a desktop or menu launcher?...to be continued...

edit: oops! it stopped working, the launcher does, though.

Ah. it was too dark. Adjust the webcam with Xawtv prior to using Skype with the gstfakevideo launcher. Don't forget to switch the paths back and forth.

---

### Post by nickmcg on 2009-03-26
How about setting up a link, rather than using mv?

Nick

---

### Post by Nhorning on 2009-04-15
Good news!   

This cam will be supported out of the box shortly after the Jaunty release as indicated here: [https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/326674](https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/326674)


In the meantime there is a much easier workaround than the Actionshrimp tutorial we've all been using. It's suggested in the above bug report.  Go to this ftp:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.1/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.1/)

Download the kernel image for your architecture.
It will automatically install with the package installer.  Restart your system and be sure the new Kernal is selected by Grub during boot. 

Thats it.   It will work.  you don't have to recompile a kernel module or get nailed to a tree or anything.  

However, keep in mind that it's an unsupported, unreleased development kernel, and things might break, blah blah blah, etc etc.

---

### Post by Aviendha09 on 2009-05-02
New solution, worked for my quickcam express plus, after this solution stopped upon upgrade to Jaunty (9.04)  [http://ubuntuforums.org/showthread.php?p=7163331#post7163331]("http://ubuntuforums.org/showthread.php?p=7163331#post7163331")

---

### Post by onecrustybaker on 2009-05-04
i had a lot of probs with dreaded green screen in skype....read this thread and now works perfectly.
[http://ubuntuforums.org/showthread.php?p=7215014#post7215014](http://ubuntuforums.org/showthread.php?p=7215014#post7215014)

---

### Post by lukeinvancouver on 2009-05-09
> **laurielegit said:**
> lol, ok then, skype it is. 

I found this in a guide here: [http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/](http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/)



Post here if you need any help with these instuctions.

Good luck,

Laurie


Four connected questions:

1) Do these instructions also apply to an Intel webcam, specifically Intel CS 430 (it's years old)?

2) I haven't downloaded Skype yet. On their dowload page it says Ubuntu 7.04 - 8.04. What are the chances that it will work with ver 9.04?

3) ls /dev/video*
yields: dev/video0

Does this mean that the webcam is installed? (When I plugged it in it recognised it.)

4) What application can I install (other than Skype) to test the webcam and how do I do this? Almost all these instructions are like a foreign language to me. 

Any help would be greatly appreciated.

Thank you in advance.

---

### Post by pieterprovoost on 2009-05-16
I've got it working pretty well now, but there is a flickering band on the bottom of the image. Any thoughts about that?

---

### Post by keenboy on 2009-10-13
Great how to. Works for me.

---

### Post by Hellola on 2010-05-04
this might not be useful per say, but i had the very dark issue with my logitech e2500 in 10.04 and 

> options gspca gamma=1 autoexpo=0

that really helped 

Thanks!

---

### Post by linmix on 2010-06-01
I tried virtually all of the suggestions here and so far the only thing i have managed is to 'lose' the webcam. I can see a moving image from cheese (very poor quality & dark) but Skype now says it doesn't detect any video device.

Can anyone suggest where to start to try and fix this?

---

### Post by samywiseguy on 2011-06-14
I'm sorry, it doesn't seem to work. "Module gspca not found."
That's serious, isn't it?

---

### Post by no2498 on 2011-06-14
samywiseguy

open a terminal type dmesg click enter
after it stops install xawtv
try the cam in xawtv

---

### Post by Lyfang on 2012-06-22
Rather old & inactive thread, however Lubuntu 12.04 doesn't seems to be able to use this driver. I can create a new forum thread if necessary to further discuss this topic.

---

### Post by Elfy on 2012-06-22
Old thread closed.

That would be best Lyfang.

---

