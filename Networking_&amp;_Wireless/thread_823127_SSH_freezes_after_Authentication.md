---
title: "SSH freezes after Authentication"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by mt_burt on 2008-06-08
Hello everyone,

I'm having a problem logging into any remote computer using ssh from my Ubuntu laptop (Hardy 64-bit).  When I attempt to log in I am prompted for the password and after accepting it, ssh just hangs until I close the terminal window (ctrl-c doesn't work).  This happens whether connecting to a server behind my firewall or on the outside.  Also, I am able to connect to the servers using Putty on a windows computer both outside and behind my firewall. 

I'm not really sure where to start looking for the solution, I've run ssh with the -vvv option and there is a long output ending with: 

"debug2: channel 0: open confirm rwindow 0 rmax 32768"

I can post the entire output if it will be beneficial.

This problem just came up a few days ago. I've been able to connect without a problem up until then.

Thanks in advance,
-mt_burt

---

### Post by kevdog on 2008-06-08
Putty and Openssh keys are slightly different.  I take it you are using the ssh command line client to attempt to make the connection.  Are you sure you are using OpenSSH pub/private keys rather that putty keys?

---

### Post by mt_burt on 2008-06-08
You're right, I am using ssh from the command line.

I'm not sure how I would use a different set of keys in ssh but I'm fairly sure I'm not mixing the them.  I am using a different computer when I connect using Putty vs when using ssh.  

I don't think I'm doing anything different from before when I was able to connect successfully.

---

### Post by mexpolk on 2008-06-26
Related to: [http://ubuntuforums.org/showthread.php?t=838873&highlight=ssh+hangs+authentication]("http://ubuntuforums.org/showthread.php?t=838873&highlight=ssh+hangs+authentication")

---

