---
title: "open office is great but..."
date: 2009-06-29
forum: New to Ubuntu
---

### Post by powel212 on 2009-06-29
I love Open Office an I use it on all my machines but I run into problems in one small area.

When I launch the text editor basically nothing happens for a period of time no less than 4 seconds depending on the processor of the machine itself. My home machine is fast and I know if i launch it then in a couple seconds it will open and do exactly what I want it to do but...

I want more people to use it on the computers I build and maintain, (less than a hundred but quite a few). I install Ooffive on all the machines I build but nobody uses it but me. I think a big reason for this is because when you launch it it doesn't seem to do anything. And then finally opens.

I think it would be helpful for normal users if a small window opened as soon as you launch the program that lets the user know that the program is loading. I think this is pretty standard for most apps on most operating systems but seems to be missing in Open office.

If there is a switch I need to turn on in Ooffice please let me know so I can get more of my user base using it.

I love it but everybody else seems to be stuck on that MS shyte. Please help.

Powel

---

### Post by Nervouswreck on 2009-06-29
I never noticed the delay you mention with the word processor but did with dBase and Calc so I opened all 3 one after the other to test and sure enough Writer does have a loading window. Since you mention "MS shyte" maybe the windows version doesn't have it.

---

### Post by philinux on 2009-06-29
I'm using OO 3.0, as soon as you click the app a splash screen appears similar to the ubuntu loading one. No delay.

---

### Post by LowSky on 2009-06-29
Im with Phil, it opens within cliking and has a load screen.
Of course I'm using Arch Linux, so my milage might vary.

---

### Post by powel212 on 2009-06-29
I have "enable quickstart in taskbar" enabled in the Open office settings memory settings.

so I am launching it from the sys tray in jaunty.

The greatest lag time comes on the older systems I admin. for example we have several Pentium 1s and pentium 2s and these machines load Open office in over 60 seconds only. and no splash screen when launched from the taskbar "quick" launch icon

any recommendations?

Powel

---

### Post by decoherence on 2009-06-29
> **powel212 said:**
> I have "enable quickstart in taskbar" enabled in the Open office settings memory settings.

so I am launching it from the sys tray in jaunty.

The greatest lag time comes on the older systems I admin. for example we have several Pentium 1s and pentium 2s and these machines load Open office in over 60 seconds only. and no splash screen when launched from the taskbar "quick" launch icon

any recommendations?

Powel

You might install the 'preload' package, however this won't result in an immediate speed gain.

Hmm... actually that raises an interesting question. Anyone know if it would be possible to do an 'optimized' version of Ubuntu by re-mixing a system that has had preload running on it for a while? I guess preload is a per-user thing... any way to get it system wide?

---

### Post by LowSky on 2009-06-29
Ubuntu wasn't made to run on such old processors like pentium 1 and 2's, and niether was openoffice. People have to realise that older hardware cannot always run newer applications. Openoffice especially because it runs on java, which does take a good amount of resources to run. So if you get it to run at all I'm suprised

---

### Post by mcduck on 2009-06-29
Unless you really need the features that use Java, I recommend turning Java off in OpenOffice's preferences (Tools/Options/OpenOffice.org/Java).

Disabling Java will greatly reduce OO's startup time.

..and if you ever try to do something that would require Java, OO will ask you if you want to enable it again, so you're not even loosing anyhting if you do this.

---

### Post by powel212 on 2009-06-29
> Unless you really need the features that use Java, I recommend turning Java off in OpenOffice's preferences (Tools/Options/OpenOffice.org/Java).

That is a great suggestion. I did not know you could do that. 

Thank you.

Powel

---

### Post by philinux on 2009-06-29
On your older machine I would seek out an alternative to Oo. Abiword for instance for word processing. Much lighter on system resources.

---

### Post by powel212 on 2009-06-29
I'll give AbiWord another try. It is a nice little program but when I used it in the past I found when it outputted .doc files they were often not compatible with MS Word. This is important because if the folks at work run into the slightest problems when typing letters or opening documents they running screaming bloody murder to the high heavens. They are my bane and so I must make their lives as simple as possible.

arg...

Powel

---

