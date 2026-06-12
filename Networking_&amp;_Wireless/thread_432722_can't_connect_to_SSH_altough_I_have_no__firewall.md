---
title: "can't connect to SSH altough I have no  firewall"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by lexarrow on 2007-05-04
Hi all, I'm configuring an enterprise network based on a server running Ubuntu Feisty 7.04. I use webmin as a GUI.

The server has a static, routable address, no firewall installed yet and my problem is I can't connect to SSH even if I have port forwarding enabled; the error I get is 'Connection Timed Out'

I can ping the server and if I try the SSH login module from webmin (from my MS Vista laptop using winSCP) it says that I'm online. 

I read any documentation I could find but still nothing.

I asked a friend to login and he also failed. Some help would be much appreciated.

---

### Post by gwm on 2007-06-04
Similar problem - now fixed. Perhaps my fix can help you track down your problem. I wrote a whole essay about it here:

[http://ubuntuforums.org/showthread.php?p=2778127#post2778127](http://ubuntuforums.org/showthread.php?p=2778127#post2778127)

:popcorn:

---

### Post by eentonig on 2007-06-04
Can you connect to the ssh from the server itself?

Does your ssh server accepts connections on the ip address/interface you're trying?

---

### Post by lexarrow on 2007-06-04
I can now login from a computer on the LAN. Tommorrow I will try from outside.

Thanks for the answers.

---

### Post by cantormath on 2007-07-24
> **lexarrow said:**
> I can now login from a computer on the LAN. Tommorrow I will try from outside.

Thanks for the answers.

What exactly did you do to fix it?

---

