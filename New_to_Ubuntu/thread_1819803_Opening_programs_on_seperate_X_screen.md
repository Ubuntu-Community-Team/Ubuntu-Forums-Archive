---
title: "Opening programs on seperate X screen"
date: 2011-08-06
forum: New to Ubuntu
---

### Post by Rikeshar on 2011-08-06
Hello everyone. This is probably a simple question, but I can't figure out the answer. I am using Ubuntu 11.04 and have an nVidia gpu. My gpu has an hdmi out and I've got it hooked up to my TV. I've got the tv set to a seperate x screen (as apposed to twinview). 

How can I open applications on the seperate x screen? When adding "DISPLAY = 0:2" etc. I can get it to open on a different virtual desktop (like if you do CTRL+ALT+LEFT) but not over on the tv!

Any ideas?

---

### Post by Rikeshar on 2011-08-07
bump, still looking for an answer

---

### Post by iseijin on 2011-08-07
Not sure but you might find this helpful 

[Start an application on second monitor?]("http://ubuntuforums.org/showthread.php?t=866139")

It's not an extended desktop like in windows when you can just drag a program (left or right) of your main screen, to the second screen is it?

---

### Post by Rikeshar on 2011-08-07
It's not, that would be the Twinview option. I'll give the link a look. Thanks.

---

### Post by Rikeshar on 2011-08-07
Yeah, unfortunately that link wasn't what I was needing. Anyone else have any ideas? Surely I"m not the only one using separate x screens.

---

### Post by LowSky on 2011-08-08
Switch to classic mode, Unity doesn't support separate X sessions yet..

---

### Post by Rikeshar on 2011-08-08
Turns out I wasn't using the variable right. I was trying to get Hulu Desktop to open on a separate x screen. Was doing "huludesktop DISPLAY=:0.1". If I do "DISPLAY=:0.1 huludesktop" then it does indeed open on a the other screen, however it's not centered, and not opened full screen like it should :(

Let try switching to classic and see what happens.

---

### Post by Rikeshar on 2011-08-08
Well crap. Just using Ubuntu Classic didn't help. Still opening up windows funny, and without title bars. Only way to get them to open properly is to run Ubuntu Classic (no effects).

---

