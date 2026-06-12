---
title: "SSH/OpenSSH/Keys: problem with some Ubuntu installation"
date: 2014-04-26
forum: Networking &amp; Wireless
---

### Post by erotavlas on 2014-04-26
Hi,

I read this guide about to use the key to login in a remote machine [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys). It works well with many different Linux distributions and also with Ubuntu server 12.04. I have some machines with Ubuntu server 12.04 for which after I have followed the guide, it still necessary to type the password. For those machines, I checked if the folder ~/.ssh has the same permissions of the same folder for the machines for which the procedure works.
I cannot figure out why. Do you have any suggestions?

Thank you

---

### Post by steeldriver on 2014-04-26
Have your tried running the ssh client with verbosity turned up?

```

ssh -v user@remotehost

ssh -vv user@remotehost

ssh -vvv user@remotehost

```

Sometimes it helps to see exactly what point in the authentication process it drops back to requesting a password

---

### Post by erotavlas on 2014-04-27
Ok, thank you. The message is the following, only the last part related to authentication.  ssh -vvv user@remotehost

```

debug1: Found key in /home/user/.ssh/known_hosts:1
debug1: ssh_ecdsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/user/.ssh/id_rsa (0xbac8a0),
debug2: key: /home/user/.ssh/id_dsa ((nil)),
debug2: key: /home/user/.ssh/id_ecdsa ((nil)),
debug1: Authentications that can continue: publickey,gssapi-keyex,gssapi-with-mic,password
debug3: start over, passed a different list publickey,gssapi-keyex,gssapi-with-mic,password
debug3: preferred publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/user/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,gssapi-keyex,gssapi-with-mic,password
debug1: Trying private key: /home/user/.ssh/id_dsa
debug3: no such identity: /home/user/.ssh/id_dsa: No such file or directory
debug1: Trying private key: /home/user/.ssh/id_ecdsa
debug3: no such identity: /home/user/.ssh/id_ecdsa: No such file or directory
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password

```

So it seems that it tries to use public key but it does not work. Do you understand why?
Thank

---

### Post by Lars Noodén on 2014-04-27
It tries the file id_rsa,

debug1: Offering RSA public key: /home/user/.ssh/id_rsa

Is that the right file name?  You can specify another file name using -i

```

ssh -i ~/.ssh/some_rsa_key server.example.org

```

Do you have the right public key loaded on to the server?  Is the public key there whole and unbroken on a single line within ~/.ssh/authorized_keys on the server?  I would try copying it anew.  

Or do those servers have a custom AuthorizedKeysFile setting in /etc/ssh/sshd_config, or are they using encrypted partitions?

Just things to check.

---

### Post by erotavlas on 2014-04-29
> debug1: Offering RSA public key: /home/user/.ssh/id_rsa
Yes it is the right key and it is the same of the other machines.
> Do you have the right public key loaded on to the server?  Is the public  key there whole and unbroken on a single line within  ~/.ssh/authorized_keys on the server?  I would try copying it anew.
I have just recopied the id_rsa.pub key on the server in ~/.ssh and I have executed the command cat id_rsa.pub >> authorized_keys
>  Or do those servers have a custom AuthorizedKeysFile setting in /etc/ssh/sshd_config, or are they using encrypted partitions?
The servers do not use encrypted partitions and the AuthorizedKeysFile setting in /etc/ssh/sshd_config is the default equal for all the machines.

It is very strange...

---

### Post by Lars Noodén on 2014-04-29
Then it might be time to look at what the server says.  Can you log in to the server and then start a second instance of sshd on a new port in debug mode?

```

sudo /usr/sbin/sshd -p 5555 -dd

```

You might have to open a port (temporarily) to do that.  

Then try connecting to that new port and see what complaints if any come from the server when trying the key pair.

---

### Post by erotavlas on 2014-05-02
Hi,

unfortunately I cannot start a second instance since I'm not root user. Is there a way to look at log of the current instance of the server?

---

### Post by erotavlas on 2014-05-02
Sorry, duplicate post.

---

### Post by Lars Noodén on 2014-05-02
The current instance of the ssh server will be logging to /var/log/auth.log.  You would be able to read that log file if you are a member of the group adm, but that won't be as verbose as using the -d option.  

If you're really pressed, you might be able to point to a second config file, copied from the original, using the -f option.  The original config file should be readable and thus copyable.  You'd have to point out new keys in the file because the normal ones will be unreadable to a non-root user.

