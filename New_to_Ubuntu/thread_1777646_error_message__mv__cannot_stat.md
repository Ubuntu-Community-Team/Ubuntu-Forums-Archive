---
title: "error message:  mv:  cannot stat"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by Ceddrwyn on 2011-06-08
I have tried a couple different types of Linux and I keep getting the same error messages.

mv:  cannot stat  log/syslog.#:  No such file or directory 
fgrep syslog.#:  No such file or directory 

I did a google search and found a forum entry that said:

"The following could be the cause of this, as I did the same installation and have no problems installing ISPConfig on my Ubuntu 6.10. 
Ubuntu developers have replaced Bash with Dash, so the regular /bin/sh that is used to be linked to /bin/bash is now pointing to /bin/dash.

You can remove the /bin/sh and create a new link using:
rm /bin/sh (or if you want to be safe: mv /bin/sh /bin/sh.dash)
ln -s /bin/bash /bin/sh"

I got a message saying that it create the (synthetic) directory, but when I tried to run autorun again, I got the same error messages.

I was able to compile the code and makefile in the scr directory, but autorun keeps giving me problems.  I can manually find the files so I know they exist.  I have tried giving myself several permissions uneer Users and Groups, but nothing has helped so far.

Oh, I nearly forgot.  I am new to Unix/Linux so I am just starting with the commands.

---

### Post by jtarin on 2011-06-08
> **Ceddrwyn said:**
> I have tried a couple different types of Linux and I keep getting the same error messages.

mv:  cannot stat  log/syslog.#:  No such file or directory 
fgrep syslog.#:  No such file or directory 

I did a google search and found a forum entry that said:

"The following could be the cause of this, as I did the same installation and have no problems installing ISPConfig on my Ubuntu 6.10. 
Ubuntu developers have replaced Bash with Dash, so the regular /bin/sh that is used to be linked to /bin/bash is now pointing to /bin/dash.

You can remove the /bin/sh and create a new link using:
rm /bin/sh (or if you want to be safe: mv /bin/sh /bin/sh.dash)
ln -s /bin/bash /bin/sh"

I got a message saying that it create the (synthetic) directory, but when I tried to run autorun again, I got the same error messages.

I was able to compile the code and makefile in the scr directory, but autorun keeps giving me problems.  I can manually find the files so I know they exist.  I have tried giving myself several permissions uneer Users and Groups, but nothing has helped so far.

Oh, I nearly forgot.  I am new to Unix/Linux so I am just starting with the commands.

Preface your command with "sudo" to become root and if that doesn't work try "sudo mv /var/log/sys.log  <tonewlocation>

Remember you only own files in "/home/username". Root (sudo) owns everything else.....practically.

---

### Post by Ceddrwyn on 2011-06-08
I did all of that,no luck.  I made sure to move everything to my home folder, but that didn't work.  The instructions say I can type

sh ./autorun & so I typed sudo sh ./autorun &

This is what keeps repeating...

ceddrwyn@Destiny-VirtualBox:~/tbamud/tbamud-3.62$ ./autorun: 174: cannot create log/olc: Permission denied
tail: cannot open `log/olc' for reading: Permission denied
./autorun: 174: cannot create log/trigger: Permission denied
tail: cannot open `log/trigger' for reading: Permission denied
./autorun: 174: cannot create log/usage: Permission denied
tail: cannot open `log/usage' for reading: Permission denied
./autorun: 174: cannot create log/errors: Permission denied
tail: cannot open `log/errors' for reading: Permission denied
./autorun: 174: cannot create log/olc: Permission denied
tail: cannot open `log/olc' for reading: Permission denied
./autorun: 174: cannot create log/trigger: Permission denied
tail: cannot open `log/trigger' for reading: Permission de

