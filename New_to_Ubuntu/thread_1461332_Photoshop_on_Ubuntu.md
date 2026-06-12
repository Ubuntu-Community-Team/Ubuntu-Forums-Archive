---
title: "Photoshop on Ubuntu"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by orphanlast on 2010-04-24
I've done a variety of tutorials to see about getting Photoshop to work on my computer. I need photoshop because I no only do quite a bit of professional quality work, but I'm going to try my hand out on some freelance Graphic Design.

I have wine on my computer and it seems like one frustrating program.

From the tutorials I've gone through, they state that I'm supposed to get a file called atmlib.dll and place it in the system32 folder, then place atmlib.dll in a library under "configure wine"...

I've really had no success at all in getting photoshop to work on my computer, but after I followed the instructions I at least got the computer to make believe as though it were opening flash. It popped up some weird logo then it dissipated. When I'd click on the photoshop icon again, it would just tell me that photoshop was already running... when it wasn't.

I DO have virtualbox, but that thing runs so amazingly slow. I'm not sure if it's even worth my time. Especially since the screen is very small and I can't seem to make the screen full sized. And Windows Vista is already giving me a lot of problems on it.

Does anyone know of a good way to get photoshop onto Ubuntu?

---

### Post by QIII on 2010-04-24
Photoshop will not run natively in Linux.  It is designed for Windows.

You may find that your virtual machine will run more quickly if you open VirtualBox, select the virtual machine for Vista and change some settings.

Give the machine 2048MB of RAM, at least two virtual processors (if you have a multi-core machine) and bump the display memory up to the (anemic) max of 128MB.

To get a better screen size and some nicer integration features (such as resizing, full screen mode, etc), open the machine and start Vista.  When it is running, click on "Devices" and "Install Guest Additions".

---

### Post by VeeDubb on 2010-04-24
Another option, which may or may not work for you in terms of functionality, is to use an older version of photoshop.

Photoshop 7, which I believe was the last version before they switched to the "CS" naming, works beautifully under wine.

You'd hardly even know you weren't running it natively, and for many people, it has all the functionality you need.

---

### Post by ddecator on 2010-04-24
While Photoshop is not currently supported on Linux, Canonical is interested in working with Adobe to have it potentially be supported sometime in the (hopefully near) future. Unfortunately, there is not much you can do to make it work on Ubuntu in the immediate future, other than what QIII suggested.

---

### Post by cespinal on 2010-04-24
I soooooooooo wish we could have the CS suite ported to linux... now THAT would make a huge difference..

---

### Post by WinterWeaver on 2010-04-24
"A good designer is not limited by his/her tools, but by their mind"... try Gimp, though not as fully featured as photoshop, it works well (except if you want to do Print Design, due to lack of CMYK support)

EDIT: Please don't misunderstand, I'm not saying: "use gimp, not photoshop". I used older versions of photoshop via Wine in the past, and it worked well, except for issues I had with Fonts.

---

### Post by QIII on 2010-04-24
Just by way of example, here is a screenshot of Fedora running in VirtualBox on my Lucid machine.  With Guest Addions installed, this fills a full screen on one of my 23" monitors.

---

### Post by orphanlast on 2010-04-24
> **WinterWeaver said:**
> "A good designer is not limited by his/her tools, but by their mind" 

Whoever said that was probably talking about pens pencils and a paintbrush. I've tried gimp. It doesn't have vector masks. This means that you're forced to obliterate and mutilate pixels. And the Imorph filter is not a satisfactory means to morph an image. This isn't just a matter of a limited imagination we're talking about, practicality. My imagination does just fine under gimp. But saying that tools don't limit ingenuity but it's actually the mind... it's kind of like saying that if aborigines in Australia wanted to become industrial and reinvent the wheel while doing it and if they can't keep up with our modern technology in America while doing it -- it's just because their minds are not creative enough. I'm sure those aborigines would become industrial, but it's more than mind over matter here. 

 Masking makes it possible for a client to come back, request five or six small but substantial differences with the project you did for them, two months ago, and prevent you from needing to do the project all over again. Instead it speeds you up in making a few minor alterations and "done".

[/quote] ... try Gimp, though not as fully featured as photoshop, it works well (except if you want to do Print Design, due to lack of CMYK support) [/quote]

Some of the freelance work I'm going to be doing is also going to deal in screen printing. So I'm also going to need to work Illustrator as well.

---

### Post by orphanlast on 2010-04-24
Sounds like the only practical way to make any industry standard program to work on Linux is indirectly through virtualbox. Fortunately the founder of Ubuntu is saying that in two years this sort or irritation is going to disapear.

---

### Post by QIII on 2010-04-24
Bear in mind that the "industry standard" applications are designed by commercial interests who target their products at where the money is.  That means they write them for Windows.

Windows does not support anything but what Microsoft produces.  It's the other way around.

Hardware OEMs and software developers strive to make their products work with Windows.  They spend a lot of time and effort getting the vaunted Redmond Seal of Approval (take a look at my profile.)

That the products do not work on Linux is no indictment of Linux.

Those "industry standard" products, so long as they are proprietary, will not work on Linux until and unless the people who produce them port them to Linux.

---

