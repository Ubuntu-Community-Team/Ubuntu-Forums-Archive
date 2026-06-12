---
title: "how to open a port"
date: 2007-07-07
forum: Networking &amp; Wireless
---

### Post by Scroopy on 2007-07-07
I want to open port 22. 

Please don't ask me why I want to open it.  Please don't tell me that it should already be open.  Please don't ask me to check if it is already open.  Please just tell me how to open it. 

Thanks in advance.

---

### Post by spd106 on 2007-07-07
```
sudo aptitude install openssh-server
```

---

### Post by regomodo on 2007-07-07
portforward.com for your router

firestarter for your firewall.

Also,try to sound less obnoxious and people may be want to help more

---

### Post by 3rdalbum on 2007-07-07
It is open, unless you have manually closed it using Firestarter or something similar. Is that what you've done?

Otherwise, your ADSL router may have a firewall built-in. You will need to tell it to route Port 22 packets to your computer. This varies by router - consult your router's manual or documentation for information.

---

### Post by Scroopy on 2007-07-07
Spd16, thank you very much.  I typed this command and it worked.  I am now able to ssh from my suse box to my ubuntu box. 

Regomodo; I shall try and sound a little less obnoxious; but that’s nothing compared to the cryptic obnoxious sarcasm that I so often get from people in these forums.

---

### Post by Mr. C. on 2007-07-07
Scroopy,

For future posts, you will receive better help if you clarify your *goal*, not ask how to perform a task.  Often users misunderstand something, and ask about how to perform some random, inappropriate task.  In your case, you indicate you want to "open port 22", but that task is ambiguous within the context of your unstated goal.

MrC

---

### Post by Bhargavi on 2007-07-17
i want to have a LAN connection to my machine to 4 machines.
Once it got connected to 1 machine via SSH. Now it is not at all getting connected. i installed SSH successfully. In the System- Adminstration- Shared folders i have SSH but while trying to connect to the other machines if i do port scan of that machine it tries and and no port is open. But it doesn't give any errors. It goes on trying to open. Please somebody help me getting connected to my other machines. It will be a great help.

Thanx

---

### Post by Mr. C. on 2007-07-17
On the SSH server machine, run the command below and show the output:

```
netstat -tln | grep :21 
```

Can you ssh from the server machine itself ?
```

ssh localhost
```

MrC

---

