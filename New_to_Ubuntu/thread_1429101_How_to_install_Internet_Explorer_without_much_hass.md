---
title: "How to install Internet Explorer without much hassle?"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by oingk on 2010-03-13
Hi  

New to Ubuntu & Linux  
Can I install MS Internet Explorer on my computer without much hassle?  
Before you think I'm a pervert, I want to do this so that I can check how the website I am building shows on IE.  

Thanks

---

### Post by OldMerovingian on 2010-03-13
> **oingk said:**
> Hi  

New to Ubuntu & Linux  
Can I install MS Internet Explorer on my computer without much hassle?  
Before you think I'm a pervert, I want to do this so that I can check how the website I am building shows on IE.  

Thanks

You could try to install it in wine.

---

### Post by appier on 2010-03-13
Two ways I know of to do it--none without much hassle.  The first, most preferable, would be to install Windows inside a virtual machine, then install IE inside the virtual machine.  The second is to install IE inside WINE--worked, but never quite right.

---

### Post by nmaster on 2010-03-13
if you have windows then you could use virtualbox

---

### Post by oingk on 2010-03-13
> **appier said:**
> Two ways I know of to do it--none without much hassle.  The first, most preferable, would be to install Windows inside a virtual machine, then install IE inside the virtual machine. 


What do you mean when you say inside a "virtual machine"?

---

### Post by oingk on 2010-03-13
> **neal.m.master said:**
> if you have windows then you could use virtualbox

What do you mean "if I have windows" ?

---

### Post by qwerty2009 on 2010-03-13
using virtual box you can have a linux or windows machine running whilst in ubuntu

---

### Post by wojox on 2010-03-13
[Install Internet Explorer under Linux]("http://www.cyberciti.biz/tips/how-to-install-internet-explorer-on-linux.html")

---

### Post by lovinglinux on 2010-03-13
> **oingk said:**
> Before you think I'm a pervert, I want to do this so that I can check how the website I am building shows on IE.

