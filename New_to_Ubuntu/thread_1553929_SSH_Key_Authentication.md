---
title: "SSH Key Authentication"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by proxyofsocks on 2010-08-15
I have the server running and can log onto it when the PasswordAuthentication is set to yes but when I set it to no I get a permission denied (publickey) error.

I generated the key pair on the client. Then I copied the id_rsa.pub file to my server's authorized_keys folder via flash drive and set PasswordAuthentication to no. When I try to login I get prompted for the password for the private key then the above error.

Any suggestions?

---

### Post by ubudog on 2010-08-15
Did you restart the ssh server on both computers after you did all that?

To do that, type this into a terminal:
```
sudo /etc/init.d/ssh restart
```

---

### Post by proxyofsocks on 2010-08-15
The ssh server only resides on one computer but I restarted it. Same error.

Do I need to have the server installed on the client as well?

---

### Post by Seq on 2010-08-15
> **proxyofsocks said:**
> Then I copied the id_rsa.pub file to my server's authorized_keys folder via flash drive and set PasswordAuthentication to no. When I try to login I get prompted for the password for the private key then the above error.

This is a little unclear. The public key should go in the file ~/.ssh/authorized_keys

Furthermore, the mode of the .ssh directory must be 700, to prevent tampering by other users. ssh probably fails reading the keys if permissions are not correct.

---

### Post by proxyofsocks on 2010-08-15
> **Seq said:**
> This is a little unclear. The public key should go in the file ~/.ssh/authorized_keys

Furthermore, the mode of the .ssh directory must be 600, to prevent tampering by other users. ssh probably fails reading the keys if permissions are not correct.

The public key is in the ~/.ssh/authorized_keys folder on the server.

On the server I:
```
chmod 600 ~/.ssh
```
Is that correct?

I am still receiving the same error.

---

### Post by proxyofsocks on 2010-08-15
Info from the client:
```

r@r:~$ ssh -vvv -2 [EMAIL="r@192.168.1.149"]r@192.168.1.149[/EMAIL]
OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.149 [192.168.1.149] port 22.
debug1: Connection established.
debug3: Not a RSA1 key file /home/r/.ssh/id_rsa.
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
debug1: identity file /home/r/.ssh/id_rsa type -1
debug1: identity file /home/r/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu4
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu4 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu4
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug3: Wrote 792 bytes for a total of 831
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: [EMAIL="aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se"]aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se[/EMAIL]
debug2: kex_parse_kexinit: [EMAIL="aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se"]aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se[/EMAIL]
debug2: kex_parse_kexinit: [EMAIL="hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96"]hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96[/EMAIL]
debug2: kex_parse_kexinit: [EMAIL="hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96"]hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96[/EMAIL]
debug2: kex_parse_kexinit: [EMAIL="none,zlib@openssh.com,zlib"]none,zlib@openssh.com,zlib[/EMAIL]
debug2: kex_parse_kexinit: [EMAIL="none,zlib@openssh.com,zlib"]none,zlib@openssh.com,zlib[/EMAIL]
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: [EMAIL="aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se"]aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se[/EMAIL]
debug2: kex_parse_kexinit: [EMAIL="aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se"]aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se[/EMAIL]
debug2: kex_parse_kexinit: [EMAIL="hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96"]hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96[/EMAIL]
debug2: kex_parse_kexinit: [EMAIL="hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96"]hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96[/EMAIL]
debug2: kex_parse_kexinit: [EMAIL="none,zlib@openssh.com"]none,zlib@openssh.com[/EMAIL]
debug2: kex_parse_kexinit: [EMAIL="none,zlib@openssh.com"]none,zlib@openssh.com[/EMAIL]
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-ctr hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug3: Wrote 24 bytes for a total of 855
debug2: dh_gen_key: priv key bits set: 122/256
debug2: bits set: 1008/2048
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: Wrote 272 bytes for a total of 1127
debug3: check_host_in_hostfile: filename /home/r/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 1
debug1: Host '192.168.1.149' is known and matches the RSA host key.
debug1: Found key in /home/r/.ssh/known_hosts:1
debug2: bits set: 1004/2048
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug3: Wrote 16 bytes for a total of 1143
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug3: Wrote 48 bytes for a total of 1191
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/r/.ssh/id_rsa ((nil))
debug2: key: /home/r/.ssh/id_dsa ((nil))
debug3: Wrote 64 bytes for a total of 1255
debug1: Authentications that can continue: publickey
debug3: start over, passed a different list publickey
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/r/.ssh/id_rsa
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
Enter passphrase for key '/home/r/.ssh/id_rsa': 
debug1: read PEM private key done: type RSA
debug3: sign_and_send_pubkey
debug2: we sent a publickey packet, wait for reply
debug3: Wrote 1152 bytes for a total of 2407
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/r/.ssh/id_dsa
debug3: no such identity: /home/r/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey).

```

---

### Post by bodhi.zazen on 2010-08-15
It appears something went wrong when you transfered the key.

IMO the easiest method is to generate the key on the client.

Then use ssh-copy-id to transfer the key to the server, it significantly reduces these kinds of errors.

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Saving](https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Saving) Keys on Remote Computers

---

### Post by ubudog on 2010-08-16
> **proxyofsocks said:**
> The ssh server only resides on one computer but I restarted it. Same error.

Do I need to have the server installed on the client as well?

Yes.

---

### Post by proxyofsocks on 2010-08-16
Thanks to everyone who helped me, I finally got it working.

There were a few problems. I thought that there was supposed to be a folder named 'authorized_keys' in the .ssh folder of the server's home directory. There is only supposed to be a 'file' with that name there and all keys are supposed to be in it.

Even with that problem corrected, it still wouldn't work. I then tried the ```
ssh-copy-id
``` method and that worked.

As it turns out I did not have to have the server installed on the client, only the client that comes with the default installation of Ubuntu.

Just two more questions. One, if I want to authorized more clients would the best way be to enable password authentication and ssh-copy-id the key over or try to append a id_rsa.pub file to the authorized_keys file via a flash drive? I don't want to fix something that isn't broke... I guess I could back up the file and try.

And how would I test that the ssh tunnel is working and encrypted? Would I have to install wireshark and look at packets or is there a web-based check?

Thanks again to everyone's help.

---

### Post by ubudog on 2010-08-16
For the first second question: You probably can just copy the authorized_keys file via flash drive to other computers.  Or, if you want, you can copy your id_rsa.pub file to a flash drive, cat (cat filename) it (view it), copy the coninto tents the authorized_keys file using gedit or something, and that should work.

---

### Post by Seq on 2010-08-16
> **proxyofsocks said:**
> The ssh server only resides on one computer but I restarted it. Same error.

Do I need to have the server installed on the client as well?

No, you only need the server installed on machines you are connecting to. You need the client on machines you are connecting from.

---

### Post by Seq on 2010-08-16
> **Seq said:**
> Furthermore, the mode of the .ssh directory must be 600, to prevent tampering by other users. ssh probably fails reading the keys if permissions are not correct.

I wasn't thinking properly here. This should have been 700 (it is a directory). I have updated said post incase anybody chances across this thread.

---

