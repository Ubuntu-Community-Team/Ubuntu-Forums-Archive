---
title: "Doxie Scanner"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by Dharma173 on 2010-08-08
My new Doxie Scanner (Mac & Windows only) works well on wife's Windows Netbook, but I want to use it with my Ubuntu!  Neither Simple Scan no Xsane recognizes the usb attached Doxie.  Any help really appreciated!

---

### Post by davidmohammed on 2010-08-08
I think [this]("http://community.getdoxie.com/discussion/56/linux-support/") doxie reply says it all!

---

### Post by Dharma173 on 2010-08-08
Thanks, davidm..., I did see that Doxie posting but keep hoping that someone will have discovered the source of the drivers.  I wouldn't have a clue as to how to do that, but someone probably does.  Even though as you've said, your reference probably says it all, I'm going to leave this open for a week to see if anyone else might reply.  Thanks, again.

---

### Post by berlinblue on 2011-06-23
Hi there,

I just received my **Doxie Scanner**.
And I am also looking much forward to be able to use the Doxie software as a native app on linux. 

Somehow, I got it to work in a *very simple* and *basic mode*, by installing the [Doxie Windows software]("http://www.getdoxie.com/support/index.html"), using **[Wine]("https://help.ubuntu.com/community/Wine")**.

Then, when I start the native scan app (Simple Scan 2.32.0.1) in Ubuntu 11.04, it determines the scanner as the model "Syscan DocketPort 467".

Doing some further searching on this, turns out hat the Doxie Scanner seems to be a variant of that model. 

Then I found an informative page at the [http://manpages.ubuntu.com]("http://manpages.ubuntu.com/manpages/natty/man5/sane-genesys.5.html") where they talk about this type of scanner, well-working on Linux.

Unfortunately, so far I lack the understanding of how to install / activate the mentioned "sane-genesys library". 

Any help to what can be done to get a Doxie Scanner (i.e. Syscan DocketPort 467) working on Ubuntu, would be higly appreciated!

Many thanks in advance.

---

### Post by duffrecords on 2012-01-08
I got it to successfully scan a page by running xsane as root.  Obviously, that's not a solution but it's proof that the driver works.  It's just a matter of setting the correct permissions for the device.  Here's the info reported by xsane:

Vendor: Syscan
Model: DocketPORT 467
Type: flatbed scanner
Device:011
Loaded backend: genesys:libusb:002
Sane version: 1.0.22

I didn't have to install any extra packages besides xsane; this was a brand new Ubuntu 11.10 installation.

---

### Post by PickleHead on 2012-09-01
Any news on this? I was thinking about buying a Doxie U for school...

---

### Post by oldos2er on 2012-09-02
Please start a new thread for your question.

---

