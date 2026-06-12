---
title: "karmic + flash: Clicking on embeded youtube movies, nothing happnes..."
date: 2009-11-01
forum: New to Ubuntu
---

### Post by occams_beard on 2009-11-01
Title says it all. When I try to click on the play button of any kind of embeded flash movie, nothing happens...

For instance, If I try to click the play button on this flash movie it just sits there like a bump on a log.

[http://hotair.com/archives/2009/10/31/paul-obama-administration-has-botched-h1n1-effort/](http://hotair.com/archives/2009/10/31/paul-obama-administration-has-botched-h1n1-effort/)

Any fox for this? Probably not, I'm guessing... but thought I'd ask just for the hell of it.

Worked in Jaunty, although it had flash problems of its own where flash would just 'go away' every now and again. So I just lived with it hoping it would be fixed in the next release. But unfortunately it looks like I have yet another flash problem to contend with... sigh....

---

### Post by lovinglinux on 2009-11-01
See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

### Post by JugglinPhil on 2009-11-01
> **lovinglinux said:**
> See **Solution** [*[COLOR=Red]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR=DarkRed]Firefox optimization and troubleshooting thread[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004").
Didn't work.. :( I did all the commands listed but the problem remains.

---

### Post by lovinglinux on 2009-11-01
> **JugglinPhil said:**
> Didn't work.. :( I did all the commands listed but the problem remains.

Do you have the same issue with other browsers?

What happens if you refresh the page?

Do you have AdBlock installed?

Do you have ipv6 enabled?

---

### Post by JugglinPhil on 2009-11-01
> **lovinglinux said:**
> Do you have the same issue with other browsers?

What happens if you refresh the page?

Do you have AdBlock installed?

Do you have ipv6 enabled?
1. I don't have any other browsers, can you recommend any just to try it?
2. Refreshing doesn't make a difference
3. No Adblock
4. Not sure bout ipv6, how do I find out?

---

### Post by potam on 2009-11-01
This is a bug, already reported in launchpad.

---

### Post by JugglinPhil on 2009-11-01
> **potam said:**
> This is a bug, already reported in launchpad.
Does this mean they are gonna fix it or is it just gonna stay like that?

---

### Post by potam on 2009-11-01
[This is the bug report]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/434050"), there are already some workarounds, try them. This must be fixed, it is a very annoying bug.

---

### Post by JugglinPhil on 2009-11-01
> **potam said:**
> __ it is a very annoying bug.
Indeed

---

### Post by potam on 2009-11-01
The problem as I understood: Currently the 64 bit flash is alpha, so Karmic uses the 32 bit version, with a wrapper.
[This workaround]("http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html#comment-151090") worked for me, it installs the beta 64 bit flash.

Updated: 64 bit flash player is alpha, thanks occams_beard for correction

---

### Post by 3rdalbum on 2009-11-01
> **potam said:**
> The problem as I understood: Currently the 64 bit flash is beta, so Karmic uses the 32 bit version, with a wrapper.
[This workaround]("http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html#comment-151090") worked for me, it installs the beta 64 bit flash.

That's certainly a problem, but the problem being described is something different. I've experienced it once and I'm using 64-bit Flash.

---

### Post by JugglinPhil on 2009-11-01
> **potam said:**
> The problem as I understood: Currently the 64 bit flash is beta, so Karmic uses the 32 bit version, with a wrapper.
[This workaround]("http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html#comment-151090") worked for me, it installs the beta 64 bit flash.
Awesome this worked, thanks a bunch.

---

### Post by JugglinPhil on 2009-11-01
Dang, actually it didn't.. It still isn't able to play embedded videos, however at least the flash controls on youtube work again.

---

### Post by potam on 2009-11-01
> **JugglinPhil said:**
> Dang, actually it didn't.. It still isn't able to play embedded videos, however at least the flash controls on youtube work again.

Embedded videos require to install mozilla-mplayer package, and a Firefox restart.

---

### Post by JugglinPhil on 2009-11-01
> **potam said:**
> Embedded videos require to install mozilla-mplayer package, and a Firefox restart.
I didn't find it in Synaptic so I installed it through the Ubuntu Software Center, but it still does not work.. Any suggestions?

---

### Post by potam on 2009-11-01
> **JugglinPhil said:**
> Any suggestions?

Could you please give me a site's url with the embedded video?

---

### Post by marcopolo1981 on 2009-11-01
@ occams_beard
If you are running 64bit Karmic, See [http://ubuntuforums.org/showthread.php?t=1259102&highlight=adobe+flash+x64](http://ubuntuforums.org/showthread.php?t=1259102&highlight=adobe+flash+x64)
This worked 100% first time for me.

For 32bit Karmic, go to [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) and download the .deb package.
I can confirm this works on my other pc also.
You may need to completely remove any flash plugins you already have before doing either of these.

---

### Post by JugglinPhil on 2009-11-01
> **potam said:**
> Could you please give me a site's url with the embedded video?
Well I just tried the one from the original post: [http://hotair.com/archives/2009/10/3...d-h1n1-effort/]("http://hotair.com/archives/2009/10/31/paul-obama-administration-has-botched-h1n1-effort/")

---

### Post by JugglinPhil on 2009-11-01
> **marcopolo1981 said:**
> @ occams_beard
If you are running 64bit Karmic, See [http://ubuntuforums.org/showthread.php?t=1259102&highlight=adobe+flash+x64](http://ubuntuforums.org/showthread.php?t=1259102&highlight=adobe+flash+x64)
This worked 100% first time for me.

For 32bit Karmic, go to [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) and download the .deb package.
I can confirm this works on my other pc also.
You may need to completely remove any flash plugins you already have before doing either of these.
After following this tutorial I can watch embedded vids, but now the controls have stopped working again.. What a shame

---

### Post by wobin77 on 2009-11-01
if you re on 64 bit, use this link. (fixed all for me)

[http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/](http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/)

---

### Post by potam on 2009-11-01
Before installing anything make sure that all default flash players are removed from your system: 
```

sudo apt-get remove mozilla-plugin-gnash swfdec-mozilla flashplugin-nonfree flashplugin-installer

```

---

### Post by occams_beard on 2009-11-01
I tried the work arounds that use the 64 bit flash. It does indeed fix the issue with the unclickable controls BUT it is unstable and various flash pages will crash firefox. Probably because the 64 bit flash plugin is *alpha*.* This just isn't a viable solution.

The only thing that works is to disable compiz. What a mess.

---

### Post by thedeparted on 2009-11-01
> **potam said:**
> Before installing anything make sure that all default flash players are removed from your system: 
```

sudo apt-get remove mozilla-plugin-gnash swfdec-mozilla flashplugin-nonfree flashplugin-installer

```


After installing the Get64Flash, i used this code and my flash works now...;)

---

### Post by philinux on 2009-11-01
> **potam said:**
> Embedded videos require to install mozilla-mplayer package, and a Firefox restart.

Embedded videos,** not flash**, use the totem plugins by default. They work fine.

---

### Post by Spiritof76 on 2009-11-01
All these complex steps.. just install 32 bit 64 bit really isn't ready yet.   ubuntu isn't all that memory demanding and 4 gig works real well

---

### Post by philinux on 2009-11-01
> **Spiritof76 said:**
> All these complex steps.. just install 32 bit 64 bit really isn't ready yet.   ubuntu isn't all that memory demanding and 4 gig works real well

Doesn't need to be complicated. And 64 bit works just fine.
[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

Clean install.

1. get the plug in from adobe. [http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.tar.gz](http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.tar.gz)) and save to Desktop.

2. Right click the archive and choose extract here.

3. copy the file libflashplayer.so to ~/.mozilla/plugins

Simple ;) and you get a performance boost from the 64 bit plugin.

---

### Post by wobin77 on 2009-11-01
> **philinux said:**
> Doesn't need to be complicated. And 64 bit works just fine.
[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

Clean install.

1. get the plug in from adobe. [http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.tar.gz]("http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.tar.gz")) and save to Desktop.

2. Right click the archive and choose extract here.

3. copy the file libflashplayer.so to ~/.mozilla/plugins

Simple ;) and you get a performance boost from the 64 bit plugin.



like i said...!   ;-) 


No really, it works if follow those few steps.

---

### Post by philinux on 2009-11-01
> **wobin77 said:**
> like i said...!   ;-) 


