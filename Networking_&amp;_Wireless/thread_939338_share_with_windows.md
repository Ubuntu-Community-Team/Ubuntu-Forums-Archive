---
title: "share with windows"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by lilmill on 2008-10-05
I cannot see my windows shares from the ubuntu box. I have shared a hard drive with write access and wish to access the shared computer from my ubuntu box. When connecting it shows a widows shares folder but there is nothing there. I have no problem going the other way From vista64 to ubuntu i can see all the shared folders on the ubuntu box

---

### Post by samster on 2008-10-05
ditto

:(

---

### Post by ajmorris on 2008-10-05
> **lilmill said:**
> I cannot see my windows shares from the ubuntu box. I have shared a hard drive with write access and wish to access the shared computer from my ubuntu box. When connecting it shows a widows shares folder but there is nothing there. I have no problem going the other way From vista64 to ubuntu i can see all the shared folders on the ubuntu box


hi there,
there are still issues with samba and vista, and only the more recent versions of samba support connecting at all.
Can you please open up a terminal, and run the following command:
```
smbclient \\\\<ip of windows box>\\<windows share name> -U <username>
```

and post any errors you receive.

AJ

---

### Post by didiercool on 2008-10-07
Well, I'm having the same problem.  Here are the errors I get when I run that command:
> Error connecting to <windows box ip> (Connection Refused)
Connection to <windows box ip> failed (Error NT_STATUS_HOST_CONNECTION_REFUSED)
Any ideas?

---

### Post by superprash2003 on 2008-10-07
firstly ensure both the ubuntu and the windows machine can ping each other..ensure that no firewall is coming in the way.. create exceptions.. to access windows files, go to places->computer and under "go to" type smb://x.x.x.x where x.x.x.x is  the ip of the windows machine.

---

