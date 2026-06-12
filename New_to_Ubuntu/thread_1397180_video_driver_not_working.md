---
title: "video driver not working"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by humanmusic on 2010-02-03
using the new ubuntu. I am a newb with linux. Video on youtube is poor so I know the video driver is not working because I used a dif version of linux and it had been fine. How do I check hardware and drivers and find alt. drivers in ubuntu?

---

### Post by 2kquik on 2010-02-03
Go to Applications --> Accessories --> Terminal

Type "lspci" without quotes and press Enter.

It should tell you information on what video card you are using. ;)

---

### Post by drzoo2 on 2010-02-03
> **humanmusic said:**
> using the new ubuntu. I am a newb with linux. Video on youtube is poor so I know the video driver is not working because I used a dif version of linux and it had been fine. How do I check hardware and drivers and find alt. drivers in ubuntu?

Before jumping into hardware and video drivers, were both computers using the same version of flash? As far as I know, Linux doesn't yet have the capability to decode flash video in GPU hardware. Adobe has only enable this functionality in Windows.

z

---

### Post by humanmusic on 2010-02-03
> **drzoo2 said:**
> Before jumping into hardware and video drivers, were both computers using the same version of flash? As far as I know, Linux doesn't yet have the capability to decode flash video in GPU hardware. Adobe has only enable this functionality in Windows.

z

The first was YLMF and the video and everything worked great, then I tried the new ubuntu and I had video issues, on youtube and some of the desktop stuff has issues. I d/l a linux version of flash from adobe and I was finally able to view youtube video but its slow and choppy. It wasnt like that with a bare install of YLMF which is based on ubuntu. I dont know what is the difference between the two OS's but just trying to get more familiar with the new ubuntu.

---

### Post by humanmusic on 2010-02-03
> **2kquik said:**
> Go to Applications --> Accessories --> Terminal

Type "lspci" without quotes and press Enter.

It should tell you information on what video card you are using. ;)

Thanks, I have identified the video card but dont know what to do from there.


01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05)

---

### Post by &#27832;&#12363;&#12373;&#12428;&#12383;&#39770;&#12398;&#20154;&#12399;&#29483;&#12434;&#33296; on 2010-02-03
> **humanmusic said:**
> Thanks, I have identified the video card but dont know what to do from there.


01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05)

That appears to be a very old card. It also seems to be poorly supported under GNU/Linux.

---

### Post by drzoo2 on 2010-02-03
> **humanmusic said:**
> The first was YLMF and the video and everything worked great, then I tried the new ubuntu and I had video issues, on youtube and some of the desktop stuff has issues. I d/l a linux version of flash from adobe and I was finally able to view youtube video but its slow and choppy. It wasnt like that with a bare install of YLMF which is based on ubuntu. I dont know what is the difference between the two OS's but just trying to get more familiar with the new ubuntu.

The difference could be in CPU overhead. If you have a slower computer your CPU may be peaking. Flash video is very CPU intensive. 

Go to "system" --> "admin" --> "system monitor" Select the recources tab while playing flash and check to see if your CPU is at 100%. If it is, it probably isn't your Video card or driver.

---

### Post by humanmusic on 2010-02-03
> **&#27832 said:**
> That appears to be a very old card. It also seems to be poorly supported under GNU/Linux.

Yes, its from an older P4 Toshiba laptop. Can you tell me how to tell that its poorly supported? This would help me solve issues in the future. Is there a website you check?

---

### Post by &#27832;&#12363;&#12373;&#12428;&#12383;&#39770;&#12398;&#20154;&#12399;&#29483;&#12434;&#33296; on 2010-02-03
> **humanmusic said:**
> Yes, its from an older P4 Toshiba laptop. Can you tell me how to tell that its poorly supported? This would help me solve issues in the future. Is there a website you check?

Your laptop is Pentium 4? Do you know the CPU speed?

---

### Post by humanmusic on 2010-02-03
> **drzoo2 said:**
> The difference could be in CPU overhead. If you have a slower computer your CPU may be peaking. Flash video is very CPU intensive. 

