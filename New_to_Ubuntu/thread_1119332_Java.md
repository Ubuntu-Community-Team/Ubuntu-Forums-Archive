---
title: "Java"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by lil_kid1333 on 2009-04-07
I was wondering how do I install the JDK on ubuntu? 

Also, I was wondering if it was the same as Windows where I got to compile via CMD and run off CMD or whatever else you use...

It would be great if I can compile through Terminal :)

It's for school and uugh I don't want to use Windows >_>

---

### Post by RedSingularity on 2009-04-07
Follow [THIS](http://ubuntuforums.org/showthread.php?t=1102050)

---

### Post by TheNosh on 2009-04-07
it's in the repositories

(aplications --> add/remove)

---

### Post by RedSingularity on 2009-04-07
Oh yeah, use the Repos if ur using 32 bit ubuntu.

---

### Post by lil_kid1333 on 2009-04-07
yeah im using 32 bit and I can't find it I typed in JDK and nothing :S

Wait nvm I found it!

So how do I use the Terminal to compile and all that stuff?

---

### Post by RedSingularity on 2009-04-07
Compile?  What are you compiling?

---

### Post by lil_kid1333 on 2009-04-08
> **Shadow121 said:**
> Compile?  What are you compiling?

just simple java programs

for example

```
public class HelloUbuntuForums {

   public static void main(String args[]) {

     System.out.println("Hello Ubuntu Forums!")

  }
}
```

hehe my ubuntu forums java program :P

Ok well let's say I got that on Text Editor and I save it as HelloUbuntuForums.java how would I compile it so it can turn into a .class file and so I can run it?

---

### Post by RedSingularity on 2009-04-08
Oh you want a program then to compile java programs.  Well i never used one so i cant give any recommendations but type "Ubuntu Java Compiler" in google and you will find lots of choices.  Chose whichever one looks good to you.

---

### Post by lil_kid1333 on 2009-04-08
thank you very much so then what's the use of the JDK here for? :S

---

### Post by Nepherte on 2009-04-08
To compile a java file you do need the jdk. You have to install sun-java6-jdk if you have a 32bit system or openjdk6 if you're on 64bit and also want the java browser plugin. Then you can compile a java file with the javac command.

---

### Post by starcannon on 2009-04-08
+1 Nepherte's answer.
Just to add to what Nepherte said, open the package manager:
System>Administration>Synaptic Package Manager
Then search for sun-java and you will see all the "official" java stuff.

GL and have fun.

---

### Post by stchman on 2009-04-08
> **lil_kid1333 said:**
> I was wondering how do I install the JDK on ubuntu? 

Also, I was wondering if it was the same as Windows where I got to compile via CMD and run off CMD or whatever else you use...

It would be great if I can compile through Terminal :)

It's for school and uugh I don't want to use Windows >_>

Use my page on essential packages.

[http://www.stchman.com/essen_pack.html](http://www.stchman.com/essen_pack.html)

---

### Post by lil_kid1333 on 2009-04-08
> **Nepherte said:**
> To compile a java file you do need the jdk. You have to install sun-java6-jdk if you have a 32bit system or openjdk6 if you're on 64bit and also want the java browser plugin. Then you can compile a java file with the javac command.

I got 32 bit ubuntu!

I was wondering what's the IcedTea java plugin for? I don't have it install do I need it?

thanks :)

---

### Post by Nepherte on 2009-04-09
The sun-java6 packages are the official packages from sun. Openjdk6 (and the icedteawebplugin) are the packages from the open source open source java. The reason why 64bit users *should* install the open source packages is because they allow you to have the java web plugin on 64bit. Older versions of the official sun packages ( < 6u12) didn't have the java web plugin. I hope that clarifies some things for you.

---

### Post by billgoldberg on 2009-04-09
> **lil_kid1333 said:**
> I got 32 bit ubuntu!

I was wondering what's the IcedTea java plugin for? I don't have it install do I need it?

thanks :)

No.

IcedTea is an open source alternative.

---

