---
title: "Vnc?"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by StOoZ on 2008-03-28
Hello.
I would like to connect to my ubuntu system remotely, from a windows operating system.
I think that I need to use VNC for that , right?

if so, firstly, I would like to test it with my native linux ->Virtualized vista (vmware), is it possible?

---

### Post by rahearn on 2008-03-28
I've had a lot of success using NX Server from [http://nomachine.com](http://nomachine.com)  It's not open source, but it is free as in beer.  You'll need to install the NX client, node, and server on your ubuntu machine (they all come as debs) and the client program on your windows box and it should just work.  Also, you'll need sshd running on your ubuntu box, and there is some configuration to be done if you're not running sshd on port 22.

---

