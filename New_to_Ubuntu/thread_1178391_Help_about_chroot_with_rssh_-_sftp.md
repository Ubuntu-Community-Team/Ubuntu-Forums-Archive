---
title: "Help about chroot with rssh - sftp"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by drakeman007 on 2009-06-04
Hello guys, can anyone help me please! i have installed openssh in my debian lenny, i follow the steps in this site
```
http://www.agali.org/node/80
```

I did everything like the tutorial, but when i tried to connect via sftp i get this error after i put the password.

```
Couldn't read packet: Connection reset by peer
```

the user.log say this:

```
Jun  4 11:27:47 drake rssh[6126]: allowing sftp to all users
Jun  4 11:27:47 drake rssh[6126]: setting umask to 0770
Jun  4 11:27:47 drake rssh[6126]: chrooting all users to /home/ftp/
Jun  4 11:27:47 drake rssh[6126]: chroot cmd line: /usr/lib/rssh/rssh_chroot_helper 2 "/usr/lib/openssh/sftp-server"
Jun  4 11:27:47 drake rssh_chroot_helper[6126]: new session for ftp, UID=1001
Jun  4 11:27:47 drake rssh_chroot_helper[6126]: chroot() failed, 2: Operation not permitted
```

the auth.log say this
```
Jun  4 11:22:50 drake sshd[6058]: Accepted password for ftp from 192.168.1.33 port 57732 ssh2
Jun  4 11:22:50 drake sshd[6058]: pam_unix(sshd:session): session opened for user ftp by (uid=0)
Jun  4 11:22:50 drake sshd[6067]: subsystem request for sftp
Jun  4 11:22:50 drake sshd[6058]: pam_unix(sshd:session): session closed for user ftp
```

what could be the problem? i dont know what else i can do!! can anyone help me please?

Regards!

---

### Post by jonobr on 2009-06-04
Could you try doing this on the localhost,
does that work?

How far do you get eg

heres what I get when I do localhost

> 
me@here:~$ sftp localhost
Connecting to localhost...
The authenticity of host 'localhost (127.0.0.1)' can't be established.
RSA key fingerprint is XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'localhost' (RSA) to the list of known hosts.
me@localhost's password: 
sftp> 



---

### Post by victorbrca on 2009-06-04
If you could also post the contents of your vsftpd.conf:

```
grep -v '^#' /etc/vsftpd.conf
```

---

### Post by drakeman007 on 2009-06-04
> **jonobr said:**
> Could you try doing this on the localhost,
does that work?

How far do you get eg

heres what I get when I do localhost

Hello, with localhost is the same, i get this.
```
Connecting to localhost...
ftp@localhost's password: 
Connection closed
```

auth.log says:
```
Jun  4 18:41:06 drake sshd[3976]: pam_unix(sshd:session): session opened for user ftp by (uid=0)
Jun  4 18:41:06 drake sshd[3985]: subsystem request for sftp
Jun  4 18:41:06 drake sshd[3976]: pam_unix(sshd:session): session closed for user ftp
```

user.log says
```
Jun  4 18:36:51 drake rssh[3834]: allowing sftp to all users
Jun  4 18:36:51 drake rssh[3834]: setting umask to 0770
Jun  4 18:36:51 drake rssh[3834]: chrooting all users to /home/ftp/
Jun  4 18:36:51 drake rssh[3834]: chroot cmd line: /usr/lib/rssh/rssh_chroot_helper 2 "/usr/lib/openssh/sftp-server"
Jun  4 18:41:06 drake rssh[3986]: allowing sftp to all users
Jun  4 18:41:06 drake rssh[3986]: setting umask to 0770
Jun  4 18:41:06 drake rssh[3986]: chrooting all users to /home/ftp/
Jun  4 18:41:06 drake rssh[3986]: chroot cmd line: /usr/lib/rssh/rssh_chroot_helper 2 "/usr/lib/openssh/sftp-server"
```

