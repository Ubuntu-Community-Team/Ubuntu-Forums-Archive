---
title: "Launcher for Application in Terminal"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by gurt on 2009-06-30
When I launch an app using the launcher, I want the Terminal title to be set to something unique automatically. Anyway to do that?

Ta!

---

### Post by Jedimaster007 on 2009-06-30
He he....  sounds good. I'd call mine 'Brain' lol

---

### Post by mcduck on 2009-06-30
Create a new profile, and set the window title in that profile. Then create a normal launcher and use something like this for the command:

gnome-terminal --window-with-profile=*yourprofile* -x *yourcommand*

(If that doesn't work, create a shell script with the above command and point your launcher to that script.)

---

### Post by gurt on 2009-06-30
That got me thinking...

This seems to do the trick...
gnome-terminal -e "minicom -o minicom.sw1" -t SW1

Thankya!

---

### Post by mcduck on 2009-06-30
> **gurt said:**
> That got me thinking...

This seems to do the trick...
gnome-terminal -e "minicom -o minicom.sw1" -t SW1

Thankya!

Yeah, that's actually a bit smoother solution than making a separate terminal profile.

I just thought about the profile as I've used that to "embed" a transparent terminal on my desktop, and didn't want to make normal terminal windows transparent so separate profile made more sense. But just setting the title is definitely a better way if you don't need any other specific settings for that terminal window.

---

### Post by gurt on 2009-06-30
Strangest thing... I came back from dinner turned on my PC and... nothing. No Ubuntu logo, no nothing. HD isn't making a sound.

Since I know nothing of Ubuntu I tried to fix it form the CD. Nada. It just hangs when looking for network HW. So I loaded my XP disk and formatted the drive and then tried to load Ubuntu again. Nada.

I'm going to try loading up 8.10 64-bit Desktop. 

I can't remember the last time I ever had a PC crash. Is this something I get to look forward to in the linux world?

---

