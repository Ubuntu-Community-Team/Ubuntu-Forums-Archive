---
title: "problem with kopete"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by semuren on 2007-06-28
I have installed kopete before and it has worked fine, but after reinstalling ubuntu 7.04 kopete wont start after i have installed it.
when i try to start it in applications-Internett-kopete nothing happens.
when I write sudo kopete in the terminal kopete starts, but I cant make an account.

Does anyone have a solution for my problem? :)

---

### Post by dreadlord_chris on 2007-06-28
> **semuren said:**
> I have installed kopete before and it has worked fine, but after reinstalling ubuntu 7.04 kopete wont start after i have installed it.
when i try to start it in applications-Internett-kopete nothing happens.
when I write sudo kopete in the terminal kopete starts, but I cant make an account.

Does anyone have a solution for my problem? :)

what happens when you just type **kopete** in the terminal?

---

### Post by semuren on 2007-06-29
> what happens when you just type kopete in the terminal?

I get this message and nothing more happens.

trying to create local folder /home/svein/.kde/share: Permission denied
trying to create local folder /home/svein/.kde/share: Permission denied
trying to create local folder /home/svein/.kde/share: Permission denied
trying to create local folder /home/svein/.kde/share: Permission denied
trying to create local folder /home/svein/.kde/share: Permission denied
trying to create local folder /home/svein/.kde/share: Permission denied
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
trying to create local folder /home/svein/.kde/share: Permission denied
trying to create local folder /home/svein/.kde/share: Permission denied
trying to create local folder /home/svein/.kde/share: Permission denied
trying to create local folder /home/svein/.kde/socket-laptop: Permission denied
trying to create local folder /home/svein/.kde/socket-laptop: Permission denied
kdeinit: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/svein/.kde/socket-laptop/kdeinit__0'
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
trying to create local folder /home/svein/.kde/share: Permission denied
trying to create local folder /home/svein/.kde/share: Permission denied
kopete: ERROR: KUniqueApplication: Can't setup DCOP communication.

---

### Post by dreadlord_chris on 2007-06-29
looks like there are problems with you home folder permissions - this should fix you up:
```

sudo chmown -hR svein:svein /home/svein

```
that will reset owner/group to your account for everything in your home folder

---

### Post by semuren on 2007-06-29
> looks like there are problems with you home folder permissions - this should fix you up:
Code:

sudo chmown -hR svein:svein /home/svein


when i tried that i got this message:
sudo: chmown: command not found

---

### Post by GeeZor on 2007-06-29
try chown.. 
will definitly do the trick for ya

so ```
 sudo chown -hR svein:svein /home/svein 
``` will solve your problem and other you will definily have when permissions in your home folder aren't set correctly. 

Enjoy!

---

### Post by semuren on 2007-06-29
Than you. that worked :D

---

### Post by GeeZor on 2007-06-29
Glad i could be of any help..

---

### Post by dreadlord_chris on 2007-06-29
> **semuren said:**
> when i tried that i got this message:
sudo: chmown: command not found

ooops.... sorry, my typo....

---

### Post by GeeZor on 2007-06-29
so it turns out, the symbol IS the thing ;);)

---

