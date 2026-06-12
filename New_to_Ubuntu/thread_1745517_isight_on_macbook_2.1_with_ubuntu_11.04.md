---
title: "isight on macbook 2.1 with ubuntu 11.04"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by fireglare on 2011-05-01
Hi there,

I have tried all sorts of things that i have read on ubuntu help forums... but i just can't get it to work!
I have downloaded the 'appleusbvideosupport' firmware and have tried to get it to happen through terminal with the commands sudo apt-get install isight-firmware-tools etc.... but it just can't source the 'apple drive' ?? i don't know enough about all this can anyone give me a tip on what to do or what software i can install to get it working? I can't seem to be able to open the appleusbvideosupport file at all, i tried saving it outside of 'downloads'folder or opening it but i can't choose an application and i am very confused...

so anyway, help needed!!

Thanks anyone :)

---

### Post by fireglare on 2011-05-01
oh and it's running on ubuntu only.... no os x..... :)

---

### Post by fireglare on 2011-05-01
The message I get on terminal is 

Apple Driver File not found. the apple driver you specified does not exist. The firmware extraction has been aborted.

:(

---

### Post by michi21609 on 2011-05-01
Hi! I have exactly the same problem:

- Ubuntu 11.04
- MacBook 2,1
- 64bit version

What I tried to do is to use the newer isight-firware-tools
You can find it hiere: [https://launchpad.net/isight-firmware-tools/main/1.6](https://launchpad.net/isight-firmware-tools/main/1.6)
--> best use the beta4, if that not works, try to compile by yourself

-> Now my webcam is recognized by Cheese and Skype but the video is still black :-( But maybe your lucky!

If you find a solution to realy get it running, let me now! I will tell you, if I get it running!

---

### Post by mredding on 2011-05-02
Try using VLC to test the camera as explained in [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam). I performed the setup found at [http://ubuntuforums.org/showthread.php?t=1609402](http://ubuntuforums.org/showthread.php?t=1609402) (except change maverick to natty) on my Macbook 2,1 and Cheese shows a black screen while VLC shows the camera working properly. I haven't found a solution yet.

You can test your camera after installing vlc by entering the following in Terminal: 
vlc v4l2:///dev/video0

EDIT: I fixed it. Sort of. 
In Cheese I get three resolution options in Edit -> Preferences: 640x480, 352x288, & 320x240. I changed it from 640x480 to something else, and it worked. Then I changed it back to 640x480, and it still worked. WTF?

If it means anything, I installed from the amd64+mac desktop CD.

---

### Post by michi21609 on 2011-05-02
Hi mredding!

Exactly same effect here! In VLC i have Video, and your strange cheese behaviour I can also reproduce....

I think I will have a look if there is already a thread on launchpad. Otherwise I will open one.... That problem has to be solved...

Thanks!

---

### Post by michi21609 on 2011-05-02
Hmmm.... now I am able to run Skype with working video by entering the following in Terminal:

LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype

---

### Post by alienseer23 on 2011-05-03
Just chiming in: I have a macbook 4.1, running natty, same behavior with cheese.

---

### Post by misterdave on 2011-05-08
> **michi21609 said:**
> Hmmm.... now I am able to run Skype with working video by entering the following in Terminal:

LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype


Hi guys. I'm new to linux/ubuntu as well.  Black macbook 4,1 , 2.4ghzC2D. Running 64bit 11.04 natty.
I agree with the above issues. I installed newest isight update pack using the firmware file extracted from osx tiger disc. 

Still have the issues above. ISight works in vlc using terminal code above.. works in cheese after the size resets.. works in guvcview as well... works in skype as listed above with LD_PRELOAD command .. 

But... 
ISight doesnt work in skype when skype is loaded normally.. just get black screen.. also using MulitmediaSystemSelector doesnt give me an image.
Does anyone have knowledge of a fix?
Is there some way to enable automatic image adjustments? I'm wondering if its just not adapting the image to lighting or something? None of the programs that so an image seem to auto adjust the the image (like auto contrast or colouring changes.)

Fingers are crossed that help is out there to get this functioning as well as it does in Snow Leopard with Skype.

Dave

---

### Post by dstien on 2011-05-18
I'll chime in here and say that I have the same problem and same strange behavior as all of the other posts.  I'm using a MacBook 1,1.  Hopefully if anything has been discovered someone can put a link here for everyone who finds this thread.

---

### Post by nsxtech on 2011-05-31
I found that using isight-firmware-tools 1.5.93 from Debian Sid worked for me. MacBook 3.1, Triple booting Snow Leopard, 11.04 and Vista.  

Interestingly when starting Cheese at 640x480 the screen is black. If the preference is changed to 352x288 it will display. Change back to 640x480 works. If Cheese is closed and reopened you will have to repeat the process.

Hopefully helpful.

---

### Post by cunyao on 2011-07-07
> **michi21609 said:**
> Hmmm.... now I am able to run Skype with working video by entering the following in Terminal:

LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype


On my macbook works:
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype

Does anyone know how to run with Skype without terminal ?

---

### Post by bkanuka on 2011-08-15
same odd cheese behavior.  macbook 4.1

anyone NOT have this odd behavior? - please post your isight driver if possible.

Also, is there a bug report for this?

EDIT: Yes, there is.  Please go here and mark this bug as effecting you too.
[https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/796471](https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/796471)

EDIT2: Some interesting discussion here: [http://ubuntuforums.org/showthread.php?t=1472809&page=5](http://ubuntuforums.org/showthread.php?t=1472809&page=5)  no time to try everything suggested today though.

---

### Post by ukberry on 2011-09-19
I've just got my iSight working with Skype on Macbook 2.1 running Natty by:
[LIST]
[*]Adding the Mactel PPA repository: [https://launchpad.net/~mactel-support/+archive/ppa?field.series_filter=natty]("https://launchpad.net/~mactel-support/+archive/ppa?field.series_filter=natty")
[*]Reinstalling the isight-firmware-tools (with a dpkg-reconfigure too) to extract the iSight firmware
[*]Creating a menu entry with the command:
```
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype'
```
[/LIST]

I can confirm that when using v4l1compat.so, the iSight is detected but has blank output on Skype's video test.

Cheese also only displays output when the resolution is set at something other than 640x480 (but 640x480 subsequently works after changing the resolution)

Hope this helps somebody.

---

### Post by kesavachandran on 2011-10-10
Hi,
I got a clue from mredding  for a couple of steps forward with my nagging Cheese on Natty 11.04 experiencing what you had stated in this forum.From my terminal $cheese  got outputs indicating my version of Cheese is Bug Ridden. ,saw a cryptic --sync in the out put, felt it was a clue to a work around.Cheese can be successfull through terminal by $ sudo cheese --sync Mind you it is only a one time result,have to repeat the command line but the result is live and stable.Try it and be convinced.
Kesava:D

---

### Post by kesavachandran on 2011-10-10
Refer my previous entry where Cheese was made functional with certain riders.To meet its expected function use terminal like $ sudo -V clear gdk_x_error  ENTER.This will negate the BUG a report of which has been submitted. Applications>Sound&Video>Cheese Webcam Booth will not find relief by this.

---

### Post by Roneous on 2011-10-19
> **fireglare said:**
> Hi there,

I have tried all sorts of things that i have read on ubuntu help forums... but i just can't get it to work!
I have downloaded the 'appleusbvideosupport' firmware and have tried to get it to happen through terminal with the commands sudo apt-get install isight-firmware-tools etc.... but it just can't source the 'apple drive' ?? i don't know enough about all this can anyone give me a tip on what to do or what software i can install to get it working? I can't seem to be able to open the appleusbvideosupport file at all, i tried saving it outside of 'downloads'folder or opening it but i can't choose an application and i am very confused...

so anyway, help needed!!

Thanks anyone :)
Hello! I have the same setup, macbook 2.1 without OSX and with Ubuntu 11.10. Nothing in this thread has helped me though! I keep getting the message in terminal "command not found" or "file directory doesnt exist" even though I copied it down and can see it! I also didn't have permission a few times???!?! WTF. I'm so frustrated I may just resort back to supporting corporate greed and be able to talk to my family thousands of miles away. I tried to also follow the Ubuntu guide and it also failed miserably.

HELP, before I break my comp and fork out for bail outs:/

---

### Post by old_toby on 2011-11-23
A little different here: It works in VLC, but NEVER in cheese, even when I change the size. This is on Oneiric.

---

