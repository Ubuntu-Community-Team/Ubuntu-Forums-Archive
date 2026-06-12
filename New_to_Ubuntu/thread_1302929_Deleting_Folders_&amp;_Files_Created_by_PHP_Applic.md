---
title: "Deleting Folders &amp; Files Created by PHP Application"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by Roger Allott on 2009-10-27
Earlier today, I downloaded a clever little php freeware app called [Single File PHP Gallery]("http://sye.dk/sfpg/").

It's a jolly nice little cheat in that it creates an online gallery of one's photo directories without creating loads of separate html or php files, or any database, or a content management doo-dah. It creates and saves thumbnails of all my photos, which is nice.

So, I did a quick set-up, looked at a few of my photos via it, and then read the configuration settings bit to refine things.

So, I've made my config changes, and now I need to delete all the folders and files it created first time round so they can be refreshed.

The problem is though that I can't. The folders and files that the php page created are not owned by me, so ubuntu prevents me from deleting or modifying them in any way. They are owned by 'www-data', according to the Permissions tab in Properties.

So, my short question is - how can I delete these folders and files?

And the long question is, how can I change php such that any files or folders a php script on my machine creates are owned by me?

---

### Post by Marflus on 2009-10-27
Short answer - open a terminal and enter:
```
gksu nautilus
```
- this'll take you to your file manager in root mode, so you'll be able to navigate to the files and remove them no problems.

Can't help with the other one, sorry. If I get chance, I'll have a poke around myself sometime, because I could do with knowing that myself...

---

### Post by Roger Allott on 2009-10-27
> **Marflus said:**
> Short answer - open a terminal and enter:
```
gksu nautilus
```
- this'll take you to your file manager in root mode, so you'll be able to navigate to the files and remove them no problems.
Cheers. Could you explain what the difference is between gksu and sudo?

> **Marflus said:**
> 
Can't help with the other one, sorry. If I get chance, I'll have a poke around myself sometime, because I could do with knowing that myself...
My guess is that there are two possible ways of handling it.

The first is to look at the settings in php.ini or Apache (is it http.conf?) to see if you can force new folders and files created to have certain permissions.

The second option is for the php code being executed to have a function that ascertains what type of OS is on the server and adjust the create folder/file command with loose permissions.

---

### Post by mgmiller on 2009-10-27
> Cheers. Could you explain what the difference is between gksu and sudo?

sudo is used to grant root privileges to commands that run in non-graphical mode in the terminal.  You would use it for copy and delete commands and other things that just give response back in the terminal.

gksu is used to grant root privileges to graphical applications like nautilus or gedit.  Although you can run graphical apps with sudo, it is considered dangerous to do so because there is a possibility of corrupting something somewhere.  This complication is rare, but when it happens it's VERY BAD.

---

