---
title: "What is futex_wait?"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by kreauchee on 2009-05-08
So I am relatively new to Ubuntu and haven't even been on anything Unix-like since I left college many years ago. Up until now I've been using Quanta for all my web development needs and just switched to Eclipse when 9.04 broke my ability to use CVS in Quanta.

Now, whenever I run Eclipse, there is a process 'java' that is sleeping at 400+M RAM on a waiting channel "futex_wait". I've seen this waiting channel state before on my system monitor but never thought much of it until a program that is essentially a fancy text editor was taking up a quarter of my machine's RAM.

1. What does futex_wait mean?

2. I have friends who have had nothing but good things to say about Eclipse. I can only assume this is my problem and not theirs or they would have not recommended this program. Any ideas on how I could fix this?

Thanks for any and all help.

-kreauchee

---

### Post by Cypher on 2009-05-08
futex is a fast mutex. Mutexes are a programming construct that allow multiple threads/processes to control access to shared resource.

Think of it as a stop light that only lets a single person through and until the person exits, a second person can't enter. Anyone else wishing to enter will essentially have to wait for the person inside to exit.

Eclipse is a Java based IDE and it can be quite memory intensive for that reason alone.

Just for web development (HTML, PHP) you might find numerous other native Linux apps to be better suited and significantly faster.

---

### Post by edwardtilbury on 2009-09-17
Same here, seems to happen when I run net beans and virtual box..

I'm on ubuntu 9.04 x64bit

It sucks! Java is using 440megs or so , for nothing

---

