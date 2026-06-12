---
title: "ssh tunnel puzzling problem??"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by ajclarkson on 2008-02-18
Ok guys, I am working on a java project which needs to connect to my university mysql server, here is the situation

for remote access i can get ssh to vega - this is the only external connection allowed

once in, mysql access comes from the server smart

so basically i need to tunnel requests to localhost:3306 through vega to smart:3306

 i have tried a couple of different guesses at how to do this, but i cant get it to work


please help this is for an assignment and really really need it to work!!! 

thanks

---

### Post by Rogers on 2008-02-18
**ssh -L 127.0.0.1:3306:TARGETHOST:3306  SSHHOST**

SSHHOST may also be the target host. Good luck on your homework.... Next time you have basic command questions take a peek at "man ssh" or "man command_in_question".  UNIX man pages are so good it's almost cheating. :-)

---

### Post by The Cog on 2008-02-18
Just to amplify that a bit:
```
ssh -L 127.0.0.1:3306:smart:3306 username@vega
```
replace smart, vega and username with real addresses and name.
Then configure your program to connect to 127.0.0.1 as the MySQL server.

---

