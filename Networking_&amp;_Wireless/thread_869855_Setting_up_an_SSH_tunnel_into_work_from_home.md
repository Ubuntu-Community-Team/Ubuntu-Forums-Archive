---
title: "Setting up an SSH tunnel into work from home"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by FBurnaby on 2008-07-25
Hi, I'm an absolute newbie to networking, and I'd just like a few tips...

I have a computer at work (I'll call it 'work') and a computer at home ('home') that I'd like to share files between using scp, and maybe use vnc, as well.
As it stands, In order to log in to my computer at work, I ssh to a serving computer, 'main' (which doesn't belong to me). From there, I can ssh into 'work' and start taking care of business.
At home, my roomates and I are behind a linksys router.

Can anyone offer advice on the best way for me to be able to log in to 'work' from 'home', and into 'home' from 'work'? The best I can do, currently, is to ssh to 'main', scp files from 'work' to 'main' and then again from 'main' to 'home'. I can't seem to ssh to home from work at all, which I think (from my reading) stems from a need for me to forward a port from my computer through the router at home...?

Thanks an advance for any suggestions!

---

### Post by tsfraser on 2008-07-25
If you are just dealing with files then I would recommend that you use sshfs

sudo apt-get install sshfs

then you use it much like the mount command

sshfs workserveraddress:/directory you want to go to/ /directory you want to mount to/


That way you just need to CD to that directory modify the files and they will automatically be put back onto the server.

---

### Post by Endwin on 2008-07-25
Ah ssh tunnels the land of fun, also a little confusing.

Assuming you are running linux, and have ssh server and clients installed. I am also assuming that you can ssh to MAIN and from MAIN ssh into WORK. On WORK there should be a SSH server running.

First we will do HOME -> MAIN -> WORK

We will set up a SSH tunnel using this format at the command line. 
```

ssh <user>@<outside accessible SSH> -L <local port>:<destination on the inside>:Destination port>
```

The setup goes ok SSH to <USER>@<MACHINE I CAN GET TO> and set up a local port to forward data on that port to some internal machine port. In your case you will want something like. 

```
ssh <USER@MAIN -L <local port>:WORK:<Destination port>
```

Now we need to figure out the port situation. Let us assume you want to send VNC through an SSH tunnel. We also have a VNC server running on WORK. VNC default port is 5900 so for this we would run the command.

```
ssh <USER>@MAIN -L 5900:WORK:5900
```

Once it is setup just bring up a VNC client and point to localhost (your machine since that is where we are forwarding the port) at port 5900. You will then be accessing your WORK computer through a SSH connection to MAIN.

Set up a similar thing for SSH file sharing through sshfs as was described above but to access WORK we need to forward a port again in this case. 

```
ssh <USER>@MAIN -L 2222:WORK:22
```

This will forward port 2222 on your local machine to port 22 on your WORK computer through MAIN. All you need to do now for sshfs to work is change the port and the computer you connect to thus...

```
sshfs <USER>@localhost:/<REMOTE DIRECTORY> /<LOCAL DIRECTORY> -p 2222  
``` 

**EDIT:** The above works make sure you use the user name and password for the WORK computer.
 
Now as for WORK -> HOME this can be done with a modification of your firewall on your router to point port 22 to your HOME computer and having SSH server installed on HOME. All you need then is the external IP of the router and you can SSH directly to HOME. Apply the above schema this time just doing something like.

```
ssh <USER>@HOME -L <local port>:localhost:<Destination port>
```

That should do it.

---

