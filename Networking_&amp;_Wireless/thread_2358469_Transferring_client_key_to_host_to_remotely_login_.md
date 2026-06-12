---
title: "Transferring client key to host to remotely login to my Lubuntu machine"
date: 2017-04-13
forum: Networking &amp; Wireless
---

### Post by John_Patrick_Mason on 2017-04-13
I would like to remotely log into my Lubuntu machine from my Ubuntu laptop using the following instructions: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys#keys-with-specific-commands](https://help.ubuntu.com/community/SSH/OpenSSH/Keys#keys-with-specific-commands)

I'm confused at the part where it says:

```
cp authorized_keys authorized_keys_Backup
cat id_rsa.pub >> authorized_keys
```

Where is this authorized_keys file that they're talking about?

---

### Post by papibe on 2017-04-13
Hi John_Patrick_Mason.

It should be on ~/.ssh/ in the server (machine running ssh server).

However, it does not exist by default, only you create it to allow remote connections.

Does that help?
Regards.

---

### Post by John_Patrick_Mason on 2017-04-13
Thank you papibe for responding so quickly.

Indeed the file does not exist by default on my Lubuntu machine. Do I have to also create a hidden folder with the name .ssh or can I just proceed to create the file in my home directory?

---

### Post by papibe on 2017-04-13
Yes. Create it if it doesn't exist:
```
mkdir ~/.ssh
chmod 700 ~/.ssh
```
Remote connections won't work if the files is in another place different than ~/.ssh

Hope it helps. Let us know how it goes.
Regards.

---

### Post by John_Patrick_Mason on 2017-04-14
I'm having a problem, when I type:

```

ssh mason@Lubuntu-Desktop

```

on the host, I get the following error message:

```

ssh: Could not resolve hostname lubuntu-desktop: Name or service not known

```

Also, if I try to connect to the localhost on the server by typing:

```
ssh mason@localhost
```

I get the following error message:

```

Permission denied (publickey).

```

I used a USB flash drive to copy the public key from the host to the server by creating a file with the public key in it, which I stored in the .ssh folder in my home directory.

---

### Post by papibe on 2017-04-14
```

ssh: Could not resolve hostname lubuntu-desktop: Name or service not known

```
It looks like your router doesn't do local DNS. You're going to have to use IP addresses. I don't know if Lubuntu have preinstalled avahi, but you could try this too:
```
ssh mason@Lubuntu-Desktop.local
```
This
```

Permission denied (publickey).

```
Could be a file permission problem, could you open a terminal run these commands on the machine running ssh-server, and post back the result?
```
ls -la ~/.ssh

ssh -vvv mason@localhost
```
Regards.

---

### Post by John_Patrick_Mason on 2017-04-14
[QUOTE=papibe]It looks like your router doesn't do local DNS. You're going to have to use IP addresses.[/QUOTE]

Way before even attempting ssh, I had my router set to max security, I don't know if that could be causing any issues.

I tried typing:

```

ssh mason@Lubuntu-Desktop.local

```

on my host, but all what I got was a blinking cursor with no prompt return.

Also, I just checked the settings in my sshd_config file.

In one of the lines which tells the server where to find the public key, I did not uncomment the following line:

```
#AuthorizedKeysFile %h/.ssh/authorized_keys
```

Was I supposed to?

Here are the logs:

```

total 32
drwx------  2 mason mason 4096 Apr 14 20:05 .
drwx------ 25 mason mason 4096 Apr 14 21:38 ..
-rw-rw-r--  1 mason mason  401 Apr 14 20:03 authorized_keys
-rw-r--r--  1 mason mason  444 Apr 14 20:07 known_hosts

```

