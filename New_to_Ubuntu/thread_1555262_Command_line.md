---
title: "Command line"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by DarrenMR415 on 2010-08-17
Can anyone explain this or point me in the direct of an explination?  I would like to add a program to my startup programs.  Its called Brightside.  What do I do?

---

### Post by ubudog on 2010-08-17
To add it to startup programs, you don't need the command line.  Use System>Preferences>Startup Applications. for that.  There are many ways to install things using the command line.  Using apt (the most common way):
```
sudo apt-get install packagename
```
(packagename being the name of the program)

---

### Post by DarrenMR415 on 2010-08-17
I already have it installed, I dont know what to put on the Startup applications where it says command.

---

### Post by scrooge_74 on 2010-08-17
Well i see it comes in tar format and is the source code.

1. You need to uncompress
2. you will need to compile it for it to run
a. need compiling tools
b. need to follow what ever instructions come inside it

how good are you at the command line and compiling stuff?

---

### Post by DarrenMR415 on 2010-08-17
I think it would be safe to assume my skills based on the fact that this thread is in the "Absolute Beginner" subforum.

---

### Post by wojox on 2010-08-17
> **DarrenMR415 said:**
> I already have it installed, I dont know what to put on the Startup applications where it says command.

Try

```
brightside
```

---

### Post by t0p on 2010-08-17
If wojox's suggestion doesn't work, open a terminal (**Applications > Accessories > Terminal**) and type in

```

which brightside
```

I don't have brightside installed on my computer; but I assume you'll get a response something like

```

/usr/bin/brightside
```

That reply is what you need to put in Startup Applications, eg in my example you would type in **/usr/bin/brightside**.

---

### Post by DarrenMR415 on 2010-08-17
Thats exactly what came up /usr/bin/brightside.  Is that how I find out what to do with everything else in that type of situation?

---

