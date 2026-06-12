---
title: "please help i just wanna play a game"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by colehelmes87 on 2010-12-05
new to ubuntu as of ...earlier tonite lol tried wine tried virtual box. idk whats wrong. plz someone explain how to play wonderland online.. its a mmorpg. if you dont know what it is and your skilled in this plz figure it out. plenty of ppl wanna play it but every one else that knows linux doesnt even try to make sense to explain and ive seen in person its possible.. i have ubuntu ver 10.10 an fully updated and understand computers quite well.. its the command terminal that gets me... plz some one help

p.s. plz dont ask questions it wont help you itll just be a waste of everyones time cuz i just dont know

---

### Post by colehelmes87 on 2010-12-05
sry just want to add if im willing to use virtual box im pretty willing to do what ever you give me.. anything would be appreciated

---

### Post by mlentink on 2010-12-05
> **colehelmes87 said:**
> i have ubuntu ver 10.10 an fully updated and understand computers quite well.. its the command terminal that gets me... plz some one help

p.s. plz dont ask questions it wont help you itll just be a waste of everyones time cuz i just dont know


I prefer it if you wouldn't use texting language. Many of us here are non-native speakers.

What OS did you try in Virtualbox? What have you tried to make it run in Wine? PLease understand that while the Wine developers do a fantastic job in making many applications run under linux, that simply doesn't  mean that everything will run.

Where have you seen it run? What has that person done to make it run?

Please provide more information as it will be very difficult to help otherwise, and if you're not prepared to answer questions it will be virtually impossible.

---

### Post by Giraffemonster on 2010-12-05
Sorry if you don't want the community to ask you questions, but it needs to be done. We can't help you if we don't have any information.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=7026](http://appdb.winehq.org/objectManager.php?sClass=application&iId=7026)
Is this the game you want to run? If the application and version of said application are not at platinum, there will be a few issues when you install/run it. Gold is good enough though.

Are you sure you installed Wine and VirtualBox correctly? More information would be of great help.

---

### Post by Mark Phelps on 2010-12-05
> **colehelmes87 said:**
> ...p.s. plz dont ask questions it wont help you itll just be a waste of everyones time cuz i just dont know

This is a self-help forum, not free techincal support.  We're not mind readers here.

Any solution is going to require you working WITH us. If you're not willing to do some work on your own -- like answering questions -- then quit wasting our time.

---

### Post by Spyderkid on 2010-12-05
go onto the sofware centre and install Ubuntu Restricted Extras. then try

---

### Post by Sef on 2010-12-05
> p.s. plz dont ask questions it wont help you itll just be a waste of everyones time cuz i just dont know

If you are not willing to answer any questions, then this thread is a waste of time for you and everyone who wants to help you. So do you want to answer questions, or should I lock it?  

Note: If you do not understand a question, then it is fine to admit that you do not understand it. All of us started from zero.

---

### Post by colehelmes87 on 2010-12-06
I wasn't trying to be rude just thought it would be easier to just tell me how, I honestly thought someone might just copy and paste a tutorial. when I start the install with wine 1.2.1 it just sits there and says connecting. Ive read all kinds of things using wine or virtual box so i got really confused.. i looked here
 [http://appdb.winehq.org/objectManager.php?sClass=application&iId=7026](http://appdb.winehq.org/objectManager.php?sClass=application&iId=7026)
and that all sounds hreat and I'd love to try it but it just says connecting theres no firewall or anything but i am new to this so as far as I know i have to just turn a setting on or something. I appreciate the feed back it actually did help but I could use more. thanks

---

### Post by blazemore on 2010-12-06
colehelmes87, please can you tell us what version of "Wonderland Online" you are trying to play?

That page you showed us has a number of different versions, some of which work very well in Ubuntu, and some of which don't.

Thanks!

---

### Post by colehelmes87 on 2010-12-06
im running wine 1.2 and trying to install wonderland 6.0. I read somewhere i need wine to recognize main.exe and aLogin.exe.. dont know what that is. when i paste the script into the terminal it seems like it tries to open but the games not installed and i assume is why it says it cant find aLogin.exe.. i try to install the game but its a downloader so it just sits there saying connecting-my biggest thing is it just wont attempt to install

---

### Post by blazemore on 2010-12-06
Okay, what you need to do is follow these steps.
I'm assuming you already have the game installed.

[LIST=1]
[*]Go to Applications -> Wine -> Configure Wine
[*]Where is says "Windows Version" change it from Windows XP to Windows ME
[*]Go to the "graphics" tab and tick the box saying "emulate a virtual desktop.
[*]Change the desktop size to your screen resolution, eg mine would be 1680 x 1050 but make sure you set yours to the right one
[*]Click OK, and run the game again
[/LIST]

---

