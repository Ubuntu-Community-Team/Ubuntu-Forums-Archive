---
title: "Port Restrictions"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by parfume on 2010-12-15
A file must be read containing the following format:

PORT# IN
PORT# OUT
PORT# BOTH
... etc

When a port is about to be used it must first check to see whether or not the port # is mentioned in the file. If not, it shouldn't be allowed access/use by the kernel. If so, the type of access (inbound, outbound, or both) should be restricted to the type specified in the file.

I have been told sockets.c is where I should start editing and that it only requires a few minor changes (I'm assuming an if statement or two to one of the methods), but I don't know where to start, nor the location of the file.

Help?

---

### Post by cariboo on 2010-12-15
I you told us what you are trying to do, it may be easier for us to help.

---

