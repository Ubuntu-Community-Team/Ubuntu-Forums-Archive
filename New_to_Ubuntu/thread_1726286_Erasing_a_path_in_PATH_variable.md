---
title: "Erasing a path in PATH variable"
date: 2011-04-10
forum: New to Ubuntu
---

### Post by Zombir on 2011-04-10
Hi all, 

I am a newbie and I fell a bit into a trouble trying to do my java project in Ubuntu. For this project I had to download a jar file (the connector, to be precise) and set the bash's PATH variable to it. I set it using, 

```

export PATH=$PATH:/home/pramod/Desktop/mysql-connector-java-5.1.15/mysql-connector-java-5.1.15

```But then I realized this path is wrong. Now I want to erase the part I added. 

I Googled around but I'm scared to do what they suggest since I don't want the whole PATH variable erasing out. 

Can somebody please suggest me a way to erase only the part I added to the PATH variable?

Sorry if this is an FAQ. 

Thank you very much.

---

### Post by ~Plue on 2011-04-10
the use of the PATH variable is to search for scripts in the given directory so that you wouldn't need to enter the complete path to the executable/script (google can give you a better definition)[FONT=monospace]

exporting [/FONT]PATH without a string is completely useless, so unless that is your /etc/profile file and you've already deleted the defaults, removing the entire line wouldn't do any harm

good luck

---

