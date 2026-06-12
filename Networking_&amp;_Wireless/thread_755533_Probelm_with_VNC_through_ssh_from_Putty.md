---
title: "Probelm with VNC through ssh from Putty"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by Sopranosmainman on 2008-04-14
Hey guys, 

ive set up 2 linux machines with ssh, and have had no problem logging in through ssh, and then using vnc to see my desktop.

Now i have a 3rd machine, set it up the same way, and i can ssh in, but my vnc does not go past initializing connection.

I have determined this is an issue with SSH. I can vnc locally into that machine, so i know that x11vnc server is running. The port i am using is also open on my router. So what about ssh can be hindering me?

I have set it up exactly like my other machines, so i can vnc in from putty. please help me out. This is driving me nuts!

---

### Post by Sopranosmainman on 2008-04-15
As a side note, i followed this guide to set everything up. Like i said i only have issues with one machine.

[http://ubuntuforums.org/showthread.php?t=383053](http://ubuntuforums.org/showthread.php?t=383053)

---

### Post by Sopranosmainman on 2008-04-16
bump?

---

### Post by krunge on 2008-04-16
No error messages or logging that might give a clue?

---

### Post by Sopranosmainman on 2008-04-16
ssh runs fine, vnc does not give any errors. All it says is connection initialized, then two minutes later ti will say connection time out.

If you can tell me how to look for logs or errors on the ssh side, please let me know

---

### Post by The Cog on 2008-04-16
Try connecting wiht telnet, which might give you a clue by what it says. You will have to connect like this:
> telnet 127.0.0.1 5900
You will at least see if the connection is being accepted or not.

---

### Post by Sopranosmainman on 2008-04-17
this is what i see in the konsole terminal

[B]telnet 127.0.0.1 5900
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection timed out[/B]

---

### Post by The Cog on 2008-04-18
I presume you are launching ssh with 
```
ssh -L 5900:127.0.0.1:5900 server_ip
```
try adding -v -v -v to the command to get very verbose messages while its running. I guesss that for some reason, the local port forwarding is not gettng set up properly.

---

### Post by Sopranosmainman on 2008-04-18
ssh -L 5900:127.0.0.1:5900 192.168.80.100 -p "xxx"-v -v -v
OpenSSH_4.7p1 Debian-8ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.80.100 [192.168.80.100] port xxx.
debug1: connect to address 192.168.80.100 port xxx: Connection timed out
ssh: connect to host 192.168.80.100 port xxx: Connection timed out


So thats what i get when i run what you told me. Thing is the port is fowarded, and i CAN ssh in with putty!

This makes less and less sense

---

### Post by Sopranosmainman on 2008-04-18
ssh -L 5900:127.0.0.1:5900 "external ip" -p xxx -v -v -v
OpenSSH_4.7p1 Debian-8ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to "external ip" ["external ip"] port xxx.
debug1: Connection established.
debug1: identity file /home/administrator/.ssh/identity type -1
debug3: Not a RSA1 key file /home/administrator/.ssh/id_rsa.
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'Proc-Type:'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'DEK-Info:'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/administrator/.ssh/id_rsa type 1
debug1: identity file /home/administrator/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1
debug2: fd 5 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 129/256
debug2: bits set: 528/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: put_host_port: ["external ip"}:xxx
debug3: put_host_port: ["external ip"]:xxx
debug3: check_host_in_hostfile: filename /home/administrator/.ssh/known_hosts
debug3: check_host_in_hostfile: filename /etc/ssh/ssh_known_hosts
debug3: check_host_in_hostfile: filename /home/administrator/.ssh/known_hosts
debug3: check_host_in_hostfile: filename /etc/ssh/ssh_known_hosts
debug1: checking without port identifier
debug3: check_host_in_hostfile: filename /home/administrator/.ssh/known_hosts
debug3: check_host_in_hostfile: filename /etc/ssh/ssh_known_hosts
debug3: check_host_in_hostfile: filename /home/administrator/.ssh/known_hosts
debug3: check_host_in_hostfile: filename /etc/ssh/ssh_known_hosts
debug3: check_host_in_hostfile: filename /home/administrator/.ssh/known_hosts
debug3: check_host_in_hostfile: filename /etc/ssh/ssh_known_hosts
debug2: no key of type 0 for host ["external ip"]:xxx
debug3: check_host_in_hostfile: filename /home/administrator/.ssh/known_hosts2
debug3: check_host_in_hostfile: filename /etc/ssh/ssh_known_hosts2
debug3: check_host_in_hostfile: filename /home/administrator/.ssh/known_hosts
debug3: check_host_in_hostfile: filename /etc/ssh/ssh_known_hosts
debug2: no key of type 2 for host "external ip":xxx
The authenticity of host '["external ip"]:xxx(["external ip"]:xxx)' can't be established.
RSA key fingerprint is 73:9c:28:1b:c8:e5:ea:fa:b1:05:33:1c:51:66:0d:bc.
Warning: Permanently added '["external ip":xxx,["external ip"]:xxx (RSA) to the list of known hosts.
debug2: bits set: 530/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
Connection closed by "external ip"


Now that output was generated by entering my dynamicdns address, much different when trying to login with my local ip.

---

### Post by Sopranosmainman on 2008-04-21
bump

---

