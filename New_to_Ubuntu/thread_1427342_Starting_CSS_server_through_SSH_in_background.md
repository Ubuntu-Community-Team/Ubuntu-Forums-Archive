---
title: "Starting CSS server through SSH in background"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by Goldline on 2010-03-11
Hey,
 
Im trying to start a CSS server through SSH.
Its working with the command below:
 
./srcds_run -console -game cstrike +map de_dust2_unlimited -maxplayers 16 -autoupdate
 
However when i close Putty the gameserver shuts down too
im guessing thats its because the window closes aswell.
How can i run the program in the background in a seperate window in such 
a way that it does not shutdown itself if im exiting Putty.

---

### Post by undecim on 2010-03-11
put nohup at the beginning of the command:
```
nohup ./srcds_run -console -game cstrike +map de_dust2_unlimited -maxplayers 16 -autoupdate
```

---

