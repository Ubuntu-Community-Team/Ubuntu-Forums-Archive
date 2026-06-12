---
title: "Black Screen for Flash in Google Chrome"
date: 2011-08-16
forum: New to Ubuntu
---

### Post by Jary316 on 2011-08-16
Hello all,

I am running Ubuntu 11.04 64 bits on an Asus N61J.

I have installed "Ubuntu restricted extras" and "Adobe Flash Plugin" in the Ubuntu software center.

Sometimes, when a flash video gets loaded, the video itself is just a black screen but sounds come on. Reloading the webpage will usually fix the issue. I am using Google Chrome 13.0.782.112 (which seems to be the latest version). My version of Flash is 10.3.183.5.

If I go into "about:plugins" for Chrome, the default built-in Flash player is enabled. This is the information I see:

```

Flash - Version: 10.3.183
Shockwave Flash 10.3 r183
Name:	Shockwave Flash
Version:	10.3 r183
Location:	/var/lib/flashplugin-installer/npwrapper.libflashplayer.so
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	FutureSplash Player	
.spl

```

I was please wondering if there was a permanent fix to solve this issue.

Thank you very much.

---

### Post by Jary316 on 2011-08-16
> **abuali said:**
> you can install Plugin from [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Are you suggesting that I disable the built-in flash and rather install a plug-in from the website please?

If I download it from Adobe, it tells me it is for Firefox, Mozilla, Seamonkey, but not for Chrome.

---

### Post by gandaran on 2011-08-16
> **Jary316 said:**
> Are you suggesting that I disable the built-in flash and rather install a plug-in from the website please?

If I download it from Adobe, it tells me it is for Firefox, Mozilla, Seamonkey, but not for Chrome.
you can disable the built-in chrome flash and set it to use the system installed flash but I don't think it will make any deference unless you are running ubuntu 64-bits then what you need is the 64-bits flash, use the [firefox flash-aid addon]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") to get 64-bits flash installed as the ubuntu packages only have 32-bits flash.
also chrome 64-bits doesn't have built-in flash only the 32-bits chrome has it.

---

### Post by Jary316 on 2011-08-16
I have Chrome 64 bits (I took "64 bit .deb (For Debian/Ubuntu)" from their website) and it seems that Flash is built-in, as stated above with "about: plugins".

I am going to try Flash-aid and see if that helps.

Thank you.

---

### Post by gandaran on 2011-08-16
> Location:	/var/lib/flashplugin-installer/npwrapper.libflashplayer.so
no, according to this flash install location it is system installed flash.

---

### Post by Jary316 on 2011-08-16
Thanks a lot gandaran. I did what you recommended, and installed the 64 bits version through Firefox using flash-aid addon.

It seems to work. I will need a little bit of time to figure out if my issue is gone though.

Thank you.

---

### Post by Jary316 on 2011-08-17
I think my problem is solved. Thank you very much gandaran.

---

