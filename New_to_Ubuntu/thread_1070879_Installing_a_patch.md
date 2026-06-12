---
title: "Installing a patch"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by portach king on 2009-02-15
Hi guys,
I've been using a great mp3 tagging program called Kid3 but recently one of its features stopped working correctly. A patch has been released here: [http://sourceforge.net/tracker/?atid=529223&group_id=70849&func=browse](http://sourceforge.net/tracker/?atid=529223&group_id=70849&func=browse) which I have downloaded, but I'm just very confused as to how to install the file. Any help would be great.

---

### Post by ajgreeny on 2009-02-15
No knowledge of kid3, but have you also tried **audio-tag-tool**, which I use quite a lot.

---

### Post by portach king on 2009-02-15
Thanks for the suggestion but Kid3 does everything that program you listed does and more.
I'm not looking for a new app, but simply a quick guide on how to install a small patch. :)

---

### Post by supersonicdarky on 2009-02-15
You need to get the source of the program, navigate to the root of the src, download patch, and run
```
patch -p0 <path to patch>
```
then compile everything

[More info](http://ubuntuforums.org/showthread.php?t=241837#3)

---

### Post by Psyphre on 2009-02-16
> **supersonicdarky said:**
> You need to get the source of the program, navigate to the root of the src, download patch, and run
```
patch -p0 <path to patch>
```
then compile everything

[More info](http://ubuntuforums.org/showthread.php?t=241837#3)

I'm also trying to learn to patch.

I have a source folder (totem)
and a patch (rgba.patch).

I navigated to the totem folder and moved the rgba.patch file into it.
Then ran:

patch -p0 rgba.patch

but I get nothing. Just blank. No new line comes up to allow me to type another command.

---

### Post by Psyphre on 2009-02-17
ah solved it.

its:

patch -p0 < patchname

there is no > at the end.

---

