---
title: "Compiz  &amp; Cairo dock compatibility with my pc"
date: 2011-03-22
forum: New to Ubuntu
---

### Post by Mylastconfusion on 2011-03-22
Hi there!

I'd like to install these Compiz & Cairo Dock but I'm scared I'll install them and my computer or graphics card might collapse! :confused: These are my pc's characteristics:

Dell Dimension 3100 - Intel(R) Pentium(R) 4 CPU 2.80GHz
Graphics card: VGA Compatible controller: Intel Corp 82915G/GV/910 GL Integrated Graphics Controller (rev 04) (prog-if 01 [VGA controller])
PCI Bridges: 
Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express port 1 (rev 04) (prog-if 00 [normal decode])
Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express port 2 (rev 04) (prog-if 00 [normal decode])
Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Bridge (rev d4) (prog-if 01 [substractive decode])

Looking forward to hearing some feedback. Thanks!!

---

### Post by Arijit_Kundu on 2011-03-22
you'll have no problem at all! I hope you have 1GB of ram or more. If you dont have more than 1 GB ram, try not to use too-fancy things in compiz.

---

### Post by Mylastconfusion on 2011-03-22
Thank you, how do I find out the RAM?

---

### Post by Frogs Hair on 2011-03-22
Type this into the terminal```
free
```

---

### Post by Dutch70 on 2011-03-22
Open system monitor and click the "system" tab.

You may want to check my sig. I have the Intel 82495 graphics card & Compiz causes my sytem to freeze. The workaround in post #22 of the thread in my sig works great! I use it on Ubuntu, Kubuntu, Linux Mint, Fedora & Zorin OS. It's very easy to do, just write down or print the instructions before going into a tty.

The workaround works with other Intel graphics cards as well. If for some reason it doesn't, just remove Compiz.

---

### Post by Mylastconfusion on 2011-03-22
It says Memory 486.8 MiB

Does that mean it's best if I don't install Compiz?:oops:

---

### Post by Dutch70 on 2011-03-22
You can always try it. If it causes problems, just uninstall it.

```
sudo apt-get remove compiz compiz-core
```

I highly recommend using post #22 of the thread in my sig.

---

### Post by mastablasta on 2011-03-22
compiz is already installed. you probably mean effects? you can enable them in desktop settings. if you can't then you can't use Compiz. you can install compiz manager where you manage what effect you want to have turned on or off. you also get some plugins i believe.
[http://en.wikipedia.org/wiki/Compiz](http://en.wikipedia.org/wiki/Compiz)
 
you can add a dock. there are a couple available. some are more resource demanding, some less.
[http://en.wikipedia.org/wiki/List_of_dock_applications](http://en.wikipedia.org/wiki/List_of_dock_applications)

---

### Post by Mylastconfusion on 2011-03-22
Thanks guys. :D

---

