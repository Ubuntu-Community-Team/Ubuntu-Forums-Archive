---
title: "How do I achieve 1024 x 768 resolution?"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by Flyvapnet on 2009-11-17
Although I've been using Ubuntu for about four years now, I still feel like an absolute beginner when faced with a problem such as the one described below.  Hence, I've decided to post this in the Absolute Beginner Talk forum.

I'm running Ubuntu 9.10 Karmic Koala on a Compaq Presario 5WV270 with a 750 MHz AMD Duron Processor and an NVidia TNT2 Vanta LT Graphics Card with 8 MB video memory (64-bit hardware-accelerated 3D graphics, maximum non-interlaced resolution of up to 1920 x 1200 @ 75 Hz when supported by monitor).  I have replaced the original Compaq MV540 monitor with an SVA VR-17B 17-Inch TFT Flat Panel Color LCD Monitor.

Unfortunately, the new-to-me monitor will not display 1024 x 768 resolution because it's being limited by Ubuntu to a maximum of 800 x 600.  This means - amongst other annoying phenomena such as everything being huge - a number of dialog boxes run off the bottom of the display and I'm unable to click vital radio buttons, such as "Cancel" or "OK"!  I've already perused the board's offered solutions to what's obviously a reoccurring problem with Ubuntu, but they're bamboozling in their ridiculous complexity.

This ongoing failure of Ubuntu to recognize monitors and/or permit logical screen resolutions is a problem I've faced before during the past four years, but it used to be relatively easy to fix.  Apparently, it isn't any more:  Ubuntu's relevant dialog-box declarations and/or command-line assertions indicate Ubuntu is adamant in its refusal to accept 1024 x 768 resolution.  Help!  I thank you in advance for any clear and concise instructions on how to fix this silly problem.

