---
title: "[SOLVED] Passwordless ssh isn't"
date: 2007-09-02
forum: Networking &amp; Wireless
---

### Post by dcroxton on 2007-09-02
I'm having no luck configuring passwordless ssh on an Ubuntu client.  Actually, I have it working for root, but not for my main user.  I've discovered several setup issues and fixed them, but there is obviously some other problem that I haven't discovered.

Steps so far:
* generated ida_dsa, copied it to remote host ~/.ssh/authorized_keys and set permissions to 600
* set GSSAPIAuthentication no on the client
* set EnableSSHKeysign yes on the client
* copied ~/.ssh/id_dsa to ~/.ssh/identity (no idea if this was needed, but it kept saying it couldn't find an identity, so I figured I would try it)
* run ssh-add

Here's the output from ssh -vvv [host] (the most important stuff is at the very bottom):

```
OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to ox [192.168.2.3] port 22.
debug1: Connection established.
debug3: Not a RSA1 key file /home/dcroxton/.ssh/identity.
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
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/dcroxton/.ssh/identity type -1
debug1: identity file /home/dcroxton/.ssh/id_rsa type -1
debug3: Not a RSA1 key file /home/dcroxton/.ssh/id_dsa.
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
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/dcroxton/.ssh/id_dsa type 2
debug1: Remote protocol version 2.0, remote software version OpenSSH_3.8.1p1 Debian 1:3.8.1p1-5
debug1: match: OpenSSH_3.8.1p1 Debian 1:3.8.1p1-5 pat OpenSSH_3.*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib
debug2: kex_parse_kexinit: none,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_init: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_init: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 153/256
debug2: bits set: 528/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /home/dcroxton/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 6
debug3: check_host_in_hostfile: filename /home/dcroxton/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 1
debug1: Host 'ox' is known and matches the RSA host key.
debug1: Found key in /home/dcroxton/.ssh/known_hosts:6
debug2: bits set: 509/1024
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
debug2: key: /home/dcroxton/.ssh/id_dsa (0x800544d8)
debug2: key: /home/dcroxton/.ssh/id_dsa (0x80059000)
debug2: key: /root/.ssh/id_dsa (0x800595f0)
debug2: key: /home/dcroxton/.ssh/identity ((nil))
debug2: key: /home/dcroxton/.ssh/id_rsa ((nil))
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug3: start over, passed a different list publickey,password,keyboard-interactive
debug3: preferred hostbased,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/dcroxton/.ssh/id_dsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug1: Offering public key: /home/dcroxton/.ssh/id_dsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug1: Offering public key: /root/.ssh/id_dsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug1: Trying private key: /home/dcroxton/.ssh/identity
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
Enter passphrase for key '/home/dcroxton/.ssh/identity': 
debug1: read PEM private key done: type DSA
debug3: sign_and_send_pubkey
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug1: Trying private key: /home/dcroxton/.ssh/id_rsa
debug3: no such identity: /home/dcroxton/.ssh/id_rsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup keyboard-interactive
debug3: remaining preferred: password
debug3: authmethod_is_enabled keyboard-interactive
debug1: Next authentication method: keyboard-interactive
debug2: userauth_kbdint
debug2: we sent a keyboard-interactive packet, wait for reply
debug2: input_userauth_info_req
debug2: input_userauth_info_req: num_prompts 1
Password: 

```

As you can see, it is asking me for the passphrase, which it shouldn't because I have already added it; and even when I enter it, that method is failing and I still have to enter a password (which does finally work).

I've scoured the net for help on this, but so far I haven't been able to find out what I'm doing wrong.  Please help!


](*,)

---

### Post by noob12 on 2007-09-02
The keygen will generate a id_dsa file and an id_dsa.pub file.  Make sure you appended the contents of the .pub file to the authorized keys on the receiving server end.  It sounded like you used the id_dsa file (from your earlier posting).

---

### Post by dcroxton on 2007-09-02
Sorry, my post was wrong.  I did copy id_dsa.pub over the first time (contrary to the post).  I copied it over again just to be sure, but it still doesn't work.

---

### Post by noob12 on 2007-09-04
You can get more info on the server side by stopping the service and running the service manually in debug mode.  This assumes the server is on Ubuntu.

```

sudo /etc/init.d/ssh stop
sudo /usr/bin/sshd -ddd

```

The service will stay on the terminal and give (lots of) output when you connect from the client.  You may find a clue that way.

---

### Post by dcroxton on 2007-09-04
Restarting the server wasn't going to be easy, since I don't have a keyboard, mouse, or monitor hooked up to it.  However, it put me on the right track.  I could never find a log file for ssh, but then I read somewhere to check in auth.log.  There I found that the permissions on my home directory were wrong.  I had checked the permissions on .ssh and on authorized_keys, but not my home directory!  Apparently I had mucked around with them sometime and changed them.  Once I reset them to 755, it worked fine.

Thanks for the help.

---

### Post by noob12 on 2007-09-05
Great to hear you solved it.

---

