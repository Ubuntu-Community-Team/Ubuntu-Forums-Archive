---
title: "Open files in Lubuntu"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by arashiko28 on 2010-04-18
I know it sound a bit weird, but here's how it goes. I have installed Xubuntu on a very old desktop, and when heard about Lubuntu, installed it, it can match any regular XP computer now. But... there is a but, I can't find the way to select an application to open files like .doc, .ptt, .exe, as usually would do open office, but have to go through a list every time a file must be opened to find the application and select it, instead of the usual double click and done.
How can I solve this or is this the way Lubuntu works?

---

### Post by Jon Monreal on 2010-04-22
What version of Lubuntu are you running?

You should be able to check the box "Set selected application as default action of this file type", or does this not work?

---

### Post by arashiko28 on 2010-04-22
It's Lubuntu desktop over a Xubuntu 9.10 installation. The check box does not shows.

---

### Post by Jon Monreal on 2010-04-22
It doesn't under Karmic.

Here's a fix posted under the [bug on Launchpad]("https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/455344").
[QUOTE=[Julien  Lavergne]("https://launchpad.net/%7Egilir")]A fixed package is avalable in my PPA : [https://edge.launchpad.net/~gilir/+archive/unstable/+packages]("https://edge.launchpad.net/%7Egilir/+archive/unstable/+packages")
 Please test it and report back any problem you have with this. If the  tests are good, I'll propose it for inclusion in official repository.
 Thanks.
[/QUOTE]

If you need help installing the fix, please feel free to ask. Also be aware that this is a private PPA, and the user could theoretically put malicious binaries in there.

Otherwise, you could wait for Lucid, as this problem will be fixed with the new release.

---

### Post by arashiko28 on 2010-04-22
> **Jon Monreal said:**
> It doesn't under Karmic.

Here's a fix posted under the [bug on Launchpad]("https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/455344").


If you need help installing the fix, please feel free to ask. Also be aware that this is a private PPA, and the user could theoretically put malicious binaries in there.

Otherwise, you could wait for Lucid, as this problem will be fixed with the new release.

I'll wait, it's only a week away. :p

---

