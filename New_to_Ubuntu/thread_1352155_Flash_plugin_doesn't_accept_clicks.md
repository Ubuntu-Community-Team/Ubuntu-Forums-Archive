---
title: "Flash plugin doesn't accept clicks"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by tom66 on 2009-12-11
I cannot click any button on any flash plugin. This includes YouTube and other sites; I cannot pause the videos or change the volume. However they still have hover effects and will accept keyboard input such as play/pause by space bar. Is this a known bug? Happens in Firefox and Chrome.

---

### Post by philinux on 2009-12-11
> **tom66 said:**
> I cannot click any button on any flash plugin. This includes YouTube and other sites; I cannot pause the videos or change the volume. However they still have hover effects and will accept keyboard input such as play/pause by space bar. Is this a known bug? Happens in Firefox and Chrome.

Which version of flash is it. Look in FF tools>addons>plugins.

Is this 32 or 64 bit os?

---

### Post by CaptainMark on 2009-12-11
I had this a few days ago, seemed a temporary bug though run sudo apt-get update && apt-get upgrade to make sure you have latest flash installed,

---

### Post by tom66 on 2009-12-11
64-bit, Flash 10.0r32.

I will do an upgrade and report back. Thanks everyone.

---

### Post by bailout on 2009-12-11
It sounds like a known bug. [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407?comments=all](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407?comments=all)

You can try the workrounds in the bug report but if you hold down shift or ctrl when clicking it may work.

---

### Post by Temposs on 2009-12-11
When I did workaround #3 listed in the bug report, it worked very well.

---

### Post by tom66 on 2009-12-11
Not fixed after upgrade... now running Flash 10.0r42.

Will check out bug report.

Strange thing is, sometimes apps will accept clicks, but only 1 in 100 times or something like that.

---

### Post by Temposs on 2009-12-11
Yes, this bug occurs when running the flash plugin in the Ubuntu repos on 64-bit Ubuntu. Even when running 64-bit Ubuntu, you still get the 32-bit version of flash, and also there's this app called npviewer that wraps the flash plugin so that it works on a 64-bit system. And I think it's the npviewer app that causes this bug.

---

### Post by Temposs on 2009-12-11
And as I said before, the workaround #3 seems to fix the problem perfectly, and I think it's the workaround that's most non-intrusive to your Ubuntu install.

---

### Post by philinux on 2009-12-12
> **tom66 said:**
> Not fixed after upgrade... now running Flash 10.0r42.

Will check out bug report.

Strange thing is, sometimes apps will accept clicks, but only 1 in 100 times or something like that.

Seeing as you are using 64 bit you would be better of ditching the 32 bit plugin. So use synaptic and remove flashplugin-installer and flashplugin-nonfree if installed.

Then get the 64 bit plugin from adobe.
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz)

Right click the tar file and choose extract here to extract libflashplayer.so 

Then Places>home ctrl h to show hidden files and navigate to your .mozilla folder. Create a folder called plugins. Then copy or move libflashplayer.so to the plugins folder.

Restart firefox.

---

### Post by tom66 on 2009-12-12
> **philinux said:**
> Seeing as you are using 64 bit you would be better of ditching the 32 bit plugin. So use synaptic and remove flashplugin-installer and flashplugin-nonfree if installed.

Then get the 64 bit plugin from adobe.
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz)

Right click the tar file and choose extract here to extract libflashplayer.so 

Then Places>home ctrl h to show hidden files and navigate to your .mozilla folder. Create a folder called plugins. Then copy or move libflashplayer.so to the plugins folder.

Restart firefox.
Can I also do this for Chrome? Where do I put files for Chrome? (I use Chrome as my main browser.)

Thanks.

(BTW, I thought I was using 64-bit Flash, but I guess I was wrong. I installed the .deb from Adobe's site.)

---

### Post by LuisGMarine on 2009-12-12
Check this out, there is an alpha for 64-bit Linux

[http://ubuntuforums.org/showthread.php?t=1352617]("http://ubuntuforums.org/showthread.php?t=1352617")

Might work, might now work make sure to make backups =)  This plugin wads released by adobe on December 8th, 2009.

---

### Post by CLEARviewF on 2010-04-08
Workaround #3 worked for me too!
My System is Mint 8 Helena (based on Ubuntu Karmic 9.10 x64), AMD64, Compiz.

---

### Post by tmx84 on 2010-04-09
> **tom66 said:**
> Can I also do this for Chrome? Where do I put files for Chrome? (I use Chrome as my main browser.)

Thanks.

(BTW, I thought I was using 64-bit Flash, but I guess I was wrong. I installed the .deb from Adobe's site.)

Yes you can do this for Chrome as well.  Just create the folder.. /usr/lib/chromium-browser/plugins and put the same file in there.

---

### Post by ProNux on 2010-04-11
> **tom66 said:**
> I cannot click any button on any flash plugin. This includes YouTube and other sites; I cannot pause the videos or change the volume. However they still have hover effects and will accept keyboard input such as play/pause by space bar. Is this a known bug? Happens in Firefox and Chrome.

In my case, I think this is related to running 64-bit Ubuntu Karmic.  What I did was (1) Close Firefox and (2) Reinstall flashplugin-installer at Synaptic.

It worked for me.

---

### Post by Sin@Sin-Sacrifice on 2010-04-11
Workaround = Right click and hold while left clicking on flash object.

---

### Post by WinterRain on 2010-04-11
> **philinux said:**
> Seeing as you are using 64 bit you would be better of ditching the 32 bit plugin. So use synaptic and remove flashplugin-installer and flashplugin-nonfree if installed.

Then get the 64 bit plugin from adobe.
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz)

Right click the tar file and choose extract here to extract libflashplayer.so 

Then Places>home ctrl h to show hidden files and navigate to your .mozilla folder. Create a folder called plugins. Then copy or move libflashplayer.so to the plugins folder.

Restart firefox.
Just as an update to the link for the 64bit flash plugin, here's the latest one. [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz)

The above directions should work fine, but note that the libflashplayer.so file can also be put in /usr/lib64/mozilla/plugins

---

### Post by ProNux on 2010-04-23
> **ProNux said:**
> In my case, I think this is related to running 64-bit Ubuntu Karmic.  What I did was (1) Close Firefox and (2) Reinstall flashplugin-installer at Synaptic.

It worked for me.

Update on my post.  Flash is still unstable.  Gonna try tomorrow the instruction on the thread link below.

[http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

---

