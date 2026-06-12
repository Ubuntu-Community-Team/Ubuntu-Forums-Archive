---
title: "svn port 3690 issue"
date: 2014-03-29
forum: Networking &amp; Wireless
---

### Post by cyclingchap on 2014-03-29
More problems :(.

I'm trying to connect to a server computer on my LAN and checkout a repository on the server to my client computers.

I'm using Kdesvn.

I'm entering svn://10.0.0.4/Projects/repo as the checkout URL and getting: "can't connect to host '10.0.0.4': connection refused".

On entering "nmap -sT -r -n -vv -p 3690 10.0.0.4" I'm getting: " 3690/tcp closed svn" on the the server and client computers.

Do I need to open this 3690 port on both machines somehow?

I'm trying: " sudo iptables -I INPUT -p tcp --dport 3690 --syn -j ACCEPT" which seems to be doing nothing at all, even after logging out and back in.

When I try:  "nc -zv 10.0.0.4 3690" on the server machine (ip 10.0.0.4) I get:

"nc: connect to 10.0.0.4 port 3690 (tcp) failed: Connection refused".  Ditto for the client machines.

I have switched off the UFW firewall completely on both machines .. until I get it working and understand what's going on.

Can anyone help?

---

### Post by apohal9 on 2014-03-29
Any entries in /etc/hosts.allow or /etc/hosts.deny?

So with iptables flushed and policy set to ACCEPT it works?

---

### Post by cyclingchap on 2014-03-29
Sorry, I have no experience of these hosts.allow and hosts.deny files. Can you explain what they do? Are you saying I should edit them on my server machine to add an entry for the local client machine that's trying to communicate?

If so, how do I do that?

Currently there are no entries in either file.

---

### Post by apohal9 on 2014-03-29
You're right. With both files you can limit access to services on your system. But if both are empty, they cannot be the cause.  As I asked: if you stop ufw the connect works? Or doesn't it work no matter if iptables rules loaded or not?  First of all: is the svn service on your server really running?

---

### Post by cyclingchap on 2014-03-29
OK.

I have solved this. Just ignorance on my part!

To open a port on 3690 for svn repository access over a LAN you need to run a svn server program called "svnserve". For example:

"svnserve -d --foreground -r Temp/Repo"

This opens the 3690 port and listens for any svn communications (i.e. requests to check out repos).

You can set up any one computer on your LAN to act as an svn server. It's a bit like having a computer on your LAN act as a SSH server by running openssh-server, which would then open up port 22.

Apparantly you can combine the svn+ssh communication for more secure access to your repos from outside your LAN, but you have to set up port forwarding (presumably on SSH channel 22). And of course you'd have to set up your firewall on the server computer accordingly.

I like this idea, but you would have to make sure your server machine is on when you plan to access it (of course).

---

### Post by steeldriver on 2014-03-29
I'm not sure you can just connect to a remote svn repository like that - even though the port is shown, afaik svn doesn't really 'listen' as an external service without additional software. The usual way would be via svn+ssh (although you could also set up a web-based interface using webdav)

```

$ sudo nmap -p 3690 192.168.1.127

Starting Nmap 5.21 ( http://nmap.org ) at 2014-03-29 20:01 EDT
Nmap scan report for 192.168.1.127
Host is up (0.00064s latency).
PORT     STATE  SERVICE
[B]3690/tcp closed svn
[/B]$ 
$ svn list **svn://**steeldriver@192.168.1.127/svn/myrepo
[B]svn: Can't connect to host '192.168.1.127': Connection refused
[/B]$ 
$ 
$ svn list **svn+ssh://**steeldriver@192.168.1.127/svn/myrepo
steeldriver@192.168.1.127's password:
svnserve: warning: cannot set LC_CTYPE locale
svnserve: warning: environment variable LANG is en_CA.UTF-8
svnserve: warning: please check that your locale name is correct
**svn: No repository found in 'svn+ssh://steeldriver@192.168.1.127/svn/myrepo'**

```

EDIT: OK so our posts crossed - you can set up svnserve if you prefer (I've always just used svn+ssh)

---

### Post by cyclingchap on 2014-03-29
Oh, OK.

Are you saying that if you use svn+ssh you don't need to run svnserve? Presumably you just run openssh-serve and go through port 22?

The example you give is not working because you actually have no repo at 
[B]steeldriver@192.168.1.127/svn/myrepo

[/B]not because the connections being refused, right?

---

### Post by steeldriver on 2014-03-29
Yes that's right, it should just work provided you have openssh-server set up on port 22 the remote machine. If you are using a non-default port you just need to modify the [Tunnels] section of your ~/.subversion/config file (on the local machine).

---

