---
title: "How Can I Connect Remotly Through a Terminal"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by f.ben.isaac@gmail.com on 2008-09-27
I'm a newbie. I just would like to access my Account on the Unix Server of my College. I usually access it through Putty. However, i need to access it through my terminal - command line.

How can i do it?

---

### Post by John164918a on 2008-09-27
try:

ssh username@url_or_ip_address

ssh stands for secure shell. That probably wont give you any windows on it though. For that you should try the -X option. you might not even need vpn!

---

### Post by John164918a on 2008-09-27
it might be like 

ssh user.computer_name.url_or_ip_address

---

### Post by Catalyst2Death on 2008-09-27
The -Y switch in ssh is better than -X because -Y opens trusted X11 forwarding rather than -X which just enables it. So:

```
ssh -Y username@hostname
```

also, ssh packages:

```
sudo apt-get install openssh-client
```

---

### Post by John164918a on 2008-09-27
Thankyou, I just read the man page on it!

---

