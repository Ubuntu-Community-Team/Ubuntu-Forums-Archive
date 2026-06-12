---
title: "Newbie- package recomendations"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by Langfan on 2009-09-02
I have just instaled linux for the first time. I am very new, never used it before. can anyone recommend what i should do package wise and settings wise to have a good set up. i don't want to just install just anything. 

What software will give me the best performance? example I use youtube but i need flash on this, where does that come from? ubuntu?.  thanks for any help you can give.

---

### Post by yabbadabbadont on 2009-09-02
I would start by reading through the information provided here:

[https://help.ubuntu.com/9.04/index.html](https://help.ubuntu.com/9.04/index.html)

It can probably answer most of your basic questions.  Then if you have any issues, please post back here with them and someone will try to help.

(Your flash question is answered in the Video section of that guide.  :D)

---

### Post by Anxious Nut on 2009-09-02
to install flash download and install this package[ http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb)]("http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb)")

and please tell us what programs you need to give you the equivalents, and about wine please tell us the programs you want to run

---

### Post by 3rdalbum on 2009-09-02
> **Langfan said:**
> I have just instaled linux for the first time. I am very new, never used it before. can anyone recommend what i should do package wise and settings wise to have a good set up. i don't want to just install just anything. 

What software will give me the best performance? example I use youtube but i need flash on this, where does that come from? ubuntu?.  thanks for any help you can give.

If you're on 32-bit, install the "flashplugin-nonfree" package. If you're on 64-bit, install the alpha 64-bit Flash Player from the Adobe website (copy the plugin into /usr/lib/mozilla/plugins, remember you need to copy it over as root because it's outside your home directory).

Well, it's all really up to you what you install. Most people start with adding the Medibuntu repository ([www.medibuntu.org](www.medibuntu.org)) and installing the "non-free-codecs" package, libdvdcss2, Skype and Google Earth from there. A lot of people install the "ubuntu-restricted-extras" package which will get Java, Flash Player, Windows fonts, MIDI synth etc from the repository (if you're on 64-bit, make sure you remove the flash plugin and "nspluginwrapper").

Other than that, install what you like, play around, have fun. If you decide later that you don't want something, you can remove it just as easily.

---

### Post by scorp123 on 2009-09-02
> **3rdalbum said:**
> If you're on 64-bit, install the alpha 64-bit Flash Player from the Adobe website And what's wrong with ```
sudo apt-get install ubuntu-restricted-extras
``` ???

