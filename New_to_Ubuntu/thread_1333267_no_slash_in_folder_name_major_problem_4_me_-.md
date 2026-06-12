---
title: "no slash in folder name major problem 4 me - ?"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by mjp29 on 2009-11-21
I have 6 years of digital photos that I've neatly organized into days, months, and years by folder on my Mac os X.  I will be transitioning from the old G4 mac to Ubuntu completely once I get all my digital photos from that box to ubuntu.

My problem I foresee is this.  Each and every single folder on the mac is labeled by date with slashed */*  For example, todays photos would be on there sa *"11/21/09"*

But any time I put photos on the ubuntu box, i have to label it *"11-21-09"*

I foresee this a problem if I transfer a bazillion folders from mac to ubuntu, as i have 6 years of digital folders in an extreme number of folders to transfer.  

Any recommendations or ideas what will happen when tried or solutions?

---

### Post by ZankerH on 2009-11-21
Use one of the billion bash scripts for batch renaming files and folders. The forward slash is indeed an illegal character for any file or folder names under GNU/Linux.

---

### Post by mjp29 on 2009-11-21
but wouldn't i need the script to do it to the mac box.  mac os x is unix based, and it has a terminal too, so perhaps someone knows a script that i could do on it to rename all "/" in folder names to "-"  

[?]

---

### Post by coffee on 2009-11-21
Hello mjp29,

I did a quick search and found "Batch File Rename 1.7" you can read about it [[COLOR="Blue"]here[/COLOR]]("http://www.macupdate.com/info.php/id/29388").  As I do not have a mac and the opportunity you have described I can not test this, but you might want to give it a try. 


Another option I found, "Name Mangler", is [[COLOR="Blue"]here[/COLOR]]("http://www.manytricks.com/namemangler/").

I hope one of these two options dose the trick.

coffee

---

### Post by ZankerH on 2009-11-21
I know mac OS is kinda UNIX-like and uses bash as well, which is why I'm surprised it allows forward slashed in  file and folder names. But yeah, any bash scripts for batch renaming should work in mac OS as well.

---

### Post by mjp29 on 2009-11-21
Your suggestions are *extremely* helpful and I will try them.  Thank you so much for your time in researching this for me.

---

### Post by Old *ix Geek on 2009-11-21
> **ZankerH said:**
> I know mac OS is kinda UNIX-like and uses bash as well, which is why I'm surprised it allows forward slashed in  file and folder names. But yeah, any bash scripts for batch renaming should work in mac OS as well.Mac OSX isn't "kinda UNIX-like," it *IS* UNIX.  And I have no idea how file names with slashes were allowed on it!

---

### Post by mjp29 on 2009-11-22
> **Old *ix Geek said:**
> Mac OSX isn't "kinda UNIX-like," it *IS* UNIX.  And I have no idea how file names with slashes were allowed on it!



Unless I'm living in an imaginary world inside my mind and not typing in reality now [ROFLMAO] then I think in the past few years using Mac os X on an old Mac G4 computer I kept creating hundreds (even thousands) of folders to put photos in [by day, month, and year of hundreds of thousands of photos I've taken as I am an amateur photographer].

I actually suspect that Mac os X isn't seeing slashes in the folder names.  I suspect that the GUI is allowing it to be done as when Steve Jobs transitioned Mac from OS 9.x to Unix [he bought Next and brought that team in, whereas I believe he created Next and it was Unix based], I believe that to make a smooth transition, then it would have perhaps been somewhat traumatic if users that were use to using slashes */* for so many years couldn't still do it.  In fact, I believe the initial version of OS X looked very very similar to the last version of non os X which was os 9.x just to help a gazillion Apple Mac users feel comfortable to make the transistion - does that make since to you or anyone or am I a lunatic that should be put in an insane asylum?

---

### Post by coffee on 2009-11-25
> **mjp29 said:**
> Your suggestions are *extremely* helpful and I will try them.  Thank you so much for your time in researching this for me.

No Trouble at all mjp29,  I am glad I could help.

coffee

---

