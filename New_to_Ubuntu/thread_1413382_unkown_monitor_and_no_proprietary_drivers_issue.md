---
title: "unkown monitor and no proprietary drivers issue"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by swapnil0545 on 2010-02-22
Hello guyz,
I m trying to shift from winxp to ubuntu.so, I installed Ubuntu 9.10.
Hope the forum members help me :KS


My graphics are not effective, when I go to Display> it shows me unkown monitor.

When I go to Hardware drivers> It shows me no proprietary drivers present.its completely blank.

How should I fix this?

---

### Post by cariboo on 2010-02-23
What graphics hardware are you running? Do you have all the repositories enable in System->Administration->Software Sources?

---

### Post by thecliff on 2010-02-23
What make/model video card do you have?  Chances are, there are open source drivers for your video card.  If there are not, you will have to install the proprietary drivers from the maker.

---

### Post by t1nm@n on 2010-02-23
if your card is nvidia get the nvidia driver from their site nvidia.com. Then install it with the command sh <package>

before that if it is necessary do this before install chmod 777 <package>
the nvidia package freom the repository is 7 megs... it's a also a safe choice...

even better if u install envyng it will automatically install your driver...

best of luck..

---

### Post by swapnil0545 on 2010-02-23
> **cariboo907 said:**
> What graphics hardware are you running? Do you have all the repositories enable in System->Administration->Software Sources?

Yes all of them are checked!


I dont have a graphic card.Its inbuilt vga of my motherboard,
something VIA/S3G unichrome.I dont remember but its 865 motherboard I think.

---

### Post by 3rdalbum on 2010-02-23
The Via Unichrome graphics processors are notorious for being barely usable on Linux. Although I don't have one, I believe that you are already running the only driver that can be used with your chipset.

Via is not exactly open-source-friendly.

Sorry. I hope somebody else has some better news.

---

### Post by swapnil0545 on 2010-02-24
I havent got it working yet*
Bump!

---

### Post by halitech on 2010-02-24
try the info here

[http://ubuntuforums.org/showthread.php?t=1340466](http://ubuntuforums.org/showthread.php?t=1340466)

---

### Post by swapnil0545 on 2010-02-24
Mine is P4M800 not 890.

---

### Post by Mark Phelps on 2010-02-25
> **swapnil0545 said:**
> Mine is P4M800 not 890.

Did you even TRY the suggested solution?

Asking, because according to the S3 drivers page, the two chipsets use the same driver.

---

### Post by swapnil0545 on 2010-02-26
> **Mark Phelps said:**
> Did you even TRY the suggested solution?

Asking, because according to the S3 drivers page, the two chipsets use the same driver.
Tried it.
Didnt worked
I also tried changing it to 800, even that didnt worked.

---

### Post by Mark Phelps on 2010-02-26
Well, looks like your out of luck regarding drivers.

The link I found to the S3 Linux drivers page only lists 430 and 440:

[http://www.s3graphics.com/en/drivers/index.aspx]("http://www.s3graphics.com/en/drivers/index.aspx")

---

