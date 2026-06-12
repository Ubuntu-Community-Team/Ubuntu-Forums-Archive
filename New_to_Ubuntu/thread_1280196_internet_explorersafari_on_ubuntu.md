---
title: "internet explorer/safari on ubuntu"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by anatak on 2009-10-01
Hello,

Does anybody know if it is possible to install internet explorer and safari on Ubuntu ?

if it is possible could you point me to the right direction ?
I found the ies4linux but I didn't found out if it would work on Jaunty 9.04

thank you so much
anatak

---

### Post by wilee-nilee on 2009-10-01
From a quick Google search it appears wine is needed to run those. Have you tried opera, chromium, seamonkey a host of open source browsers. Running Wine though can have a set of problems in itself.

---

### Post by mac9416 on 2009-10-01
I have used ies4linux in Jaunty, and it works perfectly. The installation described on their site is very easy, and went off without a hitch.

---

### Post by inobe on 2009-10-01
i don't intend on hijacking the op's post.

maybe i may learn something, why would anyone need Internet explorer in ubuntu ?

---

### Post by jrusso2 on 2009-10-01
I have gotten both to run but I would not say they run flawless.

I think playsonlinux can install both.

---

### Post by Torgas Prim on 2009-10-01
> **inobe said:**
> i don't intend on hijacking the op's post.

maybe i may learn something, why would anyone need Internet explorer in ubuntu ?

I use ubuntu only at home.
I need IE for access to my work email from home. That is the ONLY browser supported... sheesh :(

---

### Post by wilee-nilee on 2009-10-01
> **Torgas Prim said:**
> I use ubuntu only at home.
I need IE for access to my work email from home. That is the ONLY browser supported... sheesh :(

 Have you tried the add-on in Firefox user agent switcher to spoof.

---

### Post by anatak on 2009-10-02
I develop websites and I am recently switched from a windows development pc to a ubuntu pc.
Sadly enough a large part of the internet population still uses some IE browsers anciend old and new
For my personal projects I have an approach that boils down to if it works in firefox it is good enough for me but for commercial projects I have to test against internet explorer also

so that is the reason

---

### Post by Paqman on 2009-10-02
> **inobe said:**
> why would anyone need Internet explorer in ubuntu ?

Mostly for web development, as anatak says.

---

### Post by anatak on 2009-10-02
been trying to install ies4linux on ubuntu but no luck

installed the latest wine
but ies4linux still complains that my wine version is too old.
after that it just blocks

any ideas ?

---

### Post by Paddy Landau on 2009-10-02
If you develop browsers, you're going to have to check against Firefox, IE7, IE8, Safari, Chrome, and Opera. Ensure that you stick strictly to HTML and CSS standards, and usually it will work in all of them.

Chrome, IE7, IE8 and Safari, as I understand, work only under Windows. Sorry, you'll have to log into Windows to check!

---

### Post by HarrisonNapper on 2009-10-02
It may very well be worth it to run Windows and Mac in VirtualBox to run IE/Safari. Especially if you have a site that requires or supports specialized plugins (Silverlight, Flash, Java, etc).

Also, in response to the question of why, in addition to web development, some applications use an embedded IE and the way the app handles information coming over the intahrwebs requires IE to be installed.

---

### Post by FrostyC on 2009-10-22
> **Paddy Landau said:**
> Chrome, IE7, IE8 and Safari, as I understand, work only under Windows. Sorry, you'll have to log into Windows to check!

I would not recommend "log[ging] into Windows" ever. lol

Chrome (Early Access Release Channel): [http://dev.chromium.org/getting-involved/dev-channel](http://dev.chromium.org/getting-involved/dev-channel)
Chromium (More stable than Chrome): [https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

Apparently Safari's new beta works fairly decent with WINE...

As for IE, I *personally* usually redirect browsers using their User Agent string to a page that basically says "Get a different browser unless you love spyware..."
But IEs4Linux allows you to install it on Linux: [http://www.linux.com/archive/feature/147592](http://www.linux.com/archive/feature/147592)

However, these sites usually prove pretty useful for checking how your site renders in other browsers:
[http://browsershots.org/](http://browsershots.org/)
[http://ipinfo.info/netrenderer/](http://ipinfo.info/netrenderer/)

---

### Post by donaldshelton on 2009-11-04
I also need IE for work.  My wife must report her hours worked online, and they do not support anything but IE.  I could make her go to the public library, but.....

I googled the IE for Linux, and it referred my to a website called tatanka.  It says that this could be a malicious website.  Is this true?

I also followed the directions on the site "How to install IE in two easy steps." No luck.

I'd appreciate any help offered.  I'd hate to have to reinstall Windows!!!

---

### Post by Sir Jasper on 2009-11-04
Hi,

I have Wine and Wine-Doors and the latter provides for the installation of Internet Explorer 6. I have not found the slightest problem running ie 6 (however, it is less secure than Firefox, so it is only used when other programs running in Wine call it).

My regards

Addendum:
MailWasher Free, runs almost perfectly in Wine, and it may be good for auto- monitoring new email arrivals and viewing/deletion from a single email account without download

---

### Post by wmcbrine on 2009-11-04
> **Paddy Landau said:**
> Chrome, IE7, IE8 and Safari, as I understand, work only under Windows.Well, Safari originated on the Mac, but it was based on KHTML, which of course originated on Linux. So if you run Konqueror, you can emulate the Safari rendering experience to some degree. And Safari's engine has since been ported *back* to Linux, as WebKit, so there are a few more browsers based on that which you can test with as well. Google Chrome is also based on WebKit.

For those just trying to get into a site that claims to only support IE, I strongly recommend that you try the User Agent Switcher extension for Firefox first, before resorting to running IE under Wine or the like.

---

### Post by mangurt on 2009-11-04
You can install both of them via playonlinux
[http://www.playonlinux.com/en/]("http://www.playonlinux.com/en/")

They both install without a problem.

---

### Post by md08 on 2009-11-05
I need Internet Explorer because a certain site I use for school activities is limited to IE and Safari. Is there any way to have IE or Safari run on Ubuntu?

---

### Post by RJ12 on 2009-11-05
> **donaldshelton said:**
> I also need IE for work.  My wife must report her hours worked online, and they do not support anything but IE.  I could make her go to the public library, but.....

I googled the IE for Linux, and it referred my to a website called tatanka.  It says that this could be a malicious website.  Is this true?

I also followed the directions on the site "How to install IE in two easy steps." No luck.

I'd appreciate any help offered.  I'd hate to have to reinstall Windows!!!

Well just to let you know about the malicious site tatanka in the indian Sioux lang means "buffalo" so... (I learned in my Tx History class.)

---

### Post by PaulInBHC on 2009-11-05
I got ies4linux installed but can't close the terminal, don't have a desktop shortcut, and sysmon shows wineserver and a bunch of bash running. What to do?

Edit: sysmon cleared itself out while I was reading about terminal commands, lol

---

### Post by SunnyRabbiera on 2009-11-05
> **PaulInBHC said:**
> I got ies4linux installed but can't close the terminal, don't have a desktop shortcut, and sysmon shows wineserver and a bunch of bash running. What to do?

I would try playonlinux, seems to do IE7 just fine.
Playonlinux offers a .deb installer for ubuntu:
[http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html)

---

