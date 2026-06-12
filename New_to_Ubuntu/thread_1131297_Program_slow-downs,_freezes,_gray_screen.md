---
title: "Program slow-downs, freezes, gray screen"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by javadiva on 2009-04-20
I've been having problems for quite some time with my laptop.  It happens with any program.  I will be working and I left click on something.  The program window goes gray (I can still see everything) and it takes forever for the program to respond.  Sometimes I end up closing that program in which case I get a window telling me that the program is not responding and giving me the option to force a quit or not.  This is really frustrating.  It's doing it right now when I search for posts.  What is going on?

---

### Post by billgoldberg on 2009-04-20
It says under your name that you are using Ubuntu 8.04 (hardy heron).

Is that correct?

Does it mostly happen in firefox?

Is there any type of flash content displaying on any of the websites you have open?

---

### Post by porchrat on 2009-04-20
What are the specs of the machine you are running Ubuntu on?

Your machine may be running something you are not aware of that is chewing up the resources.

Open a console window (Applications --> Accessories --> Terminal) and enter the command "top" into the command line. This will provide a table of processes that may shed some light on whether or not something is using up the resources of your machine.

---

### Post by javadiva on 2009-04-20
It does happen in Firefox but it also happens with Open Office and even Rythmbox.  Yes, I am running Hardy Heron.

---

### Post by javadiva on 2009-04-20
It's an Acer Aspire 5610.  I didn't have this problem until about 6 months after I got this machine.  It's been getting worse over the months.

---

### Post by javadiva on 2009-04-20
I pulled up the table of processes.  It changes every two seconds.  I don't know what most of the stuff running is, like compiz.real, Xorg and init.

---

### Post by krzysz00 on 2009-04-20
How old is this laptop?

---

### Post by porchrat on 2009-04-22
> **javadiva said:**
> I pulled up the table of processes.  It changes every two seconds.  I don't know what most of the stuff running is, like compiz.real, Xorg and init.

You don't need to be interested in it changing. If something is using a whole lot of resources it will be at the top of that list. The CPU usage will be high.

If not then I have no idea what could be wrong.

---

### Post by shadowlands on 2009-04-22
I have an acer 5570z  and my computer is acting up just like yours.

---

