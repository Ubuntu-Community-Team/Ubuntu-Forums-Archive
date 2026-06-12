---
title: "SSH Into server from Inside University Network (blocked)"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by Tobywuk on 2008-10-17
Im trying to SSH into a server I have running at home. SSH connections to it work when im at other locations but I cant seem to connect to it inside my university's network, I get 

"ssh: connect to host xxxxxxxxxxxxx port 22: Connection refused"


Is there any way I can get round this problem and connect to a remote server via SSH inside my university network?

---

### Post by mtausig on 2008-10-17
Do you know where the connection is blocked (on the university side or on your home side)? 
What does the firewall of your home host contain?
Does the sshd logs say anything about the connection?

---

### Post by Tobywuk on 2008-10-17
I'm assuming its the university that has it blocked because it works at other locations.

not sure how to view the openSSH server logs.

I read somewhere about using a different port for SSH but im not sure how to do this.

---

### Post by mtausig on 2008-10-20
> **Tobywuk said:**
> I'm assuming its the university that has it blocked because it works at other locations.

not sure how to view the openSSH server logs.

They can be found in the syslog (/var/log/syslog or /var/log/messages)
Record the time when you try to login from you university, and when you are back home check if there are any lines which contain the line sshd at the given time (you can write "sudo grep sshd /var/log/syslog|less" to facilitate the search).

> 
I read somewhere about using a different port for SSH but im not sure how to do this.
On your server, edit the file /etc/ssh/sshd_config and change the line "Port 22" to "Port 123456", or whatever Port you like (or add it, if it is not there). You then have to login using "ssh myhost:123456"

---

### Post by kreggz on 2008-10-20
::cough:: port 80 ::cough::

---

### Post by mtausig on 2008-10-20
Port 80 for SSH? Not a good idea.
You should choose a port number higher than 49152, that's where the unassigned ports start.

---

### Post by Loudergood on 2008-10-20
Well, port 80 is handy just because if the University has blocked all other outbound ports then you know it's open.

---

### Post by mtausig on 2008-10-21
Good point.

---

