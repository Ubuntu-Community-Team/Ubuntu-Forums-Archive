---
title: "Having problems with Firefox!"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by RandomP on 2009-04-22
I am not sure why, but whenever I am scrolling in firefox, up or down, it seems to be choppy. I know it is not the graphics card drivers since I installed those. Also, this problems is only happening in firefox and not in ubuntu's menus and stuff.

Anyone know how to fix this?

---

### Post by porchrat on 2009-04-22
> **RandomP said:**
> I am not sure why, but whenever I am scrolling in firefox, up or down, it seems to be choppy. I know it is not the graphics card drivers since I installed those. Also, this problems is only happening in firefox and not in ubuntu's menus and stuff.

Anyone know how to fix this?

I have experienced something like that, I don't know if that is what you experienced, but I had choppy lines across the screen whenever I scrolled up and down in Firefox. For me it was definitely a graphics driver issue, once I had updated the drivers everything was smooth.

If you have updated with the latest drivers I don't see why you would have a problem. Which drivers did you install and what card are you using?

---

### Post by RandomP on 2009-04-22
> **porchrat said:**
> I have experienced something like that, I don't know if that is what you experienced, but I had choppy lines across the screen whenever I scrolled up and down in Firefox. For me it was definitely a graphics driver issue, once I had updated the drivers everything was smooth.

If you have updated with the latest drivers I don't see why you would have a problem. Which drivers did you install and what card are you using?
I have an ATI Radeon 200 (I think it is not a card, but a chip built into the motherboard).
I installed the ATI/AMD Proprietary FGLRX graphics driver.
Just for the record, I have an AMD processor in this PC.

I am using Opera right now and the scrolling is better, but still a little choppy.

---

### Post by porchrat on 2009-04-22
> **RandomP said:**
> I have an ATI Radeon 200 (I think it is not a card, but a chip built into the motherboard).
I installed the ATI/AMD Proprietary FGLRX graphics driver.
Just for the record, I have an AMD processor in this PC.

I am using Opera right now and the scrolling is better, but still a little choppy.

Are you sure they installed properly? How exactly did you install them?

Did you run "fglrxinfo" to make sure you aren't still using the MESA drivers?

If not then go into the terminal (Applications --> Accessories --> Terminal) and type this into the console:

```
fglrxinfo
```

Post the output if you are unsure about it, but it should be pretty self-explanatory.

---

### Post by RandomP on 2009-04-22
> **porchrat said:**
> Are you sure they installed properly? How exactly did you install them?

Did you run "fglrxinfo" to make sure you aren't still using the MESA drivers?

If not then go into the terminal (Applications --> Accessories --> Terminal) and type this into the console:

```
fglrxinfo
```

Post the output if you are unsure about it, but it should be pretty self-explanatory.
They did install and are being used since they pop-up when I typed that in.

I installed them by going to System > Administration > Hardware Drivers.

