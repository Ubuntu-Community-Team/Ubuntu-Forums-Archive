---
title: "No installation is taking place"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by hthart on 2010-03-23
I have just recently reinstalled ubi on a new drive.  All went well. Yes, here comes the "but".  When I try to install software under the software menu, I first got a message that the system was waiting for the software manager to complete its work.  Now when I go to the software menu and select a program to install there is no install button.  HELP!!

---

### Post by houseworkshy on 2010-03-23
I haven't used the wubi install, prefering separate partitons or drives, so this may not be valid but just in case.....  
First I'd take a look at software sources and make sure that all but source code are enabled then try again.  
If this doesn't work another way round would to be to use the terminal to install instead of the GUI.  The terminal can be accessed via Applications>Accessories>Terminal.  The command you'd need is "apt-get install" which will need a "sudo" in front of it as installing is an admin action.    If you type "man" in front of any command it will give you the manual page for it ( type "q" to exit the manual ), I'd recommend doing this.  First I'd use "sudo apt-get update" which will refresh your software lists, then "sudo apt-get upgrade" which will update your system.  Then "sudo apt-get install ( whatever the program name happens to be)".   The use of sudo will require your password before the command is run.  As the grace period lasts fifteen minuets you will only be asked the first time.  It is good practive to avoid browsing while the sudo grace period is active.  If you finish earlier than that and don't want to wait "sudo -k" will terminate the grace period.   This isn't a fix so much as a dodge round the GUI but will allow you to install and the updates may even fix the problem.
I notice you are fairly new here, welcome :)  If you are also fairly new to Ubuntu I can recomend this free pdf [http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)
The online documentation is also good for Ubuntu [https://help.ubuntu.com](https://help.ubuntu.com).  Working through it will not only give you a nice basic overview but helps you to install things as you go along.  Good luck with it all.

Edit :-
Sorry I miss-read ubi for wubi.  It all still applies though.  I forget to mention where you can find software sources System>Administration... This is also where you can find the synaptic package manager which is a more powerul version of the GUI installer.  You will find better and clearer advise than I can give through the links above.  

This is not directly related but will probably be useful later; read up on "mediabuntu", which is a reposititory many like to add ( free but closed source software eg flash, various codex etc ).  A nice quick guide on it can be found on these forums [http://ubuntuforums.org/showthread.php?t=766683&highlight=mediabuntu](http://ubuntuforums.org/showthread.php?t=766683&highlight=mediabuntu)

---

