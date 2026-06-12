---
title: "OpenVPN stuck at systemd-tty-ask-password-agent"
date: 2017-08-03
forum: Networking &amp; Wireless
---

### Post by neuman1812 on 2017-08-03
trying to start openvpn and I keep getting this:

```
Broadcast message from root@Media (Thu 2017-08-03 07:28:29 EDT):

Password entry required for 'Enter Auth Password:' (PID 31285).
Please enter password with the systemd-tty-ask-password-agent tool!

```

If I keep the openvpn process running I can type in that command, but whatever i put into the username it takes, then does nothing...it just drops me back to the terminal line. If I put the in the command again, it asks for a password and again..takes anything I put in it and does nothing.

If I stop the openvpn process at this point and try the command, it does nothing..it wont ask me for anything.

---

### Post by TheFu on 2017-08-03
Provide credentials via the config file.
**auth-user-pass /etc/openvpn/login.cf** Be certain that only authorized users can view the file.
in the .ovpn file is what I use.  There is another **auth** setting that needs to be removed from the config too. I don't remember what it is. Sorry.

---

### Post by neuman1812 on 2017-08-03
This is my .conf file minus my vpn info..  I have the login.txt with my vpn credential in it.

```
client
dev tun
proto tcp
remote ***
resolv-retry infinite
nobind
persist-key
persist-tun
cipher aes-128-cbc
auth sha1
tls-client
remote-cert-tls server
auth-user-pass /etc/openvpn/login.txt
auth-nocache
comp-lzo
verb 1
reneg-sec 0
ca /etc/openvpn/ca.crt
disable-occ
script-security 2
route-noexec

```

---

