---
title: "Want to install ati driver"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by request_another on 2010-05-10
Ok so im a noob at linux and ubuntu. I've toyed around with linux mint and ubuntu in virtualbox and now have it running using wubi.

So i want to install the ati driver. The propietary driver is no good for me, i tried it and it seems to cause some stuttering when maximizing and minimizing windows etc. The funny thing is that as it is right now with no extra drivers installed, i can run all setting smoothly (barring one or two settings in compiz).

So i want to ask, can i install this driver:

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.25&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.25&lang=English)

Also if u look at the end of the page, there seem to be some requirements. I have no idea what they mean so can i go ahead and install the driver anyway? if not this driver then can someone link me to one i should download?

Some important info about my setup. Im running the latest ubuntu 10.04 64 bit. On a sony vaio fw if thats important with mobility hd 3470.

---

### Post by julio_cortez on 2010-05-11
> **wankingweiner said:**
> The propietary driver is no good for me, i tried it and it seems to cause some stuttering when maximizing and minimizing windows etc.
[QUOTE=ATI site]ATI Catalyst&#8482; 10.3 _**Proprietary**_ Linux x86 Display Driver[/QUOTE]
The one you linked IS the proprietary driver.
Chances are that it is the same one that caused stuttering.

By the way, even doing a
```
sudo apt-get install fglrx
```would result in you installing the proprietary driver I guess.
*I may be wrong though, I'm still nothing more than a noob in Linux systems* :D

If you're looking for some open drivers for ATI cards, this might be an interesting read:
[http://ubuntuforums.org/showthread.php?t=1238129&highlight=ati](http://ubuntuforums.org/showthread.php?t=1238129&highlight=ati)

I don't know which grade of development they reached as I'm still using fglrx (the same you posted) even if it causes some little trouble with compositing in KDE.

---

### Post by adam22 on 2010-05-11
The newest driver can always be found via the ATI site. The one that is built into Ubuntu is likely outdated but the most stable one (I believe).

I'm using the open source driver (if you don't select the proprietary one, you're using the OS one) and it's working almost perfectly except for the reflection effect in CCSM. The ATI driver causes slowness and a funky splash screen.

I'm using a Radeon 3200 HD "card" by the way.

---

### Post by 3rdalbum on 2010-05-11
> **adam22 said:**
> The newest driver can always be found via the ATI site. The one that is built into Ubuntu is likely outdated but the most stable one (I believe).

In Ubuntu 10.04 it should still pretty much be the newest driver.

---

### Post by shebaw on 2010-05-11
The proprietary driver causes shuttering on my PC too, the open source driver included in Ubuntu 10.04 does pretty much everything for me, it's way better than the proprietary driver.

---

### Post by request_another on 2010-05-11
hmm so maybe i should stay with the one installed? It seems to be working good. Is there any way to check which driver version i have installed?

---

### Post by adam22 on 2010-05-11
> **3rdalbum said:**
> In Ubuntu 10.04 it should still pretty much be the newest driver.

For now. I've rarely had any kind of success with ATI drivers though. In 9.10 the ATI driver provided was adequate, but downloading a newer driver in Open SuSE resulted in an unusable system, and the ones provided in Kubuntu and Ubuntu 10.04 both screwed things up. Seems like the newer the drivers are, the worse they behave!

---

### Post by request_another on 2010-05-11
I would have no problem staying with the current driver seeing as its not causing me any problems. But there seem to be a lot of settings missing from compiz. I'll post a screenshot in a second.

Could this be because im using the open source driver?

edit: 

[img]http://img9.imageshack.us/img9/6239/screenshotbyf.png[/img]

Shouldn't there be more settings than this? I remember there being more in Virtualbox. Also the Blur Windows option kills my performance. Everything becomes extremely slow. Is this normal?

---

### Post by request_another on 2010-05-12
anyone?

---

### Post by 3rdalbum on 2010-05-12
Install the "compiz-fusion-plugins-extra" package to get the extra options.

The Blur Windows option gives a noticable performance penalty. Especially on the open-source driver as the performance isn't too great to begin with.

In Blur Windows, change the blur filter to Mipmap - it's less intensive, and it looks better and is more readable with semi-transparent windows because it's more "frosted".

---

### Post by request_another on 2010-05-12
thanks for the tip, now i have the extra settings :)

But unfortunately changing the settings under blur windows doesn't give me any kind of performance boost.

---

### Post by adam22 on 2010-05-12
It's some effect, which, if anything, will result in a performance hit. I just tried to activate it with the open source driver for an ATI Radeon 3200 and it broke something.

---

### Post by request_another on 2010-05-12
yeah i think i'll just forget about the setting. Ubuntu looks nice with the regular nontransparent windows.

---

### Post by adam22 on 2010-05-12
I usually just go with the reflection and window decoration plugins.

---

### Post by request_another on 2010-05-12
switching on reflections makes the window title unreadable. Is it meant to be like that?

With reflections off :

[http://img709.imageshack.us/img709/791/screenshot1ov.png](http://img709.imageshack.us/img709/791/screenshot1ov.png)

With reflection on: 

[http://img193.imageshack.us/img193/7716/screenshotlx.png](http://img193.imageshack.us/img193/7716/screenshotlx.png)

---

### Post by adam22 on 2010-05-12
No, it's not. I am experiencing the same exact issue with the open source driver for my ATI card.

---

