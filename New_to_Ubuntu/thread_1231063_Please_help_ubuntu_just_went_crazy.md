---
title: "Please help ubuntu just went crazy"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by GonZo1323 on 2009-08-04
So i was trying to upload some photos to facebook and it ask me to install java so i click of whatever.
Now i lost all my shortcuts in the menu. Mozilla lost all my bookmarks and now flash won't work.
Pidgin won't start i have restarted and tried everything i know.
PLease someone help
Thanks in advance

---

### Post by Sef on 2009-08-04
What version of Ubuntu are you using?

---

### Post by superprash2003 on 2009-08-04
post output of **sudo apt-get update** ..it could be that some package didnt install completely

---

### Post by GonZo1323 on 2009-08-04
im using 9.04

---

### Post by credobyte on 2009-08-04
Post the output of:
```
java -version

```

---

### Post by GonZo1323 on 2009-08-04
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGBUS (0x7) at pc=0xb7f6a377, pid=21040, tid=3077135248
#
# Java VM: OpenJDK Client VM (14.0-b08 mixed mode, sharing linux-x86 )
# Distribution: Ubuntu 9.04, package 6b14-1.4.1-0ubuntu10
# Problematic frame:
# C  [libc.so.6+0x79377]  memset+0x37
#
# An error report file with more information is saved as:
# /home/gonzo/hs_err_pid21040.log
Segmentation fault

---

### Post by credobyte on 2009-08-04
Check ( post here ):
```
/home/gonzo/hs_err_pid21040.log
```

Try:
```
sudo apt-get remove openjdk-6-* && sudo apt-get install sun-java6-jre sun-java6-plugin
```

---

### Post by GonZo1323 on 2009-08-04
bash: /home/gonzo/hs_err_pid21040.log: Permission denied
gonzo@gonzo-desktop:~$ sudo apt-get remove openjdk-6
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package openjdk-6

and now justin.tv works
youtube still will not play any videos
and i still dont have my bookmarks any ideas?

---

### Post by credobyte on 2009-08-04
Could you please follow the codes I've posted earlier ? If I wrote openjdk-6-*, it doesn't mean the same as openjdk-6. Also, the log file needs to be cat'ed or opened with a text editor, not executed in bash ;)
Unless you do it right, can't help you ..

---

### Post by GonZo1323 on 2009-08-05
im sorry but im not sure what you mean

---

### Post by GonZo1323 on 2009-08-06
any help please i dont wanna go back to windows.

---

