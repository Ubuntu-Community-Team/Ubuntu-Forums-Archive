---
title: "Sony Vaio webcam issues"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by Big Russ on 2009-01-05
Hi there,
Having installed Ubuntu and getting to grips with it it seems pretty cool. I do have one problem though which is my built in webcam. The Lsusb command thing won't pit it up as it's not connected by USB but nothing seems to recognise it (let alone instal). Does anyone have any ideas how to find it?

many thanks in advance

---

### Post by blueridgedog on 2009-01-06
Just to verify, can you post the output of 

```
lsusb
```

?

---

### Post by malfindin on 2009-03-30
I'm having sort of the same problem, but it is really weird. When I first installed the Webcam worked fine I even have a picture of my girlfriend on the top of my compiz sphere that I took with my built-in web-cam then with no warning it just stoped working. Cheese no longer detects a camera. No one, even some very advanced Linux experts I know here in Las Vegas have had any success fixing it. Here's my output:

frank@FKSONYU:~$ lsusb
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 005: ID 044e:3012 Alps Electric Co., Ltd 
Bus 006 Device 004: ID 044e:3013 Alps Electric Co., Ltd 
Bus 006 Device 003: ID 044e:3010 Alps Electric Co., Ltd 
Bus 006 Device 002: ID 044e:3011 Alps Electric Co., Ltd 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 05ca:183b Ricoh Co., Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0d08:0300 UTStarcom 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

To anyone posting please address the issues of the original poster first before replying to mine. I'm only chiming in because my issue might be related to theirs and it might help to have two examples instead of one.

If my web-cam never worked again, it wouldn't matter...everything else on my laptop works better than it ever did or ever could have running windows Vista, I couldn't be happier.

malfindin

---

### Post by malfindin on 2009-03-30
OK got some info here. I got it working, but I wouldn't call my fix a solution by a long shot. I (ashamed to admit it) but I still have Windows vista on my laptop as a SECOND boot option (I almost never use it). I booted to Windows fired up the SONY web-cam utility and then reset the latop with the web-cam on...and surprise, surprise. it worked in Ubuntu Cheese. My guess is that the issue lies somewhere in the ability of the Linux driver to activate the web-cam from a sleeping state. Since I never exited the SONY program correctly it never had the chance to turn it off. I don't know if it will stay on now. But obviously resetting windows all the time is bound to cause issues eventually, so at best this is a poor workaround.

In the Linux driver properties (Linux Device Manager) I found a setting that seems like it might be the culprit. But honestly, I'm afraid to start messing around with deep blue scary config files unless something really necessary wasn't working. Web-cams I can live without.

What we need here is a poster that really knows there way around driver settings and how to edit them. It would save me from having to boot to Vista for anything(a worthy cause)--and don't forget I'm not the original poster, I'm only trying to help come up with a solution for him.

Cheers,

malfindin

---

### Post by Luchador561 on 2010-05-11
I am using 9.10, for a built in sony vaio webcam you need the R5U87x driver

see [here]("https://launchpad.net/%7Er5u87x-loader/+archive/ppa") for instructions, I also copied them below:

Installation:
1. sudo add-apt-repository ppa:r5u87x-loader/ppa
2. sudo apt-get update
3. sudo apt-get install r5u87x
4. sudo /usr/share/r5u87x/r5u87x-download-firmware.sh


worked right away for me.

---

### Post by no2498 on 2010-05-11
if you still need help

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the botton test button for each 1

try the cam in cheese

if it stops working redo the gstreamer-properties

do not open cheese again

read and install all the page tells you to

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

best i can say is i like the program

---

### Post by Sealbhach on 2010-05-11
> **Luchador561 said:**
> I am using 9.10, for a built in sony vaio webcam you need the R5U87x driver

see [here]("https://launchpad.net/%7Er5u87x-loader/+archive/ppa") for instructions, I also copied them below:

Installation:
1. sudo add-apt-repository ppa:r5u87x-loader/ppa
2. sudo apt-get update
3. sudo apt-get install r5u87x
4. sudo /usr/share/r5u87x/r5u87x-download-firmware.sh


worked right away for me.

I have the same camera, this works perfectly in 10.04 for me.

.

---

### Post by huemotor on 2010-06-12
What about 05ca:1837 webcam on Sony fz series? I have installed r5u870 driver, blacklisted uvcvideo and the camera gives double vision output with green rectangle. In xawtv video works under uvcvideo driver but not r5u870. In skype 2.1.0.81 double vision problem under r5u870 and no output under uvcvideo.

Ubuntu 10.04

Anyone help please.

---

### Post by sandy8925 on 2010-06-13
I have a sony cr35g laptop with inbuilt webcam and mic. using kubuntu 10.04. webcam not detected by anything including cheese and skype.there's no /dev/video device either.camera shows up under usb devices. output of lsusb is:

Bus 001 Device 002: ID 05ca:1839 Ricoh Co., Ltd Visual Communication Camera VGP-VCC6 [R5U870]

just spotted he r5u870 at the nd. will try installing the driver and see if it works.

