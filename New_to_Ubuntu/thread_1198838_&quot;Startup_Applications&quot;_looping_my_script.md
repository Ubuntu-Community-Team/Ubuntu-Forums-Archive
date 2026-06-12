---
title: "&quot;Startup Applications&quot; looping my script"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by haunter on 2009-06-28
Hi! sooo.. I had a look around the web but didn't find any solution; hoping someone here can help me :)

I have gotten tightvnc server running on my newly installed ubuntu 9.04 desktop x64, and I'm trying to get it to autostart the vnc server on login (ive got autologin on). After looking at some sites i ended up with creating a script that looks as follows:

```
#!/bin/bash

sleep 5
vncserver
```

I also added an entry in the Sys->Prefs->Startup Applications utility that runs the script.

What happens is that when i start the system and logon everything looks fine, but after a short while the disk activity goes through the roof and the machine becomes unresponsive.
i found out that ubuntu somehow loops my script, because the vncserver log folder gets crowded real fast.

I've tried changing the script to say 'exec vncserver' instead of just 'vncserver' = same issue, adding 'exit 0' at the end of the script = same issue, running vncserver by adding it to /etc/rc.local = it wouldn't start, running the script from rc.local = wouldn't start. 

I'm kinda lost here atm so if anyone have some pointers I'd be very thankful.



i should also note that when adding an entry to "Startup Applications" for e.g. 'gedit' it behaves correctly and doesnt loop. 


~andre

---

### Post by RealPSL on 2009-07-03
If you installed using Synaptic or Apt then you should have a startup script for VNC server. In which case you should just enable it to start with System > Administration > Services

---

