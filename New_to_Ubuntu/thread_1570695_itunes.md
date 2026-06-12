---
title: "itunes"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by dan9686 on 2010-09-08
I have Wine downloaded but cannot extract Itunes. Any suggestions?

---

### Post by realzippy on 2010-09-08
> **dan9686 said:**
> I have Wine downloaded but cannot extract Itunes. Any suggestions?

itunes is a problem.Maybe it works partially in wine;someone may correct me please...

You need itunes for their drm stuff?
..for everything else there should be a alternative in  linux..

---

### Post by realzippy on 2010-09-08
Sorry,your question was how to extract?
Before running an .exe file in wine you have make it executable..
means open your terminal,navigate to that file and run

```
chmod +x yourexefile.exe
```

but,really cannot recommend installing itunes.

---

### Post by jlab on 2010-09-08
> **realzippy said:**
> Sorry,your question was how to extract?
Before running an .exe file in wine you have make it executable..
means open your terminal,navigate to that file and run

```
chmod +x yourexefile.exe
```but,really cannot recommend installing itunes.

so how do you navigate to your file in the terminal. I have this same problem

---

### Post by GaryTheCat on 2010-09-08
I got myself very stressed out trying to get iTunes to work in Wine and Playonlinux - I gave up and have a vista partition that I use for iTunes, TomTom and other niggly things that are too much hassle to get to work.

My solution is to have a partition accessible to windows and ubuntu so I can still get at my music library from either OS.

(I expect I'll get flamed for this lol)

---

### Post by jadedcritic on 2010-09-08
Last time I checked the Wine compat database, the current versions of itunes were not happening.   Personally, I wouldn't bother trying until if-when it AT least gets a bronze!  (It's currently rated "garbage", I think).

Well, either I'm missing critical information, or you're better off running Itunes in a virtual machine or a dual boot.

---

### Post by beew on 2010-09-08
> so how do you navigate to your file in the terminal. I have this same problem

Say you save your .exe file on the desktop, then you type
```
cd Desktop
```

In general you can replace "Desktop" with the path of the foder where your .exe file is.

But the easy way is simply to right click the .exe file, choose properties and go to the "permission" tab and set it to executable. I suppose it is easier to give instructions in command lines but it can be intimidating to beginners.

I agree with realzippy that itune just doesn't worth the troubles.

---

### Post by Jesus_Valdez on 2010-09-08
If you "really" need Itunes, go with a Virtual Machine or double boot.

If you just "want" Itunes, well, try the alternatives, I'm quite happy with Guayadeque, but you can try Songbird, or Rhytmbox, Amarok or any other.

---

### Post by sandyd on 2010-09-08
> **jadedcritic said:**
> Last time I checked the Wine compat database, the current versions of itunes were not happening.   Personally, I wouldn't bother trying until if-when it AT least gets a bronze!  (It's currently rated "garbage", I think).

Well, either I'm missing critical information, or you're better off running Itunes in a virtual machine or a dual boot.
meh.
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347)

weve had a breakthrough!!!
not really.

---

### Post by raysfan81 on 2010-09-08
I honestly would suggest trying an alternative.  I really dislike iTunes (I think its bloated and slow even in Mac OS X)  but I messed around trying to get it to install in wine but I gave up.  Either find something else that can do the same things or if you must a dual-boot would be a good idea.

---

### Post by sandyd on 2010-09-08
> **dan9686 said:**
> I have Wine downloaded but cannot extract Itunes. Any suggestions?
Since im pretty sure that Itunes is not exactly going to work on linux, let me tell you why you wont be able to play your itunes music on Linux either.

because of Apples Fairplay ([http://en.wikipedia.org/wiki/FairPlay](http://en.wikipedia.org/wiki/FairPlay)), it restricts the music to devices that can use Quicktime by encrypting the music.

If you want to simply transfer your music to ubuntu, and use it from there....

You can copy all your music to dvds and cds (from Itunes) and then simply play/rip those.
([http://en.wikipedia.org/wiki/FairPlay#Restrictions](http://en.wikipedia.org/wiki/FairPlay#Restrictions)).

---

