---
title: "cant download anything from software center"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by hookitup on 2011-05-14
i keep getting an error when trying to download anything from the software center 

"There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks."



Any solutions ?
Thanks in advance.

---

### Post by Rubi1200 on 2011-05-14
Hi and welcome to the forums :-)

Close all instances of package managers and open a terminal. Run the following commands and post back here with the exact errors please:

```
sudo apt-get install -f

sudo dpkg --configure -a

sudo apt-get update
```

---

### Post by ExileAmongYou on 2011-05-14
You could also try opening Synaptic Package Manager, then Edit->Fix Broken Packages.

---

### Post by hookitup on 2011-05-14
It wont let me get past this after running that command above ^


 TrueType core fonts for the Web EULA                                        
 &#9474;                                                                             
 &#9474; END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE                           
 &#9474;                                                                             
 &#9474; IMPORTANT-READ CAREFULLY: This Microsoft End-User License Agreement         
 &#9474; ("EULA") is a legal agreement between you (either an individual or a        
 &#9474; single entity) and Microsoft Corporation for the Microsoft software         
 &#9474; accompanying this EULA, which includes computer software and may include    
 &#9474; associated media, printed materials, and "on-line" or electronic            
 &#9474; documentation ("SOFTWARE PRODUCT" or "SOFTWARE"). By exercising your        
 &#9474; rights to make and use copies of the SOFTWARE PRODUCT, you agree to be      
 &#9474; bound by the terms of this EULA. If you do not agree to the terms of        
 &#9474; this EULA, you may not use the SOFTWARE PRODUCT.                            
 &#9474;                                                                             
 &#9474;                                  <Ok>

---

### Post by Rubi1200 on 2011-05-14
Were you in the process of installing the restricted packages when the problem started?

The EULA is normal and you can accept it. What happens if you do? Do you still get errors when running the commands I gave before?

---

### Post by hookitup on 2011-05-14
i ran the command you gave me and thats what poped up and it wont let me accept it, i hit enter and ok and everything, will not proceed after that . and just tried downloading something from software center , same error. i cant even watch youtube videos because i need to download adoby and it wont let me, i just put ubuntu on my computer like a week ago so im thinking i will just reinstall , i only have a Conky config on it and unity 2-d so not a big deal,


Thanks for your help

---

### Post by wildmanne39 on 2011-05-14
> **hookitup said:**
> i ran the command you gave me and thats what poped up and it wont let me accept it, i hit enter and ok and everything, will not proceed after that . and just tried downloading something from software center , same error. i cant even watch youtube videos because i need to download adoby and it wont let me, i just put ubuntu on my computer like a week ago so im thinking i will just reinstall , i only have a Conky config on it and unity 2-d so not a big deal,


Thanks for your help

HI, reinstalling is not always the best answer, I think you might have 2 programs open at  the same time trying to install packages, like the terminal and the software center, you can only install packages from one program at a time. Did you try to highlight ok to accept the agreement by using the tab key or arrow key?:D

---

### Post by hookitup on 2011-05-16
to be honest im not quiet sure what i did. i tryed to install something for teamviewer and it messed stuff up

---

### Post by hookitup on 2011-05-16
ok now its working, hum strange, maybe ur right ? there probably was a pending download or something and at the same time i was trying to download team viewer.

thanks for help

---

