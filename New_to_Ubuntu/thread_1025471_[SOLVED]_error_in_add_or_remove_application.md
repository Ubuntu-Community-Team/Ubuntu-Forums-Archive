---
title: "[SOLVED] error in add or remove application"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by m.balakrishnan on 2008-12-30
hai,
    It shows following error message, when i open add or remove application. 
[B][I]"This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.,"
[/I][/B]
i need to install some sofware. How will i correct this error?  can one of you help?

---

### Post by Sef on 2008-12-30
> hai,
    It shows following error message, when i open add or remove application. 
[B][I]"This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.,"
[/I][/B]
i need to install some sofware. How will i correct this error?  can one of you help? 	

System > Administration > Synaptic Package Manager > Edit > Fix Broken Packages

---

### Post by TomasJancik on 2008-12-30
didn't you change /etc/apt/sources.list file?
have you tried what is says? (run 'sudo apt-get update' and 'sudo apt-get install -f')

---

### Post by m.balakrishnan on 2008-12-30
thanks for ur reply. i don't konw about ubuntu. but i tried to change file list like this file system--->etc-->apt--->source.list then i dont know what i do. please tell me how to change.

---

### Post by TomasJancik on 2008-12-30
if you don't know how to change that file, don't do it...
there are listed softare sources from which the packages manager downloads packages...
sometimes you can add some new source, but if you don;t know what you are doing in that file, don't do it!

maybe you could attach the file here so we can check if it's correct

---

### Post by m.balakrishnan on 2008-12-30
Thank u  but i have one doubt. should i restart the system while i will change?

---

### Post by TomasJancik on 2008-12-30
not needed to restart, but update the packages database... just run the command in terminal
sudo aptitude update

---

### Post by m.balakrishnan on 2008-12-30
thank you friends. i done this process. now i can do install.

---

### Post by m.balakrishnan on 2008-12-30
i want to install java. is it possible? if it is possible, tell me how to install.

---

