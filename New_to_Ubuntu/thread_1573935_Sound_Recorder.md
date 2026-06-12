---
title: "Sound Recorder"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by daniell59 on 2010-09-13
I just hooked up a microphone. I tried using sound recorder. Nothing happened. I would appreciate help in setting it up in Ubuntu 9.10 64

Thanks

---

### Post by BugBuster on 2010-09-13
In a terminal type:
```
$alsamixer
```
Check the volume levels for the particular interface.
Use the left-right arrow keys to move around and use up-down arrow keys to turn up the volume.
Check if it works.

---

### Post by daniell59 on 2010-09-13
> **BugBuster said:**
> In a terminal type:
```
$alsamixer
```
Check the volume levels for the particular interface.
Use the left-right arrow keys to move around and use up-down arrow keys to turn up the volume.
Check if it works.

Your code worked when I left out the dollar sign but I could not find the arrows that you mentioned. Also, I could not change anything in that screen.

Thanks

---

### Post by Joe of loath on 2010-09-13
You use the arrow keys. Right and left to select different sections of the mixer, up and down to change the volume.

---

### Post by Nanix on 2010-09-13
> **daniell59 said:**
> Your code worked when I left out the dollar sign but I could not find the arrows that you mentioned. Also, I could not change anything in that screen.

Thanks

He means the arrows on your keyboard. Use those to go through all of the adjusters. In order to change the page press the tab key on your keyboard or F3, F4, F5.
F3: Playback Page
F4: Capture Page
F5: All Page (includes all the adjusters)

You will find the adjusters concerning the mic on the "Capture Page".
I suggest turning up the boosts and L/R Capture. Most importantly, play around with the input settings. Select one of these. (To raise and adjuster or make a selection use the up/down arrow keys on your keyboard)

While you mess with settings test to see if that gets the sound recorder working.

---

### Post by daniell59 on 2010-09-13
I turned up everything that I could. Still no progress.
How can I determine whether my mike is being detected?

Thanks

---

### Post by daniell59 on 2010-09-13
Success!

I went to sound preferences and changed it to mike 2.

Thanks to all for your kind assistance.

---

