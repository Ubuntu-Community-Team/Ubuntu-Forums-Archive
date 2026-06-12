---
title: "OpenVPN and SSH"
date: 2014-01-10
forum: Networking &amp; Wireless
---

### Post by klausmcm on 2014-01-10
I would like to be able to ssh into my ubuntu server using the IP assigned to me by my ISP. The server is also running openvpn through which I direct several programs by specifying the interface in the program configuration. Before I start openvpn, connecting to this server using my IP works (locally and from other networks). The problem starts when I run openvpn and connecting to my server using the same IP (ISP assigned) no longer works.
The interfaces displayed by ifconfig are
eth0 (IP 192.168.1.10/24)
lo
tun0 (when openvpn is started)

I have set up port forwarding in my router (port 22 gets directed to 192.168.1.10) and these are the settings I use with openvpn

```
client
dev tun
proto udp
remote ca.privateinternetaccess.com 1194
resolv-retry infinite
nobind
persist-key
persist-tun
ca /etc/openvpn/ca.crt
tls-client
remote-cert-tls server
auth-user-pass ./vpnlogin.txt
comp-lzo
verb 1
reneg-sec 0
auth-nocache
```

Please help me figure out how I can continue having a VPN connection but ssh using my real IP.

---

### Post by TheFu on 2014-01-10
Reading the post, it seems that both openvpn and sshd are listening on port 22, is that the intent?
Also, to connect to a remote server via ssh, your router doesn't need any ports open for inbound connections.

At my VPS, getting ssh to work requires faxing a government ID, then they open the server up on a non-standard port with keys only. Never password-based logins.  Your VPS might not require that, but ... something else to check.  Usually there will be a how-to guide on the VPS with step-by-step instructions.

Hope this helps.

---

### Post by klausmcm on 2014-01-10
> **TheFu said:**
> Reading the post, it seems that both openvpn and sshd are listening on port 22, is that the intent?
Also, to connect to a remote server via ssh, your router doesn't need any ports open for inbound connections.

At my VPS, getting ssh to work requires faxing a government ID, then they open the server up on a non-standard port with keys only. Never password-based logins.  Your VPS might not require that, but ... something else to check.  Usually there will be a how-to guide on the VPS with step-by-step instructions.

Hope this helps.

I was under the impression that this entry

```
remote ca.privateinternetaccess.com 1194
```

assigns openvpn to port 1194. Is the default port for openvpn 22?

Are you sure I don't have to forward port 22 so that the router knows which ssh server I am connecting to? I believe this is required when I connect to the server over the internet which I do.

---

### Post by TheFu on 2014-01-10
> **klausmcm said:**
> I was under the impression that this entry

```
remote ca.privateinternetaccess.com 1194
```

assigns openvpn to port 1194. Is the default port for openvpn 22?



Are you sure I don't have to forward port 22 so that the router knows which ssh server I am connecting to? I believe this is required when I connect to the server over the internet which I do.

Isn't the "remote" line on the client side?  The client doesn't tell the server which port to listen on. Only the server has that control. The client port will need to match whatever the server has.

Port 22 is the default for sshd (the server) to listen, but it is common for an VPS or web host to put that on a non-standard port since every client might want a port.  They may listen on port 22 on the server itself, but use port translation at their edge router to translate a different port to that.

As to opening router ports, yes, I'm positive. Only the system running the sshd process, i.e. the server, needs ports forwarded.  On most every VPS, those will be handled already and are outside your control. If you are at home and using ssh to a remote VPS server then your home router doesn't need any inbound ports opened. It works just like every other client/server method.  To use a web browser, do you have to open inbound ports on your home router? Nope.  Same for ssh clients connecting to remote servers.

---

