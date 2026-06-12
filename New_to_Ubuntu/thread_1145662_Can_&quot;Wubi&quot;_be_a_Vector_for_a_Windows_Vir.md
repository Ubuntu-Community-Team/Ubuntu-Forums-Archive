---
title: "Can &quot;Wubi&quot; be a Vector for a Windows Virus"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by knipper on 2009-05-01
So I have in the past run Linux, and Windows in  dual boot setup with Linux on it's own partition(s) with no worries about anything from the Linux side cross contaminating the Windows side. 

Now I just installed ubuntu using "Wubi" and only read enough of the documentation enough to see that Linux  installs in a file "On" or "In" Windows, and not in it's own separate, isolated Linux Partition as it would without Wubi.

So that makes me wonder if it would be possible for some code tactician to embed a Virus/Worm/Mal-ware whatsit thingamajiggybob into some popular add-on  Linux package or game etc which  would do nothing to harm Linux, but somehow migrate into the nearby Windows OS at a very low level to do it's dastardly deeds.

I'm thinking that this might be a possible vector for Windows infection since there is no "Barrier" between the Win/Lin OS's as in they are both on the same partition. Since Linux, and not Windows is  loaded Windows  would therefore not have any of it's UAC & Mal-Ware defense walls up to protect the alteration or attachment of code to system files.

Is this not possible for some rational reason, or merely not possible "yet" because nobody has worked on this potential exploit of Windows through Wubi & Linux?

I'm admittedly new to Linux, and the Furums, so cut me some slack for this question if it makes no sense, or I have posted it into the wrong area here. If it would be better answered in another Forum area please advise me, or place a link there to this.

Thanks

---

### Post by SunnyRabbiera on 2009-05-01
No there should be no issues of this scale using Wubi

---

### Post by Paqman on 2009-05-01
> **knipper said:**
> 
So that makes me wonder if it would be possible for some code tactician to embed a Virus/Worm/Mal-ware whatsit thingamajiggybob into some popular add-on  Linux package or game etc which  would do nothing to harm Linux, but somehow migrate into the nearby Windows OS at a very low level to do it's dastardly deeds.


Wubi installs Ubuntu into a virtual partition, which Windows sees as a large file. However, Windows can't do anything with this file, and certainly doesn't execute any code within it.

What is possible is that malware you download while in Ubuntu could end up on the /host drive, which is the standard Windows file system. When you boot into Windows this code could conceivably execute. However, your normal Windows security systems should protect you from this, as it would be little different to downloading and executing malware on a Windows-only system.

---

### Post by knipper on 2009-05-03
I like the low entry threshold which Wubi provides. Simplifying Ubuntu in this and other ways makes each iteration of it more and more usable, and therefore acceptable to the wide general public as opposed to just having it appeal to the the died in the wool geek/experts.

Average/casual computer users like myself want it simple and easy, and are often to lazy or uninterested to RTFM so again, I applaud Wubi for sidestepping all that uncomfortable repartitioning that I did all the other times I set up Win/Lin dual boot.

Thanks for quelling my concerns on the Virus vector possibility.

---

