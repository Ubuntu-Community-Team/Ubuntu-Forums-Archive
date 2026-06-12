---
title: "Memory Optimization"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by mwalimu54 on 2009-11-05
I found this website [http://it.toolbox.com/blogs/locutus/maximise-linux-memory-usage-23461]("http://it.toolbox.com/blogs/locutus/maximise-linux-memory-usage-23461") which suggests using the command 

echo -e "\0101\0160\0162\0151\0154\0040\0106\0157\0157\0154\0163\0041" 

to increase memory performance and I have several questions:

1. Is this a legitimate hack?
2. Does this apply or do any good in Karmic or is it already in place?
3. How could I reverse this if I break something?


I've been using Ubuntu for over a year but stick mostly with the gui having a limited understanding of the command line.  I'm running 9.10, ext4, 64-bit.  See the first part of my sig if you have any questions about my hardware.

---

### Post by qamelian on 2009-11-05
According to the writer's comments at the bottom of the article, the command is supposed to be a toggle switch, so executing it a second time reverts to the old behaviour.

---

### Post by Darce on 2009-11-05
This is cruel !    lol

---

### Post by buellman on 2009-11-05
Hmmm... anyone looked at the date of the comments? ***4/1/2008***.
Think about it. :D

Greets. Buellman

---

### Post by mwalimu54 on 2009-11-05
Can no one write anything legitimate on April Fool's?  And yes, I did notice the date (it's old and we are now in the age of Karmic).  Being a newb, I have not the faintest understanding of the bash line.  The reason I brought it to this forum was to get a more experienced perspective before I hose my system.

---

### Post by buellman on 2009-11-05
If you look at the manpage of echo (man echo) you will see the following:
"-e     enable interpretation of backslash escapes"
and
"\0NNN  the character whose ASCII code is NNN (octal)"

I can't translate ASCII but maybe you find the following table helpfull:
[http://www.asciitable.com/]("http://www.asciitable.com/")ASCII table

Greets. Buellman

---

### Post by Darce on 2009-11-05
Run the command. It won't hurt your system, and you'll also realise how childish we all are ;)

---

### Post by philinux on 2009-11-05
> **Darce said:**
> Run the command. It won't hurt your system, and you'll also realise how childish we all are ;)

Yes minus the space on the OP's string.

---

### Post by buellman on 2009-11-05
I didn't tried it but thought something like that. Would be a new way of fun for something like "sudo rm -rf" :-D

Greets. Buellman

---

### Post by kerry_s on 2009-11-05
:lolflag:
yes the command is safe.

---

### Post by mwalimu54 on 2009-11-05
oh whatefer!

---

