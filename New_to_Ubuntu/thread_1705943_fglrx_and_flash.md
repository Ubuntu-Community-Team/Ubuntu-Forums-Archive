---
title: "fglrx and flash?"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by adduds on 2011-03-13
i have fglrx driver installed if that's important 

my flash version: You have version 10,2,152,27 installed

certain not all flash videos flicker like crazy i don't know if its what people call video tear or what but an example of the player that does it is:

[http://www.imdb.com/features/hdgallery](http://www.imdb.com/features/hdgallery)

its really driving me nuts i read lots but can't really get a concise answer possibly flash? possibly video driver?

---

### Post by Vaphell on 2011-03-13
Tearing is when you get parts of 2 different video frames drawn at the same time and there is a noticeable line dividing them, especially annoying in fast changing sections of the video where the 2 sides of that border don't match hard. Flickering is more like blinking of the whole thing.

Definitions aside i think i know what you mean. I have 64 bit flash installed via flash-aid addon (Shockwave Flash 10.3 d162) and i had ungodly annoying flash flicker on youtube. I had to disable hardware acceleration in flash properties (though most flash elements have settings disabled in rightclick menu). Go to [http://derbauer.de](http://derbauer.de), right click on anything, go into 'settings' and disable hw acceleration - i don't think it does anything useful anyway in case of ATI cards (?). Maybe it will help.

---

### Post by adduds on 2011-03-13
thanks for the try did that didn't work :(

its only on certain sites [http://www.imdb.com/features/hdgallery](http://www.imdb.com/features/hdgallery)

is my example....a box in the middle shows up maybe this size

...
. .
...

right in the middle pure black it flickers

and the video progress bar flickers

at the bottom 1/4 of the video

youtubes fine

flash games are usually fine its only certain videos i noticed this site uses a jw player?

---

### Post by Vaphell on 2011-03-13
[http://www.imdb.com/features/hdgallery](http://www.imdb.com/features/hdgallery) works just fine on my box with 64bit beta flash and default catalyst driver.

recently many people reported problems with flash videos, most likely because adobe added hardware acceleration in latest versions. Check multimedia subsection of forums to see if there are valid workarounds for your issue.
Do you have 32 or 64bit system?

---

### Post by adduds on 2011-03-14
i have a 64bit ubuntu and the fglrx driver.....by default catalyst driver do you mean the radeon module?

i unchecked the hardware acceleration went back to that site and it still didn't work....maybe uninstall flash? and re-install it?

---

### Post by alphacrucis2 on 2011-03-14
Which version of fglrx are you running? The one from the Ubuntu repos or AMD's latest version (Catalyst 11.2).

---

### Post by adduds on 2011-03-14
> **alphacrucis2 said:**
> Which version of fglrx are you running? The one from the Ubuntu repos or AMD's latest version (Catalyst 11.2).

i did have amd's latest installed but i wasn't sure how to check to see what version was installed and am still new so i uninstalled it re-installed the ubuntu repo one....

when to ati one is installed to i have to remove the repo one before i install it? can i keep the same xorg.conf? should maybe i try to install the new one?

ps. when i install the ati driver how do i:

a. check to see what version i have 

b. uninstall it properly?

---

### Post by Vaphell on 2011-03-14
install flash-aid addon for firefox and try 64bit version of flash (flash-aid automates installation and removing of conflicting packages and stuff). If 64bit won't work you can always revert to repo version.
no help with gfx driver here, sorry - i go with repo catalyst so i don't know the details and caveats of manual installation.

---

### Post by adduds on 2011-03-14
> **Vaphell said:**
> install flash-aid addon for firefox and try 64bit version of flash (flash-aid automates installation and removing of conflicting packages and stuff). If 64bit won't work you can always revert to repo version.
no help with gfx driver here, sorry - i go with repo catalyst so i don't know the details and caveats of manual installation.

NICE I installed the flash aid addon (sorry vaphell you did mention it earlier but it didn't click that it was a firefox addon) it installed it advised me of a 64bit update checked out that site and it runs perfectly now! thanks muchly!!!!

manual of the driver is really easy download

chmod +x ati_latestdriver_etc.run
./ati_latestdriver_etc.run

that's it follow install gui windows....although untinstalling i'm not entirely sure about hehehe but thanks again

---

### Post by Vaphell on 2011-03-16
yes, i know it's that easy but i think that driver stops being under the control of package manager and you have to micromanage in case of kernel upgrades. I couldn't be bothered with that :)

---

### Post by adduds on 2011-03-16
exactly why i nuked it from my comp i'm kinda spoiled with the repos now hehehehe

---

