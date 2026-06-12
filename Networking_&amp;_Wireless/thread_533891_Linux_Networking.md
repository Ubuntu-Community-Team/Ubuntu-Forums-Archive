---
title: "Linux Networking"
date: 2007-08-24
forum: Networking &amp; Wireless
---

### Post by l33t fl33t on 2007-08-24
Short and sweet:

How do I connect two Feisties over a switch for file exchange?

---

### Post by sricketts on 2007-08-24
Forgive me if I misunderstood your question. I am assuming you have machine A with eth0 plugged into the switch and machine B with eth0 plugged into the switch.
[LIST=1]
[*] Use **ifconfig eth0** on each machine to find the IP address (inet addr).
[*] Use **ping** from one machine to the other to verify the connection.
[*] Use scp/ftp, etc to transfer files. 
[/LIST]
Is that what you want to do? If so, I can provide details.

---

### Post by l33t fl33t on 2007-08-25
Yes, that's exactly what I want to do.

The last step is the tricky one for me so any suggestions are welcome.

---

### Post by Jose Catre-Vandis on 2007-08-25
You have several choices:

scp
ftp
ssh
samba
nfs

Loads of howto's on the forum, so do some searching :)

---

### Post by l33t fl33t on 2007-08-25
Can anyone point me to a simple, step by step explanation since I'm still rather new at this?

EDIT: Nevermind, found a solution. 

[http://ubuntuforums.org/showthread.php?t=218630](http://ubuntuforums.org/showthread.php?t=218630)

---

