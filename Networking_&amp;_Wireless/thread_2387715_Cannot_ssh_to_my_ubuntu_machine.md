---
title: "Cannot ssh to my ubuntu machine"
date: 2018-03-22
forum: Networking &amp; Wireless
---

### Post by kulbear on 2018-03-22
Hi all,

I am a newcomer to Ubuntu. I'll keep updating the post upon request.
My desktop runs Ubuntu Desktop 16.04.

Yesterday, I tried to setup my desktop as a Jupyter Notebook server and I can access it from my mac (I'm more familiar with the mac keyboard somehow..)

When I was at home, I can easily ssh to it with no pain by 

`ssh -N -f -L localhost:8888:localhost:8889 kul@LocalIPV4`

where localhost:8889 is my local notebook server and localhost:8888 is the address I want to use on my mac. And the LocalIPV4 is my public IP address, I intentionally hide it here.

Today when I go to my office and I tried to ssh to my home desktop, I keep receiving 

$ ssh -N -f -L localhost:8888:localhost:8889 kul@LocalIPV4
ssh: connect to host LocalIPV4 port 22: Operation timed out 

I have tried to disable my firewall on Port 22. But it doesn't help.

Is there any suggestion for solving this problem? I have checked several other post streams on the forum and AskUbuntu, but things just don't work.

Thank you in advance.

---

### Post by ank2 on 2018-03-22
Do you have nmap or other means to scan your (first, directly connected to your router) machine for an open port 22? You need to scan your public address from outside your home network. If that fails to show open there is the problem.

---

### Post by kulbear on 2018-03-22
I googled what is my ip address and it gives me my IPV4 public address.

---

### Post by ank2 on 2018-03-22
Well you need to scan that from the outside. If you have a portable Linux machine, install nmap. Go to Starbucks ;-) Well any other place than yours which hopefully doesn't block port 22 outbound. In a shell do

nmap -p 22 what_ever_your_public_IP_is

That'll only scan port 22. If it says "filtered" it's likely your router is blocking it. Do a port forwarding then.

---

### Post by kulbear on 2018-03-22
Hi, it shows

