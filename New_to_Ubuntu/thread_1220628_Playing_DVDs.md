---
title: "Playing DVDs"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by jose187 on 2009-07-23
I've had to install 8.10 on a new computer, and i got everything to work including the cursed ATI graphic card.

But now i can't play DVDs.

I have installed the Restricted codecs, and i followed evry bit of instruction, even dow nloading Totem-Xine.

I still get a "libdvdcss" not installed.

I have an AMD64...any help?

---

### Post by oOarthurOo on 2009-07-23
I think the site is called medibuntu. It has instructions for adding the repo and installing the needed codecs.

---

### Post by mthalis on 2009-07-23
Try this
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by laffinet on 2009-07-23
These two commands got me going

```
sudo apt-get install totem-xine libxine1-ffmpeg libdvdread3

```
```

sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by mapes12 on 2009-07-23
Here's a very comprehensive Ubu media HowTo: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by RyanVanDiemen on 2009-07-23
best thing to do is install ubuntu-restricted-extras right after installation. it will add all files necessary to play divx, dvd, mp3 etc... before that you need to add medibuntu repository of course as described above

---

### Post by jose187 on 2009-07-23
> **laffinet said:**
> These two commands got me going

```
sudo apt-get install totem-xine libxine1-ffmpeg libdvdread3

```
```

sudo /usr/share/doc/libdvdread3/install-css.sh
```

Done all this...problem persists

> Here's a very comprehensive Ubu media HowTo: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Did everything it asked me to - reboot - problem persists.

> best thing to do is install ubuntu-restricted-extras right after installation. it will add all files necessary to play divx, dvd, mp3 etc... before that you need to add medibuntu repository of course as described above

First thing i did. I can view flash and other videos....just NOT DVDs or VCDs! ](*,):cry:

---

### Post by Paddy Landau on 2009-07-23
> **jose187 said:**
> "libdvdcss" not installed.
I don't know whether this will help...
```
sudo apt-get install libdvdcss2
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by shifty_powers on 2009-07-23
have you got vlc installed?

---

### Post by sendacow on 2009-07-23
Thanks for all the information and advice, I had the same problem
K.

---

### Post by Riaku on 2009-07-23
Whay not just try jaunty?

---

### Post by philinux on 2009-07-23
> **Riaku said:**
> Whay not just try jaunty?

Still have to do the medibuntu and retricted extras dance. :D

---

### Post by Riaku on 2009-07-23
true, but I did the sudo tome-xine libdvdcss read etcetc.. and it worked in jaunty

---

### Post by Garrovick on 2009-07-23
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Grenage on 2009-07-23
Also worth looking at mplayer; it's a good DVD/media player.

---

### Post by mapes12 on 2009-07-23
> **jose187 said:**
> I've had to install 8.10 on a new computer, and i got everything to work including the cursed ATI graphic card.

But now i can't play DVDs.

I have installed the Restricted codecs, and i followed evry bit of instruction, even dow nloading Totem-Xine.

I still get a "libdvdcss" not installed.

I have an AMD64...any help?
Could you play DVD's on this machine before installing 8.10 or did the ATI card fix mess up DVD playback?
Have you tried DVD's with the latest LTS version i.e. 8.04 with all updates?:-k

---

### Post by oOarthurOo on 2009-07-23
Ubuntu restricted extras will not enable DVD playback. 

I'm afraid all you've told us is "did this, didn't work". Can you post the output of this command:

```
cat /etc/apt/sources.list
```

---

### Post by jose187 on 2009-07-24
I made it work but it's far from an ideal solution.

I installed Ubuntu 8.10 AMD64 because 9.04 does not yet support my ATI card. Also, it was a dual boot install, with Vista next to it.

After hours of non-stop frustration and non-stop googling, I decided to re-install everything and getting rid of Vista - this time using the 32Bit version even though I have a 64 Anthlon.

Once installed, followed the instructions from the Medibuntu website and everything went smooth. This is when i realized that the DVD drive was not multiregion.

Like I said, everithing works now but because its a 32Bit, the splashscreen doesn't work (just goes black), and some programs run a bit funny...but run nonetheless.

I think the success of the 32bit was due to the fact that it was a fresh install without dual boot, and that's why I'm thinking of trying the AMD64 again. 

But why fix it if aint broken...

---

