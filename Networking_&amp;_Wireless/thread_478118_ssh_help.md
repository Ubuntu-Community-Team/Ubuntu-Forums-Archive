---
title: "ssh help"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by louislepperd on 2007-06-19
hi 
i have ssh up and running and can log on to my computer from a different one
is there a easy to tunnel gui,s (metacity, ect)
also if not is there a web browser i can use in the terminal with picures  
thanks in advance 
Louis

---

### Post by PaulFr on 2007-06-19
VNC is one way to redirect desktops, so you can see your remote desktop and interact with it as if you were sitting in front of the remote machines. See [http://www.vanemery.com/Linux/VNC/vnc-over-ssh.html](http://www.vanemery.com/Linux/VNC/vnc-over-ssh.html) for a long discussion of various VNC setups over SSH. The version discussed there is TightVNC.

---

### Post by napzilla on 2007-06-19
If I need to tunnel a GUI over ssh I typically just use:
```
ssh -X user@host
```
Obviously, this method requires a decent high-speed connection if you want to use it without tearing your hair out. As PaulFr mentioned, the other option is to use VNC (or RDP if you're connecting to a Windows machine). VNC is probably more efficient if you're planning on working with multiple GUIs simultaneously.

- napzilla

---

