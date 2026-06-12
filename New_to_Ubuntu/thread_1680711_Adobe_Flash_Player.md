---
title: "Adobe Flash Player"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by Lt. Surge on 2011-02-03
With the help of some very nice users, I have successfully installed to my Toshiba NB305.

Now, for web browsing, what do you recommend I do for Flash Player?

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
For 'Select Version to Download', which do I use? YUM, TAR, APT, etc?

And to be on the safe side, I don't need Shockwave, do I?

---

### Post by Sealbhach on 2011-02-03
To get yourself fully sorted out for your multimedia needs, I recommend you look at this how-to

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Essentially, all you have to do is copy and paste a few commands into your terminal and wait a while for all the goodies to install.

.

---

### Post by thefasterblueone on 2011-02-03
Try Flash-Aid. It has helped alot of people with flash player problems.

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/")

---

### Post by Lt. Surge on 2011-02-03
> **Sealbhach said:**
> To get yourself fully sorted out for your multimedia needs, I recommend you look at this how-to

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Essentially, all you have to do is copy and paste a few commands into your terminal and wait a while for all the goodies to install.

.

Thx again mate, after I get done with some updates I will get back to that :o

---

### Post by Ctrl-Alt-F1 on 2011-02-03
Two Methods, This:

Open software center and search for flash. Install the one called adobe flash plugin (not flashplayer 10 plugin).

Or This, Open a terminal and type:
> sudo apt-get install flashplugin-installer

Both of these methods will install the 32bit version of flash (most OS's use 32bit flash). If you're running a 64bit OS, they will download the necessary compatibility libraries and install them for you. Flash should then work automatically in 32/64bit Firefox, Chrome, etc. Flash will be automatically updated when necessary.

Some people will tell you to use the 64bit flash plugin (I've used it before). It isn't officially supported (by Adobe or Ubuntu), so I don't recommend it.

---

### Post by rajeev1204 on 2011-02-03
> **Ctrl-Alt-F1 said:**
> Two Methods, This:

Open software center and search for flash. Install the one called adobe flash plugin (not flashplayer 10 plugin).

Or This, Open a terminal and type:


Both of these methods will install the 32bit version of flash (most OS's use 32bit flash). If you're running a 64bit OS, they will download the necessary compatibility libraries and install them for you. Flash should then work automatically in 32/64bit Firefox, Chrome, etc. Flash will be automatically updated when necessary.

Some people will tell you to use the 64bit flash plugin (I've used it before). It isn't officially supported (by Adobe or Ubuntu), so I don't recommend it.

Why wouldnt adobe 'officially' support their own plugin ? 

Ubuntu does not support it because its tagged alpha release but ask any 64 bit user and he will fully recommend it.Works very well.Much better than the wrapper.

Here is the link if you using 64 bit [http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)


btw,doesnt ubuntu automatically install the flash plugin ?

---

### Post by Ctrl-Alt-F1 on 2011-02-03
I've used both and haven't had playback problems with either, except where 3rd party programs used the flash plugin but didn't support 64bit flash.

> 
Why wouldnt adobe 'officially' support their own plugin ?

You answered it in your second sentence.  It's alpha i.e. "use at your own risk"

> The following downloads provide the Flash Player "Square" installers for Linux, Mac and Windows operating systems. [COLOR="Red"]This preview release is designed for evaluation purposes only. We do not recommended that this release be used on production systems or for any mission-critical work.[/COLOR]

[COLOR="Red"]Important: Please note that if you install the Flash Player "Square" preview, you will need to keep this version up to date by manually installing updates from the Flash Player "Square" download page on Adobe Labs. You will not receive automatic update notifications for future final releases of Flash Player, and you will need to manually uninstall Flash Player "Square" before installing a final shipping version of Flash Player.[/COLOR]

---

### Post by Vaphell on 2011-02-03
it's rock solid for me and i never looked back. my 32 bit experience was less than stellar to say the least, i had problems with basic things like youtube clip navigation due to some z-depth glitches or whatever.
And it's not like the flash-aid plugin doesn't allow to easily purge everything flash related and install 32bit from scratch.

---

### Post by oldos2er on 2011-02-03
> **rajeev1204 said:**
> Ubuntu does not support it because its tagged alpha release but ask any 64 bit user and he will fully recommend it.Works very well.Much better than the wrapper.


The latest 64-bit "Square" is at release candidate stage, FWIW.

---

### Post by rajeev1204 on 2011-02-03
> **oldos2er said:**
> The latest 64-bit "Square" is at release candidate stage, FWIW.


Where ? Its a preview release .not even beta. 

[http://forums.adobe.com/thread/777366?tstart=0](http://forums.adobe.com/thread/777366?tstart=0)

---

### Post by volaer on 2011-02-17
Here's a real quick answer that solve my problem in installing this nasty update!

[http://www.brandbuildit.com/ubuntu/how-to-install-adobe-flash-player-10-on-ubuntu-64-bit-lucid-lynx/](http://www.brandbuildit.com/ubuntu/how-to-install-adobe-flash-player-10-on-ubuntu-64-bit-lucid-lynx/)

---

### Post by oldos2er on 2011-02-17
> **rajeev1204 said:**
> Where ? Its a preview release .not even beta. 

[http://forums.adobe.com/thread/777366?tstart=0](http://forums.adobe.com/thread/777366?tstart=0)

Well, I could've sworn I'd seen something on Adobe's site say it was a release candidate, but I guess I was mistaken. Thank you for pointing that out, and sorry I lost track of this thread.

---

