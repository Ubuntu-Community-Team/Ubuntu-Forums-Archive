---
title: "Firefox and Add-ons"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by GeordieJedi on 2009-05-08
Hi all, Hope your all well.

Ive got a quick question that I can hope you help with.
(Im sure im being a bit daft but....)

Right, Ive just done a nice fresh re-install of Ubuntu 8.10.
And I was setting up Firefox with some add-ons. Stuff like =

Ad block plus, No script, down them all, video download helper.
(Stuff I consider to be essential).

However the problem is this. Whenever I go into Firefox now to install
any add-ons. All I get the option to do, is "Download now" then Im
allowed download the extension to my HD?

Does anyone know what Ive done wrong? Or does No script or whatever
conflict with add-ons?

Thanks in advance for any help.

---

### Post by jlhaslip on 2009-05-08
Might be a good question to post at the Mozillazine forums. They deal with Add-ons (and conflicts) all the time over there.

---

### Post by kansasnoob on 2009-05-08
That's why I prefer a native Firefox installation!

[http://ubuntuzilla.wiki.sourceforge.net/?f=print](http://ubuntuzilla.wiki.sourceforge.net/?f=print)

Soooooooooo simple, download:

[http://sourceforge.net/project/showfiles.php?group_id=202789&package_id=241580](http://sourceforge.net/project/showfiles.php?group_id=202789&package_id=241580)

Double click, then go to terminal and:

```
ubuntuzilla.py -a install -p firefox

```

Then proceed with native Firefox!

---

### Post by Sir Jasper on 2009-05-08
Hi GeordieJedi,

Tomorrow, I will investigate Kansasnoob's interesting link.

Firefox has its own safemode (not buntu safemode)
To try it type or copy/paste into your Terminal; firefox -safe-mode
that helped me to eliminate some causes when I had a 
different problem.

The only FF add-on I cannot get to work is:
Finjan Secure Browsing 1.314
I would be very pleased to learn if anyone has successfully used it.

My regards

---

### Post by lovinglinux on 2009-05-08
> **GeordieJedi said:**
> However the problem is this. Whenever I go into Firefox now to install any add-ons. All I get the option to do, is "Download now" then Im
allowed download the extension to my HD?

It doesn't mean you only have the option to save to disk. Mozilla just changed the text in the button. When you click, it will install the extension automatically. Try it! I already did.

Even if it doesn't, then all you have to do is save the file to disk and open it through Firefox (File >> Open File).

---

### Post by kansasnoob on 2009-05-08
> **Sir Jasper said:**
> Hi GeordieJedi,

Tomorrow, I will investigate Kansasnoob's interesting link.

Firefox has its own safemode (not buntu safemode)
To try it type or copy/paste into your Terminal; firefox -safe-mode
that helped me to eliminate some causes when I had a 
different problem.

The only FF add-on I cannot get to work is:
Finjan Secure Browsing 1.314
I would be very pleased to learn if anyone has successfully used it.

My regards

I've never tried that Plug-in but I've done extensive testing with Ubuntuzilla:

[http://ubuntuforums.org/showthread.php?t=467724&page=6](http://ubuntuforums.org/showthread.php?t=467724&page=6)

Beginning with post #66!

So, if the plug-in works with a native Firefox install that should get it working. Be mindful that you should always use the newest add-on version and a lot of times the add-ons in the repos are ancient!

---

