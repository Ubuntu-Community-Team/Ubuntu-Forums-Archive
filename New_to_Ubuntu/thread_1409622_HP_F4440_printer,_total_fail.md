---
title: "HP F4440 printer, total fail"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by JiuJitsu500 on 2010-02-17
Hey all, hate to sound like a total newbie again, but after a full day of searching every forum I could ([ubuntu forums]("http://ubuntuforums.org/search.php?searchid=70174355"), linux questions, and another one that gave a pretty good detail I can't find anymore... but failed anyway), I cannot get this printer to work at all. All it can do is copy, which is great, but obviously it doesn't need a computer to do that. The commands I ran after a download were a change of directory, then the .run, and continuing all the way to the end, and installing all the missing dependencies it mentioned, to the GUI, there no PPD is listed.

Anywho though I downloaded the 3.9.10 and 3.9.12 hplip and ran both, I forget which one first, at least two times each, and purged them again to make sure, and ran both again, but still a complete failure.

I get to a script after building and installing and it looks okay, and the GUI for HP Setup comes up (which now I can just go to through hp-setup in a  terminal).... but there are NO 4400 series printers listed at all in the PPD list, in either 3.9.10 or 3.9.12. Now is 3.9.12 installed, which should have it.... but no. There isn't even a DeskJet listing (though I'm not sure that matters???). The list skips from 4300 to 4500 series and has inkjet, laserjet, etc...

Its an HP Deskjet F4440 all-in-one again.... 

So short story long, anyone know where I can simply download the 4400 series PPD's so I can add them to the HP PPD list in my computer? Or is there some other epic failure I'm doing?

EDIT - Don't know if it matters at all, but I am running a 64-Bit....

Thanks in advance again.

---

### Post by JiuJitsu500 on 2010-02-17
WOW!!!!!!!!!!!!!!

Hey, everyone send me a virtual slap in the face, or kick to the no-no spot because I feel like a complete moron all the sudden.....

Turns out, everything was WAY okay, even scanning..... BUT, I forgot about BUM, and forgot now why I even had that.. but CUPS was turned off in it, and thusly, was never running... so I turned it back on and now everything works great.

Linux.... damn you..... confusing, but it's never very hard to fix. This time, I just really, really screwed myself.

---

