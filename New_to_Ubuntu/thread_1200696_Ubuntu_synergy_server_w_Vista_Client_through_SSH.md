---
title: "Ubuntu synergy server w/ Vista Client through SSH"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by K_REY_C on 2009-06-30
I'm trying to set up synergy to run through SSH. Windows Vista client, Ubuntu (actually gOs) server. 

Currently I've got synergy working without SSH.

I've also got openSSH as a server on Ubuntu working fine (as it is accessible through FileZilla on Vista).

I've found a terminal command for doing this from linux to linux 

"Install the OpenSSH client on each synergy client computer. Then, on each client, start the OpenSSH client using port forwarding: ssh -f -N -L localhost:24800:server-hostname:24800 server-hostname" here: [http://synergy2.sourceforge.net/security.html](http://synergy2.sourceforge.net/security.html)

But how do I do this in Windows Vista?

Thanks very much.

---

### Post by tad1073 on 2009-06-30
You may want to try putty.
[http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

---

### Post by K_REY_C on 2009-06-30
Thanks very much. I've installed PuTTY on vista... and I've been able to log into the other machine via PuTTY (it looks like the terminal). 

How do I go about redirecting synergy to connect through openSSH from Vista?

This is literally my 1st day attempting anything involving the word server or SSH.

Thanks again.

---

### Post by K_REY_C on 2009-06-30
Found the answer here: [http://tech.jonathangardner.net/wiki/Synergy_%2B_Putty_on_Windows](http://tech.jonathangardner.net/wiki/Synergy_%2B_Putty_on_Windows)

Thanks all!

---

