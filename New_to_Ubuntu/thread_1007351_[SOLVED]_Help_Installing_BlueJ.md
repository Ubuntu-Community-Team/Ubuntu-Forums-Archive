---
title: "[SOLVED] Help Installing BlueJ"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by lewbram on 2008-12-10
Hey Guy's 

I am brand new to Linux I have installed ubuntu with view to my studies next semester. 

i am trying to install BlueJ as I need to finish this semesters coursework but i am having major difficulties if anybody could help I would be most grateful.

so far i have downloaded BlueJ and it is on my desktop but i have no idea have to get it working.

Please can anybody help me?

---

### Post by Titan8990 on 2008-12-10
Go to Applications -> Accessories -> Terminal

Navigate the the directory that the java installer is in. If it is on your desktop it will be:

cd ~/Desktop

If it is in its own folder on your desktop you will need to cd into that directory.


To run the installer:


java -jar NAMEOFINSTALLER.jar

---

### Post by lewbram on 2008-12-10
Thanks for replying 

completed cd to desktop 

How do I know what the directory is?

It appears on the desktop with a 'box' icon and reads bluej-250.jar

---

### Post by Titan8990 on 2008-12-10
That means it is in your Desktop directory in your home folder.

In Linux ~ = your home folder. These two commands just launch the installer:


cd ~/Desktop

sudo java -jar bluej-250.jar

---

### Post by lewbram on 2008-12-10
Excellent Thankyou very much

---

### Post by Titan8990 on 2008-12-10
No problem. I am assuming it worked and that is excellent.


Don't forget to mark your thread as "solved" under thread tools at the top.

---

### Post by lewbram on 2008-12-10
Sorry if you have time I don't suppose you could help me some more?

I need to download the JDK which is also sitting on my desktop but i am unable to access it. I have tried doing the same thing but it wont work.

---

### Post by Titan8990 on 2008-12-10
Just copy and paste the following in to the terminal:


sudo apt-get install sun-java6-jdk

---

### Post by lewbram on 2008-12-10
Thanks, i have done that and when I try to install Blue J it is asking for the JDK directory, Do you know where I could find this?

---

### Post by Titan8990 on 2008-12-10
Post the output of the following:


which sun-java6-jdk

---

### Post by lewbram on 2008-12-10
lewbram@lewbram-desktop:/$ which sun-java6-jdk
lewbram@lewbram-desktop:/$ 

nothing happened

---

### Post by lewbram on 2008-12-10
nothing happens

lewbram@lewbram-desktop:/$ which sun-java6-jdk
lewbram@lewbram-desktop:/$

---

### Post by Titan8990 on 2008-12-10
Try telling the installer is here:


/usr/share/java

---

### Post by lewbram on 2008-12-10
It says the java directory is not a valid JDK directory it must have subdirectory "lib" and file name tools.jar in it.

does this help?

---

### Post by Titan8990 on 2008-12-10
Check this directory:

/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/


Your version number WILL be different. Navigate to /usr/lib/jvm and see if there is a folder similar to the one above.


Edit: If you still are having issues finding it, try looking for that file:


sudo find / -name '*tools.jar*'

---

### Post by lewbram on 2008-12-10
that has worked it has installed now but I can't open it there is no icon anywhere and its not in applications

---

### Post by lewbram on 2008-12-10
my mistake found it, got it working! thank you so much for your help. I have to go work now but hopefully we will speak again soon!

---

### Post by Titan8990 on 2008-12-10
Good to hear.

Welcome to Linux :).

---

