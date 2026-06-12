---
title: "How to make step-by-step install on new BASKET NOTE PADS file"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by doublewitt on 2010-04-17
Can someone be kind enough to show me how to install the new Basket Note Pads file? I haven't yet understood how to work with .tar.bz2 files. I downloaded the latest file: **VERSION 2 Beta 1**. I'd appreciate a step-by-step guide - if it's not too much trouble...
thx

---

### Post by wojox on 2010-04-17
When you extract the file and look in it's directory isn't there an install or read me file?

---

### Post by doublewitt on 2010-04-17
Just looked at it.
There is an INSTALLER exec and when I click on it, I can select "run with terminal" but after doing so, I select either 1 or 2 in the dialog, and hit "enter", and then the terminal window disappears... and nothing happens...

---

### Post by Didius Falco on 2010-04-18
> **doublewitt said:**
> Just looked at it.
There is an INSTALLER exec and when I click on it, I can select "run with terminal" but after doing so, I select either 1 or 2 in the dialog, and hit "enter", and then the terminal window disappears... and nothing happens...

the package basket 2.0~beta1-0ubuntu1 is available through the universe repository. It is a KDE file, though, so it's going to pull in quite a lot of Kubuntu files with it, unless you've already installed the Kubuntu Desktop. I'm going by what your install info under your name and avatar says... 

You can install it from Synaptic Package Manager by simply doing a search for basket, or you can open a Terminal window (Menu/Accessories/Terminal) and typing 

```
sudo apt-get install basket
```If you are interested in learning how to compile a program from a  tar.bz2 archive, here is a guide to doing just that:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

I hope this helps,

Regards,

Didius

On Edit: If you are using Kubuntu, here are the directions for installing it under KDE:

[http://basket.kde.org/install.php](http://basket.kde.org/install.php)

---

### Post by doublewitt on 2010-04-18
Thanks for all the tips...

After installing these missing files:

kdelibs v4.1
qimageblitz
kdepimlibs v4.1

I was able to install the latest file for Basket Note Pads. And so the terminal window did not "disappear" as before and the installation proceeded just fine.

---

### Post by Didius Falco on 2010-04-18
You are very welcome!

Mark this thread as solved, so anyone else having the same problem has a better chance at finding the solution.

Regards,

Didius

---

