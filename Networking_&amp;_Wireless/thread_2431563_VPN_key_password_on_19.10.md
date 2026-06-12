---
title: "VPN key password on 19.10"
date: 2019-11-18
forum: Networking &amp; Wireless
---

### Post by menext on 2019-11-18
I recently updated to 19.10 and VPN with password protected keys stopped working. System doesn't ask for a password when selecting connection. When I try to save the password in the VPN settings it  doesn't seem to save the password. VPN settings without passwords work. All the VPN are openvpn.  

Searching online hasn't produced and reliable results.

---

### Post by crip720 on 2019-11-18
Does the 'passwords and keys' program show/list them?.  Might also try to delete the VPN/s and reinstalling.  If logging in with password required, that will also loggin to password and keys, without asking again for password.

---

### Post by #&amp;thj^% on 2019-11-18
> **menext said:**
> I recently updated to 19.10 and VPN with password protected keys stopped working. System doesn't ask for a password when selecting connection. When I try to save the password in the VPN settings it  doesn't seem to save the password. VPN settings without passwords work. All the VPN are openvpn.  

Searching online hasn't produced and reliable results.

On linux my file is called "**/etc/openvpn/client.conf** "
Here is an older config I used for example
```

##############################################
# Sample client-side OpenVPN 2.0 config file.
# for connecting to multi-client server. 
##############################################

# Specify that we are a client and that we
# will be pulling certain config file directives
# from the server.
client

dev tun
proto udp

# The hostname/IP and port of the server.
remote my-server-2.domain 1194


# host name of the OpenVPN server.  Very useful
# on machines which are not permanently connected
# to the internet such as laptops.
resolv-retry infinite

# Most clients don't need to bind to
# a specific local port number.
nobind

# Try to preserve some state across restarts.
persist-key
persist-tun

# Certificate Authority
ca ca.crt

# Username/Password authentication is used on the server
auth-user-pass

# Verify server certificate by checking
# that the certicate has the nsCertType
# field set to "server".  This is an
# important precaution to protect against
# a potential attack discussed here:
#  http://openvpn.net/howto.html#mitm
#
# To use this feature, you will need to generate
# your server certificates with the nsCertType
# field set to "server".  The build-key-server
# script in the easy-rsa folder will do this.
ns-cert-type server

# Set log file verbosity.
verb 3

# To start the openvpn client, simply type:
# openvpn --config /etc/openvpn/client.conf

```

