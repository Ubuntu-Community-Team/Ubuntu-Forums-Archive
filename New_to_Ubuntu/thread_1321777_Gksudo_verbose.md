---
title: "Gksudo verbose?"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by coldReactive on 2009-11-10
Is it possible to show an exact path of where the application that is calling gksudo is?

Can it be applied so that gksudo always shows this information by default?

---

### Post by Little Girl on 2009-11-10
> **coldReactive said:**
> Is it possible to show an exact path of where the application that is calling gksudo is?


I'm not sure exactly what you're looking for. You use gksudo to call other applications. If it's the path to the gksudo command you're looking for, that's in the /usr/bin directory. If you're wanting to know the path to applications that get launched by gksudo, open a terminal window and use one of the methods below, replacing COMMANDNAME with the command for your application.

Type this to display the path to the application's executable file:
```

which COMMANDNAME

```
Type this to display the path to the application and also launch it using gksudo.
```

which COMMANDNAME && gksudo COMMANDNAME

```

> **coldReactive said:**
> Can it be applied so that gksudo always shows this information by default?

You can use a [BASH alias]("http://ubuntuforums.org/showthread.php?t=89732") to automate or customize commands, but COMMANDNAME is a variable that will change. I'm sure it can be done, but I'm not knowledgeable enough to come up with the alias you'd need to use. Maybe someone else who reads this will know it. :p

---

### Post by coldReactive on 2009-11-10
No, it's not really want I want, I want the gksudo dialog, right below the password box, to show a "Details" hide/show line that when shown will show the location and the command that is going to be executed and where it will execute, who called the application (username/alias), and what called the program (IE: GNOME Menu.)

I'll draw up a nice little mockup shortly.

---

### Post by coldReactive on 2009-11-10
Here you go: [Click Here](http://coldreactive.deviantart.com/art/GKSUDO-Details-Concept-143199805)

Brainstorm:

[[IMG]http://brainstorm.ubuntu.com/idea/4986/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/4986/)

---

### Post by Little Girl on 2009-11-11
Ah, I see! [This]("http://brainstorm.ubuntu.com/") seems like it would be a great place to present such an idea. :p

---

### Post by coldReactive on 2009-11-11
> **Little Girl said:**
> Ah, I see! [This]("http://brainstorm.ubuntu.com/") seems like it would be a great place to present such an idea. :p

I think you missed where I posted the brainstorm link. :|

---

### Post by Little Girl on 2009-11-11
LOL - I did! It just goes to show how well conditioned we can get when we purposely ignore all advertising. \\:D/

---

