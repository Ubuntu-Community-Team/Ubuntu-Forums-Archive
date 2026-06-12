---
title: "Freezing when I try to run an app?"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by yourcat on 2010-02-23
[COLOR=black][FONT=Verdana]Hello, I have recently installed Ubuntu 9.10 on a Dell Latitude D600. It has been working ok, except the fact when I try to run an application it freezes. I have tried to open Firefox and it just stops and I have to restart the computer the "hard way" by pressing the power button. It did the same thing when I attempted run open office. I also tried reinstalling from the disk I burned.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I then came across an article (on this site) saying to run failsafe GROME. I tried it and have not crashed since! The only problem is that I can’t get wireless. I have to go by the Ethernet cable.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Also, something happened to my panel up top on the right. The only icon on the right is the email icon, the time and my name.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Please help!![/FONT][/COLOR]
[FONT=Calibri][SIZE=3]thanks.[/SIZE][/FONT]

---

### Post by wojox on 2010-02-23
Try going into appearance and turning off Desktop Effects.

---

### Post by yourcat on 2010-02-23
[COLOR=black][FONT=Verdana]Ok I did. How do i connect wirelessly?[/FONT][/COLOR]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]

---

### Post by yourcat on 2010-02-23
YAY i opened an internet without crashing!! now how do i connect it....

---

### Post by wojox on 2010-02-23
If you open a terminal and copy and paste:

```
lspci | grep -i net
```

What does it say?

---

### Post by Rayve on 2010-02-23
To get icons back on your top panel, right click on a free space on the panel and click "Add to Panel".  Then choose the item you want to add - Network Connections, for example.

You can also go to System > Preferences > Network Connections to get there directly.  From there, you can examine in more detail your wireless set up and try to find the problem.  Sometimes, for me, it's a matter of adding the new wireless connection with appropriate connection information and then making it available to all users, usually by clicking on the button on the bottom left of the Connections window.

Good luck!

---

### Post by yourcat on 2010-02-23
this may seem like a stupid question, but how do you make the vertical line in the code? (I'm new to this)
 
Also, i cannot add network connections to the panel. it just is not one of the selections

---

### Post by yourcat on 2010-02-23
never mind i figured out how to make a vertical line shift+\=|
 
and I figured out how to add to pannel

---

### Post by yourcat on 2010-02-23
Ok i tried the code and it said
 
"no command '1spci' found, did you mean:
    Command '1spci' from package 'pciutils (main)
1spci: command not found"
 
did i type it wrong? what should i do know?

---

### Post by mechro on 2010-02-23
lspci... Letter l, not number 1 :)

---

### Post by yourcat on 2010-02-23
ohhhh thanks. testing now

---

### Post by yourcat on 2010-02-23
Ok this is what it says 
 
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless Controler (rev 02) 
 
what does it mean?

---

