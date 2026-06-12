---
title: "Vpn"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by auraithx on 2008-05-21
I'm trying to set up a VPN connection with a dedicated server I share with a mate. I've installed OpenVPN and he's sent me the keys but I cannot, for the life of me, figure out how to work it. 

I've looked on google for ages and found squat. All the tutorials are for something else or don't work. If someone could tell me what to do quickly or point me towards a tutorial it would be greatly appreciated.

Thanks,
AuraithX

ps; I'm running Hardy Heron

---

### Post by Monicker on 2008-05-21
Your friend is running Openvpn as a server, and you want to connect as a client?

```
sudo mkdir /etc/openvpn/keys
cp the key files to /etc/openvpn/keys
sudo chown -R root.root /etc/openvpn/keys/*
sudo chmod 600 /etc/openvpn/keys/*
cp /usr/share/doc/openvpn/examples/sample-config-files/client.conf /etc/openvpn
```

Now you will need to edit the client.conf file to fit your particular situation.

Edit with the text editor of your choice.  At a minimum you will need to specify the remote server.  

```
remote 10.10.10.10 1194
```

The remote can be specified by ip or its dns name.  Did you friend mention anything about whether or not you will need to enter a usern
ame and password to connect to his openvpn server?  There is also an option to require a tls-authorization key for greater security.  If either of these is the case, then you will need to modify additional lines in the client.conf.

Once your config is done just do 
```

sudo /etc/init.d/openvpn start
```

You can do an ifconfig afterwards to verify the tun interface is up and has an ip address from the openvpn server.

---

### Post by auraithx on 2008-05-21
```
mark@mark-desktop:~$ sudo /etc/init.d/openvpn start
 * Starting virtual private network daemon.                                      *  (failure: No such VPN: openvpn)
                                                                         [ OK ]

```

---

### Post by Monicker on 2008-05-21
> **auraithx said:**
> ```
mark@mark-desktop:~$ sudo /etc/init.d/openvpn start
 * Starting virtual private network daemon.                                      *  (failure: No such VPN: openvpn)
                                                                         [ OK ]

```


Not much detail there.  Check the openvpn logs in /var/log.  You should post your client.conf config file, so that I can see exactly what is in it.  Do you know if the additional authentication methods I mentioned are required?

Also show the results of
```

ls /etc/openvpn
ls /etc/openvpn/keys
```

EDIT: Just realized that you do have an OK message there.  Did you check to see if the client vpn interface came up?

---

### Post by auraithx on 2008-05-22
> **Monicker said:**
> Not much detail there.  Check the openvpn logs in /var/log.  You should post your client.conf config file, so that I can see exactly what is in it.  Do you know if the additional authentication methods I mentioned are required?

Also show the results of
```

ls /etc/openvpn
ls /etc/openvpn/keys
```

EDIT: Just realized that you do have an OK message there.  Did you check to see if the client vpn interface came up?

My mate to just told me to leave the username/pw in /config (he's on windows so I assume that's the equivalent of /keys)

> mark@mark-desktop:~$ ls /etc/openvpn
client.conf  client.conf~  config  keys  update-resolv-conf
mark@mark-desktop:~$ ls /etc/openvpn/keys
biker11.crt  biker11.csr  biker11.key  biker11.ovpn  ca.crt


I don't have a openvpn folder in /var/logs - Is it just the general logs to check? I looked at all of them and couldn't see anything relating to openvpn in the recent ones.

> ##############################################
# Sample client-side OpenVPN 2.0 config file #
# for connecting to multi-client server.     #
#                                            #
# This configuration can be used by multiple #
# clients, however each client should have   #
# its own cert and key files.                #
#                                            #
# On Windows, you might want to rename this  #
# file so it has a .ovpn extension           #
##############################################

# Specify that we are a client and that we
# will be pulling certain config file directives
# from the server.
client

# Use the same setting as you are using on
# the server.
# On most systems, the VPN will not function
# unless you partially or fully disable
# the firewall for the TUN/TAP interface.
;dev tap
dev tun

# Windows needs the TAP-Win32 adapter name
# from the Network Connections panel
# if you have more than one.  On XP SP2,
# you may need to disable the firewall
# for the TAP adapter.
;dev-node MyTap

# Are we connecting to a TCP or
# UDP server?  Use the same setting as
# on the server.
;proto tcp
proto udp

# The hostname/IP and port of the server.
# You can have multiple remote entries
# to load balance between the servers.
remote 64.191.[retracted] 1194


# Choose a random host from the remote
# list for load-balancing.  Otherwise
# try hosts in the order specified.
;remote-random

# Keep trying indefinitely to resolve the
# host name of the OpenVPN server.  Very useful
# on machines which are not permanently connected
# to the internet such as laptops.
resolv-retry infinite

# Most clients don't need to bind to
# a specific local port number.
nobind

# Downgrade privileges after initialization (non-Windows only)
;user nobody
;group nobody

# Try to preserve some state across restarts.
persist-key
persist-tun

