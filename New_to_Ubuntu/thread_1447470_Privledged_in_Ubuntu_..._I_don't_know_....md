---
title: "Privledged in Ubuntu ... I don't know ..."
date: 2010-04-05
forum: New to Ubuntu
---

### Post by carrarin on 2010-04-05
Hey everyone,

I'm using Cincoms Smalltalk IDE VisualWorks in linux. I have it installed at /opt/CincomSmalltalk/.

I have found that when I try to save my work I either get an error, or the data does not get written correctly to the file.(When not root.)


When I run the VisualWorks under sudo, these problems disappear.

But, I don't like having to open a terminal and navigating to the folder and then sudoing. I'd much rather go to my applications menu  and just run VisualWorks like a normal application. 

How do I do this?

Thanks,
you guys are awesome :)

---

### Post by s_ø on 2010-04-05
Are you saving to a directory you have write permissions to?

---

### Post by carrarin on 2010-04-05
Well, yes. I save it to my ~/Desktop/cs476 folder.

---

### Post by da burger on 2010-04-05
Please run ```
ls ~/Desktop -l
``` and post the output.

---

### Post by carrarin on 2010-04-05
ls -l Test.st 
-rw-r--r-- 1 carrarin carrarin 947 2010-04-05 12:18 Test.st

---

### Post by s_ø on 2010-04-05
Test.st is not the directory you are saving to.
What are the permissions on the  ~/Desktop/cs476 directory?
```
ls -ld   ~/Desktop/cs476
```

Try and start the program from terminal without using sudo. When you get the error are anything displayed in the terminal window?

---

### Post by carrarin on 2010-04-05
drwxr-xr-x  6 carrarin carrarin 4096 2010-04-05 12:19 cs476

also, there is no error when saving the file.
When I open the file, I get a bland error that says 
error <- exception ... or something.

---

### Post by warfacegod on 2010-04-05
Try this. Right click your Apps./Places/System Menu and select Edit Menus. In the window that opens, navigate to the application and right click it to select Properties. In the Command section add gksudo to the beginning of the command.

Example:

gksudo nautilus (note the space)

or

gksudo jockey

---

### Post by carrarin on 2010-04-05
it works ... but I still have to use my passwd ... I will accept it though. 

Thanks dude, you truly are a god :> !!!

---

### Post by warfacegod on 2010-04-05
Gladly providing divine mana/code from heaven since the beginning of time.

If you are satisfied with your current universe, please mark as Solved under Thread Tools. No refunds.

This message has been brought to you by the creators of existence and *Blammo*!

---

### Post by sandyd on 2010-04-05
> **warfacegod said:**
> Gladly providing divine mana/code from heaven since the beginning of time.

If you are satisfied with your current universe, please mark as Solved under Thread Tools. No refunds.

This message has been brought to you by the creators of existence and *Blammo*!
:lolflag:

---

