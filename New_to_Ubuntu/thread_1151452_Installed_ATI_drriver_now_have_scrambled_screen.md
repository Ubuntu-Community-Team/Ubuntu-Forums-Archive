---
title: "Installed ATI drriver now have scrambled screen"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by servicetech on 2009-05-06
What to do? The computer works normally up until the ATI driver loads then goes to a scrambled screen. Do I have to start all over since I can't see to remove the ATI driver?
I'm posting on DW's windows machine... UGH

---

### Post by RedSingularity on 2009-05-06
Can you load the terminal interface?  Wait for the messed up screen to appear then press Ctl+Alt+F1.

---

### Post by servicetech on 2009-05-06
Terminal doesn't work once scrambled screen comes up
I can get terminal through safe mode

---

### Post by RedSingularity on 2009-05-07
```
sudo apt-get autoremove xorg-driver-fglrx
```

In terminal

---

### Post by servicetech on 2009-05-07
I tried it, no go. Since I haven't added much to this fresh install I just reformatted and started over. It's sad that making a driver install error brings ubuntu to it's knees.

---

### Post by Megamanic on 2009-05-07
I've just endured exactly the same experience with Ubuntu Studio on my nx6125 laptop. Graphics card not supported by latest ATI driver thanks to ATI dropping support for "older" cards - thanks guys.

My issue was even worse because Ubuntu Studio seems to have unincluded most of the usable command line text editors (along with open office) so with my (very limited) terminal skills I was unable to find anything I could use to edit xorg.conf

Can Ubuntu do a little bit of work on the hardware detection side of things to identify the "legacy" ATI cards & stop the installation of bad drivers?

Also, seeing as ATI have now completely dropped these old cards how about they release the full interface specs so the open source community can use them to improve the free drivers.  Note that I'm not asking them to open-source the driver code which they may not want to do (though it would be nice... - you could open-source the last version of the driver BEFORE the new generation was introduced & we'd be streets ahead - how about it?).  Just give us SOMETHING!!!

---

### Post by swinky on 2009-05-07
Are you running Jaunty? If you are I'd recommend using the open source ati drivers anyways. It seems to me that the ones that come with Jaunty have improved a lot over the ones that came with Intrepid. And since ATI has dropped support for "legacy" cards (which is sad seeing as how I bought my x1950 a mere 18 months ago), there isn't going to be any improvement in the proprietary drivers, even though they still had a lot of room left for improvement. 

The only reason I could imagine needing the proprietary drivers is if you are really needing a lot of extra video performance. I'm running the open source driver and running compiz just fine, video playback is great, and I've had very little in the way of issues with them. That's just my two cents.

---

### Post by Duskao on 2009-05-07
I am going to recomment EnvyNG. It will detect your video card then install the best driver known to work with your Distro Version. At least in Ubuntu anyway.

---

### Post by porchrat on 2009-05-07
> **servicetech said:**
> I tried it, no go. Since I haven't added much to this fresh install I just reformatted and started over. It's sad that making a driver install error brings ubuntu to it's knees.

It isn't sad. Chances are you have installed the wrong driver. That would bring any OS to it's knees. Next time check that the driver you're installing is actually built for the OS you are installing it on.

I did the same thing with the ATI legacy drivers. ATI is not supporting any Linux distro released after February 2009 with their legacy drivers.

---

### Post by swinky on 2009-05-07
I had similar issues some weeks back removing fglrx and going back to the open source ati driver. I fixed it in the end, but due to finals and everything, I spaced *exactly* how it was I fixed it.

I've been sniffing around and now I am 90% sure that I fixed my issues by following the instructions [here]("https://wiki.edubuntu.org/X/Troubleshooting/FglrxInteferesWithRadeonDriver"). Hope it helps!

---

