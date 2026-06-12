---
title: "Problem with Desktop."
date: 2009-07-06
forum: New to Ubuntu
---

### Post by MaximeDebosschere on 2009-07-06
Hi Everyone


I'm new to Linux and this forums (this is my first post), I installed Ubuntu yesterday using Wubi (so I'm just working on an image here) and everything went smoothly.

The only problem is that I've installed Linux with the wrong language by accident: I used Dutch instead of English.

I have changed the Language for the entire OS (I've used 'System > Administration > Language Support' to do this), and after my first reboot it kindly asked me if I wanted to change the names of 'Desktop', 'Documents', 'Music', 'Pictures', etc as well (which I confirmed).

This all worked except for some links to the Desktop. 
- 'Places > Desktop' still leads me to the old 'file:///home/maxime/Bureaublad'.
- Copying a file to the desktop gives me this error: 'Error stating file '/home/maxime/Bureaublad': No such file or directory'

I believe Ubuntu forgot to update some links... Some help here would be very welcome.

Thanks in advance,

Maxime Debosschere.


P.S.: In case I've posted this in the wrong forum, I appologise.

---

### Post by frunns on 2009-07-06
Seems to be the right forum. :)

I can't really help you though... Except for a bad solution, that should work.
```
ln -s /home/maxime/Desktop /home/maxime/Bureaublad
```
Might do the trick.

---

### Post by sadaruwan12 on 2009-07-06
like to know what is the version of your distro and don't worry you're in the right place.

---

### Post by MaximeDebosschere on 2009-07-06
Cheers for the fast replies!

I'm using the (AFAIK latest) version of Ubuntu: 9.04 - the Jaunty Jackalope

I haven't used the ln command yet, will try this if nothing else works. Thanks!

---

### Post by Paddy Landau on 2009-07-06
I suggest that you do not use the *ln* command.

If this is a brand new installation of Wubi, have you considered uninstalling Wubi and reinstalling it with your preferred language? (I'm guessing that, as it's a new installation, you have no data that you would lose.)

Alternatively, instead of the *ln* command, rather try renaming your home folder. If you boot into recovery mode, then
```
cd /home/maxime
mv Bureaublad Desktop
```Reboot.

It may work -- but it may also cause you problems. A clean reinstallation would be best.

---

### Post by frunns on 2009-07-06
So, you still have the Bureaublad folder?

---

### Post by Paddy Landau on 2009-07-06
> **frunns said:**
> So, you still have the Bureaublad folder?
Ah, perhaps I got the wrong end of the stick. In that case, a Wubi uninstall followed by a Wubi install would be the best bet, I think.

---

### Post by frunns on 2009-07-06
> **Paddy Landau said:**
> Ah, perhaps I got the wrong end of the stick. In that case, a Wubi uninstall followed by a Wubi install would be the best bet, I think.

Well...

> - 'Places > Desktop' still leads me to the old 'file:///home/maxime/Bureaublad'.

Kind of makes it sound like the folder still exists. Though, as copying to the desktop makes it give an error message saying it doesn't exist, it probably doesn't... But yeah, re-installing sounds like a simple solution tbh.

---

### Post by MaximeDebosschere on 2009-07-06
A reboot has solved my problem... A simple solution to a seemingly difficult problem. Incredible!

Sorry for the inconvenience, thanks for all kind help! Hopefully this topic will help other people with similar symptoms.

(Maybe future versions should mention the need for a reboot?)

---

