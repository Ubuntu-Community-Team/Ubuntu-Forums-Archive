---
title: "How to remotely log into Ubuntu desktop ?"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by bodycorp on 2009-05-24
Hello .... In the Ubuntu 9.04 Jaunty desktop edition, menu "Administration" , "Logon Window" a tab exists labelled "remote"  i.e. specifying preferences for a remote login. But how does one remotely log in to an Ubuntu desktop session ?    I realise that I can use "Applications", "Internet", "Remote Desktop Viewer" (or VNC from windows) to see and control the desktop of another ("remote") Ubuntu machine , but that is just piggy backing on a session or log-in which exists already  .. it is not a log-in to a remote machine but rather just a looking at its desktop ... So my question is , how do I remotely log on to an other remote machine ?

many thanks .. Colin

---

### Post by Kareeser on 2009-05-24
If you are looking for the functionality of Windows "Remote Desktop Protocol", that technology is proprietary, and has not been duplicated flawlessly onto Linux.

From what I read just now, XDMCP might be a viable alternative - executing a login session on a server (the host), and piping the graphical output to your client connection.

This may help: [http://ubuntuguide.org/wiki/Ubuntu:Feisty/RemoteAccess](http://ubuntuguide.org/wiki/Ubuntu:Feisty/RemoteAccess)

---

### Post by issih on 2009-05-24
You can log in via a terminal (i.e. via ssh forwarded to your ubuntu box with openssh server installed), and then use that terminal to start a vncserver for that user, which you then tunnel through the ssh connection...this gives you a secure remote connection without ever needing an existing session to be running on the box.

Hope that helps.

---

### Post by chiru.infy on 2009-06-25
bump,,

I am also looking for a similar solution

---

### Post by bodhi.zazen on 2009-06-25
What do you want to do ?

You can log on with ssh.

If you want a graphical interface use a VNC server. Now there are some differences between vnc servers. The default, as well as x11vnc, all share one X session. 

vnc4server will start a new session.

You should take great care with VNC and consider tunneling over ssh.

---

### Post by ricardisimo on 2009-06-26
There's something I do not appear to be getting about vinagre. I set up my computer at home to "allow others to control your desktop", with the password proviso. It gave me an address where my desktop could be located (a series of numbers, comma, my-desktop-name.local. I jotted down all of this information, but I have no idea how to enter it.

I've tried entering all of it, then just the numbers, then just my desktop name, desktop-name.local, etc., etc. Nothing. What am I not getting?

---

### Post by ricardisimo on 2009-06-26
Well, I may have figured out one way to do it:
```
vinagre 192.168.blah.blahblah
```
I at least get a black screen, with some network activity taking place, although I never got a request for a password, and after about five minutes I got notice that the connection was shut down. Any clue what's going on?

---

### Post by bodhi.zazen on 2009-06-26
Usually you need to specify a port with vnc clients (I know, it is a pain).

vnc server:5900

```
vinagre 192.168.blah.blahblah:5900
```

---

### Post by ricardisimo on 2009-06-27
No luck, although I am able to remotely log onto the very computer I am on at any moment, which is weird.

Maybe I'm missing a basic element here: Do both computers have to be connected to the same network? They definitely are not in my case.

---

### Post by bodhi.zazen on 2009-06-27
> **ricardisimo said:**
> No luck, although I am able to remotely log onto the very computer I am on at any moment, which is weird.

Maybe I'm missing a basic element here: Do both computers have to be connected to the same network? They definitely are not in my case.

Yes, or you need to forward the vnc port (5900)

---

### Post by ricardisimo on 2009-06-29
> Yes, or you need to forward the vnc port (5900) 
Firstly, how is that done? Secondly, is it safe and secure to do so?

---

### Post by nhasian on 2009-06-29
yes, its safe to forward ports.  you must open the port in your router and forward it to the ip address of the computer your trying to reach.  for more info see:

[http://portforward.com/](http://portforward.com/)

I have ports open in my router for remote desktop, ssh, xboxlive, bittorrent, hellanzb, just to name a few.

---

### Post by ricardisimo on 2009-06-29
Which program do I choose? VNC? Remote Desktop? Ultimately, I'd like to be able to transfer files from my work computer to my home. That's going to be 99% of what I do, if not all of it. I can still just burn a bunch of data DVDs to do this, but I thought vinagre might be convenient.

---

### Post by scrooge_74 on 2009-06-29
But if you only plan to transfer files you can do that using ssh from command line.

scp name_of_file user@target:/home/user/path_to_new_location

You need to forward the ssh port in the home router for this to work

---

### Post by ricardisimo on 2009-06-29
In other words, run all of this from work and send, not from home retrieving?

Something like this:
```
scp salmahayek.jpg ricardisimo@work-desktop:/home/ricardisimo/Desktop
```
It seems a tad too simple. Obviously I've a ways to go towards understanding all of this.

---

### Post by scrooge_74 on 2009-06-29
You can also retrieve it from home just do it the way around

scp user@somewhere:/home/user/name_of_file /home/user/target_destination

If the remote machine has the ssh server installed it will ask for the pass and fetch the file (You also need to have the ssh port forwarded on that router)

[This]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch17_:_Secure_Remote_Logins_and_File_Copying") should put you in the right course

---

### Post by Ad88Ab99 on 2009-06-29
> **bodycorp said:**
> Hello .... In the Ubuntu 9.04 Jaunty desktop edition, menu "Administration" , "Logon Window" a tab exists labelled "remote"  i.e. specifying preferences for a remote login. But how does one remotely log in to an Ubuntu desktop session ?    I realise that I can use "Applications", "Internet", "Remote Desktop Viewer" (or VNC from windows) to see and control the desktop of another ("remote") Ubuntu machine , but that is just piggy backing on a session or log-in which exists already  .. it is not a log-in to a remote machine but rather just a looking at its desktop ... So my question is , how do I remotely log on to an other remote machine ?

many thanks .. Colin
Go to System>Prefrences>Remote Desktop

---

### Post by Ad88Ab99 on 2009-06-29
there is always a risk in logging in remotely, however if u don't tell anybody your password u should be fine

---

