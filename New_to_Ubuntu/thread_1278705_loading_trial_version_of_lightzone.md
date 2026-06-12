---
title: "loading trial version of lightzone"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by Ewan Cameron on 2009-09-29
I want to trial the linux version of the  commercial image editing software lightzone. I downloaded a "tar.gz" file and extracted its contents to a folder called "lightzone" in my home folder. This folder contains a number of files with various suffixes including .so and .jar and various other icons that may be folders or that have no suffixes.  I have clicked on a number of these, and tried to use the add/remove software utility, but made no progress. I have also looked at Keir Thomas's pocket guide to ubuntu, but he seems to envisage only ever getting software from repositories, and not from commercial providers.

I am stuck and would appreciated advice on what to try next.

cheers

kc

---

### Post by tomBorgia on 2009-09-30
Hi,

The .jar file is a java file... make sure you've java installed and try and run it - Open terminal and type ```
cd lightzone/
java filename.jar
``` And see what happens...

As it's commercial software it's not going to be supplied by the repos as they only supply opensource software... "the GIMP" is ok for image editing (despite having a stupid name) and available in the repos...

---

### Post by Ewan Cameron on 2009-09-30
Thanks tom. i ended up finding an old thread on the question which solved the problem - there is a launcher file in there, I just hadn't picked it.

---