```

OpenSSH_7.2p2 Ubuntu-4ubuntu2.1, OpenSSL 1.0.2g  1 Mar 2016
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: resolving "localhost" port 22
debug2: ssh_connect_direct: needpriv 0
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: Connection established.
debug1: key_load_public: No such file or directory
debug1: identity file /home/mason/.ssh/id_rsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/mason/.ssh/id_rsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/mason/.ssh/id_dsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/mason/.ssh/id_dsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/mason/.ssh/id_ecdsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/mason/.ssh/id_ecdsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/mason/.ssh/id_ed25519 type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/mason/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_7.2p2 Ubuntu-4ubuntu2.1
debug1: Remote protocol version 2.0, remote software version OpenSSH_7.2p2 Ubuntu-4ubuntu2.1
debug1: match: OpenSSH_7.2p2 Ubuntu-4ubuntu2.1 pat OpenSSH* compat 0x04000000
debug2: fd 3 setting O_NONBLOCK
debug1: Authenticating to localhost:22 as 'mason'
debug3: hostkeys_foreach: reading file "/home/mason/.ssh/known_hosts"
debug3: record_hostkey: found key type ECDSA in file /home/mason/.ssh/known_hosts:2
debug3: load_hostkeys: loaded 1 keys from localhost
debug3: order_hostkeyalgs: prefer hostkeyalgs: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521
debug3: send packet: type 20
debug1: SSH2_MSG_KEXINIT sent
debug3: receive packet: type 20
debug1: SSH2_MSG_KEXINIT received
debug2: local client KEXINIT proposal
debug2: KEX algorithms: [EMAIL="curve25519-sha256@libssh.org"]curve25519-sha256@libssh.org[/EMAIL],ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,ext-info-c
debug2: host key algorithms: [email]ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-ed25519-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com[/email],ssh-ed25519,rsa-sha2-512,rsa-sha2-256,ssh-rsa
debug2: ciphers ctos: [email]chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com[/email],aes128-cbc,aes192-cbc,aes256-cbc,3des-cbc
debug2: ciphers stoc: [email]chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com[/email],aes128-cbc,aes192-cbc,aes256-cbc,3des-cbc
debug2: MACs ctos: [email]umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com[/email],hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: MACs stoc: [email]umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com[/email],hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com,zlib
debug2: compression stoc: none,zlib@openssh.com,zlib
debug2: languages ctos: 
debug2: languages stoc: 
debug2: first_kex_follows 0 
debug2: reserved 0 
debug2: peer server KEXINIT proposal
debug2: KEX algorithms: [EMAIL="curve25519-sha256@libssh.org"]curve25519-sha256@libssh.org[/EMAIL],ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha1
debug2: host key algorithms: ssh-rsa,rsa-sha2-512,rsa-sha2-256,ecdsa-sha2-nistp256,ssh-ed25519
debug2: ciphers ctos: [email]chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com[/email]
debug2: ciphers stoc: [email]chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com[/email]
debug2: MACs ctos: [email]umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com[/email],hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: MACs stoc: [email]umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com[/email],hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com
debug2: compression stoc: none,zlib@openssh.com
debug2: languages ctos: 
debug2: languages stoc: 
debug2: first_kex_follows 0 
debug2: reserved 0 
debug1: kex: algorithm: [EMAIL="curve25519-sha256@libssh.org"]curve25519-sha256@libssh.org[/EMAIL]
debug1: kex: host key algorithm: ecdsa-sha2-nistp256
debug1: kex: server->client cipher: [EMAIL="chacha20-poly1305@openssh.com"]chacha20-poly1305@openssh.com[/EMAIL] MAC: <implicit> compression: none
debug1: kex: client->server cipher: [EMAIL="chacha20-poly1305@openssh.com"]chacha20-poly1305@openssh.com[/EMAIL] MAC: <implicit> compression: none
debug3: send packet: type 30
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug3: receive packet: type 31
debug1: Server host key: ecdsa-sha2-nistp256 SHA256:QDl2pBwyqIWEgUcL4SgLHK6EXLYlJxJe3G5KOU9lBwU
debug3: hostkeys_foreach: reading file "/home/mason/.ssh/known_hosts"
debug3: record_hostkey: found key type ECDSA in file /home/mason/.ssh/known_hosts:2
debug3: load_hostkeys: loaded 1 keys from localhost
debug1: Host 'localhost' is known and matches the ECDSA host key.
debug1: Found key in /home/mason/.ssh/known_hosts:2
debug3: send packet: type 21
debug2: set_newkeys: mode 1
debug1: rekey after 134217728 blocks
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug3: receive packet: type 21
debug2: set_newkeys: mode 0
debug1: rekey after 134217728 blocks
debug1: SSH2_MSG_NEWKEYS received
debug2: key: /home/mason/.ssh/id_rsa ((nil))
debug2: key: /home/mason/.ssh/id_dsa ((nil))
debug2: key: /home/mason/.ssh/id_ecdsa ((nil))
debug2: key: /home/mason/.ssh/id_ed25519 ((nil))
debug3: send packet: type 5
debug3: receive packet: type 7
debug1: SSH2_MSG_EXT_INFO received
debug1: kex_input_ext_info: server-sig-algs=<rsa-sha2-256,rsa-sha2-512>
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
debug1: Trying private key: /home/mason/.ssh/id_rsa
debug3: no such identity: /home/mason/.ssh/id_rsa: No such file or directory
debug1: Trying private key: /home/mason/.ssh/id_dsa
debug3: no such identity: /home/mason/.ssh/id_dsa: No such file or directory
debug1: Trying private key: /home/mason/.ssh/id_ecdsa
debug3: no such identity: /home/mason/.ssh/id_ecdsa: No such file or directory
debug1: Trying private key: /home/mason/.ssh/id_ed25519
debug3: no such identity: /home/mason/.ssh/id_ed25519: No such file or directory
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey).

```

