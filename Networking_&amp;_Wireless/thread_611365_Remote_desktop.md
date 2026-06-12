---
title: "Remote desktop"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by mchaley on 2007-11-12
Alright. 
I've been working on this for about a day now. I'm trying to figure out a way to remote desktop into a ubuntu desktop/server from a windows XP machine. 

I've learned that NX> VNC. 
I've got NoMachine client/node/server installed on the ubuntu (desktop edition). 
I've got NoMachine client on my XP machine. 

problems thus far: 
 I can not figure out how to configure the server.(ie. usernames, passwords, servername, etc.) 

Ideally, I'd like a walk through. This is really complicated... for me anyway. I've installed the server manager and cant even figure out how to open it >:C 

Thanks

---

### Post by c0mp13371331337 on 2007-11-12
I'm sure you have your reasons for using VNC varients, but I must say, I'm quite satisfied with running vino-server (Ubuntu default package) and plain old vnc-viewer (in Windoze) at work.  Its a very fast, very stable remote connection, even cranking the 3200x1200 resolution of my home computer.  Configuring is a snap in System > Preferences > Remote Desktop, and you can specify a non-standard port in the Ubuntu Configuration Editor.

As far as your actual question goes, unfortunately I'm not familiar with the software you're using, so I'd be of no assistance at all with that.  Just commenting on how quick and easy it is with the tools included in Ubuntu.

---

### Post by mchaley on 2007-11-12
At this point, I'm told that NX>VNC. 
NX includes SSH whereas VNC requires more tweeking to pipe through SSH. 

I'm trying to go the NX route. I'm experimenting now because over the Thanksgiving break, I'm going to build a multi-os web server to experiment with. I'm trying to figure all of this out so I dont waste time later :P

---

### Post by weblordpepe on 2007-11-13
Good stuff. Try to get NX going. It's vastly superior to VNC. If you ask me, it should be integrated into the remote desktop client & VNC should be given the boot.

The NX server uses your system's authentication system. Because it logs in via SSH, you are logging into the actual system. I beleive on the nomachine site there is information on how to do it.

What happens when you try to connect? Are you able to connect successfully?

---

### Post by mchaley on 2007-11-13
No, I'm not able to connect. 
Like I've said, the client, node, and server are on the ubuntu machine. No configs done. 

client is on the xp machine. 
I've tried connecting to IP and comp name. 
tried an array of usernames/passwords. 
Nothing yet. 

I've been searching, but nothing found so far. :(

---

### Post by mchaley on 2007-11-13
NX> 203 NXSSH running with pid: 11204
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
ssh: connect to host 10.4.51.244 port 22: Connection timed ou

---

### Post by Fire_Chief on 2007-11-13
Do you have a firewall enabled on the server machine? Are you trying to access it from the same network or from the Internet for testing? Can you ping the Ubuntu system from the XP system?

---

### Post by mchaley on 2007-11-13
Cool, got it working. 
a few questions:

1). is SSH active on default settings? (ie. am I encrypted at first use?) 
2). I went into system monitor on my XP machine. Nothing came up on that session, however system monitor moved desktops on my ubuntu machine (laptop right next to me). Err... how do I fix that :P

---

### Post by Inxsible on 2007-11-13
> **mchaley said:**
> Cool, got it working. 
a few questions:

1). is SSH active on default settings? (ie. am I encrypted at first use?) 
2). I went into system monitor on my XP machine. Nothing came up on that session, however system monitor moved desktops on my ubuntu machine (laptop right next to me). Err... how do I fix that :P
how did you get it working ?

I get the same connection timed out messages too please see this thread and help out if you can. [http://ubuntuforums.org/showthread.php?t=612208](http://ubuntuforums.org/showthread.php?t=612208)

---

### Post by mchaley on 2007-11-13
lol in my case, I thought the IP was one thing when it was really another IP. I also created another username/pw to login from over NX. It all seems to be working... I just HOPE its SSH encrypted. I'm not sure how to tell if it is or not.

---

### Post by Inxsible on 2007-11-13
> **mchaley said:**
> lol in my case, I thought the IP was one thing when it was really another IP. I also created another username/pw to login from over NX. It all seems to be working... I just HOPE its SSH encrypted. I'm not sure how to tell if it is or not.Using the local IP address works for me too, altho with a few problems like resolutions and such. did you get it working with using a no-ip hostname instead of the local ip address ?

---

### Post by mchaley on 2007-11-13
no i just used the propper IP.

---

### Post by weblordpepe on 2007-11-14
My understanding is that NX only talks to another computer via SSH.

---

### Post by Inxsible on 2007-11-14
> **weblordpepe said:**
> My understanding is that NX only talks to another computer via SSH.Yes, I am trying to connect NX over SSH. Still doesn't work however :(

---

### Post by serpentine on 2007-11-14
> **mchaley said:**
> lol in my case, I thought the IP was one thing when it was really another IP. I also created another username/pw to login from over NX. It all seems to be working... I just HOPE its SSH encrypted. I'm not sure how to tell if it is or not.

mchaley,

All NX communication is tunneled via a SSH connection.  By default, it is also encapsulated by SSL  This can be turned off in the configuration files to allow unencrypted connections or force only encrypted connections to the server.

.

---

