---
title: "Secure Remote Desktop Connections"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by Lazy-buntu on 2009-04-13
I'm looking into secure remote desktop connections. I'm not very knowledgeable in this area. I guess RDP is a Windows protocol for remote desktop connection, but I don't believe the packets are secure/encrypted. What are other ways to remote desktop?

My Ubuntu install doubles as an SSH server by the way. I can SFTP to my computer, run commands via SSH clients like putty, and all things like that. I have a ghetto way of remotely using my computer from where ever I may be. If I run gnome-session in an SSH/putty terminal I can run my own session from where ever I am, but it is horribly slow even with compression enabled. I use a portable version of putty and an x-server for Windows.

So bottom line: what alternatives are there for securely controlling a desktop remotely? I stress secure because I can easily do insecure remote desktop connection with an application like TeamViewer, but I don't want anyone eaves dropping on my connection. If I'm at a web cafe, or my university, or any other insecure network I want to be able to remotely connect to my computer without having to worry. 

I'm not familiar with plain old RDP, so maybe I'll read up on that, but I'm pretty sure that's not going to fit the bill. Also, usability should be taken into consideration. Please note if it will work on a Windows computer, and if so, am I going to need a portable app for that.

---

### Post by steve101101 on 2009-04-13
try this page. [http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop](http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop)

it may help ya.

---

### Post by Lazy-buntu on 2009-04-13
> **steve101101 said:**
> try this page. [http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop](http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop)

it may help ya.

I'll read through that. I'm looking at: [http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop#Establishing_a_Secure_Remote_Desktop_Session_from_a_Windows_System](http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop#Establishing_a_Secure_Remote_Desktop_Session_from_a_Windows_System)

Do you have any experience with VNC? I'm wondering if it's going to lag as bad as what I was doing by running gnome-session.

---

### Post by steve101101 on 2009-04-13
i have used it in the past and was quite good. also you might want to try logmein.com 

I use this to access a computer across the country and it works great. I would give this a try as well.

---

### Post by Lazy-buntu on 2009-04-13
I'm guessing you don't need an x-server app if you're doing VNC on a Windows computer over SSH.

As for logmein.com, are you referring to: [https://secure.logmein.com/products/free/](https://secure.logmein.com/products/free/) ? It doesn't mention anything about being secure.

One thing I'd like to avoid is having to install anything on the client computer (installing on the server or computer I plan on controlling is fine), so if it works off of a flash drive that would be awesome.

---

### Post by Lazy-buntu on 2009-04-13
It doesn't seem like LogMeIn is what I'm looking for. I'd like a direct connection to the computer I want to control, or go through my SSH server then to the computer I want to control.

Should I just tunnel VNC through the SSH server?

---

### Post by steve101101 on 2009-04-13
> **Lazy-buntu said:**
> I'm guessing you don't need an x-server app if you're doing VNC on a Windows computer over SSH.

As for logmein.com, are you referring to: [https://secure.logmein.com/products/free/](https://secure.logmein.com/products/free/) ? It doesn't mention anything about being secure.

One thing I'd like to avoid is having to install anything on the client computer (installing on the server or computer I plan on controlling is fine), so if it works off of a flash drive that would be awesome.

logmein has to have a client installed on the computer that needs to be controlled. I am not sure if it can be installed on a flash drive or not. For my uses secure connects aren't too critical b/c i do it for computer maintenance.

---

### Post by Lazy-buntu on 2009-04-13
> **steve101101 said:**
> logmein has to have a client installed on the computer that needs to be controlled. I am not sure if it can be installed on a flash drive or not. For my uses secure connects aren't too critical b/c i do it for computer maintenance.

Oh, so the client just uses the website then?

Still, I don't think it's secure for my purposes. Would tunneling VNC through SSH work efficiently? I.E. wouldn't be very laggy.

---

### Post by steve101101 on 2009-04-13
> **Lazy-buntu said:**
> Oh, so the client just uses the website then?

Still, I don't think it's secure for my purposes. Would tunneling VNC through SSH work efficiently? I.E. wouldn't be very laggy.

the computer you are using to control uses a web client. the computer that is being controlled has a program installed on it.

---