If i run sftp commnand with -v option i get this
```
drakeman@drake:~$ sftp -v -v ftp@localhost
Connecting to localhost...
OpenSSH_5.1p1 Debian-5+b1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to localhost [::1] port 770.
debug1: Connection established.
debug1: identity file /home/drakeman/.ssh/id_rsa type -1
debug1: identity file /home/drakeman/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-5+b1
debug1: match: OpenSSH_5.1p1 Debian-5+b1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-5+b1
debug2: fd 3 setting O_NONBLOCK
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
debug2: dh_gen_key: priv key bits set: 135/256
debug2: bits set: 527/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '[localhost]:770' is known and matches the RSA host key.
debug1: Found key in /home/drakeman/.ssh/known_hosts:2
debug2: bits set: 507/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/drakeman/.ssh/id_rsa ((nil))
debug2: key: /home/drakeman/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/drakeman/.ssh/id_rsa
debug1: Trying private key: /home/drakeman/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: Next authentication method: password
ftp@localhost's password: 
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug2: fd 4 setting O_NONBLOCK
debug1: channel 0: new [client-session]
debug2: channel 0: send open
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug1: Sending subsystem: sftp
debug2: channel 0: request subsystem confirm 1
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel 0: rcvd adjust 2097152
debug2: channel_input_confirm: type 99 id 0
debug2: subsystem request accepted on channel 0
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: client_input_channel_req: channel 0 rtype eow@openssh.com reply 0
debug2: channel 0: rcvd eow
debug2: channel 0: close_read
debug2: channel 0: input open -> closed
debug2: channel 0: rcvd eof
debug2: channel 0: output open -> drain
debug2: channel 0: obuf empty
debug2: channel 0: close_write
debug2: channel 0: output drain -> closed
debug2: channel 0: rcvd close
debug2: channel 0: almost dead
debug2: channel 0: gc: notify user
debug2: channel 0: gc: user detached
debug2: channel 0: send close
debug2: channel 0: is dead
debug2: channel 0: garbage collecting
debug1: channel 0: free: client-session, nchannels 1
debug1: fd 0 clearing O_NONBLOCK
Transferred: sent 1392, received 1960 bytes, in 0.0 seconds
Bytes per second: sent 91290.4, received 128541.1
debug1: Exit status 1
Couldn't read packet: Connection reset by peer
```


Oh, i want to clarify, the problem is only with the user i "jailed" in home directory in the sftp, because when i use my other user, without any jails i can enter from outside and in localhost too.

I really dont know what else i can do! there must be any way, or i must have an error, but dont know where...

Thanks.

---

### Post by drakeman007 on 2009-06-04
> **victorbrca said:**
> If you could also post the contents of your vsftpd.conf:

```
grep -v '^#' /etc/vsftpd.conf
```

I dont have that file, im using rssh.conf, im not using vsfptd server, im using openssh with rssh..

---

### Post by victorbrca on 2009-06-04
> **drakeman007 said:**
> I dont have that file, im using rssh.conf, im not using vsfptd server, im using openssh with rssh..

For some stupid reason I thought I read vsftp somewhere!!! :oops:

---

### Post by drakeman007 on 2009-06-04
> **victorbrca said:**
> For some stupid reason I thought I read vsftp somewhere!!! :oops:

Dont worry, and thanks for trying to help here.

---

### Post by jonobr on 2009-06-05
Hello


It seems from your logs that authentication is working and the user is 
granted access but terminated soon after?

```
ebug1: Next authentication method: password
ftp@localhost's password: 
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
```

I did a compare to my -v login and after the password all I see is this.

```
lme@localhost's password: 
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
debug1: Sending subsystem: sftp

```

And Im logged in,
Yours go into callback? and then goes into what looks like some windowing configuration requests.
This makes me think your doing something different to me.

Useless arent I??? But I hope the above logs from me show something?

---

### Post by drakeman007 on 2009-06-07
> **jonobr said:**
> Hello


It seems from your logs that authentication is working and the user is 
granted access but terminated soon after?

```
ebug1: Next authentication method: password
ftp@localhost's password: 
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
```

I did a compare to my -v login and after the password all I see is this.

```
lme@localhost's password: 
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
debug1: Sending subsystem: sftp

```

And Im logged in,
Yours go into callback? and then goes into what looks like some windowing configuration requests.
This makes me think your doing something different to me.

Useless arent I??? But I hope the above logs from me show something?

Thanks for your answer, i have to use another method (jailkit) to chroot a terminal, ssh, and using the sshd_config to chroot the sftp connection, now everything is working now! thanks very appreciate your help...

---

### Post by jonobr on 2009-06-07
hi 

Glad you got it working!

---