(I can't remember what to type for code, sorry.)

I also tried following th steps here:

[http://ubuntuforums.org/showthread.php?t=1128388](http://ubuntuforums.org/showthread.php?t=1128388)

I upgraded and updated, but no such luck.  I didn't get the same exact error messages he did as he was following the guru's instructions, but it is still not working.

I need Linux to run this application, but I can't get the permissions to work as I want.  I am not sure how to proceed.

---

### Post by jtarin on 2011-06-08
sudo sh ./autorun &

---

### Post by Ceddrwyn on 2011-06-08
I typed that, I pasted how my error message changed above.  Now instead of mv Cannot stat and fgrep, I am getting tail and autorun 174.

I went to my home folder and I noticed the files had images of locks on them.  I right-clicked and choose permissions.  Even though this is in my home folder, it says that root is the owner not me.  How do I become the owner?

---

### Post by jtarin on 2011-06-08
Read that post again and start from message #12

---

### Post by Ceddrwyn on 2011-06-08
I don't have any broken packages.  I updated 4 pkg, but I am still getting the same error messages.

---

### Post by jtarin on 2011-06-08
> **Ceddrwyn said:**
> I typed that, I pasted how my error message changed above.  Now instead of mv Cannot stat and fgrep, I am getting tail and autorun 174.

I went to my home folder and I noticed the files had images of locks on them.  I right-clicked and choose permissions.  Even though this is in my home folder, it says that root is the owner not me.  How do I become the owner?Right-click on your /home/username directory and choose properties. Change "root" to your username then logout and then back in. If permissions are changed don't do anything until you post here again and I or someone responds. Your following instructions from other site then coming here for help. Start here and explain in detail what you are trying to do. If you are trying to install some software.....what is the name of the software and I will look and help you install it.

---

### Post by Ceddrwyn on 2011-06-08
Okay, I have done what you asked.
I am trying to compile and run TBAmud.  Here is the webpage:

[http://www.tbamud.com/content/readmebsd](http://www.tbamud.com/content/readmebsd)

---

### Post by wildmanne39 on 2011-06-08
> **Ceddrwyn said:**
> Okay, I have done what you asked.
I am trying to compile and run TBAmud.  Here is the webpage:

[http://www.tbamud.com/content/readmebsd](http://www.tbamud.com/content/readmebsd)
Hi, this should help with permissions.
[http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html)

---

### Post by jtarin on 2011-06-08
> **Ceddrwyn said:**
> Okay, I have done what you asked.
I am trying to compile and run TBAmud.  Here is the webpage:

[http://www.tbamud.com/content/readmebsd](http://www.tbamud.com/content/readmebsd)Have you compiled it successfully? If not here is a [link]("http://www.tbamud.com/files/FAQ.txt") to FAQ.

---

### Post by Ceddrwyn on 2011-06-08
Thanks wildman but I am going to wait until jtarin comes back before I do anything.  ;)

---

### Post by jtarin on 2011-06-08
> **Ceddrwyn said:**
> 
I did a google search and found a forum entry that said:

"The following could be the cause of this, as I did the same installation and have no problems installing ISPConfig on my Ubuntu 6.10. 
Ubuntu developers have replaced Bash with Dash, so the regular /bin/sh that is used to be linked to /bin/bash is now pointing to /bin/dash.

You can remove the /bin/sh and create a new link using:
rm /bin/sh (or if you want to be safe: mv /bin/sh /bin/sh.dash)
ln -s /bin/bash /bin/sh"

There are several solutions to this – you can modify the scripts that fail such that they use bash (change #! /bin/sh to #! /bin/bash), or more simply you can change the symbolic link sh, found in the /bin directory, to point to /bin/bash.
Like this on the autorun.sh file....open in gedit and edit the very first line.```
[COLOR="Red"]#! /bin/bash[/COLOR]
#
# CircleMUD 3.0 autorun script
# Contributions by Fred Merkel, Stuart Lamble, and Jeremy Elson
# Copyright (c) 1996 The Trustees of The Johns Hopkins University
# All Rights Reserved
# See license.doc for more information
```

---

### Post by Ceddrwyn on 2011-06-08
> **jtarin said:**
> Have you compiled it successfully? If not here is a [link]("http://www.tbamud.com/files/FAQ.txt") to FAQ.

I am able to compile and create the make file in the src directory.  It is the permission errors that stop me from initializing autorun.  I believe that is the last step.

---

### Post by jtarin on 2011-06-08
OK I compiled it and ran it with no problems.....if you will follow the attached instructions.I didn't change any scripts....I only followed instructions. Pay attention to changing directories. Use the command "ls" to list all files in the directory. You can copy a command from the text and paste it in the terminal. I did al of this in my /home/username/downloads/tbamud-3.62 folder. No problem with permissions. It made the syslog in the same folder automatically when I ran ./autorun.sh.

---

### Post by Ceddrwyn on 2011-06-08
> **jtarin said:**
> There are several solutions to this – you can modify the scripts that fail such that they use bash (change #! /bin/sh to #! /bin/bash), or more simply you can change the symbolic link sh, found in the /bin directory, to point to /bin/bash.
Like this on the autorun.sh file....open in gedit and edit the very first line.```
[COLOR="Red"]#! /bin/bash[/COLOR]
#
# CircleMUD 3.0 autorun script
# Contributions by Fred Merkel, Stuart Lamble, and Jeremy Elson
# Copyright (c) 1996 The Trustees of The Johns Hopkins University
# All Rights Reserved
# See license.doc for more information
```

Should I go ahead and try to run autorun again once I do this or is there another step?

---

### Post by jtarin on 2011-06-08
Read my last message #15. Ignore changing the script...not needed. Just read the document and my instructions in that message.. It's very easy.

---

### Post by Ceddrwyn on 2011-06-08
Nope, didn't work.  Same error messages.

---

### Post by jtarin on 2011-06-08
I'm going to recommend you compile again from the beginning following the instructions in Doc I sent, but first make a folder in your home directory and name it tbamud.Check your folder permissions on this folder before beginning. Now move tbamud-3.62.tgz into this folder. Delete your old tbamud-3.62 folder then go back to the tbamud folder you just made and right-click on tbamud-3.62.tgz and extract it.Now follow the document instuctions.You have to understand that autorun.sh creates the syslog. Read those instructions twice if need be. It works.

---

### Post by Ceddrwyn on 2011-06-08
> **jtarin said:**
> I'm going to recommend you compile again from the beginning following the instructions in Doc I sent, but first make a folder in your home directory and name it tbamud.Check your folder permissions on this folder before beginning. Now move tbamud-3.62.tgz into this folder. Delete your old tbamud-3.62 folder then go back to the tbamud folder you just made and right-click on tbamud-3.62.tgz and extract it.Now follow the document instuctions.You have to understand that autorun.sh creates the syslog. Read those instructions twice if need be. It works.

I have read these instructions in this format and on the TBAmud page dozens of times.  I have tried all these steps with Linux Mint, FreeBSD and Ubuntu.  Always get the same errors.


Oh ha ha ha,  just found something new.  I didn't understand that after I read the license I was supposed to type Q to accept.  I would always type it instead of trying to read it since I had read it 20 times.  It is doing something new.
Let me see if this works.

---

### Post by Ceddrwyn on 2011-06-09
Okay I tried this once but I got the same error message so I went back and followed the instructions to unzip and untar in the terminal and reconfigured and makefile.  I typed ./autorun.sh and it seems to be hanging.  I tried to close the terminal but it said it was in the middle of a process.  How long before I start seeing text or did I do something wrong?

---

### Post by jtarin on 2011-06-09
not ./autorun.sh......there is another.....    ./autorun  
You can probably Ctrl + C out of that terminal. You didn't read the Docs like I told you too.:P

---

### Post by Ceddrwyn on 2011-06-09
> **jtarin said:**
> OK I compiled it and ran it with no problems.....if you will follow the attached instructions.I didn't change any scripts....I only followed instructions. Pay attention to changing directories. Use the command "ls" to list all files in the directory. You can copy a command from the text and paste it in the terminal. I did all of this in my /home/username/downloads/tbamud-3.62 folder. No problem with permissions. It made the syslog in the same folder automatically when I ran ./autorun.sh.

You said autorun.sh, I was following your instructions.  I tried ./autorun & and sh ./autorun & -as the docs said and I have tried sh ./autorun.sh and sh ./autorun.sh & .  These are all possibilities from what you said and what the doc said.  I either getting a hanging prompt, the error messages, or 

ceddrwyn@Destiny-VirtualBox:~/tbamud/tbamud-3.62$ sh ./autorun &
[1] 9811
ceddrwyn@Destiny-VirtualBox:~/tbamud/tbamud-3.62$ 


What do you think I missed?

Also this message:


ceddrwyn@Destiny-VirtualBox:~/tbamud/tbamud-3.62$ ^C
[1]+  Done                    sh ./autorun
ceddrwyn@Destiny-VirtualBox:~/tbamud/tbamud-3.62$ 

but I didn't press Ctrl+C to get the message that time.

---

### Post by jtarin on 2011-06-09
I just noticed your hostname....ceddrwyn@Destiny-VirtualBox
Is this on a VirtualBox installation?

---

### Post by Ceddrwyn on 2011-06-09
I tried it yet again and got this...

ceddrwyn@Destiny-VirtualBox:~/tbamud/tbamud-3.62$ sh ./autorun &
[2] 12495
ceddrwyn@Destiny-VirtualBox:~/tbamud/tbamud-3.62$ ./autorun &
[3] 12670
[2]   Done                    sh ./autorun
ceddrwyn@Destiny-VirtualBox:~/tbamud/tbamud-3.62$

---

### Post by jtarin on 2011-06-09
> ceddrwyn@Destiny-VirtualBox:~/tbamud/tbamud-3.62$ sh ./autorun &
[1] 9811
ceddrwyn@Destiny-VirtualBox:~/tbamud/tbamud-3.62$ That means your server is running and if you look you'll have a syslog in that folder.....knucklhead!!!:popcorn:
Now your on your own...:p Have fun and mark this thread as solved.

---

### Post by Ceddrwyn on 2011-06-09
> **jtarin said:**
> I just noticed your hostname....ceddrwyn@Destiny-VirtualBox
Is this on a VirtualBox installation?

yes

---

### Post by jtarin on 2011-06-09
> **Ceddrwyn said:**
> I tried it yet again and got this...

ceddrwyn@Destiny-VirtualBox:~/tbamud/tbamud-3.62$ sh ./autorun &
[2] 12495
ceddrwyn@Destiny-VirtualBox:~/tbamud/tbamud-3.62$ ./autorun &
[3] 12670
[2]   Done                    sh ./autorun
ceddrwyn@Destiny-VirtualBox:~/tbamud/tbamud-3.62$That is your server starting and running in the background...open syslog from that folder and look at the times.(use gedit)
You should only have to do ./autorun & ......but either is fine...whatever works.

---

### Post by Ceddrwyn on 2011-06-09
> **jtarin said:**
> That means your server is running and if you look you'll have a syslog in that folder.....knucklhead!!!:popcorn:
Now your on your own...:p Have fun and mark this thread as solved.

Okay, stupid question time, what does that mean?
I'm not getting the message "No connections.  Going to sleep."

I checked syslog.crash and this is what it says...

autorun starting game Thu Jun  9 01:01:46 EDT 2011
running bin/circle -q 4000
nohup: ignoring input
No etc/config file, using defaults: No such file or directory
Jun  9 01:01:46 :: Loading configuration.
Jun  9 01:01:46 :: tbaMUD 3.62
Jun  9 01:01:46 :: Using lib as data directory.
Jun  9 01:01:46 :: Running game on port 4000.
Jun  9 01:01:46 :: Finding player limit.
Jun  9 01:01:46 ::    Setting player limit to 300 using rlimit.
Jun  9 01:01:46 :: Opening mother connection.
Jun  9 01:01:46 :: Binding to all IP interfaces on this host.
SYSERR: bind: Address already in use
Quick boot mode -- rent check supressed.
Using file descriptor for logging.
autoscript terminated Thu Jun  9 01:01:47 EDT 2011

---

### Post by jtarin on 2011-06-09
You'll need to mark this thread solved and start another one on running your application. I would check the FAQ for the application whichI gave you a link earlier and their forums.....seem active. I don't play this but looking at your run it wants to be configured.> Jun 9 01:01:46 :: Binding to all IP interfaces on this host.
SYSERR: bind: Address already in useNeeds another address.

---

### Post by Ceddrwyn on 2011-06-09
It worked, it worked, it worked.

Hehehe

---

### Post by jtarin on 2011-06-09
Great! Later Ceddrwyn! :)

---

