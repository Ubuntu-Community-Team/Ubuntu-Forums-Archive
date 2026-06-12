---
title: "Question of Chrome"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by fleamour on 2009-12-13
Will Ubuntu ever adopt Chrome as browser of choice?  It is much faster then FF by all accounts, though I suppose add-ons are limited.  I read that Chrome has now been ported to Linux, will it ever be available in repositories?

---

### Post by mkvnmtr on 2009-12-13
It is very simple to enable the repository for Chromium which is Chrome. As for the browser of choice for Ubuntu the choice is yours. You might try Opera or Midori they seem to be just as fast-

---

### Post by ikt on 2009-12-13
> **fleamour said:**
> Will Ubuntu ever adopt Chrome as browser of choice?  It is much faster then FF by all accounts, though I suppose add-ons are limited.  I read that Chrome has now been ported to Linux, will it ever be available in repositories?

You can download the .deb from here:

[http://www.google.com/chrome](http://www.google.com/chrome)

---

### Post by fleamour on 2009-12-13
Thanks!

---

### Post by Tahakki on 2009-12-13
I've been using it for a while now, and while it's brilliantly fast, it's still not perfectly integrated with GTK (that's your themes etc.) - highlighting stuff is still blue even though I'm on a green theme. Otherwise it seems okay.

---

### Post by Zzl1xndd on 2009-12-13
As others have already stated it is easy to install Chrome. 

However as for your original question it would be possible, from my understanding there are some Ubuntu developers helping with Chrome OS. So there is a foundation of Canonical and Google working together.

---

### Post by 3rdalbum on 2009-12-13
The Chrome window doesn't have drop shadows, and the highlight colour is wrong. Also, the Chrome window uses RGBA to get rounded corners - but Google didn't bother setting the RGBA so we could have a semitransparent window?! Didn't anyone actually think about the eye candy?

I'm impressed with the speed of Javascript execution - it does definitely seem snappy. If Chrome reaches the amount of marketshare that Firefox has, I'm sure the Ubuntu developers will consider a switch.

---

### Post by ubulette on 2009-12-13
> **fleamour said:**
> Will Ubuntu ever adopt Chrome as browser of choice?  It is much faster then FF by all accounts, though I suppose add-ons are limited.  I read that Chrome has now been ported to Linux, will it ever be available in repositories?

Chrome, never. Chromium, maybe one day. We have Chromium in a PPA for about a year and now the beta too:

[http://castrojo.wordpress.com/2009/12/11/chromium-builds-tracking-the-chrome-beta-channel/](http://castrojo.wordpress.com/2009/12/11/chromium-builds-tracking-the-chrome-beta-channel/)

---

### Post by fleamour on 2009-12-14
Are they not the same thing?

I've installed Chrome, where will I find the Chrome icon for the quick launcher I just created?

Blazingly fast though!  Have made it default.

---

### Post by fleamour on 2009-12-15
Using Catfish:

usr/local/share/icons/hicolor

Then choose from:

16x16 up to 256x256.

Class!

---

### Post by northern lights on 2009-12-15
> **fleamour said:**
> Are they not the same thing?
Chromium is the open source project behind Chrome.
Chrome is a essentially a product name, chromium the project.

Now as for why ubulette refused to ever adopt chrome:
[QUOTE=Google Chrome's EULA]“By submitting, posting or displaying the content you give Google a perpetual, irrevocable, worldwide, royalty-free, and non-exclusive license to reproduce, adapt, modify, translate, publish, publicly perform, publicly display and distribute any content which you submit, post or display on or through, the services. This license is for the sole purpose of enabling Google to display, distribute and promote the services and may be revoked for certain services as defined in the additional terms of those services.”[/QUOTE]

Makes a difference, doesn't it?

---

### Post by fleamour on 2009-12-15
Certainly does!

---

### Post by mkvnmtr on 2009-12-15
I believe that anyone that thinks they will like Chrome as a web browser should at least try Midori. Seems to do everything just as fast.

---

### Post by howefield on 2009-12-15
> **northern lights said:**
> Originally Posted by Google Chrome's EULA
“By submitting, posting or displaying the content you give Google a perpetual, irrevocable, worldwide, royalty-free, and non-exclusive license to reproduce, adapt, modify, translate, publish, publicly perform, publicly display and distribute any content which you submit, post or display on or through, the services. This license is for the sole purpose of enabling Google to display, distribute and promote the services and may be revoked for certain services as defined in the additional terms of those services.”

Perhaps you could point me to where this is stated in the Chrome terms of service ?

I don't see it.

---

### Post by Grenage on 2009-12-15
It's probably not there now:

[http://arstechnica.com/tech-policy/news/2008/09/google-on-chrome-eula-controversy-our-bad-well-change-it.ars](http://arstechnica.com/tech-policy/news/2008/09/google-on-chrome-eula-controversy-our-bad-well-change-it.ars)

---

### Post by howefield on 2009-12-15
> **Grenage said:**
> It's probably not there now:

Correct.

---

### Post by fleamour on 2009-12-15
This assumes you have installed Chrome.

A little guide for any beginners, convert your Firefox quick launcher to Chrome by right clicking & changing properties.

Name:  Google Chrome
Description:  Access the Internet
Icon:  usr/local/share/icons/hicolor (choose the 16x16.)
Command: '/opt/google/chrome/google-chrome'

Leave all other settings alone.

---

