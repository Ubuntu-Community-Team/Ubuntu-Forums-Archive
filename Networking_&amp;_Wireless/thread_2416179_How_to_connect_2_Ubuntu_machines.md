---
title: "How to connect 2 Ubuntu machines?"
date: 2019-04-06
forum: Networking &amp; Wireless
---

### Post by ubontik22 on 2019-04-06
Hi,  I want to connect 2 Ubuntu (18.04) machines (wireless). They ping to each other but I can't connect them. Thanks

---

### Post by sudodus on 2019-04-06
Are the two computers connected via a router (wireless access point)?

In that case it should be straightforward to install an ssh server into one of the computers,

```

sudo apt update
sudo apt install openssh-server

```

and then log in from the other computer via

```

ssh user@ip-address

```

or access files (get/put) via

```

sftp user@ip-address

```

or the corresponding via the file manager, write in the address box:

```

ssh://user@ip-address
# or
sftp://user@ip-address

```

and log in.

---

### Post by ubontik22 on 2019-04-06
One is wired connection to the router and other wireless

---

### Post by ubontik22 on 2019-04-06
Do I need instead of user@ip-address enter user name in 1st machine and IP-address of 1st machine? Thank you

---

### Post by sudodus on 2019-04-06
Use the **user ID in the server machine** and the **ip-address of the server machine**, when you log in from the other machine.

For example: ubontik@192.168.0.2

---

### Post by ubontik22 on 2019-04-06
sudodus  I typed in terminal ssh and then sftp and in both cases got "no such file or directory". But when I pinged it was OK.

---

### Post by sudodus on 2019-04-07
Please describe exactly what you did (in which computer) and exactly what was the output.

---

### Post by ubontik22 on 2019-04-09
comp1    

```
$ ifconfig
enp4s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.67  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 2600:1700:87d0:7630::655  prefixlen 128  scopeid 0x0<global>
        inet6 2600:1700:87d0:7630:eed5:cf85:671e:b3a3  prefixlen 64  scopeid 0x0<global>
```


comp2   
  
```
$ ifconfig
enp1s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 54:bf:64:3f:5a:14  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 221  bytes 18269 (18.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 221  bytes 18269 (18.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.68  netmask 255.255.255.0  broadcast 192.168.1.255
```
    
After entering in comp2 in address box of File Manager ssh://comp1ID@192.168.1.67 or sftp://comp1ID@192.168.1.67   I've got:
  
```
 
Failed to open "File System" 
Timed out when logging in. 
```
-      

Thank you

---

### Post by sudodus on 2019-04-10
Have you installed **openssh-server** in computer 1?

Is there a user ID with the name **comp1ID** in computer 1?

Have you tried to log in 'directly' by using the command **ssh** (from a terminal window in computer 2)?

```

ssh comp1ID@192.168.1.67
# and
sftp comp1ID@192.168.1.67

```

---

### Post by ubontik22 on 2019-04-10
comp2 is a laptop and I've installed Studio 18.04, and comp1 is desktop 18.04

```
$ sudo apt install openssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssh-server is already the newest version (1:7.6p1-4ubuntu0.3).
The following package was automatically installed and is no longer required:
  libopenshot16
Use 'sudo apt autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

```
$ ssh comp1ID@192.168.1.67
ssh: connect to host 192.168.1.67 port 22: Connection timed out
```

```
$ sftp comp1ID@192.168.1.67
ssh: connect to host 192.168.1.67 port 22: Connection timed out
Connection closed
```

---

### Post by sudodus on 2019-04-11
Is there a user ID with the name **comp1ID** in computer 1?

What happens if you ping computer 1 from computer 2?

```

ping 192.168.1.67

```

---

### Post by ubontik22 on 2019-04-11
The user ID is kapidze. The ping is OK

---

### Post by ubontik22 on 2019-04-11
ssh kapidze@192.168.1.67

---

### Post by sudodus on 2019-04-12
Does it work with the following command?

```

ssh kapidze@192.168.1.67 

