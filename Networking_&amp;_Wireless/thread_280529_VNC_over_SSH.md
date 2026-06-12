---
title: "VNC over SSH"
date: 2006-10-19
forum: Networking &amp; Wireless
---

### Post by _Dan on 2006-10-19
Hi,

I have used this article [https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

to attempt to remote desktop to another ubuntu machine across the internet.

I followed the instructions, installation etc.

Now I get the other person to run "vncserver :1"

then I run "vncviewer -via their_IP ubuntu:1"

But it doesn't work! Eventually I get a time out error.

> daniel@ubuntu-laptop:~$ vncviewer -via their_IP ubuntu:1
VNC viewer version 3.3.7 - built Feb 20 2006 12:04:05
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
ssh: connect to host their_IP port 22: Connection timed out
vncviewer: Tunneling command failed: /usr/bin/ssh -f -L 5599:ubuntu:5901 their_IP sleep 20.

(I replaced the actual IP with "their_IP")

Perhaps the problem is with ports. I am on a university network and am allowed to specify 10 OUTGOING ports. I have port 22 with TCP opened. Is that enough/correct?

Please help.

---

### Post by kidders on 2006-10-19
Hi there,

Port 21 is the wrong port -- you need port 22.

---

### Post by _Dan on 2006-10-20
> **kidders said:**
> Hi there,

Port 21 is the wrong port -- you need port 22.

Sorry, that was a typo. I do have port 22 open for TCP.

---

### Post by kidders on 2006-10-20
Oic... in that case, your problem is more complicated :-(

Have you covered all the basic stuff, like ensuring port 22 is open on the destination box? (What happens, for instance, if you try to SSH into it normally?)

Here's a quick list...

[LIST]
[*]Is port 22 actually the port you want to connect to? (Sometimes people use non-standard ports on purpose, to throw off port scanners.)
[*]Are external connections to port 22 firewalled on the target machine?
[*]Is an SSH server really listening on an external interface on the target machine?
[*]Are outgoing TCP connections destined for port 22 firewalled on *your* end?
[*]Are you using the correct hostname/IP on your end?
[/LIST]

That covers the SSH end of things, so if you get this far, you should be able to initiate a plain SSH connection between the two computers. Assuming you can, here are some additional issues:

[LIST]
[*]Are your login details correct?
[*]Does the target machine let you redirect unprivileged ports?
[*]Can you run a more basic redirection test than VNC?
[/LIST]

By "a more basic" test, I mean something like hijacking the remote computer's www proxy or web server. Starting with a simpler protocol than VNC's makes problems easier to diagnose :-)

I hope something here identifies your problem for you. It seems as though your issue is SSH-related, rather than VNC-related. With any luck, once you sort it out, you won't discover any additional issues!!

---

### Post by _Dan on 2006-10-21
I finally managed to get ssh working after about 2 hours stepping the other person through port forwarding on their router...

Now, I try the command

vncviewer -via username@ip_address ubuntu:1

but it gives the error "can't open display"

```

daniel@ubuntu:/$ vncviewer -via user@ip_address ubuntu:1
VNC viewer version 3.3.7 - built Feb 20 2006 12:04:05
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
Could not create directory '/home/daniel/.ssh'.
The authenticity of host 'ip_address (ip_address)' can't be established.
RSA key fingerprint is a1:f6:98:7a:08:11:03:bb:94:5c:45:3a:5c:b8:38:18.
Are you sure you want to continue connecting (yes/no)? yes
Failed to add the host to the list of known hosts (/home/daniel/.ssh/known_hosts).
user@ip_address's password:
Error: Can't open display:
```

Why might this be?

Also, I'm not sure if I am supposed to open ports for VNC too (I haven't), or if VNC goes over the ssh and just uses port 22 as well?

Thanks :)

---

### Post by kidders on 2006-10-21
Hey again,

If you are in a position to open VNC-related ports, tunnelling the connection over SSH is completely unnecessary. SSH connections are encrypted, which will significantly slow down your remote graphical environment. Having said that, encryption may be exactly *why* you are tunnelling your VNC in the first place. Another advantage is that the target computer's X-related security can afford to be a bit laxer if it's only being exposed locally.

Anyhow, back to your problem.

In **Can't open display:**, you would normally expect to see something after the colon. Your VNC viewer may not be configuring the X display forwarding properly.

Try performing the connection step-by-step yourself first, to see if it will work. Once it does, you can worry about automating it.

Also (and probably unrelated to your problem), **Could not create directory '/home/daniel/.ssh'** is concerning. Why can't you create files in your own home directory, I wonder!

---

### Post by _Dan on 2006-10-23
Sorry to be a n00b ;) But how do I perform it step by step?

---

