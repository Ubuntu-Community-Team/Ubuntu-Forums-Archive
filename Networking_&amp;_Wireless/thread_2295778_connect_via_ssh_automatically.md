---
title: "connect via ssh automatically"
date: 2015-09-21
forum: Networking &amp; Wireless
---

### Post by marchello_lippi2 on 2015-09-21
Hi all, 

My need is to establish ssh connection automatically (with password) and reconnect if the pipe is broken. Now I do it manually: 

ssh user@ip -D5902 (password is entered manually too). 

How do I perform it? 

Thanks ahead.

---

### Post by Lars Noodén on 2015-09-21
Set up a key pair, and use a good passphrase.  Then load the key into the agent which Ubuntu has running for you then use a while loop.

```

while true; do ssh -i /path/to/some/key -D5902 user@ip; done

```

---

### Post by ian-weisser on 2015-09-21
You seem to have several problems here.

1) How to connect. Lars Nooden is totally right - DON'T use passwords to connect to an internet-facing server. There are huge botnets on the internet that do NOTHING BUT try to break into password-protected SSH servers...successfully too often for my comfort.

2) How to detect that the connection is broken. [EDIT] Superior advice in Post #4 below.

3) How to reconnect. Do you need to reconnect to the *same session? *(to rejoin a game or return to a running application) If so, use a terminal multiplexor (screen, tmux) to preserve a single session across multiple connections. Or structure your application as a service/daemon so you don't need to always be connected to it.

---

### Post by Lars Noodén on 2015-09-21
> **ian-weisser said:**
> 2) How to detect that the connection is broken....

That can be done in ~/.ssh/config for that particular server or by adding to the runtime options to your script.  That would be [ServerAliveCountMax or ServerAliveInterval](http://manpages.ubuntu.com/manpages/trusty/en/man5/ssh_config.5.html)

---

