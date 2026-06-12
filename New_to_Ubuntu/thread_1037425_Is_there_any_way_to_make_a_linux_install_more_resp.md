---
title: "Is there any way to make a linux install more responsive running off of a USB flash"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by Andross707 on 2009-01-11
for X-mas I got a neat 64 GB USB flash drive. My first thought was to install Ubuntu on it so I can use Linux without taking up all of my laptop's hard drive. It generally works quite well in how I don't have to keep on installing Flash every time I want to use Youtube with a LiveCD but it gets slow when running off the flash drive. I have all of the graphics turned down to minimum and that seemed to help but sometimes simply opening a game of chess or having more than 2 tabs open in firefox led me to about a 2 minute freeze where I could not do anything (though the mouse was still responsive). My question is is there anyway to still have to persistence that running off of a flash drive gives while getting a little more speed (even having the speed I had running off of the liveCD was a little better.)

---

### Post by Xiong Chiamiov on 2009-01-11
In general, live systems try to keep as much in RAM as possible.  That's why you'll notice that, when running off of a live cd, applications will take a while to load, but will be fairly fast after that.

So then, the less RAM each application uses, the more applications you can have running.  Firefox in particular can be a memory hog sometimes, especially if you have any extensions installed.

---

### Post by earthpigg on 2009-01-11
[http://en.wikipedia.org/wiki/Puppy_linux](http://en.wikipedia.org/wiki/Puppy_linux)

> If the computer has at least 256 MB of RAM, the entire operating system and all the applications will run from RAM

when you boot from the live CD, it includes a pretty easy app that'll install puppy onto a thumb drive. ubuntu does this as well, as you know.

what is unique is that puppy also makes it pretty easy to boot from both the live cd and use the thumb drive to save files and stuff to - so it boots from the cd and loads the entire OS into ram... then saves stuff to the thumb drive that kinda 'lives' with the live cd and goes where it goes.

---

### Post by earthpigg on 2009-01-11
also, this:

> A unique feature that sets Puppy Linux apart from other Linux distributions is the ability to run a normal working environment on a write-once multisession CD. (It does not require a rewritable CD.) Puppy automatically detects changes in the file system and saves them incrementally on the CD.[3]When the CD is full, users can easily switch to a new CD while carrying over all their files and desktop environment. While other distributions offer Live CD versions of their operating systems, they do not allow programs to be permanently added nor do they allow files to be written to the CD.

---

### Post by mjheagle8 on 2009-01-11
puppy would be a good option here. also xubuntu would run way faster.

---

