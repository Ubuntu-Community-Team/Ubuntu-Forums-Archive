---
title: "alternatives of Illustrator, InDesign, Dreamweaver for web design"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by Sunrise 3388 on 2009-11-17
I want to learn about web design: upload & constantly changing photos, update the contents, leave comments & more...  My friend says I need Adobe Photoshop, Illustrator, InDesign, Dreamweaver.  I have GIMP.  Would anyone please tell me what are the Linux alternatives of Illustrator, InDesign, Dreamweaver?  Please put links for me to download.   I'm determined to learn although I'm a newbie.  What else do I need beside a brain & cups of tea?

I'm running Ubuntu Studio 9.10/ Ubuntu 9.10
Hard wares: 4 AMD 2.3 Ghz Phenom 9650 Quad-core processor, 8 G Ram, 1T & a 500 G hard drives. ATI hd3850 video card  with 512 megs of dedicated ram. 
  
I'd greatly appreciate any suggestions :)
Thank you in advance!

---

### Post by etali on 2009-11-17
One of the best places I've found to look for open source alternatives to popular software is:

[http://www.osalt.com/](http://www.osalt.com/)

I don't use Illustrator or InDesign, so I don't know how good the alternatives to those are on Ubuntu, but hopefully you'll find something that works for you.

---

### Post by Sunrise 3388 on 2009-11-17
Thank you very much.  What do you use to design web pages?

---

### Post by swisscow on 2009-11-17
Kompozer. Once you get the hang of it great for learning how web pages work

---

### Post by SeanHodges on 2009-11-17
Personally, I learned using a text editor (like gedit) and various resources like books and the Web. But there are some who prefer a more point-and-click approach (particularly if they are more of a casual Web designer, who wishes to learn as a hobby).

I've heard good things about "Nvu" ([http://net2.com/nvu/screenshots.html](http://net2.com/nvu/screenshots.html)), if you'd prefer a more Dreamweaver-like approach to Web design. You can always experiment with other alternatives later.

---

### Post by Sunrise 3388 on 2009-11-17
Thank you, guys.

---

### Post by peace.gangsta on 2010-01-27
I have used Dreamweaver , Illustrator ,Photoshop to contribute to some really wonderful web pages. So now I am used to that environment.Using the linux counterpart will be a fresh start  again which I dont  need.
So cant we use wine to run all these sfowares on ubuntu??
I found Photoshop much better than GIMP , but I found Ubuntu even more better than Windows. Help me out ...

---

### Post by SeanHodges on 2010-01-27
> **peace.gangsta said:**
> I have used Dreamweaver , Illustrator ,Photoshop to contribute to some really wonderful web pages. So now I am used to that environment.Using the linux counterpart will be a fresh start  again which I dont  need.
So cant we use wine to run all these sfowares on ubuntu??
I found Photoshop much better than GIMP , but I found Ubuntu even more better than Windows. Help me out ...

Of course you can: if you really don't want to support open-source software, and you're happy to troubleshoot potential problems when running Windows software in a platform it was not designed for. Take a look at the AppDB site to find out how compatible your software is in Wine:

[http://appdb.winehq.org/](http://appdb.winehq.org/)

Now I'm a big advocate of Wine, but I hate to see it used simply because people think it's a way of cutting corners when switching from Windows. Wine is some great software, but never expect things will just work without tinkering. 

My suggestion is to try the open-source alternatives first. Some suggestions to try:

[LIST]
[*] Photoshop: [http://www.gimp.org/](http://www.gimp.org/) (install by clicking [here]("apt://gimp"))
[*] Dreamweaver: [http://net2.com/nvu/](http://net2.com/nvu/) (install by clicking [here]("apt://nvu"))
[*] Illustrator: [http://www.inkscape.org/](http://www.inkscape.org/) (install by clicking [here]("apt://inkscape"))
[/LIST]

If they don't work for you then perhaps try running your Adobe software in Wine, but don't spend too long messing around with it. 

If neither approach works out for you, you need Windows. Dual-boot or install Windows in a virtual machine, there are plenty of instructions in the Ubuntu documentation on how to do either of these. 

Ultimately, you need your computer to make you productive. Ubuntu is a tool, just like Windows is. You have to use the tools that work for your needs.

---

### Post by peace.gangsta on 2010-01-27
First of all thanks a lot for the info.
> **SeanHodges said:**
> Of course you can: if you really don't want to support open-source software, 
Of course I support open source but I am used to the interface on the windows counterpart of these softwares. In fact , my support rose by the time I have already learned  to design web pages and related stuffs using these softys. That is why I wondered if wine could suffice.

---

### Post by SeanHodges on 2010-01-27
> **peace.gangsta said:**
> First of all thanks a lot for the info.

Of course I support open source but I am used to the interface on the windows counterpart of these softwares. In fact , my support rose by the time I have already learned  to design web pages and related stuffs using these softys. That is why I wondered if wine could suffice.

I worded that badly. I meant if you do not intend to support the open-source alternatives of the software you are looking for, rather than all open-source in general.

---

### Post by bodhi.zazen on 2010-01-27
> **peace.gangsta said:**
> I have used Dreamweaver , Illustrator ,Photoshop to contribute to some really wonderful web pages. So now I am used to that environment.Using the linux counterpart will be a fresh start  again which I dont  need.

I know this is probably not what you want to hear, but now that you are familiar with web pages I respectfully suggest you actually "start over".

Personally , I really like Bluefish. Bluefish automates much of the coding and generates much cleaner pages then the WYSIWYG editors.

If you wish to view your pages, open them with Firefox or opera or as many browsers as you have installed to see how the pages are actually rendered.

If you are willing to follow this advice I think you will find you are not really "starting over" as much of the html/css/php markup will make sense to you (you did say you know how to generate web pages already, so you should have a solid foundation) and your code will be much cleaner.

> So cant we use wine to run all these sfowares on ubuntu??
I found Photoshop much better than GIMP , but I found Ubuntu even more  better than Windows. Help me out ...

Linux is not a drop in replacement for Windows and the Photoshop developers have not released the code or binaries that run on Linux and the wine developers have not been able to build a compatibility layer.

IMO, if you really want to run photoshop you should either dual boot or better run Windows in Ubuntu via VirtualBox.

for example : 

[https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)

---

### Post by peace.gangsta on 2010-01-28
> **bodhi.zazen said:**
> I know this is probably not what you want to hear, but now that you are familiar with web pages I respectfully suggest you actually "start over".

Personally , I really like Bluefish. Bluefish automates much of the coding and generates much cleaner pages then the WYSIWYG editors.

If you wish to view your pages, open them with Firefox or opera or as many browsers as you have installed to see how the pages are actually rendered.

If you are willing to follow this advice I think you will find you are not really "starting over" as much of the html/css/php markup will make sense to you (you did say you know how to generate web pages already, so you should have a solid foundation) and your code will be much cleaner.

I get your point and well now i have decided to really "start over" without any more fuss.I was a bit sheepish.I think i can make my way through the open source softwares easily since I have the 'basics'.
Thanks a lot for the advice..
Really helped me make my mind up :D

---

### Post by andrew.46 on 2010-02-12
Hi bhodi.zazen,

> **bodhi.zazen said:**
> If you are willing to follow this advice I think you will find you are not really "starting over" as much of the html/css/php markup will make sense to you (you did say you know how to generate web pages already, so you should have a solid foundation) and your code will be much cleaner.

I could not agree more and I would suggest some time spent in the many html usenet groups would also be time well spent: comp.infosystems.www.authoring.html and comp.infosystems.www.authoring.stylesheets would be an excellent start.

> IMO, if you really want to run photoshop you should either dual boot or better run Windows in Ubuntu via VirtualBox.

Which gives me an opportunity to add in a gratuitous screenshot showing photoshop running in a vm on my own system :). I will confess I have found, like many others I suspect, that photoshop is a bit of overkill for web development.

All the best,

Andrew

---

### Post by charlieangles on 2010-02-17
> **Sunrise 3388 said:**
> I want to learn about web design: upload & constantly changing photos, update the contents, leave comments & more...  My friend says I need Adobe Photoshop, Illustrator, InDesign, Dreamweaver.  I have GIMP.  Would anyone please tell me what are the Linux alternatives of Illustrator, InDesign, Dreamweaver?  Please put links for me to download.   I'm determined to learn although I'm a newbie.  What else do I need beside a brain & cups of tea?

I'm running Ubuntu Studio 9.10/ Ubuntu 9.10
Hard wares: 4 AMD 2.3 Ghz Phenom 9650 Quad-core processor, 8 G Ram, 1T & a 500 G hard drives. ATI hd3850 video card  with 512 megs of dedicated ram. 
  
I'd greatly appreciate any suggestions :)
Thank you in advance!

I think you must visit the site W3shcools.com. There you will find the excellent stuff related to the Adobe Photoshop, Illustrator, InDesign, Dreamweaver. In that site, There are some excellent tutorials and practicals which will help you in learn all the subjects related to the web design.

---

### Post by woodmaster on 2010-02-17
Photoshop has been running in WINE on my system flawlessly with no tinkering.  I use Seamonkey Composer for web design like> [www.thefallfrolic.com]("http://www.thefallfrolic.com") .  This page was made with SeaMonkey for Linux

---

