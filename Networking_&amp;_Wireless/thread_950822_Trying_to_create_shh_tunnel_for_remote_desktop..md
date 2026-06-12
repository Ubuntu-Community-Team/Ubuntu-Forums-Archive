---
title: "Trying to create shh tunnel for remote desktop."
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by Stefa on 2008-10-17
I'm trying to use remote desktop by using openssh on a lan.
I'm on winXp(TightVNC), trying to connect to ubuntu(openSSH, vino).

I could connect without password/authentication(checked the box to allow it)
Then I needed more security so wanted to use ssh, I don't understand the ssh tunnel part.

I created a private/public key using putty.
ubuntu shh server is running on ubuntu:5009

I start putty
destination stefan@ubuntu port 5009
when I connect I get a warning: server host key not cached in register... ok
It prompts for my user password and I get a linux ubuntu header
and a cmd.

So I guess it accepts my key?
but no tunnel is made. so vnc can't use the ssh connection?

So that's where i'm lost.
I link what port to what local port :/

I've read most of the other posts but cannot figure this out.

---

### Post by jimv on 2008-10-17
ssh -L 5900:localhost:5900 myserver

This command binds(forwards) port 5900 on your machine to port 5900 on your server.  Then all you do is type 'localhost:5900' for the server in VNC.

Oh wait, you're using Putty.

Ok, so in Putty, put the address/port for your SSH server into the Session info.  Then go down the list on the left and expand SSH, then click on Tunnels.  On the right, for source port, put 5900.  For the Destination, put the LAN ip address of the machine you want to VNC into followed by ':5900'.  Click Add, and then click on Session at the top of the list on the left.  Type a name in the Saved Sessions and click Save.  Then click Open.  Now you should be able to VNC into the remote machine by using 'localhost:5900' as the address.

---

### Post by Stefa on 2008-10-18
Ubuntu ip: 192.168.2.2
SSH running on the default port 22
WinBox ip: 192.168.2.3

Putty:
Destination (stefan@192.168.2.2:22)
Tunnel(5900 -> 192.168.2.2:22)

I can connect to ubuntu, ssh auth using key, connected, cmd.

Then I Run TightVnc(localhost:5900) and I get:
Failed to connect to server(192.168.2.3)

What's wrong?:confused:
Where can I get more information about what exactly went wrong?

---

### Post by jimv on 2008-10-19
This is the command you ran?

ssh -L 5900:192.168.2.3:5900 192.168.2.2

---

### Post by eldragon on 2008-10-19
if you are using putty, its the same as with ssh
```

putty -L 5900:localhost:5900 username@server

```

then try to connect with the vnc client to localhost

thats all there is to it

---

### Post by kevdog on 2008-10-19
Putty keys and openssh keys are not compatible.  You need to make the keys on Ubuntu (openssh), and then import the private key into puttykey gen and then re-save it in the putty format.

---

### Post by Stefa on 2008-10-22
ok, created key on ubuntu and indeed that worked.
Then used putty -L 5900:localhost:5900 username@server
and got connected. woot :lolflag:

thanks all.

But I don't want to just copy a cmd line :p
Where can I find information about the -L switch for example.
I searched for linux -L switch but found switching to linux sites.

I will try to explain the tunneling(please correct me if I write something wrong)
I connect from windows to the openssh server on port 22(default)
My private key is send once and I'm authorized.
then I say localHost port 5900 is tunneled to ubuntu:5900 through the current connection(happens to be ssh)
Then Vnc connects to 5900 locally, it goes through the current connection and comes up at 5900 at ubuntu 
and there it is.

---

