---
title: "Chrome does not have flash (64 bit)"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by phour10n3 on 2011-05-26
Running Ubuntu 11.04 64 bit with Chrome 11.0.696.68 (64 bit). Any time I go to any website that requires flash I am directed to download Flash 10.

On Adobe's website they say that Chrome must simply have flash disabled, and to check under about: plugins. However on this page I don't have flash showing up. 

I've tried searching for the problem, and it seems like some other people might have had similar experiences, but I haven't been able to solve it. I tried installing flash control for chrome, but it changes nothing. I also tried uninstalling firefox and trying again in chrome, but nothing.

---

### Post by wildmanne39 on 2011-05-26
> **phour10n3 said:**
> Running Ubuntu 11.04 64 bit with Chrome 11.0.696.68 (64 bit). Any time I go to any website that requires flash I am directed to download Flash 10.

On Adobe's website they say that Chrome must simply have flash disabled, and to check under about: plugins. However on this page I don't have flash showing up. 

I've tried searching for the problem, and it seems like some other people might have had similar experiences, but I haven't been able to solve it. I tried installing flash control for chrome, but it changes nothing. I also tried uninstalling firefox and trying again in chrome, but nothing.
Hi, why would you unintstall firefox when you are having a problem with chrome? My understanding is that chrome comes with its on flash so keep looking for a way to turn it on, I do not have chrome installed or I would look for you.

---

### Post by mikewhatever on 2011-05-26
Have you installed Adobe Flash, either from the repositories (32bit) or from [labs.adobe.com]("http://labs.adobe.com/technologies/flashplayer10/square/")?

---

### Post by phour10n3 on 2011-05-26
> **mikewhatever said:**
> Have you installed Adobe Flash, either from the repositories (32bit) or from [labs.adobe.com]("http://labs.adobe.com/technologies/flashplayer10/square/")?

Adobe's site said that Chrome should already have flash and should update it automatically. Im not sure if this is different for the 64 bit version, but I did not install square because it said that it should only be used for developers/testing. I was hoping for a more stable version, but I will try installing that now.

---

### Post by jtarin on 2011-05-26
[http://maketecheasier.com/enable-flash-support-in-google-chrome-in-ubuntu/2009/08/19/](http://maketecheasier.com/enable-flash-support-in-google-chrome-in-ubuntu/2009/08/19/)

Read comments also.......scroll down the page.

---

### Post by mikewhatever on 2011-05-26
I am sure Google would very much like to see a more stable 64bit version. May be then it will be included with the 64bit Chrome.

---

### Post by phour10n3 on 2011-05-26
Thanks guys.
My solution:

download libflashplayer.so
mkdir /opt/google/chrome/plugins
copy libflashplayer to that location

Thanks.

---

### Post by screaminj3sus on 2011-05-26
> **phour10n3 said:**
> Running Ubuntu 11.04 64 bit with Chrome 11.0.696.68 (64 bit). Any time I go to any website that requires flash I am directed to download Flash 10.

On Adobe's website they say that Chrome must simply have flash disabled, and to check under about: plugins. However on this page I don't have flash showing up. 

I've tried searching for the problem, and it seems like some other people might have had similar experiences, but I haven't been able to solve it. I tried installing flash control for chrome, but it changes nothing. I also tried uninstalling firefox and trying again in chrome, but nothing.

Only the 32 bit version of chrome includes flash afaik. Chrome 64 bit will pick up whatever flash plugin firefox has installed though.

---

### Post by jtarin on 2011-05-26
> **phour10n3 said:**
> Thanks guys.
My solution:

download libflashplayer.so
mkdir /opt/google/chrome/plugins
copy libflashplayer to that location

Thanks.Cool! Sounds remotely like my suggested solution....complete w/pictures. This is the way I have always installed my plugins in Linux since the days of Mozilla.Usually I just symlink. Keeps the fluff down.

---

### Post by ThaKidChillz on 2011-05-26
Hey, could u plz check out my post on my chromium issue and lemme know if you where experiencing similar symptoms?? Thanx!

---

### Post by Fedz on 2011-05-26
> **ThaKidChillz said:**
> Hey, could u plz check out my post on my chromium issue and lemme know if you where experiencing similar symptoms?? Thanx!
For continuity: **_[[xubuntu] Chromium Plug-in Problem](http://ubuntuforums.org/showthread.php?t=1767746)**_.

---

