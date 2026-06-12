---
title: "Skype Strange Problem"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by ketenev on 2009-08-21
Sorry for disturbing you all guys but i am beginner in ubuntu and i have many serious problems with it , so i am asking for your help . First of all the biggest problem that i have is     when i start skype it starts , but is [COLOR=#CC0000][/COLOR]_******_immediately off . I have tried to reinstall it but no effect i have tried to update my system but no effect , so now i am asking for your help ....Thank you!
P.S Forgive me but my english is not very good

---

### Post by JDShu on 2009-08-21
Hi, and welcome to the forums!

Some more information would be helpful, like what version of Ubuntu do you have, and how did you install skype?

---

### Post by diablo75 on 2009-08-21
First thing you should do is run skype from Terminal so any error messages will be printed on screen.

Applications>Accessories>Terminal

In terminal, just type "skype" at the prompt and press Enter.  (Remember, linux terminal is CASE-SENSITIVE so type the word skype in all lowercase, and not "Skype").

If Skype crashes, have a look at the terminal window to see what appears.  Copy and paste the output from the terminal into this forum thread for us to look at and decide what to do next.

---

### Post by ketenev on 2009-08-22
Thank you Diablo75 :!:    The error is   "Fatal: Cannot mix incompatible Qt libraries aborted"   :?:

---

### Post by PGScooter on 2009-08-22
If you don't end up figuring out how to solve that error, I would suggest installing skype-static and skype-static-oss. The last one worked for me. But I'm guessing you'll get the same errors from all three. Note that to install one of those two, you need to add the medibuntu repository.

---

### Post by diablo75 on 2009-08-22
> **ketenev said:**
> Thank you Diablo75 :!:    The error is   "Fatal: Cannot mix incompatible Qt libraries aborted"   :?:

Well I'm not too sure what to do with that error message, but I am wondering (thanks to another poster):

What version of Skype are you using?
How did you install Skype (download from skype's website?  Use 3rd party repository like Medibuntu?)
What version of Ubuntu are you using?

---

### Post by ketenev on 2009-08-23
I downloaded it from skype website its version 2.0.0

---

### Post by PGScooter on 2009-08-23
ketenev,

If you are having problems with that version, I would uninstall it and install it using apt-get or synaptic and try that:
```
sudo apt-get skype
```

---

### Post by ketenev on 2009-08-23
Instaling it from terminal dosen't work , it shows me another error  "Invalid operation":icon_frown:

---

### Post by PGScooter on 2009-08-23
sorry ketenev!!!! what a silly mistake of mine :(
Here is the correct code:

```
sudo apt-get install skype
```

see if that works. Did you uninstall the other version?

---

### Post by ketenev on 2009-08-23
I did it in with "sudo apt-get install skype" but there is another error comming out "Pack skype a candidate of installation is away" or somethig like that ..... not very sure because my Ubuntu is in Bulgarian and some Error Messages are in Bulgarian so there is possibility to be wrong translated.........

---

### Post by PGScooter on 2009-08-23
> **ketenev said:**
> I did it in with "sudo apt-get install skype" but there is another error comming out "Pack skype a candidate of installation is away" or somethig like that ..... not very sure because my Ubuntu is in Bulgarian and some Error Messages are in Bulgarian so there is possibility to be wrong translated.........

ok, I think that's because you have to add the skype repository. I would go here: [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype) and follow the instructions for adding the medibuntu repository.

---

### Post by PGScooter on 2009-08-28
Did you get it working? You can download 2.1 beta if you want. Go here:

[http://www.skype.com/download/skype/linux/](http://www.skype.com/download/skype/linux/)

once you get it, just use ```
sudo dpkg -i debname.deb
``` to install

---