---

### Post by papibe on 2017-04-15
Thanks.

Just in case change the permissions to the auth file, in the server:
```
chmod 600 ~/.ssh/authorized_keys
```
Now it looks like the other key (the private one) is not in the client ~/.ssh directory:
```
debug1: Trying private key: /home/mason/.ssh/id_rsa
debug3: no such identity: /home/mason/.ssh/id_rsa: No such file or directory
debug1: Trying private key: /home/mason/.ssh/id_dsa
debug3: no such identity: /home/mason/.ssh/id_dsa: No such file or directory
```
Could you check is there? and if is not move it to ~/.ssh

Another question, do you have an encrypted home partition?

Regards.

---

### Post by John_Patrick_Mason on 2017-04-15
[QUOTE=papibe]Now it looks like the other key (the private one) is not in the client ~/.ssh directory:[/QUOTE]
By "client" you mean the machine running the ssh-server. This is so that the following command:

```
ssh mason@localhost
```
will work on the server, am I right?

[QUOTE=papibe]Another question, do you have an encrypted home partition?[/QUOTE]

*Yes*, that was going to be my next question.

---

### Post by again? on 2017-04-15
The key pairs are created on the client... ie the machine you want to use to connect to an ssh server.
You then copy the content of  **~/.ssh/id_rsa.pub** on the client to the **~/.ssh/authorized_keys** file on the server machine.

So you would plug your usb with the client's id_rsa.pub into the ssh server machine and the run
```
cat [COLOR="#FF0000"]/path/to/usb[/COLOR]/id_rsa.pub >> ~/.ssh/authorized_keys
```

In /etc/ssh/sshd_config the only changes I made were to restrict the users and disable passwords
```
PasswordAuthentication no
AllowUsers daniel

```
daniel is the user name of the account where the ssh server is running.

I don't use encryption so don't know if that's an issue or not but your link in first post appears to have the solution.
May want to wait for papibe to answer though.

---

### Post by papibe on 2017-04-16
> **John_Patrick_Mason said:**
> *Yes*, that was going to be my next question.
Alright.

We need to change the configuration. SSH won't be able to read from the partition, thus reading the key, before you login.

Change the /etc/ssh/sshd_config. Edit this line:
```
#AuthorizedKeysFile %h/.ssh/authorized_keys
```
So that looks like this:
```
AuthorizedKeysFile /etc/ssh/%u/authorized_keys
```
Then create the directory and copy the file:
```
sudo mkdir /etc/ssh/$USER

sudo chmod 700 /etc/ssh/$USER

sudo cp ~/.ssh/authorized_keys /etc/ssh/$USER
```
Finally restart the ssh service:
```
sudo systemctl restart ssh.service 
```
Try connecting using ssh again. Let us know how it goes.
Regards.

---