Why do you recommend downloading stuff manually (and outside of the package manager's control) when Flash will work tip top when you get it from the repos?

---

### Post by dearingj on 2009-09-03
I'd suggest installing [Ubuntu Tweak]("http://ubuntu-tweak.com/"). It's a very useful utility for configuring Ubuntu.

---

### Post by oldos2er on 2009-09-03
> **scorp123 said:**
> And what's wrong with ```
sudo apt-get install ubuntu-restricted-extras
``` ???

Why do you recommend downloading stuff manually (and outside of the package manager's control) when Flash will work tip top when you get it from the repos?

 The repository Flash is 32-bit, with ndiswrapper. 64-bit Flash is still alpha software, and can only be had from Adobe's site. There's a deb package here: [https://launchpad.net/~dinxter/+archive/test](https://launchpad.net/~dinxter/+archive/test)

---

### Post by running_rabbit07 on 2009-09-03
> **scorp123 said:**
> And what's wrong with ```
sudo apt-get install ubuntu-restricted-extras
``` ???

Why do you recommend downloading stuff manually (and outside of the package manager's control) when Flash will work tip top when you get it from the repos?

+1 

I must add that I hadn't seen this package until today. I have always went straight to myspace.com and got the flash player.

---

### Post by anujpathania on 2009-09-03
Probably the most important packages for me when I do a fresh install or update my Ubuntu are -

1. MP3 & other Codec Pack (GStream)
2. Flash (Adobe One)
3. VLC Player
4. CCSM (Compiz)

Rest the pre-installed software do a great job (firefox, pidgin) and more.

---

### Post by jrox717 on 2009-09-03
Don't be afraid of trying new packages! One of my favorite things about Ubuntu is the package management system (thanks Debian!). Just install and, if you don't like it, "completely remove" it in Synaptic (apt-get purge package in the terminal), as this will get rid of all your configuration folders for the app.

---

### Post by theozzlives on 2009-09-03
If you have a network with Windows Boxes on it, you want to install samba. On a fresh install, I install startup-manager, gparted, ubuntu-restricted-extras, and the Medibuntu repositories.

---

### Post by kansasnoob on 2009-09-03
Well, this is good:

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04](http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04)

But we all develop our own favorites!

---

### Post by 3rdalbum on 2009-09-03
> **scorp123 said:**
> And what's wrong with ```
sudo apt-get install ubuntu-restricted-extras
``` ???

Why do you recommend downloading stuff manually (and outside of the package manager's control) when Flash will work tip top when you get it from the repos?

On 64-bit Ubuntu, the native 64-bit plugin works better than the 32-bit version from the repositories.

---

### Post by scorp123 on 2009-09-03
> **oldos2er said:**
> The repository Flash is 32-bit, with ndiswrapper.  You seem to confuse a few things here.

***NDIS*** stands for ***"Network Driver Interface Specification"*** and is something you will encounter when you use _network drivers_ on Windows, especially _WiFi_ cards. So ***"ndiswrapper"*** is a package that allows you to run Windows _WiFi drivers_ on a Linux kernel.

I fail to see what this supposedly should have to do with ***Adobe Flash*** which is a browser plugin and has nothing whatsoever to do with any WiFi chipset drivers??

Don't believe me? I have a 64-bit machine:
```
> uname -a
Linux phalanx 2.6.28-15-generic #51-Ubuntu SMP Mon Aug 31 13:39:06 UTC 2009 **[COLOR="Red"]x86_64[/COLOR]** GNU/Linux
```

Flash is installed:
```
> dpkg -l flash* | grep ii
ii  flashplugin-installer  10.0.32.18ubuntu0.9.04.1  Adobe Flash Player plugin installer
ii  flashplugin-nonfree    10.0.32.18ubuntu0.9.04.1  Adobe Flash Player plugin installer (transitional package)

```

"ndiswrapper" definitely is NOT installed (output shortened):
```
> dpkg -l ndis*
un  ndiswrapper-modules-1.9
```

And as for your "32-bit" theory:
```
> apt-cache show flashplugin-installer | grep Filename
Filename: pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.0.32.18ubuntu0.9.04.1_[COLOR="Red"]**amd64**[/COLOR].deb
```  That filename strongly suggests it's the right file for my architecture? So 32-bit or not: It just works. That's the important thing here.

> **oldos2er said:**
>  64-bit Flash is still alpha software, and can only be had from Adobe's site.  You said it yourself: this stuff is "alpha" software, so it's probably unstable as hell. And why should Flash even be in 64-bit? I have yet to see a Flash movie that really needs more than 4 GB of memory? :D

Don't get me wrong please. I just don't see any advantages for "Joe Average User" getting buggy "alpha" quality software from a web site if he could easily install this stuff via the package manager (because that's what we have it for). And the stuff you get from the repository works tip top, no matter if you're using 32-bit Ubuntu or the 64-bit one. It just works. No downloading, no hassle, no manual hunting for files and what not.

---

### Post by scorp123 on 2009-09-03
> **3rdalbum said:**
> On 64-bit Ubuntu, the native 64-bit plugin works better than the 32-bit version from the repositories. Even though the software is supposedly "alpha"?

---

### Post by oldos2er on 2009-09-03
Apologies for "ndiswrapper". I meant to say nspluginwrapper, which shows as a dependency of the package flashplugin-installer (I'm running 9.04).

 "You said it yourself: this stuff is "alpha" software, so it's probably unstable as hell."

 Normally I would never recommend alpha software, however, in this case I think it's justified. The 64-bit flash works better for me than the 32-bit version did.

---

### Post by sourav123 on 2009-09-03
> **Langfan said:**
> I have just instaled linux for the first time. I am very new, never used it before. can anyone recommend what i should do package wise and settings wise to have a good set up. i don't want to just install just anything. 

What software will give me the best performance? example I use youtube but i need flash on this, where does that come from? ubuntu?.  thanks for any help you can give.

Based on your post above, I assume you are new to not only Ubuntu but Linux as well. If so, please visit the below link:
[http://www.ubuntupocketguide.com/index_main.html]("http://www.ubuntupocketguide.com/index_main.html")
Here you can download a getting started guide for free (legally). Also, try googling around for similar resources.

Regarding your queries on packages, I think it would be good to stick to the default packages in Ubuntu for some time until you get used to Linux. Also, in Ubuntu, most of the media components (like mp3/dvd playback/flash) are installed on demand. So, to install flash, go to any website that requires flash and firefox will pop up a dialog box where you can select to install the flash plugin.

Note that at present there are 3 flash plugins available: Adobe Offcial, SWFDec and GNash. Which one you want to install is upto you although the official version will be the best and stable one. Although I prefer to stay with non proprietary plugin and use SWFDec.

Post any other help you need and most of us will be happy to help you out.

---

### Post by scorp123 on 2009-09-03
> **oldos2er said:**
> Normally I would never recommend alpha software, however, in this case I think it's justified. The 64-bit flash works better for me than the 32-bit version did. Ooookaay ... maybe it's worth to give it a shot then, "alpha" or not.

---

### Post by sloggerkhan on 2009-09-03
Try Inkscape.
Really what software to get depends on what you want to do...

---

### Post by oldos2er on 2009-09-03
> **scorp123 said:**
> Ooookaay ... maybe it's worth to give it a shot then, "alpha" or not.

 Wouldn't hurt to try. Since the end-of-July update, I can run flash full-screen--something I never could get to work before.

---

### Post by Sealbhach on 2009-09-03
Check out games as well, there's some good ones, most are free to download:

[https://help.ubuntu.com/community/Games](https://help.ubuntu.com/community/Games)

.

---

### Post by Langfan on 2009-09-03
Thankyou all very much, you have given me great information. you all are very nice and helpfull. i will take it all to mind and learn it all. and if i have a question about a program can i ask it here?.

---

### Post by Langfan on 2009-09-03
Wow! great information thanks a lot! great starting place.

---

