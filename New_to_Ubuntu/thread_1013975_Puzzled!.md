---
title: "Puzzled?!"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by bostock73 on 2008-12-17
So i installed ubuntu 4 times yesterday. I say 4 times because after an hour of each installation (after i restart ubuntu) it fails to load the log in screen.

The first time it didnt do anything, black screen. I left it for ages. The other times i heard the bongo sound to log in but the screen was bright brown and didnt budge.

whats going on here? could it be any of the following....

I installed ONTO MY C, inside of windows and not a dedicated partition.

Each time i installed ubuntu i installed graphics drivers for my ati chipset... the drivers are actually available too (ATI radeon x1250).

---

### Post by nothingspecial on 2008-12-17
Never used windows so I don`t know what would happen if you installed on your c drive.

On installing Ubuntu though look [[COLOR="Magenta"]here[/COLOR]]("http://www.psychocats.net/ubuntu/")

That should help.

---

### Post by rlunger on 2008-12-17
> 

Each time i installed ubuntu i installed graphics drivers for my ati chipset... the drivers are actually available too (ATI radeon x1250).

Try it without the drivers.  My nvidia drivers messed w/ my display so I removed it.  Ubuntu has enough built-in support for most hardware you shouldn't need these.

---

### Post by bostock73 on 2008-12-17
well i want to use all the special effects and eye candy, and my ATI RADEON X1250 isnt supported out of the box....

---

### Post by Hospadar on 2008-12-17
Did you install with wubi?  You might want to try doing a more traditional livecd/resize your windows partition/install in free space type install.

---

### Post by bostock73 on 2008-12-17
i dont exactly know what wubi is, but everytime i uninstalled ubuntu it read 'wubi uninstall successfull' so yeah i guess it was wubi.

whats the difference between installing on a seperate partition than in windows?

will this cure my problem?

---

### Post by rlunger on 2008-12-17
> **bostock73 said:**
> i dont exactly know what wubi is, but everytime i uninstalled ubuntu it read 'wubi uninstall successfull' so yeah i guess it was wubi.

whats the difference between installing on a seperate partition than in windows?

will this cure my problem?

I'm assuming you installed Ubuntu from your Windows desktop (that is what wubi is for).  He's suggesting a standard install (boot up with the LiveCD) because there could either be a problem with wubi that it doesn't recognize, or an interference between Windows and Ubuntu, since you've said you have them on the same partition.  I've done both (wubi and standard install) and haven't had a problem either way.  I still think it's the driver - just because one is available for a piece of hardware, doesn't mean it's going to work.   If that's the case, you may have to wait for an updated one, or out-of-the-box support from Ubuntu.

---

