---
title: "i can't find drivers for logitech webcam"
date: 2010-03-14
forum: New to Ubuntu
---

### Post by bradmayne04 on 2010-03-14
does anyone know where there may be a generic driver for a logitech webcam?  I can't find any drivers that would work in synaptic.

---

### Post by hansdown on 2010-03-14
Hi bradmayne04.

Some logitec webcams work well, and some don't.

Can you tell us the model?

Here is a pretty good list of webcams.

[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

---

### Post by no2498 on 2010-03-14
do this open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 and v4l2 click the bottom test button for each 1

now you need a program like  cheese to see/use it on
it is already loaded on 910 karmic
ekiga softphone is loaded also and will most likely see your cam

---

### Post by bradmayne04 on 2010-03-17
I'm not sure what model logitech web cam it is but I'm gonna try that advice out later tonight.  Thanks man!!

---

### Post by llamabr on 2010-03-17
allow me to save you many hours of frustration, and ultimate failure.  You're doing this the wrong way around.  It's a complete nightmare to make a webcam work, if it is not supported.  You'll spend an entire weekend googling, and sudo-ing, and updating, and it will be for naught.  

Instead, follow the link above, spend 15$ on a webcam that works out of the box, and go see a movie this weekend, instead.  It's money well spent.

---

### Post by no2498 on 2010-03-18
llamabr

what i said is how they/ubuntu test the webcams
its in the cheese help files faq's

and it is the fastest way to set the video dev 0
so if you do lsusb in a terminal the cam is seen

99% of all web cams will work now days
just some better than others 
an yes the older ones too
you may need to get the gstreamer in the add/remove
good, bad, ugly
cheese is what they use to every thing to do with a webcam now days
it just dont work for me on 910 karmic 
the cam works i just cant set the color there backwards for me

---

### Post by penguinv on 2010-03-18
> **hansdown said:**
> by hansdown - May the Ubuntu Be With You!
Hi bradmayne04.

Some logitec webcams work well, and some don't.
Can you tell us the model?

Here is a pretty good list of webcams.
   [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

and[QUOTE=llamabr]
Re: i can't find drivers for logitech webcam
allow me to save you many hours of frustration, and ultimate failure. You're doing this the wrong way around. It's a complete nightmare to make a webcam work, if it is not supported. You'll spend an entire weekend googling, and sudo-ing, and updating, and it will be for naught. 

Instead, follow the link above, spend 15$ on a webcam that works out of the box, and go see a movie this weekend, instead. It's money well spent.[/QUOTE]

OK There's a lot of pages and I think mine is a no-go but I'll put in my info anyhoo:

I have a Logitech V-UBS47
   QuickCam® for NotebooksM/N: V-UBS47
   [http://www.logitech.com/index.cfm/435/2989&hub=1&cl=us,en?WT.z_sp=Image](http://www.logitech.com/index.cfm/435/2989&hub=1&cl=us,en?WT.z_sp=Image)

[http://www.quickcamteam.net/hcl/software/linux/drivers](http://www.quickcamteam.net/hcl/software/linux/drivers)
  It is listed here in a way.
Leading to here: [http://www.quickcamteam.net/software/linux/drivers/quickcam-usb-driver/](http://www.quickcamteam.net/software/linux/drivers/quickcam-usb-driver/)

But this seems to mean NO: The Logitech non-UVC Camera Device List [http://www.quickcamteam.net/devices/non-uvc-webcams](http://www.quickcamteam.net/devices/non-uvc-webcams)

I installed Skype 2.1 Beta 2 for Linux
I started it up. If it works would I see my image in skype or do I have to do something to make it visible?

---

### Post by penguinv on 2010-03-18
> **no2498 said:**
> do this open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 and v4l2 click the bottom test button for each 1

now you need a program like  cheese to see/use it on
it is already loaded on 910 karmic
ekiga softphone is loaded also and will most likely see your cam

OK now I see ekiga softphone.
So I click on it. It gives me trouble then stats, I sign up for things, start it up, click on everything, confrence, find see my own camera somewhere. Ah ha, it works. But I cant get into configuration Assistant. when I try Preferences it stick s wit the menu open. Oh and it's always on top. (I'd rather not. But I see myself -- after I turned the light on my face.

Bueno. And now, how do I do the same in skype which hopefully is better behaved and used by more persons.

I'm so happy to have something -- and NOT to have gone and read a bunch first. On the other hand EXIGA froze. I had to forcequit. And it didnt have a handy microphone check.

Now -- how to skype? When I was in skype I could not hear myself. That's a bad sign.

I appreciate that you read this and hope for good advice.
So far better than before.
Thanks.

I've been working on it.

---

### Post by penguinv on 2010-03-19
[SIZE="2"]It worked, then it didnt.[/SIZE]

I neglected to mention that in ekiga it asked for my password and then didnt accept it. I finally clicked, [FONT="Fixedsys"]Deny.[/FONT]I thought I finessed that but when I reopend it the same thing happened.

[INDENT] [FONT="Fixedsys"]The application desktop_couch service (/usr/bin/python2.6) wants access to the default keyring but it is locked.[/FONT][/INDENT]

(what is the keyring?)

then **I read more on Skype and Web Cameras**
[INDENT]Following the recent release of a beta version of Skype that has support for video calling, this page will give a list of webcams that have been tested on Skype, and other details. This may differ from the list of webcams working in general on Ubuntu, given here. For general webcam issues see here.[/INDENT]

[LIST]
[*]If your webcam is not working at all or not consistently you may try the following hack.
[/LIST]

astafidli  New member  Posts: 3 
I have found ***horrible hack*** how to make this camera work under Linux :-)

**But he didnt have quite the same situation:**
I am trying to get my Logitech quickcam 5000 pro work with Skype 2.0.0.72 on Linux Ubuntu 8.04 Hardy Heron

[INDENT]1. Install VMware server, Windows XP guest, Skype for Windows
2. Once the VMware and XP guest is started and before connecting the camera to the guest using Devices -> Logitech Audio Device -> Connect run the following in the console
sudo rmmod ehci-hcd
3. Do Devices -> Logitech Audio Device -> Connect
Windows will complain that the device can run faster but that is OK.
4. Now you can Skype using this camera and microphone on this camera. Works beautifully even though it runs in virtual machine (Core 2 Duo 1.8Ghz/2GB ram). 

This just proofs that this camera not working in Linux is combination of two things
1. Bug in the camera USB handling which is solved using rmmod ehci-hcd
2. Bug/Missing feature in Skype for Linux handling the video format provided by this camera. 

This post has been edited by bastafidli: Thu Oct 23 2008, 07:49[/INDENT]

on the page [http://forum.skype.com/index.php?showtopic=217441&st=0&p=1007431&#entry1007431](http://forum.skype.com/index.php?showtopic=217441&st=0&p=1007431&#entry1007431)

In My Dreams: someday this all will "just work".

For now I'll see if there is any help from the community.

---

### Post by penguinv on 2010-03-19
I just cant quit.
I found this.

Logitech Quickcam for Notebooks
Ubuntu 7.10
ld  (whatever that is) 046d:08ae
driver = gspca
Works in Ekiga but is not recognized in Skype 2.0.0.27

**Testing things in Ubuntu terminal:**
 
 **lsmod |grep videodev**
videodev               36736  1 gspca_main
v4l1_compat            14336  1 videodev

**gstreamer-properties** - brings up a GUI window called **Multimedia systems Selector**. I saw my image. Then it couldnt do it again. It wasnt clear how to test the mic built into the webcam but I ended up with it on ALSA - USB.

For video, default output gave me a test screen: not the cam output.
default input (which gave me the cam output the first time I tried it) 

I GOT ERRORS: lots in terminal:
[INDENT]gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink' and repeated for a host of other plugins
... 
gstreamer-properties-Message: Error running pipeline 'OSS - Open Sound System': Could not open audio device for recording. [gstosssrc.c(383): gst_oss_src_open (): /GstPipeline:pipeline2/GstOssSrc:osssrc2:
Unable to open device /dev/dsp for recording: Device or resource busy]
... 
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff[/INDENT]

The nice thing was that it kept showing the cam image till I closed it.


**I started ekiga.** I put it on local video.
Configuration assistant: is what signs me in so it did work when it was supposed to (earlier) and I hadnt identified its title.
Preferences open: (I havent started the camera) 

I didnt sign in. **I went to conference room**. It dialed me into [email]501@ekiga.org[/email] I clicked but this time it didnt give me the window for my camera image. 
**Audio settings:** on max mic sensitivity I could see it on the monitor. Great.

THERE IS NO APPARENT WAY TO CLOSE THE CONNECTION. I did click the red item near the greyed out green receiver (legacy!)

This time when I wnet back to then ekiga window, after typing in here, well it wouldnt even get anything in it.

What now?

---

### Post by no2498 on 2010-03-19
you may need to reset the gstreamer-properties

cheese sees my cam but after i start cheese no other program see the cam
i like wxcam 
[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

you can also find it at [http://www.getdeb.net/welcome/](http://www.getdeb.net/welcome/)

your cam will work on ubuntu 910
you had it on 1 time is all it takes
hope this helps

---

### Post by aldous on 2010-06-23
You are not crazy and I see the same thing since upgrading to 10.04.  If you run cheese from the command line you will likely see something like this:


libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffd9
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff

The issue is with libv4l and rebuilding the latest from source doesn't help.

My lsusb:
Bus 005 Device 004: ID 046d:089d Logitech, Inc. QuickCam E2500 series

---

