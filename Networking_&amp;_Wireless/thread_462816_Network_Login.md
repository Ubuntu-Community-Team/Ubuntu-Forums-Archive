---
title: "Network Login"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by russell.h on 2007-06-03
Is there a way to set up an Ubuntu server that stores user logins and their files, then set up workstations that can log in to the server the way schools and businesses do with Windows and Mac (and presumably Linux, although I've never seen it with my own eyes)?

I think I phrased that badly, but hopefully someone will know what I'm talking about. I want to be able to log in to my user account from any PC connected to my network, and always have it be the same account.

Thanks,

Russell

---

### Post by netztier on 2007-06-03
> **russell.h said:**
> Is there a way to set up an Ubuntu server that stores user logins and their files, then set up workstations that can log in to the server the way schools and businesses do with Windows and Mac (and presumably Linux, although I've never seen it with my own eyes)?

I think I phrased that badly, but hopefully someone will know what I'm talking about. I want to be able to log in to my user account from any PC connected to my network, and always have it be the same account.

Thanks,

Russell

This thread is looking into the same direction: [Linux Fat Clients?]("http://ubuntuforums.org/showthread.php?t=435863")

best regards

Marc

---

### Post by russell.h on 2007-06-03
Yes, that seems to be about what I'm interested in.

I have at various points messed tried logging in to remote machines via XDMCP, what would be the advantages/disadvantages of that approach? If I were doing that would the program actually be "running" on the server, and all that is being done locally is display stuff? (In my case my "server" has 256mb of RAM, and an unimpressive processor, so that might not be such a good plan...)

Thanks,

Russell

---

### Post by netztier on 2007-06-03
> **russell.h said:**
> Yes, that seems to be about what I'm interested in.

I have at various points messed tried logging in to remote machines via XDMCP, what would be the advantages/disadvantages of that approach? If I were doing that would the program actually be "running" on the server, and all that is being done locally is display stuff? (In my case my "server" has 256mb of RAM, and an unimpressive processor, so that might not be such a good plan...)


Using XDMCP brings load to the server, and a lot at that - all programs need CPU and disk I/O as if the user was sitting at the machine's local screen and keyboard: your assumption is correct. The Edubuntu Project is doing something similar, as well as most "terminal server" project that relies on a "thin client" (Citrix and the likes...)

Using your server with "fat clients" however might work; DNS, LDAP, Kerberos, are lightweight enough for that machine to start with, maybe NFS even included. When your environment grows, it should feasible to distribute these service to different machines without too much hassle.

best regards

Marc

---

### Post by corbouk on 2007-06-05
Are you talking about roaming profiles?  So you log on to any PC on the network and your desktop icons, my documents and program shortcuts etc?

---

### Post by netztier on 2007-06-05
> **corbouk said:**
> Are you talking about roaming profiles?  So you log on to any PC on the network and your desktop icons, my documents and program shortcuts etc?

I think that's what the OP's intention is.

Since the things you mention such as Desktop settings and files etc. are all in each user's home directory or (hidden) subfolders thereof, a "roaming profile" feature is implicitely given if you have NFS-mounted home directories. Most programs create their own hidden subdirectory to store the individual user's settings there.

So if you have a central repository for home directories on  an NFS server and your home directory gets mounted every time you log on to a machine, the "profile" roams with you.

best regards

Marc

---

