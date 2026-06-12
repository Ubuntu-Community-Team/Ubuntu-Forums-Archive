---
title: "Need Help:ShellScripting,NetworkConnection,ApplicationI nstallation"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by D BRUCE on 2010-04-09
Hello all
I am new to Linux and I installed Ubuntu9.04 CD version 
I have 3 main problems 

1) I am able to execute basic UNIX commands but I am not able to know how to run SHELL SCRIPTS in my Linux machine.
I tried vi command but I was not able to punch in the code and run it.

2) I am not  able to use internet . I played with Network Manager but failed

3) This is the most embarrassing problem I've been facing for a long time.
   [U] Difficulty in installing different applications like MP3 players,java,c,c++          
    compilers   etc.[/U] I tried to get the help from ubuntu forums .and got generous solutions.
     Even offline downloading of the required packages and depedencies and their
     installation remained as my reverie.

Any one please help to sort this out and to have a smooth Linux journey.

Regards,
D Bruce

---

### Post by moetunes on 2010-04-09
1) are you making the scripts executable -  chmod +x /path/to/scriptname
2) is it wired or wireless internet please?
3)try in terminal   apt-cache search "app name"
for mp3 do   sudo apt-get install ubuntu-restricted-extras
java I don't know about but c++ falls under   sudo apt-get install build-essential

---

