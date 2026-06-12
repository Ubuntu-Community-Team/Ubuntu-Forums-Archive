---
title: "Installing minecraft"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by DarrenMR415 on 2010-09-22
Im sorry Im sure this is a stupid question.  I have the jar folder on my desktop, but I have no idea what to do next.

---

### Post by ronnielsen1 on 2010-09-22
Assuming you have java installed

From terminal cd to where your minefield is

chmod +x Minecraft.jar (To mark as executable)
./Minecraft.jar

Or from GUI

Right click on the folder, choose permissions tab and mark as executable
Right click on the folder, choose open with Sun Java 6 Runtime

---

### Post by DarrenMR415 on 2010-09-22
Stupider question, I just installed java, how do I accept the terms and conditions?

---

### Post by mcduck on 2010-09-22
> **DarrenMR415 said:**
> Stupider question, I just installed java, how do I accept the terms and conditions?

just press the Tab key to highlight the "accept"-button (or whatever it's named, I can't remember) and hit enter.

---

### Post by DarrenMR415 on 2010-09-22
> **mcduck said:**
> just press the Tab key to highlight the "accept"-button (or whatever it's named, I can't remember) and hit enter.

Youre amazing.  Thank you.

---

### Post by wolfen10 on 2011-07-05
hello, i havent had so much luck with this
i followed your instructions and i have sun java 6 runtime but when i login to minecraft it just crashes...
any ideas?:confused:

please just answer me!!!!

---

### Post by Perkins on 2011-07-06
Post the console output and maybe somebody can pick out what's going wrong.

---

### Post by linuxman94 on 2011-07-06
Please post the crash file that minecraft generated.  It should be in your home folder.

---

### Post by Purplerob on 2011-07-06
Found this on the download page try launching it with the command 
```
java -Xmx1024M -Xms512M -cp Minecraft.jar net.minecraft.LauncherFrame
```

---

### Post by Paqman on 2011-07-06
If you've got Java installed, all you need to do is click on the minecraft.jar and it'll do its thing. Officially Notch says to use the Sun Java, but I've never had any problems running Minecraft with OpenJDK.

---

