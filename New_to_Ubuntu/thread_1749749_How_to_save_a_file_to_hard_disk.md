---
title: "How to save a file to hard disk?"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by justjeff on 2011-05-04
Can someone tell me how to do this, what hard disk, and how I copy it to the xxxxx/xxx.list

"You've got references to both Lucid and Maverick that shouldn't be there, I've fixed the errors below. Save this file to your hard disk and copy it to /etc/apt/sources.list"

"After you've copied the file, run"

and where exactly do I run this?  off the terminal?  I am not being lazy I have been searching google for a couple of hours now for the  answers and if your not aware of it there are about a zillion ubuntu linux how to pages and tips...

---

### Post by wojox on 2011-05-04
Do this, open a terminal and 

```
gksudo gedit /etc/apt/sources.lst
```

Then copy and paste the new list you have had fixed and save.

Then run:

```
sudo apt-get update; sudo apt-get upgrade
```

---

### Post by dFlyer on 2011-05-04
> **justjeff said:**
> Can someone tell me how to do this, what hard disk, and how I copy it to the xxxxx/xxx.list

"You've got references to both Lucid and Maverick that shouldn't be there, I've fixed the errors below. Save this file to your hard disk and copy it to /etc/apt/sources.list"

"After you've copied the file, run"

and where exactly do I run this?  off the terminal?  I am not being lazy I have been searching google for a couple of hours now for the  answers and if your not aware of it there are about a zillion ubuntu linux how to pages and tips...

I don't understand your question. Copy what, run what. cp is the copy command, from the command line. Drag and drop is another way to copy a program. Right click copy and paste is another way.

Clicking on a program will start it. On the command line ./file will start it. sh file will start some programs. cat >dog.txt will create a file called dog.txt. gedit dog.txt will allow you to edit the file and then save it with the same name or a new name.

---

### Post by justjeff on 2011-05-04
I'm sorry forget that not everyone has read all the post, should of linked it, but don't know how, to my post earlier which is [ubuntu] jre problems   - tried or am trying to do what the other guy was saying to do not sure if it is working but dont think it is.  think that may be half my problem, things are getting input and ran somewhere...

---

### Post by justjeff on 2011-05-04
This is for Gary "dFlyer" who has been doing this for 5 or 6 years at least while I have got about 48 hours under my belt.
 I had to go back and check and make sure I was is the right forum which is  Absolute Beginner Talk, what you said made even least amount of sence to me from all I have heard today,
  What I need and others like me is step by step, click on places, select from the drop down desktop....right click, paste this...

---

