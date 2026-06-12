---
title: "SSH issue: Can not SSH in to Ubuntu 18.04 Server via Port Forwarding"
date: 2019-01-20
forum: Networking &amp; Wireless
---

### Post by B99 on 2019-01-20
I am running Ubuntu 18.04 Server on a Raspberry Pi 3B+.  It is behind a router so I've forwarded a port to my Pi's port 22 to give me remote access.  I can SSH in from my LAN and  was able over WAN until today. As far as I know, nothing of significance changed since I was last able to log in remotely.  Shortly before that I installed Bit Torrent on my PC and it set up some port forwards via UPnP and I thought some how that might have been the issue, so I uninstalled Bit Torrent and got rid of it's port forwards. That did not fix the problem.  I thought the problem might still be with the router so I booted up the Pi with a SD running Raspbian and discovered that it worked fine, so it would seem to be an issue with my Ubuntu set up.

I'll post ssh -vvv for a successful log in from the LAN and for a failed one for the WAN. Any help greatly appreciated.  Thanks!
```
r@LAPTOP-27CPUBHK:~$ ssh -vvv r@10.100.102.9OpenSSH_7.2p2 Ubuntu-4ubuntu2.1, OpenSSL 1.0.2g  1 Mar 2016
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: resolving "10.100.102.9" port 22
debug2: ssh_connect_direct: needpriv 0
debug1: Connecting to 10.100.102.9 [10.100.102.9] port 22.
debug1: Connection established.
debug1: identity file /home/r/.ssh/id_rsa type 1
debug1: key_load_public: No such file or directory
debug1: identity file /home/r/.ssh/id_rsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/r/.ssh/id_dsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/r/.ssh/id_dsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/r/.ssh/id_ecdsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/r/.ssh/id_ecdsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/r/.ssh/id_ed25519 type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/r/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_7.2p2 Ubuntu-4ubuntu2.1
debug1: Remote protocol version 2.0, remote software version OpenSSH_7.6p1 Ubuntu-4ubuntu0.1
debug1: match: OpenSSH_7.6p1 Ubuntu-4ubuntu0.1 pat OpenSSH* compat 0x04000000
debug2: fd 3 setting O_NONBLOCK
debug1: Authenticating to 10.100.102.9:22 as 'r'
debug3: hostkeys_foreach: reading file "/home/r/.ssh/known_hosts"
debug3: record_hostkey: found key type ECDSA in file /home/r/.ssh/known_hosts:17
debug3: load_hostkeys: loaded 1 keys from 10.100.102.9
debug3: order_hostkeyalgs: prefer hostkeyalgs: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521
debug3: send packet: type 20
debug1: SSH2_MSG_KEXINIT sent
debug3: receive packet: type 20
debug1: SSH2_MSG_KEXINIT received
debug2: local client KEXINIT proposal
debug2: KEX algorithms: curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,ext-info-c
debug2: host key algorithms: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-ed25519-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com,ssh-ed25519,rsa-sha2-512,rsa-sha2-256,ssh-rsa
debug2: ciphers ctos: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com,aes128-cbc,aes192-cbc,aes256-cbc,3des-cbc
debug2: ciphers stoc: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com,aes128-cbc,aes192-cbc,aes256-cbc,3des-cbc
debug2: MACs ctos: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: MACs stoc: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com,zlib
debug2: compression stoc: none,zlib@openssh.com,zlib
debug2: languages ctos:
debug2: languages stoc:
debug2: first_kex_follows 0
debug2: reserved 0
debug2: peer server KEXINIT proposal
debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group14-sha256,diffie-hellman-group14-sha1
debug2: host key algorithms: ssh-rsa,rsa-sha2-512,rsa-sha2-256,ecdsa-sha2-nistp256,ssh-ed25519
debug2: ciphers ctos: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: ciphers stoc: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: MACs ctos: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: MACs stoc: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com
debug2: compression stoc: none,zlib@openssh.com
debug2: languages ctos:
debug2: languages stoc:
debug2: first_kex_follows 0
debug2: reserved 0
debug1: kex: algorithm: curve25519-sha256@libssh.org
debug1: kex: host key algorithm: ecdsa-sha2-nistp256
debug1: kex: server->client cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug1: kex: client->server cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug3: send packet: type 30
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug3: receive packet: type 31
debug1: Server host key: ecdsa-sha2-nistp256 SHA256:fQJO7qoOLGxTJgK3g35D8ARFOoGGbt/PQ9cvNDZAZLc
debug3: hostkeys_foreach: reading file "/home/r/.ssh/known_hosts"
debug3: record_hostkey: found key type ECDSA in file /home/r/.ssh/known_hosts:17
debug3: load_hostkeys: loaded 1 keys from 10.100.102.9
debug1: Host '10.100.102.9' is known and matches the ECDSA host key.
debug1: Found key in /home/r/.ssh/known_hosts:17
debug3: send packet: type 21
debug2: set_newkeys: mode 1
debug1: rekey after 134217728 blocks
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug3: receive packet: type 21
debug2: set_newkeys: mode 0
debug1: rekey after 134217728 blocks
debug1: SSH2_MSG_NEWKEYS received
debug2: key: /home/r/.ssh/id_rsa (0x7ffff2227720)
debug2: key: /home/r/.ssh/id_dsa ((nil))
debug2: key: /home/r/.ssh/id_ecdsa ((nil))
debug2: key: /home/r/.ssh/id_ed25519 ((nil))
debug3: send packet: type 5
debug3: receive packet: type 7
debug1: SSH2_MSG_EXT_INFO received
debug1: kex_input_ext_info: server-sig-algs=<ssh-ed25519,ssh-rsa,rsa-sha2-256,rsa-sha2-512,ssh-dss,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521>
debug3: receive packet: type 6
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug3: send packet: type 50
debug3: receive packet: type 51
debug1: Authentications that can continue: publickey
debug3: start over, passed a different list publickey
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/r/.ssh/id_rsa
debug3: send_pubkey_test
debug3: send packet: type 50
debug2: we sent a publickey packet, wait for reply
debug3: receive packet: type 60
debug3: send packet: type 50
debug3: receive packet: type 52
debug1: Authentication succeeded (publickey).
Authenticated to 10.100.102.9 ([10.100.102.9]:22).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug3: send packet: type 90
debug1: Requesting no-more-sessions@openssh.com
debug3: send packet: type 80
debug1: Entering interactive session.
debug1: pledge: network
debug3: receive packet: type 80
debug1: client_input_global_request: rtype hostkeys-00@openssh.com want_reply 0
debug3: receive packet: type 91
debug2: callback start
debug2: fd 3 setting TCP_NODELAY
debug3: ssh_packet_set_tos: set IP_TOS 0x10
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 1
debug3: send packet: type 98
debug1: Sending environment.
debug3: Ignored env SHELL
debug3: Ignored env TERM
debug3: Ignored env USER
debug3: Ignored env NAME
debug3: Ignored env LS_COLORS
debug3: Ignored env HOSTTYPE
debug3: Ignored env PATH
debug3: Ignored env PWD
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug3: send packet: type 98
debug3: Ignored env SHLVL
debug3: Ignored env HOME
debug3: Ignored env LOGNAME
debug3: Ignored env LESSOPEN
debug3: Ignored env LESSCLOSE
debug3: Ignored env _
debug2: channel 0: request shell confirm 1
debug3: send packet: type 98
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug3: receive packet: type 99
debug2: channel_input_status_confirm: type 99 id 0
debug2: PTY allocation request accepted on channel 0
debug2: channel 0: rcvd adjust 2097152
debug3: receive packet: type 99
debug2: channel_input_status_confirm: type 99 id 0
debug2: shell request accepted on channel 0
Last login: Sun Jan 20 14:09:38 2019 from 10.100.102.3
r@ubuntu:~$
```






 ```
r@LAPTOP-27CPUBHK:~$ ssh -vvv r@XXXXXXXXXX -p 6637OpenSSH_7.2p2 Ubuntu-4ubuntu2.1, OpenSSL 1.0.2g  1 Mar 2016
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: resolving "XXXXXXXXXXX" port XXXXX
debug2: ssh_connect_direct: needpriv 0
debug1: Connecting to XXXXXXXXXXXXX[XXXXXXXXXX] port 6637.
debug1: Connection established.
debug1: identity file /home/r/.ssh/id_rsa type 1
debug1: key_load_public: No such file or directory
debug1: identity file /home/r/.ssh/id_rsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/r/.ssh/id_dsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/r/.ssh/id_dsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/r/.ssh/id_ecdsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/r/.ssh/id_ecdsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/r/.ssh/id_ed25519 type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/r/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_7.2p2 Ubuntu-4ubuntu2.1
ssh_exchange_identification: Connection closed by remote host
r@LAPTOP-27CPUBHK:~$
```

