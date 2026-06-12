---
title: "VPN connection"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by kriukov on 2008-07-03
I have been struggling to connect to my university's VPN. First I used vpnc, then finally compiled the university's own Linux version of Cisco (had to patch it before). I tried both, from command line and from the network manager plugin. The scenario is the same all the time: it says the connection is successful, and I have no more Internet connection, but neither can I connect to anything inside the VPN! For example, if I do

ssh [login]@[university-server].com

then it says the server is unavailable. However, if I do

ssh [login]@xxx.xxx.xxx.xxx

(meaning the IP address of the server), then it connects and asks for the password, but does not accept it. What can I try to do here? Also, do I have to allow incoming connection from the VPN server? My firewall said it requested incoming connection when I was connecting to the VPN. I allowed incoming connections from the university IP, but it didn't help.

---

### Post by nutsosa on 2008-07-09
Similar problem here.  I was able to connect yesterday, but today, no luck.  I reinstalled vpnc, etc., but again no luck.

Any help would be appreciated.  Thanks :)

---

### Post by kriukov on 2008-07-25
I've been reading the materials on this forum, but I've tried a lot of things and don't have any result. I guess what I am stuck at is routing, DNS and gateway (I don't have experience with networking). Using Network Manager or kvpnc I am able to connect to VPN, but then I can't access it. If I keep the default route (as in kvpnc), ssh refuses to connect as it does with no VPN connection (connection refused); if I replace existing route, it doesn't connect altogether (name or service not known). It is probably an easy step, I don't know. This is a Cisco VPN connection.

---

### Post by jerremy-tamlin on 2008-08-27
I use vpnc from the repositories to connect to Murdoch Uni (Western Australia) and it works appart from a little dificulty I'm currently having with firewall settings.

I can't connect with the firewall up but after I've connected I can put the firewall back again and everything works fine.

Re: Connecting in the first place here is the procedure for my uni:

[LIST]
[*]Install vpnc using synaptic.

[*]create a configuration file: Open a terminal and type 
```
~$ sudo gedit /etc/vpnc/murdoch.conf
```
[*]Paste the following settings into this file

```
IPSec gateway vpn.murdoch.edu.au
IPSec ID mu_stu_wireless
IPSec obfuscated secret *You will have to find out what yours is. If your at murdoch it's [here]("https://wwwcoms.murdoch.edu.au/vpn/download/Student%20Wireless%20(v1.1-11Mar2004).pcf")*
Xauth username yourstudentnumber
```
[*]Start vpnc and enter your murdoch password when prompted.

```
~$ sudo vpnc murdoch.conf
```
[*]Create a secure tunnel to Murdoch Gateway with ssh and enter your password.
(if you do not have ssh installed then install openssh-client with synaptic)

```
~$ sudo ssh yourstudentnumber@gateway.murdoch.edu.au
```
[*]You now connected to the internet. :-) 
[/LIST]

This works at my uni, hope it helps.

---

