---
title: "Alternative to wine?"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-04
Hi,
what are some other (if not better) alternatives to wine?

Is anything going to be able to run Office 2007 and Adobe CS4 Master collection? (Photoshop Cs4 etc..)


Thanks!

---

### Post by skymera on 2009-03-04
Wine is basically it.

Crossover is good for office tools (It's just Wine underneath)
Cedega is good for games. (It's just Wine underneath)
Wine is good for most things with some settings fiddling (It's just Wine)

---

### Post by simtaalo on 2009-03-04
[http://www.codeweavers.com/products/](http://www.codeweavers.com/products/) 
crossover is the more "pro" app to use, its proprietary though, but they do filter stuff into the wine project AFAIK.

---

### Post by jaminux on 2009-03-04
If you are willing to look beyond compatibility layers you could try an emulator.

See the virtualiztion forum for more details.

At the moment I am install CS4 Master Collection in XP Professional x86-64 in VMware Workstation. I will tell you how it goes.

It prolly won't be suitable for doing HD content though unless you have a massive RAM...

---

### Post by handy on 2009-03-04
There are none.

There are a few Wine enhancements available that I know of.

[*_Codeweavers_*]("http://www.codeweavers.com/") make Crossover Office & Crossover Games.  Both of these are Wine based, & in actual fact the prime Wine coders work for Codeweavers.  We all need to eat.

Codeweavers are by far the prime corporate sponsor of Wine.

The Codeweavers Crossover people are very honest & if you deal with them, they don't give you spin.  Their dev's also watch their forums closely, replying & coding to solve problems as best they can & as soon as they can. 

Transgaming & it's Cedega offspring do not support Wine, though they have used some of the early Wine code before the license was changed.

Transgaming give very poor support no matter what the circumstances.

Sometimes things work on Cedega that won't work on any of the other Wine children.

It certainly pays to research here in the Wine forum to find out which of the 3 prime candidates supports your software best.

Though having said that, you will find that the Wine forum is somewhat biased towards straight Wine, & that ain't necessarily always the most efficient solution. ;)

---

### Post by jaminux on 2009-03-04
Update: I can run Adobe Photoshop on Ubuntu fine with VMware. It is slightly more annoying than running it natively, buy nevermind.

---

### Post by Ms_Angel_D on 2009-03-04
There is also [playonlinux]("http://www.playonlinux.com") which I've had great success running guild wars on, but it does install more than just games. I also use [wine-doors]("http://wddb.wine-doors.org/") to install a few applications.

---

### Post by Gp. on 2009-03-04
Hmm, well.

The main thing stopping me from using ubuntu as my full out primary os is the compatibility with things I need.


If I can get ubuntu to run the adobe CS4 suite, then I'll be with Ubuntu all the way....


Anyone know if it's possible? Will it be? How is it? lol

Thanks for the replies btw. Great help! =)

---

### Post by kanikilu on 2009-03-04
This may not be a practical or viable alternative depending on your situation, but if you have access to Windows XP or Vista installation media (and license), you could use virtualization.

Personally, I use VirtualBox, but a friend of mine swears by VMWare. I use it for Office 2007, Dreamweaver (although not so much anymore as I'm doing more web editing by hand), Active Directory administration, checking websites in other non-Linux browsers (IE, Safari, Chrome) and a number of other tasks that are either impossible, hard to do or sub-optimal under Ubuntu.

---

### Post by mlentink on 2009-03-04
> **Gp. said:**
> The main thing stopping me from using ubuntu as my full out primary os is the compatibility with things I need.


I don't want to be blunt, but what exactly is it in CS4 that you need? Is it proprietary file formats? 
You could try and get used to using the Gimp, Inkscape, Scribus and some other fine FOSS programs. 
But if you really absolutely have to use CS4 itself, then I'm afraid the best solution is to run it in Windows or OSX, either natively or virtualized. The latter would set you back the extra license fees, but if CS4 is a necessity, you won't mind.

---

### Post by handy on 2009-03-04
> **Gp. said:**
> Hmm, well.

The main thing stopping me from using ubuntu as my full out primary os is the compatibility with things I need.


If I can get ubuntu to run the adobe CS4 suite, then I'll be with Ubuntu all the way....


Anyone know if it's possible? Will it be? How is it? lol

Thanks for the replies btw. Great help! =)

Go to Codeweavers & have a look at their compatibility list?

I gave you their link in a previous post.

---

### Post by presence1960 on 2009-03-04
> **Gp. said:**
> Hi,
what are some other (if not better) alternatives to wine?

Is anything going to be able to run Office 2007 and Adobe CS4 Master collection? (Photoshop Cs4 etc..)


Thanks!

There are a number of Virtualization options. I ran Windows in Sun Virtual Box for a couple months. Only used Office Enterprise 2007 and Adobe Acrobat professional for work. Worked like a charm. Unfortunately when my DSL went on the fritz the techs either didn't know how or didn't want to work on a Linux box so I had to reinstall Windows to my hard disk. Sun Virtual box is free.

---

### Post by handy on 2009-03-05
In a previous post I answered the OP's thread title with a simple there are none.  Now that I think about it I was incorrect.

I was answering literally with regard to emulators that are not emulators. :)

I did not consider virtualisation at the time.

& 

There ***is*** actually another Wine competitor called [Win4lin]("http://win4lin.net/content/"), we don't hear much about that one, probably because you have to pay for it. :P

---

### Post by Gp. on 2009-03-05
So VirtualBox is the only thing that's going to get CS4 working in ubuntu? lol


I need dreamweaver, premiere, I need 3d studio max, I need a fair few windows programs, some of which don't run on wine.


Any alternatives to dreamweaver you guys know of?

---

### Post by SunnyRabbiera on 2009-03-05
Crossover might suit you, I like crossover as even though it its not free its developments go to wine.

---

### Post by cwsnyder on 2009-03-05
Unless you are open to using some of the FOSS equivalents, it sounds like you are going to be stuck in Windows.  It is similar to going to a Mac.  You can't expect to run all of your Windows applications on a Mac, either, unless you run Parallels or one of the other Virtual Machine host programs and actually install Windows as a Virtual Machine.

While you are converting over, you may want to consider dual-booting Windows and Ubuntu.  This does not allow you to easily switch environments, but Ubuntu can read all of the files on your NTFS partition.

---

### Post by insineratehymn on 2009-03-05
> **Gp. said:**
> So VirtualBox is the only thing that's going to get CS4 working in ubuntu? lol


I need dreamweaver, premiere, I need 3d studio max, I need a fair few windows programs, some of which don't run on wine.


Any alternatives to dreamweaver you guys know of?

The short answer is probably yes.

CS4 will not work right in Ubuntu until Adobe gets on the bandwagon. I have gotten Dreamweaver CS2 to install, but it was buggy at best. 

It sounds like you do some serious graphical arts... I would suggest Mac OSX to get you through the day, and if you really need to mess with Ubuntu then VM it (don't vm windows) and see how you like it. 

Just my two cents.

---

### Post by dmizer on 2009-03-05
> **Gp. said:**
> I need dreamweaver, premiere, I need 3d studio max, I need a fair few windows programs, some of which don't run on wine.
If you absolutely must have these programs, then you're stuck with Windows or OSX. It's really that simple.

If you use those graphical arts programs (especially 3D rendering) to their full abilities, you'll also find that virtualization won't be suitable for you either.

You may get some things to work in wine, but if you're using current versions of these programs, you'll probably find the interface to be buggy and unstable.

Edit:
If I may make a suggestion, if you're seriously interested in converting to Ubuntu, you'll need to be open to using different tools. Most of the previously mentioned programs (Gimp, Inkscape, Scribus, Open office) have Windows versions. Try using them more for smaller tasks. Instead of relying on MS Word for 100% of your documents, write drafts in OOo ... even if you dislike it at first. Same thing with Gimp. If you only need to touch up redeye in a photo, don't break out the big guns.

Make your transition more gradual, and wean your dependence on the proprietary stuff.

Edit edit:
Here's something for 3D: [http://aminesoft.wordpress.com/2009/03/04/7-awesome-3d-graphic-design-applications-for-linux/](http://aminesoft.wordpress.com/2009/03/04/7-awesome-3d-graphic-design-applications-for-linux/)

---

### Post by Ms_Angel_D on 2009-03-05
> **Gp. said:**
> I need dreamweaver, premiere, I need 3d studio max, I need a fair few windows programs, some of which don't run on wine.


Any alternatives to dreamweaver you guys know of?

On windows I used the latest version of Dreamweaver but to me there really wasn't much difference between it and Dreamweaver 8, and Dreamweaver 8 works great in wine. You can use wine-doors to install it.

Probably the one program I've found closest to Dreamweaver in functionality is Quanta Plus.

---

