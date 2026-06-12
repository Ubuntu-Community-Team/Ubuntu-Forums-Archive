---
title: "disappearing paths problem"
date: 2010-09-01
forum: New to Ubuntu
---

### Post by MrBeef on 2010-09-01
Hi,

I installed Ubuntu a few days ago and one of the first things I did was to create shortcuts on my desktop to some directories I use often like "My documents" and "Music".

Today all the links I created were "broken", and the default partition shortcuts were missing. 
After I entered My Computer and clicked on each partition the corresponding link appeared by itself on my desktop.

Is that a problem or am I missing something?

Thanks

---

### Post by egalvan on 2010-09-01
How did you install Ubuntu?
As a separate OS, in it's own partitions?

Or "inside" Windows with Wubi?


You mention of "My Computer" and "My Documents" leads me to think
you have a Wubi install...
Those folder names don't appear on a standard Ubuntu install.


Next, HOW did you create the shortcuts (more correctly named "links" under Linux)?

---

### Post by MrBeef on 2010-09-01
> **egalvan said:**
> How did you install Ubuntu?
As a separate OS, in it's own partitions?

Or "inside" Windows with Wubi?


You mention of "My Computer" and "My Documents" leads me to think
you have a Wubi install...
Those folder names don't appear on a standard Ubuntu install.


Next, HOW did you create the shortcuts (more correctly named "links" under Linux)?

I installed it as a separate OS so I'm dual booting with Windows 7 now.
I created the link by selecting the folder in the File Browser, created a link there, and just copied it to my desktop.

And me mentioning My Computer and My Documents is just an old windows habit :)

---

### Post by bcbc on 2010-09-01
Most likely you manually mount your windows partition (by clicking on it under Places). The shortcuts only show up after it is mounted.

If you want it to be mounted automatically you have to add an entry in /etc/fstab

---

### Post by bredman on 2010-09-02
It is not clear if you are trying to create a link to your Ubuntu directories, or to your Windows directories.

You seem to be using a correct procedure, but there may be something unusual about the directory. To get more help, I suggest you do the following...

Right-click on a desktop link that is causing trouble.
Select "Proprties".
Tell us what the link target is.

---

### Post by BJones007 on 2010-09-02
I have a similar problem to that too, when i open the "Places" drop down box and click on the Home Folder icon an error message comes up saying "No application is registered as handling this file" it happens for all other files except for the Computer icon

---

### Post by egalvan on 2010-09-02
> **MrBeef said:**
> I installed it as a separate OS so I'm dual booting with Windows 7 now.

OK, a good way to install and dual boot, nothing to see here.
Let's move on.


> I created the link by selecting the folder in the File Browser, created a link there, and just copied it to my desktop.

OK, one correct way to create a link, nothing to see here.
Let's move on.

> And me mentioning My Computer and My Documents is just an old windows habit :)

OK,old Windows habit, dying hard, but that's how Mr Gates wants it...
And may I add, the proper Linux term is **LINK** not "shortcut" :)
One more old Windows habit to kill... :)

No, I think **bcbc** in post #4 got it right...
your NTFS partition is probably not mounting until you first access it.
You can either keep this behavior, which entails you manually clicking the partition (which may or may not be what you want)

or you can have the partition auto-mounted, by adding the necessary info to the 'fstab' file.
This can be done either manually via a direct edit to 'fstab' and adding the needed line...

or using one of the excellent sets of NTFS tools available under linux.



**EDIT**

Uhhhh, OK, why are we all "assuming" that he is talking about an NTFS or WIndows partition???

I just re-read his original post, and, durn it all, he says nothing about WHAT KIND OF PARTITION it is.

Why is my face turning red??  :redface: 
Did the air conditioning pack up again?
Did someone turn up the heat?

---

### Post by bcbc on 2010-09-02
> **egalvan said:**
> 
**EDIT**

Uhhhh, OK, why are we all "assuming" that he is talking about an NTFS or WIndows partition???

I just re-read his original post, and, durn it all, he says nothing about WHAT KIND OF PARTITION it is.

Why is my face turning red??  :redface: 
Did the air conditioning pack up again?
Did someone turn up the heat?

