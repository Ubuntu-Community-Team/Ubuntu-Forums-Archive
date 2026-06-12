---
title: "Virtual Box Systems displaying a black screen"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by beastrace91 on 2009-02-06
So I have had virtual box running great on my Ubuntu 8.10 system but for some strange reason when I went to boot up my Xp Guest this evening all it showed was a black screen. Not a big deal I have a Vista guest as well, when to boot this also got nothing but a black screen. Now slightly curious, I tried my opensolairs guest... it also gets just a black screen. Anyone have any idea what might be causing this? I was going to try and sync my black berry tonight and I needed my windows VB to do so.

Halp!
~Jeff

---

### Post by beastrace91 on 2009-02-06
I also just recently updated to the lastest nVidia driver (180.27) would this be the cause maybe?

~Jeff

---

### Post by jolx on 2009-02-06
maybe you could try running
```
sudo vbox_build_module
```

and see if that helps

---

### Post by beastrace91 on 2009-02-06
That yields command not found :(

~Jeff

---

### Post by jolx on 2009-02-06
so is 'sudo' not found, or is it 'vbox_build_module'?

---

### Post by hoxboy on 2009-02-06
can i ask??
what happend to my ubuntu?

if all the letters are square?

[[img]http://www.hoxboy.dragonadopters.com/dragonimage_37618_43129_pixel.gif[/img]](http://hoxboy.dragonadopters.com/dragon_37618):popcorn:

---

### Post by beastrace91 on 2009-02-07
```
jeff@jeff-ubuntu:~/Desktop/FAH6.24beta-Linux$ sudo vbox_build_module
sudo: vbox_build_module: command not found

```

If it was saying "sudo" command not found this would be a different thread entirely lol.

~Jeff

---

### Post by beastrace91 on 2009-02-08
I believe my recently updated NVidia driver (180.xx) is causing the issue. Does anyone have VB working with any form of the NVidia 180.xx driver?

~Jeff

---

### Post by beastrace91 on 2009-02-09
Alright Virtual Box is flat out not working at this point for me. I have tried reverting drivers back the 177.xx and I still get a black screen, I have tried recompiling the VBox kernel, I have even tried reinstalling VB. Anyone have any ideas? I was really enjoying this handy piece of software.

~Jeff

---

### Post by the_unforgiven on 2009-02-16
> **beastrace91 said:**
> Alright Virtual Box is flat out not working at this point for me. I have tried reverting drivers back the 177.xx and I still get a black screen, I have tried recompiling the VBox kernel, I have even tried reinstalling VB. Anyone have any ideas? I was really enjoying this handy piece of software.

~Jeff
Looks like the emulated VBox bios is corrupt.
Can you please try to build it from sources? maybe, from a fresh checkout?
I'm using nVidia 177.82 and VBox built from sources - seem to be working fine for me.

If you want help in how to build it from sources, please let me know - I'll give the pointers.

---

### Post by beastrace91 on 2009-02-16
Can you get the source for the non-OSE version? I really need USB support (I need the virtual system to make my TI84 and blackberry software work)

~Jeff

---

