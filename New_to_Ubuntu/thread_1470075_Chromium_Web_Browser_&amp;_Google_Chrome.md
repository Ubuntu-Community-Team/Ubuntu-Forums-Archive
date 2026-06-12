---
title: "Chromium Web Browser &amp; Google Chrome"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by captgadget on 2010-05-02
After a clean install Lucid 10.4 I now have a Chromium Web Browser & a Google Chrome. It appears they are one in the same. Should I remove one of them so I don't have both of them?

---

### Post by WiReIs on 2010-05-02
Its up to yourself, no point in having two browsers really. Chromium rocks :guitar:

---

### Post by sixthwheel on 2010-05-02
> Chromium rocks
Not since this morning.:confused:

---

### Post by flyfishingphil on 2010-05-02
> **WiReIs said:**
> Its up to yourself, no point in having two browsers really. Chromium rocks :guitar:
So, I tried Chromium but, when visiting places like Pogo.com, I get the message that I need to install Java before it will work. In trying to add the icedtea thin I got this message:
dk-6-jre-lib icedtea-plugin
[sudo] password for flyfishingphil: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openjdk-6-jre is already the newest version.
openjdk-6-jre-lib is already the newest version.
openjdk-6-jre-lib set to manually installed.
E: Couldn't find package icedtea-plugin

It appears to me that the java is already in there but Chromium doesn't "see" it. Is there something I need to do to get it to "see" and "use" the java that's already plugged in?

---

### Post by Tulsapoke on 2010-05-03
I upgraded to Lucid 10.04 and now my Java in Chrome and Chromium quit working.  I haven't found any way to get it working yet either.  Hopefully someone comes up with a fix as I have become addicted to Chrome.

---

### Post by Mike.lifeguard on 2010-05-03
> **Tulsapoke said:**
> I upgraded to Lucid 10.04 and now my Java in Chrome and Chromium quit working.  I haven't found any way to get it working yet either.  Hopefully someone comes up with a fix as I have become addicted to Chrome.

Strange - I did the same upgrade with no issue re java in chrome. Is there any error message?

---

### Post by zeroseven0183 on 2010-05-03
For a summary of their differences, check out [http://code.google.com/p/chromium/wiki/ChromiumBrowserVsGoogleChrome](http://code.google.com/p/chromium/wiki/ChromiumBrowserVsGoogleChrome) where it says

> Google Chrome is the Chromium open source project built, packaged, and distributed by Google.

I only use Google Chrome beta. I believe Chromium-browser is the daily-build.

---

### Post by ubunterooster on 2010-05-03
Google Chrome is the official. Chromium is what's given to the distributions to alter. Chromium will vary from one distro to another, but Google Chrome is always the same.

---

### Post by ruario on 2010-06-20
> **flyfishingphil said:**
>  It appears to me that the java is already in there but Chromium doesn't "see" it. Is there something I need to do to get it to "see" and "use" the java that's already plugged in?

Use Sun's Java or hack around it by creating various symlinks, see:
[https://bugs.edge.launchpad.net/ubuntu/+source/openjdk-6/+bug/594791](https://bugs.edge.launchpad.net/ubuntu/+source/openjdk-6/+bug/594791)

---

### Post by da burger on 2010-06-20
The primary difference though is how it was built. Chrome is built by google and is an official release. It is built from the chromium source code with only a few modifications. Chromium is what it is called when built by anyone else who can of course make their own modifications.

---