```

sshd -p 5555 -f /home/erotavlas/sshd_config.test -d

```

---

### Post by erotavlas on 2014-05-02
Ok, this works! The message from server is this
```

debug1: HPN Buffer Size: 87380
debug1: sshd version OpenSSH_6.2, OpenSSL 1.0.1 14 Mar 2012
debug1: read PEM private key done: type RSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: private host key: #0 type 1 RSA
debug1: read PEM private key done: type DSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: private host key: #1 type 2 DSA
debug1: read PEM private key done: type ECDSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.ECDSA-256
debug1: Checking blacklist file /etc/ssh/blacklist.ECDSA-256
debug1: private host key: #2 type 3 ECDSA
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-p'
debug1: rexec_argv[2]='5555'
debug1: rexec_argv[3]='-f'
debug1: rexec_argv[4]='/home/erotavlas/sshd_config.test'
debug1: rexec_argv[5]='-d'
Set /proc/self/oom_score_adj from 0 to -1000
debug1: Bind to port 5555 on 0.0.0.0.
debug1: Server TCP RWIN socket size: 87380
debug1: HPN Buffer Size: 87380
Server listening on 0.0.0.0 port 5555.
debug1: Bind to port 5555 on ::.
debug1: Server TCP RWIN socket size: 87380
debug1: HPN Buffer Size: 87380
Server listening on :: port 5555.
debug1: Server will not fork when running in debugging mode.
debug1: rexec start in 5 out 5 newsock 5 pipe -1 sock 8
debug1: inetd sockets after dupping: 3, 3
Connection from IP port 40888
debug1: HPN Disabled: 0, HPN Buffer Size: 87380
debug1: Client protocol version 2.0; client software version OpenSSH_6.6p1 Ubuntu-2ubuntu1
SSH: Server;Ltype: Version;Remote: IP-40888;Protocol: 2.0;Client: OpenSSH_6.6p1 Ubuntu-2ubuntu1
debug1: match: OpenSSH_6.6p1 Ubuntu-2ubuntu1 pat OpenSSH*
debug1: Remote is NON-HPN aware
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.2p2-hpn14v1 Ubuntu-6hpn14v1~wrouesnel~precise2
debug1: permanently_set_uid: 105/65534 [preauth]
debug1: MYFLAG IS 1 [preauth]
debug1: list_hostkey_types: ssh-rsa,ssh-dss,ecdsa-sha2-nistp256 [preauth]
debug1: SSH2_MSG_KEXINIT sent [preauth]
debug1: SSH2_MSG_KEXINIT received [preauth]
debug1: AUTH STATE IS 0 [preauth]
debug1: REQUESTED ENC.NAME is 'aes128-ctr' [preauth]
debug1: kex: client->server aes128-ctr hmac-md5-etm@openssh.com none [preauth]
SSH: Server;Ltype: Kex;Remote: IP-40888;Enc: aes128-ctr;MAC: hmac-md5-etm@openssh.com;Comp: none [preauth]
debug1: REQUESTED ENC.NAME is 'aes128-ctr' [preauth]
debug1: kex: server->client aes128-ctr hmac-md5-etm@openssh.com none [preauth]
debug1: expecting SSH2_MSG_KEX_ECDH_INIT [preauth]
debug1: SSH2_MSG_NEWKEYS sent [preauth]
debug1: expecting SSH2_MSG_NEWKEYS [preauth]
debug1: SSH2_MSG_NEWKEYS received [preauth]
debug1: KEX done [preauth]
debug1: userauth-request for user erotavlas service ssh-connection method none [preauth]
SSH: Server;Ltype: Authname;Remote: IP-40888;Name: erotavlas [preauth]
debug1: attempt 0 failures 0 [preauth]
debug1: userauth-request for user erotavlas service ssh-connection method publickey [preauth]
debug1: attempt 1 failures 0 [preauth]
debug1: test whether pkalg/pkblob are acceptable [preauth]
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: temporarily_use_uid: 1001/1001 (e=0/0)
debug1: trying public key file /home/erotavlas/.ssh/authorized_keys
debug1: fd 4 clearing O_NONBLOCK
Authentication refused: bad ownership or modes for directory /home/erotavlas
debug1: restore_uid: 0/0
debug1: temporarily_use_uid: 1001/1001 (e=0/0)
debug1: trying public key file /home/erotavlas/.ssh/authorized_keys2
debug1: Could not open authorized keys '/home/erotavlas/.ssh/authorized_keys2': No such file or directory
debug1: restore_uid: 0/0
Failed publickey for erotavlas from IP port 40888 ssh2
debug1: userauth-request for user erotavlas service ssh-connection method keyboard-interactive [preauth]
debug1: attempt 2 failures 1 [preauth]
debug1: keyboard-interactive devs  [preauth]
debug1: auth2_challenge: user=erotavlas devs= [preauth]
debug1: kbdint_alloc: devices '' [preauth]
debug1: userauth-request for user erotavlas service ssh-connection method password [preauth]
debug1: attempt 3 failures 2 [preauth]
Accepted password for erotavlas from IP port 40888 ssh2
debug1: monitor_child_preauth: erotavlas has been authenticated by privileged process
debug1: monitor_read_log: child log fd closed
User child is on pid 10782
debug1: SELinux support disabled
debug1: permanently_set_uid: 1001/1001
debug1: Single to Multithreaded CTR cipher swap - server request
debug1: Entering interactive session for SSH2.
debug1: server_init_dispatch_20
debug1: need rekeying
debug1: SSH2_MSG_KEXINIT sent
debug1: server_input_channel_open: ctype session rchan 0 win 1048576 max 16384
debug1: input_session_request
debug1: channel 0: new [server-session]
debug1: session_new: session 0
debug1: session_open: channel 0
debug1: session_open: session 0: link with channel 0
debug1: server_input_channel_open: confirm session
debug1: enqueue packet: 91
debug1: server_input_global_request: rtype no-more-sessions@openssh.com want_reply 0
debug1: SSH2_MSG_KEXINIT received
debug1: AUTH STATE IS 1
debug1: REQUESTED ENC.NAME is 'aes128-ctr'
debug1: kex: client->server aes128-ctr hmac-md5-etm@openssh.com none
SSH: Server;Ltype: Kex;Remote: IP-40888;Enc: aes128-ctr;MAC: hmac-md5-etm@openssh.com;Comp: none
debug1: REQUESTED ENC.NAME is 'aes128-ctr'
debug1: kex: server->client aes128-ctr hmac-md5-etm@openssh.com none
debug1: expecting SSH2_MSG_KEX_ECDH_INIT
debug1: set_newkeys: rekeying
debug1: spawned a thread
debug1: spawned a thread
debug1: dequeue packet: 91
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: set_newkeys: rekeying
debug1: spawned a thread
debug1: spawned a thread
debug1: SSH2_MSG_NEWKEYS received
debug1: server_input_channel_req: channel 0 request pty-req reply 1
debug1: session_by_channel: session 0 channel 0
debug1: session_input_channel_req: session 0 req pty-req
debug1: Allocating pty.
debug1: session_new: session 0
debug1: SELinux support disabled
debug1: session_pty_req: session 0 alloc /dev/pts/23
debug1: server_input_channel_req: channel 0 request env reply 0
debug1: session_by_channel: session 0 channel 0
debug1: session_input_channel_req: session 0 req env
debug1: server_input_channel_req: channel 0 request env reply 0
debug1: session_by_channel: session 0 channel 0
debug1: session_input_channel_req: session 0 req env
debug1: server_input_channel_req: channel 0 request env reply 0
debug1: session_by_channel: session 0 channel 0
debug1: session_input_channel_req: session 0 req env
debug1: server_input_channel_req: channel 0 request env reply 0
debug1: session_by_channel: session 0 channel 0
debug1: session_input_channel_req: session 0 req env
debug1: server_input_channel_req: channel 0 request env reply 0
debug1: session_by_channel: session 0 channel 0
debug1: session_input_channel_req: session 0 req env
debug1: server_input_channel_req: channel 0 request env reply 0
debug1: session_by_channel: session 0 channel 0
debug1: session_input_channel_req: session 0 req env
debug1: server_input_channel_req: channel 0 request env reply 0
debug1: session_by_channel: session 0 channel 0
debug1: session_input_channel_req: session 0 req env
debug1: server_input_channel_req: channel 0 request env reply 0
debug1: session_by_channel: session 0 channel 0
debug1: session_input_channel_req: session 0 req env
debug1: server_input_channel_req: channel 0 request env reply 0
debug1: session_by_channel: session 0 channel 0
debug1: session_input_channel_req: session 0 req env
debug1: server_input_channel_req: channel 0 request env reply 0
debug1: session_by_channel: session 0 channel 0
debug1: session_input_channel_req: session 0 req env
debug1: server_input_channel_req: channel 0 request shell reply 1
debug1: session_by_channel: session 0 channel 0
debug1: session_input_channel_req: session 0 req shell
debug1: Setting controlling tty using TIOCSCTTY.
debug1: Received SIGCHLD.
debug1: session_by_pid: pid 10907
debug1: session_exit_message: session 0 channel 0 pid 10907
debug1: session_exit_message: release channel 0
debug1: session_by_tty: session 0 tty /dev/pts/23
debug1: session_pty_cleanup: session 0 release /dev/pts/23
debug1: session_by_channel: session 0 channel 0
debug1: session_close_by_channel: channel 0 child 0
debug1: session_close: session 0 pid 0
debug1: channel 0: free: server-session, nchannels 1
Received disconnect from IP 11: disconnected by user
debug1: do_cleanup
debug1: do_cleanup

```

