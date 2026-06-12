---
title: "Ubuntu Software Center"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by noobda on 2011-07-21
i cant install any software
when i try to install any software like "ccsm/cairo-dock or many softwares using ubuntu software center 
i cant see install button and there is only one button which is more
when i press it ..
i get this error
? Not Fount
There isn't a software called " most softwares give this" in your current software sources

---

### Post by ddastoor on 2011-07-21
Are you sure you giving a ciorrect search ? or in other words, is ur searched software showing up in the search results?

Or most probably, these apps are not listed in you software sources and so the software center doesn't show it up.

Try:
[http://linux-setting.blogspot.com/2011/05/how-to-install-cairo-dock-in-ubuntu.html]("http://linux-setting.blogspot.com/2011/05/how-to-install-cairo-dock-in-ubuntu.html")

In general, the software center (or command line apt-get) uses a list of software sourses from which it installs complete apps with dependencies.

Certain software is not present in these and so you have to add the software source first.

---

### Post by mittwit on 2011-07-21
Have you tried using the "Synaptic Package Manager"? You can access it via System > Administration
If you can install software with the package manager maybe your Ubuntu Software Centre needs reinstalling.

---

### Post by Frogs Hair on 2011-07-21
Try running the update manager and then try the software center again .

---

### Post by ddastoor on 2011-07-21
> i cant install any software
when i try to install any software like "ccsm/cairo-dock or many softwares 

cairo-dock's a PPA, can't use software center till he adds the software sources, hence i posted the link howto install cairo..

---

### Post by noobda on 2011-07-21
i guess i need to re install ubuntu software center

can nyone provide me how can i reinstall it?

---

### Post by oldos2er on 2011-07-21
Can you run ```
sudo apt-get update && sudo apt-get upgrade
``` in a terminal, and post the output here?

---

### Post by mokrates on 2011-07-21
> **noobda said:**
> i guess i need to re install ubuntu software center

can nyone provide me how can i reinstall it?

You probably don't.

Please be more specific as to why you would want to do that.

Did you try the posted howto to installing cairo?

---

### Post by nagromlt on 2011-07-29
> **Ubuntu Software Center - Bug?** 			
 			 			 		   		 		 		Just did the  two-step upgrade from 10.04 --> 11.04.  While testing the USC by  cleaning up old/unwanted apps, after x amount of times the remove icon  will 'disappear' {x as in variable, between 5-20 times}.  Once its  restarted it goes back to 'normal'.

Not sure if this is a bug or what, but seems illogical to me and just plain bizarre.:???:  Thought someone might have a vested interest/knowledge into this peculiarity.

Edit:  Release: 11.04Natty | Kernel: 2.6.38-10-generic | GNOME:  2.32.1 | 3.7GB RAM | AMD Athlon 64 2x Core 4400+
GeForce 6150SE nForce 430 (rev a2) | MCP61 High Definition Audio (rev a2)  {BOTH ON BOARD}

Not sure if my signature came up like it was supposed too...
 		                   		  		  		  		  		 		 			 				 				* 					 						[Last edited by nagromlt]("http://ubuntuforums.org/posthistory.php?p=11099448"); 41 Minutes Ago at 01:13 PM.. 					 					 						Reason: Signature?*


Searched for a forum to talk about USC but didn't didn't find anything, so started own post...  Is there a way to move that one here or delete it?


As an addendum, I've noticed several other minor glitches.
1. When removing, sometimes the highlight bar will not jump back to where it is supposed to be (the next item or back to the original, etc.)
2.  sometimes when trying to remove the first time, it will list other items that will be removed also.  But if you cancel and then try to remove again, then those items will not be listed anymore as being removed with it.
3.  Also a weird glitch/thing that happens is when you remove something and then sometimes it will no longer be listed after it is done, but then other times it will be still listed and have an option to install (under installed, at least).  

All these things aren't catastrophic, but just weird and seems not quite right...

---

