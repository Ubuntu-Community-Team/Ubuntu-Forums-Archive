---
title: "scp lost connection"
date: 2019-04-16
forum: Networking &amp; Wireless
---

### Post by caseinpoint2 on 2019-04-16
Tried sending a file between two Ubuntu 18.04 machines with scp, but got the following:

```
$ scp -vi [pem key] [file] ububuntu@[ip address]:/home/ubuntu
Executing: program /usr/bin/ssh host [ip address], user ububuntu, command scp -v -t /home/ubuntu
OpenSSH_7.6p1 Ubuntu-4ubuntu0.3, OpenSSL 1.0.2n  7 Dec 2017
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to [ip address] port 22.
debug1: Connection established.
debug1: key_load_public: No such file or directory
debug1: identity file [pem key] type -1
debug1: key_load_public: No such file or directory
debug1: identity file [pem key]-cert type -1
debug1: Local version string SSH-2.0-OpenSSH_7.6p1 Ubuntu-4ubuntu0.3
debug1: Remote protocol version 2.0, remote software version OpenSSH_7.6p1 Ubuntu-4ubuntu0.3
debug1: match: OpenSSH_7.6p1 Ubuntu-4ubuntu0.3 pat OpenSSH* compat 0x04000000
debug1: Authenticating to [ip address]:22 as 'ububuntu'
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: algorithm: curve25519-sha256
debug1: kex: host key algorithm: ecdsa-sha2-nistp256
debug1: kex: server->client cipher: [EMAIL="chacha20-poly1305@openssh.com"]chacha20-poly1305@openssh.com[/EMAIL] MAC: <implicit> compression: none
debug1: kex: client->server cipher: [EMAIL="chacha20-poly1305@openssh.com"]chacha20-poly1305@openssh.com[/EMAIL] MAC: <implicit> compression: none
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ecdsa-sha2-nistp256 SHA256:Q8y6SB4PFcHn7ZcNvJmn3MMFKibE2fU75PZAqX2F90Q
debug1: Host '13.59.198.223' is known and matches the ECDSA host key.
debug1: Found key in /home/drue/.ssh/known_hosts:9
debug1: rekey after 134217728 blocks
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: rekey after 134217728 blocks
debug1: SSH2_MSG_EXT_INFO received
debug1: kex_input_ext_info: server-sig-algs=<ssh-ed25519,ssh-rsa,rsa-sha2-256,rsa-sha2-512,ssh-dss,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521>
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Trying private key: [pem key]
Connection closed by [ip address] port 22
lost connection
```

Why is this happening, and how do I fix it? Thanks.

---

### Post by TheFu on 2019-04-17
Add some more 'v's to the command and look at what the server is seeing.

It could be that your .bashrc is doing things that break non-interactive connections.  At the top, you can check for that and return.

```

 #If not running interactively, don't do anything
[ -z "$PS1" ] && return
```

But add a few more -vvv to the ssh command to see more debug info. There should be an error you can google.

---

### Post by caseinpoint2 on 2019-04-17
Nevermind, typo in the username.  Thanks, though.

---

### Post by TheFu on 2019-04-17
If that is the issue, then fix it so it never happens again using the ~/.ssh/config file.  Every ssh-based tool honors it. scp, rsync, rdiff-backup, sftp, vim, ... and the 50 other tools too. 
The manpage for ssh_config explains what to put into it.
[https://blog.jdpfu.com/2011/07/14/easy-key-based-ssh-authentication](https://blog.jdpfu.com/2011/07/14/easy-key-based-ssh-authentication) has the sort-form of the config for 1 remote system.
```
host short-name
 user jdpfu
 hostname remote-server.dyndns.org
 port 62280
```

Then use **scp /tmp/somefile* short-name:** to push files over.  That will get expanded automatically for the userid, remote server (name or IP), and non-standard port.

If you need to use a different key, cipher, or any other connection setting, then that can be put into the host stanza too. As many stanzas as you like.

And it would be helpful if this thread was marked as "SOLVED" to help the community.  Thread tools button above.

---