### Post by John_Patrick_Mason on 2017-04-16
[QUOTE=papibe]
Alright.

We need to change the configuration. SSH won't be able to read from the partition, thus reading the key, before you login.
[/QUOTE]

OK, before I do the things you said, I need to know whether you also want me to transfer the private key to the machine running openssh-server. The reason I'm asking is because the private key is already saved in the .ssh folder on the client. That's why I am a bit confused.

---

### Post by again? on 2017-04-16
You only need copy over **id_rsa.pub** from client to the servers ~/.ssh/authorized_keys file as in post #10.
In post #11 the commands change the location where ssh looks for the authorized_keys file 
and copies it to this location.(/etc/ssh/$USER/authorized_keys)

---

### Post by papibe on 2017-04-16
> **John_Patrick_Mason said:**
> OK, before I do the things you said, I need to know whether you also want me to transfer the private key to the machine running openssh-server. The reason I'm asking is because the private key is already saved in the .ssh folder on the client. That's why I am a bit confused.

Much like guber2 said....

The private key should be only in the client, that is, the machine that is going to run the command 'ssh mason_IP'.

Only if you want to test locally (running 'ssh localhost' on the server itself), you would need to also copy the private key to your local ~/.ssh directory

Does that help?
Regards.

---

### Post by John_Patrick_Mason on 2017-04-16
OK, so I deleted the private key from the server, made the changes in post #11 also on the server, then typed:

```

ssh mason@Lubuntu-Desktop


```

from the host, and got the following error again:

```


ssh: Could not resolve hostname lubuntu-desktop: Name or service not known


```

In one of the posts, it was mentioned that I needed to use the IP address of the server. So my question is, how do I go about finding that piece of information?

---

### Post by papibe on 2017-04-16
> **John_Patrick_Mason said:**
> how do I go about finding that piece of information?
Log into the machine Lubuntu-Desktop. Open a terminal and run this command:
```
ip addr
```
I should be something like:
```
inet 192.168.x.xx/24
```
If you are not sure, post the output of the command.

Regards.

---

### Post by John_Patrick_Mason on 2017-04-16
Just tried to connect to the server with the new IP address. All what I got was a blinking cursor with no prompt return.
When I first tried using ssh, I disabled X11 Forwarding and Tcp forwarding in the sshd_config file. Could that be causing any issues?
I'm posting the results just in case, to make sure I'm using the right IP address:

```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp6s8: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether 00:11:11:e4:3a:5b brd ff:ff:ff:ff:ff:ff
3: wlx9cefd5fe9817: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 9c:ef:d5:fe:98:17 brd ff:ff:ff:ff:ff:ff
    inet 10.0.0.158/24 brd 10.0.0.255 scope global dynamic wlx9cefd5fe9817
       valid_lft 561614sec preferred_lft 561614sec
    inet6 2601:19c:c000:a548::4e84/128 scope global dynamic 
       valid_lft 561617sec preferred_lft 561617sec
    inet6 2601:19c:c000:a548:68cf:f771:68:f9e6/64 scope global noprefixroute dynamic 
       valid_lft 182123sec preferred_lft 182123sec
    inet6 fe80::96ed:8605:883:cb39/64 scope link 
       valid_lft forever preferred_lft forever


```

---

### Post by papibe on 2017-04-16
Could you post a verbose try?
```
ssh -vvv 192.168.x.xx
```
with the proper address.

Regards.

---

### Post by John_Patrick_Mason on 2017-04-16
Please reread my previous post. I want to make sure I'm using the right IP address.

---

### Post by papibe on 2017-04-16
It should be 10.0.0.158

Try:
```
ping 10.0.0.158

ssh -vvv 10.0.0.158
```

---

### Post by John_Patrick_Mason on 2017-04-16
Ping seems to work fine. Maybe a firewall issue?

