---
title: "How do I VNC into my computer using SSH?"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2008-11-15
I currently VNC into my computer remotely using plain old remote desktop preferences built into Ubuntu.  But I would like to know how I might do this in the event I have to access my machine from behind a filtered network that blocks traffic on ports in the 5900 range.

---

### Post by graysky on 2008-11-15
Here's how to do this under two different circumstances:

#1 Windows to LINUX
#2 LINUX to LINUX

The key here is that you have ssh open to the world.  If you can't ssh into your box, you can't do this.  You'll be using ssh tunneling which is a VERY powerful and secure way to connect connect two machines one various ports.  Note: it'll work for anything that runs on the port you select, not just vnc.  I'll give you an example using http as well.

**Windows to LINUX**
If you're connecting from a Windows machine, doing so it trivial with PuTTY.  I'm assuming you have ssh setup and working on your LINUX box.  Also, if your windows machine is outside your LAN, you'll obviously need to have the port that you've used for ssh forwarded to the IP addy of your LINUX box.

Load up PuTTY and create a new or edit an existing session for your LINUX machine setting up the IP addy or hostname (if you have it in your c:\windows\system32\etc\drivers\hosts file).  Gave the session a name and then expand the [color=purple]Connection>SSH>Tunnels[/color] option in PuTTY.

I. For source port, enter a number that you'll be connecting to on your WINDOWS box.  I used 222.

II. For destination, use localhost:5900 since you're using the default 5900 port on your LINUX box.

[img]http://img126.imageshack.us/img126/2639/61568256ei1.gif[/img]

Now save your session and connect.  Once you're into your LINUX box, PuTTY is tunneling (via ssh) connections on the LINUX end from port 5900 to port 222 on your Windows box.

To connect via VNC to the LINUX box, simple point your VNC client on the Windows box to "localhost:222" and the magic begins.  LEAVE THE PUTTY WINDOW OPEN or else the encrypted tunnel will collapse.

This technique is useful for ANY network service on your LINUX box.  For example, http.  

Source port: 10080
Destination: localhost:80

This configuration will securely tunnel port 80 on the LINUX box to port 10080 on your windows box.  Therefore, simply point your windows browser to "http://localhost:10080" and you should have your LINUX box's webroot displayed.

Very cool, no?

**LINUX to LINUX**

Accomplished even easier via a single shell command:

```
$ ssh IP.ADDY.OF.LINUX -l USERNAME -L 222/localhost/5900
```

Again, if you have an entry in your /etc/hosts for your LINUX server, you can use the hostname instead of the IP addy.

So that'll setup the tunnel, now just open your vnc client and again, connect to "localhost:222" and you should be in business.

---

### Post by diablo75 on 2008-11-15
I'd likely be connecting using my Ubuntu laptop to connect to my Ubuntu PC.  But I don't know how to set SSH up on my PC...  :confused:

---

### Post by graysky on 2008-11-15
> **diablo75 said:**
> I'd likely be connecting using my Ubuntu laptop to connect to my Ubuntu PC.  But I don't know how to set SSH up on my PC...  :confused:

:confused:

You have to LINUX boxes right?  Don't both boxes have ssh installed?  On my debian lenny box, # apt-get install ssh did the trick.

---

### Post by Steve1961 on 2008-11-15
sudo apt-get install openssh-server is what you need to run.  Ubuntu has the ssh client installed but not the server package.

---

### Post by Steve1961 on 2008-11-15
there's also a useful page on setting up VNC over ssh here:

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

or if you want something faster than vnc you could also try nomachine's NX.  I wrote a simple how to for that here:

[http://ubuntuforums.org/showthread.php?t=941530&highlight=nomachine](http://ubuntuforums.org/showthread.php?t=941530&highlight=nomachine)

---

### Post by diablo75 on 2008-11-15
> **Steve1961 said:**
> sudo apt-get install openssh-server is what you need to run.

I wish I were a newb so I could more easily hide my embarrasment, but I'll get this down with some more help.

I've installed the above package.... now what?  Does the server automatically start when I turn the computer on?  Or do I have to run it to set up some config?

---

### Post by Steve1961 on 2008-11-15
> **diablo75 said:**
> I wish I were a newb so I could more easily hide my embarrasment, but I'll get this down with some more help.

I've installed the above package.... now what?  Does the server automatically start when I turn the computer on?  Or do I have to run it to set up some config?

:)  It runs after you install it.  Once you've installed it go to another machine and just type:

