---
title: "Ethernet connection drops out after a while"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by dhallgt on 2011-06-21
Pretty new to ubuntu.  I have a minecraft server running and after it has been running for so many hours it ethernet connection drops out.  The only way I know of to re-enable it is for a reboot.  connect automatically is checked and only seems to make an effect on boot.  Is there a way to stop it from closing out the connection?  is there a script I can install somewhere that refreshes it every so often.  I kinda was hoping to let this thing run for weeks at a time without having to mess with it but it seems to drop out every 10 or so hours.

---

### Post by hobbit1983 on 2011-06-21
I think you could use ifup and ifdown to easily create a script that would test if the ethernet  connection is down and if so restart it.  That script could then be run as a cron job every x minutes.  

Sorry I don't know the exact commands or can give you the script but I think that should be a nudge in the right direction

---

