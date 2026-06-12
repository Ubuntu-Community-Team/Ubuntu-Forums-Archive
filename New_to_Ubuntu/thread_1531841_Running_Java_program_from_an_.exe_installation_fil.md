---
title: "Running Java program from an .exe installation file?"
date: 2010-07-15
forum: New to Ubuntu
---

### Post by Grone1985 on 2010-07-15
This program is written in java and used to have a version packed for linux but I can't find it.

[http://www.e-biometria.com/gstat2_0.zip]("http://www.e-biometria.com/gstat2_0.zip")

I tried to extract the files and run it but I don't really know how. Is it even possible to do it? Thanks!

---

### Post by jtarin on 2010-07-15
How many people are going to want to download your file? I suggest you list the contents or point to a page where the app can be reviewed. What happens when you click on the .exe?
You can try starting from a terminal.List the files found in the package then I might be able to help. Insure Java is installed on your machine before you even attempt this.

---

### Post by Grone1985 on 2010-07-15
Yeah, I thought about it too... But how can I list all the files in it? The zip file has many folders with many .jar .dll and all kinds of files.

The program is made by GlaxoSmithKline, a pharmaceutical company, it is a statistical analysis app. What I mean is it's not "my" file, that is their download page.

[http://www.e-biometria.com/](http://www.e-biometria.com/)

---

### Post by jtarin on 2010-07-15
Many times you can just unzip it to its own folder and run it from there. Try using the terminal and enter the directory of the app and issuing the command ```
ls
```this will list all files in that directory. Then highlight in your terminal, right-click, copy and paste to your posted response here. Many java applications can be run from the terminal if they have a script or sometimes they can just be run from a .jar file issuing ```
./nameoffile.jar
```or in the case of a script ```
./nameoffile.sh
```.

---

