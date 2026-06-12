---
title: "Setup Remote Desktop - VNC?"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by blueridgedog on 2009-02-17
This weekend I am setting up Ubuntu for a retired friend that lives about an hour away.  He is leaving Vista behind and I want to be able to help him when he needs a bit of support.  I want to setup something like VNC on his system do he can see what I do with the mouse/etc so that he learns along the way.  I could simply setup VNC and forward the ports in through his router, but that would be insecure. 

Is there a simple method to do this?  I have looked at ssh tunneling, but need something that will work without fail and something that can be setup and tested while there.  I am pretty network aware and can setup his router as needed.

Any suggestions for how to help him when he calls?

---

### Post by DGortze380 on 2009-02-17
> **blueridgedog said:**
> This weekend I am setting up Ubuntu for a retired friend that lives about an hour away.  He is leaving Vista behind and I want to be able to help him when he needs a bit of support.  I want to setup something like VNC on his system do he can see what I do with the mouse/etc so that he learns along the way.  I could simply setup VNC and forward the ports in through his router, but that would be insecure. 

Is there a simple method to do this?  I have looked at ssh tunneling, but need something that will work without fail and something that can be setup and tested while there.  I am pretty network aware and can setup his router as needed.

Any suggestions for how to help him when he calls?

Dyndns for the IP issues.

RDP is encrypted by default. Not sure what protocol Ubuntu uses for Remote Desktop Functionality.

Road Warrior VPN may be useful to look at.

---

### Post by blueridgedog on 2009-02-19
I have elected to tunnel VNC over ssh by opening port 22 on the firewall then porting it to the host in question.

Locally I setup the tunnel with:

```
ssh -L 5901:localhost:5901 user@remotehost.IP.com
```

Then I VNC to localhost:5901

If I am running a server (which I am not), then I will use another port locally as the "here" end of the tunnel.  I will test it this weekend.

---

