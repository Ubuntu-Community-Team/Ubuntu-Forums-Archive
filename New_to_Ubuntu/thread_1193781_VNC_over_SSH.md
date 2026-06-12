---
title: "VNC over SSH"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by Sock puppet on 2009-06-21
I'm trying to run vnc over ssh to my windows machine at the office. I used putty on my home pc running ubuntu and connected, creating a tunnel over port 5900 and I get a command line. But when I try to connect my vnc viewer to 127.0.0.1 it won't connect. I must be missing something. Let me know if I'm being unclear, I've lurked in these forums for a long time but never posted any questions. Thanks!

---

### Post by Bachstelze on 2009-06-21
Which VNC software are you running?

---

### Post by Sock puppet on 2009-06-21
> **HymnToLife said:**
> Which VNC software are you running?

I'm running Vinagre. and tightvnc on the windows box

---

### Post by Bachstelze on 2009-06-21
Are you sure your VNC server is listening on port 5900? What does this command output?

```
sudo netstat -aln | grep 5900
```

---

### Post by Sock puppet on 2009-06-21
> **HymnToLife said:**
> Are you sure your VNC server is listening on port 5900? What does this command output?

```
sudo netstat -aln | grep 5900
```

that command doesn't seem to work on the windows box. I'm running cygwin. I know that it was listening to 5900 because I could get a direct vnc connection through that port. I currently have 5900 closed on my router and am only forwarding through port 22 on the router.

---

### Post by XCan on 2009-06-22
I am slightly confused by your question Sock puppet. Are you running sshd on your Windows machine and want to ssh into it and tunnel VNC, i.e., connection from ubuntu -> Windows or the other way around?

---

### Post by Sock puppet on 2009-06-22
Yes, I'm trying to go Ubuntu -> windows. I was following these instructions [ here. ]("http://members.shaw.ca/nicholas.fong/vnc/")

---