```


mason@Lubuntu-Desktop:~$ ssh -vvv 10.0.0.158

OpenSSH_7.2p2 Ubuntu-4ubuntu2.1, OpenSSL 1.0.2g  1 Mar 2016
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: resolving "10.0.0.158" port 22
debug2: ssh_connect_direct: needpriv 0
debug1: Connecting to 10.0.0.158 [10.0.0.158] port 22.
debug1: Connection established.
debug1: key_load_public: No such file or directory
debug1: identity file /home/mason/.ssh/id_rsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/mason/.ssh/id_rsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/mason/.ssh/id_dsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/mason/.ssh/id_dsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/mason/.ssh/id_ecdsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/mason/.ssh/id_ecdsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/mason/.ssh/id_ed25519 type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/mason/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_7.2p2 Ubuntu-4ubuntu2.1
debug1: Remote protocol version 2.0, remote software version OpenSSH_7.2p2 Ubuntu-4ubuntu2.1
debug1: match: OpenSSH_7.2p2 Ubuntu-4ubuntu2.1 pat OpenSSH* compat 0x04000000
debug2: fd 3 setting O_NONBLOCK
debug1: Authenticating to 10.0.0.158:22 as 'mason'
debug3: hostkeys_foreach: reading file "/home/mason/.ssh/known_hosts"
debug3: send packet: type 20
debug1: SSH2_MSG_KEXINIT sent
debug3: receive packet: type 20
debug1: SSH2_MSG_KEXINIT received
debug2: local client KEXINIT proposal
debug2: KEX algorithms: curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,ext-info-c
debug2: host key algorithms: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-ed25519-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-ed25519,rsa-sha2-512,rsa-sha2-256,ssh-rsa
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
debug2: KEX algorithms: curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha1
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
debug1: Server host key: ecdsa-sha2-nistp256 SHA256:QDl2pBwyqIWEgUcL4SgLHK6EXLYlJxJe3G5KOU9lBwU
debug3: hostkeys_foreach: reading file "/home/mason/.ssh/known_hosts"
The authenticity of host '10.0.0.158 (10.0.0.158)' can't be established.
ECDSA key fingerprint is SHA256:QDl2pBwyqIWEgUcL4SgLHK6EXLYlJxJe3G5KOU9lBwU.
Are you sure you want to continue connecting (yes/no)? y
Please type 'yes' or 'no': yes
Warning: Permanently added '10.0.0.158' (ECDSA) to the list of known hosts.
debug3: send packet: type 21
debug2: set_newkeys: mode 1
debug1: rekey after 134217728 blocks
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug3: receive packet: type 21
debug2: set_newkeys: mode 0
debug1: rekey after 134217728 blocks
debug1: SSH2_MSG_NEWKEYS received
debug2: key: /home/mason/.ssh/id_rsa ((nil))
debug2: key: /home/mason/.ssh/id_dsa ((nil))
debug2: key: /home/mason/.ssh/id_ecdsa ((nil))
debug2: key: /home/mason/.ssh/id_ed25519 ((nil))
debug3: send packet: type 5
debug3: receive packet: type 7
debug1: SSH2_MSG_EXT_INFO received
debug1: kex_input_ext_info: server-sig-algs=<rsa-sha2-256,rsa-sha2-512>
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
debug1: Trying private key: /home/mason/.ssh/id_rsa
debug3: no such identity: /home/mason/.ssh/id_rsa: No such file or directory
debug1: Trying private key: /home/mason/.ssh/id_dsa
debug3: no such identity: /home/mason/.ssh/id_dsa: No such file or directory
debug1: Trying private key: /home/mason/.ssh/id_ecdsa
debug3: no such identity: /home/mason/.ssh/id_ecdsa: No such file or directory
debug1: Trying private key: /home/mason/.ssh/id_ed25519
debug3: no such identity: /home/mason/.ssh/id_ed25519: No such file or directory
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey).


```

---

### Post by papibe on 2017-04-16
```
debug1: Trying private key: /home/mason/.ssh/id_rsa
debug3: no such identity: /home/mason/.ssh/id_rsa: No such file or directory
debug1: Trying private key: /home/mason/.ssh/id_dsa
debug3: no such identity: /home/mason/.ssh/id_dsa: No such file or directory
debug1: Trying private key: /home/mason/.ssh/id_ecdsa
debug3: no such identity: /home/mason/.ssh/id_ecdsa: No such file or directory
debug1: Trying private key: /home/mason/.ssh/id_ed25519
debug3: no such identity: /home/mason/.ssh/id_ed25519: No such file or directory
```
It looks like the private key is not on the client. Did you rename the private key? 

