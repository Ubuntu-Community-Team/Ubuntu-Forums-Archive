---
title: "wine source directory"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by beamo on 2008-12-13
I am trying to install something and it tells you to put a paatch in the wine source directory. Is that just ~/wine/?

---

### Post by Titan8990 on 2008-12-13
Try this command:

whereis wine


which wine


The directory it is looking for is most likely NOT the one that which returns. It should be somewhere under the /usr/ dir.

---

### Post by beamo on 2008-12-13
Thanks, I found it that way. My problem now is executing these instructions. They are not clear to me...




At this point only way to get it to work is to download latest(1.1.8) sources, patch them and then compile wine.
WinD3D patch: [http://bugs.winehq.org/attachment.cgi?id=17130](http://bugs.winehq.org/attachment.cgi?id=17130)
Download it, paste it to wine sources dir (wine-1.1.8) and type
patch -p1 < filename.diff

---

### Post by CatKiller on 2008-12-13
> **beamo said:**
> I am trying to install something and it tells you to put a paatch in the wine source directory. Is that just ~/wine/?

No.

If you wanted to patch the source code to Wine, you would first need to acquire the source code to Wine. Either directly from the Wine website, or with ```
sudo apt-get source wine
``` Installing Wine from the repositories just installs the binaries that are needed to make it run.

Then you would run your patch against the source tree, wherever you'd downloaded it to, and then run the standard configure/make/checkinstall to compile and install your patched source code.

---

### Post by beamo on 2008-12-13
Thanks catkiller. I installed wine as you suggested. My problem is the patch code. Do I put the code he links to (: [http://bugs.winehq.org/attachment.cgi?id=17130](http://bugs.winehq.org/attachment.cgi?id=17130)) into a file? If so, what do I call it? I'm putting it at /usr/share/wine. He tells you to "Download it, paste it to wine sources dir (wine-1.1.8) and type
patch -p1 < filename.diff." Does the filename matter?

---

### Post by CatKiller on 2008-12-13
I've never done this, so I can't tell you from experience. But it seems from the instructions that you save that text as a file. It doesn't matter what you call it, but you'll replace *filename.diff* with whatever you've chosen to call it.

The instructions state that it's a patch against the Wine 1.1.8 source code, so that's the source code you'll be patching. You can get that from [here]("http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449"). You probably **don't** want Wine already installed from the repositories when you're installing another version from source. After you've downloaded and extracted the source code, you'd put your patch file in the directory you've extracted the source code to, and then run the *patch* command you were given.

**Checkinstall** is a utility that turns your compiled source into a package, so that it can be easily removed or upgraded using the package managment mechanism. I don't recall if it's included by default. If not, it's easy to install using Synaptic or apt-get, or what-have you.

You might find that [this page]("https://help.ubuntu.com/community/CompilingEasyHowTo") has some information that will help you on compiling from source. It seems like this might be quite complicated for you; is it really necessary that you use this patch? The problem might be fixed in a later version of Wine. Compiling software is quite interesting, but I'd generally avoid it unless I had to.

---

### Post by beamo on 2008-12-13
Thanks. I'm going to work on it until I get it. Thanks for all your help.

---

