---
title: "hi i can not open raw files from my new digital camera"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by blake7 on 2011-01-15
hi 
i have just brought
a panasonic dmc lx5 camera
which shots raw i have tryed loading the software which comes with the camera but it will not load onto ubuntu.

the file type is called .rw2
can any one help me open this file

thank you 

ps i have tryed gimp and it say frist file
 

then 


Opening '/home/dude/Desktop/photo 12111 /P1000458.RW2' failed:

Procedure 'file-ufraw-load' returned no return values

---

### Post by Nickjpost on 2011-01-15
Hi there, check this out:
[http://www.ubuntuka.com/raw-files-ubuntu-dlsr-camer/](http://www.ubuntuka.com/raw-files-ubuntu-dlsr-camer/)

---

### Post by blake7 on 2011-01-15
how can i tell if that has been successful??

that you 
ps
i just tryed it and it still say the same message as before

---

### Post by Nickjpost on 2011-01-15
Check that file on a different system that you know will successfully open the file....the problem may be the file itself.

---

### Post by blake7 on 2011-01-15
how can it be the file it self the camera is brand new ??
the sd card i have is a little old but seem fine 
all the jpegs are good

cheers

---

### Post by blake7 on 2011-01-15
could it have something to do with the way im coping them on to my hard drive 

it seem odd if it where im just loading them from sd card

---

### Post by blake7 on 2011-01-15
its says

frist 

/home/dude/Desktop/photo11111/P1000585.RW2: Corrupt data near 0x7de00

then 

Opening '/home/dude/Desktop/photo11111/P1000585.RW2' failed:

Procedure 'file-ufraw-load' returned no return values

does this mean anything to you??/
thank you

---

### Post by blake7 on 2011-01-15
its says

frist 

/home/dude/Desktop/photo11111/P1000585.RW2: Corrupt data near 0x7de00

then 

Opening '/home/dude/Desktop/photo11111/P1000585.RW2' failed:

Procedure 'file-ufraw-load' returned no return values

does this mean anything to you??/
thank you

---

### Post by blake7 on 2011-01-15
its says

frist 

/home/dude/Desktop/photo11111/P1000585.RW2: Corrupt data near 0x7de00

then 

Opening '/home/dude/Desktop/photo11111/P1000585.RW2' failed:

Procedure 'file-ufraw-load' returned no return values

does this mean anything to you??/
thank you

---

### Post by Nickjpost on 2011-01-15
I didn't think so either, just wanted to rule out the possibility. sometimes, my home video gets weird when I copy them from SD. I'll research a little more
It may be the SD card itself when the data was saved
 
Is this for only that particular file for all of the files?
Are they playable/viewable on the camera?
The output tells me that the file is corrupt in some way

---

### Post by blake7 on 2011-01-15
ok cool but that mean i <snip> lost all my raw file
i deleted them from my sd card

is this so

---

### Post by blake7 on 2011-01-15
has ubuntu destroyed thoes raw files???

cheers

---

### Post by Elfy on 2011-01-15
Please stop bumping your thread.

---

### Post by no2498 on 2011-01-15
drag an drop 1 on the desk top see if gmip will open it then

---

### Post by gordintoronto on 2011-01-15
Use Administration/Synaptic to install dcraw.

---

### Post by I2k4 on 2011-01-15
Gimp needs a UFRaw plug in:

[http://ufraw.sourceforge.net/Install.html](http://ufraw.sourceforge.net/Install.html)

You'll have to research to see if the RAW files your camera produces are supported - there is very often a time lag between new cameras and the RAW file support in software - it's unfortunate that "RAW" is not a standard but keeps being changed for different models by different manufacturers, and newer cameras often cause problems for a while.

---

### Post by jcolyn on 2011-01-15
Have you tried Rawtherapee? It opens nearly all raw files..

```
sudo apt-get install rawtherapee
```

---

### Post by blake7 on 2011-01-21
will the raw files i have loaded on to ubuntu be lost for ever

---

### Post by gordintoronto on 2011-01-21
> **blake7 said:**
> will the raw files i have loaded on to ubuntu be lost for ever

No, you just need to read some of the messages people have sent you.

---