Go to "system" --> "admin" --> "system monitor" Select the recources tab while playing flash and check to see if your CPU is at 100%. If it is, it probably isn't your Video card or driver.


The CPU was maxing out while I played a youtube video. But in YLMF the video played very well. Any idea what might be the difference? Is there a better flash program for linux than adobe?

---

### Post by humanmusic on 2010-02-03
> **&#27832 said:**
> Your laptop is Pentium 4? Do you know the CPU speed?

2ghz, 1 gig ram

---

### Post by &#27832;&#12363;&#12373;&#12428;&#12383;&#39770;&#12398;&#20154;&#12399;&#29483;&#12434;&#33296; on 2010-02-03
> **humanmusic said:**
> 2ghz, 1 gig ram

What was the 'other' version of Linux that worked so well?

---

### Post by drzoo2 on 2010-02-03
> **humanmusic said:**
> The CPU was maxing out while I played a youtube video. But in YLMF the video played very well. Any idea what might be the difference? Is there a better flash program for linux than adobe?

Without listing the process differences between the two installs I really don't know. Try turning off compiz? Though I can't imagine it would be on with a Video card that it that old.

Back into system monitor, click the process tab. Then click the CPU list twice. This will show the processes that are eating the most CPU cycles. Anything extraordinarily high?

---

### Post by humanmusic on 2010-02-03
> **&#27832 said:**
> what was the 'other' version of linux that worked so well?

ylmf

---

### Post by humanmusic on 2010-02-03
> **drzoo2 said:**
> Without listing the process differences between the two installs I really don't know. Try turning off compiz? Though I can't imagine it would be on with a Video card that it that old.

I dont know where to find compiz.

> Back into system monitor, click the process tab. Then click the CPU list twice. This will show the processes that are eating the most CPU cycles. Anything extraordinarily high?  

firefox is 16 percent and gnome system monitor is 23 percent, and thats not playing a video. Playing a video firefox goes up to 59 percent.

---

### Post by &#27832;&#12363;&#12373;&#12428;&#12383;&#39770;&#12398;&#20154;&#12399;&#29483;&#12434;&#33296; on 2010-02-03
> **humanmusic said:**
> ylmf

