---
title: "Whats the best os for a file server ?"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by bobyo134 on 2009-07-20
Whats the best os for a file server ? I have a webserver , and i just built a file server , the specs are 3.4ghz intel (single core) , 512mb of ram , msi mainboard , 2 ide drives ( main boot =8gb , second =250gb ) , and 1 sata drive (500gb ) . i'm thinking about debian but i don't no , this system is not new it's peices and parts mostly from my old old gaming rig from 2004 , and most of you are ganna hate for putting the parts into an emachiens case but it was just so small and perfect, anyways i tried windows server 2003 ( bigest mistake ever !) and it'd could'nt even connect to the internet, so i tried 2008 , and it connected but after 9 years u'd think thed upgrade the user interface . well thx for helping guyz ur the best !

---

### Post by eragon100 on 2009-07-20
Debian will fly on that machine, and ubuntu would to. Ubuntu is based on Debian anyway.

However, do you want a GUI? Because if you think the windows GUI is outdated, you should be informed that a server linux installation of either debian or ubuntu doesn't have a GUI at all. You will have to use the terminal. There is nothing wrong with that, it is like old DOS but more powerfull. You will however have to spend some time on learning some commands and stuff.

If you want a GUI, I suggest you keep windows server 2008, because an outdated GUI is still better than no GUI, right? I presume windows server is running fast and stable enough, since you don't mention any problems with that?

---

### Post by Mighty_Joe on 2009-07-20
> **eragon100 said:**
> However, do you want a GUI? Because if you think the windows GUI is outdated, you should be informed that a server linux installation of either debian or ubuntu doesn't have a GUI at all. You will have to use the terminal.

You can install X on Ubuntu Server.  It's a [popular option]("http://ubuntuforums.org/showthread.php?t=1155961") for those who don't like all the extra stuff on the standard Ubuntu desktop.
Personally, I run Ubuntu Server (no GUI) on my home file server.  Since you aren't running a high-availability server, any OS that does what you need it to do service-wise should do fine.

---

### Post by Cyked on 2009-07-20
What are the draw backs from going with an Ubuntu install vs. Ubuntu server (I mean other than no GUI)?   Is there something you can run on server but not the desktop install of Ubuntu?

I would assume the main reason is the server version is much, much lighter.  Is that all?

---

### Post by benj1 on 2009-07-20
is a gui really that important for a file server?

im assuming youre asking what distro to use. ubuntu has a server iso but that doesn't have a gui, debian stable is probably a good idea also.

---

### Post by benj1 on 2009-07-20
> **Cyked said:**
> What are the draw backs from going with an Ubuntu install vs. Ubuntu server (I mean other than no GUI)?   Is there something you can run on server but not the desktop install of Ubuntu?

I would assume the main reason is the server version is much, much lighter.  Is that all?

i think it has a slightly modified kernel, add the apps are more server orientated so no open office, but apache

---

### Post by NightwishFan on 2009-07-20
Under the hood, Ubuntu makes a lot of changes for server performance. So I would actually advise you use the server edition. You can get a rundown here:

[http://www.ubuntu.com/products/whatIsubuntu/serveredition](http://www.ubuntu.com/products/whatIsubuntu/serveredition)

---

### Post by bobyo134 on 2009-07-20
well i should have mentiond that windows server is really slow and is consuming most of my resources and i don't even have it set up to do anything yet , i have have run ubuntu server , but it was on a different machien and with a usr interface installed it was so slow i couldnt use it but now that i think about it that computer had manythings wrong with is and is now sitting in 15 picies, i think i will try ubuntu , i prefer it over debian , even thought it is debian based

---

### Post by NightwishFan on 2009-07-20
Good luck. I am not experienced in server affairs sadly, but I hear good things about Ubuntu server. I advise you use a lightweight GUI if you would rather not use the commandline. Try fluxbox. There might be some GUI frontends to server commands.

---

