---
title: "[SOLVED] GtK record my desktop will not work"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by DigitalJedi on 2008-12-11
It says recordmydesktop has exited with status: 228
Description: Cannot open file for writing. I don't know what the problem is or how to fix it. I am on 8.10 intrepid ibex if that helps.

---

### Post by glennric on 2008-12-11
Check that you have write permission to the location you are trying to save the file.  Also check that you have write permission to the working directory.  To check the first click on "Save As", the check the second click on "Advanced" and look under the files tab.  The working directory should be set to /tmp by default.  That should work.  If it is not set there make it so, or change it to your home directory.

---

### Post by DigitalJedi on 2008-12-11
> **glennric said:**
> Check that you have write permission to the location you are trying to save the file.  Also check that you have write permission to the working directory.  To check the first click on "Save As", the check the second click on "Advanced" and look under the files tab.  The working directory should be set to /tmp by default.  That should work.  If it is not set there make it so, or change it to your home directory.

I tried that and still same message:confused:

---

### Post by DigitalJedi on 2008-12-11
> **DigitalJedi said:**
> I tried that and still same message:confused:
Nevermind I got it to work there was no free space where I was saving thanks

---

