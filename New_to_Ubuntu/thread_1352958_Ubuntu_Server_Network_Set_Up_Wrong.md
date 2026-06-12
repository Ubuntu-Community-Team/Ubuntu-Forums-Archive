---
title: "Ubuntu Server Network Set Up Wrong"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by nitrusoxide on 2009-12-12
I have an old desktop that I installed Ubuntu server on, but I don't have a monitor or keyboard for it.  I went to a friends and borrowed his while installing.  The install went fine, and afterwards, I set the IP address to static in the /etc/network/interfaces file.

The problem is, I set it up with the wrong network address.  Is there anyway for me to get into the server from my MacBook without bringing it back to my friend's and using his monitor?  I set up the server with OpenSSH and Samba, if that means anything.

Also, if the only option is to go back to the monitor, should I leave the IP settings as DCHP or should I put in the correct static IP addresses?

Thanks!

---

### Post by nitrusoxide on 2009-12-13
Sorry, one more question.  Is it better to just switch the interface file back to DCHP, then assign a static IP address through the router?  I'm new to Linux, so I don't really know what the best way to do this is.

---

### Post by Iowan on 2009-12-13
Servers generally work better with static address (primarily so they're not a moving target). I have a server and a network printer set up to get a "static lease". I like the idea of centralized IP address management, but others think it just over complicates things - your call...
If you know the "wrong" IP address, you *should* be able to log in via SSH and change it.

---

### Post by Locke_99GS on 2009-12-13
With ssh set up on the server, you can simply ssh into it from another machine. You have to know the ip address (or named pipe) of the server.

Use *ssh username@ipaddress_of_server*, like this: (example)

```
ssh locke@192.168.2.21
```

If your username is the same on the server as it is on the host, you don't need to add the username to the ssh statement.

---

### Post by jvc26 on 2009-12-13
Basically open up an x11 terminal - assuming you have it installed on your mac, then ssh to the server - syntax:

```
ssh <user>@<host ip>
```

Enter your username and password, and once logged in:

Edit the /etc/network/interfaces file, and put the new static address in. Then either ```
/etc/init.d/networking restart
``` or reboot the server.

Il

---

### Post by nitrusoxide on 2009-12-13
Thanks for the information.  I'm going to set it up so that it is DHCP, then SSH into it later and set the IP address to static.

Thanks again!

---

### Post by Iowan on 2009-12-13
Unless you have a static lease set up in the router, you may need to go hunting for its DHCP address. Just my opinion, but if you're gonna go static address (via */etc/network/interfaces*) later, you may as well save an extra trip and change it the first time. 
But...
 practice is a good thing, too!

---

