---
title: "Open office word processor crash"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by Jonathan E-D on 2009-05-13
Hello, I'm a complete beginner.  Every time I want to open an an existing Open Office word processor document (or even to start a new document) a screen appears where I must go through a document recovery process (recover and finish must be clicked each time.  Normally I put up with this because it works, but this time I have a problem: I am now advised that Open Office has crashed, and that the documents will be recovered.  Nothing is recovered though. The document I want to open appears for a fraction of a second and then disappears from the screen; the same happens with a new document and even an email document.  I have the impression something is wrong with the word processor.  How do I repair it?

---

### Post by okey666 on 2009-05-13
You could try reinstalleing writer (OpenOffice word processor):
```
sudo aptitude reinstall openoffice.org-writer

```

---

### Post by aeiah on 2009-05-13
something is indeed wrong with it. the first thing to do perhaps is to launch it from the terminal, that way any immediate errors will get reported back to the terminal and you can go from there.

ive never encountered that kind of error but it would be hard to believe you're the only person affected. hopefully with enough searching you'll find someone who has a solution.

anyway, to launch open office with a document in a terminal you'd do:
```

openoffice.org documentname.odf

```

note that my open office 3 on ubuntu 9.04 works fine but i still get errors in the terminal, namely:
```

javaldx: Could not find a Java Runtime Environment! 
Please ensure that the package openoffice.org-java-common is installed.
If it is already installed then try removing ~/.openoffice.org/3/user/config/javasettings_Linux_*.xml

** (soffice:769): WARNING **: unable to get gail version number

```

so if you get the same, it probably isnt what's causing the problem (but you could always fix it as it suggested)

---

