---
title: "ssh frustration"
date: 2015-07-29
forum: Networking &amp; Wireless
---

### Post by cmcanulty on 2015-07-29
can you explain please I am all mixed up on which is which in the commands I want to reach a remote server over wan windows 7 via vnc to the ip:port and do I use my username or the one for the remote server I have putty installed on the win 7 server and have port 22 open have had no luck with ssh tunnels
I can successfully connect with this command and no ssh tunnel

```
cmcanulty@ubuntu1:~$ vncviewer xxx.xxx.xxx.xx:xxxx
VNC Viewer Free Edition 4.1.1 for X - built Nov 18 2014 16:03:02
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Wed Jul 29 11:37:58 2015
 CConn:       connected to host xxx.xxx.xxx.xx port xxxx
 CConnection: Server supports RFB protocol version 3.8
 CConnection: Using RFB protocol version 3.8
Password: 
Wed Jul 29 11:38:11 2015
 TXImage:     Using default colormap and visual, TrueColor, depth 24.
 CConn:       Using pixel format depth 6 (8bpp) rgb222
 CConn:       Using ZRLE encoding

Wed Jul 29 11:38:12 2015
 CConn:       Throughput 2140 kbit/s - changing to full colour
 CConn:       Using pixel format depth 24 (32bpp) little-endian rgb888
cmcanulty@ubuntu1:~$ 
```


but as soon as I try ssh it fails on the same hostname I have putty installed on the remote win 7 but maybe ssh tunnel is wrong I want to see the actual desktop in use not another display I have also tried this in vinagre and remmina

```
cmcanulty@ubuntu1:~$ ssh -p 22 -f -N -L 5900:cmcanulty@ubuntu1:5900 xxx.xxx.xxx.xx:5xxx
ssh: Could not resolve hostname xxx.xxx.xxx.xx:5xxx: Name or service not known
cmcanulty@ubuntu1:~$ ssh -p 22 -f -N -L 5901:cmcanulty@ubuntu1:5901 xxx.xxx.xxx.xx:5xxx
ssh: Could not resolve hostname xxx.xxx.xxx.xx:5xxx: Name or service not known
cmcanulty@ubuntu1:~$ 

```

---

### Post by Lars Noodén on 2015-07-29
It looks like you have the syntax wrong for the tunnel.  If you are tunneling port 5901 and otherwise want to connect to xxx.xxx.xxx.xx with SSH on port 5xxx then it would be more like this:

```

ssh -p *5xxx* -f -N -L 5901:localhost:5901 cmcanulty@xxx.xxx.xxx.xx

```

Substitute 5xxx for the port that OpenSSH-server is listening on.  The default is 22.  The target machine does need to have the package OpenSSH-server installed and running for the connection / tunnel to be made.  Then you can connect the VNC client to display 1 on the localhost and it will really be connecting to xxx.xxx.xxx.xx

After that, turn on the firewall so that VNC cannot be connected directly.   That is rather unsafe to have open these days.

---

### Post by cmcanulty on 2015-07-29
that gets no output, should I use my name or the name of the server admin ie librarian? Also there are 17 computers at the ip I need to reach a particular one. And should I use 5901 or5900 to gete the actual desktop. I opened 5900 on my local router and firewall. The vnc I am trying to reach is 5999, a windows computer running openssh server, putty, and tightvnc server over a WAN. I may have putty set up wrong. I am attaching a screenshot of the putty window for tunneling. The putty is blank now as I have tried so many things I decided to get some more advice on that. I have port 22 open on both routers and firewalls

[ATTACH=CONFIG]263470[/ATTACH]

```
cmcanulty@ubuntu1:~$ ssh -p 22 -f -N -L 5901:localhost:5901 cmcanulty@xxx.xxx.xxx.xx
```

---

### Post by Lars Noodén on 2015-07-29
The above formula should stay quiet once it connects that's what [ssh -f -N](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh.1.html) does.  If you would like to see an interactive connection in conjunction with the tunnel, then leave off the *-f* and *-N*

```
ssh -p 22 -L 5901:localhost:5901 cmcanulty@xxx.xxx.xxx.xx
```[/QUOTE]