No really, it works if follow those few steps.

Even that link has more words to read. ;)

Check out the benchmarks, very interesting.

---

### Post by JugglinPhil on 2009-11-02
> **philinux said:**
> Doesn't need to be complicated. And 64 bit works just fine.
[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

Clean install.

1. get the plug in from adobe. [http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.tar.gz]("http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.tar.gz")) and save to Desktop.

2. Right click the archive and choose extract here.

3. copy the file libflashplayer.so to ~/.mozilla/plugins

Simple ;) and you get a performance boost from the 64 bit plugin.
Did it, now I can watch them and press pause once, but after that the controls stop working..

---

### Post by potam on 2009-11-03
Check [this link]("http://www.ubuntugeek.com/fix-for-flash-is-not-recognizing-mouse-clicks.html") too!

---

### Post by JugglinPhil on 2009-11-03
> **potam said:**
> Check [this link]("http://www.ubuntugeek.com/fix-for-flash-is-not-recognizing-mouse-clicks.html") too!
Nice looks like it is working, but I thought that a few times before. I'll report if it keeps up or not. :)

---

### Post by dwasifar on 2009-11-06
I tried the 64-bit beta from Adobe, but that was unstable and kept crashing Firefox.  So I disabled it, reinstalled flashplugin-installer, and edited the configuration as described in the first step of potam's link, like so:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Add the following line *before* the last line of text (i.e. it should be the next-to-last line):

```
export GDK_NATIVE_WINDOWS=1
```

Save and exit the file.

This worked for me.  Embedded flash videos now behave normally, and Firefox doesn't crash from them.  

That link warns that next time you update you'll have to reverse the changes, so remember what you did.

---

### Post by coolen on 2009-11-08
> **potam said:**
> Check [this link]("http://www.ubuntugeek.com/fix-for-flash-is-not-recognizing-mouse-clicks.html") too!

That worked for Firefox. I don't suppose anyone knows of a way to get Chrome to use that?

---

### Post by potam on 2009-12-11
Another **alpha** version of 64 bit flash player is available, released on 8th of December. Check [this link]("http://humphreybc.wordpress.com/2009/12/09/install-the-new-64-bit-flash-in-ubuntu/") for installation instructions.

---