ssh user@host

where user is your user name and host is the hostname or ip address of the server.  Once you start using ssh you'll wonder how you ever did without it.  You can also just use the places/connect to server menu item, select ssh and it will open nautilus with a view of the server file structure that you can just drag and drop files to.

These Ubuntu wiki pages are good guides:

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

They show how to change the default port and discuss key based authentication.

---

### Post by diablo75 on 2008-11-15
> **Steve1961 said:**
> :)  It runs after you install it.  Once you've installed it go to another machine and just type:

ssh user@host

where user is your user name and host is the hostname or ip address of the server.  Once you start using ssh you'll wonder how you ever did without it.  You can also just use the places/connect to server menu item, select ssh and it will open nautilus with a view of the server file structure that you can just drag and drop files to.

These Ubuntu wiki pages are good guides:

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

They show how to change the default port and discuss key based authentication.

Okay, that sounds simple enough.  What if I'm outside the local network?  I know how to port forward with my router.  What port should I use?  Is SSH server listening on any one port number in particular?

---

### Post by Steve1961 on 2008-11-15
> **diablo75 said:**
> Okay, that sounds simple enough.  What if I'm outside the local network?  I know how to port forward with my router.  What port should I use?  Is SSH server listening on any one port number in particular?

ssh uses tcp port 22 by default so you need to make sure that's open in any firewall software you use and forward that port in your router.  However, if you're going to open up a port to the world you'd be safer changing the default port to something much higher so that you avoid automated attacks.  Something above, say 40000.  You can change the port in /etc/ssh/sshd_config and then just do a sudo /etc/init.d/ssh restart.  You then log in by doing ssh -p 40000 user@host

All the details are in the links so just play around with it to get comfortable

---

### Post by Steve1961 on 2008-11-15
just thought of something else you might find useful.  If like most of us your isp gives you a dynamic ip address using the dyndns service will give you a fixed hostname even if your ip changes.  You can then just ssh to that hostname from anywhere on the internet.  The basic service is free and works really well:

[http://www.dyndns.com/](http://www.dyndns.com/)

---

### Post by diablo75 on 2008-11-15
I've already got a dyndns setup.

Now... what if the network I'm "dialing out" from is filtering its traffic and block non-standard ports?  I'm thinking I'd have to stick with port 22 or even perhaps port-forward 80 from my router to my PC.... is that a bad idea if I use public authentication?  I was just thumbing through one of the linked guides and saw that you can do public key authentication instead of password authentication.  How do you set that up?

---

### Post by Steve1961 on 2008-11-15
> **diablo75 said:**
> I've already got a dyndns setup.

Now... what if the network I'm "dialing out" from is filtering its traffic and block non-standard ports?  I'm thinking I'd have to stick with port 22 or even perhaps port-forward 80 from my router to my PC.... is that a bad idea if I use public authentication?  I was just thumbing through one of the linked guides and saw that you can do public key authentication instead of password authentication.  How do you set that up?

public key authentication plus a non-standard port is the way I do it.  If you follow the guide in that link I sent, you basically create a public/private key pair, copy the public key to the server machine, make sure that it works by sshing to the server.  Then edit sshd_config and turn off password authentication and root logins.  i don't know about the port 80 issue though, doesn't sound right.  Is that the only port you can get out on?  a quick google brought up this link:

[http://www.latenightpc.com/blog/archives/2006/10/11/running-an-ssh-server-on-multiple-ports](http://www.latenightpc.com/blog/archives/2006/10/11/running-an-ssh-server-on-multiple-ports)

---

### Post by diablo75 on 2008-11-15
> **Steve1961 said:**
> Is that the only port you can get out on?

It's too early for me to know so I am just anticipating the possibility of traffic being blocked on all ports except for stuff like HTTP (port 80) and a few others.

---

