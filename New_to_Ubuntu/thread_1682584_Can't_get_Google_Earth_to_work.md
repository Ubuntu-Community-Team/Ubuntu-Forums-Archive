---
title: "Can't get Google Earth to work"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by lance23dillon on 2011-02-06
I downloaded Google Earth and it comes up in applications under internet, but when I click on it nothing happens. I've tried reinstalling it and it had the same results.

There are no errors popping up or anything, nothing happens.

---

### Post by Joe of loath on 2011-02-06
how did you install it? I tried the google installer, which didn't work, but the medibuntu version did.

---

### Post by mick8985 on 2011-02-06
[https://help.ubuntu.com/community/GoogleEarth#Using make-googleearth-package](https://help.ubuntu.com/community/GoogleEarth#Using make-googleearth-package)

---

### Post by Elfy on 2011-02-06
Try running it from a terminal 

```
googleearth
```

If you get 
```
/usr/lib/googleearth/googleearth-bin: not found
```

Try installing lsb-core

```
sudo apt-get install lsb-core
```

Then try again.

---

### Post by lance23dillon on 2011-02-06
I haven't tried the medibuntu. where do I go to get it?

---

### Post by Elfy on 2011-02-06
[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository)

---

### Post by lance23dillon on 2011-02-06
Okay, now its stuck on a package configuration screen and isn't doing anything.

---

### Post by Elfy on 2011-02-06
Use tab to get to the Ok button and enter.

Did installing lsb-core not work then - or did you just go for installing from medibuntu - that said I needed to install it when I installed it from medibuntu.

If it still fails to work - go back to post #4

---

### Post by fabricator4 on 2011-02-06
> **lance23dillon said:**
> Okay, now its stuck on a package configuration screen and isn't doing anything.

Wheee! that was fun.  I used [these instructions]("https://help.ubuntu.com/community/GoogleEarth#Using%20make-googleearth-package") and it worked fine.  I didn't see one single screen that looked like your screen shot however...

Basically, the steps are:

1) install the "installer" package. I used Ubuntu Software Center

2) "sudo apt-get install lsb-core" as per the instructions

3) "make-googleearth-package --force" also as per the instructions
Ignore the errors about not being able to extract names and version numbers. The make took several minutes to complete but resulted in the production of another .deb file: googleearth_6.0.1.2032+0.5.7-1_i386.deb. I simply did this in ~/ and that's where it made the deb package.

4) Install the new deb package.  I simply double clicked on it in Nautilus.  The package installer opened and installed the deb plus two other dependancies.

5) Go zooming around the planet, stick a placemarker on your house, look at the Eiffel Tower etc.

Chris.

---

### Post by lance23dillon on 2011-02-06
Awesome, its up and running now. 

Thanks for all the help you guys!!!

---

