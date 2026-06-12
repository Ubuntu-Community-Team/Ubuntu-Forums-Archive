---
title: "Problems with mp3 player"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by winstont11 on 2009-05-06
Hello, I'm trying to add songs to my MP3 player and the process I'm taking is not allowing me to do so. I connect the MP3 player to the computer and then I click on the icon that comes on the screen "Sansa e250R." From there I open the music folder and I open a separate file that holds the songs I have on my computer. When I click and drag them into the Sansa folder it gives me this error. "There was an error copying the file into /media/Sansa e250R/MUSIC." & "Error opening file '/media/Sansa e250R/MUSIC/Atreyu - When Two Are One.mp3': Read-only file system."

Thanks for the help : )

---

### Post by logos34 on 2009-05-06
try running

sudo chmod -R +w /media/Sansa e250R/MUSIC

---

### Post by winstont11 on 2009-05-06
thank you! I'll try that

---

### Post by logos34 on 2009-05-06
jus noticed a gap...might have to put the middle part in quotes or escape:

[COLOR="Red"]"[/COLOR]Sansa e250R[COLOR="Red"]"[/COLOR]

Sansa[COLOR="Red"]\[/COLOR] e250R

---

### Post by winstont11 on 2009-05-07
I  tried this command: sudo chmod -R +w /media/"Sansa e250R"/MUSIC
however, it just brought up a list in the terminal of the current songs I have on my MP3 player.  I still cannot add new songs... I dont know what I'm doing wrong.

---

### Post by logos34 on 2009-05-07
you can try 

sudo chmod -R 777 /media/"Sansa e250R"/MUSIC

but that probably won't work either.  Hopefully some DAP expert out there will have the solution

---

### Post by winstont11 on 2009-05-07
> **logos34 said:**
> you can try 

sudo chmod -R 777 /media/"Sansa e250R"/MUSIC

I tried that to, but to no avail.  Thank you for trying to help : )

---

### Post by colau on 2009-05-07
> **winstont11 said:**
> I tried that to, but to no avail.  Thank you for trying to help : )
I had same problem.
Is your problem solved?

---

### Post by winstont11 on 2009-05-07
> **colau said:**
> I had same problem.
Is your problem solved?

Hey, no it hasn't been solved yet.

---

### Post by winstont11 on 2009-06-16
Can anyone help with this?

---

