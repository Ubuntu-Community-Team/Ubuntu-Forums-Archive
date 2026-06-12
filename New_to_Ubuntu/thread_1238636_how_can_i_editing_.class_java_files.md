---
title: "how can i editing .class java files ??"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by MBG1987 on 2009-08-12
[SIZE=3]I already have java program for mobile phones ,and i extracted it to .class files ,and i want to edit that files to get what i want ,how can i do that ??! 
[/SIZE]

---

### Post by vegesm on 2009-08-12
The class files are compiled java binaries. You can't edit them easily. If you want to edit the Java source code then you have to download the .java files.

---

### Post by slakkie on 2009-08-12
Get a java decompiler like jad: [http://en.wikipedia.org/wiki/JAD_%28JAva_Decompiler%29](http://en.wikipedia.org/wiki/JAD_%28JAva_Decompiler%29)

Works really well, I've used it in the past. Only problem is that comments are lost and you get syntax like public function get_string(String a), instead of the usual logic var names. But it works. 

Had to decompile my own project once after I deleted my own java files. Took me hours to get the comments back and usefull names, but at least my pc didn't eat my homework!

---

### Post by MBG1987 on 2009-08-12
> **vegesm said:**
> If you want to edit the Java source code then you have to download the .java files.

tnx ,but what program do so ?

---

### Post by Skrynesaver on 2009-08-12
If they are supplied as class files, you don't have the source, as a result you'll either have to run a [java decompiler]("http://www.faqs.org/docs/Linux-HOWTO/Java-Decompiler-HOWTO.htm") on the class file.  As Slakkie said above, it's not perfect, but it will give you the logic back in java, after that you have to try and work out what it's at.

---

### Post by credobyte on 2009-08-12
If you don't have it's source code ( .java ), decompiling and editing class files might be illegal ( not always ). As said above, *reverse engineering* is all you can do in this case ..

---

### Post by Defyinggravitygaming on 2012-07-05
> **MBG1987 said:**
> [SIZE=3]I already have java program for mobile phones ,and i extracted it to .class files ,and i want to edit that files to get what i want ,how can i do that ??! 
[/SIZE]

U can install eclipse from the Ubuntu software center :D

---

### Post by lisati on 2012-07-05
With that, this old thread can go back to sleep. A lot can change in three years!

---

