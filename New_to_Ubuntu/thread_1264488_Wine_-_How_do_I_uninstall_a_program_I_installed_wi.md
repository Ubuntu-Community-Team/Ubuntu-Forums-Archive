---
title: "Wine - How do I uninstall a program I installed with Wine"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by Ronchap on 2009-09-12
I was trying to get World of Warcraft to work, but I have zero experience with any Linux format. I have only used Windows, so I just decided to throw it on my other comp. (I know I should have just used that one first, but this comp is new and alot better).

I tried looking for it in "/home/rchap/.wine" but when I opened my rchao folder, I didnt see any Wine folders at all. Just a easy to follow step by step guide to locating the game's I have installed to re-install or delete them. 

Any idea's/tip's would be greatly appreciated! Thanks!!

---

### Post by MelDJ on 2009-09-12
it might be in your wine hard disk. under applications, wine, there should be add/remove

---

### Post by TobiasV on 2009-09-12
First of all, your wine folder is hidden (hence the . in front of it). So if you're using Nautilus (that's if you're not using the terminal basically) to locate them, you'll have to press Ctrl+H (that'll show hidden files). Then you can enter .wine. In your .wine folder there should be a "drive_c" folder (that's your C drive). All your programmes should be in that folder (unless you specifically chose to install them elsewhere), they'll most likely be in the "Program Files" folder inside.

To get there through your terminal:

```

cd /home/$user/.wine/drive_c

or for the Program Files folder

cd /home/$user/.wine/drive_c/Program\ Files

```

As MelDJ says, if you want to uninstall an application installed through Wine, you can also go to Applications>Wine>Programs>[Company that made the programme]>[Name of the programme]>Uninstall (should usually be an uninstall here).

---

### Post by Ronchap on 2009-09-12
rofl! Thanks!

Edit: I was rofl at Mel... the solution was so easy and I felt like a artard.

---

### Post by TobiasV on 2009-09-12
Oh, that's what he was talking about, the "Uninstall Wine Software", I'd never seen that (or used that) before, I guess it's a lot easier than what I just said...

---

### Post by MelDJ on 2009-09-12
> **Ronchap said:**
> rofl! Thanks!

Edit: I was rofl at Mel... the solution was so easy and I felt like a artard.

i dont mind being laughed at:D

---

### Post by Ronchap on 2009-09-12
> **MelDJ said:**
> i dont mind being laughed at:D

Nooo.. wasn't laughing at you. I laughed cause I felt stupid that I over looked something that simple.

---

