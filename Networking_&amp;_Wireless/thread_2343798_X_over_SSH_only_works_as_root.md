---
title: "X over SSH only works as root"
date: 2016-11-19
forum: Networking &amp; Wireless
---

### Post by miszt on 2016-11-19
i can access X over SSH as root, but not as any other user, not sure what the solution is?

Running any X app gives the error:

xterm: Xt error: Can't open display: localhost:0

(i set export DISPLAY=localhost:0 manually, it works fine as root, but i dont really want to be using it as root)

Any suggestions?

I've tried both X and Y switches in ssh

X11forwarding and uselocal are both set yes, in sshd_config (i also tried uselocal no)

The only warning i get is about xauth, which afaik isnt relevant to this problem

---

### Post by CantankRus on 2016-11-19
Try just...
```
export DISPLAY=:0
```

---

### Post by steeldriver on 2016-11-19
How exactly are you establishing the SSH connection, and on what platform? What X server is running locally? How are you starting the X client application on the remote machine?

Normally, setting DISPLAY=:0 (or localhost:0) would be exactly the wrong thing to do when forwarding to a local X server - SSH is configured by default to assign a higher number display (starting from :10 iirc) for forwarded connections.

---

### Post by SeijiSensei on 2016-11-19
Try running "xhost +" (include the space) before connecting with SSH.  Any better?

Just now testing as an ordinary user, I ran "xhost +" then connected with "ssh -X" to my account on another machine. I ran xterm on the remote box and the window popped up here as it should.  I needed no root privileges on either end.

---

### Post by miszt on 2016-11-19
I tried display:0 already

> **steeldriver said:**
> How exactly are you establishing the SSH connection, and on what platform? What X server is running locally? How are you starting the X client application on the remote machine?

 Normally, setting DISPLAY=:0 (or localhost:0) would be exactly the wrong thing to do when forwarding to a local X server - SSH is configured by default to assign a higher number display (starting from :10 iirc) for forwarded connections.

Xming and Bash on Ubuntu on Windows; i dont believe the local system is the issue tho, it works fine if i ssh as root

Cant get x apps to run at all without setting display first, it gave me a slight different error (didnt note it, but it had a * in it lol) 


> **SeijiSensei said:**
> Try running "xhost +" (include the space) before connecting with SSH.  Any better?

Just now testing as an ordinary user, I ran "xhost +" then connected with "ssh -X" to my account on another machine. I ran xterm on the remote box and the window popped up here as it should.  I needed no root privileges on either end.

Xhost asks me to install x11 programs, which i cant do in Bash On Ubuntu On Windows; however i dont believe the issue is at my end, but the server end, as i can access X programs without any problem as long as i SSH as root

---

### Post by SeijiSensei on 2016-11-19
Running as root may give you more privileges on the X server than running as an ordinary user.  That's why I thought xhost might matter.  I don't know what "Bash on Ubuntu on Windows" is so I don't know why you can't install xhost, but if you can't, you can't.

---

### Post by miszt on 2016-11-19
> **SeijiSensei said:**
> Running as root may give you more privileges on the X server than running as an ordinary user.  That's why I thought xhost might matter.  I don't know what "Bash on Ubuntu on Windows" is so I don't know why you can't install xhost, but if you can't, you can't.

Its a complete ubuntu image that comes as part of "windows subsystem for linux" in win 10 pro, brilliant feature; having linux on my windows tablet has simplified my life no end!

I'll have a look again at xhost, but i guess i really need to adjust permission on the server

---

