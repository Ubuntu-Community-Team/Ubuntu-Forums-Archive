---
title: "Activating Restricted Drivers"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by helenka on 2009-01-06
Hi - I am a first time Ubuntu user and have just installed the latest version :D I went to enable my restricted drivers so I could get the advanced desktop effects but every time I click the Activate button a little progress bar comes up saying downloading and installing and then nothing happens - the box says they're still not activated and I can't get the advanced effects menu. Can anyone help?

Thanks :)

---

### Post by oldos2er on 2009-01-06
Do you have a working internet connection?

---

### Post by JoshuaRL on 2009-01-06
Alright, are you connected to the internet on that computer?  If so, could you do a couple commands for me in the terminal?
```

sudo apt-get update
sudo apt-get update

```

This will just update the system and tell us if your APT settings are correct.

---

### Post by theinnercityhippy on 2009-01-06
(Don't forget to check that the graphics card is opengl compatible. working on another prob but thought I'd mention it)

---

### Post by helenka on 2009-01-06
Hi :) Yes I do have a working internet connection - sudp apt-get upgrade seems to run fine both times - I've included the output below if that helps. The card is an ATI Mobility Radeon X1400

---

### Post by JoshuaRL on 2009-01-06
How about this, restart your computer.  For the proprietary drivers to work, sometimes X has to restart.

Also, I'm dumb.  I meant this:
```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by helenka on 2009-01-06
It seems to be working fine - although it'll be a while before it's finished *yawn* ;)

---

### Post by JoshuaRL on 2009-01-06
Yeah, it may have a lot of updates to install.  And then when you restart it, go to System->Administration->Hardware Drivers.  See if the proprietary ones are activated.

---

### Post by alphaakenny1 on 2009-01-06
Hey thats the same card i have do

> sudo apt-get install xorg-driver-fglrx

Then you can activate it

---

### Post by JoshuaRL on 2009-01-06
> **alphaakenny1 said:**
> Hey thats the same card i have do



Then you can activate it

Did you have to do that in Intrepid?  Or did you get a chance to try the Hardware Drivers GUI?

---

### Post by alphaakenny1 on 2009-01-06
No I have done this on dapper, edgy, fiesty, gutsy, and on hardy...I haven't tried intrepid...but I'm guessing it will work.

---

### Post by JoshuaRL on 2009-01-06
Okay, have you tried using the Hardware Drivers from the System menu before?

---

### Post by helenka on 2009-01-06
that worked perfectly - thanks very much :D

---

### Post by JoshuaRL on 2009-01-06
> **helenka said:**
> that worked perfectly - thanks very much :D

Sweet!  You might want to go on this page to Thread Tools and click Mark Thread as Solved.  That way other people searching the forum with this problem can tell what worked for you.

---

