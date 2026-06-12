---
title: "screen card"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by hemoali on 2011-02-08
please i USE UBUNTU10.10
and I want to know how to know the type of the screen card and and if it 1 , 2 , 512 I want to know every thing about screen card
how??????????

---

### Post by Joe of loath on 2011-02-08
Umm

What is a screen card?

---

### Post by Lucradia on 2011-02-08
> **Joe of loath said:**
> Umm

What is a screen card?

Guessing with the "512" maybe "Video card"? Also guessing the OP's major language isn't English due to that.

---

### Post by s.fox on 2011-02-08
Thread moved to [Absolute Beginner Talk]("http://ubuntuforums.org/forumdisplay.php?f=326")

---

### Post by hemoali on 2011-02-08
ok I mean The video card 
And I want to know the kind of this video card

---

### Post by Lucradia on 2011-02-08
> **hemoali said:**
> ok I mean The video card 
And I want to know the kind of this video card

You mean, you want to know the video card you currently have?

---

### Post by hemoali on 2011-02-08
yes

---

### Post by Lucradia on 2011-02-08
> **hemoali said:**
> yes

In terminal, type:

```
lspci | grep VGA
```

---

### Post by s.fox on 2011-02-08
> **hemoali said:**
> yes

Please open a terminal.

Run this command:

```
lspci
```

---

### Post by hemoali on 2011-02-08
ok that what appeared know what is the kind and is this 1 mh or 128k or 512 k or 2 mh

00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)

---

### Post by Lucradia on 2011-02-08
> **hemoali said:**
> ok that what appeared know what is the kind and is this 1 mh or 128k or 512 k or 2 mh

00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)

You probably won't be running any good 3D on that, but, to figure out the video memory on this, you'll need to install another program like hardinfo. Intel doesn't like to specify the memory of the integrated chipsets.

---

### Post by hemoali on 2011-02-08
please what is the type of my video card

---

### Post by hemoali on 2011-02-08
ok look what I am find there
[IMG]http://store3.up-00.com/Feb11/0BL71676.png[/IMG][IMG]http://store3.up-00.com/Feb11/0BL71676.png[/IMG]http://store3.up-00.com/Feb11/0BL71676.png
now is it 512kb 
or 256 mb
or 1 mb

---

