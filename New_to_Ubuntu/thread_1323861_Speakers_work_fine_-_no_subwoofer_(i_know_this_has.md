---
title: "Speakers work fine - no subwoofer (i know this has been asked already)"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by SpatzST on 2009-11-12
I attempted to find a solution to this problem myself but when I realized i've only been using Linux for less than 1 hour, the explanations on how to fix my problem were confusing. :)

Anyhow, i have an HP DV7 laptop with speakers and a subwoofer built in.  I know absolutely nothing about Ubuntu, but am running the latest version 8.10 is it?  well i know a LITTLE bit about Ubuntu, my friend gave me a crash course but it was limited.

please let me know what information you need me to post, and how to get this information.

Just to clarify, the speakers work fine, there is no subwoofer though, and yes I know the subwoofer works (in Vista).

thanks for your help :)
-Chris

---

### Post by ubhi on 2009-11-12
hi, first of all 9.10 is the latest distro.. & check sound preferences then sound setting -- in system preferences then select sound.. do test for all..

---

### Post by SpatzST on 2009-11-12
no problems with the audio.. it comes out... theres just no subwoofer.  i know this because my music sounds bass'less where it does not on my Vista install

i ran the tests.

---

### Post by SpatzST on 2009-11-12
bump?

---

### Post by SpatzST on 2009-11-14
double bump!

anything?

---

### Post by bradleypariah on 2009-12-05
triple bump.  I've been fighting this for months.
I too am on 9.10.
Dell Inspiron, Quad-core Intel 2.4 GHz, 4 GBR.
Creative Soundblaster X-Fi 5.1 card

---

### Post by bradleypariah on 2009-12-05
p.s. - I typed 

```
speaker-test -Dplug:surround51 -c6 -l1 -twav
```

and I only heard audio from left, right, left surround, and right surround, which are stereo jacks 1 and 2, or outputs 0, 1, 2, and 3 internally.

So, the Center and LFE are both on the 3rd mini-jack, outputs 4 & 5.

I know the outputs work correctly - I'm still (sadly) running a closed-source OS as well... but "it just works" in that one.  Grrrrr.  :mad:

---

### Post by whitethorn on 2009-12-05
Sounds like the same problem I have.  In order to get my Sub to work with pulse audio.  I had to do the following.

```
sudo nano /etc/pulse/daemon.conf
```
In the file remove the ; before the following lines and change it to.

> 
enable-lfe-remixing = yes
...
default-sample-rate = 48000 (optional*)
default-sample-channels = 6


*make sure you remove the (optional) if you want to use the line.  

Then you need to restart pulse, the easiest way is to reboot your pc.  Then you should be able to use your sub.

I hope this solves your problem.

---

### Post by bradleypariah on 2009-12-05
I appreciate your time good sir, but I'm afraid that had no effect.
I even DL'd the tar.gz file from Creative and tried to compile it.  No luck.  :-(
```

root@linux-gamer:/home/bradley/Desktop# ls
XFiDrv_Linux_Public_US_1.00  XFiDrv_Linux_Public_US_1.00.tar.gz

root@linux-gamer:/home/bradley/Desktop# cd XFiDrv_Linux_Public_US_1.00

root@linux-gamer:/home/bradley/Desktop/XFiDrv_Linux_Public_US_1.00# make
make -C /lib/modules/2.6.31-14-generic/build M=/home/bradley/Desktop/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  LD      /home/bradley/Desktop/XFiDrv_Linux_Public_US_1.00/built-in.o
  CC [M]  /home/bradley/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o
/home/bradley/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:14:26: error: sound/driver.h: No such file or directory
/home/bradley/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c: In function &#8216;ct_card_probe&#8217;:
/home/bradley/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:55: error: implicit declaration of function &#8216;snd_card_new&#8217;
/home/bradley/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:55: warning: assignment makes pointer from integer without a cast
make[2]: *** [/home/bradley/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/home/bradley/Desktop/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [all] Error 2

```

---

### Post by whitethorn on 2009-12-06
can you send me a link to the tar.gz you used?  I'm not quite sure which x-fi card you have.

---

### Post by bradleypariah on 2009-12-06
Sure!  Thanks for taking the time.
[SIZE=1]

[/SIZE][COLOR=Black]_[Creative Sound Blaster X-Fi and X-Fi Titanium Series Linux 32-bit / 64-bit Driver Source Release]("http://support.creative.com/Downloads/welcome.aspx#")_  [/COLOR]
File Name                                         :                                         XFiDrv_Linux_Public_US_1.00.tar.gz
In case the link takes you back to the top,
I have a **Sound Blaster, PCI,** **X-Fi XtremeGamer**