That will connect your client running ssh (openssh-client) to the server running sshd (openssh-server).  Both are Ubuntu machines I presume?  I'm not sure how Windows is involved there since it cannot run an SSH server.  

It would be best to close 5900, 5901 and so on at the firewall.  VNC should not be exposed to the wild Internet.  It gets easily taken over.  The tunnel should take care of the VNC connection between the two machines as long as you have port 22 open for SSH.  (I'm not that familiar with PuTTy, having last used it over a decade ago, but from the screenshot the ciphers look a bit dated and perhaps a newer version of PuTTY is needed.)

0.  have OpenSSH-server running on machine B
1.  start the VNC server on machine B
2.  open an SSH tunnel from machine A to machine B
3.  connect the VNC client on machine A to local host (127.0.0.1) on the tunneled port (5900, 5901, etc)

Again, that is based on there being two machines in the chain.

---

### Post by cmcanulty on 2015-07-29
I am connecting to a windows 7 pro machine over a wan through a router that's why I think the putty screenshot may be the issue:
"a windows computer running openssh server, putty, and tightvnc server over a WAN"

---

### Post by Lars Noodén on 2015-07-29
Is the map a bit like this then?

```

+--------+          +--------+   +--------+
|   A    |     B    |    C   |   |   D    |
| Ubuntu +--router--+ Ubuntu +---+ Vista7 |
|        |          |        |   |        |
+--------+          +--------+   +--------+

```

Where the connection between C and D is VNC but everything else is SSH?

---

### Post by cmcanulty on 2015-07-29
no it is client xubuntu 14.04 to router to windows 7 server. I need help with making ssh work both from xubuntu to win 7  server over wan and xubuntu to xubuntu server over wan

---

### Post by Lars Noodén on 2015-07-30
Is A to B is over the WAN (regular Internet), where B has a public address, 
and B to C and B to D is over the LAN, where  C and D have private addresses?

```

                        +--------+
                        |   C    |
                    +---+ Ubuntu |
+--------+          |   |        |
|   A    |     B    |   +--------+
| Ubuntu +--router--+
|        |          |   +--------+
+--------+          |   |   D    |
                    +---+ Vista7 |
                        |        |
                        +--------+

```

In the example in post #1 above, does xxx.xxx.xxx.xx stand for the IP number of B?  If so, are you connecting to B itself or is B forwarding port 22 to C or D?

Either way, both C and D need an SSH server.   PuTTY does not provide that, it provides only a client.  C, being Ubuntu (xubuntu), can have OpenSSH-server.  D, I wouldn't know anything about, but have read that Cygwin could be used to run the SSH server.

---

### Post by cmcanulty on 2015-07-30
no the xxx is the remote computer behind the router and the windows is windows 7.isn't openssh-server  a sshserver?  I have it on all computers.

---

### Post by Lars Noodén on 2015-07-30
In post #3, you indicated success (no output) from 

```
ssh -p 22 -f -N -L 5901:localhost:5901 cmcanulty@xxx.xxx.xxx.xx
```

Does leaving off the -f and -N give you a shell?  If so that will indicate that SSH is working and we can look at the tunneling then.  

```
ssh -p 22 -L 5901:localhost:5901 cmcanulty@xxx.xxx.xxx.xx
```

Can you connect to both target machines by varying the ip address?

---

### Post by cmcanulty on 2015-07-30
what I am still guessing at is do I use the user name and ip of server I am trying to reach or my own user name and ip? or one of each, the above commands did nothing and I still need to somehow reach a computer the ip in xxx etc is the static ip of the library router. I have also set static ips for all the computers behind the router and forwarded specific vnc ports  for each, thank you I really hope we can get this working as otherwise I am using the unsecure vnc for everything

---

### Post by steeldriver on 2015-07-30
If all you are trying to do is connect from Windows to a remote Ubuntu desktop over an SSH-tunneled VNC connection, then the normal way to do that is simply to set up the tunnel via the PuTTY GUI. 

This can be done EITHER at the time the SSH terminal session is established, or later by right-clicking on the edge of the PuTTY window and selecting 'Change settings...' : ***for now, I will assume that you are opening a new session***.

In either case, you need to expand the '+' under the SSH item in PuTTY's configuration pane and find the 'Tunnels' item:

[ATTACH=CONFIG]263498[/ATTACH]

Enter a the port on which the remote VNC server is listening in the 'Destination' box in the form 'localhost:port' (yes it's confusing: 'localhost' in this context is actually the remote host, it's "local" to the far end of the SSH connection). Also remember that if you have forwarded ports across a remote router, the port number may be different from the port number on the actual target machine.

Then enter a port that you are going to point your VNC viewer to on the Windows machine in the 'Source port' box: this can be any free port on the Windows machine (although I usually try to make it the same as the remote port, for simplicity). Press 'Add' to add the tunnel:

[ATTACH=CONFIG]263499[/ATTACH]

Go back to the PuTTY 'Session' pane and click 'Open', just like you are opening a regular (terminal-based) SSH session. The tunnel will be created for you behind the scenes - no need to type anything into the SSH terminal session. fire up your Windows VNC viewer, and point it to 'localhost:sourceport' - this time, 'localhost' does mean your local (i.e. Windows) box:

[ATTACH=CONFIG]263500[/ATTACH]

That should be all that's needed

---

### Post by Lars Noodén on 2015-07-31
> **cmcanulty said:**
> what I am still guessing at is do I use the user name and ip of server I am trying to reach or my own user name and ip? or one of each, the above commands did nothing and I still need to somehow reach a computer the ip in xxx etc is the static ip of the library router. I have also set static ips for all the computers behind the router and forwarded specific vnc ports  for each, thank you I really hope we can get this working as otherwise I am using the unsecure vnc for everything

You would use a login name that is valid on the computer you are trying to reach.  About the ip number of the server you are trying to reach, you would use it if it is not on a private network.  A private network would be 192.168.0.0/16, 172.16.0.0/12, or 10.0.0.0/8.  If the target server is on a private network, you would use the router's ip instead but have it forward SSH to a designated machine on the private network, one running the package OpenSSH-server.  

```

ssh -p 22 -L 5901:localhost:5901 librarian@xxx.xxx.xxx.xx

```

If that gives you a shell on a remote computer then everything else will also be possible.

---

### Post by cmcanulty on 2015-07-31
well as I said the xxx is the router and I don't know how  to forward ssh to  an actual computer, also do I need 5901 open on all routers and fireewalls or can I use 5900? I guess I'm not clear. I am connecting to a windows 7 FROM a xubuntu. so somehow I have to configure putty to accept incoming ssh. I do have open ssh installed on all win and linux computers and port 22 open on all

---

### Post by Lars Noodén on 2015-07-31
> **cmcanulty said:**
> well as I said the xxx is the router and I don't know how  to forward ssh to  an actual computer, also do I need 5901 open on all routers and fireewalls or can I use 5900? I guess I'm not clear I am connecting to a windows 7 FROM a xubuntu. so somehow I have to configure putty to accept incoming ssh. I do have open ssh installed on alll win and linux computers and port 22 open on all

5900 and 5901 and the other 590x ports should be closed on the router, at least closed to access from the outside.  VNC connections from inside to other machines inside is your choice.  The point of the SSH tunnel is that VNC is not available to the outside world.  Only the port for SSH needs to be forwarded from outside to inside.  The VNC connections from outside to inside should be blocked, the tunnel will be used instead.  

Do the machines behind the router have external IP numbers or are the internal (private) ones?  A private IP number would be in the range 10.0.0.0 - 10.255.255.255 or 172.16.0.0 - 172.31.255.255 or 192.168.0.0 - 192.168.255.255.  

And just to double check, you have one Xubuntu machine on the outside of the router and at least one Xubuntu machine behind the router running [OpenSSH-server](http://packages.ubuntu.com/trusty/openssh-server)?

---

### Post by cmcanulty on 2015-07-31
well as I said the xxx is the router and I don't know how  to forward ssh to  an actual computer, also do I need 5901 open on all routers and fireewalls or can I use 5900? I guess I'm not clear I am connecting to a windows 7 FROM a xubuntu. so somehow I have to configure putty to accept incoming ssh. I do have open ssh installed on all win and linux computers and port 22 open on all

---

### Post by Lars Noodén on 2015-07-31
> **cmcanulty said:**
> I do have open ssh installed on all win and linux computers and port 22 open on all

Ok that helps but there are two components to OpenSSH, a client and  a server.  All the target computers will need the server package.  You can find it in the repository under the name *openssh-server* and make sure it is installed on each target.  

Please, make sure the package *openssh-server* is installed on the target computers, at least the Xubuntu ones.  

> **cmcanulty said:**
>  also do I need 5901 open on all routers and fireewalls or can I use 5900? 

Neither, if you are using an SSH tunnel to reach the VNC server on each machine.  
If it is the case that you are going to use an SSH tunnel, then you only need **port 22** for SSH.
With tunneling, the connection visible between the machines will be SSH.  That will be carrying inside it the VNC connection when you start it with a tunnel (-L) 

> **cmcanulty said:**
> well as I said the xxx is the router and I don't know how  to forward ssh to  an actual computer

That depends a little on your network topology and your router. 

Do the target computers have addresses in the **range** 10.0.0.0 - 10.255.255.255 or 172.16.0.0 - 172.31.255.255 or 192.168.0.0 - 192.168.255.255 ?

---

### Post by cmcanulty on 2015-07-31
openssh client and server is on all win and xubuntus

---

### Post by Lars Noodén on 2015-08-01
Great.  From a machine behind the router, can you connect to another machine also behind the router using SSH?

Also, do the machines behind the router have fixed IP addresses or are they getting new ones each time via DHCP?

---

### Post by cmcanulty on 2015-08-17
well I figured out part of the problem I have openssh server installed and ssh as a startup but not openssh as a startup do I need it at start for the local and remote ones? There are a ton of files listed, which one should I use for startup. Also I don't know for remmina ssh tunneling what configuration I need to do on both local and remote computers. I have a bunch of remote ones to do. I can ssh into router and then ssh to a remote but I need the vnc actual desktop so ssh doesn't do enough by itself. I need the remmina ssh tunneling. At some point I always get in a fog between local, remote, client server. Also the remote router is a static ip but my home one isn't though I can use a static ip from no-ip if necessary. Thank you.

---

### Post by Lars Noodén on 2015-08-18
The package openssh-server should be on each remote machine to provide an SSH server, but it runs automatically there once it is installed.  Apparently it is also on the router, which can be used as a stepping stone.

If you can ssh into the router and then ssh to a remote machine, then you can still tunnel to the remote machines.  You just have to make a tunnel at each step, and do it in two steps:

```

ssh -A -L 5900:localhost:5900 routeruser@router.example.com ssh -L 5900:localhost:5900 remoteuser@xx.yy.zz.aa

```

That runs the ssh client to connect to the router and then runs another ssh client on the router itself to connect to xx.yy.zz.aa
When you try it, do you get a shell on the remote machine?

If a VNC server is running on display :****0 then tunnel 5900.  If it is on display :****1 then tunnel 5901, and :****2 is on 5902 and so on.  
The [-A option](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh.1.html) is needed if you are going to use keys to connect to the remote machines but want to keep them on your client instead of copying them to the router.  

The machines behind the router are, in this context, servers since they are running each a VNC server and an SSH server.  And the machine you youself are sitting at is the client.  Yes, it's a bit confusing but it depends on which part one is talking about at the time.  So there are three machines in the connection (aside from the more or less invisible networking), A your desktop (aka the client), B the router, and C the remote machine (aka the server).

---

### Post by cmcanulty on 2015-08-18
OK so I get this error, I have port 5900 open on my home router. I get into the remote router OK with the router password, but can never get beyond it to the local machine which is the 192.168.1.12 or any of the other local ones with the terminal or remmina. I get in fine without ssh tunnel using rdp or vnc in remmina. The first xxx address is the remote router ip.

```
cmcanulty@ubuntu1:~$ ssh -A -L 5900:localhost:5900 librarian@xxx.xxx.xxx.xx ssh -L 5900:localhost:5900 librarian@192.168.1.12
librarian@xxx.xxx.xxx.xx's password: 
bind: Address already in use
channel_setup_fwd_listener: cannot listen to port: 5900
Could not request local forwarding.
```

Same error if I take out the -A

```
cmcanulty@ubuntu1:~$ ssh -L 5900:localhost:5900 librarian@xxx.xxx.xxx.xx ssh -L 5900:localhost:5900 librarian@ 
librarian@xxx.xxx.xxx.xx's password: 
bind: Address already in use
channel_setup_fwd_listener: cannot listen to port: 5900
Could not request local forwarding.
```

I also tried it with the 2nd local port 5901 which is what I have setup for local behind the router 192.168.1.12 vnc port

---

### Post by Lars Noodén on 2015-08-18
If you are tunneling over SSH, no VNC ports need to be opened on the router.  Just SSH allowed in is enough.  The home router's configuration does not need to be changed unless you are connecting to home from away from home.  The work router, if you are connecting that direction, needs allow SSH which you just mentioned it does.  

About the error "bind: Address already in use", you are already forwarding 5900 on that machine. It's hard to tell if that is on the router or your client, without logging in using a more verbose mode.  

If it is your client, then this will also produce the error, and it is a matter of finding the terminal window to the router that is still open and closing it:

```

ssh -A -L 5900:localhost:5900 librarian@xxx.xxx.xxx.xx

```

( Once logged in, make sure it is the router you are logged into and not the remote machine.  

```

uname -mno

```

The machine name and architecture should match the router.  If it matches the remote machine, then you don't need to ssh twice.  )

If it is that does not produce the bind error, then different ports can be used over the router.

---

### Post by cmcanulty on 2015-08-18
Ok that totally confuses me, my local name is cmcanulty the remote user name for the router and remote computer is librarian. I get through the router and the I get the error when I type librarian@192.168.1.12 or any of the other remote computer local ips I don't even get asked for the remote computers password which is different from the router password. I have opened 5900 on my local router and the ufw am I supposed to use 5901 instead?

---

### Post by Lars Noodén on 2015-08-18
> **cmcanulty said:**
> Ok that totally confuses me, my local name is cmcanulty the remote user name for the router and remote computer is librarian. I get through the router and the I get the error when I type librarian@192.168.1.12 or any of the other remote computer local ips I don't even get asked for the remote computers password which is different from the router password. I have opened 5900 on my local router and the ufw am I supposed to use 5901 instead?

Ports 5900, 5901 and so on should stay closed on the remote machines and the router.  It will be SSH moving VNC through the firewall.  

Which of these gives an error?

1.
```

ssh -A mcanulty@xxx.xxx.xxx.xx 'uname -mno'

```

2.
```

ssh -A mcanulty@xxx.xxx.xxx.xx ssh librarian@192.168.1.12 'uname -mno'

```

3.
```

ssh -A -L 5900:localhost:5900 mcanulty@xxx.xxx.xxx.xx ssh librarian@192.168.1.12 'uname -mno'

```

4.
```

ssh -A -L 5900:localhost:5900 mcanulty@xxx.xxx.xxx.xx ssh -L 5900:localhost:5900 librarian@192.168.1.12 'uname -mno'

```

#1 is running uname on the router.  #2 is running uname on the remote host, if it gets through.  #3 is tunneling port 5900 on your machine to the router's port 5900.  #4 is the same as #3 but also carrying it onward to .12's port 5900.

---

### Post by cmcanulty on 2015-08-18
all give permission denied. But I can ssh to the router successfully and from there I can ssh to any remote xubuntu what I can't do is ssh with vnc or rdp

here are the errors

bind: Address already in use
channel_setup_fwd_listener: cannot listen to port: 5900
Could not request local forwarding.
ssh: exited: Error connecting: Connection timed out
cmcanulty@ubuntu1:~$  


bind: Address already in use
channel_setup_fwd_listener: cannot listen to port: 5900
Could not request local forwarding.
ssh: exited: Error connecting: Connection timed out

ASUSWRT RT-AC68U_3.0.0.4 Wed Mar  4 04:45:38 UTC 2015
librarian@(none):/tmp/home/root# ssh 192.168.1.12
ssh: exited: Error connecting: Connection timed out
librarian@(none):/tmp/home/root# 

Permission denied (publickey,password).
cmcanulty@ubuntu1:~$

I think this is the issue I am attaching 2 screenshots of remmina the xxx address is the remote router ip. 2nd screenshot works fine, when I do the 1st screenshot for ssh tunneling it always fails. I have tried my username, librarian username and any other combinations I can think of

---