You need to make certain assumptions sometimes. That's why I started with "Most likely". :)

If posters always knew what information was relevant to the problem, they probably would know the answers as well. It's up to the OP to confirm the assumption or supply additional information.

PS in the original post MrBeef mentioned they appeared after clicking on the partitions. Sounds like a mounting issue.

PPS why do you assume the OP is a man ;) Same reason I suppose Mr. Beef

---

### Post by egalvan on 2010-09-06
> **bcbc said:**
> 
PPS **why do you assume the OP is a man** ;) Same reason I suppose [COLOR="Red"]Mr. Beef[/COLOR]

Why? It's the Queen's English, Old Fellow!
Jolly Good.

[COLOR="Red"]MrBeef[/COLOR] could stand for ANYTHING, I certainly don't use usernames as an indication of gender :)
Then my face would REALLY be red...AL the time... ;)

That, and I REFUSE to use he/she :)
(my subordinates call me Lieutenant, and I call them all Mister,
regardless of plumbing... if I just use their last names, they know I'm either really busy, or really p/o'd)
(In my engineering classes, we had over 400 students, and only 4 were females. Sadly, they all dropped out by the start of the third semester)


> PS in the original post MrBeef mentioned they appeared after clicking on the partitions. Sounds like a mounting issue.

Yep, which is why I wrote

*No, I think **bcbc **in post #4 got it right.*

I even "bold"ed your username.

It's further true that mounting issues are more likely with non-Linux partitions,
I should have caught it earlier...


> It's up to the OP to confirm the assumption or supply additional information.

I have to disagree with this... a good forensics examination should not require the problem to supply all the information needed...
It's up to the examiner to make sure he is asking pertinent questions.
IF the problem can supply pertinent/corroborative info, all the better... but this is not the norm.

and in "Absolute Beginner's", where many are recently from the Windows camp, with the MS mind-set, this is even more important...
Linux Is Not Windows
Windows Is Not Linux

):P

---

### Post by bcbc on 2010-09-06
> **egalvan said:**
> Why? It's the Queen's English, Old Fellow!
Jolly Good.

[COLOR="Red"]MrBeef[/COLOR] could stand for ANYTHING, I certainly don't use usernames as an indication of gender :)
Then my face would REALLY be red...AL the time... ;)

That, and I REFUSE to use he/she :)
(my subordinates call me Lieutenant, and I call them all Mister,
regardless of plumbing... if I just use their last names, they know I'm either really busy, or really p/o'd)
(In my engineering classes, we had over 400 students, and only 4 were females. Sadly, they all dropped out by the start of the third semester)




Yep, which is why I wrote

*No, I think **bcbc **in post #4 got it right.*

I even "bold"ed your username.

It's further true that mounting issues are more likely with non-Linux partitions,
I should have caught it earlier...




I have to disagree with this... a good forensics examination should not require the problem to supply all the information needed...
It's up to the examiner to make sure he is asking pertinent questions.
IF the problem can supply pertinent/corroborative info, all the better... but this is not the norm.

and in "Absolute Beginner's", where many are recently from the Windows camp, with the MS mind-set, this is even more important...
Linux Is Not Windows
Windows Is Not Linux

):P

My post wasn't meant as a criticism - I'm sorry if it came out that way :)  

I guess I didn't explain myself properly... reading it now, my comment seems defensive, but I was really trying to be supportive. I'll stop now before I shoot myself in the other foot ;)

---

### Post by Land Rover Series 3 on 2010-09-29
Did you ever get an answer to this, or just get bogged down in unhelpful, esoteric discussions about the Queen's english?

To cure it, you need to first (somehow) run nautilus. If all else fails, you can simply open a terminal and typing gksu nautilus. Browse to your home directory so that your "Documents" folders etc. are listed in the right hand side pane. Right click on one of your folders and choose "Open with Other Application". Select "Custom Command" and type in nautilus. That should sort it.

THIS SEEMS TO BE SUCH A COMMON OCCURRENCE that maybe it would be useful if Ubuntu developers could add some simple instructions like this in the (so-called) "Help and Support" system, as I personally have yet to find anything truly useful in it.

---

