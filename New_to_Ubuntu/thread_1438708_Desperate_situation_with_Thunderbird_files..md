---
title: "Desperate situation with Thunderbird files."
date: 2010-03-25
forum: New to Ubuntu
---

### Post by T4K3Z0U on 2010-03-25
OMG I have done something beyond belief. I was trying to upgrade to TB3 following advice here, decided to be on the safe side and make a backup of the main/current .mozilla-thunderbird folder, got a couple of error messages when trying to put it on flash drive, so figured I would just copy (drag and drop that is) it to my desktop, and that's when it happened..... Instead of the usually copying of a folder, the folder vanished out of nautilus and is not found anywhere on my desktop, and the search feature does not display it.

I am assuming without that folder, or at least it's location, ALL on my emails will be lost forever!? Is this correct? How can I find it again? What could have happened?

I have not yet proceeded with the upgrade, just to be on the safe side, though I doubt it's possible to upgrade without that folder.

PLEASE HELP ME, THIS IS A DESPERATE SITUATION [-o<

---

### Post by Kenny_Larsen on 2010-03-25
I could hazard a guess that it moved the folder to the desktop and the as it is usually hidden you can't see it. Have you tried going to the desktop in nautilus and enabling view hidden files?
 
Kenny

---

### Post by T4K3Z0U on 2010-03-25
> **Kenny_Larsen said:**
> I could hazard a guess that it moved the folder to the desktop and the as it is usually hidden you can't see it. Have you tried going to the desktop in nautilus and enabling view hidden files?
 
Kenny

Thanks for the reply Kenny. I did do that as I was writing this thread, and unfortunately it was unsuccessful.

ETA: I also rechecked the home folder on the off chance it found it's way back.

---

### Post by Kenny_Larsen on 2010-03-25
This might give you a lot to trawl through but you could try:
 
```
 
find / -mmin -15

```
from the terminal (depending how long ago you moved it) although I'm not sure if moving it changes the timestamp.
 
Kenny

---

### Post by T4K3Z0U on 2010-03-25
> **Kenny_Larsen said:**
> This might give you a lot to trawl through but you could try:
 
```
 
find / -mmin -15

```
from the terminal (depending how long ago you moved it) although I'm not sure if moving it changes the timestamp.
 
Kenny

It's been about 45mins or less, I looked as much I could for 5 or so mins then posted. Am I to understand that to be searching for activity in the last 15mins? So changing it to 45 should help yes?

---

### Post by philinux on 2010-03-25
> **T4K3Z0U said:**
> Thanks for the reply Kenny. I did do that as I was writing this thread, and unfortunately it was unsuccessful.

ETA: I also rechecked the home folder on the off chance it found it's way back.


You have set nautilus to show hidden files?

---

### Post by T4K3Z0U on 2010-03-25
> **philinux said:**
> You have set nautilus to show hidden files?

Perhaps my answer was not clear the first time. Yes, I checked the box to show hidden folders/files, but it did not show. I've since done it again, but still no luck.

---

### Post by philinux on 2010-03-25
> **T4K3Z0U said:**
> Perhaps my answer was not clear the first time. Yes, I checked the box to show hidden folders/files, but it did not show. I've since done it again, but still no luck.

I thought you would have. Try this.
```

sudo updatedb

then 

locate .mozilla-thunderbird
```

---

### Post by T4K3Z0U on 2010-03-25
> **philinux said:**
> I thought you would have. Try this.
```

sudo updatedb

then 

locate .mozilla-thunderbird
```

Wow, that spat out a huge list. It's pretty late now, so I will read over it in the morning with fresh eyes.

Thanks.

---

### Post by T4K3Z0U on 2010-03-25
> **Kenny_Larsen said:**
> I could hazard a guess that it moved the folder to the desktop and the as it is usually hidden you can't see it. Have you tried going to the desktop in nautilus and enabling view hidden files?
 
Kenny

> **philinux said:**
> You have set nautilus to show hidden files?

Uughh I'm a complete dunce. I couldn't make head nor tails of that locate .mozilla-thunderbird thing that terminal spat out last night, so I had a look at nautilus again. When I clicked show files, I was only clicking on the desktop ***icon***. Then it dawned on me, perhaps I need to click the "home" folder, then click on the "desktop" folder and click show files, to be able to find it. Well sure enough, I did this and found my file, and managed to put the folder back where it belongs, and everything seems to be working fine.

---

### Post by T4K3Z0U on 2010-03-26
I think during the course of this, I may have stuffed something up. Instead of firefox, for some reason I now have some new browser called Namoroka. Does anyone know what this is? Also the little icon is no longer there, just a black square with a red circle with the line through it, like the "no" whatever signs.

---

### Post by Kenny_Larsen on 2010-03-26
Again I'm only hazarding guesses based on what I would do, but if you do System->Administration-> Synaptic Package Manager and search for firefox is it still installed?
 
You might want to open a new thread on this topic specifically.
 
Kenny

---

### Post by 1915flyer on 2010-03-26
A search shows that Namoroka is the code name for the pre-release of Firefox - 3.6.

---

### Post by T4K3Z0U on 2010-03-26
> **1915flyer said:**
> A search shows that Namoroka is the code name for the pre-release of Firefox - 3.6.

Is it just a code name, or is Firefox now going to be known as Namoroka? I ask because the Namoroka icon is a little earth rather than the little Firefox, and of course the name in the title bar or whatever it's called, also now says Namoroka rather than Firefox. Not too many other differences than that.

Mods, feel free to separate this into a new thread if need be. Also the original topic of this thread has been solved.

---

