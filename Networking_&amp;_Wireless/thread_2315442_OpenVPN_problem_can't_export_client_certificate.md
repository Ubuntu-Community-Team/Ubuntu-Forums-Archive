---
title: "OpenVPN problem: can't export client certificate"
date: 2016-02-28
forum: Networking &amp; Wireless
---

### Post by spacer.x-infinity on 2016-02-28
Alright, here's my situation:

Server machine: Toshiba Satellite L500 running a hard install of Kubuntu 14.04
Client machine:  Samsung 305V4A with a Windows 7 Home Premium host and a Kubuntu 14.04 VirtualBox VM.

I'm trying to set up a VPN that connects both the Toshiba and the VM on a single secure network. With the help of this tutorial [here]("http://ubuntuforums.org/newthread.php?do=newthread&f=336"), I've already managed to get the server side up and running. As suggested by the tutorial, I've done this mostly from within *root#* and, being the newbie that I am, I'm feeling quite pleased with myself that I haven't royally screwed anything up yet. ;) However, the difficulty mentioned in the thread title arises when I try to export the client certificate and other associated files over to the VM. Again, as suggested by the tutorial, I've zipped the following files into an archive that I called *VPN_archive.zip*:

```

/etc/openvpn/easy-rsa/keys/ca.crt

 /etc/openvpn/easy-rsa/keys/MyVPN.crt

 /etc/openvpn/easy-rsa/keys/MyVPN.key

```

I then tried to export it over to the VM client with the command:

```
scp VPN_archive.zip *<IP address>*
```

When I hit enter, I'm not given any indication about whether the transfer took place. A fresh command prompt just comes up and that's pretty much the end of it. This wouldn't seem all that odd considering that I have public key authentication enacted on SSH, except for the fact that my private key is password protected and I would have thought I'd have to enter it when running *scp.* And, when I look on the home directory of the VM, the *VPN_archive.zip* file is nowhere to be found. 

So here's my first question: did the transfer actually take place and I just don't know where to find the file or did it *not* take place and I need to use a different command in order to export it?

An instruction manual on Ubuntu that I'm reading suggested this command to transfer a file on to a specified directory (in this case, */etc/openvpn*) on the remote machine:

```
scp VPN_archive.zip *<IP address>*:subdir/etc/openvpn
```

 However, when I run this command, I get the following error message:

```

ssh: connect to host *<IP address>* port 22: No route to host
lost connection

```

I acknowledge that I may have messed up the syntax on either or both of these commands. If that's the case, could someone please set me straight? If it *isn't* the case, could someone please tell me what else I might be doing wrong? Is there another command I should use instead? Have I just not looked in the right place for the *VPN_archive.zip* file on the VM client? If not, where else should I look? Speaking of which, I've noticed that this is the only file in the */etc/openvpn//easy-rsa/keys/* directory that appears in **[COLOR=#ff0000]red[/COLOR]** when logged in as *root#*. Is this in any way significant? I've copied files using *scp* before and have never had a problem finding them on the remote machine. If someone could help me figure out where I'm going wrong, I'd really appreciate it.

---

### Post by spacer.x-infinity on 2016-02-29
After doing some research online, it seems to be a combination of improper iptables rules and IP routing rules that are preventing me from connecting to SSH via OpenVPN. At the suggestion of [this article]("http://arashmilani.com/post?id=53"), I've added the following rules to iptables with no success:

```

iptables -A INPUT -i eth0 -m state --state NEW -p udp --dport 1194 -j ACCEPT
iptables -A INPUT -i tun+ -j ACCEPT
iptables -A FORWARD -i tun+ -j ACCEPT 
iptables -A FORWARD -i tun+ -o eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT 
iptables -A FORWARD -i eth0 -o tun+ -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -t nat -A POSTROUTING -s 10.8.0.2 -o eth0 -j MASQUERADE

```

In addition, I've also followed all of the directions  [here]("http://serverfault.com/questions/425493/anonymizing-openvpn-allow-ssh-access-to-internal-server") in an effort to reroute SSH traffic through eth0 but got stuck on this command:

```
ip route add default via YOUR.GATEWAY.IP.HERE dev eth0 table novpn
```

When I ran it with my own gateway IP, the output was:

 ```
RTNETLINK answers: Network is unreachable
```

I am honestly at a loss here and feel quite out of my depth. I'm hoping that this latest post might provide some intelligent person with the additional information they need to help with a solution. If that person is you, I'm ready and willing to learn.

---

