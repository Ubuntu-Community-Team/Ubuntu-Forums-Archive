---
title: "command to run .jar in java from terminal?"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by liquid150 on 2011-07-31
It's a little bit more complicated than that, but if I can get this info I ought to be able to figure out the rest.

I want to use terminal to run a .jar file in Sun Java. Then, after I can do this from the terminal, I plan to create a launcher icon on the desktop for easy access by my non-user friends when they need to use my computer.

If I try running it normally, it just opens up the jar but doesn't execute.

Any help would be greatly appreciated.

---

### Post by Wim Sturkenboom on 2011-07-31
Is the run time environment installed?

---

### Post by liquid150 on 2011-07-31
> **Wim Sturkenboom said:**
> Is the run time environment installed?

Absolutely, one of the first things I did after putting Ubuntu on my laptop.

The program works fine if I navigate to it and right click on it and hit "Open With Sun Java 6 Runtime."

I just want to be able to replicate that process through a clickable desktop shortcut. I already know how to create a .sh in gedit and create a launcher icon that points to the .sh file, thereby launching the script it contains. I just need to find out what the script is that replicates the above process so I can stick it in the file.

If there's something more elegant, I'm open to suggestions.

---

### Post by Wim Sturkenboom on 2011-07-31
OK
```

java -jar filename.jar

```

---

### Post by liquid150 on 2011-07-31
> **Wim Sturkenboom said:**
> OK
```

java -jar filename.jar

```

Excellent! Thank you!

---

