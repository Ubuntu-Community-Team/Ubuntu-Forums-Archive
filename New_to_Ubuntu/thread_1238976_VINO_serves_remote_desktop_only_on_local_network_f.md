---
title: "VINO serves remote desktop only on local network for one user but not the other."
date: 2009-08-13
forum: New to Ubuntu
---

### Post by Zanahade on 2009-08-13
Ubuntu 9.04 : Under one user vino serves to the network out side my lan... no problem. On second user vino will not serve to any vnc outside of local. Vino reads: "Your desktop is only reachable over the local network. Others can access your computer using the address localhost." Same exact settings unless they hid the magic "allow vnc beyond local" somewhere?

---

### Post by Zanahade on 2009-08-13
-Bump-  Anyone?

---

### Post by tetsuc on 2009-09-24
not sure if it is the same issue that I was having, but I actually had to start the server manually... It wasn't showing up in my ps -aux even after I had set all the settings correctly via the gui.

set things in the gui then run this and put it in the background. Hope it works!
/usr/lib/vino/vino-server

good luck!

---

### Post by comradekingu on 2010-01-12
I killed the process, started it again with "/usr/lib/vino/vino-server" Then went to the remote desktop settings and toggled the "configure network automatically" then it works. A reboot would probably have done the trick aswell. 9.10

The main point of getting things to work is having port 5900 open to your machine.

Edit: i actually read your post this time.

If you have a IPv4 network and the port opened in NAT you can only use 5900 once, or set up translation for connections to another port to reach port 5900 on said machine.
Alternatively you can change the port vino listens to and forward that, ending up having to connect to a different port for your second machine even then.

---

