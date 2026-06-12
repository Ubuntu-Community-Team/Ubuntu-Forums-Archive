---
title: "Adding an item to Start menu??"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by PepeLapiu on 2009-12-15
OK, if it were win-doze I would easily know this but here I am:

If I want to add an application to the Startup Menu I have to go to:

System > Startup Application > Startup Programs > Add

From there, I should fill the 'Name' field (aMule in this case), then for the Command field I should browse to that specific item.

Had it been win-doze, I would browse to Programs > aMule and find the appropriate .exe file. But this is not win-doze, so to which folder should I be browsing to and what file will I be looking for in that folder?

I am guessing the right folder is Home > (username) > aMule ..... but what file in there is the right one to choose?

Thanx and Cheers,
PepeLapiu :)

---

### Post by hobo14 on 2009-12-15
So you know how to add items to the menu in Ubuntu, what you actually want to know is where to find the aMule executable?

Is there one called "aMule"?  Is there /bin/aMule?

---

### Post by PepeLapiu on 2009-12-15
> **hobo14 said:**
> So you know how to add items to the menu in Ubuntu, what you actually want to know is where to find the aMule executable?

Precisely!
> Is there one called "aMule"?  Is there /bin/aMule?

Nope, I went to Home/(username) and could not find a 'bin' folder there. 
So I went to File System and I looked to /bin and could not find anything there called aMule, neither folder nor file.

But aMule IS installed, I am running it as I type this.

Where else should I be looking?

---

### Post by valvegrid on 2009-12-15
Have a look in /usr/bin

Otherwise, if you can open aMule by typing it in the terminal, then just put that in as the command.

---

### Post by akoskm on 2009-12-15
> **PepeLapiu said:**
> Precisely!


Nope, I went to Home/(username) and could not find a 'bin' folder there. 
So I went to File System and I looked to /bin and could not find anything there called aMule, neither folder nor file.

But aMule IS installed, I am running it as I type this.

Where else should I be looking?

The 
```

dpkg -L amule

```
will list you all files owned by the aMule package. If you  want to know the exact patch to the executable then search for the line what ends with aMule.
Because the executable should be in a directory called bin you can simplify the search by extending the command to:
```

dpkg -L amule | grep bin

```.
Of course the solution posted by valvegrid should work.
Good luck.

---

### Post by PepeLapiu on 2009-12-15
Yes, valvegrid's solution worked perfectly. Dude! Do I have a lot to learn about this OS or what!?

Thanx, the treat is solved!

Cheers,
PepeLapiu :)

---

### Post by 3rdalbum on 2009-12-15
> **PepeLapiu said:**
> Yes, valvegrid's solution worked perfectly. Dude! Do I have a lot to learn about this OS or what!?

Not usually. Usually, the package you install will contains .desktop files that will automatically create menu items for you.

And secondly, you didn't actually need to go hunting around for the binary. You can actually just put "amule" as the command, because the "amule" binary is inside /usr/bin, which is where the system checks to find programs.

---

### Post by PepeLapiu on 2009-12-15
Duh!!! Stupid me, it wasn't working because I was typing in terminal "amule" (with the brackets)

However, I just tried to run amule and that worked, so just for kicks I ran the command 'amule' and that worked too.

Thanx

---

