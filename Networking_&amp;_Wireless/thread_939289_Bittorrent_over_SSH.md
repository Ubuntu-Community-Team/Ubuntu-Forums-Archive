---
title: "Bittorrent over SSH"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by bizso on 2008-10-05
Hi,
I'm behind a university firewall where nearly all ports are blocked. Therefore I've set up a ssh tunnel to my comp at home so that I can bypass the uni firewall and dl with bittorrent. I used mainly these 3 guides to setup the tunnel: [http://freebsdcluster.org/~lasse/sshazureustunnel/](http://freebsdcluster.org/~lasse/sshazureustunnel/) , [http://whalesalad.com/2006/08/27/tunneling-bittorrent-over-ssh/](http://whalesalad.com/2006/08/27/tunneling-bittorrent-over-ssh/) and [http://fosswire.com/2007/09/02/a-very-easy-ssh-proxytunnel/](http://fosswire.com/2007/09/02/a-very-easy-ssh-proxytunnel/) . I'm running Windows on both machines and I used Cygwin to install OpenSSH server at home.

I DDO manage to connect to my cpu at home and also am able to download! (Priorly, I couldn't dl at all). I have been also able to forward port TCP 7654 via SSH to my laptop using this command line in the client terminal: ssh -R 7654:localhost:7654 -A -D 1080 root@serveripathome. I dont use Putty because it randomly crashes on my laptop for some strange reason.

On the ssh server at home I've virtually enabled everything including TCPKeepAlive, AllowTcpForwarding, AllowAgentForwarding and GatewayPorts. I've also configured Azureus to use a proxy.

However, when I test port 7654 I get NAT OK and a green dot in the bottom, but at the same time there are, in fact, no incoming connections at all ever! My download speed is also really pathetic like 5-10kB/s while my upload speed is always at its max....
In the Cygwin terminal window I keep getting these messages every 2 sec: channel 3: open failed: connect failed: connection timed out, channel 4: open failed connect failed: connection refused.... etc

Any help plz?:confused:

---

