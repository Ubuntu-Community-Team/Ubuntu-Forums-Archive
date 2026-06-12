---
title: "No such file or directory ,, please help me !"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by BoyoungAhn on 2008-12-03
i cannot install java (which is --.bin file)

please help me..

-----this is what i have to do----------

  1. At the terminal: Type:
      su
   2. Enter the root password.
   3. Change to the directory in which you want to install. Type:
      cd <directory path name>
      For example, to install the software in the /usr/java/ directory, Type:
      cd /usr/java/

   4. Change the permission of the file you downloaded to be executable. Type:
      chmod a+x jre-6ull-linux-i586.bin
   5. Verify that you have permission to execute the file. Type:
      ls -l

-------------------------


----this is my problem-----------
root@ahnboyoung-laptop:/home/ahnboyoung# /home/ahnboyoung/Documents/java
bash: /home/ahnboyoung/Documents/java: is a directory
root@ahnboyoung-laptop:/home/ahnboyoung# chmod a+x jre-6ull-linux-i586.binchmod: cannot access `jre-6ull-linux-i586.bin': No such file or directory
------------------------


please help me !

---

### Post by Mazza558 on 2008-12-03
The terminal is always finnicky with this kind of thing. Try right-clicking on the actual java file, wherever it is, and going to properties, and then "permissions" - check the checkbox which allows it to be executable and then double-click and click "open in terminal"

---

### Post by binbash on 2008-12-03
dude 

you will navigate to the directory where you downloaded .bin file with cd command

example : 

cd /home/bblabla/binfileishere/
sudo ./binfile.bin

---

### Post by LowSky on 2008-12-03
intall java from synaptic or add remove
r use this command in terminal

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

---

### Post by Michael.Godawski on 2008-12-03
LosSky is so right.
Before fumbling around with the terminal always check the Synaptics. Only if you want to have the latest version consider a manual way of installation.

---