Heres a video. I am not sure if you can see it clearly though.
[http://www.youtube.com/watch?v=TXeqaDEkFhM](http://www.youtube.com/watch?v=TXeqaDEkFhM)

---

### Post by porchrat on 2009-04-22
> **RandomP said:**
> They did install and are being used since they pop-up when I typed that in.

I installed them by going to System > Administration > Hardware Drivers.

Heres a video. I am not sure if you can see it clearly though.
[http://www.youtube.com/watch?v=TXeqaDEkFhM](http://www.youtube.com/watch?v=TXeqaDEkFhM)

Please post the output of fglrxinfo so that we can take a look.

I doubt the drivers under the "Hardware Drivers" section will be acceptable, I have always had bad experiences with them. I believe that is your problem. I recommend you download the drivers from the ATI website and install those.

In order to find the driver that you need for your specific card/chipset you need to go to [http://ati.amd.com/support/driver.HTML](http://ati.amd.com/support/driver.HTML) and pick your operating system from the list, and your card/chipset. Then download the file.

There is a guide to installing it [here]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide").

However the catalyst drivers come with an installer now so all you need to do is make the file you downloaded executable:
```
sudo chmod u+x ~/Desktop/filename
```
Where "filename" is the name of the file you downloaded (this assumed the file you downloaded is sitting on your desktop).

Then run the file using sudo:
```
cd ~/Desktop
sudo ./filename
```

Again "filename" is the name of the file you have downloaded (should have a .run file extension).

Then a GUI window should open after 30 seconds or so and you can just click through the installation. Much easier than the command line install and I have never had it cause a problem before.

Keep in mind that these are graphics drivers and if something goes wrong you are going to be unable to boot into the desktop. If this happens you can always go back to the old drivers by rebooting into the "recovery mode" and fixing the X-server (don't worry it only involves selecting the fix X-server option from the menu that comes up when you boot recovery mode, it is easy) and then rebooting normally and reinstalling the drivers from the "Hardware Drivers" window.

EDIT:
> **RandomP said:**
> I have an ATI Radeon 200 (I think it is not a card, but a chip built into the motherboard).
I installed the ATI/AMD Proprietary FGLRX graphics driver.
Just for the record, I have an AMD processor in this PC.

I am using Opera right now and the scrolling is better, but still a little choppy.
I run the Radeon Xpress 200M chipset with an AMD Turion and I can tell you now that I had the same problem you've mentioned until I installed the ATI catalyst drivers from the ATI website. Doing that solved my problem and sped up my entire Desktop environment a whole lot, allowing me to use compiz cube without a problem.

---

### Post by RandomP on 2009-04-22
This is what is says in the terminal when I type in fglrxinfo: 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.8543 Release

For more info on my PC:
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00496280&lc=en&dlc=en&cc=us&lang=en&product=1130851](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00496280&lc=en&dlc=en&cc=us&lang=en&product=1130851)

It is running with the AMD Sempron 2GHz processor and 512MB of RAM.

---

### Post by porchrat on 2009-04-23
> **RandomP said:**
> This is what is says in the terminal when I type in fglrxinfo: 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.8543 Release

For more info on my PC:
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00496280&lc=en&dlc=en&cc=us&lang=en&product=1130851](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00496280&lc=en&dlc=en&cc=us&lang=en&product=1130851)

It is running with the AMD Sempron 2GHz processor and 512MB of RAM.

Well as I mentioned before, I actually run pretty much the same chipset as you, the Radeon Xpress 200M (horrible chip, just horrible) and the drivers on the ATI website are what sorted me out.

However you definitely are running the ATI fglrx drivers they're probably just a little outdated as the ones in the Ubuntu repositories always are, however this should not be an issue because the drivers for these older Xpress200 chipsets are not updated very frequently.

My advice to you is still to download and install the latest drivers and see if they make a difference. They really helped me out.

Your machine has enough power that it shouldn't be causing the tearing you're seeing in firefox. I've run 8.04 on much weaker machines than the one you're running it on without any issues.

---

### Post by RandomP on 2009-04-23
> **porchrat said:**
> Well as I mentioned before, I actually run pretty much the same chipset as you, the Radeon Xpress 200M (horrible chip, just horrible) and the drivers on the ATI website are what sorted me out.

However you definitely are running the ATI fglrx drivers they're probably just a little outdated as the ones in the Ubuntu repositories always are, however this should not be an issue because the drivers for these older Xpress200 chipsets are not updated very frequently.

My advice to you is still to download and install the latest drivers and see if they make a difference. They really helped me out.

Your machine has enough power that it shouldn't be causing the tearing you're seeing in firefox. I've run 8.04 on much weaker machines than the one you're running it on without any issues.

The thing is I is, I installed the drivers from ATI, (the ones you linked me to) though I used an automatic install when the window poped up, maybe I should have done custom? I uninstalled the Ubuntu given ones by the way.

---

### Post by WatchingThePain on 2009-04-23
Choppiness isn't the same as tearing.
Any time I have seen choppiness it was down to the graphics driver.

---

### Post by porchrat on 2009-04-23
> **RandomP said:**
> The thing is I is, I installed the drivers from ATI, (the ones you linked me to) though I used an automatic install when the window poped up, maybe I should have done custom? I uninstalled the Ubuntu given ones by the way.

Well that is strange. That solved my problem straight away. As WatchingThePain said, I have never heard of that chopping problem being caused by anything other than a graphics driver issue.

---

### Post by RandomP on 2009-05-01
> **WatchingThePain said:**
> Choppiness isn't the same as tearing.
Any time I have seen choppiness it was down to the graphics driver.

This is frustrating since I know that older PC's can handle Ubuntu and Firefox quite well. 

I recently uninstalled Ubuntu from my PC's main 250GB hard drive and just today I have reinstalled it on my 80GB spare drive. So I have 74GB to play with while in Ubuntu. The choppiness problem still persists, but I like how much faster Ubuntu is upon start up than XP.

---

### Post by crjackson on 2009-05-01
It sounds like something is consuming a lot of CPU cycles and depriving it of the needed cycles to process the video.

Open a terminal and run:
```
top
```

From there you should be able to figure out what is eating up your cpu power.

---

### Post by RandomP on 2009-05-01
I just switched to 9.04. The choppiness is now gone... Wow.

Even my MS mouse's scroll wheel works good. I love Jaunty already.

It also seems that Jaunty does not support the ATI drivers I was using.

---

### Post by RandomP on 2009-05-01
Any way, thanks for all of the support you guys!

---