Could you post the output of this on the client?
```
ls -la ~/.ssh
```
Regards.

---

### Post by John_Patrick_Mason on 2017-04-16
[QUOTE=papibe]It looks like the private key is not on the client. Did you rename the private key?[/QUOTE]

OK, this isn't the first time this question has come up. By "client" do you mean the machine running Ubuntu or Lubuntu?
Cause I ran the following command:

```

ssh -vvv 10.0.0.158


```

on the machine running the openssh-server, that is, on my Lubuntu machine.

---

### Post by John_Patrick_Mason on 2017-04-16
This on the *Ubuntu* client:

```

mason@Ubuntu-Laptop:~$ ls -la ~/.ssh

total 40
drwx------  2 mason mason  4096 Apr 13 19:32 .
drwx------ 28 mason mason 12288 Apr 16 21:48 ..
-rw-------  1 mason mason  1766 Apr 13 19:32 id_rsa
-rw-r--r--  1 mason mason   401 Apr 13 19:32 id_rsa.pub

```

---

### Post by John_Patrick_Mason on 2017-04-17
In post #1 in the link I provided, they did something similar to this:

```

sudo mkdir /etc/ssh/$USER

sudo chmod 700 /etc/ssh/$USER

sudo cp ~/.ssh/authorized_keys /etc/ssh/$USER
```

The only difference is that they suggested changing the directory owner of /etc/ssh/mason, since by default it would be owned by the root user. Maybe that's what's causing issues. Also, whenever I do a fresh install of Ubuntu or Lubuntu, I always do:

```

chmod -v 700 $HOME

```

to prevent other users from accessing files from my account. Maybe that could be an issue.

---

### Post by papibe on 2017-04-17
A few distinctions:

**server**: the machine running the openssh-server package. The machine that receives connections. The machine you want to connect to.

**client**: the machine that runs the command 'ssh -vvv 10.0.0.158'. The machine opening a terminal window to connect to the server. 

I believe you're running the ssh -vvv ... on the server, that's the reason there's not private key there.

Yes, you are right. I think it would be better to change the ownership of /etc/ssh/$USER to your own user. On the server:
```
sudo chown -R $USER:$USER /etc/ssh/$USER
```

Let us know how it goes.
Regards.

---

### Post by John_Patrick_Mason on 2017-04-17
I get it now. The reason I was initially confused on whether to run the command on the client or on the server is because when you first asked me to run the same command with the same options, you asked me to do it on the server. But that was when I was trying to get the server to connect to itself through localhost.

Here is the output of the commands you asked me to execute on the client:

```

mason@Ubuntu-Laptop:~$ ls -la ~/.ssh

total 40
drwx------  2 mason mason  4096 Apr 13 19:32 .
drwx------ 28 mason mason 12288 Apr 17 18:37 ..
-rw-------  1 mason mason  1766 Apr 13 19:32 id_rsa
-rw-r--r--  1 mason mason   401 Apr 13 19:32 id_rsa.pub

```

```

mason@Ubuntu-Laptop:~$ ssh -vvv 10.0.0.158

OpenSSH_7.2p2 Ubuntu-4ubuntu2.1, OpenSSL 1.0.2g  1 Mar 2016
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: resolving "10.0.0.158" port 22
debug2: ssh_connect_direct: needpriv 0
debug1: Connecting to 10.0.0.158 [10.0.0.158] port 22.
debug1: connect to address 10.0.0.158 port 22: Connection timed out
ssh: connect to host 10.0.0.158 port 22: Connection timed out

```

Ping works fine from the client, no packet loss or anything.

---

### Post by papibe on 2017-04-17
10.0.0.158 is the IP of the server, right?

Does ping works from the client?
```
ping 10.0.0.158
```
If so, check if you have a firewall, or iptables running on the server. You can 'nmap' the server from the client, to see if the port is open:
```
nmap 10.0.0.158
```
Then, check if the client is in the same network segment, that is, it has an address like 10.0.0.xx.

