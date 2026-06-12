---
title: "SSH without a Password"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by ashton88 on 2009-05-02
I can't seem to get SSH working without a password using ssh-keygen.  The ultimate goal is to get rsync working over ssh without a password for the purposes of a nightly crontab backup across the network which will not be as picky about whether remote filesystems are mounted and such... but I am stumped at this step - ssh without a password (I want to use a private/public key pair rather then keeping my password in plain text in a --password-file).

I have primarily used this link (but done reading on many links):
[http://troy.jdmz.net/rsync/index.html]("http://troy.jdmz.net/rsync/index.html")

Having done this a few times I just restarted from scratch to document the exact steps I took:

1) On thishost I ran:
ssh-keygen -t rsa -b 2048 -f /home/user/.ssh/thishost-rsync-key
(Hit Enter twice, no passphrase, key was generated).

2) On thishost I ran:
ssh-copy-id -i /home/user/.ssh/thishost-rsync-key.pub remotehost
(Got prompted for user password on remote system, entered it, got the message indicating it had been copied to authorized_keys).

3) On thishost I:
ssh to remotehost (get prompted for password???) type in password, log in, verify that thishost-rsync-key.pub is in the /home/user/.ssh/authorized_keys file.  It's there.

4) I double check the permissions on ~/.ssh (700) and on authorized_keys (600). As well as the private key file on thishost (600).

5) Try to ssh to remotehost again, but get prompted for a password.

6) ssh with the -v switch and I get the following output:

OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to remotehost [192.168.1.10] port 22.
debug1: Connection established.
debug1: identity file /home/user/.ssh/identity type -1
debug1: identity file /home/user/.ssh/id_rsa type -1
debug1: identity file /home/user/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-3ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-3ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'remotehost' is known and matches the RSA host key.
debug1: Found key in /home/user/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/user/.ssh/identity
debug1: Trying private key: /home/user/.ssh/id_rsa
debug1: Trying private key: /home/user/.ssh/id_dsa
debug1: Next authentication method: password
(Computer and user names have been changed)

I am then prompted for a password.

Any help would be appreciated, even a nudge in the right direction.  I've reached a roadblock.

Thanks!

---

### Post by ashton88 on 2009-05-02
I just stopping by to say that I figured this out.  Posting what I did here in the case that someone stumbles upon this in a search many years from now...

After reading the man pages for sshd_config and ssh I got to thinking that there was nowhere that I specified what my customname-private-key file was, so how would it be found during the authentication request?

Although I'm sure there is a command line switch or config file option to point your computer to the customname-private-key file somewhere... I just took the easy road and used the defaults (id_rsa and id_rsa.pub) and everything worked.

Cheers.

---

### Post by Cephi on 2009-08-05
OH MAN THANK YOU!
I was going nuts.

brb, goin to close the fifteen ffox tabs i have open looking for a solution to this problem :D

---

### Post by slakkie on 2009-08-05
iirc ssh -i $keyfile -o BatchMode=yes $user@$host 

That batchmode is pretty nice, also works with scp.

---

