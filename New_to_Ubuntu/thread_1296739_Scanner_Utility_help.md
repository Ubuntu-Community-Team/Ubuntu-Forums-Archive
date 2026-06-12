---
title: "Scanner Utility help"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by 289531.EXE on 2009-10-21
I keep getting an error message:

AN ERROR OCCURRED WHILE ACCESSING DEVICE!
The scan backened returned the following error: Invalid Argument

Then it goes on  to tell me no  device is found even though I have the printer working.

Does anyone know what this means? and  can anyone help me out? I need the scanner utility for a job.

---

### Post by mapes12 on 2009-10-21
What make and model scanner do you have?

---

### Post by 289531.EXE on 2009-10-21
It's one of those 80 dollar scanner/printers. its an  "HP Deskjet F380 All-In-One".

It worked  fine  but  last night all of a sudden it just pops up with that message.

---

### Post by mapes12 on 2009-10-22
This may help: [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

You can install the application through Terminal ```
sudo apt-get install hplip
```

---

### Post by The Cog on 2009-10-22
Do you have a webcam? It sounds like the old webcam v4l problem to me. If so, you have to disable the v4l webcam driver in sane. I think you do it by editing /etc/sane.d/v4l.conf and commenting out all the entries in there - can't remember for certain though.

---

### Post by 289531.EXE on 2009-10-22
> **mapes12 said:**
> This may help: [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

You can install the application through Terminal ```
sudo apt-get install hplip
```


Thanks  man, that worked like a charm

---

### Post by 289531.EXE on 2009-10-22
ok, tha hp  thing is installed, worked up to a few minutes ago when it just popped up with that error message again

---

