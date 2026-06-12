---
title: "Help getting a few things going in Xubuntu."
date: 2009-02-15
forum: New to Ubuntu
---

### Post by Jaydn on 2009-02-15
Hi. 
I've just installed Xubuntu on an older computer and I have run into a few problems. Firstly, upon boot up, it tells me it has to run in low-graphics mode. This is a tad annoying. Secondly, I am in need of the appropriate plugins so that I may watch Youtube videos in Xubuntu. Thanks in advance to anyone who can help me out.

-Jaydn

---

### Post by Jollyollydog66 on 2009-02-15
```
sudo apt-get install xubuntu-restricted-extras
``` Will allow you to watch youtube videos. You can get it through the package manager just make sure you enable restricted repositories.

I don't know about your other issue sorry.

---

### Post by Jaydn on 2009-02-15
Yeah....
That didn't work...
It says it cannot find xubuntu-restricted-extras.
I have multiverse repositories enabled, yet it still can't find it.
I even tried just finding the ubuntu-restricted-extras. Nothing.

---

### Post by Jollyollydog66 on 2009-02-15
In Add/Remove do you have "all available options" chosen on the little drop down menu? I didn't have to enable any extra repositories, I just had to choose all available options and let it refresh. If that doesn't work I'm afraid I don't know.

---

### Post by 4Orbs on 2009-02-15
On these forums, under the Multimedia & Video section, there is a sticky post titled Comprehensive Multimedia & Video Howto. I have followed this tutorial from top to bottom on numerous Xubuntu installations and recommend you take a look. Works perfectly for me.

---

### Post by Jaydn on 2009-02-15
Ok. 
This thing is getting on my nerves. 
I was finally able to find xubuntu-restricted-extras, but it said "This package cannot be installed on your system." Wtpf?
This is all so dang annoying.

---

### Post by SunnyRabbiera on 2009-02-15
hmm, well you can try it the direct way:
try this page
[http://packages.ubuntu.com/intrepid/xubuntu-restricted-extras](http://packages.ubuntu.com/intrepid/xubuntu-restricted-extras)

choose the one for your system (1386 or amd64)

---

### Post by anjilslaire on 2009-02-15
post system specs & xubuntu version (i386? x64?) please.

Also, is the network access working properly?

---

### Post by Jaydn on 2009-02-15
Alright. I have now installed all the plugins I needed. So that's all taken care of. Now the only problem is the low-graphics crap.
It's i386 x32. The thing says something about the chipset...
I hope this doesn't mean it's a lost cause...:(

The tower's got 512mb of RAM and an AMD Athlon processor, if that helps at all....

---

### Post by gn2 on 2009-02-15
What graphics adapter does it have?

---

### Post by Jaydn on 2009-02-15
No idea. I can't get that info, as the tower was given to me for free by a friend. I don't know if it has any graphics capability at all, now that I think about it...
Nevermind then. Sorry for wasting your time....

---

### Post by anjilslaire on 2009-02-17
you can see your video chipset with
```

sudo lshw

```

---

