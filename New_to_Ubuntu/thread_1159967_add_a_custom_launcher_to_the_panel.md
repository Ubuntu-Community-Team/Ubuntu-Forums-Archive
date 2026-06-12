---
title: "add a custom launcher to the panel"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by ierpe on 2009-05-15
Newbie question:

I have this application in /opt/jude_community/jude.jar
so to launch it the command is java -jar /opt/jude_community/jude.jar

But when I add this to a launcher on the panel it doesnt work!!

What am I doing wrong?

---

### Post by timcredible on 2009-05-15
maybe pick 'application in terminal' instead of 'application' when creating the launcher.  not sure, just a guess, but easy to try.

---

### Post by superprash2003 on 2009-05-15
try this, place jude.jar in your home folder and insert command as java -jar jude.jar ... does it work?

---

### Post by ierpe on 2009-05-18
I created a symbolic link to the jar I wanted to launch, then copied it into my home folder.

I finally added the command: java -jar jude-community.jar to the launcher I created and it works fine!

Thanks for your help.
P

---

