---
title: "How to make a link in the menu"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by t4ggs on 2008-12-16
I have JDownloader installed, the file is jdownloader.jar and I want to made a link to it in the Applications menu, what should I write as a command?

---

### Post by Locke_99GS on 2008-12-16
Open the menu editor (*alacarte* from shell) and add from there.

---

### Post by t4ggs on 2008-12-16
yeah but what should i wrote? /home/user/JDownloader/jdownloader/jar??? it didn't work.

---

### Post by kyphi on 2008-12-16
If you have a file in your Home directory called JDownloader and the jdownloader.jar is in that, the path should be

/home/username/JDownloader/jdownloader.jar

---

### Post by t4ggs on 2008-12-16
I did it but i get this message: 

Could not launch menu item

Failed to execute child process "/home/ytagger/.jdownloader/JDownloader.jar" (Permission denied)


When i create a link to the desktop it works but in the menu it doesn't and i get that message, how do i solve it?

---

### Post by kyphi on 2008-12-16
What is that hidden file doing in your path statement?

Where have you put the .jar file?

---

### Post by donkyhotay on 2008-12-16
Also make certain that you have run permissions on that file. Are you capable of running the .jar file from the CLI directly (without the menus)?

---

### Post by darthmob on 2008-12-16
did you try *java -jar /home/ytagger/.jdownloader/JDownloader.jar* ?
personally I created a executable jdownloader.sh which uses this command and linked to the sh file in my top bar.

---

### Post by t4ggs on 2008-12-16
well it is in a hidden folder because i like my home folder to be organized and when i double click the file, it runs... so i suppouse that i do have the permissions...btw the file is a java archive...I tink i need to write something in the command to make it run with java

---

### Post by kyphi on 2008-12-16
I need to know exactly what the .jar file is called and where it is so that I can tell you what the path should be.

---

### Post by donkyhotay on 2008-12-16
as darthmob mentioned try using
```
java -jar /home/ytagger/.jdownloader/JDownloader.jar
```
if you can run it from the GUI but not the command line then most likely it's a file association issue. Specifying your running java and having java open the file with the command above should resolve it.

---

### Post by t4ggs on 2008-12-16
> **kyphi said:**
> I need to know exactly what the .jar file is called and where it is so that I can tell you what the path should be.

/home/ytagger/.jdownloader/JDownloader.jar


and i tried -jar /home/ytagger/.jdownloader/JDownloader.jar but it didnt worked...yeah i i know a can make a link to a link, but there must be a solution...

---

### Post by t4ggs on 2008-12-16
I am so stupid, the problem is that when editing the menu i didnt close the window where u edit the menu so it didnt apply the new setting.. now it works

---

### Post by kyphi on 2008-12-16
I have just downloaded JDownloader and put it in my home directory.  It came as a zip file.  The path is:

/home/username/jDownloader/jDownloader_v0.2.888_multios/jDownloader/JDownloader.jar

Watch out for capital letters (see jDownloader and JDownloader).

---

### Post by nazrysamaratin on 2009-02-11
anyone here can tranlate to english please [http://ubuntu-ar.org/node/210](http://ubuntu-ar.org/node/210)

---

### Post by t4ggs on 2009-02-11
> **nazrysamaratin said:**
> anyone here can tranlate to english please [http://ubuntu-ar.org/node/210](http://ubuntu-ar.org/node/210)

Introduction:

JDownloader has a writing recognize system that will override the rapidshare and megaupload protection system and it also works as a downloads manager that let us introduce many downloadable links that will start to download according to each site policy.

Process:
First download the program from [http://jdownloader.org/download](http://jdownloader.org/download), in this tutorial its assumed that the program was downloaded to "/tmp"

In order to execute this application you have to install JRE (Java Runtime Environment).  For install JRE do the following:

< sudo apt-get update
< sudo apt-get -udV sun-java6-jre
< sudo apt-get install sun-java6-jre

Then in your home folder, create a folder to house the program:

< cd 
< mkdir JDownloader

Then enter that directory and unzip the downloaded file:

< cd JDownloader/
< unzip /tmp/jdownloader_v0.3668.zip

To use the program, run this command.

< java -jar ~/JDownloader/JDownloader.jar

In order to create a link in your meno, do the following:go to the menu System -> preferences -> menu
Then you will see this window.  Select the menu Applications and inside, the menu Internetand click on the icon for a new element.

FIRST PICTURE
Fill the name and the command used before (java -jar ~/JDownloader/JDownloader.jar)

SECOND PICTURE

Click on close

THIRD IMAGE

JDownlader by default will download the files to a folder called "downloads" inside the folder where the program is ("~/JDownloader/downloads").

---

