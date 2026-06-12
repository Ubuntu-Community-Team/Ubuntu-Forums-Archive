---
title: "Problems with Wine"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by spribo on 2009-08-14
I have Ubuntu Jaunty and Wine installed. I tried to run the installer of a scanner driver (Canoscan LiDE 100), but after a while Wine sais "Runtime Error: The program has requested the Visual C++ runtime to terminate in an unusual way". How could I fix it?

---

### Post by Bachstelze on 2009-08-14
First off, are you sure the program you're trying to run is compatible with WINE?

---

### Post by spribo on 2009-08-14
I am not sure, but why does this error appear? I mean, if there was an issue of compatibility, the application shouldn't run at all, right? Excuse me, I don't know in depth Wine yet, so I could be wrong.

---

### Post by Mark Phelps on 2009-08-14
You can't use Wine to install devices or drivers using MS software; it is only an interface layer that allows SOME MS Windows programs to run.  You have to use Linux drivers for your devices.

---

### Post by RedSingularity on 2009-08-14
Check if it is compatable through [this]("http://appdb.winehq.org/")

---

### Post by pedro3005 on 2009-08-14
Yes, as above, you can't use WINE to install drivers. Maybe it's even working out of the box, have you tried using XSane? If not, search google for "ProductModel + ubuntu".

---

### Post by spribo on 2009-08-14
Unfortunately, it isn't compatible with Wine, and this scanner isn't supported by Sane. Is there any way to make the scanner work under Ubuntu Jaunty?

---

### Post by Liolikas on 2009-08-14
Canon do not know that Linux exist, but still try your luck here:
[http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)

---

