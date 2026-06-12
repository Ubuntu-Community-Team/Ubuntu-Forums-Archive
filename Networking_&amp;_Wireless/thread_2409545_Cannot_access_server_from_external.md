---
title: "Cannot access server from external"
date: 2019-01-03
forum: Networking &amp; Wireless
---

### Post by mpez on 2019-01-03
So i installed a 18.04.1 server a few hours ago but i cannot access it from outside my local network ( using my IP address )

Of course 
[LIST]
[*]SSH server is installed
[*]Port 22 is open from SSH config
[*]Allowed Port 22 on UFW (both IPv4 and IPv6)
[*]Restarted SSH service multiple times (including the machine itself)
[*]Enabled port forwarding through my router (and tested it with [http://www.canyouseeme.org/](http://www.canyouseeme.org/) just to be sure)
[*]Even tried DMZ option from router settings
[*]Checked for IP conflicts and everything is fine
[/LIST]

My local network architecture is below
Rooter->unmanaged switch->all PCs are connected to switch

If i try to locally connect using 192.168.1.80 (that's my actual local IPv4 address) everything is fine
When i try to access the server using my internet IP i always get "Network error: Connection refused"

Any ideas?

---

### Post by The Cog on 2019-01-03
That leads me to suspect that the connection request is not reaching the server. Possibly the router is refusing the call, possibly the router is forwarding to a different address, and possibly your ISP is blocking it.

The best way to prove this is to run this command on the server to show any port 22 traffic and then try to connect from outside. If you don't see the connect request and the response in tcpdump then the call is not reaching the server.
```
sudo tcpdump -nnp tcp port 22
```

---

### Post by mpez on 2019-01-03
I don't know if what i get is correct but here's a part of a looooooong post

```
23:37:42.261863 IP 192.168.1.3.53807 > 192.168.1.80.22: Flags [.], ack 18327232, win 2087, length 023:37:42.261879 IP 192.168.1.80.22 > 192.168.1.3.53807: Flags [P.], seq 18327232:18327408, ack 130081, win 269, length 176
23:37:42.261932 IP 192.168.1.80.22 > 192.168.1.3.53807: Flags [P.], seq 18327408:18327696, ack 130081, win 269, length 288
23:37:42.262138 IP 192.168.1.80.22 > 192.168.1.3.53807: Flags [P.], seq 18327696:18327872, ack 130081, win 269, length 176
23:37:42.262392 IP 192.168.1.80.22 > 192.168.1.3.53807: Flags [P.], seq 18327872:18328048, ack 130081, win 269, length 176
23:37:42.262644 IP 192.168.1.3.53807 > 192.168.1.80.22: Flags [.], ack 18327872, win 2091, length 0
23:37:42.262659 IP 192.168.1.80.22 > 192.168.1.3.53807: Flags [P.], seq 18328048:18328224, ack 130081, win 269, length 176
23:37:42.262714 IP 192.168.1.80.22 > 192.168.1.3.53807: Flags [P.], seq 18328224:18328512, ack 130081, win 269, length 288
23:37:42.262917 IP 192.168.1.80.22 > 192.168.1.3.53807: Flags [P.], seq 18328512:18328688, ack 130081, win 269, length 176
23:37:42.263167 IP 192.168.1.3.53807 > 192.168.1.80.22: Flags [.], ack 18328688, win 2087, length 0
23:37:42.263182 IP 192.168.1.80.22 > 192.168.1.3.53807: Flags [P.], seq 18328688:18328864, ack 130081, win 269, length 176
23:37:42.263235 IP 192.168.1.80.22 > 192.168.1.3.53807: Flags [P.], seq 18328864:18329152, ack 130081, win 269, length 288
23:37:42.263434 IP 192.168.1.80.22 > 192.168.1.3.53807: Flags [P.], seq 18329152:18329328, ack 130081, win 269, length 176
23:37:42.263687 IP 192.168.1.80.22 > 192.168.1.3.53807: Flags [P.], seq 18329328:18329504, ack 130081, win 269, length 176
23:37:42.263937 IP 192.168.1.3.53807 > 192.168.1.80.22: Flags [.], ack 18329328, win 2091, length 0
23:37:42.263952 IP 192.168.1.80.22 > 192.168.1.3.53807: Flags [P.], seq 18329504:18329680, ack 130081, win 269, length 176
23:37:42.264015 IP 192.168.1.80.22 > 192.168.1.3.53807: Flags [P.], seq 18329680:18329968, ack 130081, win 269, length 288
23:37:42.264209 IP 192.168.1.80.22 > 192.168.1.3.53807: Flags [P.], seq 18329968:18330144, ack 130081, win 269, length 176
23:37:42.264463 IP 192.168.1.80.22 > 192.168.1.3.53807: Flags [P.], seq 18330144:18330320, ack 130081, win 269, length 176
23:37:42.264713 IP 192.168.1.3.53807 > 192.168.1.80.22: Flags [.], ack 18330144, win 2087, length 0
23:37:42.264727 IP 192.168.1.80.22 > 192.168.1.3.53807: Flags [P.], seq 18330320:18330496, ack 130081, win 269, length 176
23:37:42.264788 IP 192.168.1.80.22 > 192.168.1.3.53807: Flags [P.], seq 18330496:18330784, ack 130081, win 269, length 288
23:37:42.264984 IP 192.168.1.80.22 > 192.168.1.3.53807: Flags [P.], seq 18330784:18330960, ack 130081, win 269, length 176
23:37:42.265233 IP 192.168.1.3.53807 > 192.168.1.80.22: Flags [.], ack 18330784, win 2091, length 0
23:37:42.265246 IP 192.168.1.80.22 > 192.168.1.3.53807: Flags [P.], seq 18330960:18331136, ack 130081, win 269, length 176
23:37:42.265307 IP 192.168.1.80.22 > 192.168.1.3.53807: Flags [P.], seq 18331136:18331424, ack 130081, win 269, length 288
23:37:42.265503 IP 192.168.1.80.22 > 192.168.1.3.53807: Flags [P.], seq 18331424:18331600, ack 130081, win 269, length 176
23:37:42.265758 IP 192.168.1.80.22 > 192.168.1.3.53807: Flags [P.], seq 18331600:18331776, ack 130081, win 269, length 176
23:37:42.266007 IP 192.168.1.3.53807 > 192.168.1.80.22: Flags [.], ack 18331600, win 2087, length 0
23:37:42.266021 IP 192.168.1.80.22 > 192.168.1.3.53807: Flags [P.], seq 18331776:18331952, ack 130081, win 269, length 176
23:37:42.266082 IP 192.168.1.80.22 > 192.168.1.3.53807: Flags [P.], seq 18331952:18332240, ack 130081, win 269, length 288
23:37:42.266273 IP 192.168.1.3.53807 > 192.168.1.80.22: Flags [P.], seq 130081:130145, ack 18331600, win 2087, length 64
23:37:42.266289 IP 192.168.1.80.22 > 192.168.1.3.53807: Flags [P.], seq 18332240:18332416, ack 130145, win 269, length 176

```

Tried to connect while running the command but i did not spot any difference in IPs. I am pretty sure that my ISP is not blocking port 22 ( but will check tomorrow just to be sure) . Do you think that the switch might causing the problem ? I mean its just a "dump" unmanaged one but i am able to find server's IPv4 locally.

---

### Post by QIII on 2019-01-03
I'd be pretty surprised if your ISP is blocking port 22.  (By the way, I'd never use port 22, even inside my LAN.  Always us a high-numberd port and use keys and not passwords.)

Are you trying to access your machine using the local LAN IP from the outside, or are you using the external IP assigned by your ISP?

---

### Post by mpez on 2019-01-03
> **QIII said:**
> I'd be pretty surprised if your ISP is blocking port 22.  (By the way, I'd never use port 22, even inside my LAN.  Always us a high-numberd port and use keys and not passwords.)

Are you trying to access your machine using the local LAN IP from the outside, or are you using the external IP assigned by your ISP?
Using 22 because of SSH but also tried different ports. Nothing seems to be working.

If i try ti connect locally using another PC in the network it works fine. If i try to connect using my external IP assigned by my ISP i get the error i mentioned above. Clearly the problem is somewhere in the middle. As The Cog said, either the Router blocks/doesn't forward the request or my switch is messing things up. Or maybe i messed something up by installation .....? But TBH i haven't even install any other packages aside SSH server
But the question is how to determine where the problem is ?

---

### Post by QIII on 2019-01-03
You can set up SSH to work over any random port by modifying your sshd_config, just so long as you don't use one of the lower ports that are already spoken for by convention.

Could you post your sshd_config?

Also please post the exact, full message returned when you try to ssh from outside of your LAN.

---

### Post by mpez on 2019-01-03
There
> 
#  $OpenBSD: sshd_config,v 1.101 2017/03/14 07:19:07 djm Exp $# This is the sshd server system-wide configuration file.  See
# sshd_config(5) for more information.


# This sshd was compiled with PATH=/usr/bin:/bin:/usr/sbin:/sbin


# The strategy used for options in the default sshd_config shipped with
# OpenSSH is to specify options with their default value where
# possible, but leave them commented.  Uncommented options override the
# default value.


Port 22
#AddressFamily any
#ListenAddress 0.0.0.0
#ListenAddress ::


#HostKey /etc/ssh/ssh_host_rsa_key
#HostKey /etc/ssh/ssh_host_ecdsa_key
#HostKey /etc/ssh/ssh_host_ed25519_key


# Ciphers and keying
#RekeyLimit default none


# Logging
#SyslogFacility AUTH
#LogLevel INFO


# Authentication:


#LoginGraceTime 2m
#PermitRootLogin prohibit-password
#StrictModes yes
#MaxAuthTries 6
#MaxSessions 10


#PubkeyAuthentication yes


# Expect .ssh/authorized_keys2 to be disregarded by default in future.
#AuthorizedKeysFile     .ssh/authorized_keys .ssh/authorized_keys2


#AuthorizedPrincipalsFile none


#AuthorizedKeysCommand none
#AuthorizedKeysCommandUser nobody


# For this to work you will also need host keys in /etc/ssh/ssh_known_hosts
#HostbasedAuthentication no
# Change to yes if you don't trust ~/.ssh/known_hosts for
# HostbasedAuthentication
#IgnoreUserKnownHosts no
# Don't read the user's ~/.rhosts and ~/.shosts files
#IgnoreRhosts yes


# To disable tunneled clear text passwords, change to no here!
#PasswordAuthentication yes
#PermitEmptyPasswords no


---

### Post by The Cog on 2019-01-04
Somebody is already using ssh to talk to that server in your tcpdump output. 
This should pick out any connections/disconnections and ignore the rest:
```
sudo tcpdump -l tcp port 22 | grep '\[[SFR]'
```

I don't think the switch will be anything to do with it. Switches don't care about IP addresses.

The interesting thing is that something somewhere is actively refusing the connection: you are getting connection refused, not timeout which would happen if the connect request was being dropped or ignored. We really need to know if the connect request is reaching the server you think it should be reaching.

It occurs to me, you are actually trying the connection from outside your network aren't you? I mean not just trying to connect to the public address from inside your network. I would not expect that to work.

---

