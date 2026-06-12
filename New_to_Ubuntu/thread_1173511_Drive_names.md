---
title: "Drive names"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by ThewhiteLynx on 2009-05-29
I am use to Windows, and in windows when you open My Computer it displays the different drive names, however ubuntu when I open Computer shows the types of drives, eg 21.0 GB Media, but it doesn't give its name for use in say the terminal window.  How would I find out the different partitions and their names for use in the terminal window?

Thanks,

Lynx

---

### Post by halitech on 2009-05-29
you could try```
 sudo fdisk -l
``` as it will list the partitions

---

### Post by arsenic23 on 2009-05-29
**df** will give you a cli output of what's what with your partitions.
**gnome-system-monitor** will give you a filesystems tab if you want a gui interface.

---

### Post by halitech on 2009-05-29
never thought of df but thats a better option as it lists the partitions and the mount points for them

---

### Post by ThewhiteLynx on 2009-05-29
Thanks that does help, I also found that I can get the directories in the properties of the folder.

The new question is (and probably won't be easy to answer unless you play around with Java at all) how do I install thisText editor BlueJ, I have tried the install instructions on their website, however I found that there are better instructions on another rather out of date ubuntu thread [http://ubuntuforums.org/showthread.php?t=148758](http://ubuntuforums.org/showthread.php?t=148758)
however once I get to the point where I should enter 
sudo java -jar bluej-251.jar
it says, "sudo: java: command not found."
I looked in the directory and there is "java.exe" in the folder, so why is it giving the error?

---

### Post by arsenic23 on 2009-05-29
> **ThewhiteLynx said:**
> Thanks that does help, I also found that I can get the directories in the properties of the folder.

The new question is (and probably won't be easy to answer unless you play around with Java at all) how do I install thisText editor BlueJ, I have tried the install instructions on their website, however I found that there are better instructions on another rather out of date ubuntu thread [http://ubuntuforums.org/showthread.php?t=148758](http://ubuntuforums.org/showthread.php?t=148758)
however once I get to the point where I should enter 
sudo java -jar bluej-251.jar
it says, "sudo: java: command not found."
I looked in the directory and there is "java.exe" in the folder, so why is it giving the error?

You might want to start a new thread with a title that would atract people who are familiar with this problem.

---

