---
title: "sh script on startup"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by DarkRookie on 2009-02-05
I am trying to run a .sh script on start up. I go into Sessions and add it, but it doesn't run on start up.
Also, Is there a way to disable the splash screen on boot. It make the monitor I have go crazy when it does it.

---

### Post by binbash on 2009-02-05
you can disable the splash screen with startup manager easily.Did you try adding the command to /etc/rc.local ? (add it above the exit)

---

### Post by Voland on 2009-02-05
[HOWTO disable splash screen]("http://ubuntuforums.org/showthread.php?t=542082")
Try to make your script executable: chmod +x *scriptname.sh* or add *sh* before scriptname in Sessions.

---

### Post by DarkRookie on 2009-02-05
[stupid question posted here]

---