# If you are connecting through an
# HTTP proxy to reach the actual OpenVPN
# server, put the proxy server/IP and
# port number here.  See the man page
# if your proxy server requires
# authentication.
;http-proxy-retry # retry on connection failures
;http-proxy [proxy server] [proxy port #]

# Wireless networks often produce a lot
# of duplicate packets.  Set this flag
# to silence duplicate packet warnings.
;mute-replay-warnings

# SSL/TLS parms.
# See the server config file for more
# description.  It's best to use
# a separate .crt/.key file pair
# for each client.  A single ca
# file can be used for all clients.
ca ca.crt
cert biker11.crt
key biker11.key

# Verify server certificate by checking
# that the certicate has the nsCertType
# field set to "server".  This is an
# important precaution to protect against
# a potential attack discussed here:
#  [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm)
#
# To use this feature, you will need to generate
# your server certificates with the nsCertType
# field set to "server".  The build-key-server
# script in the easy-rsa folder will do this.
;ns-cert-type server

# If a tls-auth key is used on the server
# then every client must also have the key.
;tls-auth ta.key 1

# Select a cryptographic cipher.
# If the cipher option is used on the server
# then you must also specify it here.
;cipher x

# Enable compression on the VPN link.
# Don't enable this unless it is also
# enabled in the server config file.
comp-lzo

# Set log file verbosity.
verb 3

# Silence repeating messages
;mute 20

---

### Post by Monicker on 2008-05-22
What is the file called "config" in the /etc/openvpn directory? Did he already supply you with a config file to use?  Test it by running it manually - sudo openvpn /etc/openvpn/config.  If that one has already been set up for you and works, use it. 

I have never seen a password declared in the config file itself; I do not believe there is even a directive for explicitly setting it, just to get prompted for it. 

Normally the logs are in /var/log; at least that has been the case whenever I have used openvpn  It may be logging to /var/log/messages since you do not have anything specified.

---

### Post by auraithx on 2008-05-22
I created the /config folder to put the keys in as that's what you do on windows. But then you told me to put them in /keys - which I assume is the ubuntu equivalent. 

Can't see anything in usr/var/messages - just a bunch of logs about my I/O devices.

---

### Post by Monicker on 2008-05-22
As I mentioned previously, you did get an OK message.

Please show the results of

```
sudo /etc/init.d/openvpn restart
```

wait about 15 seconds

```
ifconfig
```

---

### Post by auraithx on 2008-05-22
```
mark@mark-desktop:~$  sudo /etc/init.d/openvpn restart
[sudo] password for mark: 
 * Stopping virtual private network daemon.                              [ OK ] 
 * Starting virtual private network daemon.                                      *  (failure: No such VPN: openvpn)
                                                                         [ OK ]
mark@mark-desktop:~$  ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:20:1b:59:28  
          inet addr:192.168.1.200  Bcast:192.168.1.255  Mask:255.255.255.128
          inet6 addr: fe80::213:20ff:fe1b:5928/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46649 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49049 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41266959 (39.3 MB)  TX bytes:7038840 (6.7 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:926 errors:0 dropped:0 overruns:0 frame:0
          TX packets:926 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:46300 (45.2 KB)  TX bytes:46300 (45.2 KB)

```

---

### Post by auraithx on 2008-05-23
.ovpn is the wind. equiv. of .conf so I just renamed it now my config looks like this

```


  GNU nano 2.0.7         File: /etc/openvpn/client.conf                         

client
dev tun
proto tcp

#Change my.publicdomain.com to your public domain or IP address
remote 64.[retracted] 1194

resolv-retry infinite
nobind


persist-key
persist-tun


ca ca.crt
cert biker11.crt
key biker11.key

ns-cert-type server

push "dhcp-option DNS 66.[retracted]"
push "dhcp-option DNS 4.2.2.1"

comp-lzo

verb 3

```

I also tried using the GUI method - no luck.

---

### Post by Monicker on 2008-05-23
The default for openvpn is to use udp, not tcp.  Verify which one your friend is using on the server.

Specify a log parameter so that you can see why it is failing.

```
log         /var/log/openvpn.log
```

---

### Post by auraithx on 2008-05-26
> **Monicker said:**
> The default for openvpn is to use udp, not tcp.  Verify which one your friend is using on the server.

Specify a log parameter so that you can see why it is failing.

```
log         /var/log/openvpn.log
```

I've c/p his config file so it'll be right.

I've added that log line but it's still not logging.

> log         /var/log/openvpn.log

log-append  /var/log/openvpn.log

status /var/log/status.log


---

### Post by uzi09 on 2009-03-03
What I understand from your first question is that you cannot connect to a server. IE: You are the CLIENT.

As per [http://openvpn.net/index.php/documentation/howto.html#start](http://openvpn.net/index.php/documentation/howto.html#start)
```

You just type openvpn /path/to/openvpn/config/file/client.conf

```

So for me, I've stored the keys & client config file in my home folder under the (hidden) folder .openvpn
So to run openvpn and connect to my openvpn server, I type the following in the client:
```

sudo openvpn ~/.openvpn/client.conf

```
It seems like the client needs to be run as a superuser. If you're successful you'll see:
```

Initialization Sequence Completed
```

A sample client.conf file is located here:
/usr/share/doc/openvpn/examples/sample-config-files/client.conf

Although your friend should probably provide it to you with the correct information in it (with the exception of where the client keys are located on YOUR computer)

---