It seems that I don't have the right permissions on folder ~/.ssh
```

Authentication refused: bad ownership or modes for directory /home/erotavlas

```

but I did 
```

chmod 700 ~/.ssh

```

---

### Post by Lars Noodén on 2014-05-02
This looks like it:

```

debug1: trying public key file /home/erotavlas/.ssh/authorized_keys
debug1: fd 4 clearing O_NONBLOCK
Authentication refused: bad ownership or modes for directory /home/erotavlas

```

Something is wrong with the home directory permissions, write permissions are too liberal maybe.  You could see what they are with

```

ls -ld /home/erotavlas

```

Then you'll have to use chmod (and maybe chgrp) to fix them. 

Maybe other home directories are also affected.

---

### Post by erotavlas on 2014-05-02
This is the output of the command ls -ld /home/erotavlas
```

drwxrwxrwx 25 another_user another_user 4096 May  2 10:40 /home/erotavlas

```

---

### Post by Lars Noodén on 2014-05-02
Ouch.  Somehow you'll have to get ownership of the directory.  The sysadmin should be able to do that for you.  

```

sudo chown erotavlas:erotavlas /home/erotavlas
sudo chmod o-w /home/erotavlas

```

Was there an accident that changed the ownership to someone else and zapped with o=rwx?  As it stands, anyone on that server can read and write your home directory and, to a certain extent, the subdirectories and files.

