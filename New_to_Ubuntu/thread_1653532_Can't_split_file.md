---
title: "Can't split file?"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by rom3lol on 2010-12-27
I have a .rar file that is 4.5 gigs and the actual size is 13gigs. I would like to extract it to my desktop.
I believe the file size is too big too extract?
This is what I've tried 

>  rar x filename.rar

and I get this error
bash: syntax error near unexpected token `('

---

### Post by karthick87 on 2010-12-27
Welcome to ubuntuforums :)
[B]
Install unrar[/B]
```
sudo apt-get install unrar
```[B]

To extract:[/B]
```
unrar e filename
```
 or 
```
unrar x filename
```

---

### Post by rom3lol on 2010-12-27
Thank  you and Thank you for the quick reply

I install the program and did

 " unrar e filename.rar "

But I still get the[I][U] error
bash: syntax error near unexpected token `('[/U][/I]

---

### Post by karthick87 on 2010-12-27
May be your rar file is damaged i guess..

---

### Post by rom3lol on 2010-12-27
I hope not. I copied it from my external hdd.
Im going to re-copy it and ill try again. 
Ill post back with more info Thank You

---

### Post by mcduck on 2010-12-27
> **rom3lol said:**
> I have a .rar file that is 4.5 gigs and the actual size is 13gigs. I would like to extract it to my desktop.
I believe the file size is too big too extract?
This is what I've tried 


and I get this error
bash: syntax error near unexpected token `('

Like already said, "unrar" is the tool used to extract rar archives.

But you really don't need to do this from command-line, just right-click one of the files that belongs to the archive and select "Extract Here"... ;)

---

### Post by karthick87 on 2010-12-27
+1 on post #6

---

### Post by rom3lol on 2010-12-27
I extracted the file lol
I left if overnight and all is well. I was just being to inpatient.
Thanks you guys.
By the way would you know why I was getting  the error and what it means?

***bash: syntax error near unexpected token `('***

---