---

### Post by sandy8925 on 2010-06-13
it works! detected as a uvc webcam. works in cheese and skype and should work in others as well. dunno abt the inbuilt mic though. anyone know how to use that?

---

### Post by pirron on 2010-06-14
> **huemotor said:**
> What about 05ca:1837 webcam on Sony fz series? I have installed r5u870 driver, blacklisted uvcvideo and the camera gives double vision output with green rectangle. In xawtv video works under uvcvideo driver but not r5u870. In skype 2.1.0.81 double vision problem under r5u870 and no output under uvcvideo.

Ubuntu 10.04

Anyone help please.
Have you tried what is at [http://ubuntuforums.org/showthread.php?t=1502624?](http://ubuntuforums.org/showthread.php?t=1502624?) (post#9) I have vaio CR360 and my webcam works even with skype.

---

### Post by sandy8925 on 2010-06-21
ok my inbuilt mic is working now. might be bcos i compiled the new kernel or bcos i missed seeing the settings. 

in kubuntu opened kmixer then: settings->configure channels. added the mic to the visible channels. then unmuted it and increased volume to full. also went to alsamixer and increased the mic volume but set mic boost to lowest since it was too sensitive then.

works well in guvcview with following settings: device set to my card instead of /dev/dsp ; sample rate 44100 Hz ; channels stereo ; audio format pcm.

BUT does not work properly in skype. skype gives a garbled voice but it's definitely working. probably something to do with the sample rate.

---

### Post by Dexter_Greycells on 2010-07-17
@Luchador561 - Thanks! I finally got Ubuntu 10.04 to detect my webcam in Cheese. I am able to make video calls in Empathy too but my video preview is greyed, split into two screens with bars and has a 3 second lag. I checked it with my friend on the other end and even he saw the same thing. However, I could see my friend clearly (he was on Windows 7). Must have something to do with frame rate and resolution. Trying to figure it out...

---

### Post by atherakhia on 2010-08-11
I have also been having issues with in-built Sony Vaio Webcam.
I am running Kubuntu KDE

here's my output to lsusb... can anyone help?

Bus 007 Device 002: ID 044e:300d Alps Electric Co., Ltd Bluetooth Controller (ALPS/UGPZ6)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05ca:1837 Ricoh Co., Ltd Visual Communication Camera VGP-VCC4 [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by danielsilipo on 2011-08-04
Installation:
1. sudo add-apt-repository ppa:r5u87x-loader/ppa
2. sudo apt-get update
3. sudo apt-get install r5u87x
4. sudo /usr/share/r5u87x/r5u87x-download-firmware.sh


worked right away for me.

That reply was brilliant!! Fixed my computer after months of annoyance. Thanks very much!!!!!!!!!!!

 		                   		  		  		  		  		  	   	 		[IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]   		 		 		 		 		  	 	 	 	 		  		 		 		 			[[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=9282752")

---

### Post by Coronas and Pretzels on 2011-10-05
:D> **Luchador561 said:**
> I am using 9.10, for a built in sony vaio webcam you need the R5U87x driver

see [here]("https://launchpad.net/%7Er5u87x-loader/+archive/ppa") for instructions, I also copied them below:

Installation:
1. sudo add-apt-repository ppa:r5u87x-loader/ppa
2. sudo apt-get update
3. sudo apt-get install r5u87x
4. sudo /usr/share/r5u87x/r5u87x-download-firmware.sh


worked right away for me.
  These worked perferfect for my Sony vgn-ar520e as well! Super Happy :D

---

### Post by dr_anirudh_shukla on 2011-10-25
> **Luchador561 said:**
> I am using 9.10, for a built in sony vaio webcam you need the R5U87x driver

see [here]("https://launchpad.net/%7Er5u87x-loader/+archive/ppa") for instructions, I also copied them below:

Installation:
1. sudo add-apt-repository ppa:r5u87x-loader/ppa
2. sudo apt-get update
3. sudo apt-get install r5u87x
4. sudo /usr/share/r5u87x/r5u87x-download-firmware.sh


worked right away for me.
wow. thanks. Worked for me 2.

---

### Post by Coddy on 2011-12-13
I have a VAIO VPCF11M1E and the built-in camera doesn't work. Here is what i get from lsusb:

Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0489:e00f Foxconn / Hon Hai 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Any ideas?:confused:

---

### Post by mebomechanicno1 on 2012-07-17
> **Sealbhach said:**
> I have the same camera, this works perfectly in 10.04 for me.
 
.
 
It finds the web cam on a Vaio SZ5VWN, but Cheese does not seem to want to take snapshots; experiments continue

---

### Post by mebomechanicno1 on 2012-07-17
> **mebomechanicno1 said:**
> It finds the web cam on a Vaio SZ5VWN, but Cheese does not seem to want to take snapshots; experiments continue
 
I correct myself, I have been playing with my iPad too long.  Instead of leaving the pix untidy on the foot of the desktop, Cheese files them neatly away in the Home directory.  Clever Cheese.

---

