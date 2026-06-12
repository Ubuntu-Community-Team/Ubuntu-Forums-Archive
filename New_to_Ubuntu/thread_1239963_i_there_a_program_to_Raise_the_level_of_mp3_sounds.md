---
title: "i there a program to Raise the level of mp3 sounds?"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by MBG1987 on 2009-08-14
my mp3 sounds are to low ! so is there any program on ubuntu to rise the level of these mp3 sounds ? tnx

---

### Post by cmannnn on 2009-08-14
have you tried audacity? it can edit the songs volume

---

### Post by MrWES on 2009-08-14
> **MBG1987 said:**
> my mp3 sounds are to low ! so is there any program on ubuntu to rise the level of these mp3 sounds ? tnx


Are your levels turned up on PCM? Right click on the volume control in the upper right hand corner of the notification area | Open Volume Control. Adjust the PCM setting upwards and see if that helps. Otherwise there is a program called mp3gain, and it has a Java based GUI:

[http://ubuntuforums.org/showthread.php?t=329854]("http://ubuntuforums.org/showthread.php?t=329854")

---

### Post by colau on 2009-08-17
> **MBG1987 said:**
> my mp3 sounds are to low ! so is there any program on ubuntu to rise the level of these mp3 sounds ? tnx
First check the volume control.
```

sudo aptitude install audacity

```

---

### Post by niteshifter on 2009-08-17
Hi,

Yes, mp3gain. But do check your system's volume settings first.

```
sudo apt-get install mp3gain
```

Next step:
```
man mp3gain
```

Usage (for plain level increase):
```
mp3gain -g N *somefile.mp3*
```
Where N is a number, greater than 1 and less than 255. Experiment with small numbers to start (like 10 or less) lest you pop speakers or eardrums. If the program warns about clipping consider that there is something amiss with your sound hardware.

---

