---
title: "Swscaner not working in feisty"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by A*p on 2007-06-28
I have just put feisty onto a new laptop and cannot get swscanner to work.  On my old laptop it would not work with feisty either so had to revert back to Edgy.  I suspect that the same will apply to my new laptop though I have not tested it yet.

Swscanner will launch fine but as soon as I start a scan the application will die.  Both laptops use the intel chipset, my old laptop uses ipw2000 and the new one ipw395.

Anyone else had this issue with feisty or know what the cause/fix is?

---

### Post by hops33n on 2007-07-23
Any update on this problem?  I have fiesty with intel 3945 and when I start a scan it errors out.  If there is no fix, does anyone know of another utility thats similar?  Thanks in advance.

---

### Post by A*p on 2007-07-23
I had to revert to edgy to get this working, which is most annoying, SWScanner is one of the most important tools for my job.  You should try compiling from source to see if that gets you any joy, this is something I am wanting to do but cannot afford any downtime with my laptop due to work, so I am waiting till I have some days free to try this.  I am hoping that the next ubuntu release will fix this but that may just be wishful thinking.

---

### Post by A*p on 2007-08-13
Just to update this has been listed as a bug in Launchpad and has been fixed in the SVN  here is what was said....

> 
 Ivan Forcada Atienza said on 2007-07-08: (permalink)

Hi all.

It's fixed on the SVN. You can check it out whenever you want.
Nevertheless, I don't plan to release a new version until KDE4 is out, when I will completely rewrite the GUI and there will be a lot of new features so for now I only plan to upgrade SVN version with bug fixes.

Regards.

> 
Jared Sutton said on 2007-07-08: (permalink)

Thanks for the update Ivan. I just built from SVN, and everything seems to be working well. :)


As a note I have not built this myself from subversion so I cannot comment, at this stage I will wait for Gutsy and give it a go then.  Just thought I would post this info should someone find it useful.

---

### Post by mateuszbaranski on 2008-01-23
> **A*p said:**
> 
Swscanner will launch fine but as soon as I start a scan the application will die.  Both laptops use the intel chipset, my old laptop uses ipw2000 and the new one ipw395.

Anyone else had this issue with feisty or know what the cause/fix is?

I have the same. It starts (in sudo) but it crashes after clicking START scan.
I have intel PRO/Wireless 2200BG card.

using kubuntu gutsy

---

### Post by bwtranch on 2008-01-23
There is this wrapper tool that I don't know much about. Sorry. It's kinda like the cupswrapper for printers, but I haven't got it to work yet. I wrote a How-To for the printer driver and once I get this to work I'll write about it. I got that stupid Brother driver to work and I think this is similar.

---

### Post by calraith on 2008-05-23
For what it's worth, I built a Hardy .deb of the SVN version of SWScanner.  [http://headcandy.org/rojo/swscanner](http://headcandy.org/rojo/swscanner)

---

