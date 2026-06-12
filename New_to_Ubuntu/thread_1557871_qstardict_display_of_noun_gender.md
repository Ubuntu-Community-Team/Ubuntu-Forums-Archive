---
title: "qstardict display of noun gender"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by Chough39 on 2010-08-21
I am in the process of changing to Ubuntu (9.10) and am using QStarDict which I have downloaded using Synaptic Package Manager.
I am unable to see the noun gender, what do I need to do to acheive this please?

---

### Post by ENigma885 on 2010-08-21
What languages and dictionaries are you using?

---

### Post by Chough39 on 2010-08-21
Dictionaries used are:

	 	 stardict-babylon-Babylon_English_French-2.4.2
 

 stardict-babylon-Babylon_French_English-2.4.2

---

### Post by ENigma885 on 2010-08-22
Depending on my personal experience with all the Babylon-like dictionaries I have used in both Windows and Linux platforms, I recommend GoldenDict.
A masterpiece of art!!
It can load Babylon's dictionaries (.bgl) natively without any conversions. And it can also load Lingvo's dictionaries the same way. Not to mention Stardict's as well.
[[IMG]http://img594.imageshack.us/img594/8056/goldendict.th.png[/IMG]](http://img594.imageshack.us/i/goldendict.png/)

**[SIZE="3"]So, let's get to what u r going to do exactly![/SIZE]**
**01-** install GoldenDict 
from Synaptic Package Manager, or open a terminal window (*Application>Accessories>Terminal*) and paste 
```
sudo apt-get install goldendict
```
**02-**Make a folder anywhere u prefer and put the dictionaries u want to work with in it. (must be uncompressed)
**03-**Launch GoldenDict. And from the Edit menu choose Dictionaries.
In the Sources tab choose Files tab and click Add to browse to the directory where the uncompressed dictionaries are. 
**04-**The program will make a quick scan to index the dictionaries.

That's it!!:)

*******Considering the French dictionaries that u use, I don't recommend using them in Stardict format. As they are originally converted from .bgl, it's better to use them in their native format.

I have a couple of French Babylon dictionaries besides the ones u use. But I am doubtful if it's the proper place to share them especially that they are copyrighted and others have their own trademark like Larousse.
*So as a temporary solution, I will send u a link to download them in a _private_ message.*

You can also check [this link]("http://goldendict.org/dictionaries.php") for some additional resources. Some links are in Russian; u can use "Google translate" for the whole link.

---

### Post by Chough39 on 2010-09-20
Having consulted others and done a little research I summarise the answer to my problem by stating that different dictionaries contain different information (surprise surprise). Selecting the correct dictionaries for ones needs is essential, this applies to gender amongst other things. The dictionaries given below are excellent . Whilst QstarDict is a good dictionary a more versatile programme is GoldenDict which is available from the Ubuntu Software Centre. The  GoldenDict website should also be visited ([http://goldendict.org/](http://goldendict.org/))
 

 Larousse Chambers English-French
 Larousse Chambers français-anglais
 

 Larousse Compact English-French
 Larousse Compact français-anglais
 

 Larousse Multidico
 

 Wikipedia  
 

 GoldenDicts' forum also provides much usefull information.


I hope this will be of some use to others.


Chough39

---

