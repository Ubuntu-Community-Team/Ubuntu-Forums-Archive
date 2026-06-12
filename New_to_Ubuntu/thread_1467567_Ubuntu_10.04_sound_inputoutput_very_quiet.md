---
title: "Ubuntu 10.04 sound input/output very quiet"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by fallenashes on 2010-04-30
When I upgraded to 10.04, my sound was very quiet, but the sound is all the way turned up.  Also when I got on Skype my friend said he could barely hear me but he could hear some white noise.  How can I fix this.

---

### Post by wookiefoot on 2010-04-30
My first thought would be to make sure the "front" sound channel is at 100%, as I have found that it tends to default to 80%. 
Open a terminal, enter "alsamixer" (without quotes), go to whichever channel you want to edit with the left & right arrow keys, change the level with the up & down arrow keys. 

Hope this helps!

---

### Post by vangelas on 2010-05-01
Same problem, although I think the mic is OK. Everything is maximised at alsamixer.

---

### Post by edauenhauer on 2010-05-04
When you open alsamixer in the terminal, press F6 to select your sound card.  On mine, the "speaker" was set to 0, and turning that up to 100 made all the difference.

---

### Post by hodgkinr on 2010-05-20
I had the same problem and the alsamixer suggestion by edauenhauer fixed it.  Also my headphone jack didnt work in 9.10 and works perfect now.

---

### Post by fallenashes on 2010-06-10
> **edauenhauer said:**
> When you open alsamixer in the terminal, press F6 to select your sound card.  On mine, the "speaker" was set to 0, and turning that up to 100 made all the difference.

Worked like a charm!

---

### Post by monarchheels on 2010-08-08
I was having this same problem after upgrading to 10.04. 
Turns out my speakers were also set to zero.
Thanks for the tip!!

---

