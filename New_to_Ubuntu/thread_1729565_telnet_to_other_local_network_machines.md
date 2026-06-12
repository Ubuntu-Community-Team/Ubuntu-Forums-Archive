---
title: "telnet to other local network machines"
date: 2011-04-15
forum: New to Ubuntu
---

### Post by tysonh80 on 2011-04-15
I've been trying to find a way to host a telnet session on my desktop and connect to that sesison on my laptop.  Is this even possible.  I haven't been able to find much info on doing this in your local network.  I've downloaded putty but its only the client version.  Is there a server/host version I should be using?

---

### Post by r-senior on 2011-04-15
You probably want SSH rather than telnet ...

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

Once set up, you'll be able to open up a terminal window and type 'ssh desktop', or whatever your machine name is. Set up the keys correctly and you effectively have a single-sign-on.

You can also copy files using scp.

---

### Post by alphacrucis2 on 2011-04-15
> **tysonh80 said:**
> I've been trying to find a way to host a telnet session on my desktop and connect to that sesison on my laptop.  Is this even possible.  I haven't been able to find much info on doing this in your local network.  I've downloaded putty but its only the client version.  Is there a server/host version I should be using?

As the other poster said, forget telnet, it even sends passwords in the clear. Install the OpenSSH server instead. You can still use putty as an SSH client. In fact I use putty myself, I greatly prefer it to the basic OpenSSH client.

---

### Post by seawolf167 on 2011-04-15
> **r-senior said:**
> You probably want SSH rather than telnet ...

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

Once set up, you'll be able to open up a terminal window and type 'ssh desktop', or whatever your machine name is. Set up the keys correctly and you effectively have a single-sign-on.

You can also copy files using scp.

+1 for SSH, telnet is way insecure

---

### Post by tysonh80 on 2011-04-15
thanks for the info.  I'm going to give open ssh a try

---

### Post by tysonh80 on 2011-04-15
> **r-senior said:**
> You probably want SSH rather than telnet ...

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

Once set up, you'll be able to open up a terminal window and type 'ssh desktop', or whatever your machine name is. Set up the keys correctly and you effectively have a single-sign-on.

You can also copy files using scp.

I followed the link.  On my laptop(putty client) I'm not sure what I type in for username so I have just been entering the laptop name as it appears on the network.  Secondly it keeps asking me for a password when i changed the config file to allow for public keys and blank passwords.

Am I missing something?

---

### Post by seawolf167 on 2011-04-15
The username would be the user you want to login as, the password would be that user's password.

When you change the config file on your local machine, the password required is the root password (i.e. the password you enter when you want to do a *sudo* command)

---

### Post by tysonh80 on 2011-04-16
> **seawolf167 said:**
> The username would be the user you want to login as, the password would be that user's password.

When you change the config file on your local machine, the password required is the root password (i.e. the password you enter when you want to do a *sudo* command)

thanks for the tip and I got it to work, but I was moving through the directories on the host machine and I wanted to see if I could open a movie I have stored on the host machine.  With my Putty client I entered gnome-open <file name.avi>  and it spit an error saying it failed to contact the configuration server and that I may need to enable tcp/ip networking for ORBit.

---

### Post by tysonh80 on 2011-04-16
also when I try to connect to the ssh server from outside my network the connection times out.  On my router I would open the port and forward it to the host machine right?

---

### Post by seawolf167 on 2011-04-16
To forward windows, you'll have to use the *-X* switch

Sample command to connect with X forwarding (in Putty, go to the X forwarding section and click the box to select to "forward X11"

```
ssh -l *username* -X -c blowfish -C -X *ipaddresshere*
```

To access your box from the internet, you'll need to port forward from your router to your computer. The default port is 22, so unless you changed that, forward port 22 from your router to your computer.

---

