---
title: "ssh with vpn via AnyConnect"
date: 2014-03-17
forum: Networking &amp; Wireless
---

### Post by buntu_hugenewbie11 on 2014-03-17
I am trying to ssh via vpn to a remote (LAMP) server.
I am using kubuntu 12.04 64bit.
My institution uses Cisco AnyConnect and I can connect through the AnyConnect client (GUI).
Once I am connected with the client I try to ssh to the server on that network using the terminal.
The terminal just hangs until the remote server disconnects me.
I have no idea why it won't connect properly. It seems to see the machine and connect but then just hangs.
Please help.

The ssh -vv response is below:
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 164.76.xxx.xx [164.76.xxx.xx] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/id_rsa type -1
debug1: identity file /root/.ssh/id_rsa-cert type -1
debug1: identity file /root/.ssh/id_dsa type -1
debug1: identity file /root/.ssh/id_dsa-cert type -1
debug1: identity file /root/.ssh/id_ecdsa type -1
debug1: identity file /root/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu7
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu7 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1.1
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: [email]ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com[/email],ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-ctr hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP

---

### Post by TheFu on 2014-03-17
Please post the IPs for the client, the server and the VPN IPs for the client.

---

### Post by buntu_hugenewbie11 on 2014-03-17
The server: 164.76.232.10 which is behind a firewall hence the vpn use.
Client: 98.209.83.157
VPN Client: 164.76.27.14
VPN Server: 164.76.25.2

---

### Post by TheFu on 2014-03-17
Thanks.  I asked just to see if you were trying to break any split-tunnel rules. Looks fine.
So - does the ssh server restrict connections from any subnets?  Check the /etc/ssh/sshd_config on that machine and the /etc/hosts.deny and /etc/hosts.allow.

Thanks.  I asked just to see if you were trying to break any split-tunnel rules. Looks fine.
So - does the ssh server restrict connections from any subnets?  Check the /etc/ssh/sshd_config on that machine and the /etc/hosts.deny and /etc/hosts.allow.

Can you run an nmap from the client to the server over the VPN?
```
sudo nmap -sT 164.76.232.10
```

Checking that the routing is setup correctly through the VPN is worth a look.
```
route
```

---

### Post by buntu_hugenewbie11 on 2014-03-17
I currently do not have access to the server. But it does not have any restrictions to my knowledge. Also, I have a colleague who can access it remotely via a windows client on the other side of the country.
Nmap:
Nmap scan report for 164.76.232.10
Host is up (0.030s latency).
Not shown: 996 closed ports
PORT   STATE SERVICE
21/tcp open  ftp
22/tcp open  ssh
53/tcp open  domain
80/tcp open  http

Nmap done: 1 IP address (1 host up) scanned in 3.64 seconds
-----------------------------------------------------------------------------------------------
As for the ip table:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         *               0.0.0.0         U     0      0        0 cscotun0
default         192.168.1.1     0.0.0.0         UG    256    0        0 wlan0
vpn-pri.emich.e 192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0
164.76.26.0     *               255.255.254.0   U     0      0        0 cscotun0
192.168.1.1     *               255.255.255.255 UH    0      0        0 wlan0

---

### Post by TheFu on 2014-03-17
> **buntu_hugenewbie11 said:**
> I currently do not have access to the server. But it does not have any restrictions to my knowledge. Also, I have a colleague who can access it remotely via a windows client on the other side of the country.
Nmap:
```
Nmap scan report for 164.76.232.10
Host is up (0.030s latency).
Not shown: 996 closed ports
PORT   STATE SERVICE
21/tcp open  ftp
22/tcp open  ssh
53/tcp open  domain
80/tcp open  http

Nmap done: 1 IP address (1 host up) scanned in 3.64 seconds
```
-----------------------------------------------------------------------------------------------
As for the ip table:
Kernel IP routing table
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         *               0.0.0.0         U     0      0        0 cscotun0
default         192.168.1.1     0.0.0.0         UG    256    0        0 wlan0
vpn-pri.emich.e 192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0
164.76.26.0     *               255.255.254.0   U     0      0        0 cscotun0
192.168.1.1     *               255.255.255.255 UH    0      0        0 wlan0
```


Wrapped in "code" tags to make it readable. ;)

So I think we found the issue.  Going from 164.76.27.14 --> 164.76.232.10 through the cscotun0 route above needs a different netmask. If you don't control it, the VPN team will need to change it for this to work.
You have a 164.76.26.0/23 network - that provide this:
```
Address:     	164.76.26.0           	10100100.01001100.0001101 0.00000000
Netmask: 	255.255.254.0 = 23 	11111111.11111111.1111111 0.00000000
Wildcard: 	0.0.1.255 	00000000.00000000.0000000 1.11111111
=>
Network:     	164.76.26.0/23        	10100100.01001100.0001101 0.00000000
HostMin: 	164.76.26.1 	10100100.01001100.0001101 0.00000001
HostMax: 	164.76.27.254 	10100100.01001100.0001101 1.11111110
Broadcast: 	164.76.27.255 	10100100.01001100.0001101 1.11111111
Hosts/Net: 	510 	Class B
```

Simply stated - you can't get there from here. ;(
At least that's my troubleshooting result.

---

### Post by buntu_hugenewbie11 on 2014-03-18
I may not be understanding.
Are most netmasks not 255.255.255.255? What do most vpn networks use?

How come this only affects Linux and not Putty Windows clients?
Sorry, I am not understanding what my potential solutions are beyond asking the institution to change it's netmask for vpn.

---

### Post by TheFu on 2014-03-18
Check the routing table under Windows, if it works there.
**route print**

Then you will have ways forward to make the Linux routing table look the same.

---

### Post by buntu_hugenewbie11 on 2014-03-26
The netmask for windows ends in 254 for the vpn.
So do I need to change it on my client?

---