P.S. - I don't know if this is pertinent information, but right before I type my password, you know that "Bongo quadruplet" that plays?   It doesn't come out right.  It sounds like a quick digital "snat" or a quick cricket chirp or something.  Quite odd.  Then, after I type my password, the African conga-beat log-on music plays fine (minus the center and sub of course).  So weird! I verified with a different OS that sound does indeed work through that output.  In ubuntu, I tried every_single_setting in the Hardware Profile with no luck.   ](*,)  

I am studying for my LPIC1 and CompTIA Linx+ Certification as we speak, but compiling is only a week-old subject for me.  Since there were no un-met dependencies during "make", I'm too much of a novice to fix it on my own at this point.  I've Googled the errors, but it didn't really turn up anything useful.

Your help is extremely appreciated.   Really.  :D

---

### Post by whitethorn on 2009-12-06
Well I'll try to do my best.  I'm not quite an expert and I don't have the same card so I can't test it.  The README doesn't really explain much.  I'm not quite sure what the problem is or why it's not compiling.  Do you have build-essentials and I think they're called kernel-sources (or kernel-headers) you probably need alsa-dev or libalsa installed.  I currently don't have access to my ubuntu installation. Then try to remake the package.

---

### Post by bradleypariah on 2009-12-07
No success.
Weird problem, isn't it?
I did end up having to install libalsa or alsa-dev... one of those, don't remember which.  I restarted the box just to be safe, tried to compile, no luck.  I tried playing around with the daemon.conf file some more, but I don't see anything in the code pertaining to me... plus some of it is a little greek.

[I]Dang it!  :cry:

[/I]I wish Jack Controller had a version where I could redirect an output to another output.  I have this funny feeling alsa really is playing these illusive audio tracks back, they're just going to the wrong place.  Maybe?  Do you know if there's a file similar to the daemon.conf file that maps channel names to specific outputs?  Or... should the second line below from the the daemon.conf file be manipulated?

```
default-sample-channels = 6
; default-channel-map = front-left,front-right
```

---

### Post by whitethorn on 2009-12-07
So I did some researching looks like if you have the newest version of ubuntu you shouldn't need to install the driver.  [http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)

You need a 2.6.31.* kernel to check what kernel you're using run
```
uname -r
```

Next check to see if your channels are unmuted. Easiest way to do that is to install gnome-alsamixer and unmute everything (except maybe the mic) and see if it works then.

```
sudo apt-get install gnome-alsamixer && gnome-alsamixer
```

Hopefully you should see center and LFE in the list just make sure you're on the right tab (gah should've checked this first). You might alsa want to go to System -> Preferences -> Sound and make sure the output is pointed to the right device. I like to see some visual results so

```
sudo apt-get install pavucontrol padevchooser pavumeter paprefs
```

After checking if everything is unmuted start playing something, then run

```
pavumeter
``` 

If everything is working you should see something similar to this.

[ATTACH]138916[/ATTACH]

---

### Post by bradleypariah on 2009-12-08
You___just____saved____the____day!!!

Woo hoo!!!  I wish I was the thread starter for this post.  From my end, this is [SOLVED]!!!

Thank you so much for everything.  The center/LFE channel WAS muted!  Why in the world would that be default???  I never would've known without installing that ALSA mixer GUI.  Haha!  Oh well.  Maybe that was supposed to be one of ubuntu's ways of encouraging customers to spend the darn $30 to get live customer support!  lol

I really should do that anyway.  I'm loving this, even the really frustrating times.  It's so rewarding!  :-D

Thanks whitethorn!  You rock!!!

:guitar:

---

### Post by whitethorn on 2009-12-08
> **bradleypariah said:**
> You___just____saved____the____day!!!

Woo hoo!!!  I wish I was the thread starter for this post.  From my end, this is [SOLVED]!!!

Thank you so much for everything.  The center/LFE channel WAS muted!  Why in the world would that be default???  I never would've known without installing that ALSA mixer GUI.  Haha!  Oh well.  Maybe that was supposed to be one of ubuntu's ways of encouraging customers to spend the darn $30 to get live customer support!  lol

I really should do that anyway.  I'm loving this, even the really frustrating times.  It's so rewarding!  :-D

Thanks whitethorn!  You rock!!!

:guitar:

Nice!!

---

### Post by tar- on 2010-04-09
You just fixed my sound as well! Thank you white:)

.. now if only i could get my front-jacks working with my headset :confused:

---

### Post by SpatzST on 2010-04-09
OP Here!

I wish i was notified earlier that this problem was solved... i no longer have ubuntu on my main laptop with the subwoofer, i now have NBR on my netbook.

darn...

:)

---