:(

**[COLOR="DarkRed"]=^..^=[/COLOR]**

---

### Post by emigrant on 2009-11-17
hi,
hope this post would help solve your problem:
[http://ubuntuforums.org/showpost.php?p=8316537&postcount=6](http://ubuntuforums.org/showpost.php?p=8316537&postcount=6)

---

### Post by prshah on 2009-11-17
> **Flyvapnet said:**
> 

NVidia TNT2 Vanta LT Graphics Card with 8 MB video memory 
with an SVA VR-17B 17-Inch TFT Flat Panel Color LCD Monitor.

Unfortunately, the new-to-me monitor will not display 1024 x 768 resolution

i think you first need to check if you have the nvidia driver installed. You can do this by checking the /var/log/Xorg.0.log file; in a terminal (Applications-Accessories-Terminal) ```
cat /var/log/Xorg.0.log|grep -i -E driver\|autoconfigured
``` You can post back this output here if you cannot figure out which driver is being loaded.

If you find that the nvidia driver is being loaded, then you can set the correct resolution with the nvidia-settings tool```
sudo nvidia-settings
```

If you are not using the nvidia driver, I recommend you download and install the proprietary driver, I've always used the nVidia proprietary / binary drivers, downloaded direct from nVidia. You can do the same; a good starting point is [http://www.nvidia.com/object/linux_display_ia32_185.18.36.html](http://www.nvidia.com/object/linux_display_ia32_185.18.36.html) , and if this link is not suitable for your system, please click the "Download drivers" link near the bottom left of the page, and fill in suitable configuration options to be led to the correct driver.

I believe the proprietary perform better than the opensource drivers, especially in 3d / intensive graphics related matters.

There is more than just a philosophical and performance difference between the two types of drivers, however; but I can't point you to a suitable discussion.

---

### Post by Flyvapnet on 2009-11-17
Thank you, **[COLOR="DarkRed"]emigrant[/COLOR]**, for your suggestion.  The problem is, there's no line called "Modes" anywhere on that configuration page.  I tried adding it under "Monitor," but that caused a completely-unhelpful troubleshooting program to start on re-boot.  Adding those modes under "Display" on the configuration page didn't work, either.

Thank you too, **[COLOR="DarkRed"]prshah[/COLOR]**, for your guidance.  However, "cat /var/log/Xorg.0.log|grep -i -E driver\|autoconfigured" doesn't do anything apart from returning me to my prompt.  So I decided to download and install the NVidia driver located at the other end of that link you gave me; but what I end up with is a file named "NVIDIA-Linux-x86-185.18.36-pkg1.run" which asserts it's to be opened by the "Virus Scanner."  Are they kidding, or what?  In the file's "Properties" window, the "Open With" choice is the Wine program loader - but, although Wine is installed, it doesn't do anything.

See what I mean?  Nothing works!  There's no "Modes" line on a page which is apparently supposed to contain such a category, there's an NVidia driver already installed but Ubuntu refuses to display its data, then that downloaded driver-file just sits there whilst Ubuntu doesn't know how to open it.  Another thing:  Ubuntu's "Device Manager" provides no avenue whatsoever for installing/reinstalling drivers.

I'm at the end of my rope.  I've been patient with Ubuntu's esoteric geek-o-rama user-unfriendly command-line fixation for four years, but this present intransigence takes the prize. I like mazes and puzzles as much as the next guy; but this local machine is supposed to be a tool, not an occupation.

:cry:

**[COLOR="DarkRed"]=^..^=[/COLOR]**

---

### Post by ukripper on 2009-11-17
Have you tried installing Nv drivers from System-->Administration-->Hardware drivers and see if that works?

---

### Post by halitech on 2009-11-17
try following the info here: [http://ubuntuforums.org/showpost.php?p=7869601&postcount=5](http://ubuntuforums.org/showpost.php?p=7869601&postcount=5)

> Start the Synaptic Package manager and do a search for 'nvidia-71'. Select the following 3 packages for installation:

nvidia-glx-71
nvidia-71-modaliases
nvidia-71-kernel-source

Hopefully all you'll have to do now is reboot. If the driver is still not functional, go back to Hardware Drivers to see if it is listed and make sure it's selected and activated.


---

### Post by prshah on 2009-11-17
> **Flyvapnet said:**
> is a file named "NVIDIA-Linux-x86-185.18.36-pkg1.run"

See what I mean?  Nothing works!

I'm at the end of my rope.  I've been patient with Ubuntu's esoteric geek-o-rama user-unfriendly command-line fixation for four years, but this present intransigence takes the prize. 

You can run the downloaded file with the terminal (Applications-Accessories-Terminal) command ```
sudo ./NVIDIA-Linux-x86-185.18.36-pkg1.run
``` You will need to CD to the directory that contains the downloaded file. All of this is documented in the post-download page at NVidia's site. This is not a Wine executable (Windows EXE); it is a native Linux app.

NOT reading documentation and attempting to do stuff in Linux is a waste of your time and patience. The Modes line has to be added correctly; there's an [example here]("http://ubuntuforums.org/showpost.php?p=7656979&postcount=2"). Your patience would be better spent trying to find relevant documentation (it's not that hard) and understanding it.

All in all, I suggest that a better attitude towards Linux will be required if you want to continue with it. If you persist in ignoring documentation and applying half-understood fixes, you will continue to find Linux a pain in the neck. In this case, I suggest you will be better off with Windows XP, Vista, 7, Media Center or whatever else you get for $299... or whatever.

> **halitech said:**
> try following the info here: [http://ubuntuforums.org/showpost.php?p=7869601&postcount=5](http://ubuntuforums.org/showpost.php?p=7869601&postcount=5)

I think (I am not sure) that these refer to the Open Source drivers; these are supposedly not as efficient and capable as the closed source drivers. However, for the purists...

---

### Post by halitech on 2009-11-17
> **prshah said:**
> 
I think (I am not sure) that these refer to the Open Source drivers; these are supposedly not as efficient and capable as the closed source drivers. However, for the purists...

could be but for right now I was just trying to help the OP get above 800x600 resolution.

---

### Post by ST3ALTHPSYCH0 on 2009-11-17
Post #38 [here](http://ubuntuforums.org/showthread.php?t=1319491&page=4) gives a fairly easy to understand guide to editing your xorg.conf file. Post #34 gives a link to my uneducated lazy way that I got my resolution fixed. You will need an 8.04 LTS CD to implement my solution, but it does work with legacy Nvidia hardware.

---

### Post by Flyvapnet on 2009-11-17
Thanks, everyone, for your advice and assistance.  I'm going to try *all* your suggestions!

**[COLOR="DarkRed"]Prshah[/COLOR]**, I appreciate your knowledge and willingness to help; but I'm the one who's having difficulties and this is my thread.  Don't come in here and lecture me.  If I want to let off steam in my thread, I will; and if you insist on posting arrogant and/or *personally demeaning* remarks I'd just as soon you keep out.

:-x

**[COLOR="DarkRed"]=^..^=[/COLOR]**

---

### Post by arnab_das on 2009-11-17
well you could try this method. works perfectly and best of all you get the latest drivers.

[http://thoughtsndreams.wordpress.com/2009/10/23/installing-nvidia-drivers-in-ubuntu/](http://thoughtsndreams.wordpress.com/2009/10/23/installing-nvidia-drivers-in-ubuntu/)

---

### Post by prshah on 2009-11-17
> **Flyvapnet said:**
> and if you insist on posting arrogant and/or *personally demeaning* remarks

Whew, if that's the way you take my remarks, then you better report my post; click on the "report abuse" button next to the post in question.

---

