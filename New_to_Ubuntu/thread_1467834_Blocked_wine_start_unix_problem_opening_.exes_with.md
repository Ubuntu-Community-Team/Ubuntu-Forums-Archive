---
title: "Blocked: wine start /unix problem opening .exes with Wine"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by thejakeman on 2010-05-01
When I try to open an .exe I get the following error message:

```
The file '/home/jake/Downloads/shotgun_funfun.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.
```

I don't know anything about wine at all except for if you open up an .exe with it it should install it/run it. What am I missing? Is there a solution to this?

---

### Post by StuM on 2010-05-01
I had this problem when trying to install Spotify in WINE.  Try right clicking on the .exe file then selecting properties then select the permissions tab.  On that tab you should see "Allow executing file as program" if you check the tickbox next to that statement it should allow the file to be executable.  (At least it did for me anyway)

---

### Post by garretthylltun on 2010-05-03
Also see the following thread for more information:

[http://ubuntuforums.org/showthread.php?t=1467914&highlight=blocked%3A+wine+start](http://ubuntuforums.org/showthread.php?t=1467914&highlight=blocked%3A+wine+start)

---

### Post by SpatzST on 2010-05-04
wow, this is exactly what i wanted... perfect :D

---

### Post by noah_vale on 2010-05-04
> **StuM said:**
> I had this problem when trying to install Spotify in WINE.  Try right clicking on the .exe file then selecting properties then select the permissions tab.  On that tab you should see "Allow executing file as program" if you check the tickbox next to that statement it should allow the file to be executable.  (At least it did for me anyway)

[FONT="Comic Sans MS"]Thank you for this piece of advice. You've just saved me from a lot of head scratching![/FONT]

---

### Post by xumuk37 on 2010-05-04
have you done chmod +x file.exe before you try to run it as executable?

---

### Post by thejakeman on 2010-05-06
> **xumuk37 said:**
> have you done chmod +x file.exe before you try to run it as executable?

what the heck does that mean?

---

### Post by WinterRain on 2010-05-06
Right click the exe and go to properties then permissions tab. There's a box to check off called "allow executing file as program" .

---

### Post by supernoodle on 2010-06-29
> **WinterRain said:**
> Right click the exe and go to properties then permissions tab. There's a box to check off called "allow executing file as program" .

Thank you for this short simple answer versus having to use the terminal as so many other place say. I just installed Ubuntu to run Boxee and decided to try and run air video in wine. I am just not at all familiar with Ubuntu, but I should have been able to figure this one out, thanks again!

---

### Post by synchronize on 2010-12-27
didn't work for me ... tried all the possible method.. already did the gksu gedit the wine.dekstop file  thingy..still.. fruitless..

---

### Post by rirchse on 2013-05-04
Thank you very much [**[COLOR=#AEA79F]WinterRain[/COLOR]**]("http://ubuntuforums.org/member.php?u=1050851").

---

### Post by QIII on 2013-05-04
If a post is older than a year or so and hasn't had a new reply in that  time, instead of replying to it, create a new thread. In the software  world, a lot can change in a very short time, and doing things this way  makes it more likely that you will find the best information. You may  link to the original discussion in the new thread if you think it may be  helpful.

*Thread** closed***

---