Use [http://browsershots.org/](http://browsershots.org/)

---

### Post by The Real Dave on 2010-03-13
> **oingk said:**
> What do you mean when you say inside a "virtual machine"?

Vritualbox creates a virtual computer, running as a program on Ubuntu. Within this virtual computer, you can install other operating systems.

For example, you could install Windows (just as you would install it on a computer) in the virtual machine. Because this virtual machine runs as a program, on top of Ubunut, it won't have the same performance as if you just had it natively installed on your computer. However, as far as Windows knows, it's installed on a real computer, not a virtual one.

To install Windows in a virtual machine, you will need a Windows install disk, and will have to go through giving it a key, activation etc, just as you would if you installed it on a real computer.

EDIT: Heres a nice explanation and guide :)
[http://lifehacker.com/5204434/the-beginners-guide-to-creating-virtual-machines-with-virtualbox]("http://lifehacker.com/5204434/the-beginners-guide-to-creating-virtual-machines-with-virtualbox")

---

### Post by oldsoundguy on 2010-03-13
The real question is WHY?  Firefox, Opera and Google Chrome are far superior to IE .. especially within Linux.

You can even make Firefox work on most Windows Centric sites (those that use IE only (DUMB!!) by installing "user agent switcher" from the Mozilla add-ons.

---

### Post by drs305 on 2010-03-13
> **oingk said:**
> Hi  

New to Ubuntu & Linux  
Can I install MS Internet Explorer on my computer without much hassle?  
Before you think I'm a pervert, I want to do this so that I can check how the website I am building shows on IE.  

Thanks

There is a site called IEs 4 Linux that simplifies installing wine and IE. I've used it a few times and it is pretty straightforward. The downside is it is for IE 6 and you would want a later version for viewing your web design results. I noticed there is a beta version link available at the top right of the page, so you might want to check that out.
[http://www.tatanka.com.br/ies4linux/page/Installation]("http://www.tatanka.com.br/ies4linux/page/Installation")
The beta page says it currently only uses the 7 engine but states that is helpful for web testing, so it may do.

---

### Post by lovinglinux on 2010-03-13
> **oldsoundguy said:**
> The real question is WHY?  Firefox, Opera and Google Chrome are far superior to IE .. especially within Linux.

You can even make Firefox work on most Windows Centric sites (those that use IE only (DUMB!!) by installing "user agent switcher" from the Mozilla add-ons.

Read the OP post again. Is for testing a site under development, not for regular use.

---

### Post by oingk on 2010-03-13
Trying to follow youre suggestions. It seems a bit difficult but I'll manage, I think.

Thank to all of you for your help, you gave me some very good information.

---

### Post by Sir Jasper on 2010-03-13
Hi,

If you have difficulty, then if you can install Wine-Doors you can use it to install IE6 and also ActiveX if you need that as well.

I think, though I&#7743; not totally sure, that within within the last few months it was carlee who explained how to install IE8. If you use the search box (above right) do not enter anything but click Go,and then in the top left hand box try typing IE8 (or, ie, or internet explorer) and type carlee on the Posts By box on the right.

My regards

---

### Post by d3v1150m471c on 2010-03-13
Why would you install IE? Use winetricks on wine.
```

wget http://www.kegel.com/wine/winetricks
sh winetricks

```
IE is listed in there as an abbreviation. Cannot remember exactly which one.

---

### Post by achase79 on 2010-03-13
you can also use playonlinux to download and install IE6 or 7 and various other programs for wine.

---

### Post by Sir Jasper on 2010-03-13
Hi again,

Having read the post above by d3v1150m471c and having just googled Winetricks it seems you can have IE6 or 7 and many other options if you use Winetricks with the latest version of Wine.

Do return and let us know how it went and which method you used.

My regards

---

### Post by wilee-nilee on 2010-03-13
Here is a link to a site owned by one of the mods that is quite helpful. This link will show a install of Ie4 with wine on up to 9.04. I suspect this will work in karmic though.
[http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux)

---

### Post by oldsoundguy on 2010-03-13
All this about installing IE 4, 5. 6 is fine as it can be done .. but since there is no longer support for any of those and most sites (Google being the biggest example) will no longer support anything but 7 & up.

So using IE 4 to check web design would be useless since it is not in USE by enough people to be viable. 

And what about Safari?  Is the design work to be checked against it also?

---

### Post by oingk on 2010-03-20
> **Sir Jasper said:**
> Hi again,

Having read the post above by d3v1150m471c and having just googled Winetricks it seems you can have IE6 or 7 and many other options if you use Winetricks with the latest version of Wine.

Do return and let us know how it went and which method you used.

My regards

Hi.
I have installed Wine a few days ago. Today after reading here I followed d3v1150m471c's suggestion and selected IE6 and 7.

Now it seems that they have been installed. Then I.E. fired up by itself, and I used it (it worked :)), but then the terminal gave me a warning saying "Extraction Failed: Unable to find volume for file extraction. Please verify that you have proper permissions".

What does this mean?

---

### Post by oingk on 2010-03-20
Also, IE7 started up by itself now (apparently previous on was IE6).

Now Windows is asking me what OS do I use, there's the following choices:
-Windows XP service pack 2
-Windows XP Pro x64 Edition
-Windows Server 2003 x64 Edition
-Windows SEver 2003 SP1 or SP2
-Windows server 2003 ia64 edition

What should I chose?

---

### Post by Dayofswords on 2010-03-20
> **oingk said:**
> 
Before you think I'm a pervert
I cant figure out a reason why we'd think this

---

### Post by oingk on 2010-03-20
I messed up at that part, when I didn't know what to do I just closed the window.

If I try to find the file via Wine, (the file is IEXPLORE.EXE) and I click on it, it comes up with "an error occured while loading the archive" and gives me a "command line input" (I can copy paste for you if you want).

Don;t know what's going on. How do I launch IE now I've (or I think I have) installed it?

I'll go back to studying and check back later, hopefully someone can help.

---

### Post by oingk on 2010-03-20
OK basically the command line it gives me is this:

> [FONT=Courier New]Archive:  /home/user/.wine/dosdevices/c:/Program Files/Internet Explorer/IEXPLORE.EXE
[/home/user/.wine/dosdevices/c:/Program Files/Internet Explorer/IEXPLORE.EXE]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /home/user/.wine/dosdevices/c:/Program Files/Internet Explorer/IEXPLORE.EXE may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /home/user/.wine/dosdevices/c:/Program Files/Internet Explorer/IEXPLORE.EXE or
          /home/user/.wine/dosdevices/c:/Program Files/Internet Explorer/IEXPLORE.EXE.zip, and cannot find /home/user/.wine/dosdevices/c:/Program Files/Internet Explorer/IEXPLORE.EXE.ZIP, period.[/FONT]

---

### Post by HermanAB on 2010-03-20
Hmm, probably the easiest way to install Windows software on Linux is by purchasing a copy of Codeweavers Crossover.  Their wizards are easy to use and installing Windows software into different bottles is a snap.

---