Have you read through this also: [https://help.ubuntu.com/lts/serverguide/openvpn.html](https://help.ubuntu.com/lts/serverguide/openvpn.html)

---

### Post by menext on 2019-11-18
The config is not the problem. Of 10 VPN connection 2 that require a password to access the keys, don't ask for a password and therefore fail. I will try recreating from scratch to see if it helps.

UPDATE: recreating new connection doesn't help. 

This was working on 19.04. When the connection was activated it would ask for the password and if the correct password to the key was issued the OpenVPN connection would be established.The keys are not the issue since it still works on other systems.

---

### Post by #&amp;thj^% on 2019-11-19
I was really trying to see if you would give more information;
Have a look @ "openvpn server.conf"
```
openvpn server.conf

```
Here is one I mucked-up intentionally:
```
openvpn server.conf
Options error: --ca fails with 'ca.crt': Permission denied (errno=13)
Options error: --cert fails with 'server_qhpOowxxxxxx4op.crt': Permission denied (errno=13)
Options error: --key fails with 'server_qhpOowxxxxxx4op.key': Permission denied (errno=13)
Options error: --tls-crypt fails with 'tls-crypt.key': Permission denied (errno=13)
Options error: --status fails with '/var/log/openvpn/status.log': Permission denied (errno=13)
Options error: Please correct these errors.
Use --help for more information.


```
And I told it **not** to use a password during this test set-up.
Now after adding "Ask for Password"
```
Tue Nov 19 11:46:16 2019 OpenVPN 2.4.8 [git:makepkg/3976acda9bf10b5e+] x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [LZ4] [EPOLL] [PKCS11] [MH/PKTINFO] [AEAD] built on Oct 30 2019
Tue Nov 19 11:46:16 2019 library versions: OpenSSL 1.1.1d  10 Sep 2019, LZO 2.10
Tue Nov 19 11:46:16 2019 NOTE: your local LAN uses the extremely common subnet address 192.168.0.x or 192.168.1.x.  Be aware that this might create routing conflicts if you connect to the VPN server from public locations such as internet cafes that use the same subnet.
Tue Nov 19 11:46:16 2019 ECDH curve prime256v1 added
Tue Nov 19 11:46:16 2019 Outgoing Control Channel Encryption: Cipher 'AES-256-CTR' initialized with 256 bit key
Tue Nov 19 11:46:16 2019 Outgoing Control Channel Encryption: Using 256 bit message hash 'SHA256' for HMAC authentication
Tue Nov 19 11:46:16 2019 Incoming Control Channel Encryption: Cipher 'AES-256-CTR' initialized with 256 bit key
Tue Nov 19 11:46:16 2019 Incoming Control Channel Encryption: Using 256 bit message hash 'SHA256' for HMAC authentication
Tue Nov 19 11:46:16 2019 TUN/TAP device tun2 opened
Tue Nov 19 11:46:16 2019 TUN/TAP TX queue length set to 100
Tue Nov 19 11:46:16 2019 /usr/bin/ip link set dev tun2 up mtu 1500
Tue Nov 19 11:46:16 2019 /usr/bin/ip addr add dev tun2 10.8.0.1/24 broadcast 10.8.0.255
Tue Nov 19 11:46:16 2019 Could not determine IPv4/IPv6 protocol. Using AF_INET
Tue Nov 19 11:46:16 2019 Socket Buffers: R=[212992->212992] S=[212992->212992]
Tue Nov 19 11:46:16 2019 TCP/UDP: Socket bind failed on local address [AF_INET][undef]:1194: Address already in use (errno=98)
Tue Nov 19 11:46:16 2019 Exiting due to fatal error
Tue Nov 19 11:46:16 2019 Closing TUN/TAP interface
Tue Nov 19 11:46:16 2019 /usr/bin/ip addr del dev tun2 10.8.0.1/24

```
Note: "Socket bind failed on local address [AF_INET][undef]:1194: Address already in use (errno=98)"
is because I'm using the same port for another VPN service.
I don't recall asking you if your key's were valid??? (That's on you)
Is this a dedicated OpenVPN server, Desktop, Headless?
Another example used for this thread only:
```
sudo openvpn --remote 10.56.100.53 --comp-lzo --dev tun --auth-user-pass --ca ca.crt --client
```

This tells the client to use the remote OpenVPN server at IP address 10.56.100.53, use LZO compression (**Which I DON"T recommend for safety**), a tunnel interface, authenticate with username / password and check if the certificate of the server matches. There are many difference (GUI) clients for OpenVPN but this is just a quick method to connect.
Here is one that works, but no longer in service "**udp.ovpn**":
```
client
dev tun
proto udp
remote 31.171.152.19 1194
resolv-retry infinite
remote-random
nobind
tun-mtu 1500
tun-mtu-extra 32
mssfix 1450
persist-key
persist-tun
ping 15
ping-restart 0
ping-timer-rem
reneg-sec 0
comp-lzo no

remote-cert-tls server

**[COLOR="#990000"]auth-user-pass[/COLOR]**
verb 3
pull
fast-io
cipher AES-256-CBC
auth SHA512

```
BTW: This is on 20.04 Development 
```
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Focal Fossa (development branch)
Release:	20.04
Codename:	focal

```

---

### Post by menext on 2019-11-20
Sorry. I assumed since most here were on the Desktop Ubuntu it would be understood that this is not the server side. The servers are FreeBSD which have multiple configurations and clients. The work without a hitch with Windows, Mac, Fedora, Android, Ubuntu 19.04 and before clients. The same config files worked without a hitch on 19.04. In Gnome under network you could choose a VPN. One option is openvpn. Before, if the kwy had a password it would ask for the password. Now even when you set it to ask for the password it doesn't ask. Setting the option to save the password doesn't seem to do anything.

openvpn.conf (client)

client
dev tun
proto udp
remote openvpn.CHANGEDFROMORIG.com 1194
resolv-retry infinite
nobind
persist-key
persist-tun

ca ca.crt
cert my.crt
key my.key

tls-auth ta.key 1
comp-lzo
verb 3

-------------------------

Like I said above. It works on 19.04 without an issue. I was hoping that there may have been an easy solution.

---

### Post by #&amp;thj^% on 2019-11-26
There still could be an easy solution, providing there is enough information given by a poster.
Anyway I have found that there are times when OpenVPN is enabled at start-up.
First thing I would try is:
```
sudo killall openvpn
```
Then try your logins again.
Until I get any needed info from you, I'm just stabbing in the dark here. :(
With each new Version Up-grade come's new bits of software
On 19.10 (And newer 20.04 Development) I had to kill openvpn so it would let me use my Set-up the way I liked it. ;)
```
netstat -rn tun0
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         10.10.234.1     128.0.0.0       UG        0 0          0 tun1
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlp3s0
10.8.0.0        0.0.0.0         255.255.255.0   U         0 0          0 tun0
10.10.234.0     0.0.0.0         255.255.255.0   U         0 0          0 tun1
128.0.0.0       10.10.234.1     128.0.0.0       UG        0 0          0 tun1
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlp3s0
184.75.223.235  10.10.234.1     255.255.255.255 UGH       0 0          0 tun1
184.75.223.237  192.168.1.1     255.255.255.255 UGH       0 0          0 wlp3s0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlp3s0

```
And:
```
netstat -i tun0
Kernel Interface table
Iface      MTU    RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
enp0s25   1500        0      0      0 0             0      0      0      0 BMU
lo       65536    22507      0      0 0         22507      0      0      0 LRU
tun0      1500        0      0      0 0             9      0      0      0 MOPRU
tun1      1500    37192      0      0 0         16455      0    137      0 MOPRU
wlp3s0    1500    37849      0      0 0         17407      0      0      0 BMRU

```
Trust me I know how frustrating this can be....:)
EDIT: Also check this to see if everything looks right to you:
```
ps aux | grep openvpn | grep -v grep
```
It should look something like this:
```
nobody      1401  0.0  0.0  11872  6868 ?        Ss   10:57   0:00 /usr/sbin/openvpn --daemon ovpn-server --status /run/openvpn/server.status 10 --cd /etc/openvpn --script-security 2 --config /etc/openvpn/server.conf --writepid /run/openvpn/server.pid
root        4392  0.1  0.0  11928  7120 ?        S    10:58   0:03 /usr/sbin/openvpn --config /home/me/.airvpn**<Sniped key by me>**.tmp.ovpn
```
Just noticed your ovpn config, and mine works with:
```
client
dev tun
remote ca.vpn.Changed by me.org 443
resolv-retry infinite
nobind
persist-key
persist-tun
auth-nocache
route-delay 5
verb 3
explicit-exit-notify 5
remote-cert-tls server
cipher AES-256-CBC
**comp-lzo no**
proto udp
key-direction 1
<ca>
#and below the above, are all my certs.
```

---

