---
title: "Help with 11.04 Launcher"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by slayner117 on 2011-06-27
Alright what I am trying to do is access the option with the launcher where you have multiple windows and you click on the icon (in which you have the multiple windows Ex: Firefox) and it shows the windows and from there you can select which window to open. 

However it is not working. I have tried restarting the computer and tried it with different icons, but for some reason it will not work. 


I will also mention I have set different compiz options. I believe it may be an issue within there. If it is, can someone tell me what I need to set to have this option. 

Thank you in advance.

---

### Post by josephmills on 2011-06-27
try reinstaling fire fox save any setting and bookmarks and what not and open your terminal and do a ```
sudo apt-get remove --purge firefox
``` then ```
sudo apt-get install firefox
```anything ? but I am not sure that I follow you question 100% is it firefox or is it other programs that are not doing this ?

---

### Post by slayner117 on 2011-06-27
Sorry about me not being 100% clear on my wording. It was all applications.

However I got it to work, All I had to do was do was type 

Unity --reset 

In the terminal, that reset all the compiz options back to normal. Thank you for your help regardless. I suppose the problem was simply an option I messed up.

---

### Post by josephmills on 2011-06-27
cool you should mark this as solves so other members can see it and it might help them out. thanks for getting back to me you :guitar:

---

