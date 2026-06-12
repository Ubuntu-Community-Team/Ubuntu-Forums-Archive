---
title: "proplem in having updates"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by en_mohamed on 2010-03-30
[SIZE=4]hello dears
i hope you are fine
when the os ask tell me with new updates ,i  respond it to install updates but it tell me with an existed partial updates then it go to it then tell me an error occurred.
and today i wanted to make file to be shared ,it ask me to install some services i press ok but again showed me
an error  message "[COLOR=Red]E: Archive directory /var/cache/apt/archives/partial is missing.
E: Archive directory /var/cache/apt/archives/partial is missing.
E: Archive directory /var/cache/apt/archives/partial is missing.
E: Unable to lock the download directory"[COLOR=Black]
when i followed this link "[/COLOR][/COLOR][/SIZE][SIZE=4][COLOR=Red]E: Archive directory /var/cache/apt/archives[/COLOR][/SIZE][SIZE=4][COLOR=Red][COLOR=Black]" the browser showed me this screen (in attached file)
[/COLOR][/COLOR]

[/SIZE]

---

### Post by Nisal on 2010-03-30
whats the way u use ? terminal command ?

---

### Post by arochester on 2010-03-30
In a console, type:


> sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
sudp apt-get update

The first three commands will clean out the downloaded packages in /var/cache/apt/archives and /var/cache/apt/archives/partial and the last command updates the cache.

---

### Post by en_mohamed on 2010-03-30
> **[SIZE=3]arochester[/SIZE] said:**
> In a console, type:
The first three commands will clean out the downloaded packages in /var/cache/apt/archives and /var/cache/apt/archives/partial and the last command updates the cache.

thanks mr arochester,but i typed what you mentioned but the output is"[COLOR=DarkRed]E: Archive directory /var/cache/apt/archives/partial is missing[/COLOR].
"
i do not no what this message.

---

### Post by en_mohamed on 2010-03-30
does any body help me?

---

### Post by en_mohamed on 2010-03-30
thank god, i have searched on the internet and found the solution in this forum
[http://ubuntuforums.org/showthread.php?p=3847774](http://ubuntuforums.org/showthread.php?p=3847774)

---

