---
title: "Folder Permission"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by Tabu.it on 2011-02-28
Hi
is there a way to allow 3 non sudo users to read/write/delete files in a folder? I need it for a samba server where i store my downloaded files. Thank you

---

### Post by TechWiz2100 on 2011-02-28
```
chmod +rwt /path/to/folder
```

This will set the folder to read/write for everyone and the sticky bit so new users get access as well

---

### Post by Naggobot on 2011-02-28
Is it possible to run the command recursive?

---

### Post by TechWiz2100 on 2011-02-28
> **Naggobot said:**
> Is it possible to run the command recursive?

```
 chmod -R +rwt /path/to/folder 
```

---

### Post by Tabu.it on 2011-02-28
Thank you

> **Naggobot said:**
> Is it possible to run the command recursive?

chmod -R Mode File

[http://ss64.com/bash/chmod.html](http://ss64.com/bash/chmod.html)

---

### Post by Tabu.it on 2011-02-28
Is there a way to allow a user to remote login (ssh and samba) only from a bind ip + password?

---

### Post by TechWiz2100 on 2011-02-28
I think you can do that by setting domains on the usernames
e.g. 192.168.1.2/techwiz vs just techwiz

I'm not sure how well that works with SSHd but I've done something similar with NT network shares and SFTP

---

### Post by Tabu.it on 2011-02-28
Thank you

I googled and found for smb.conf this 

[http://www.faqs.org/docs/securing/chap29sec284.html](http://www.faqs.org/docs/securing/chap29sec284.html)

> 
hosts allow = 127.0.0.1 192.168.2.0/24 192.168.3.0/24
hosts deny = 0.0.0.0/0

The above will only allow SMB connections from 'localhost' (your own computer) and from the two private networks 192.168.2 and 192.168.3. All other connections will be refused connections as soon as the client sends its first packet. The refusal will be marked as a 'not listening on called name' error.

but i couldn't understand the /24 maybe is 192.168.2.0 to 192.168.2.24 ?

and for sshd.conf i found 

> AllowUsers [email]you@ip.add.re.ss[/email]

So for example i could do:
AllowUser [email]me@my.ip[/email] [email]userb@userb.ip[/email] [email]userc@userc.ip[/email] and so on?

---

### Post by TechWiz2100 on 2011-02-28
> **Tabu.it said:**
> 
but i couldn't understand the /24 maybe is 192.168.2.0 to 192.168.2.24 ?

[http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing#Prefix_aggregation](http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing#Prefix_aggregation)

Its a type of notation for an IP range; more specifically one that defines the host and the network prefix. The /24 is the same as network mask 255.255.255.0 so the IP range would be 192.168.2.0 to 192.168.2.254 (192.168.2.255 is probably reserved for Broadcasting)

---

### Post by Tabu.it on 2011-02-28
> **TechWiz2100 said:**
> [http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing#Prefix_aggregation](http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing#Prefix_aggregation)

Its a type of notation for an IP range; more specifically one that defines the host and the network prefix. The /24 is the same as network mask 255.255.255.0 so the IP range would be 192.168.2.0 to 192.168.2.254 (192.168.2.255 is probably reserved for Broadcasting)

Thank you and regarding 

> AllowUsers [email]you@ip.add.re.ss[/email]

So for example i could do:
AllowUser [email]me@my.ip[/email] [email]userb@userb.ip[/email] [email]userc@userc.ip[/email] and so on?

---

### Post by TechWiz2100 on 2011-02-28
> **Tabu.it said:**
> 
So for example i could do:
AllowUser [email]me@my.ip[/email] [email]userb@userb.ip[/email] [email]userc@userc.ip[/email] and so on?

For me at my home address it would be techwiz@192.168.1.1 and I would add that to sshd.conf as

AllowUsers techwiz@192.168.1.1, [email]anotheruser@foreign.domain[/email], remoteuser, networkuser@192.168.1.*

TechWiz can only access from 192.168.1.1, anotheruser can only access from the machine called foreign.domain, remoteuser can access from anywhere and networkuser can access from within the 192.168.1.0-255 network

As for passwords, I'm not sure and I think you actually want to add users to you're machine to assign passwords.

---

### Post by Tabu.it on 2011-02-28
Thank you it works :D

---

### Post by Tabu.it on 2011-03-18
Is possible to allow a user to browse only some directory?
For example i want userA(admin) to navigate all system and userB to navigate only its home folders and a directory under /media?

---

### Post by Tabu.it on 2011-03-19
*bump*

---

