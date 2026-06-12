---
title: "I need help"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by reaply on 2011-08-15
Hey there ubuntu community, I am having problems with teamspeak 3 :p. I downloaded the file from the teamspeak 3 website for linux and I extracted the file and I see two .sh files (ts3server_starscript.sh and ts3server_minimal_startscript.sh)
But when I do, nothing happens! Can I have some help?

---

### Post by GWBouge on 2011-08-15
It needs an argument, and it also prints out an admin key that you'll need.  Run it in the terminal.

```
$ ./ts3server_startscript.sh start
```

---

### Post by reaply on 2011-08-15
Err, I haven't used ubuntu in a long time, in all honesty. How do I go to folders in terminal? :(

---

### Post by Ac30nfir3 on 2011-08-15
By "going to folders" I assume you mean browsing through the file system and opening folders.

To view what files/folders are in the current directory use the command: ```
$ ls
```

To open a folder use the command: ```
$ cd FOLDERNAME
``` where FOLDERNAME is replaced with the name of the folder you want to open and browse.

Hope this helps. Cheers.

---

### Post by reaply on 2011-08-15
Sorry I ment to how to get to directorys in terminal. But I remembered it was something like cd /home/(username)/ right?

---

### Post by Ac30nfir3 on 2011-08-15
Yes. You can use cd to get to any directory. you can also use ```
$ cd ..
``` to go up to the parent directory of the current directory.

---

### Post by GWBouge on 2011-08-15
You can also get something for Nautilus that will allow you to Right-Click on a folder -> Open in Terminal, to open the terminal in a desired directory.  Look in Synaptic for nautilus-open-terminal or something like that (at least I think that's where I got it from).

---

### Post by reaply on 2011-08-15
Thanks, but I am having trouble accessing the folder. I have the folder on the desktop and I have it set to cd /home/reaply/Desktop/. So it's on the desktop, but I can't get it to open the folder for the teamspeak folder.

---

### Post by Ac30nfir3 on 2011-08-15
Oh right, I've been using Ubuntu Server Edition for so long, I sort of forgot that Ubuntu has a GUI... :)

EDIT: try using ```
$ cd teamspeak
```

---

### Post by reaply on 2011-08-15
Oh I got it, I was putting it with /teamspeak/ and not just teamspeak. :p

---

### Post by Ac30nfir3 on 2011-08-15
Good to hear.

Cheers mate.

---

### Post by reaply on 2011-08-15
> Starting the TeamSpeak 3 server
TeamSpeak 3 server started, for details please view the log file
reaply@reaply-VirtualBox:~/Desktop/teamserver$ ./ts3server_linux_amd64: 1: ELF: not found
./ts3server_linux_amd64: 2: Syntax error: ")" unexpected



What does this mean? O_o

---

### Post by GWBouge on 2011-08-16
Means ... you might need to start a new thread, lol.  Seems to be a pretty rare bug for TS3 on Natty x64, so not sure if it's it's a dependency thing, or if there's even a fix other than trying to find an older version, or maybe using the 'minimal' script.

[http://forum.teamspeak.com/showthread.php/64876-RC1-amd64-Server-Won-t-Start-on-Ubuntu-11.04-Desktop]("http://forum.teamspeak.com/showthread.php/64876-RC1-amd64-Server-Won-t-Start-on-Ubuntu-11.04-Desktop")

---

