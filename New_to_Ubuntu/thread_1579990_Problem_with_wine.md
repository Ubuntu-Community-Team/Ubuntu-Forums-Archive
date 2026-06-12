---
title: "Problem with wine"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by grobar87 on 2010-09-22
Hi,
I try to run FIFA 2008:lolflag: on my ubuntu lucid with wine and when i start the game i got this:( (screenshot)
Can someone tell me what is the problem with graphics...btw i have sound:confused:

---

### Post by Lateralis on 2010-09-22
[WineHQ]("http://appdb.winehq.org/") seems to suggest that FIFA 08 runs fine on [older version of Ubuntu]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9476").  So, which version of Wine are you using? 

```

wine --version

```

Also, some pretty obvious, silly and basic questions, but what hardware are you using?  Does your graphics card need proprietary drivers that aren't installed?  Have you got Wine working with other programs on this same PC?

---

### Post by grobar87 on 2010-09-22
> **Lateralis said:**
> [WineHQ]("http://appdb.winehq.org/") seems to suggest that FIFA 08 runs fine on [older version of Ubuntu]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9476").  So, which version of Wine are you using? 

```

wine --version

```Also, some pretty obvious, silly and basic questions, but what hardware are you using?  Does your graphics card need proprietary drivers that aren't installed?  Have you got Wine working with other programs on this same PC?

Thanks for help..
I'm using wine 1.2 stable and not working with any game i try to run:confused:
I have this graphic card: 
Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller

---

### Post by l32007 on 2010-09-22
Make sure you go to the [http://appdb.winehq.org/](http://appdb.winehq.org/) to check if the game is compatitble.

---

### Post by grobar87 on 2010-09-22
> **l32007 said:**
> Make sure you go to the [http://appdb.winehq.org/](http://appdb.winehq.org/) to check if the game is compatitble.

Thanks for that information.. :)

---

### Post by Lateralis on 2010-09-23
Yes, I did that for him l32007 and posted the relevent links.  It looks like that Fifa 08 played OK on older versions of Ubuntu with versions of Wine ~0.8, but I didn't see any reports for later versions of Wine or Ubuntu.

As for your problem grobar87, I think it should run. :/  At least I can't think of any reason off the top of my head why it wouldn't.  Sorry. :(

---

### Post by grobar87 on 2010-09-23
> **Lateralis said:**
> Yes, I did that for him l32007 and posted the relevent links.  It looks like that Fifa 08 played OK on older versions of Ubuntu with versions of Wine ~0.8, but I didn't see any reports for later versions of Wine or Ubuntu.

As for your problem grobar87, I think it should run. :/  At least I can't think of any reason off the top of my head why it wouldn't.  Sorry. :(

Ok,thanks for your help...i hope some game will run under my ubuntu:-|

---

### Post by beew on 2010-09-23
Keep a windows partition or buy another pc installed with windows if you must play windows games,--or you can try some native Linux games. I find wine to be unstable and flaky and it gives strange error messages even when things work,--so I can't really trust a program running in wine for anything serious. Good primarily for small utilities such as pdf viewers (which is useful as long as there is no alternative in Linux)

---

### Post by Lateralis on 2010-09-23
Actually, I use Wine for all sorts of stuff used for my work.  Good examples are Orgin8 (a sophisticated plotting package) and XPSpeak (data fitting software).  Spotify also runs perfectly fine in Wine.  

I've recently installed Neverwinter Nights using Wine as I can't play it in Windows anymore.  I know there is a native Linux client for Neverwinter Nights but installing it seems kludgy and has severe limitiations anyway.  In Wine it works nearly flawlessly.   

It is true that Wine hasn't always worked well in the past, but these Days I find it to be a very useful and stable asset that I couldn't be without.

---

### Post by beew on 2010-09-23
I would hope that there are more native Linux applications so that Linux users wouldn't have to rely on outdated, partially or sub-optimally functional windows apps. As long as that is the case I can't persuade others to try Linux. So I try not to use wine as much as possible,--yes, but I do use it for a few apps.

---

### Post by Lateralis on 2010-09-23
Yes, I wish there were more native games for Linux too, but the argument is a circular one.  Developers will only make games for Linux if there is a market for it.  That means there have to be a large body of Linux users that want those games.  Unfortunately, people won't switch to Linux without the games being available so don't switch so there's no large body of Linux users hungry for games.  

I do however dual bual boot, so that if I want to play games that I can't get to work nicely in Wine then I just simply switch OS.  Once I'm done I switch back.  Its not *real* hardship; just a minor inconvenience.

---

