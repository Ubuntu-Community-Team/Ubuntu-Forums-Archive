---
title: "DVD help"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by powell on 2009-01-10
I have a DVD, and when I put it in my ubuntu, it says its blank.


Any help?

---

### Post by powell on 2009-01-10
anyhelp guys?

---

### Post by Oak37 on 2009-01-10
What program did you use to burn data onto the DVD and were there any error messages?

---

### Post by powell on 2009-01-10
> **Oak37 said:**
> What program did you use to burn data onto the DVD and were there any error messages?

Nero, no errors

---

### Post by Oak37 on 2009-01-10
Can you check if it's blank on another PC?

---

### Post by powell on 2009-01-10
> **Oak37 said:**
> Can you check if it's blank on another PC?

Already checked twice, works fine on the other computer

---

### Post by Oak37 on 2009-01-10
Not too sure what could cause this. Perhaps it is the type of data itself that is causing the issue although I'm not sure how plausible that is.

---

### Post by powell on 2009-01-10
> **Oak37 said:**
> Not too sure what could cause this. Perhaps it is the type of data itself that is causing the issue although I'm not sure how plausible that is.

Thanks anyways mate

---

### Post by TransitMan on 2009-01-11
What system did you burn the DVD on?

In Ubuntu, you need libdvdcss2 to read DVDs. 
In synaptic, make sure you have "Proprietary drivers for devices" (restricted) and "Software restricted by copyright or legal issues" (multiverse) checked.

You may also want to get the Medibuntu repos as well, as these contain some program/packages for restricted/legal/license problems.

---

### Post by mkvnmtr on 2009-01-11
There are a number of file types that are not read if you don't download the proper library. Not knowing what you have I could not recommend. What I do is when I encounter a file type I can't read I do a search in the package manager to see if I can find something to help. I almost always wind up being able to read whatever it is. The bad thing is there are so many that I can't remember what they all are. But at least now it is rare to not be able to read a file or play a movie or music type.

---

