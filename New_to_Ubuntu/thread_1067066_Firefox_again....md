---
title: "Firefox again..."
date: 2009-02-11
forum: New to Ubuntu
---

### Post by Leo Dragonheart on 2009-02-11
My Fire Fox browser should be named Fire Snail browser... I don't know what i did or did not do but it is taking me 20 to 45 seconds or longer to load pages I have visited many times... Please help me at least get it up to the pace of a Turtle, then I will rename it Fire Turtle...lol

---

### Post by unixeducation on 2009-02-11
Have you tried using a different browser on the same machine (maybe Opera) to see if the problem is limited to Firefox?

---

### Post by Leo Dragonheart on 2009-02-11
> **unixeducation said:**
> Have you tried using a different browser on the same machine (maybe Opera) to see if the problem is limited to Firefox?

Yes I have tried Opera and I can't use it because when I go to my Myspace page it bunches all the words up so I can't read them... I have tried a couple of others but they just don't have features I like...

---

### Post by Kellemora on 2009-02-11
Hi Leo

I loaded the System Monitor into the upper Panel so I could keep an eye on my CPU usage.

Sometimes, Firefox decides it's going to HOG 100% of the CPU and it slows down to slower than a SLUG.  A snail could beat it hands down!

Closing and opening Firefox again, often returns it to it's normal low CPU usage.  Except for intensive web sites with 85 to 100 ads to download, hi hi...........

If I completely open System Monitor usage jumps up to 18% WHILE firefox is open and running, but the panel monitor for same only uses about 2 to 3% CPU.

But I have noticed that once it starts eating the CPU, it don't quit until you shut firefox down and restart it again.

Not a cure, but can help speed up those pages when firefox goes on a Longshoreman's holiday.

TTUL
Gary

---

### Post by unixeducation on 2009-02-11
What I meant by the Opera question was whether the speed issue was duplicated in other browsers, or whether it was just limited to Firefox. You may want to check what version of Flash you have installed (Flash 10 is now native for Linux systems, and available in the repositories), since that has given me issues in the past.

---

### Post by Leo Dragonheart on 2009-02-11
> **unixeducation said:**
> What I meant by the Opera question was whether the speed issue was duplicated in other browsers, or whether it was just limited to Firefox. You may want to check what version of Flash you have installed (Flash 10 is now native for Linux systems, and available in the repositories), since that has given me issues in the past.

Yes I do have the flash plugin for firefox installed, and no Opera runs fine except for that one problem I would use Opera. I like it better than fox.

---

### Post by kansasnoob on 2009-02-11
Well, I have a couple of thoughts!

First, Flash in Linux is a power hog! Of course it's also necessary. Assuming you're already using Flash 10 then be sure you have Flashblock 1.5.7 or 1.5.8 installed. It only replaces the Flash objects with a "button" and reduces CPU & RAM usage.

Second, the Mozilla build of Firefox brings with it the latest updates much sooner (including Add-ons). One of the first things I do after installing Ubuntu is to install Ubuntuzilla and then use it to install the official Mozilla build of Firefox:

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

I've done some pretty extensive testing on the newest Ubuntuzilla, beginning with post #66 here:

