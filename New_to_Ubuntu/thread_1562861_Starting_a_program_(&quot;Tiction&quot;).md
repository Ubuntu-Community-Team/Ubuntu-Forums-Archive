---
title: "Starting a program? (&quot;Tiction&quot;)"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by Crazychicken on 2010-08-28
This is the thing: it's a kind of music generator.
[http://www.shoddyandquick.com/software/tiction/](http://www.shoddyandquick.com/software/tiction/)
I wanted to create some music to go along my Evolvotron creations... but anyway: it's not working. 

I extracted it, but when I open the file "Tiction" it does nothing. Choosing "run in terminal" it writes a lot of stuff starting with > java.lang.IllegalArgumentException: GLDrawableFactory.chooseGraphicsConfiguration() was not used when creating this Component
I do have "open JDK java 6 runtime" according to the Software Center.

---

### Post by Crazychicken on 2010-08-30
Bump. er, I'm allowed to bump, right? :)

---

### Post by sandyd on 2010-08-30
> **Crazychicken said:**
> This is the thing: it's a kind of music generator.
[http://www.shoddyandquick.com/software/tiction/](http://www.shoddyandquick.com/software/tiction/)
I wanted to create some music to go along my Evolvotron creations... but anyway: it's not working. 

I extracted it, but when I open the file "Tiction" it does nothing. Choosing "run in terminal" it writes a lot of stuff starting with 
I do have "open JDK java 6 runtime" according to the Software Center.
have you tried using the sun/oracle java instead?

---

### Post by Crazychicken on 2010-08-31
It's proving a bit hard: the software center wants to "update" to install it, but shows me no button, the self extracting package from the Java website tells me "rpm not found" :(

---

### Post by chaanakya_chiraag on 2010-08-31
I'm getting the same exact problem (namely the IllegalArgumentException).  I think it's a Tiction problem, because Java *is running*, but it's throwing an error, which indicates it's a problem with the program itself.  If you know Java, you could probably cajole it to run by looking at the error and playing around with the source file.  You could also check out Musik, my program for creating music, at the link in my signature.  However, unlike Tiction, Musik is a text-based system, which means you enter in the notes you want the program to play in a text file and run the program on the file.  If you are familiar with LaTeX (or TeX), it's kinda like that, but for music.

---

### Post by Crazychicken on 2010-08-31
Aww. At least I know. I'll try the windows version in Wine.
I actually wanted generative music to go with generative images, so your program wouldn't do (plus I use italian music notation, not letters ^^')

---

### Post by Crazychicken on 2010-09-01
When I try it in Wine it tells me "Error file not found" then "Error calling ShellExecuteEx()" I really have no idea what it's on about :/

---

