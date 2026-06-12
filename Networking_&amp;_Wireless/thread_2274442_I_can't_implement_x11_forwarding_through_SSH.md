---
title: "I can't implement x11 forwarding through SSH"
date: 2015-04-20
forum: Networking &amp; Wireless
---

### Post by peter1897 on 2015-04-20
I have Ubuntu server installed locally on virtual machine and i have Ubuntu server on remote VPS. I am trying to implement X11 forwarding through SSH from the local server to the remote server because i want to run applications with GUI on the remote server. 
I edited the files **ssh_config** and **sshd_config** on both machines to allow X11 forwarding. I used this command to set the display variable on both machines **export DISPLAY=:0**. The echo **$DISPLAY** command return this result **:0**. I have XORG installed on both machines. 

If i try to run application with GUI i get this error: Can't open display
If i run xhost command i get this result:
```
ubuntu@ip-xx-xx-xx-xx:~$ xhostdebug1: client_input_channel_open: ctype x11 rchan 3 win 65536 max 16384
debug1: client_request_x11: request from 127.0.0.1 46527
connect /tmp/.X11-unix/X0: No such file or directory
debug1: failure x11

xhost:  unable to open display "localhost:10.0"
```

If i run the ssh x11 forwarding command in verbose mode from the result it seems to show that it doesn't pass the x11 forwarding:

```
root@ubuntu:~# ssh -X -i privatekey.pem ubuntu@xx.xx.xx.xx -v
OpenSSH_5.3p1 Debian-3ubuntu7, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to xx.xx.xx.xx [xx.xx.xx.xx] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file privatekey.pem type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.6.1p1 Ubuntu-2ubuntu2
debug1: match: OpenSSH_6.6.1p1 Ubuntu-2ubuntu2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu7
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'xx.xx.xx.xx' is known and matches the RSA host key.
debug1: Found key in /root/.ssh/known_hosts:2
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Trying private key: private.pem
debug1: read PEM private key done: type RSA
debug1: Authentication succeeded (publickey).
debug1: channel 0: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
Warning: No xauth data; using fake authentication data for X11 forwarding.
debug1: Requesting X11 forwarding with authentication spoofing.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
Welcome to Ubuntu 14.04.2 LTS (GNU/Linux 3.13.0-48-generic x86_64)
```

I hope someone can help me to fix this because i am not very advanced in lunux.

---

### Post by TheFu on 2015-04-20
Remote X11 over any WAN connection will be painful. That's putting it nicely. It isn't worth your time to trouble shoot this.

Use x2go. Instructions: [http://wiki.x2go.org/doku.php/wiki:repositories:ubuntu](http://wiki.x2go.org/doku.php/wiki:repositories:ubuntu)
There are many reasons to use x2go over X-forwarding, VNC or RDP if you need a remote desktop. It is based on NX and is the most stable of the NX solutions today. Performance is surprising. NX uses ssh - it is built in. It will use existing ssh-key based authentication, so if you already have keys working between the client and server, just load the server and a non-Unity GUI (xfce/lxde are good) on the far machine, and load the x2go client on the local machine (Linux/Windows/OSX), run the client, make connection settings, and connect.

---

### Post by peter1897 on 2015-04-20
Yes, after two days of unsuccessful efforts to create X11 forwarding through ssh i think i will agree that this is a real pain. Well, at least i learn lot of new stuff about Linux that i didn't know, so i don't count my time as wasted.

I will give a try to x2go.

---

### Post by TheFu on 2015-04-20
X/Windows isn't Linux. It is a cross-platform solution.  The key things to know about it are:
* only use on the LAN. WAN is too painful
* alway, always, always use **ssh -X** to do remote X/Windows. It provides a secure tunnel and makes the DISPLAY
* the remote machine sshd_config has to allow x-forwarding, otherwise it will not work.
* setup ssh with keys first.
* for outside the LAN, use NX protocols for remote desktops. NX uses ssh and honors ssh-keys for authentation, shares the same port that ssh is using.  Of course, you must open a port on the WAN side of the router to allow ssh inbound connections. Securing ssh is important. DO NOT ALLOW PASSWORDS and install fail2ban (or equiv).

---

### Post by The Cog on 2015-04-20
I think that maybe your trying to do the forwarding manually (with exporting display IDs etc) has broken the normal ssh -X working. I'm pretty sure that ssh -X uses displays other than :0. I also know that on a default install of openssh-server on Ubuntu, you can ssh -X to it straight away, no messing needed on the server. It may be worth undoing all the custom configuration you did for the manual ssh forwarding and then just trying ssh -X again.

---

### Post by steeldriver on 2015-04-20
How are you starting the X server on the local machine? I don't see any mention of that in your post

---

### Post by TheFu on 2015-04-20
> **steeldriver said:**
> How are you starting the X server on the local machine? I don't see any mention of that in your post

He's trying to do this over a WAN connection. Remote X11 performance over a WAN link sucks. Truly not worth the effort to get working.  NX is the tool needed for this, IMHO. **x2go** is the easiest/best of that type of remote desktop tool. All the other option are at least 2x slower and X11 will be 10-100x slower. 

I think we call all agree on this.

---

