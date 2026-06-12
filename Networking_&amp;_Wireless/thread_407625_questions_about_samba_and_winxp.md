---
title: "questions about samba and winxp"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by bugler on 2007-04-12
Ok, here goes.

I have installed smbfs, smbclient, winbind, and can ping my winxp machine //COPLAND by name (thank you winbind).

I cannot browse or smbtree my workgroup for winxp.  
Question is this:
is the only way to setup a workgroup in linux is to setup samba?  If so, isn't samba a server and could potentially have a security issue?  Yes, I know you could lock it down (google). I installed samba at one time and setup workgroup= 'MYWORKGROUP'  and could smbtree.

Is there an easier way to setup linux to winxp workgroup network than with samba.

Any insight would be AWESOME.

thanks in advance for the help.

bugler

---

### Post by dmizer on 2007-04-12
you can set up your ubuntu box as a local doman name server.  but it requires static ip for your local network.

basically you simply end up with all the machine's on your network listed with their ip and host name in the /etc/hosts file.

more secure, and perhaps a titch easier to set up ... but not so friendly to end users.  it's fine for a network of desktop systems, but portables will require changes to their network configuration to connect to a dhcp network.

more detail and howto here: [http://ubuntuforums.org/showthread.php?t=391601](http://ubuntuforums.org/showthread.php?t=391601)

---

