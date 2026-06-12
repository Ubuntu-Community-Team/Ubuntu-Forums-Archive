---
title: "Apt-get dist-upgrade"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by Dori922 on 2011-07-19
Hey!

I recently got an internship with a company and they gave me a task of learning how to build and manage UEC servers.

So far its going grand but i tried out a command, sudo apt-get dist-upgrade and it ran fine until the end. Its been stuck on one line for the past 30-50minutes, "Eucalyptus start/running, process 14546" the command hasnt finished i dont think, because it hasnt given me a command prompt... i havent installed a gui yet so im very stuck as to what to do :( is this normal or has it crashed?

---

### Post by jacksaff on 2011-07-19
This site is very useful.

[http://www.linuxcommand.org/lts0080.php](http://www.linuxcommand.org/lts0080.php)

---

### Post by Dori922 on 2011-07-19
problem is its not giving me back control/cmd prompt so i cant issue any new commands.. its like its trapped in an infinite loop but this is second time ive installed uec and hit this problem... :(

---

### Post by jacksaff on 2011-07-20
ctrl-alt-f1 (to f6) will give you another terminal to log into.
You can switch between them by the same command. 

ctrl-c should bring your command prompt back. Is this not working?

---

### Post by Dori922 on 2011-07-21
hey jack, 

i can switch between terminals but ctrl-c on the upgrade terminal(T1) doesnt give the command prompt back.. this is on the node now using "sudo apt-get upgrade" instead of "sudo apt-get dist-upgrade" and it hit the same problem... which is odd because on the front end earlier i used "sudo apt-get upgrade" and it worked.... someone suggested that the network drivers are being updated but then the following packets have the old network info so dont know where to go causing a loop... but i dont know how to fix it :/ and upgrade is kinda important, or will be when i put it into production :/ :P

---

