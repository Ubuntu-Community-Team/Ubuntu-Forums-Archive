---
title: "flash player does not load"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by chethankrish on 2009-01-20
am using ubuntu from a week or so.. the flash player does not load many a times in mozilla firefox..

i have to close the existing firefox window and reopen the same... this resolves the issue.. 

but can someone please help me in understanding why is this happening and oblege.... thank you...

---

### Post by Temposs on 2009-01-20
It would be most helpful to know which version of Ubuntu you are using, and to perhaps get a screenshot of what it looks like when flash player isn't loading. To take a screenshot, you can press the Print Screen button, or go to Applications->Accessories->Take Screenshot.

---

### Post by pdtpatrick on 2009-01-20
sudo apt-get install ubuntu-restricted-extras.. 

make sure firefox is closed before doing that. After installation, try going to adobe.com and see if flash works.

---

### Post by kansasnoob on 2009-01-20
Knowing what version you're running is very important but just the basics, go to Accessories > Terminal and run:

```
sudo apt-get install ubuntu-restricted-extras
```

Then in Firefox go to the upper toolbar > Tools > Add-ons > Get Add-ons and search for (and install) Flashblock.

Yes, an older version of Flashblock is available in the repos but you want 1.5.7.1!

Beyond that we need more info!

---

### Post by chethankrish on 2009-01-21
i entered this lin of code in terminal...sudo apt-get install ubuntu-restricted-extras

 after a while am getting a screen as shown in screen shot-1... what am i suposed to enter to accept the license..

i tried  enter key , spacebar and even i left clicked on OK(using mouse).. but nothing is happening.. what am i supposed to do now?

the second screen shot gives my ubuntu version and other information.. sorry for not including these in my previous post...

---

### Post by chethankrish on 2009-01-21
please somebody help me..... please....

---

### Post by Corey4666 on 2009-01-21
downgrade to firefox2 :popcorn: thats how i fixed this very annoying problem

---

### Post by chethankrish on 2009-01-21
the problem wright now is.. what do i do to accept this license... i have to hit OK.. but i dont seem to know what key to press...

---

### Post by Corey4666 on 2009-01-21
emm... try to hit the TAB key then hit enter.

---

### Post by chethankrish on 2009-01-21
thanx for your help.. that worked....thank you...............

---

### Post by Corey4666 on 2009-01-21
Okay man, great! any problems just post back here! :p

---

