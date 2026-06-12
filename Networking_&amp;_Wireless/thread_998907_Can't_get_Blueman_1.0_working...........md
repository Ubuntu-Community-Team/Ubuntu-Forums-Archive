---
title: "Can't get Blueman 1.0 working.........."
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by tsbaker on 2008-12-01
I followed the thread on how to get Blueman and then what to do with it there after. I've got the files. Instructions said I could right click and use gDebi installer, however that is not an option. I tried using the instructions that came with the download on how to build the app from command line, and that doesn't work either. I'm not an expert when it comes to Linux, but I'm certainly no novice either and I cannot figure this out. Someone please help or direct me to a good walk through bc I've been working on this for 2 hours now and at a loss. Thanks in advance

---

### Post by walmis on 2008-12-01
1.0 is not yet ready, you can try version 0.6 though.

add this repository: [https://edge.launchpad.net/~blueman/+archive](https://edge.launchpad.net/~blueman/+archive)

and sudo apt-get install blueman

Note that it will replace bluez 4 with bluez 3. You can revert back by reinstalling bluez package.

---

### Post by tsbaker on 2008-12-01
thanks for the speedy reply, that would explain it. However, I have already done that, and in assuming I was in error, I removed it and tried for v1.0. I followed these instructions from another post,

"I bought the Sony DR-BT50 headphones at a store where I have 30 days to return them. Using blueman I got them paired up. Using Services > Headset Connection I entered the passkey according to the manual that came with the headphones, and it worked."

When in Blueman, I went to Services > but there is no "Headset Connection" option. Am I missing something or is worded different etc?

I tried the inquiry option to try and scan for my headset, which happens to be the above mentions pair of Sony's also, and my laptops adapter cannot find them. 

If it helps or matters, Im running AMD64 Intrepid, kernel version 2.6.27-9

thanks again

---

### Post by tsbaker on 2008-12-02
Well after no response, and doing some seperate research, it turns out that my Bluetooth adapter was partly to blame. I purchased a dif. one and it works, but only from within my virtualization. Blueman sees the adapter, and see my room mates phone, but does not see my Sony DR-BT50 head phones, but all other bluetooth devices in the house see them almost instantly. It has to be a problem with either Ubuntu or Blueman or I just plain dont get linux. 

If anyone reads this and had any ideas, I'm all ears, if not, I'm going to suffer XP until something turns up. Thanks

---

### Post by John Jason Jordan on 2009-01-14
> **tsbaker said:**
> If anyone reads this and had any ideas, I'm all ears, if not, I'm going to suffer XP until something turns up. Thanks

I'm coming to this thread very late, but I am the one who bought the DR-BT50 headphones quoted previously in this thread. I have some update information.

My headphones worked fine with Hardy. I did find Blueman a great help in getting them paired up although, now that I have a bit more knowledge of how bluetooth works I might have been able to do it without Blueman.

A month ago I finally upgraded my computer from Hardy to Intrepid. And ever since the headphones have not worked. In truth, I was not using them for most of the time after upgrading to Intrepid and I was unaware that they were no longer working. But a few days ago I discovered the problem and have been working on fixing it ever since. At this writing I have not found the magic key.

---

