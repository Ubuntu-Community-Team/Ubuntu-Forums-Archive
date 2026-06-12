---
title: "Need desktop icons help"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by joshjani on 2009-02-24
I can't seem to get desktop items for Computer, Network, Trash, or Volumes.

This Compaq Presario is running 8.04, all updates current.

I've run sudo gconf-editor in terminal, gone to apps-nautilus-desktop, and made sure that the boxes are checked, but still the icons do not appear.

I wish for this computer to have similar icons to windows, which my kids are using at school. I want them to be able to navigate at least close to the same way, so some of the same icons on the desktop are important to me.

Thanks for any help-
JC

---

### Post by roger_1960 on 2009-02-24
Hi

Right click on the empty desktop.  Select "create launcher".  Select your application - most are in the system folder usr/bin 

eg if you want an icon to run Nautilus (the file manager) use the browse button and select 'nautilus" in the folder /usr/bin  Press OK and the icon which runs nautilus appears.  You can then right click the icon to change its properties if you wish.

Hope this helps.  The tricky bit is finding the right files to point the launcher at!

Many useful icons can be easily added to the panels at top and bottom by right clicking on the panel, selecting "add to panel" and choosing what you want.

---

### Post by MrWES on 2009-02-24
you need to run gconf-editor from the terminal and navigate to apps | nautilus | desktop and tell it what icons you want to view on your desktop.

Bill

---

### Post by roger_1960 on 2009-02-24
Yes!  MrWes is right - I even have gconf-editor installed but had forgotten!

---

### Post by joshjani on 2009-02-24
> **joshjani said:**
> 

I've run sudo gconf-editor in terminal, gone to apps-nautilus-desktop, and made sure that the boxes are checked, but still the icons do not appear.



Thanks for the info there, but I already tried that. That's why I'm stymied!

---

### Post by Michael.Godawski on 2009-02-24
hi,

did the icons disappear out of the blue or did you some changes to the system?
Like installing or removing some applications?

Some packages are dependencies for others, so removing one can cause others not to work. (wild guess)

---

### Post by MrWES on 2009-02-24
Just guessing here, since you ran sudo gconf-editor; the changes you made were to the root desktop? Dunno, since the root account doesn't even exsist. I always ran it as the user sans the sudo.

Bill

---

### Post by BDNiner on 2009-02-24
You have to run gconf-editor under your username not under root using sudo
so just type 'gconf-editor'. The other way this can happen is if nautilus is no longer drawing your desktop. Some setups of compiz let compiz draw the desktop not nautilus.

---

### Post by joshjani on 2009-02-24
OH...OK- I will try without the "sudo" next time. I am away from the box in question at the moment. I'll try at my earliest convenience and report back
JC

---

### Post by MrWES on 2009-02-24
Workin' hard aye? heh...

---

### Post by newbee70 on 2009-02-24
> **joshjani said:**
> I can't seem to get desktop items for Computer, Network, Trash, or Volumes.

This Compaq Presario is running 8.04, all updates current.

I've run sudo gconf-editor in terminal, gone to apps-nautilus-desktop, and made sure that the boxes are checked, but still the icons do not appear.

I wish for this computer to have similar icons to windows, which my kids are using at school. I want them to be able to navigate at least close to the same way, so some of the same icons on the desktop are important to me.

Thanks for any help-
JC

Hi JC!

Since your running Gutsy, I'm sure your aware of the tool bars at the top and bottom of the screen, and I'm sure you are aware that you can go into the Applications "drop down menu" and into any of the categories and "drag and drop" the launcher on to your desktop "or onto your tool bar". As you can from places and system.

So is it a problem that your tool bars are not showing?

---

### Post by joshjani on 2009-02-25
OK- it was that I was using "sudo" with gconf-editor...

Using gconf-editor without sudo showed me that I did not have the icons checked as I wanted them.

I now DO have my icons as I want them! Thanks for all the suggestions!

---

### Post by newbee70 on 2009-02-25
> **joshjani said:**
> OK- it was that I was using "sudo" with gconf-editor...

Using gconf-editor without sudo showed me that I did not have the icons checked as I wanted them.

I now DO have my icons as I want them! Thanks for all the suggestions!


So you were setting up your root desktop instead of your desktop?

---

