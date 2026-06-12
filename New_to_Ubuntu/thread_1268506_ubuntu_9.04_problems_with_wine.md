---
title: "ubuntu 9.04 problems with wine"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by theoak on 2009-09-17
hi so i have a new problem i can not figure out or find any posts about my current problem

so i have ubuntu 9.04 and installed wine through my terminal, and when i open any program i get an error that says the program ran into a serious problem and had to be closed. 

any idea what the reason for that is. mayhap i have the wrong wine program or did i not do something right configuring wine.

---

### Post by stumbleUpon on 2009-09-17
What do you mean you installed wine through the terminal? Did you use apt-get or aptitude to install....??? If so that should be fine.

The preferred way to install wine is using the ubuntu repos. See here

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

and

[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)


What program were you trying to run using wine and how were you trying to open the program...?? can you post some details and also the terminal output...??

---

### Post by theoak on 2009-09-17
ok so i am trying to run world of warcraft and i copied the files from the cd dvd into a root desktop and ran the installer from the acttual folder i copied the files into because i couldnt get it to run from my terminal. then after full installation when i started the program and it was patching i got the serious problem program needs to close error, and now when i try to run the program from the file folder i get the same error before i even start patching.

i also had this error when i tryed to open other programs that came with wine, such as internet explore and windows media player. im not trying to install those programs but was just checking if it could be a problem with wow or if it was a problem with wine. and what i conclude is its a problem with wine.

i used the command sudo apt-get install wine

---

### Post by XCan on 2009-09-17
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=17421](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17421) is rated as platinum by most users. So I wouldn't draw the conclusion that it's Wine that quickly. Have a look at the link, there should be plenty of troubleshooting tip there.

---

### Post by theoak on 2009-09-17
i have to say thank you to everyone that replied to my post.
i have wow patching and no errors.
as well i was not implying wine doesnt work, but that i was having problems running programs in wine... due to my inexperience using linux/ubuntu and wine. with that note i thank everyone that has helped me through my problems.

Thank You!

---

### Post by theoak on 2009-09-17
ughguhguhgg so many problems.

so now ive finished patching when i run the program from the wow.exe file i get a blizzard error it says this 
application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:        C:\Program Files\World of Warcraft\Wow.exe
Exception:       0xC0000005 (ACCESS_VIOLATION) at 0073:7C1DE0a0

The   instruction at "0x7C1DE0a0" referenced memory at "0x00000000".

Press OK to terminate the application

any ideas on what i should do??? i also along with this error i got another window that was to send the error to blizzard support to notify them of the error.

---

### Post by XCan on 2009-09-17
Although I've no experience with WoW, I noticed that the link I posted all were referring to new versions of Wine. There was also a discussion regarding Erro #132 on the same page. Which version of Wine are you using? Perhaps you may be interested in updating it to the newest version of Wine using the instructions at [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

