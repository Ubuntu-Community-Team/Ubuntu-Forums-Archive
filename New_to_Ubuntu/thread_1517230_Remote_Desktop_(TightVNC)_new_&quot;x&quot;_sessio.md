---
title: "Remote Desktop (TightVNC) new &quot;x&quot; session"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by Ezrie on 2010-06-24
Hi.  Connecting from XP to Kubuntu 10.4 using TightVNC.  I can easily connect using the computer IP.

I read that adding a ":1" to the end of the IP will create a new "x" session separate from the one a user at the target machine is using; i.e. I could connect remotely without disturbing the current session at the target machine.  However, this doesn't seem to be working as I get an error when trying with the ":1" at the end of the IP.

Thanks for the help!

---

### Post by Windows Nerd on 2010-06-24
> **Ezrie said:**
> Hi.  Connecting from XP to Kubuntu 10.4 using TightVNC.  I can easily connect using the computer IP.

I read that adding a ":1" to the end of the IP will create a new "x" session separate from the one a user at the target machine is using; i.e. I could connect remotely without disturbing the current session at the target machine.  However, this doesn't seem to be working as I get an error when trying with the ":1" at the end of the IP.

Thanks for the help!
Where did you read that? Adding ":1" to the end of an IP makes the IP void an null, which is why you cannot connect to the target machine. It is like telling someone to look for the adress 1590:1. That person will tell you that no such address exists because no address has a colon in it. Same with TightVNC.

I'm curious where you read that, please, let me know!

---

### Post by Ezrie on 2010-06-24
> **Windows Nerd said:**
> Where did you read that? Adding ":1" to the end of an IP makes the IP void an null, which is why you cannot connect to the target machine. It is like telling someone to look for the adress 1590:1. That person will tell you that no such address exists because no address has a colon in it. Same with TightVNC.

I'm curious where you read that, please, let me know!

[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

I see now that this is old information but it does say:

"So here's the complete list of steps that are required to set the VNC server that any user can login into and start a session. It is also persistent, meanning that even if you disconnect the VNC client your X session will not end (unless you explicitly log out) and you can reconnect to the same session again. The VNC server uses a separate display (:1) than your regular X server, which works with your physical display (:0). So two sessions can be active at the same time (one person sitting at the physical display and another remotely connecting using VNC"

**All that said, is it now possible to have 2 "x" sessions running, 1 for a local user and 1 for a vnc connected user?**

---

### Post by CharlesA on 2010-06-24
> **Windows Nerd said:**
> Where did you read that? Adding ":1" to the end of an IP makes the IP void an null, which is why you cannot connect to the target machine. It is like telling someone to look for the adress 1590:1. That person will tell you that no such address exists because no address has a colon in it. Same with TightVNC.

I'm curious where you read that, please, let me know!

It's specifying for port number, or in this case display number. 5900+(display).

@OP: You can do it that way, since tightvnc server creates "virtual" desktops.

---

### Post by Ezrie on 2010-06-24
> **CharlesA said:**
> It's specifying for port number, or in this case display number. 5900+(display).

@OP: You can do it that way, since tightvnc server creates "virtual" desktops.

Am I doing this right?  In the connection dialog in VNC on my windows machine i put in the *ipaddress*:5901.  The error message still says "error connecting to *ipaddress*:1"

---

### Post by CharlesA on 2010-06-24
You would have to start a new session from a terimal by typing: vncserver :1 I believe.

---

### Post by Ezrie on 2010-06-24
> **CharlesA said:**
> You would have to start a new session from a terimal by typing: vncserver :1 I believe.

I don't understand this.  Is the done on the target (kubuntu) or on the viewer (xp)?

---

### Post by Ezrie on 2010-06-25
We are so close!  Anyone?

---

### Post by rbc on 2010-06-25
Erzie,
In case you haven't figured this out,  here's the way I just did it. Keep in mind, I am using Ubuntu, not Kubuntu and on the Windows side, I am using RealVNC, not TightVNC. Hope this doesn't make a difference.
You need vncserver installed and running on the linux machine. Search for vnc4server in Synaptic. Then you need PuTTY for the Windows machine. Use PuTTY to get a terminal window of the linux computer and type:
vncserver :1
Now open TightVNC (on the Windows machine) and type ipaddress:1


To kill the vncserver :1 session, type vncserver -kill :1

---

### Post by Ezrie on 2010-06-25
> **rbc said:**
> Erzie,
In case you haven't figured this out,  here's the way I just did it. Keep in mind, I am using Ubuntu, not Kubuntu and on the Windows side, I am using RealVNC, not TightVNC. Hope this doesn't make a difference.
You need vncserver installed and running on the linux machine. Search for vnc4server in Synaptic. Then you need PuTTY for the Windows machine. Use PuTTY to get a terminal window of the linux computer and type:
vncserver :1
Now open TightVNC (on the Windows machine) and type ipaddress:1


To kill the vncserver :1 session, type vncserver -kill :1

Rbc,

Thanks. I will try this and report back.

---

### Post by Oblong_Cheese on 2010-06-26
> **rbc said:**
> Erzie,
In case you haven't figured this out,  here's the way I just did it. Keep in mind, I am using Ubuntu, not Kubuntu and on the Windows side, I am using RealVNC, not TightVNC. Hope this doesn't make a difference.
You need vncserver installed and running on the linux machine. Search for vnc4server in Synaptic. Then you need PuTTY for the Windows machine. Use PuTTY to get a terminal window of the linux computer and type:
vncserver :1
Now open TightVNC (on the Windows machine) and type ipaddress:1


To kill the vncserver :1 session, type vncserver -kill :1

Just found this thread through Google, and had to say that this is awesome! Thanks!

---

### Post by Ezrie on 2010-06-30
> **rbc said:**
> Erzie,
In case you haven't figured this out,  here's the way I just did it. Keep in mind, I am using Ubuntu, not Kubuntu and on the Windows side, I am using RealVNC, not TightVNC. Hope this doesn't make a difference.
You need vncserver installed and running on the linux machine. Search for vnc4server in Synaptic. Then you need PuTTY for the Windows machine. Use PuTTY to get a terminal window of the linux computer and type:
vncserver :1
Now open TightVNC (on the Windows machine) and type ipaddress:1


To kill the vncserver :1 session, type vncserver -kill :1

Before I try this, does it make sense to download vnc4server?  Doesn't Ubuntu have a built in vnc server?  Also, I already installed an nx server as well.  

Does 3 remote servers running on the machine make sense?  Can I turn off the built in vnc server?

---

### Post by Ezrie on 2010-07-11
Didn't work.  Thanks though.  Current solution is vnc for current session and nx for logging into a new session.

---