---

### Post by TheFu on 2019-01-20
Using UPnP is anti-security.  Best to disable that.

Also, does the Pi have a static IP?

ssh troubleshooting: [http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)

BTW, might want to setup the ~/.ssh/config file to deal with the different connections.

---

### Post by B99 on 2019-01-20
I know UPnP is a risk, my router menu doesn't seem to have an option to disable.  Is there a command line method to disable?

Thanks, I will run through the troubleshooting checklist (yours?) and report back.

Ok, I've run through the checklist.  SSH is clearly running with proper permissions as I can login from my PC on the LAN.  I can ping all ports on the external IP including the ones forwarding to port 22 on my Pi.

I don't know how to read iptables but some stuff looks suspicious to me.

 $ iptables -L
```
Chain INPUT (policy DROP)target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     esp  --  anywhere             anywhere
ACCEPT     ah   --  anywhere             anywhere
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request limit: up to 5/sec burst 5 mode srcip
ACCEPT     udp  --  anywhere             anywhere             multiport dports isakmp,ipsec-nat-t,51820
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh ctstate NEW
ACCEPT     ipencap--  anywhere             anywhere             policy match dir in pol ipsec proto esp
ACCEPT     udp  --  anywhere             ubuntu               udp dpt:domain


Chain FORWARD (policy DROP)
target     prot opt source               destination
DROP       all  --  10.19.48.0/24        10.19.48.0/24
DROP       all  --  10.19.48.0/24        10.19.49.0/24
DROP       all  --  10.19.49.0/24        10.19.48.0/24
DROP       all  --  10.19.49.0/24        10.19.49.0/24
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
DROP       tcp  --  anywhere             anywhere             tcp dpt:microsoft-ds
DROP       udp  --  anywhere             anywhere             multiport ports netbios-ns,netbios-dgm
DROP       tcp  --  anywhere             anywhere             multiport ports netbios-ns,netbios-ssn
ACCEPT     all  --  10.19.48.0/24        anywhere             ctstate NEW policy match dir in pol ipsec
ACCEPT     all  --  10.19.49.0/24        anywhere             ctstate NEW policy match dir in pol none


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

---

### Post by TheFu on 2019-01-20
ping works at the port level?  Some routers will not transmit data that originates from inside the LAN over the outer public IP (WAN) port.  Can you test that using a different protocol?

No matter, this appears to be the issue.
```
ssh_exchange_identification: Connection closed by remote host
```

Can you check the server-side sshd logs?  There is a debug option.  For IPv4-only setups, adding:
```
AddressFamily inet
```
to the sshd_config file will prevent IPv6 connections from being used before you are prepared for some installs.  I have multiple 16.04 server installs, but only 1 needed the "inet" added, which confused me.  I disable IPv6 on all my servers, routers, and switches. Just not ready to secure it yet.

Hopefully, the server-side logs will lead to why the connection is being refused.

---

### Post by B99 on 2019-01-20
> **TheFu said:**
> ping works at the port level?  Some routers will not transmit data that originates from inside the LAN over the outer public IP (WAN) port.  Can you test that using a different protocol? 
I can successfully transmit data from the LAN to the server over the WAN using a different SD card in my Pi with Raspbian installed.
> 
No matter, this appears to be the issue.
```
ssh_exchange_identification: Connection closed by remote host
```

Can you check the server-side sshd logs?  There is a debug option.  For IPv4-only setups, adding:
```
AddressFamily inet
```
to the sshd_config file will prevent IPv6 connections from being used before you are prepared for some installs.  I have multiple 16.04 server installs, but only 1 needed the "inet" added, which confused me.  I disable IPv6 on all my servers, routers, and switches. Just not ready to secure it yet.

Hopefully, the server-side logs will lead to why the connection is being refused.
/var/log/auth.log Doesn't appear to be picking up the failed attempts. I've changed LogLevel in /etc/ssh/sshd_config to VERBOSE, and still auth.log seems to only be logging the root logins from my sudo tail -2000 /var/log/auth.log requests.

```
Jan 20 21:06:15 ubuntu sudo: pam_unix(sudo:session): session opened for user root by r(uid=0)Jan 20 21:06:15 ubuntu sudo: pam_unix(sudo:session): session closed for user root
Jan 20 21:06:31 ubuntu sudo:        r : TTY=pts/1 ; PWD=/home/r ; USER=root ; COMMAND=/usr/bin/tail -2000 /var/log/auth.log
Jan 20 21:06:31 ubuntu sudo: pam_unix(sudo:session): session opened for user root by r(uid=0)
Jan 20 21:06:32 ubuntu sudo: pam_unix(sudo:session): session closed for user root
Jan 20 21:07:21 ubuntu sudo:        r : TTY=pts/1 ; PWD=/home/r ; USER=root ; COMMAND=/usr/bin/tail -2000 /var/log/auth.log
Jan 20 21:07:21 ubuntu sudo: pam_unix(sudo:session): session opened for user root by r(uid=0)
Jan 20 21:07:21 ubuntu sudo: pam_unix(sudo:session): session closed for user root
Jan 20 21:09:38 ubuntu sudo:        r : TTY=pts/1 ; PWD=/home/r ; USER=root ; COMMAND=/usr/bin/tail -2000 /var/log/auth.log
Jan 20 21:09:38 ubuntu sudo: pam_unix(sudo:session): session opened for user root by r(uid=0)
Jan 20 21:09:38 ubuntu sudo: pam_unix(sudo:session): session closed for user root
Jan 20 21:10:01 ubuntu CRON[337]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 20 21:10:01 ubuntu CRON[337]: pam_unix(cron:session): session closed for user root
Jan 20 21:10:26 ubuntu sudo:        r : TTY=pts/1 ; PWD=/home/r ; USER=root ; COMMAND=/usr/bin/tail -2000 /var/log/syslog
Jan 20 21:10:26 ubuntu sudo: pam_unix(sudo:session): session opened for user root by r(uid=0)
Jan 20 21:10:26 ubuntu sudo: pam_unix(sudo:session): session closed for user root
Jan 20 21:10:43 ubuntu sudo:        r : TTY=pts/1 ; PWD=/home/r ; USER=root ; COMMAND=/usr/bin/tail -2000 /var/log/syslog
Jan 20 21:10:43 ubuntu sudo: pam_unix(sudo:session): session opened for user root by r(uid=0)
Jan 20 21:10:43 ubuntu sudo: pam_unix(sudo:session): session closed for user root
Jan 20 21:10:55 ubuntu sudo:        r : TTY=pts/1 ; PWD=/home/r ; USER=root ; COMMAND=/usr/bin/tail -2000 /var/log/auth.log
Jan 20 21:10:55 ubuntu sudo: pam_unix(sudo:session): session opened for user root by r(uid=0)
``` 


I'm not sure what you are suggesting with the IPv6. I am not using it and can disable. Do you think that is somehow related to my issue?

---

### Post by TheFu on 2019-01-21
> I can successfully transmit data from the LAN to the server over the WAN using a different SD card in my Pi with Raspbian installed.

If the client tries to connect to the same IP but the server-side ssh-key is different, then the connection should be refused. ssh thinks someone is trying to MiTM attack.

> I'm not sure what you are suggesting with the IPv6. I am not using it and can disable. Do you think that is somehow related to my issue? 
When I google'd the error, a fix included that inet setting. That result reminded me of my issue which was fixed with that setting - it is related?  Maybe.  In this case, I'm not just sharing random data and random settings.  Google the error. You'll see.

We are guessing until the server-side debug messages are provided.  To get those, you must run the sshd -d interactively.

But if the same Ubuntu client can connect to the same physical hardware, but running a different OS, doesn't that say the likely issue is on the server-side to you?  The only alternative is either that or that the client-side is trying to protect itself from an attack caused by a lying server that doesn't pass the expected server and public-key tests.  There are methods to re-create the server-side ssh key, but doing so should break LAN access, so I didn't mention it.

Regardless, it is best to ensure that different OSes on the same physical hardware use different IPs on the LAN.  If you are using DHCP, then specific steps will be necessary to correct for that.

---

### Post by The Cog on 2019-01-21
> I don't know how to read iptables but some stuff looks suspicious to me.
```
Chain INPUT (policy DROP)target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
```

This looks very suspicious, but that is because the info is incomplete. It is missing restrictions on ports - this rule probably only applies to local loopback traffic. A better command is **sudo iptables -nvL** but better still to my mind is **sudo iptables-save** which outputs **all** iptables information, in a form that can be re-imported with iptables-restore.

---

### Post by B99 on 2019-01-21
@TheFu I'm working on getting some more details from server-side sshd.  If you don't mind spoon feeding me some direction I'd appreciate it.

@TheCog

Is worth bearing in mind that I have Algo VPN running on this server. It set up the firewall.  I not otherwise set one up (the server is behind a router.)

```
# Generated by iptables-save v1.6.1 on Mon Jan 21 18:22:10 2019*filter
:INPUT DROP [8411:1566601]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [20784:6335695]
-A INPUT -i lo -j ACCEPT
-A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A INPUT -p esp -j ACCEPT
-A INPUT -p ah -j ACCEPT
-A INPUT -p icmp -m icmp --icmp-type 8 -m hashlimit --hashlimit-upto 5/sec --hashlimit-burst 5 --hashlimit-mode srcip --hashlimit-name icmp-echo-drop -j ACCEPT
-A INPUT -p udp -m multiport --dports 500,4500,51820 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 22 -m conntrack --ctstate NEW -j ACCEPT
-A INPUT -p ipencap -m policy --dir in --pol ipsec --proto esp -j ACCEPT
-A INPUT -d 172.16.0.1/32 -p udp -m udp --dport 53 -j ACCEPT
-A FORWARD -s 10.19.48.0/24 -d 10.19.48.0/24 -j DROP
-A FORWARD -s 10.19.48.0/24 -d 10.19.49.0/24 -j DROP
-A FORWARD -s 10.19.49.0/24 -d 10.19.48.0/24 -j DROP
-A FORWARD -s 10.19.49.0/24 -d 10.19.49.0/24 -j DROP
-A FORWARD -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -p tcp -m tcp --dport 445 -j DROP
-A FORWARD -p udp -m multiport --ports 137,138 -j DROP
-A FORWARD -p tcp -m multiport --ports 137,139 -j DROP
-A FORWARD -s 10.19.48.0/24 -m conntrack --ctstate NEW -m policy --dir in --pol ipsec -j ACCEPT
-A FORWARD -s 10.19.49.0/24 -m conntrack --ctstate NEW -m policy --dir in --pol none -j ACCEPT
COMMIT
# Completed on Mon Jan 21 18:22:10 2019
# Generated by iptables-save v1.6.1 on Mon Jan 21 18:22:10 2019
*nat
:PREROUTING ACCEPT [16787:3107891]
:INPUT ACCEPT [15:916]
:OUTPUT ACCEPT [3059:221677]
:POSTROUTING ACCEPT [3059:221677]
-A POSTROUTING -s 10.19.48.0/24 -m policy --dir out --pol none -j MASQUERADE
-A POSTROUTING -s 10.19.49.0/24 -m policy --dir out --pol none -j MASQUERADE
COMMIT
# Completed on Mon Jan 21 18:22:10 2019
# Generated by iptables-save v1.6.1 on Mon Jan 21 18:22:10 2019
*mangle
:PREROUTING ACCEPT [36191:14336361]
:INPUT ACCEPT [27830:12795987]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [20879:6344523]
:POSTROUTING ACCEPT [20879:6344523]
COMMIT
# Completed on Mon Jan 21 18:22:10 2019
```

An additional data point.

When attempting to ssh to the server from my PC on the LAN via WAN, it hangs for about 15 seconds before I get "ssh_exchange_identification: Connection closed by remote host."

When I try from an android device not connected to the LAN, the client app(JuiceSSH) says in about 3 seconds "No route to host"

---

### Post by TheFu on 2019-01-21
I would guess that the VPN has hosed the routing and is preventing the ssh connections from responding.  Algo is just a font-end to FreeSwan/IPSec right?

Disable Algo and test again. May need to reboot the Algo server to clean up the routes too.

---

### Post by B99 on 2019-01-22
I wasn't sure how to disable Algo so I reflashed the image and started from scratch.  The issue persists. With further testing I discovered that I could either ssh remotely to the wlan0 or the eth0 but not both.  If I disable wlan0 (ifconfig wlan0 down) then I can ssh to eth0.  Once I enable wlan0 again, I can no longer ssh to eth0 remotely but I can to wlan0.

This leads me to  think the issue is with my Netplan, as I used the Netplan from the previous install.  Here it is:

```
# This file is generated from information provided by# the datasource.  Changes to it will not persist across an instance.
# To disable cloud-init's network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}