A Chinese XP clone? (&#65507;&#9661;&#65507;)

---

### Post by humanmusic on 2010-02-03
> **&#27832 said:**
> A Chinese XP clone? (&#65507;&#9661;&#65507;)

Yep. Its basically ubuntu and gnomeXp but it appears to work easier than plain ubuntu so far.

BTW, I am running gnomeXp on the current ubuntu as well.

---

### Post by &#27832;&#12363;&#12373;&#12428;&#12383;&#39770;&#12398;&#20154;&#12399;&#29483;&#12434;&#33296; on 2010-02-03
> **humanmusic said:**
> Yep. Its basically ubuntu and gnomeXp but it appears to work easier than plain ubuntu so far.

BTW, I am running gnomeXp on the current ubuntu as well.

Does it use Firefox as the default browser?

---

### Post by humanmusic on 2010-02-03
> **&#27832 said:**
> Does it use Firefox as the default browser?

yes

---

### Post by &#27832;&#12363;&#12373;&#12428;&#12383;&#39770;&#12398;&#20154;&#12399;&#29483;&#12434;&#33296; on 2010-02-03
> **humanmusic said:**
> yes

3.0 or 3.5?

---

### Post by drzoo2 on 2010-02-03
Right click on your desktop --> " change desktop background" --> "visual effects"

Make sure it's set to none.

---

### Post by humanmusic on 2010-02-03
> **&#27832 said:**
> 3.0 or 3.5?

I dont recall what version they used.

---

### Post by humanmusic on 2010-02-03
> **drzoo2 said:**
> Right click on your desktop --> " change desktop background" --> "visual effects"

Make sure it's set to none.

Yes, its set to none but I tried for NORMAL but it wasnt able to enable that. Does that imply a video card driver issue?

---

### Post by &#27832;&#12363;&#12373;&#12428;&#12383;&#39770;&#12398;&#20154;&#12399;&#29483;&#12434;&#33296; on 2010-02-03
> **humanmusic said:**
> Yes, its set to none but I tried for NORMAL but it wasnt able to enable that. Does that imply a video card driver issue?

It sounds more like resource hogging.

---

### Post by drzoo2 on 2010-02-03
> **humanmusic said:**
> Yes, its set to none but I tried for NORMAL but it wasnt able to enable that. Does that imply a video card driver issue?

Yes and no. It won;t enable because of your video card but not because it's broken or a driver issue. It's because of it's power. Compiz is Desktop 3-D affects.

z

---

### Post by &#27832;&#12363;&#12373;&#12428;&#12383;&#39770;&#12398;&#20154;&#12399;&#29483;&#12434;&#33296; on 2010-02-03
> **drzoo2 said:**
> Yes and no. It won;t enable because of your video card but not because it's broken or a driver issue. It's because of it's power. Compiz is Desktop 3-D affects.

z

Power?

---

### Post by drzoo2 on 2010-02-03
> **&#27832 said:**
> Power?

Sorry, not power as in voltage/current issues. Power as in it is too old and not capable of running those effects.

---

### Post by &#27832;&#12363;&#12373;&#12428;&#12383;&#39770;&#12398;&#20154;&#12399;&#29483;&#12434;&#33296; on 2010-02-03
> **drzoo2 said:**
> Sorry, not power as in voltage/current issues. Power as in it is too old and not capable of running those effects.

It's capable.

---

### Post by drzoo2 on 2010-02-03
> **&#27832 said:**
> It's capable.

I stand corrected since I don't own that card and made an assumption. It needs the right driver then. I thought you said it wasn't well supported?

---

### Post by &#27832;&#12363;&#12373;&#12428;&#12383;&#39770;&#12398;&#20154;&#12399;&#29483;&#12434;&#33296; on 2010-02-03
> **drzoo2 said:**
> I stand corrected since I don't own that card and made an assumption. It needs the right driver then. I thought you said it wasn't well supported?

I meant the drivers are poor.

---

### Post by humanmusic on 2010-02-03
Where can I go to find any other drivers? Apparently YLMF had a better driver. I might also need advice on how to install a driver unless its automatic.

---

### Post by &#27832;&#12363;&#12373;&#12428;&#12383;&#39770;&#12398;&#20154;&#12399;&#29483;&#12434;&#33296; on 2010-02-03
> **humanmusic said:**
> Where can I go to find any other drivers? Apparently YLMF had a better driver. I might also need advice on how to install a driver unless its automatic.

The drivers come OOtB, unless Ubuntu doesn't provide the Savage driver anymore.

---

### Post by humanmusic on 2010-02-03
> **&#27832 said:**
> The drivers come OOtB, unless Ubuntu doesn't provide the Savage driver anymore.

I dont understand what OOtB means...

---

### Post by &#27832;&#12363;&#12373;&#12428;&#12383;&#39770;&#12398;&#20154;&#12399;&#29483;&#12434;&#33296; on 2010-02-03
> **humanmusic said:**
> I dont understand what OOtB means...

OOtB means;

**O**ut

**O**f

**t**he

**B**ox

---

### Post by humanmusic on 2010-02-03
> **&#27832 said:**
> OOtB means;

**O**ut

**O**f

**t**he

**B**ox

Ok, is there a place that would have the driver?

---

### Post by &#27832;&#12363;&#12373;&#12428;&#12383;&#39770;&#12398;&#20154;&#12399;&#29483;&#12434;&#33296; on 2010-02-03
> **humanmusic said:**
> Ok, is there a place that would have the driver?

Possibly, but I think the driver may already be installed. 

When you put the desktop effects to normal, what, if any message, do you get?

---

### Post by humanmusic on 2010-02-03
> **&#27832 said:**
> Possibly, but I think the driver may already be installed. 

When you put the desktop effects to normal, what, if any message, do you get?

Desktop effects could not be enabled.

---

