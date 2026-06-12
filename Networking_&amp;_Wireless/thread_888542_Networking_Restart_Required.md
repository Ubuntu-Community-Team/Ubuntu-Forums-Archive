---
title: "Networking Restart Required"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by JJL79 on 2008-08-13
When i start my Ubuntu Server 8.04 i have to login and run "/etc/init.d/networking restart" i order for my wifi connection to start/get ip.

Is there anything i can do to make this happen automatically?

---

### Post by caljohnsmith on 2008-08-13
You could create a really small bash script to start your server that includes the networking restart:
```
#!/bin/bash
<start server command>
sleep 30
/etc/init.d/networking restart
```
You'll need to run the script as root, and the above is just to give you the idea; it is not meant to be an exact solution since I would need more info from you to make the script better for your situation.

---

### Post by JJL79 on 2008-08-13
> **caljohnsmith said:**
> You could create a really small bash script to start your server that includes the networking restart:
```
#!/bin/bash
<start server command>
sleep 30
/etc/init.d/networking restart
```
You'll need to run the script as root, and the above is just to give you the idea; it is not meant to be an exact solution since I would need more info from you to make the script better for your situation.

What info do you need because i am very new to linux and do not know what to do with the info you gave me :-)

---

### Post by caljohnsmith on 2008-08-13
How is it you start your Ubuntu server? I don't use the Ubuntu server software so I really don't know any particulars about it, and whether it is done automatically on login or not. I would need to know that before I could make a recommendation of how to automatically run that networking restart command. For instance, the Server might have its own bash script of services it starts, and you could just put the networking restart in there.

---

### Post by JJL79 on 2008-08-13
> **caljohnsmith said:**
> How is it you start your Ubuntu server? I don't use the Ubuntu server software so I really don't know any particulars about it, and whether it is done automatically on login or not. I would need to know that before I could make a recommendation of how to automatically run that networking restart command. For instance, the Server might have its own bash script of services it starts, and you could just put the networking restart in there.

Only thing i can tell you is it is a standard installation of Ubuntu server. Configured my wifi connection by editing /etc/network/interfaces. And i also installed VMware server but i dont think this has nothing to do with this particular problem. I have not installed or edited anything else, all default settings

---

### Post by Iowan on 2008-08-13
> **JJL79 said:**
> Is there anything i can do to make this happen automatically?Check the **/etc/network/interfaces** file.  If there is no "auto" line for the wireless connection, add one.
 I like **nano** as an editor - *Might* need to use ```
sudo nano /etc/network/interfaces
```

---

### Post by lucia_engel on 2008-08-13
First make a script
```
sudo nano /etc/init.d/wireless.sh
```
Put the following line into the file:

/etc/init.d/networking restart

ctrl+x, y to exit

Make this script executable
```
sudo chmod +x /etc/init.d/wireless.sh
```

Run this script during startup
```
sudo ln -s /etc/init.d/wireless.sh /etc/rcS.d/S40wireless
```

---

### Post by JJL79 on 2008-08-14
I cannot access this computer before friday but i will post here as soon as i can. Thanks for you help.

---

