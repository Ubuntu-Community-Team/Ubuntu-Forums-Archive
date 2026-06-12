---
title: "Swapping languages in Ubuntu"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by RabbitWho on 2010-03-20
I found the code for this which is
```

sudo aptitude install language-pack-es
```

What i found was the Spanish one but i changed "es" to "cs" if this is the wrong code for Czech then someone warn me! 

Anyway here's the terminal read out: 

rabbit@penguincounter:~$ sudo aptitude install language-pack-cs
[sudo] password for rabbit: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  language-pack-cs language-pack-cs-base{a} 
The following packages will be REMOVED:
  libgnomedesktop2.20-cil{u} libnotify0.4-cil{u} librsvg2-2.18-cil{u} 
  libwnck2.20-cil{u} linux-headers-2.6.28-11{u} 
  linux-headers-2.6.28-11-generic{u} 
0 packages upgraded, 2 newly installed, 6 to remove and 1 not upgraded.
Need to get 1545kB of archives. After unpacking 70.1MB will be freed.
Do you want to continue? [Y/n/?]  


My question is: What is it removing and why? Don't I need that stuff? I'll want the English version of the desktop too in case of emergencies or if someone else uses the computer, so I was hoping I'd be able to just swap back and forth at the log in screen.


Thanks for your help.

---

### Post by RabbitWho on 2010-03-20
So I bit the bullet and tried it and taking those things out doesn't seem to have done any harm. But it also didn't make much difference, all that has changed is the file names for default files and I could have done that myself anyway. 
Applications, Places, System, all that, the log out screen, the alert messages, everything is still in English.

---

### Post by RabbitWho on 2010-03-20
Oh my goodness, it didn't rename the files it created new ones with the  new names. What a load of hassle! Half my programs stopped working for a while because they were all like "Cannot find file specified" and I was all like "!?" and it was all like "bash: !?: event not found" and i've had to go around and manually fix everything back to how it was.

---