[http://ubuntuforums.org/showthread.php?t=467724&page=7](http://ubuntuforums.org/showthread.php?t=467724&page=7)

And it's simple! Just install Ubuntuzilla, double click the icon/folder and then run in terminal:

```
ubuntuzilla.py -a install -p firefox

```

After answering a few simple questions you'll have the official Mozilla build of Firefox.

---

### Post by Leo Dragonheart on 2009-02-11
> **kansasnoob said:**
> Well, I have a couple of thoughts!

First, Flash in Linux is a power hog! Of course it's also necessary. Assuming you're already using Flash 10 then be sure you have Flashblock 1.5.7 or 1.5.8 installed. It only replaces the Flash objects with a "button" and reduces CPU & RAM usage.

Second, the Mozilla build of Firefox brings with it the latest updates much sooner (including Add-ons). One of the first things I do after installing Ubuntu is to install Ubuntuzilla and then use it to install the official Mozilla build of Firefox:

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

I've done some pretty extensive testing on the newest Ubuntuzilla, beginning with post #66 here:

[http://ubuntuforums.org/showthread.php?t=467724&page=7](http://ubuntuforums.org/showthread.php?t=467724&page=7)

And it's simple! Just install Ubuntuzilla, double click the icon/folder and then run in terminal:

```
ubuntuzilla.py -a install -p firefox

```

After answering a few simple questions you'll have the official Mozilla build of Firefox.

Thanx for the info. I will give it a try. I would have gotten back to you sooner but my fox was taking a nap...:(

---

### Post by ajgreeny on 2009-02-11
Another thing worth looking at is the extensions you have installed for firefox, some of which can cause problems.  Try disabling them all in the **Tools > Add-ons** menu dialog box, then enabling them one by one.  It may give you a clue.

If that is no help, try renaming your **~/.mozilla** folder to **~/.mozilla.backup** and then restart firefox.  If that is the answer, you can then put back all your bookmarks by copying back to the new profile the **places.sqlite** file in your old profile, but I would avoid everything else, as that may put back the problem again, and you'll be back where you started.

---

### Post by Artemis3 on 2009-02-11
Try this: [http://www.getdeb.net/app/Midori](http://www.getdeb.net/app/Midori)

As for firefox, when in system monitor, see if there is an evil process called npviewer.bin This is the proprietary flash plugin, which often causes slowdowns and lockups; you might discover Firefox coming back to life after killing this.

Be sure to use the Adblock Plus plugin to mitigate this. There is also a flashblock plugin which lets you choose which flash to play. Sometimes flash decides to not work on itself, in that case restart Firefox.

---

### Post by kansasnoob on 2009-02-11
> **ajgreeny said:**
> Another thing worth looking at is the extensions you have installed for firefox, some of which can cause problems.  Try disabling them all in the **Tools > Add-ons** menu dialog box, then enabling them one by one.  It may give you a clue.

If that is no help, try renaming your **~/.mozilla** folder to **~/.mozilla.backup** and then restart firefox.  If that is the answer, you can then put back all your bookmarks by copying back to the new profile the **places.sqlite** file in your old profile, but I would avoid everything else, as that may put back the problem again, and you'll be back where you started.

Very true, I hadn't thought of that! You can certainly, very easily, disable different add-ons from the Tools menu!

Come to think of it I'm a "tool" that malfunctions from time to time:)

---

### Post by kansasnoob on 2009-02-11
> **Artemis3 said:**
> Try this: [http://www.getdeb.net/app/Midori](http://www.getdeb.net/app/Midori)

As for firefox, when in system monitor, see if there is an evil process called npviewer.bin This is the proprietary flash plugin, which often causes slowdowns and lockups; you might discover Firefox coming back to life after killing this.

Be sure to use the Adblock Plus plugin to mitigate this. There is also a flashblock plugin which lets you choose which flash to play. Sometimes flash decides to not work on itself, in that case restart Firefox.

Also an excellent suggestion! I seldom use Adblock because I know that some sites I visit rely on revenue from ads to stay free, but if the system won't handle all the ads opening then that's a good idea!

---

### Post by mkvnmtr on 2009-02-11
I think ad blocker and no script will help some. Also Firefox checks for bad sites that might harm your computer. The list is very lkong and it is using resources and time to run through the list every time you click. You can disable some of this in tools and still be safe. that should help some also. Firefox just uses a lot of resources and always seems to take some tinkering.

---

### Post by Leo Dragonheart on 2009-02-11
Thank you all for your replies. I was not able to download the Ubuntuzilla or the Matori because when it went to load them gdebi said I was missing something, a libst??++5 for the Ubuntuzilla and something along the same lines for the Matori. But thanx again for your advise. I just disabled all the extentions and pulg ins and such and now it seems to work better...

---

