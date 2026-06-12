---
title: "Running a program at startup."
date: 2011-04-16
forum: New to Ubuntu
---

### Post by Jay86 on 2011-04-16
Hello everyone.

I have managed to set-up a dedicated unreal tournament server (for my friends and I to play on) on my home server that I use for file sharing (samba/ftp) and websites (LAMP stack). I believe that this is legal so please do not ban me from the forum if I'm wrong.

I would be glad to write a tutorial in the future on how to do this with very little effort.

So far, having our own UT99 server has been great. The only problem is that I have to manually start the UT server software every time I reboot my machine (which is less than ideal). This is how I have been starting it:

First, I get into the directory where my game server files are:

"cd /usr/local/games/ut-server"

Then I use this command to start my game server:

"./ucc server CTF-Face?game=BotPack.CTFGame? ini=UnrealTournament.ini log=ut.log -nohomedir &"

Could you please tell me how to make this application start when my server powers on, without me having to ssh into it and set it up again every time we have a power failure? (Power failures are common due to overloaded circuits and my friends tripping over power cords).

(I would know how to do this in windows.. I am not sure how to go about this in Ubuntu)

More info:
This is my first post. I am good at following instructions, but am still learning about Ubuntu. I do all management of my server via telnet/ssh (command line) and have no graphical desktops installed. I do have physical access to it and a spare monitor/keyboard if needed. I know how to use VI as a text editor.

This is my server:
Old junky motherboard (can't remember manufacturer)
Intel P4 3.0 GHz
512 MB RAM
500 GB Western Digital Caviar "Green" connected via Sata2
Dlink Gigabit NIC

Thank you.

---

### Post by fabricator4 on 2011-04-16
[This]("http://www.linuxquestions.org/questions/slackware-14/auto-execute-shell-script-on-startup-294891/") appears to be the method most often suggested.

Chris

---

### Post by Jay86 on 2011-04-16
Thanks for your help.
After reading that link and googling around some more..

I made a file called "unreal" and put it in the /etc/init.d/ folder. This is the file:

"#!/bin/sh
/usr/local/games/ut-server/./ucc server CTF-Face?game=BotPack.CTFGame? ini=UnrealTournament.ini log=ut.log -nohomedir &"

If I go to the init.d directory and give the command "bash unreal" it starts up the unreal server perfectly, but when I reboot my server this script is not executed.. I was under the impression that everything in init.d is executed at start-up. What am I missing?

---

### Post by Dlambert on 2011-04-16
System>Prefrences>Start-up Applications? Then add the command? Will that work?

---

### Post by Jay86 on 2011-04-16
I am doing this over ssh, and have no desktop. (All command line). Thanks for the suggestion though.

I think I figured out what I was missing. Here's a link explaining it pretty well: [http://www.debian-administration.org/articles/28](http://www.debian-administration.org/articles/28)

I'll post back if this works, so that others can learn from my confusion.

---

### Post by Jay86 on 2011-04-16
Nope, it still doesn't work.

---

### Post by vivek.pandey on 2011-04-16
> **Jay86 said:**
> Hello everyone.



I would be glad to write a tutorial in the future on how to do this with very little effort.


i am waiting impatiently for your tutorial

---

### Post by dcsoldschool53 on 2011-04-16
Check out those pages.

[run_startup_programs]("http://ubuntuforums.org/showthread.php?t=1639458&highlight=Running+program+startup.")

[startup script]("http://www.howtoforge.com/forums/showthread.php?t=22914")

Did you do the update for it?

---

