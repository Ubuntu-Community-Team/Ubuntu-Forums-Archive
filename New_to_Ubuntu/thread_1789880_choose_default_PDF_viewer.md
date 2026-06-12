---
title: "choose default PDF viewer"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by webmaker on 2011-06-24
I have never been able to get FoxIt to work, how can I remove it and use a different viewer as the default?  I can't find it in the Synaptic Package Manager list to remove.
Thanks

---

### Post by owiknowi on 2011-06-24
by default ubuntu installed and used evince document viewer to view pdf files.
till now i haven't seen foxit in a ubuntu repository? don't know about v11.xx though.

---

### Post by kimda on 2011-06-24
You can change the default application by going to a pdf file in nautilus. Right click with mouse and select properties. Then choose the fourth tab called "Open with" and select the default application you want to open pdf's with. Now it should open with your pdf viewer.

---

### Post by haqking on 2011-06-24
whats wrong with Adobe reader ?

acroread from synaptic package manager or software centre.

here is a link if you are unfamiliar with how to add it.

[http://www.liberiangeek.net/2011/04/how-to-install-adobe-reader-acroread-in-ubuntu-11-04-natty-narwhal/](http://www.liberiangeek.net/2011/04/how-to-install-adobe-reader-acroread-in-ubuntu-11-04-natty-narwhal/) this is for 11.04 but applicable to prior versions

---

### Post by lovinglinux on 2011-06-24
> **haqking said:**
> whats wrong with Adobe reader ?

[LIST]
[*]200+ Mb
[*]Adobe Reader X next generation not supported in Linux
[*]Security vulnerabilities
[*]Proprietary
[/LIST]

BTW, Mozilla is working on a built-in HTML5 PDF viewer, that will allow to view PDF files in Firefox without the need of a plugin, with much better security.

---

### Post by haqking on 2011-06-24
> **lovinglinux said:**
> 
[LIST]
[*]200+ Mb
[*]Adobe Reader X next generation not supported in Linux
[*]Security vulnerabilities
[*]Proprietary
[/LIST]

BTW, Mozilla is working on a built-in HTML5 PDF viewer, that will allow to view PDF files in Firefox without the need of a plugin, with much better security.


well yeah i concur with your statements, but he never asked for open source, i was just supplying information as he said he wanted a different viewer but yes i agree with what you said.

of course i could of added gv, xpdf, okular ad infinitum ad nauseum ;-)

---

### Post by Frogs Hair on 2011-06-24
If you are looking for more features , take a look at PDF Editor in the software center . Not even Adobe suggests using older less secure versions of their products, so if you install the version in the software center make sure it is up to date  . If the evince icon is not visible on the menu , open the main menu and check the box under the graphics category.
  [http://pdfedit.cz/en/index.html](http://pdfedit.cz/en/index.html)

---

### Post by walt.smith1960 on 2011-06-24
> **webmaker said:**
> I have never been able to get FoxIt to work, how can I remove it and use a different viewer as the default?  I can't find it in the Synaptic Package Manager list to remove.
Thanks

I was able to get Foxit to work but it's version 1.1 for Linux and 4.x or 5.x for Windows.  I used it like a Windows .exe app.  Create a new launcher and link to <user>/foxit/ Foxit.bin.  This was in an older version of Ubuntu.

Edit:  There is a .deb package for Foxit for Linux 1.1.  it's 32 bit only so you'd have to do the force-architecture or force-all trick if you have 64 bit.  I just did what I did before- download, extract and double-click the executable foxit file.  Less messing around.

---