Let us know how it goes.
Regards.

---

### Post by John_Patrick_Mason on 2017-04-17
[QUOTE=papibe]
10.0.0.158 is the IP of the server, right?
[/QUOTE]

I think so. That's what you told me to use.

[QUOTE=papibe]
Does ping works from the client?
[/QUOTE]

Yep. Here is the output, just in case:

```

mason@Ubuntu-Laptop:~$ ping 10.0.0.158

PING 10.0.0.158 (10.0.0.158) 56(84) bytes of data.
64 bytes from 10.0.0.158: icmp_seq=1 ttl=64 time=1.73 ms
64 bytes from 10.0.0.158: icmp_seq=2 ttl=64 time=2.00 ms
64 bytes from 10.0.0.158: icmp_seq=3 ttl=64 time=1.63 ms
64 bytes from 10.0.0.158: icmp_seq=4 ttl=64 time=1.89 ms
64 bytes from 10.0.0.158: icmp_seq=5 ttl=64 time=2.21 ms
64 bytes from 10.0.0.158: icmp_seq=6 ttl=64 time=4.12 ms
64 bytes from 10.0.0.158: icmp_seq=7 ttl=64 time=2.24 ms
64 bytes from 10.0.0.158: icmp_seq=8 ttl=64 time=1.73 ms
64 bytes from 10.0.0.158: icmp_seq=9 ttl=64 time=2.30 ms
64 bytes from 10.0.0.158: icmp_seq=10 ttl=64 time=1.81 ms
^C
--- 10.0.0.158 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9014ms
rtt min/avg/max/mdev = 1.630/2.171/4.127/0.689 ms

```

[QUOTE=papibe]
If so, check if you have a firewall, or iptables running on the server.
[/QUOTE]

I'm not sure what iptables are, but I do know for a fact that there is a firewall running on the server.

Had to install nmap first. This is what I got for its output:

```

mason@Ubuntu-Laptop:~$ nmap 10.0.0.158

Starting Nmap 7.01 ( https://nmap.org ) at 2017-04-17 22:05 EDT
Note: Host seems down. If it is really up, but blocking our ping probes, try -Pn
Nmap done: 1 IP address (0 hosts up) scanned in 3.08 seconds


```

The IP address of the client starts the same way as the server's IP address: 10.0.0.xx.

---

### Post by papibe on 2017-04-17
The nmap does not show any port open so you have a very strict firewall: no ports open.

Which firewall are you using? You need to open the port 22.

Regards/

---

### Post by John_Patrick_Mason on 2017-04-17
[QUOTE=papibe]
Which firewall are you using?
[/QUOTE]

The default firewall that comes with Lubuntu. This is the command I typed after doing a fresh install of Lubuntu:

```

sudo ufw enable

```

as explained [here]("https://sites.google.com/site/easylinuxtipsproject/first-lubuntu#TOC-Turn-on-the-firewall") under "turn on firewall".

I'm not yet familiar with the commands needed to open port 22 through the terminal; I only know how to configure the firewall through Gufw.

---

### Post by papibe on 2017-04-17
It's pretty easy from the command line. This should work on the server:
```
sudo ufw allow ssh
```
If not, try this:
```
sudo ufw allow 22
```
Try connecting again from the client, and let us know how that went.
Regards.

---

### Post by John_Patrick_Mason on 2017-04-18
*Yes*, I'm in! I had a feeling it had something to do with the firewall.

Thanks a bunch, papibe.

Now, how do I open a new tab on an existing running instance of Firefox?

I tried typing:

```

firefox -new-tab arstechnica.com

```

but got an error message:

```

Error: GDK_BACKEND does not match available displays

```

Tried doing:

```

firefox -new-window arstechnica.com

```

got the same error message.

Tried:

```

google-chrome -new-window arstechnica.com

```

and got a different error message:
```

[20735:20735:0418/001236.324278:ERROR:browser_main_loop.cc(279)] Gtk: cannot open display: 

```

---

### Post by papibe on 2017-04-18
> **John_Patrick_Mason said:**
> *Yes*, I'm in!
Yay! :D

