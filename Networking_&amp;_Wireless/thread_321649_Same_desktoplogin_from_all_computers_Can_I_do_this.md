---
title: "Same desktop/login from all computers? Can I do this?"
date: 2006-12-19
forum: Networking &amp; Wireless
---

### Post by jondecker76 on 2006-12-19
Hello

After trying out Ubuntu I am convinced that all of my windows machines must go...
However, before installing everything, I want to know if I can set up a kind of "corporate environment" for our network in which:

A) Ubuntu runs locally on each machine, but the file system is served to the desktops. I.e. If my logon is "jon", then I can go to any computer in my house and login with "jon" with my password and get the exact same desktop with the exact same settings. 
B) If I install software while using computer A, then log out and go to computer B, the software is there as well

Basically I want all of us in my house to be able to log onto our account from any computer in the house with all settings, software etc preserved. 

I would imagine that I have to mount parts of the file system onto a NAS server or possibly another computer running Ubuntu SE, but I'm not sure which directories and/or how to do it.

Is this possible? Can anyone give me any help?

thanks,
Jon

---

### Post by jondecker76 on 2006-12-20
bump

---

### Post by jondecker76 on 2006-12-20
OK, I think i found out how to do this - please read:

[https://help.ubuntu.com/6.10/ubuntu/serverguide/C/network-file-system.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/network-file-system.html)

it mentions mounting /home and /ubuntu on a NFS and mounting the directories on each client.. 

I think i got this, but can anyone with knowledge give me a little bit better of a breakdown?

thanks,

Jon

---

