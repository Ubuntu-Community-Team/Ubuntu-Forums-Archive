---
title: "ssh won't connect"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by Mets on 2008-06-09
I installed openssh server and client on my computer so that I can access my files from other locations, but I can't seem to connect.  I can ssh to other computers, so the client is working.  If I do "ssh localhost" from my computer, it will connect.  But if I do ssh <my ip> it times out.  What's going on?

---

### Post by frankos44 on 2008-06-09
> **Mets said:**
> I installed openssh server and client on my computer so that I can access my files from other locations, but I can't seem to connect.  I can ssh to other computers, so the client is working.  If I do "ssh localhost" from my computer, it will connect.  But if I do ssh <my ip> it times out.  What's going on?

The PC you are connecting to (remote) needs openssh-server while the PC you are using needs openssh-client.

You need to know the IP address of the remote PC. You can check this by typing ping in the terminal.

The user name must exist on the remote PC.

eg. ssh tom@192.168.0.76

If the remote computer is at a different location (other side of your gateway) the remote router must allow port 22 requests through its firewall.

Hope ths helps.

---

### Post by Mets on 2008-06-09
Thanks, it was the router!

---

