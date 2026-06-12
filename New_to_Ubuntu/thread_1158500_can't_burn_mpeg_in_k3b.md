---
title: "can't burn mpeg in k3b"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by mahmater on 2009-05-13
well friends,since I k3b cannot burn avi files as DVDs I convert it by tovid as mpeg file. now the problem is that k3b doesn't burn it and gives a message saying that necessary files are messing in the dvd video project

---

### Post by PocketDog on 2009-05-13
I use Devede to make the DVD files, and Brasero to burn them to disc. They've never failed me yet. Mind you, neither has K3b, even on Gnome. Are you sure you're outputting .VOB files which is what K3b will be looking for?

---

### Post by mahmater on 2009-05-14
well pocketdog, what happened is that all the output I got from Tovid after the conversion is *.mpeg. when I tried to burn it with k3b, the error message said: video project doesn't contain necessary files.

I tried to use devede but it required a space of more than 8 G (for a movie of 680 M),that's why I chose Tovid which required only 4.6 G.

---

### Post by PocketDog on 2009-05-15
K3b is looking for DVD files (vob, bup, ifo) which you'd find in a VIDEO_TS folder on a DVD. If you just want to put a mpeg or avi video on a disc as they are then choose 'data disc' in K3b, don't choose 'burn DVD files' (I'm not sure of the exact wording, I don't have K3b installed). If you're trying to make a 'real' DVD then you have to set the output size of the blank disc in Devede - it's a drop-down menu bottom left of Devede's main screen. Choose '4.7GB DVD' and the resulting files will be the right size and type for K3b to burn to a blank DVD

---

### Post by mahmater on 2009-05-15
thanks for the step-by-step help friend. for devede I already chose the right size but the obstacle is the 8.5 Gb space it required.

Now my question is; if I burned my mpg file as data disk can I still see it on a stand alone dvd ?

---

### Post by PocketDog on 2009-05-15
That depends entirely on the hardware. My DVD player will play mpeg and avi, but not wmv. Some machines won't play any video files, only  proper DVDs.

---

### Post by fooman on 2009-05-15
i have burnt *many* .avi's to dvds using devede and k3b.

i have never tried saving one as mpeg.

i choose "create an iso or bin/cue image,  ready to burn to a disc",  set the "media size" to 4.7 gbs and "adjust disc usage" to 99%

i am not sure where you think it needs 8.5 gbs of disc space....maybe i am missing something?

anyways,  after that i use k3b to "burn dvd iso image"

...works a treat!!  :p

after encoding and burning, a 700mb avi takes up about 2gbs on a dvd....therefore,  i can take two 700mb .avi files,  encode them to .iso and fit them both onto one 4.7gb dvd.

---

### Post by mahmater on 2009-05-15
well, It's been more than 4 nights that I try to burn george orwell's based movie 1984 into devede. now I want just to ask where do you find this last option . burn the file into an iso or cue...? when I start devede it just give you five or six options: dvd,vcd,china cd ...etc.

I tried it once more,and it says that it couldn't encode the file because I ran out of space. I have only 4.2 while more than 8 Gb is required.

/home/willis/Screenshot.png
/home/willis/Screenshot-1.png
/home/willis/Screenshot-2.png

---

### Post by fooman on 2009-05-15
when you start devede...choose "video dvd'

then when devede opens,  click on "advanced options" (near the bottom)....choose "create an iso..."

also,  while in the advanced options you can choose to "erase temporary files".  since you seem to be short on space.

and choose "use optimizations for multicore cpus"* if *you have a dual or quad core....it might help speed up the encoding process.

EDIT....your screenshots above are not working.

---

### Post by mahmater on 2009-05-15
i appreciate your valuable help? and I really learnt a lot from both of you friends. Now that I knew how to do things,may be the only solution left is to free my hard disk space ...I'll try to purchase tomorrow an extrenal HD.many thanks.

---

### Post by fooman on 2009-05-15
one other thing to consider....if you are in the U.S.,  you will need to change the "default format" to NTSC in order to play it in standard dvd players.

PAL or NTSC depends on your country...might want to check on that before you proceed.  ;)

---

### Post by Teber on 2009-05-15
just a thought. you may encounter mpegs of movies far longer than 2 hours playing time. devede has an option to split the movie and burn same to two dvds. you will find this option under properties at the files side in advanced options. maybe this will be useful to somebody out there...

---

### Post by mahmater on 2009-05-15
actually I'm from Morocco and I will check which of the two options actually work here.thanks for the remark.

i understand that many people use devede because of its practicality,but I still can't see how a movie of less than 700 M can require a space of nearly 9 Gb to be converted to a devede.Isn't it illogical?

---

### Post by mahmater on 2009-05-15
Now what can I do with this 1.8 Gb movie.mpg which I got from Tovid. can i still use in a way or in onother and be able to play it on a DVD?

---

