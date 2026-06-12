---
title: "Java in ubuntu"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by dmakshay2002 on 2009-11-28
Hello,
 Im very new to ubuntu and learning now. So im trying to execute java using terminal window. So i installed the jdk package and then i did few programs and executed it and it worked perfectly. I always used to do this in the same folder. So now i've created a folder named classes and another source so that all my source files will be saved in source directory and classes in classes directory. In windows i simply used to use command as javac -d c:\java\classes <programname>.java to compile in classes folder. In ubuntu i tried using -d to change the directory and it didn work. Pls guys help me out here.
Thanks in advance..

---

### Post by jbrown96 on 2009-11-28
check out the man page ```
man javac
``` This looks relevant >        -d directory
                Set the destination directory for class files. The directory must already exist; javac will not create it. If a
                class is part of a package, javac puts the class file in a subdirectory reflecting the package name, creating
                directories as needed. For example, if you specify -d /home/myclasses and the class is called com.mypack&#8208;
                age.MyClass, then the class file is called /home/myclasses/com/mypackage/MyClass.class.

             If -d is not specified, javac puts each class files in the same directory as the source file from which it was gener&#8208;
             ated.

             Note:   The directory specified by -d is not automatically added to your user class path.


---

### Post by dmakshay2002 on 2009-11-28
Hey jbrown i got it man. Thanks a lot..:)

---

