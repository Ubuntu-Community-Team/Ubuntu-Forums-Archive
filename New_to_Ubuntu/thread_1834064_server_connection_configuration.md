---
title: "server connection configuration"
date: 2011-08-27
forum: New to Ubuntu
---

### Post by louie2114 on 2011-08-27
hello, ubuntu genius! 

i'm totally new to ubuntu, if anyone out there could please help me.

i have two computers in my room: 

one is installed with win7 where i do most of my works. im using wifi to connect this pc to the internet.

in one special place sits a dell optiplex745 box with 1GB RAM and an 80GB HDD.in this second box, i installed LAMP using ubuntu server 10.4 LTS. i have not installed anything in this box except those packages that come from ubuntu as i wish to make it as a standalone server, not even a GUI.on top of this box is where my modem rests with a cable connected to it for internet access.

my questions (please bear with me as i have lots of questions):
1. how can i access my server from my windows pc? is it through what is called ftp connection? if it is, what is its configuration process? (both windows and ubuntu)

2. can i manipulate PHP, phpMyAdmin and/or SQL in my server from my win7 pc? how?

i am a newbie in web designing using CS3 and manipulating them  trough PHP and SQL (phpMyAdmin). as of now, i am doing all of these in my windows pc installing a WAMP server on it. so far, designing with WAMP works fine but i trust the robustness of ubuntu to carry out  server handling more than windows - my reason to venture this other box. the concept that i wish to relay is this: i will do exactly the same CS3 web designing in my windows pc but, instead of using WAMP in the same pc (localhost/server_name/page_name.php), i will be using LAMP from that other box. could this be possible? do i need to install additional applications from windows or packages from ubuntu to make it work? (btw, every time i run the ubuntu server, everything works fine [OK], except *check syslog for diagnostics [failed] - mention this just in case this has something to do with the process later on). 

please, if anyone out there can give me idea on steps of this process, or recommend a site or a blog that could provide answers to these, i would appreciate it very, very much.

---

### Post by jacobsallan on 2011-08-27
You can run command line arguments on your Linux box from a Windows program.  Download PUTTY from [http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/) , read the manual (at least the start of it), and try it out.

---

