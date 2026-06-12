---
title: "ssh tunnel with remmina"
date: 2014-08-30
forum: Networking &amp; Wireless
---

### Post by cmcanulty on 2014-08-30
I can connect to all computers behind a wan router with remmina, but when I try the ssh tunneling I never can. I have read numerous posts and can't figure out what I'm doing wrong. I have port 22 open on my home router and the work router. On the ssh tab do I put my user name or the name of the user on the remote machine? I have tried both and neither works.There must be some config I have to do on the remote computers or my own that I am missing. I run xubuntu 14.04 at home and some of the work ones, others at work 
run win 7 home premium or win 7 pro.

---

### Post by steeldriver on 2014-08-30
You should use your credentials (username and login password) for the remote machine - also iirc the 'Tunnel via loopback address' option needs to be checked

[ATTACH=CONFIG]255971[/ATTACH]


In the main tab, remember to append the display number (or port) and enter your remote username and VNC password (which is not necessarily the same as your login password)

 [ATTACH=CONFIG]255973[/ATTACH]

---

### Post by cmcanulty on 2014-08-30
I have done all that but no go. As soon as I uncheck ssh it connects fine

---

### Post by steeldriver on 2014-08-30
Are you able to connect to a plain SSH session on the specified port(s)? IIRC you are forwarding different public ports to server1:22, server2:22 and so on. Make sure that side of things is working first.

---

### Post by cmcanulty on 2014-08-30
OK I am closer I didn't realize I had to install ssh as I had openshhserver and opensshclient installed. Now I at least get an error message. I have port 22 open on both machines and port 22 forwarded to 5906 on one machine that connects easily without the ssh to port 5906 in x11vnc
```
Failed to startup SSH session: Protocol mismatch: RFB 003.008
```

---

### Post by steeldriver on 2014-08-30
What exactly do you mean by "port 22 forwarded to 5906"? to tunnel VNC traffic, you should ignore the actual VNC ports (in fact you can leave them as the default 5900 on every machine, and - once you get the tunnelling to work - close them completely) and just set up an SSH connection to each machine's SSH server (which I'd recommend leaving on the default port also i.e. all machines listen on port 22, with your router forwarding 20022 to machine #0, 20023 to machine #1 and so on, or some such numbering scheme of your choice). 

You then open an SSH connection e.g. to your.rem.ote.ip:20023 with a tunnel that effectively tells the target machine to connect its local port 5900 via its port 22 to a specified port on your local machine (e.g. L5901:localhost:5900) where your VNC client can access it via localhost:5901

---

### Post by cmcanulty on 2014-08-30
I guess I don't have a clue how to do what you are saying. I thought if I left all to 5900 how will the router know where to go? There must be some config done on each machine that I can't find anywhere.

---

### Post by steeldriver on 2014-08-30
Your SSH tunnel setup tells the remote machine where to send its VNC traffic (i.e. up the tunnel, via SSH, to a unique port on your local machine)

---

### Post by cmcanulty on 2014-08-30
well I opened 22 on home and work but nothing works for tunneling. Remmina says this is easy to do but obviously I must be missing something very basic

---

### Post by Lars Noodén on 2014-08-31
Which direction are you planning on connecting, from work to home or home to work?

As mentioned by steeldriver, getting plain SSH working is the first step.  If you have a set up like this:

```

  W ----- WR ----- Internet ----- HR ----- H

```

where you want to connnect from box W to box H via the routers WR and HR, then H needs to have openssh-server installed and running (and UFW has to allow port 22 in).  When you can connect to H via ssh from another machine on the same LAN, then this step is done.

Then you have to forward a port on the router HR to H for SSH.  (Extra: If you pick a higher port on the outside your logs will be quieter.)  When you can ssh from W to HR's ip address and you see that you are on H, then this step is done.

```

ssh -p 22  cmcanulty@*xx.yy.zz.aa*

```

After that, it is a good idea to enable key-based authentication for SSH and disable password authentication before going further.

---

### Post by cmcanulty on 2014-08-31
I am going only from home to work and I can access and set router at both ends as I wish. So far I have port 22 open both places and a test of forwarding port 22 to port 5906 at the work end. As that computer uses 5906 for x11vnc. On a windows 7 machine I have openssh installed but see no way to configure it. I have to do this for 17 machines 11 xubuntu 14.04 and 5 win 7, 2 pro, and 4 home premium.I did read that x11vnc is encrypted so is it still necessary to tunnel it?

 x11vnc allows one to view remotely and interact with real X displays (i.e. a display corresponding to a physical monitor, keyboard, and mouse) with any VNC viewer. In this way it plays the role for Unix/X11 that WinVNC plays for Windows.

It has **built-in SSL/TLS encryption **and 2048 bit RSA authentication, including VeNCrypt support; UNIX account and password login support; server-side scaling; single port HTTPS/HTTP+VNC; Zeroconf service advertising; and TightVNC and UltraVNC file-transfer.

---

### Post by steeldriver on 2014-08-31
I still don't get what you mean by forwarding "port 22 to port 5906 [at the work end]". Maybe you are getting confused between ***forwarding*** and ***tunneling***? They are 2 different things - you should be *forwarding* the SSH port and then *tunneling* the VNC traffic over your SSH connection.

---

### Post by Lars Noodén on 2014-08-31
> **cmcanulty said:**
> I am going only from home to work and I can access and set router at both ends as I wish. So far I have port 22 open both places and a test of forwarding port 22 to port 5906 at the work end. As that computer uses 5906 for x11vnc.

Ok, that direction works, too, as long as you can adjust the port forwarding on the router which is receiving incoming connections.  

However, SSH and VNC cannot both listen on port 5906.  If SSH (port 22) is getting redirected to a port (e.g. 5906) where VNC is listening instead of SSH, then the client ssh will report a protocol error probably like the one you showed above.  I would set the router so that it forwards port 22 on the outside to whichever port box W has openssh-server listening on, usually 22.  You need a basic SSH connection first.  Then Remmina will use that SSH service to make the connection and will run VNC inside that.  You won't need to forward anything from the router (WR) to x11vnc (W), Remmina will do that for you over a tunnel it will make using the plain SSH connection.

---

