---
title: "Certain ports are blocked"
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by TorchlightJay on 2007-08-28
So I am on a school network and it blocks certain ports. Example, I run a server back at my office and have webmin. It uses port 10000 and I use SSL so I type https:// to log in. I can do it anywhere else but at school I can't. I also ahve some people I need to remote connect to and 5900 is blocked as well. I want to use MSN or AIM messenger and those ports are blocked as well. I am sure more are too for security. 

Naturally I don't want to cause any problems and I don't want to change all of my ports and configuration on all my machines just to get past that. Anyone have any idea on how to bypass this without like you know hacking or anything. You know, can't I just forward ports or something. SSH does work, I can say that. Thanks.

---

### Post by ddrichardson on 2007-08-28
No is the quick answer - if they are blocking ports its a policy decision that could lead you into hot water if you circumvent it.

---

### Post by TorchlightJay on 2007-08-28
Man that stinks lol. hmmm, so there is no way to like create a tunnel or do a port forward and do my webmin traffic through say port 8080?

---

### Post by croto on 2007-08-29
Ok, here's my recommendation: run a VNC server in a computer out of the school network (say, your home computer). The idea would be to run everything - the browser, instant messegers, etc. - in that VNC session. Let's assume that the vnc server is listening on 208.120.22.15, port 5901. You'll need to bypass the school's firewall. For that, as you mentioned, you want to create an ssh tunnel. Let's use the same computer that's running the vnc server:

```

ssh -N -L5901:127.0.0.1:5901 user@208.120.22.15

```

That should create the tunnel. Then connect your vnc viewer to 127.0.0.1:5901.

In case you want to use a different computer to create the ssh tunnel, say 208.120.22.20:

```

ssh -N -L5901:208.120.22.15:5901 user@208.120.22.20

```
and point your vnc viewer to 127.0.0.1:5901 (this assumes that you can connect to 208.120.22.15 from 208.120.22.20!)

I hope that helps.

---

### Post by TorchlightJay on 2007-08-29
I am feeling your theory. i think it's good but I think 5900/10 are blocked. Can we use another port. Perhaps I have the wrong theory lol. Let's say the firewall blocks port 5900/10 and I still want to create a tunnel, by creating an SSH tunnel, it automatically breaks through the firewall but utilizing port 22? If that's the case then cool, I'll do that. So do I need to log onto my computer via SSH and type in that command or do i do that on my notebook?

---

### Post by croto on 2007-08-29
Even though the firewall blocks outgoing connections to ports 5900-5910, it wouldn't matter. Let me try to explain it with an example. Suppose you create a tunnel:
```

ssh -N -L5905:208.120.22.15:5901 user@208.120.22.20

```
and the connect the vncviewer to 127.0.0.1:5905.  The ssh line causes the connection to localhost (127.0.0.1) port 5905 to be forwarded to 208.120.22.20 (this goes through port 22), then from there, it connects to 208.120.22.15:5901.

Does it make sense?

---

### Post by TorchlightJay on 2007-08-29
Ya, it makes sense. Let me run this by you and you can correct me if I get anything wrong. 

I have my notebook that I am carrying around to school and I have my desktop back at the office (as well as my server). I want to connect to my server and everyone elses server amongst other things so what i will do is connect to my desktop via VNC and do all these things through the my desktop. 

I create a tunnel and it connects me from port 22 on my notebook to port 5901 on my desktop. 

Now I have a question about the code here.

ssh -N -L5905:208.120.22.15:5901 user@208.120.22.20

it shows both port 5905 and port 5901, does this mean send all traffic from 5905 on the desktop to 5901 or what does the code actually mean? I just like to know so I have better understanding of what I am doing.

---

### Post by croto on 2007-08-29
ssh -N -L localport:remotehost:remoteport user@host

That line means: forward all connections received on localhost:localport to remotehost:remoteport through host. As seen by remotehost, the connection was originated from host. The -N option is to avoid spawning a shell when you connect to host. It's actually not necessary...

---

### Post by TorchlightJay on 2007-08-29
Cool, so what do I put as local port or does it matter? Like should I put down 5900 seeing as that is the port I need to connect to or do I put 22 for SSH purposes. I am guessing theremote port is the port I am trying to access (5900 for VNC in this instance).

---

### Post by croto on 2007-08-29
Actually it's doesn't really matter what local port you use. It's recommended you use a port above 1024 (if you want to use a port < 1024, then you need to run the ssh command as root, those ports are reserved, but there's no need for that indeed). Another thing is that the port shouldn't be used by another program. Anyways, if for any reason, the port is unavailable or there's any problem, SSH will complain. And your guess about the remote port is absolutely correct ;)

Good luck!

---

### Post by TorchlightJay on 2007-08-29
Cool, one quick question. You mentioned it doesn't matter what port i use, well do I still need to use a port that is available and not blocked by the firewall or can I use any port (so long as it's above 1024). If I do need to use a specific port, you have any idea how I can scan to see what ports are available for usage for my computer on the network I am on? I think that should cover all my questions.

---

### Post by croto on 2007-08-29
When you connect to localhost:localport, you are making a connection to the local computer, so according to the firewall, there's no *outgoing* connection on port localport. In other words, you're not connecting to the port localport on an outside computer, that's blocked. But local conections should be totally permitted.

---

### Post by TorchlightJay on 2007-08-29
Okay, sorry, this is kind of related. For some reason, my ssh won't allow me to connect to my desktop from another network. Any thoughts?

---

### Post by croto on 2007-08-30
maybe your router at home is not forwarding port 22 to your desktop box

---

### Post by TorchlightJay on 2007-08-30
I think I know the problem. I went and connected to two other computers and tried doing SSH to my desktop from them and it worked just fine. I think my computer has some kind of firewall blocking it. I use firestarter and I think it integrates with iptables. How do I set it to allow me in?

---

### Post by croto on 2007-08-30
can you please post the output of 
```

sudo iptables -L

```
in your computer? This should show the firewall rules, let's see if there's anything weird there...

---

