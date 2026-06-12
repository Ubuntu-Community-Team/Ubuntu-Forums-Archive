---
title: "skype video problem"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by grobar87 on 2010-06-22
Hi
How to enable video on skype?When i recived camera from someone,just white box is showing and no video..

---

### Post by Ivkosky on 2010-06-22
Try to go to Skype Options - Video Devices and try to run Test. Also, take a look if you have your webcam listed in the Select webcam box.

If not, then Ubuntu does not recognize your webcam. It sometimes happen to me that Skype does not recognize my webcam and I have to restart the whole system... If the problem is permanent then Ubuntu wasnt able to find appropriate drivers to your webcam...

---

### Post by grobar87 on 2010-06-22
I don't have webcam,my problem is when i recive video from someone.Just white box and nothing....I hear audio but video is missing....

---

### Post by grobar87 on 2010-06-23
anyone??

---

### Post by pablolie on 2010-06-23
Ubuntu can be finicky about video camera support, so it is a bit of a hit and miss thing, unfortunately. 10.04 has made it easier, but the plug&play webcam world has not yet moved into Ubuntu... :-(

There are a coule pf places for drivers for some webcams, but I know in the past I wasn't too successful with the manual configuration.

---

### Post by grobar87 on 2010-06-23
But on karmic works perfectly...what is wrong on lucid :confused::confused::confused:

---

### Post by mongoose_za on 2010-06-23
I have the same problem.

My webcam used to work with skype then I upgraded to kernel 2.6.32-22. Since then I have not been able to view webcam from other people. Just white square.

If you ever find a solution I hope to try it aswell.
I'm on Lucid Lynx 64bit. I've tried skype via repositories and also tried static. Still same problem.

---

### Post by Ivkosky on 2010-06-23
Hmm

Skype is working fine for me under Lucid as well as Karmic (both 64 bit)...

**mongoose_za:** Do you have also your own webcam? Because grobar87 doesn't have webcam, I do and therefore I thought it could be a problem just in the case of not having one's own webcam.

---

### Post by grobar87 on 2010-06-23
Please someone tell me some messenger program with camera support,i need right now :confused:
Thanks.

---

### Post by mongoose_za on 2010-06-23
I have got a webcam.
My skype used to work perfectly until I did the kernel upgrade. Then I started getting the white blank screen when trying to receive a webcam feed from another person. 

My sending of webcam is OK. Other people can see me. I can't see them.

I reinstalled the previous kernel but that did nothing. Still the same problem.

> Video

  * Sometimes receiving video shows a white square on top-left part of the 
    window.
    
  * Skype does not work well with newer version of GSPCA Webcams driver (Linux
    Kernel >=2.6.27), possible workaround:
    - Ubuntu 32 bit: install "libv4l-0" package and launch Skype with: 
      LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
    - Ubuntu 64 bit: install "lib32v4l-0" package and launch Skype with: 
      LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
    - Other distributions might have the same library, but may have a 
      different path.

Found that in the SKYPE readme. I tried it and it didn't help either but may help someone else.

---

### Post by grobar87 on 2010-06-23
Thanks mongoose_za but it didn't help me too.I am so dissapointed...:sad: This is my only problem with ubuntu... I just want to be able to recive video...

---

### Post by ndstate on 2010-06-26
> **mongoose_za said:**
> I have got a webcam.
My skype used to work perfectly until I did the kernel upgrade. Then I started getting the white blank screen when trying to receive a webcam feed from another person. 

My sending of webcam is OK. Other people can see me. I can't see them.

I reinstalled the previous kernel but that did nothing. Still the same problem.



Found that in the SKYPE readme. I tried it and it didn't help either but may help someone else.


I am having the same issue, has anyone found a way to fix this?

---

### Post by ndstate on 2010-06-26
Anyone have any idea what the following means?

```
X Error, request 133, minor 18, error code 8 BadMatch (invalid parameter attributes) 
```

It came up in the terminal when I hit the video test button in Skype

---

### Post by ndstate on 2010-06-26
[http://ubuntuforums.org/showpost.php?p=9270395&postcount=27](http://ubuntuforums.org/showpost.php?p=9270395&postcount=27)

Works for me.

---

### Post by mongoose_za on 2010-10-29
I installed Ubuntu x64 10.10 and installed Skype from the repos. Since then I've had no problem with Skype :>

---

