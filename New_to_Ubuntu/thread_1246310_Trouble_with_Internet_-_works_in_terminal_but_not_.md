---
title: "Trouble with Internet - works in terminal but not in other applications"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by cyberram on 2009-08-21
Hi All,

I need some help here. I used to connect to Internet through my universities wireless network. The network connects fine and I can browse using firefox and chat using skype.

But something is preventing my other system applications like update manager from connecting to the internet. When I run the update from terminal using

sudo apt-get update
sudo apt-get upgrade

It works fine. Problem exists only when I use the GUI. Can this be a problem with my proxy settings? Could someone please explain me what could be wrong in my system.

Thanks.

---

### Post by bodyharvester on 2009-08-21
im sorry but i dont see how thats a problem, lol, the terminal is quicker, im sure my gui freezes for a second or something when it checks for updates, i know thats not exactly your problem but id advise getting to love the terminal, it reaaly will make life easier than using any gui

enjoy

---

### Post by cyberram on 2009-08-21
I do love to use the terminal. But the point is I m a beginner. I m trying to switch from windows to linux. I still don't knw wat the commands I can use in terminal and I m having some difficulty in understanding the man pages too. I am feeling the details too technical to digest in one shot.

but still I am trying :)

u knw wat, I don't knw where the binaries for my programs are stored in linux. I knw in windows the "program files" folder contains the installed applications. I still don't knw how linux handles the installs and which system folder is for wat purpose.

It would be much appreciated, If u could help me with some input on tht or if u can guide me to some nice tutorial abt it. :)

---

### Post by dlmarti on 2009-08-21
apt-get uses http just like firefox, doesn't make sense that it doesn't work.
Are you by any chance using a proxy?

---

### Post by bodyharvester on 2009-08-22
> **cyberram said:**
> u knw wat, I don't knw where the binaries for my programs are stored in linux. I knw in windows the "program files" folder contains the installed applications. I still don't knw how linux handles the installs and which system folder is for wat purpose.

me neither, i havent a clue where most is stored, usually somewhere like /usr/share
but i guess ill learn properly someday. if you "sudo apt-get install" the program or whatever is usually ready for use and you can get to them form the correct menus, everything is much easier than in Windows, i guess thats the biggest thing you must get used to, less configuration and everything just kinda works.

:)

---

### Post by cyberram on 2009-08-22
Ya I am behind a proxy and I have configured it using the network proxy in administration menu. I have set Firefox to use the system proxy. I am not sure whether update manager is loading the correct proxy from the system. Is there a way I can check what proxy setting each application is using?

---

