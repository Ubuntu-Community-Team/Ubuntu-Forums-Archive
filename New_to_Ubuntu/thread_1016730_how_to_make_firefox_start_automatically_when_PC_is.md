---
title: "how to make firefox start automatically when PC is turned on?"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by candtalan on 2008-12-20
What do I do to ensure that firefox starts automatically when the machine is turned on, or soon after the PC starts up please?
tia

---

### Post by binbash on 2008-12-20
System > Preferences > Sessions

add firefox command to there.

---

### Post by lovelyvik293 on 2008-12-20
click - system > preferences > sessions
click the startup programs tab
then click add to add the command to start the program

---

### Post by dwasifar on 2008-12-20
Those two suggestions will work, or you can try it this way:

1) In the System menu, choose Preferences, and choose Sessions
2) In the Application menu, find Firefox.  Click on it and hold, drag it to the Sessions window, and release.

Doing it this way populates the title and comment fields of the new Sessions entry automatically.

---

### Post by candtalan on 2008-12-22
I have a problem: Firefox is starting when the PC starts, yes, however, it frequently comes up too early, before the network is settled or established, and so the (very elderly) user is often faced with a browser error message(!)

Is there any way I can contrive to have a delay in this command?

the command at present is simply
/usr/bin/firefox-3.0
(to start up)

tia

---

### Post by bryncoles on 2008-12-22
no idea if this will work, but what happens if you change the command from 

```
/usr/bin/firefox-3.0
```

to

```
sleep 10 && /usr/bin/firefox-3.0
```

if im right, that should delay firefox's start by ten seconds. if im wrong then i dont know what im talking about and please ignore me!

---

### Post by candtalan on 2008-12-22
thanks I will certainly give it a try!

---

### Post by candtalan on 2008-12-26
> **bryncoles said:**
> no idea if this will work, but what happens if you change the command .....
to
```
sleep 10 && /usr/bin/firefox-3.0
```
if im right, that should delay firefox's start by ten seconds. if im wrong then i dont know what im talking about and please ignore me!

Worry not! It fact, it did not work, however your suggestion was most useful to enable me to re think along a similar direction - thanks!

I realised I could create a simple file (a script file) and after giving it execute permissions, I could use *it* to run firefox after a delay at startup.

for the record:
1) created a file using text editor, saved it as filename 
firefox-startup.sh
in a new directory in my home directory
/home/user1/bin/firefox-startup.sh
2) put contents into the file as follows:

```

#!/bin/bash
# filename is firefox-startup.sh

# delay is 25 seconds
sleep 25

# for ubuntu 8.04 has firefox-3.0
/usr/bin/firefox-3.0

# for ubuntu 7.10 has firefox
#/usr/bin/firefox 
```

after that, I could use 
system > preferences > sessions
 and click the startup programs tab
and browse to my file at
/home/user1/bin/firefox-startup.sh

Thanks!

---

### Post by adobrakic on 2008-12-26
I think putting firefox at the end of the list would have made it open later instead of sooner. By making it the name 'zfirefox' or something like that to make it go to the end.

---

