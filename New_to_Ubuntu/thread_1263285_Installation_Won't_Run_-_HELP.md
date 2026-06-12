---
title: "Installation Won't Run - HELP"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by mcp1 on 2009-09-10
Ok, let me preface this by saying that I am a TOTAL novice here.
 
I just tried to install 9.04 on an 800mhz IBM Netvista. I got it all to install, but when I restarted the computer it went through the login prompts (user, password), showed the basis disclaimers and then ended with a prompt that looks like this...
 
pamatt@MCP1:~$
 
What in the world am I supposed to do here?
 
Does this mean the system didn't fully install? If not, how can I get to the CD ROM to execute the rescue functions?
 
Thanks...

---

### Post by wojox on 2009-09-10
Try:

```
sudo /etc/init.d/gdm start
```

---

### Post by mcp1 on 2009-09-10
[SIZE=2]it says   sudo: /etc/init.d/gdm: command not found[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]Did something not install?[/SIZE]

---

### Post by mbrush on 2009-09-10
Try installing 'gdm'

sudo apt-get install gdm

Which version of the install CD are you using?  If it's the Server version, it doesn't have any GUI/Desktop Environment by default.

Good luck

---

### Post by Sealbhach on 2009-09-10
Sounds like you might have installed the server version, which doesn't come with a desktop.

.

---

### Post by mcp1 on 2009-09-10
Crap - you're probably right.  Ok, what do I do to delete this system and install the desktop version (once I download that)? 
 
Specifically, how do I get it to boot from the CD now (since I don't get the option at startup)?
 
Thanks - I can't beleive I did this...

---

### Post by Sealbhach on 2009-09-10
You could just install the desktop from the command like:

```
sudo apt-get install ubuntu-desktop
```

Run that command and you will have a working desktop in a few minutes. 

.

---

### Post by mcp1 on 2009-09-10
[SIZE=3]Ok, it ran for a while, but now says...[/SIZE]
[SIZE=3][/SIZE] 
[SIZE=2]Errors were encounterd while processing:[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]/cdrom/pool/main/c/compiz-fusion-lugins-extra/compiz-fusion-plugins-extra_0.8.2-oubuntu1_i386.deb[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]E: sub-process /usr/bin/dpkg returned error code (1) [/SIZE]
[SIZE=2][/SIZE] 
[SIZE=3]Anything I can do from here?[/SIZE]

---

### Post by mbrush on 2009-09-10
Do you still have the CD in the CDROM drive?

If you don't, put it back in or remove the line from '/etc/apt/sources.list' for the CD, near the top of the file.

Then run, sudo apt-get update

---

### Post by mcp1 on 2009-09-10
OK, I did that and it worked and I'm back to the prompt...
 
[EMAIL="pamatt@MCP1:~$"]pamatt@MCP1:~$[/EMAIL]

 
What do I do from here?  (Sorry - I said I was a total newbie...)

---

### Post by Sealbhach on 2009-09-10
Ok, try to install the desktop again:

sudo apt-get install ubuntu-desktop
Then, reboot. Normally you wouldn't have to do stuff like this.

.

---

### Post by mcp1 on 2009-09-10
No luck, now I get the gui log in screens, but it then goes back to the server prompt. 
 
Thanks so much Sealbhach Wojox and mbrush for  all your help, but I'm hanging it up. 
 
last Q:  How can I overwrite this system once I can download the right  (desktop) version tomorrow?  There is no prompt to boot from the CD rom...

---

### Post by mbrush on 2009-09-10
Just run through the Desktop CD installer, it will give options to automatically erase and repartition the existing installation.

---

### Post by SoftwareExplorer on 2009-09-10
> **mcp1 said:**
> 
last Q:  How can I overwrite this system once I can download the right  (desktop) version tomorrow?  There is no prompt to boot from the CD rom...
You would boot the desktop install CD the same way you did the server cd. Sometimes the computer is set to try booting the CD first and then the hard disk. Other you have to press something like DELETE when you first turn them on to be able to tell it to boot from CD. And as far as overwriting the server install,  you would just selet manual partitioning when it asks and then tell it to format and use the server partition as /

---

