---
title: "Creating a simple exe/bat file."
date: 2010-11-29
forum: New to Ubuntu
---

### Post by tonypg on 2010-11-29
Hi i have downloaded SQLdeveloper and used the forum post below to run it. 

> Ah, crud. Managed to solve this problem with the help of another more-advanced-than-me linux user. Anyway, I'll write up how we got it sorted without needing to convert an rpm package to deb just so if anyone else has this same problem in the future and googles this or something...

First make sure you have Java JDK installed. I used openjdk (open-source alternative to the official Sun Java jdk thingie).
Download the "Oracle SQL Developer for other platforms" from the Oracle site ([http://www.oracle.com/technology/sof...index.html)and](http://www.oracle.com/technology/sof...index.html)and) then extract it into its own folder. Then in terminal, cd to the extracted directory and:
sudo sh sqldeveloper.sh
It'll ask you to type the pathname of your J2SE installation.
Mine turned out to be "/usr/lib/jvm/java-6-openjdk". Then press enter and you should be right and it will boot up and work the exact same as it does under Windows or OS X.

Hopefully this helps another linux newbie out one day down the track 

What i would like to do is to create a batch file that when i click on it to run from Terminal it will run this command lines above so that i don't have to go to Terminal every time i want to run this program. Any ideas?

---

### Post by Gone fishing on 2010-11-30
To make a file executable create a blank test file open it and add the command and save. The close the file and then make the file executable this can be done in the gui right click go to properties and in permission click the executable tick box.

---

### Post by tonypg on 2010-11-30
Thank you

---