Regarding the remote Firefox tabs: take a look at [this]("https://askubuntu.com/questions/802877/x11-errors-over-ssh"). You may need to tune a few ssh options in both the client and the server.

You may also try creating a new Firefox profile for the pages from the remote pages:
```
firefox -ProfileManager -no-remote
```
Then you should be able to open remote tabs in a different profile than you currently, local, Firefox:
```
firefox -P remoteProfile -new-tab -url google.com
```
where remoteProfile is the name of the new profile.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by John_Patrick_Mason on 2017-04-18
> **papibe said:**
> Yay! :D

Regarding the remote Firefox tabs: take a look at [this]("https://askubuntu.com/questions/802877/x11-errors-over-ssh"). You may need to tune a few ssh options in both the client and the server.

You may also try creating a new Firefox profile for the pages from the remote pages:
```
firefox -ProfileManager -no-remote
```
Then you should be able to open remote tabs in a different profile than you currently, local, Firefox:
```
firefox -P remoteProfile -new-tab -url google.com
```
where remoteProfile is the name of the new profile.

Hope it helps. Let us know how it goes.
Regards.

OK, so I re-enabled X11 forwarding on the server, ssh'd into the server from the client using:

```

ssh -X mason@10.0.0.158

```

, created a new profile for Firefox called Test_Profile using:

```

firefox -ProfileManager -no-remote

```

, closed the Firefox session that pops up after entering the command,

and then typed:

```

firefox -P Test_Profile -new-tab -url arstechnica.com

```

Then, after that, I typed:

```
top
```

on the server to see if it worked, and found what seemed like two running instances of Firefox. One associated with PID 11883 and another with PID 11330. So that means I got it to work, right?

---

### Post by John_Patrick_Mason on 2017-04-20
I was kinda hoping that I would be able to see a new Firefox window open *on the server*. Is there any way I can make that happen from the client?

---

### Post by papibe on 2017-04-20
> **John_Patrick_Mason said:**
> I was kinda hoping that I would be able to see a new Firefox window open *on the server*. Is there any way I can make that happen from the client?
Sure. I think that's easier than X forwarding.

Call ssh without x-forwarding, just like a regular ssh:
```
ssh mason@10.0.0.158
```
and then call a GUI app like this:
```
DISPLAY=:0 firefox
```
(the latter suppose just one X session, which is the most common situation)

Hope it helps. Let us know if that works.
Regards.

---

### Post by John_Patrick_Mason on 2017-04-20
Tried typing:  ```
 DISPLAY=:0 firefox 
```  got the following error:  ```
 Failed to connect to Mir: Failed to connect to server socket: No such file or directory Unable to init server: Could not connect: Connection refused Error: cannot open display: :0 
```  I didn't notice any window opening on the server either.

---

### Post by papibe on 2017-04-21
You have to be running the desktop on the server in order for that to work

Firefox is a little tricker to run. Try something simpler like a terminal window:
```
DISPLAY=:0 lxterminal
```

If that's working, consider this other options to launch Firefox:
```
DISPLAY=:0 firefox -P Test_Profile -new-tab -url arstechnica.com
```
or this:
```
DISPLAY=:0 firefox -no-remote -P Test_Profile -new-tab -url arstechnica.com
```
Regards.

---

### Post by John_Patrick_Mason on 2017-04-21
Tried:

```

DISPLAY=:0 lxterminal

```

got the following error:

```

(lxterminal:2962): Gtk-WARNING **: cannot open display: :0

```

Tried:

```

DISPLAY=:0 firefox -P Test_Profile -new-tab -url arstechnica.com

```

got the following error:

```

Failed to connect to Mir: Failed to connect to server socket: No such file or directory
Unable to init server: Could not connect: Connection refused
Error: cannot open display: :0

```

Tried:

```

DISPLAY=:0 firefox -no-remote -P Test_Profile -new-tab -url arstechnica.com

```

got the following error:

```

Failed to connect to Mir: Failed to connect to server socket: No such file or directory
Unable to init server: Could not connect: Connection refused
Error: cannot open display: :0

```

I disabled Tcp forwarding, don't know if that matters. Server was up and running when I inputed the above commands.

---

