---
title: "Downloading files option?"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by Camilia on 2008-12-17
I want to fill out an application that requires Adobe Acrobat Reader thus in synapse I clicked xpdf. I got 5 programs, xpdf-common, pdf-reader, Lesstif2, and Lib1-5. 

There was a question as to just download package files. What would happen if I clicked that?

---

### Post by Titan8990 on 2008-12-17
You would have to install them yourself after downloading the .deb.

---

### Post by Camilia on 2008-12-17
> **Titan8990 said:**
> You would have to install them yourself after downloading the .deb.

So then I could decide on which 1s I wanted to install?

---

### Post by handydan918 on 2008-12-17
No. It the package manager installed those because they are "dependencies" for the program you want. You need them, even if you don't want them...;-)

---

### Post by Camilia on 2008-12-17
I wonder if all the programs that added along with those check is the reason that surfing with ubuntu get slow at times?

---

### Post by Kellemora on 2008-12-17
Hi Camilia

Programs loaded shouldn't have anything to do with Networking Speed.

How many hidden programs you have running in the background for convenience service might be using up too much CPU or memory causing page file swapping.

I've noticed the internet to be a little slow these past couple of days and I thought it might be my machines.  But I have 8 machines here on-line and even the most bare bones machine was slow too!

My Internet Provider has said we have a heavy user on our trunk and when they are doing major stuff, we all get slowed down a little as we get less of the share of the bandwidth.
I just told them at these prices I should have a dedicated fiber optic cable, hi hi........

TTUL
Gary

---

### Post by emilstanescu on 2008-12-27
Hei there, is anybody who can help me  about installing AdobeReader. After download extension(plug-in) for Firefox I got this error: /tmp/AdobeReader_enu-8.1.3-1.i486.rpm could not be opened, because the associated helper application does not exist. Change the association in your preferences. I do not know what that means. Thanks, Emil S.

---

### Post by Camilia on 2008-12-27
I don't understand why you didn't start a thread for help. There is probably some software missing that you need to download. 

Anyways I simply went to system - administration - synapse manager. Then searched for adobe reader. There were many programs that are for adobe. Then click on 1s you want and click apply. I am not certain which are needed so I downloaded all of them.

There are 4 ways you can download programs, synapse manager, add/remove, terminal, and website.

---

### Post by homer693 on 2008-12-27
> **emilstanescu said:**
> Hei there, is anybody who can help me  about installing AdobeReader. After download extension(plug-in) for Firefox I got this error: /tmp/AdobeReader_enu-8.1.3-1.i486.rpm could not be opened, because the associated helper application does not exist. Change the association in your preferences. I do not know what that means. Thanks, Emil S.

emilstanescu, you need a .deb file, not a .RPM file, RPM files are normally for red hat linux, not ubuntu, re-download the package in .DEB format and it should install

---

### Post by Camilia on 2008-12-27
> **homer693 said:**
> emilstanescu, you need a .deb file, not a .RPM file, RPM files are normally for red hat linux, not ubuntu, re-download the package in .DEB format and it should install

So the wrong form of adobe reader was downloaded?  How is it reloaded into .deb format?

---

### Post by snova on 2008-12-27
> There was a question as to just download package files. What would happen if I clicked that?

It would download the required packages and then leave them. Nothing would be installed, but then you wouldn't have to download them when you did decide to install them.

What use this is, I do not know...

> So then I could decide on which 1s I wanted to install?

No. It downloads all of them because all of them are necessary. One package depends on another, or several others, and they have their own dependencies, so in this manner several packages are installed. Two or three of them appear to be libraries.

> Hei there, is anybody who can help me about installing AdobeReader. After download extension(plug-in) for Firefox I got this error: /tmp/AdobeReader_enu-8.1.3-1.i486.rpm could not be opened, because the associated helper application does not exist. Change the association in your preferences. I do not know what that means. Thanks, Emil S.

It's an RPM, which isn't native to Ubuntu. Ordinarily, you'll never come across them. So it doesn't know what to do with it.

They release a .deb, found here: [http://get.adobe.com/reader/otherversions/](http://get.adobe.com/reader/otherversions/)

Select, "Linux - x86 (.deb)".

This page has instructions for getting PDF support in Firefox, it may help: [http://support.mozilla.com/en-US/kb/Opening+PDF+files+within+Firefox](http://support.mozilla.com/en-US/kb/Opening+PDF+files+within+Firefox)

> So the wrong form of adobe reader was downloaded? How is it reloaded into .deb format?

It is possible, but tricky and not generally a good idea...

---

### Post by Camilia on 2008-12-28
emilstanescu did you get it working?

I noticed at the site for adobe reader that under different os there is linux .deb. Perhaps that would work.

Also the instructions here might help:[http://ubuntuforums.org/showthread.php?t=1014336](http://ubuntuforums.org/showthread.php?t=1014336)

Following the instructions a got a form that needed to fill info on downloaded.

---

