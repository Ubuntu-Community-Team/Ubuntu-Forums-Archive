---
title: "got xp share with ubuntu"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by m3t3ors on 2010-08-25
ive just set up network share with windows xp and ubuntu and all works well but ive lost internet on ubuntu
having followed problem 3 on this post 
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)
my net work share works but internet doesnt?

---

### Post by Isaacgallegos on 2010-08-25
Will ubuntu connect if it's connected directly to the modem or if it's the only one on the router?

---

### Post by m3t3ors on 2010-08-25
wont connect at all, but will check when i get home from work, ( on nights)

---

### Post by m3t3ors on 2010-08-26
just tried with ubuntu machine direct into the modem and still no internet.

---

### Post by m3t3ors on 2010-08-26
just checked my internet connections and it states my wireless connection is active but my wired connection isnt?
my wireless connections states connected but still no internet?

how can i enable wired connection?

---

### Post by m3t3ors on 2010-08-26
right got ethernet running on ubuntu machine, but can only see and enter my network computers.
cant access the internet at all, but can on windows machines

---

### Post by Morbius1 on 2010-08-26
> ive just set up network share with windows xp and ubuntu and all works well but ive lost internet on ubuntu
[COLOR=Blue]having followed problem 3 on this post [/COLOR]
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)
my net work share works but internet doesnt?     For the benefit of others, Problem 3 requires the use of winbind:
> Open /etc/nsswitch.conf for editing with the following command:
```
      gksudo gedit /etc/nsswitch.conf 
```Find the line that looks something like:
```
    hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4 
```For this line, [order IS important]("http://ubuntuforums.org/showpost.php?p=7255859&postcount=15"). You’ll need to add the “wins” option before dns, so the line reads like this:
```
    hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4 
```Now, save the file by clicking on "File" > "save" and close gedit.

You'll also have to install the winbind daemon in order to resolve hostnames. This is easily done with the following command:
```
      sudo apt-get install winbind
```Member capscrew can better articulate how nsswitch is now looking for a WINS server that isn't there: [http://ubuntuforums.org/showthread.php?t=1496488](http://ubuntuforums.org/showthread.php?t=1496488)

Perhaps that is the source of your dilemma.

---

### Post by m3t3ors on 2010-08-27
solved
thanks to those who helped

got wireless internet and network

problem was in the line 

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

dns was missing
once i added dns everything works

---

