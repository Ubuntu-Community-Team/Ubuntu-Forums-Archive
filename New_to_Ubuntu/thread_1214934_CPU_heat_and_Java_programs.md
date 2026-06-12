---
title: "CPU heat and Java programs"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by Koobelakahn on 2009-07-16
Hi, my name is Koobelakahn (Koob for short)
I have a question.
I have the Computer Temperature Monitor 0.9.6.1.
it says something about activating an alarm, so i wrote a program in Java that would display the lines that my CPU is getting too hot, and that i need to cool down.

How can i make that program run as the alarm?
I saw (under properties) command to execute.
so, i have the program written (its a simple repitition of System.out.println)

So.
How to i make the terminal pop up, with my program running when my CPU reaches a certain temprature?

---

### Post by Koobelakahn on 2009-07-16
i have one more question about the forum too.
Is there some sort of a thread bumping in place or no?

---

### Post by Koobelakahn on 2009-07-16
i have the JDK installed, im just curious about how to make the program that i wrote pop up when my CPU gets to hot.

help please.

---

### Post by Finalfantasykid on 2009-07-16
> I saw (under properties) command to execute.

For that command, you would use:

```
java myprogram
```

or if you are using a .jar

```
java -jar myprogram.jar
```

---

### Post by Koobelakahn on 2009-07-16
> **Finalfantasykid said:**
> For that command, you would use:

```
java myprogram
```or if you are using a .jar

```
java -jar myprogram.jar
```


See, i tried that, and it didnt do anything at all.
maybe i have to write the equivilant of a .bat file (for ubuntu) and have it open the terminal, which would run my program.

Do i have to tell that program where to look for my program?

---

