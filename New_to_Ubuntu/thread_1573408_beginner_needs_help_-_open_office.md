---
title: "beginner needs help - open office"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by djkisa on 2010-09-12
hi :)

I just installed ubuntu 10.04.1 a week ago and have been having slight problems that I have been able to google my way out of but not this one. I can't save anything from open office draw, I keep getting the error message " Error saving the document [name] :/home/dorothea/Documents/[name].odg does not exist." I also got something like that using gedit but not now when I'm trying :þ 

If there is anything else I should know about please feel free to add those :D

---

### Post by sgosnell on 2010-09-12
Assuming your post is a formatting error, /home/dorothea/Documents/filename.odg should be a valid location, after Draw saves it.  You may have a permissions problem with that folder.  If there is indeed a colon before the / as in your post, that isn't a valid location.

---

### Post by djkisa on 2010-09-12
> **sgosnell said:**
> Assuming your post is a formatting error, /home/dorothea/Documents/filename.odg should be a valid location, after Draw saves it.  You may have a permissions problem with that folder.  If there is indeed a colon before the / as in your post, that isn't a valid location.

So how do I get the permission ? :/

---

### Post by Miljet on 2010-09-12
Open a terminal by seecting Applications -> Accessories -> Terminal. Type in the following  ```
ls -l 
```
 That is a dash small L, not a one.
Please copy and paste the output here.

---

### Post by djkisa on 2010-09-12
I was able to save my project after writing chmod 755 Documents  :) but more and more problems keep piling up...

---

### Post by wilee-nilee on 2010-09-12
> **djkisa said:**
> I was able to save my project after writing chmod 755 Documents  :) but more and more problems keep piling up...

Are you launching OO with the terminal in root?

---

### Post by djkisa on 2010-09-12
no from the applications (if I understood what you were even asking)

---

### Post by wilee-nilee on 2010-09-12
> **djkisa said:**
> no from the applications (if I understood what you were even asking)

Thats okay I hardly understand. A Ubuntu setup has root accessible basically via a password. In Windows root is basically the administrative account, at times we have people trying to run their computers in root all the time, I was just checking.

---

### Post by sgosnell on 2010-09-12
"More and more problems" isn't very specific.  What problems, exactly, "keep piling up"?

---

### Post by anewguy on 2010-09-13
> **wilee-nilee said:**
> Thats okay I hardly understand. A Ubuntu setup has root accessible basically via a password. In Windows root is basically the administrative account, at times we have people trying to run their computers in root all the time, I was just checking.

Off-topic, but wilee-nilee - I love your avatar - I think I've seen the little dude flying around in our backyard!

---

### Post by djkisa on 2010-09-13
one of which is:

Could not display "/home/dorothea/Downloads/postgresql-8.4.4-1-linux.bin".

The file is of an unknown type

and I don't know how I managed to lock my self out, I'm trying to set up a database management system for class... Thaaanks for all the help though :D

---

### Post by coutts99 on 2010-09-13
> **djkisa said:**
> one of which is:

Could not display "/home/dorothea/Downloads/postgresql-8.4.4-1-linux.bin".

The file is of an unknown type

and I don't know how I managed to lock my self out, I'm trying to set up a database management system for class... Thaaanks for all the help though :D

Are you trying to open that file in OO?

If you are, you shouldn't be.

---

### Post by sgosnell on 2010-09-13
You can't show much in a .bin file.  Those are the Linux equivalent of a .exe file, an executable program.  You don't want to display it, you want to run it, probably.  I don't recognize the app.  It certainly can't be opened in Open Office.

---

