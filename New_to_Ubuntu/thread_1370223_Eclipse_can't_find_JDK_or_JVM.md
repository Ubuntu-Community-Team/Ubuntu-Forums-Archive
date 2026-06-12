---
title: "Eclipse can't find JDK or JVM"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by esedizzle on 2010-01-02
Hello,
I run eclipse for all my java development and am having trouble as of recently after uninstalling it and reinstalling it.  Now it would appear it cannot locate the the JVM.  Eclipse will list all previous projects however all files appear as only filename.java or filename.class and when double clicked on will open a text editor holding the code.  I cannot create new packages, java projects, classes, etc.  Please tell me if this is consistent with eclipse not locating the jvm or if it is something else.  Also, please tell me how to locate my jvm and how to make eclipse recognize it.  Attached is a screenshot of the program as it is.

---

### Post by paultag on 2010-01-02
Change window view to Java :)

---

### Post by paultag on 2010-01-02
Sorry, forgot to follow up

Window --> Open Perspective --> Java

---

### Post by esedizzle on 2010-01-02
The only options under open perspective is debug and other.  Java is not an option.  Also, extra note the following code in the terminal:
sudo update-java-alternatives --list
returns
java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk

---

### Post by esedizzle on 2010-01-02
How would I go about manually adding a Java IDE to eclipse?  is this what i'm missing?

---

