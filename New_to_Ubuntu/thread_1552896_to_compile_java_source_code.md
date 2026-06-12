---
title: "to compile java source code"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by amityadav9314 on 2010-08-14
hi!
I have intalled JDK and JRE in wine(exe files).
I need to compile and run java source code using javac.exe and java.exe files like we do in windows.
so what are the commands to change the path and go to--->
wine-->c:-->program files-->j2sdk-->bin under terminal?
thanks!

---

### Post by McNils on 2010-08-14
why install windows version of java?

To install java just enable the partner repository and install sun-javaX.

---

### Post by amityadav9314 on 2010-08-14
no, i am just curious.
i want to know how to enter in wine through terminals.

---

### Post by Spice Weasel on 2010-08-14
Type "wine cmd" into a terminal

and then

"cd /path/to/file/" if you want to navigate in to your Linux files.
"cd ~/.wine/drive_c/path/to/file" for your wine files.

---

### Post by KdotJ on 2010-08-14
> **amityadav9314 said:**
> no, i am just curious.
i want to know how to enter in wine through terminals.

Just out of interest, is this purely because you want to do it via wine? You still have to use the "javac" and "java" commands under linux when compiling and running java programs.

---

### Post by amityadav9314 on 2010-08-14
yeah i have already installed java in my ubuntu.

---

### Post by amityadav9314 on 2010-08-14
thanks!
it worked.
it was so simple.

---