---

### Post by erotavlas on 2014-05-02
Thank you. I asked to administrator to change the permissions.
Now ls -ld /home/erotavlas
```

drwxrwxr-x 25 erotavlas erotavlas 4096 May  2 11:55 /home/erotavlas/

```

I receive the same answer
```

debug1: userauth-request for user erotavlas service ssh-connection method none [preauth]
SSH: Server;Ltype: Authname;Remote: IP-41406;Name: erotavlas [preauth]
debug1: attempt 0 failures 0 [preauth]
debug1: userauth-request for user erotavlas service ssh-connection method publickey [preauth]
debug1: attempt 1 failures 0 [preauth]
debug1: test whether pkalg/pkblob are acceptable [preauth]
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: temporarily_use_uid: 1001/1001 (e=0/0)
debug1: trying public key file /home/erotavlas/.ssh/authorized_keys
debug1: fd 4 clearing O_NONBLOCK
Authentication refused: bad ownership or modes for file /home/erotavlas/.ssh/authorized_keys
debug1: restore_uid: 0/0
debug1: temporarily_use_uid: 1001/1001 (e=0/0)
debug1: trying public key file /home/erotavlas/.ssh/authorized_keys2
debug1: Could not open authorized keys '/home/erotavlas/.ssh/authorized_keys2': No such file or directory
debug1: restore_uid: 0/0
Failed publickey for erotavlas from IP port 41406 ssh2

```

---

### Post by Lars Noodén on 2014-05-02
It's progress.  It's actually a slightly different error. ;)

```

Authentication refused: bad ownership or modes for file /home/erotavlas/.ssh/authorized_keys

```

Make sure that the file /home/erotavlas/.ssh/authorized_keys is owned by you and belongs to your group and that it is not writable by anyone else.  If the file is owned by someone else, you can just rename it and make a copy:

```

mv /home/erotavlas/.ssh/authorized_keys /home/erotavlas/.ssh/authorized_keys.old
cp /home/erotavlas/.ssh/authorized_keys.old /home/erotavlas/.ssh/authorized_keys
chmod 644 /home/erotavlas/.ssh/authorized_keys

```

---

### Post by erotavlas on 2014-05-07
Ok, thank you. There were problems on file permissions as you found out.

---