network:
        version: 2
        renderer: networkd
        ethernets:
                eth0:
                  optional: true
                  addresses: [10.100.102.12/24]
                  gateway4: 10.100.102.1
                  nameservers:
                   addresses: [8.8.8.8,8.8.4.4]
                  dhcp4: no


        wifis:
             wlan0:
                optional: true
                dhcp4: true
                access-points:
                        ***********:
                                password: ***********   
```

---

### Post by TheFu on 2019-01-22
You shouldn't have both wifi and wired ethernet enabled at the same time on the same subnet.  That totally screws routing up.

Ok, there are ways to make the routing work, but ...

---

### Post by B99 on 2019-01-22
Ok, I've removed wifi from netplan and all seems to be working.  I'll make a backup and try installing Algo.

I feel like it's better to have wifi and wired ethernet enabled to have a backup in case one fails, especially as I am preping this for installation in a very remote location.

---

### Post by TheFu on 2019-01-22
Routing tables don't care about our "feelings."  When you have 2 interfaces working on the same subnet, care and understanding is required to know which is primary for all external routes.

When you add the VPN, it modifies the routing tables too.  If you connect in on a public IP, the return traffic has no choice but to follow the routing table, which likely uses a different device and different public IP.  To ssh, that looks like a MiTM attack.  If you ssh into the VPN public IP and it allows inbound connections (most do not), then ssh should work.  I think.

My routing knowledge is only sufficient to recognize issues, but not sufficient to help others get beyond those issues. Sorry.

Always check the routing table and figure out how the packets get in and how they must leave based on the priorities for each different route and subnetting.

---

### Post by B99 on 2019-01-22
Thank you, I very much appreciate your help in solving this issue and your time spent educating me. I'll try and see if I can learn more about iptables and maybe make an attempt then.

---

