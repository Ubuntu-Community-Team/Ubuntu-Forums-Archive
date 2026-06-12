---
title: "ssh keys don't work"
date: 2005-10-26
forum: Networking &amp; Wireless
---

### Post by fedesuarez on 2005-10-26
Hi,  I'm trying to set up keys to avoid writting pwds each time I ssh another computer inside my network, but after I generate the keys, ssh keeps asking for the pwd.
Of course, what I did:  ssh-keygen -t dsa   (in my laptop), then I added my id_dsa.pub line inside ~/.ssh/authorized_keys2 file.  But it keeps asking for the pwd.
Then I tried to do the same thing in another server, and of course, same result.
So, I finally got the idea of doing the reverse ssh, so I added the id_dsa.pub line inside the authorized_keys2 file in my laptop, and   Voila!!! it worked perfectly.

Just in case, I decided to generate rsa keys, but I got the same result, so I deleted them.

I really don't know what's wrong but it seems that I can't enter in any computer using keys, and everybody can enter in mine (using keys, of course).  But even more weird is that I succeded on setting the keys in another desktop computer to log in on the same server that rejects my laptop.  So it is clear that I have something wrong set on my laptop but I can't find it.

I also checked in the files (hosts.allow, hosts.deny, etc.), but nothing is inside those files.

I already read the thread from David in this section, but I couldn't make it work either.  Just as a comment, the file /var/log/auth.log doesn't exist on the server.

Could someone please help me with this?

this is the reply of my ssh -v:

[email]fede@fede:~/.ssh[/email]$ ssh -v bertou@x
OpenSSH_3.9p1 Debian-1ubuntu2, OpenSSL 0.9.7e 25 Oct 2004
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to x [192.168.2.24] port 22.
debug1: Connection established.
debug1: identity file /home/fede/.ssh/identity type -1
debug1: identity file /home/fede/.ssh/id_rsa type -1
debug1: identity file /home/fede/.ssh/id_dsa type 2
debug1: Remote protocol version 1.99, remote software version OpenSSH_3.6.1p2
debug1: match: OpenSSH_3.6.1p2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_3.9p1 Debian-1ubuntu2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'x' is known and matches the RSA host key.
debug1: Found key in /home/fede/.ssh/known_hosts:10
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug1: Next authentication method: publickey
debug1: Offering public key: /home/fede/.ssh/id_dsa
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug1: Trying private key: /home/fede/.ssh/identity
debug1: Trying private key: /home/fede/.ssh/id_rsa
debug1: Next authentication method: keyboard-interactive
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug1: Next authentication method: password
bertou@x's password:

---

