---
title: "Skype no video"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by beew on 2010-12-11
I am trying to set up skype in 10.10 on my Samsung R469 laptop (Geforce G105M graphic card, the Nvidia driver is installed and works perfectly) It comes with  a built in webcam. The sound works flawlessly but there is no video. I opened Cheese and video works out of the box so it appears to be a skype problem.

I have no idea even where to begin for trouble shooting (like how to find out the webcam's model).

Please help, thanks.


Edited: an unrelated thing, it is not really a problem but just kind of odd. I have installed Skype on different machines and downloaded Skype from different sources (from Skype and from the Partners repository) but it is always the same. The guy (yes, it is a guy) in the test call service speaks some kind of Slavic language rather than English. He always greets me with something that sounds like "Dobilidan" I have checked and rechecked that all my settings are in English but it is all the same. I tried reinsinstalling Skype after deleting all configuration files (~/.skype) but it is still the same. I searched the internet but couldn't find anything. I wonder if this is normal.

---

### Post by diablo75 on 2010-12-11
Well, one way to find out some info about your camera is to run the following in a terminal window:

```
lspci
```

As well as:

```
lsusb
```

These commands list PCI and USB devices.  You'll notice they all have hardware identifying numbers in [brackets], that look like this [8003:3280].  Look over the list to find the name of your camera and it's hardware ID.  Then visit this link and see if there's any information about your camera and ways to get it to work with skype:

[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

Considering that it works just fine in Cheese, it would seem like a software or kernel module issue...

---

### Post by diablo75 on 2010-12-11
> **beew said:**
> 
Edited: an unrelated thing, it is not really a problem but just kind of odd. I have installed Skype on different machines and downloaded Skype from different sources (from Skype and from the Partners repository) but it is always the same. The guy (yes, it is a guy) in the test call service speaks some kind of Slavic language rather than English. He always greets me with something that sounds like "Dobilidan" I have checked and rechecked that all my settings are in English but it is all the same. I tried reinsinstalling Skype after deleting all configuration files (~/.skype) but it is still the same. I searched the internet but couldn't find anything. I wonder if this is normal.

I always download Skype from Skype's website (as a deb file).  I wouldn't trust it from another source unless it was in the official repositories.  If you did download it from their website it's possible there's a localization issue that's auto-feeding you a file that was meant for a different country.  I'd check the website for language/location menus when downloading.

---

### Post by beew on 2010-12-11
Hi, diablo75,

Thanks for the reply.

The webcam is z-star 0ac8:c33e  from the lsusb command. It is not on Ubuntu wiki's lists.

---

### Post by beew on 2010-12-11
> **diablo75 said:**
> I always download Skype from Skype's website (as a deb file).  I wouldn't trust it from another source unless it was in the official repositories.  If you did download it from their website it's possible there's a localization issue that's auto-feeding you a file that was meant for a different country.  I'd check the website for language/location menus when downloading.

I have downloaded from both Skype's website and The partners' repository the results are the same.

---

### Post by beew on 2010-12-11
Only information found is this [https://wiki.kubuntu.org/LaptopTestingTeam/Old/SamsungR519](https://wiki.kubuntu.org/LaptopTestingTeam/Old/SamsungR519) It says webcam works on jaunty but no mention of skype. I think webcam works on Maverick too since Cheese works out of the box. But skype is not working. :(

---

### Post by beew on 2010-12-12
Hello? Anyone?

---

### Post by tudor117 on 2010-12-12
Hi, for the weird Slavic Test Guy, try changing your Language and Country settings. Here's some pics to show you how.

As for the webcam, the one from the repos (skype 2.1.0.81-1ubuntu5) worked out of the box for me. That kind of surprised me because it would usually require some config for 64 bit systems. Try reading [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams) but no promises.
By the way, what architecture are you running? 64 bit or 32 bit?

---

### Post by beew on 2010-12-12
> **tudor117 said:**
> Hi, for the weird Slavic Test Guy, try changing your Language and Country settings. Here's some pics to show you how.

As for the webcam, the one from the repos (skype 2.1.0.81-1ubuntu5) worked out of the box for me. That kind of surprised me because it would usually require some config for 64 bit systems. Try reading [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams) but no promises.
By the way, what architecture are you running? 64 bit or 32 bit?

Hi, I have installled the same version of Skype from the repo (previously I have also installed from Skype). I use 32 bits.

I will check my profile and see if that would change the Slavic test guy.

I have searched the Wiki article, my card is not on any list, see above. However, this just caught my eye
> If: 1. You can see video in Cheese or other apps; but 2. You only see a  white rectangle in Skype when you activate video;and 3. Testing the  video under the Skype Preferences fails; BUT 4. the person you are  calling CAN see video of you from your webcam, then: the problem may be Cairo-Dock. 
I can't call anyone to test for 4 right now, will try that tomorrow. If it is Cairo Dock then it is easy to fix. 

Thanks.

---

### Post by mastablasta on 2010-12-13
does the camera work in gstreamer (type in terminal)
 
also try to run skype like this:
```
 
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

```

---

### Post by labinnsw on 2010-12-13
[This post sets out how I got this to work]("http://ubuntuforums.org/showpost.php?p=9419207&postcount=50")

---

### Post by beew on 2010-12-13
Thanks mastablasta and labinnsw,

I will try your suggestions later when I go home. However since I have lost my internet connection at home it may be a while before I can post back.

mastablasta, how to test if camera works in gstreamer? Sorry, I am a total newbie for this. :)

---

### Post by freshmeatz on 2010-12-13
if you use cario dock use

```
sh -c 'export XLIB_SKIP_ARGB_VISUALS=1 && LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype'
```

Just make a launcher and place this in the command line

---

### Post by RedRat on 2010-12-13
First, is your camera on? On my laptop I turn it on by holding down the Fn key and hitting F10. Run the Ubuntu app Cheese, which should be pre-installed in your system. If not download it from the repos. You might want to try this before trying Skype to make sure your system actually sees the camera.

---

### Post by Harald Franzen on 2010-12-25
> **freshmeatz said:**
> if you use cario dock use

```
sh -c 'export XLIB_SKIP_ARGB_VISUALS=1 && LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype'
```

Just make a launcher and place this in the command line

This is the one that worked for me, as I run Cairo-dock too.
Thanks!

---

### Post by mastablasta on 2010-12-25
> **beew said:**
> 
mastablasta, how to test if camera works in gstreamer? Sorry, I am a total newbie for this. :)

run gstreamer from terminal using this command (you can copy it and apste it in the terminal):

```
gstreamer-properties
```


A properties window will pop up. Then select video and where you see a device for video input press the test button.

---

### Post by Harry h on 2011-01-02
Fix for webcam not working in Skype (Beta) Version 2.1.0.81 with Ubuntu 10.10
 

 Skype is trying to load Video for Linux1 (v4l1) which does not exist in Ubuntu 10.10.
 

 To fix this problem I made the simple change in the last line of the /usr/bin/skype-wrapper as below:-

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so  /usr/bin/skype "$@"
 to
LD_PRELOAD=/usr/lib/libv4l/v4l2compat.so  /usr/bin/skype "$@" (note the 2 in v4l2compat.so)

To check  you Default Input go Applications > Accessories > Terminal and type (gstreamer-properties) without the brackets.  When the Multimedia Systems Locator &#8211; Settings panel appears  click on the Video tag and check your  Default Input. In nine I found the Default Input is Video for Linux2 (v4l2). While the choices Ubutu 10.10 has is Video for Linux (v4l) or Video for Linux2 (v4l2) there is no Video for Linux1 (v4l1). When using Video for Linux (v4l) as the Default Input in GStreamer properties a test returns an error message.

---

### Post by beew on 2011-01-18
I use the Cairo Dock and freshmeatz's work around works for me. Also thanks  harryh  for the explanation for why this works.

Thanks everyone for the input. 

Sorry for leaving the thread dangling. I have been away for a few weeks and I didn't have regular internet connection.

---

### Post by jesuisbenjamin on 2011-01-27
> **Harry h said:**
> Fix for webcam not working in Skype (Beta) Version 2.1.0.81 with Ubuntu 10.10
 

 Skype is trying to load Video for Linux1 (v4l1) which does not exist in Ubuntu 10.10.
 

 To fix this problem I made the simple change in the last line of the /usr/bin/skype-wrapper as below:-

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so  /usr/bin/skype "$@"
 to
LD_PRELOAD=/usr/lib/libv4l/v4l2compat.so  /usr/bin/skype "$@" (note the 2 in v4l2compat.so)


Hi there: i cannot find the /usr/bin/skype-wrapper file you mention. How come you have it and i don't? Thanks for helping.

---

### Post by sdowney717 on 2011-02-19
yes, same here, no video
my gstreamer properties shows the usb camera works

I tried the LD load for v4l2 but still nothing

---

### Post by sdowney717 on 2011-02-20
It works now following this
[http://forum.skype.com/index.php?showtopic=144791](http://forum.skype.com/index.php?showtopic=144791).
> How to launch Skype + V4L2 directly from Gnome/Ubuntu Jaunty menus so that the webcam works:
Menu System --> Preferences --> Main Menu
In the window select Internet, then Skype
Click on [Properties] button
In Command enter this exacly as shown:
it used to say skype-wrapper

bash -c 'export LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so; skype'

It makes me wonder if skype-wrapper in the command line would have worked as I always was starting it from terminal

---

### Post by KingLex on 2011-02-20
i would like to ask what version of Skype are you using ? mine look out dated - :(

---

### Post by sdowney717 on 2011-02-20
skype beta 2.1.081

---

