---
title: "Windows Vista defrag glitch"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by Ravernomina on 2009-05-04
hello... sorry if this is in the wrong place no ware else to go... Anyway im using windows vista and every time i defrag i lose 3 gigs hard drive space -.-. i only have a 80 gig hard drive. so could some 1 please tell me how to fix this glitch :). Its annoying and im down to 37 gigs.... I HAVE NO CLUE AT ALL!! so please assist TYVM!!
   Ravernomina.

---

### Post by jerrrys on 2009-05-04
"sorry if this is in the wrong place"...

yes you are, but a defrag in windows cannot cause this...are you using windows defrag or a third party?

---

### Post by Ravernomina on 2009-05-05
Windows defrag

Windows vista ultimate 64bit

4 gig RAM

---

### Post by Sef on 2009-05-05
Moved to Absolute Beginners.

> **Absolute Beginner Talk**
 The perfect starting place to find out more about computers, Linux and Ubuntu.

---

### Post by Ravernomina on 2009-05-05
ty

---

### Post by Paddy Landau on 2009-05-05
> **Ravernomina said:**
> sorry if this is in the wrong place...
Go to Microsoft's Support area
[http://answers.microsoft.com/en-gb/windows/default.aspx](http://answers.microsoft.com/en-gb/windows/default.aspx)
Choose a forum and post to it.

---

### Post by abn91c on 2009-05-05
have you run virus and spyware scans? install and run ccleaner(found in downloads.com) to identify and get rid of useless junk files, also if you use **limewire** or similar programs remember that incomplete files stay on the hardrive taking up space.

---

### Post by Mark Phelps on 2009-05-05
Did you even look for any Vista forums?  A quick google found several of them.  Suggest you try again and post to a Vista forum.

BTW, defrag does NOT delete files; it only rearranges the distribution of the used blocks on the drive.  When done, you have the same amount of free space as before you started.

---

### Post by Ravernomina on 2009-05-05
I know that after i use disk clean up i have for example 46 gigs free i use defrag i lose 3 gigs down to 43 gigs... :l

---

### Post by lavinog on 2009-05-05
Maybe you need to remove the system restore points.

---

### Post by SentientFluid on 2009-05-05
According to several web pages I found via a Google search, this is a common complaint with Vista.  It's caused by a combination of system restore points and shadow copies.

Here's the search I used:
[http://www.google.ca/search?hl=en&q=vista+defrag+lose+hard+drive+space&meta=](http://www.google.ca/search?hl=en&q=vista+defrag+lose+hard+drive+space&meta=)

Here's a link on how to tell Vista not to devote so much space to it.
[http://www.howtogeek.com/howto/windows-vista/reduce-system-restores-disk-usage-in-vista/](http://www.howtogeek.com/howto/windows-vista/reduce-system-restores-disk-usage-in-vista/)

---

### Post by Ravernomina on 2009-05-05
THAT DID IT!!!! OMG UBUNTU FORUMS HAS EVERY ANSWER U GUYS ARE AMAZING!!!! :popcorn::popcorn::popcorn::popcorn::popcorn::popcorn:

---

### Post by automaton26 on 2009-05-05
Empty the Recycle Bin for that drive ?

---

### Post by Ravernomina on 2009-05-05
No the shadow copies

---

### Post by jerrrys on 2009-05-05
SentientFluid...this is good to know...will now see if this is a problem on my wife's vista driven computer...thanks

---

### Post by SentientFluid on 2009-05-05
> **jerrrys said:**
> SentientFluid...this is good to know...will now see if this is a problem on my wife's vista driven computer...thanks

I've never run Vista or worked on Vista. Thank Google. Google is your friend. ;)

---

### Post by jerrrys on 2009-05-05
two friends...google and SentientFluid...thanks again...

---

### Post by lisati on 2009-05-05
I've found by experience that the cleanup utilities that come with Windows don't always do that thorough a job: there's often a lot of rubbish left behind in the %temp% directory. You can open it up and have a look by clicking on "run" then typing "%temp%" (without the quotes) in the box that opens. Most of it can be safely deleted.

---

### Post by freeman2000 on 2009-05-06
I would recommend at least 2 programs, which are both better than what comes with Widows.  The first is "CCleaner", which you can use quickly as an every day cleanup program.  The second program is "Smart Defrag", which I would recommend running at least weekly to defrag your hard drive.  Both programs are freeware and you can safely download them from either [www.download.com](www.download.com) or [www.filehippo.com](www.filehippo.com)   Good luck.

---

### Post by Lakers on 2009-06-19
You are loosing free space when the Windows Vista defrag runs and that is probably due to a conflict between Volume Shadow API and the defragmenter.  [COLOR=#1f497d][COLOR=black][FONT=Verdana][COLOR=black][FONT=Verdana]When a file is moved during defragmentation , Volume Shadow API makes unnecessary snapshots confusing a file movement to a file modification.  Microsoft recommends as a workaround to format the drives to a 16kb or larger to avoid these unnecessary snapshots.   Here is a knowledge article by Microsoft in regard to this issue[/FONT][/COLOR][COLOR=black][FONT=Verdana]:[/FONT][/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][[COLOR=blue]http://support.microsoft.com/default.aspx?scid=kb;en-us;312067[/COLOR]]("http://support.microsoft.com/default.aspx?scid=kb;en-us;312067")[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]However Diskeeper has added a defragmentation algorithm for users that have formatted their drives to 4KB cluster size  or smaller than 16 kb that they can select via the user interface.  This method moves files in a 16kb cluster size in order for the VSS to not take unnecessary snapshots during the defrag process. [/FONT][/COLOR]
[/FONT][/COLOR][FONT=Verdana][COLOR=#000000] [/COLOR][/FONT]
[/COLOR]

---