```

---

### Post by ubontik22 on 2019-04-12
```
$ ssh kapidze@192.168.1.67 ssh: connect to host 192.168.1.67 port 22: Connection timed out
```

---

### Post by sudodus on 2019-04-12
Is openssh-server installed in the computer at 192.168.1.67 ?

Have you done anything to limit the access via the ports for ssh and sftp?

It could be in one of the computers or in the router?

Or has someone else done anything to limit the access via the ports for ssh and sftp?

I'm thinking of firewall settings.

The numbers 67 and 68 in the IP addresses indicate that the network is rather big, and could include several users. This makes me think that someone may have put restrictions in a firewall.

---

### Post by sudodus on 2019-04-12
One more question: Is the system in the computer at 192.168.1.67 an **installed** system?

I am asking because there are problems to connect to openssh-server in a live or persistent live system, where there is no password.

---

### Post by ubontik22 on 2019-04-12
Yes the system is installed and updated regularly. Is there a way to check the openssh-server from terminal (I mean an output)?  
Is it possible that a firewall blocks access? If yes, how to configure the firewall to allow access to 192.168.1.67?  
Thank you

---

### Post by sudodus on 2019-04-13
You can test openssh-server from the computer where it is installed (with the same commands, that you would use from another computer).

I am not good at configuring firewalls. Let us hope that someone else will see this and helps you.

---

### Post by ubontik22 on 2019-04-13
The is an output from the server:

```

$ ssh comp1ID@192.168.1.67
The authenticity of host '192.168.1.67 (192.168.1.67)' can't be established.
ECDSA key fingerprint is SHA256:9Kd7zYMwuKx0lJYTZYS2AmE0H0uwR9R0coK4AbynE40.$ ssh comp1ID@192.168.1.67
The authenticity of host '192.168.1.67 (192.168.1.67)' can't be established.
ECDSA key fingerprint is SHA256:9Kd7zYMwuKx0lJYTZYS2AmE0H0uwR9R0coK4AbynE40.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.1.67' (ECDSA) to the list of known hosts.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.1.67' (ECDSA) to the list of known hosts.

