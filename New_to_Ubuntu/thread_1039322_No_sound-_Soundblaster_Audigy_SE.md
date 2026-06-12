---
title: "No sound- Soundblaster Audigy SE"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by ditto1958 on 2009-01-14
I have Ubuntu installed on a Dell desktop as a dual boot with XP.

I can't get my sound to work, though. I recently wiped my HD and did a fresh install of XP and Ubuntu. I had the same setup before and sound worked. I can't remember any issues with getting it to work the first time.  The system seems to recognize the sound card.

Sound card and speakers work fine in XP, so it shouldn't be a hardware issue.

---

### Post by gettinoriginal on 2009-01-15
After a fresh install, I also had problems.  I used this and it fixed them all:  :p
[http://ubuntuforums.org/showthread.php?t=789578&highlight=usb+mic](http://ubuntuforums.org/showthread.php?t=789578&highlight=usb+mic)

---

### Post by ditto1958 on 2009-01-16
Thahk you. I tried that, but still no go. There is sound when I power on my computer and load Ubuntu, but I can't get anything to play once the machine is booted up.

---

### Post by mc4man on 2009-01-16
Are you running 8.04 (hardy) or 8.10 (intrepid)?

---

### Post by ditto1958 on 2009-01-17
Intrepid.

---

### Post by mc4man on 2009-01-17
You can try this (can't say if it will work, only have audigy2 zs cards

double click on the little speaker icon in your upper panel next to the date.
In the window that opens click on preferences, scroll down the list and look for a listing 'Audigy Analog/Digital Output Jack'.

If it's there then enable it and close the box out. Then in the main window will be a tab "Switches". Click on it and set it (Audigy Analog/Digital Output Jack) to the **opposite **of what it is currently.

Then go into system -> preferences -> sound and test movies and music.


If you want/need to get the full alsamixer from the terminal run this and look for number of card (usually 0
```

cat /proc/asound/cards
```

Then use this (substitute red if needed
```

alsamixer -c [COLOR="Red"]0[/COLOR]
```

---

### Post by slick666 on 2009-01-17
I'm looking at getting a sound card for my Mythbuntu system. I'm looking at getting an Audigy SE ([New Egg Link]("http://www.newegg.com/Product/Product.aspx?Item=N82E16829102010")). I'm interested how this works out. Are you using a stereo setup or a surround sound setup?

---

### Post by ditto1958 on 2009-01-31
I apologize for not being around for a week, but I haven't had any time to work on this. I still can't get this to work. Thinking about just starting over again. The computer in question is one that I use as sort of a "lab" computer for me to learn on.

The thing that irks me the most, though, is that on my previous install on the same machine the sound worked wonderfully. I can't remember having to do anything in particular to get it to work, either.

---