~ nmap -p 22 ipipipip
Starting Nmap 7.70 ( [https://nmap.org](https://nmap.org) ) at 2018-03-22 14:17 MDT
Note: Host seems down. If it is really up, but blocking our ping probes, try -Pn
Nmap done: 1 IP address (0 hosts up) scanned in 3.32 seconds

I'm sure it's up since I can teamviewer to it.

---

### Post by ank2 on 2018-03-22
Try

nmap -p 22 -P0  [COLOR=#000000]ipipipip[/COLOR]

---

### Post by kulbear on 2018-03-22
I think it is filtered then. As mentioned by you in a previous reply. But how could I solve it? 

nmap -p 22 -P0 137.186.144.247
Starting Nmap 7.70 ( [https://nmap.org](https://nmap.org) ) at 2018-03-22 20:58 MDT
Nmap scan report for d137-186-144-247.abhsia.telus.net (137.186.144.247)
Host is up.


PORT STATE SERVICE
22/tcp filtered ssh


Nmap done: 1 IP address (1 host up) scanned in 2.45 seconds

I have tried

`sudo ufw allow 22`

and 

`sudo ufw disable`

After a reboot, I checked ufw with

`ufw status`

and it returned "Status: inactive"

---

### Post by ank2 on 2018-03-23
> **kulbear said:**
> I think it is filtered then. As mentioned by you in a previous reply. But how could I solve it? 

nmap -p 22 -P0 137.186.144.247
Starting Nmap 7.70 ( [https://nmap.org](https://nmap.org) ) at 2018-03-22 20:58 MDT
Nmap scan report for d137-186-144-247.abhsia.telus.net (137.186.144.247)
Host is up.


PORT STATE SERVICE
22/tcp filtered ssh


Nmap done: 1 IP address (1 host up) scanned in 2.45 seconds

I have tried

`sudo ufw allow 22`

and 

`sudo ufw disable`

After a reboot, I checked ufw with

`ufw status`

and it returned "Status: inactive"

I suppose your router is firewalling you. You need to set up port forwarding there, not in Linux itself. Once done, port scan yourself again to verify the port is open now.

---

### Post by Hadaka on 2018-03-23
Hi, some things to check...
```
ssh localhost
```
#Are you entering 'exit 0' to close ?
can you...local area network LAN
#Example
```
ssh -p22 hostname@local_ip
ssh -p22 kulbear@192.168.1.155
```

#Is port 22 present ?
# What ports, IPs and protocols we listen for
```
[COLOR=#000000]cat /etc/ssh/sshd_config | grep -iA4 ports[/COLOR]
```

#Access from outside the LAN
#Is port 22 forwarded to the local ip in the router for off net access ?
#port forward port 22 --> 192.168.1.155
```
ssh -p22 hostname@public_ip
ssh -p22 kulbear@97.134.63.128
```
Please let us know the results.

---

### Post by ank2 on 2018-03-23
> **Hadaka said:**
> Hi, some things to check...
```
ssh localhost
```
#Are you entering 'exit 0' to close ?
can you...local area network LAN
#Example
```
ssh -p22 hostname@local_ip
ssh -p22 kulbear@192.168.1.155
```

#Is port 22 present ?
# What ports, IPs and protocols we listen for
```
[COLOR=#000000]cat /etc/ssh/sshd_config | grep -iA4 "What ports"[/COLOR]
```

#Access from outside the LAN
#Is port 22 forwarded to the local ip in the router for off net access ?
#port forward port 22 --> 192.168.1.155
```
ssh -p22 hostname@public_ip
ssh -p22 kulbear@97.134.63.128
```
Please let us know the results.

It is not aLinux thing in my opinion. He says a port scan from outside the router reports "[COLOR=#000000]filtered". If there would be a problem with SSH itself it would report "closed". Most likely the router has no port forwarding activated. Something like [/COLOR]https://www.wikihow.com/Set-Up-Port-Forwarding-on-a-Router might help.

---

### Post by kulbear on 2018-03-26
> **Hadaka said:**
> Hi, some things to check...
```
ssh localhost
```
#Are you entering 'exit 0' to close ?
can you...local area network LAN
#Example
```
ssh -p22 hostname@local_ip
ssh -p22 kulbear@192.168.1.155
```

#Is port 22 present ?
# What ports, IPs and protocols we listen for
```
[COLOR=#000000]cat /etc/ssh/sshd_config | grep -iA4 ports[/COLOR]
```

#Access from outside the LAN
#Is port 22 forwarded to the local ip in the router for off net access ?
#port forward port 22 --> 192.168.1.155
```
ssh -p22 hostname@public_ip
ssh -p22 kulbear@97.134.63.128
```
Please let us know the results.

```
(dl) &#10140;  ~ ssh localhostThe authenticity of host 'localhost (127.0.0.1)' can't be established.
ECDSA key fingerprint is SHA256:Dsi8jXQBir3yIhm1x3niQRq3Sp7QseocLRSjU3wWM/w.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'localhost' (ECDSA) to the list of known hosts.
kul@localhost's password: 
Welcome to Ubuntu 16.04.4 LTS (GNU/Linux 4.13.0-37-generic x86_64)


 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage


0 packages can be updated.
0 updates are security updates.


Last login: Thu Mar 22 10:49:02 2018
(dl) &#10140;  ~ exit 0
Connection to localhost closed.

(dl) &#10140;  ~ cat /etc/ssh/sshd_config | grep -iA4 ports
# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0




```

I also tried to use another mac under the same router to ssh to the ubuntu machine, there is no problem.
I'm using [http://ip4.me/](http://ip4.me/) to check my IP address since on my ubuntu machine I can only see my IPv6.

I think the problem could be a sharing IPv4? When I check the IP address with my mac, it also shows the exact same IPv4 as my Ubuntu did. 

Then I switch to another router, and also my cell phone hotspot, and I tried to ssh to my ubuntu machine, it always said Port 22: connection timed out.

---