```

---

### Post by ubontik22 on 2019-04-13
```
$ ssh comp1ID@192.168.1.67
comp1ID@192.168.1.67's password: 
Welcome to Ubuntu 18.04.2 LTS (GNU/Linux 4.15.0-47-generic x86_64)

 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)

 * Ubuntu's Kubernetes 1.14 distributions can bypass Docker and use containerd
   directly, see [https://bit.ly/ubuntu-containerd](https://bit.ly/ubuntu-containerd) or try it now with

     snap install microk8s --classic

 * Canonical Livepatch is available for installation.
   - Reduce system reboots and improve kernel security. Activate at:
     [https://ubuntu.com/livepatch](https://ubuntu.com/livepatch)

8 packages can be updated.
0 updates are security updates.

Last login: Sat Apr 13 15:06:49 2019 from 192.168.1.67
```

---

### Post by sudodus on 2019-04-14
This is what ssh should look like :-)

But I guess that you ran it from the computer itself (and that it does not work from the other computer). So I think there is something that prevents the connection between the two computers. It could be a setting in a firewall.

---

### Post by ubontik22 on 2019-04-15
Yes, I ssh-ed to itself.
You remember when I ssh-ed from other computer it said something about port 22. Probably I should allow an input from the port 22.

Thank you for your help

---

### Post by sudodus on 2019-04-16
> **ubontik22 said:**
> Yes, I ssh-ed to itself.
You remember when I ssh-ed from other computer it said something about port 22. **Probably I should allow an input from the port 22.**

Thank you for your help

Yes, I agree, you should allow input from port 22. But I am not very good at managing firewalls (I use the default settings in Ubuntu). Let us invite someone who knows to help you with that.

If you will not get enough help here to solve your problem, you can start another thread with 'firewall' in the title and a description of your problem in the first post.

---

### Post by ubontik22 on 2019-05-01
Is it possible that on the Studio machine there is no sharing (at least I did not find)?
Is possible to connect them by **Remmina**?

---

### Post by TheFu on 2019-05-01
Anything is possible, but getting ssh working is the first step.  Both systems should be able to ssh into the other.  ssh works on 22/tcp by default. Same for sftp, scp, rsync and 50 other ssh-based tools.

If you enabled the firewall, then you'll need to open port 22/tcp for any of this to work.

The **ssh -vvv userid@IP** will show if any connection is being made at all. If not, start checking firewalls.

Remmina isn't something I use.  **vinagre** is how I connect to either NX or RDP or VNC connections.  NX is the fastest of those three when Linux is involved. It is also the most secure, since it uses ssh-keys for authentication. Best of all, with just the ssh port open, NX will work.  That's just 1 firewall port for all that amazing access.  
But there's more <my best late-night TV voice>!  ssh can do 50+ other things. Master ssh and you can connect pretty much any Unix-like systems together, securely, anywhere in the world.  All of them need "lite" desktops, no Gnome3, KDE, or any desktop that wants direct access to a GPU.  None of them will deal with high-end graphics or video well, if at all.  There are other techniques for those problems.

If you just want NX for a remote desktop, x2go is the easiest way to get it, but only after ssh is working.  Until ssh works, don't bother.

---

### Post by ubontik22 on 2019-05-02
Below is an out for [B]ssh -vvv userid@IP:
```
$  ssh -vvv userid@[IP]
OpenSSH_7.6p1 Ubuntu-4ubuntu0.3, OpenSSL 1.0.2n  7 Dec 2017
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: resolving "[IP]" port 22
debug2: ssh_connect_direct: needpriv 0
debug1: Connecting to [IP] [[IP]] port 22.
debug1: Connection established.
debug1: key_load_public: No such file or directory
debug1: identity file /home/tomsoy/.ssh/id_rsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/tomsoy/.ssh/id_rsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/tomsoy/.ssh/id_dsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/tomsoy/.ssh/id_dsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/tomsoy/.ssh/id_ecdsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/tomsoy/.ssh/id_ecdsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/tomsoy/.ssh/id_ed25519 type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/tomsoy/.ssh/id_ed25519-cert type -1
debug1: Local version string SSH-2.0-OpenSSH_7.6p1 Ubuntu-4ubuntu0.3
debug1: Remote protocol version 2.0, remote software version OpenSSH_7.6p1 Ubuntu-4ubuntu0.3
debug1: match: OpenSSH_7.6p1 Ubuntu-4ubuntu0.3 pat OpenSSH* compat 0x04000000
debug2: fd 3 setting O_NONBLOCK
debug1: Authenticating to [IP]:22 as 'userid'
debug3: hostkeys_foreach: reading file "/home/tomsoy/.ssh/known_hosts"
debug3: record_hostkey: found key type ECDSA in file /home/tomsoy/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys from [IP]
debug3:  order_hostkeyalgs: prefer hostkeyalgs:  [email]ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com[/email],ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521
debug3: send packet: type 20
debug1: SSH2_MSG_KEXINIT sent
debug3: receive packet: type 20
debug1: SSH2_MSG_KEXINIT received
debug2: local client KEXINIT proposal
debug2:  KEX algorithms:  curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha256,diffie-hellman-group14-sha1,ext-info-c
debug2:  host key algorithms:  [email]ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-ed25519-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com[/email],ssh-ed25519,rsa-sha2-512,rsa-sha2-256,ssh-rsa
debug2:  ciphers ctos:  [email]chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com[/email]
debug2:  ciphers stoc:  [email]chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com[/email]
debug2:  MACs ctos:  [email]umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com[/email],hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2:  MACs stoc:  [email]umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com[/email],hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com,zlib
debug2: compression stoc: none,zlib@openssh.com,zlib
debug2: languages ctos: 
debug2: languages stoc: 
debug2: first_kex_follows 0 
debug2: reserved 0 
debug2: peer server KEXINIT proposal
debug2:  KEX algorithms:  curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group14-sha256,diffie-hellman-group14-sha1
debug2: host key algorithms: ssh-rsa,rsa-sha2-512,rsa-sha2-256,ecdsa-sha2-nistp256,ssh-ed25519
debug2:  ciphers ctos:  [email]chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com[/email]
debug2:  ciphers stoc:  [email]chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com[/email]
debug2:  MACs ctos:  [email]umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com[/email],hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2:  MACs stoc:  [email]umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com[/email],hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com
debug2: compression stoc: none,zlib@openssh.com
debug2: languages ctos: 
debug2: languages stoc: 
debug2: first_kex_follows 0 
debug2: reserved 0 
debug1: kex: algorithm: curve25519-sha256
debug1: kex: host key algorithm: ecdsa-sha2-nistp256
debug1: kex: server->client cipher: [email]chacha20-poly1305@openssh.com[/email] MAC: <implicit> compression: none
debug1: kex: client->server cipher: [email]chacha20-poly1305@openssh.com[/email] MAC: <implicit> compression: none
debug3: send packet: type 30
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug3: receive packet: type 31
debug1: Server host key: ecdsa-sha2-nistp256 SHA256:9Kd7zYMwuKx0lJYTZYS2AmE0H0uwR9R0coK4AbynE40
debug3: hostkeys_foreach: reading file "/home/tomsoy/.ssh/known_hosts"
debug3: record_hostkey: found key type ECDSA in file /home/tomsoy/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys from [IP]
debug1: Host '[IP]' is known and matches the ECDSA host key.
debug1: Found key in /home/tomsoy/.ssh/known_hosts:1
debug3: send packet: type 21
debug2: set_newkeys: mode 1
debug1: rekey after 134217728 blocks
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug3: receive packet: type 21
debug1: SSH2_MSG_NEWKEYS received
debug2: set_newkeys: mode 0
debug1: rekey after 134217728 blocks
debug2: key: /home/tomsoy/.ssh/id_rsa ((nil))
debug2: key: /home/tomsoy/.ssh/id_dsa ((nil))
debug2: key: /home/tomsoy/.ssh/id_ecdsa ((nil))
debug2: key: /home/tomsoy/.ssh/id_ed25519 ((nil))
debug3: send packet: type 5
debug3: receive packet: type 7
debug1: SSH2_MSG_EXT_INFO received
debug1:  kex_input_ext_info:  server-sig-algs=<ssh-ed25519,ssh-rsa,rsa-sha2-256,rsa-sha2-512,ssh-dss,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521>
debug3: receive packet: type 6
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug3: send packet: type 50
debug3: receive packet: type 51
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/tomsoy/.ssh/id_rsa
debug3: no such identity: /home/tomsoy/.ssh/id_rsa: No such file or directory
debug1: Trying private key: /home/tomsoy/.ssh/id_dsa
debug3: no such identity: /home/tomsoy/.ssh/id_dsa: No such file or directory
debug1: Trying private key: /home/tomsoy/.ssh/id_ecdsa
debug3: no such identity: /home/tomsoy/.ssh/id_ecdsa: No such file or directory
debug1: Trying private key: /home/tomsoy/.ssh/id_ed25519
debug3: no such identity: /home/tomsoy/.ssh/id_ed25519: No such file or directory
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
userid@[IP]'s password: 
debug3: send packet: type 50
debug2: we sent a password packet, wait for reply
debug3: receive packet: type 51
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
userid@[IP]'s  password: &#1053;&#1072;&#1083;&#1080;&#1095;&#1080;&#1077; &#1087;&#1072;&#1089;&#1087;&#1086;&#1088;&#1090;&#1086;&#1074; &#1059;&#1082;&#1088;&#1072;&#1080;&#1085;&#1099; &#1080; &#1056;&#1086;&#1089;&#1089;&#1080;&#1080; &#1085;&#1077; &#1087;&#1088;&#1080;&#1074;&#1077;&#1076;&#1077;&#1090; &#1082; &#1087;&#1091;&#1090;&#1072;&#1085;&#1080;&#1094;&#1077;,  &#1075;&#1086;&#1074;&#1086;&#1088;&#1080;&#1090; &#1055;&#1077;&#1089;&#1082;&#1086;&#1074;. &#1055;&#1088;&#1080; &#1101;&#1090;&#1086;&#1084; &#1086;&#1085; &#1087;&#1086;&#1089;&#1090;&#1072;&#1074;&#1080;&#1083; &#1074; &#1087;&#1088;&#1080;&#1084;&#1077;&#1088; &#1091;&#1082;&#1088;&#1072;&#1080;&#1085;&#1094;&#1077;&#1074; &#1089; &#1074;&#1077;&#1085;&#1075;&#1077;&#1088;&#1089;&#1082;&#1080;&#1084;&#1080;  &#1087;&#1072;&#1089;&#1087;&#1086;&#1088;&#1090;&#1072;&#1084;&#1080;.
debug3: send packet: type 50
debug2: we sent a password packet, wait for reply
debug3: receive packet: type 51
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
userid@[IP]'s password: 

```

---

### Post by TheFu on 2019-05-02
[https://ubuntuforums.org/showthread.php?t=2338032](https://ubuntuforums.org/showthread.php?t=2338032) - I'd check the directory and file permissions for ~/.ssh/ and files inside on both systems. If they are too open or too closed, ssh isn't happy.

There are lots of ways to prevent a specific user from being able to use ssh/sftp/scp/rsync, but someone would have gone out of their way to set that up. By defaults, any userid has ssh access on stock Ubuntu systems, if the openssh-server package is installed.

Please post all output using 'code' tags, so things line up.  Sometimes the indentation is VERY important in the output.

---

### Post by him610 on 2019-05-02
FWIW, I have two machines on the same network. As I was following along with the sequences of postings, I decided I would see if I could ssh from one machine to the other. Upon trying it, I could not ssh from either one to the other.

I discovered I did not have openssh-server installed on the target machine. After installing it along with three supporting programs, I was successful in logging onto the target machine with the newly installed openssh-server.

Maybe, this will help someone.

---

### Post by QIII on 2019-05-02
@ubontik22 --

I have gone through your posts in this thread and added code tags instead of non-default font, colors, etc.

Please use the default font and size in your posts unless there is some particular part to which you want to draw attention or using another font/color makes you meaning clearer.

Also, please enclose all terminal commands and their results in code tags.  That will preserve formatting and make your posts much easier to read.

To use code tags:

If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by TheFu on 2019-05-02
If you ever open the ssh port to the internet, some more security is needed.

Install fail2ban.  This will block brute-force, password, attacks.
Setup ssh-keys between the systems.  The client should run **ssh-keygen -t ed25519** to generate the private and public keys for that client.  
Then use **ssh-copy-id  userid@remote-server** 
```
     The default_ID_file is the most recent file that matches: ~/.ssh/id*.pub,
     (excluding those that match ~/.ssh/*-cert.pub) so if you create a key
     that is not the one you want ssh-copy-id to use, just use touch(1) on
     your preferred key's .pub file to reinstate it as the most recent.

``` That will push the public key to teh other box, create the ~/.ssh/ directory, update the authorized_keys file, retain the correct permissions for the directory and files in there.

ed25519 is secure choice today. Over time, the best choice has changed.
Now test **ssh userid@remote-server** to see that no password is necessary once the key-file has been unlocked. More secure, very difficult to hack, more convenient.  I don't know of any more secure solution that is also more convenient too.

After all that is setup, then it is time to block all password use over the internet. Allow it on the LAN, but never over the internet.  sshd_config has settings for that.
Put something like this at the bottom of the file.
# Change to no to disable tunnelled clear text passwords
```
PasswordAuthentication no
Match Address 172.22.22.0/24,172.21.22.0/24
      PasswordAuthentication yes

``` Obviously, change the subnet for what ever subnet your LAN has - or even just the specific IPs.  The "Match Address" is good until a different match address happens, which is why putting it at the bottom of the file is best.
There are some other settings to help with security and while the default settings for fail2ban are helpful, there are some others to be nastier towards the bad guys.

---

### Post by ubontik22 on 2019-08-29
?

---

