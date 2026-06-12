---
title: "SSH pubkey authentication works only if another session is already open."
date: 2011-03-30
forum: New to Ubuntu
---

### Post by AncientPC on 2011-03-30
Permissions are set correctly on the server (chibi).  If I do not have an existing ssh session open to the server, then all new sessions require a password.  However if there's already one open, additional ssh sessions authenticate with pubkey correctly.

My $home is on an SD card.  I moved authorized_keys to / and linked it, but that didn't resolve the issue.

No sessions open:

```
    ting@core[0][09:11:32]:~$ ssh-add -L
    ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDXRYefDRi18Qtlkfmt/qK5dbzMk5ajMgIv4+jUyWTtL1detZAs/hoIKocqBib5ul+/snrGiFbYV1JQiiLaidXNwe1nsNCk6UMagrRaCkPxyEqiygh9Ha5pf7anVdx2sLwdSXU42qKOgmVAHolpQfZQ4r/XItmR8fbDzNgkYeT+yEpm9b69wSl2d3xWPMd+EnqiqXuUoXISvMxDXIsC8I4qff6ms4JMX1S6HxBnVUKg/4DgJ7x07m4cM6RbXvGXNy2KBMhHoy45V/lPlf8pey+Af0Zxyw+na3mlG2WmAyOCnwXKJ/9TqLpYiCUHhTR4wgmgZpLWpSyyHYZhGP951ozP /home/ting/.ssh/id_rsa
    ting@core[0][09:12:35]:~$ ssh -v chibi
    OpenSSH_5.5p1 Debian-4ubuntu5, OpenSSL 0.9.8o 01 Jun 2010
    debug1: Reading configuration data /etc/ssh/ssh_config
    debug1: Applying options for *
    debug1: Connecting to chibi [192.168.1.2] port 22.
    debug1: Connection established.
    debug1: identity file /home/ting/.ssh/id_rsa type 1
    debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
    debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
    debug1: identity file /home/ting/.ssh/id_rsa-cert type -1
    debug1: identity file /home/ting/.ssh/id_dsa type -1
    debug1: identity file /home/ting/.ssh/id_dsa-cert type -1
    debug1: Remote protocol version 2.0, remote software version OpenSSH_5.5p1 Debian-4ubuntu5
    debug1: match: OpenSSH_5.5p1 Debian-4ubuntu5 pat OpenSSH*
    debug1: Enabling compatibility mode for protocol 2.0
    debug1: Local version string SSH-2.0-OpenSSH_5.5p1 Debian-4ubuntu5
    debug1: SSH2_MSG_KEXINIT sent
    debug1: SSH2_MSG_KEXINIT received
    debug1: kex: server->client aes128-ctr hmac-md5 none
    debug1: kex: client->server aes128-ctr hmac-md5 none
    debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
    debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
    debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
    debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
    debug1: Host 'chibi' is known and matches the RSA host key.
    debug1: Found key in /home/ting/.ssh/known_hosts:37
    debug1: ssh_rsa_verify: signature correct
    debug1: SSH2_MSG_NEWKEYS sent
    debug1: expecting SSH2_MSG_NEWKEYS
    debug1: SSH2_MSG_NEWKEYS received
    debug1: Roaming not allowed by server
    debug1: SSH2_MSG_SERVICE_REQUEST sent
    debug1: SSH2_MSG_SERVICE_ACCEPT received
    debug1: Authentications that can continue: publickey,password
    debug1: Next authentication method: publickey
    debug1: Offering public key: /home/ting/.ssh/id_rsa
    debug1: Authentications that can continue: publickey,password
    debug1: Trying private key: /home/ting/.ssh/id_dsa
    debug1: Next authentication method: password
    ting@chibi's password: 

```
One session already connected, opening second session:

```
    ting@core[0][09:14:14]:~$ ssh-add -L
    ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDXRYefDRi18Qtlkfmt/qK5dbzMk5ajMgIv4+jUyWTtL1detZAs/hoIKocqBib5ul+/snrGiFbYV1JQiiLaidXNwe1nsNCk6UMagrRaCkPxyEqiygh9Ha5pf7anVdx2sLwdSXU42qKOgmVAHolpQfZQ4r/XItmR8fbDzNgkYeT+yEpm9b69wSl2d3xWPMd+EnqiqXuUoXISvMxDXIsC8I4qff6ms4JMX1S6HxBnVUKg/4DgJ7x07m4cM6RbXvGXNy2KBMhHoy45V/lPlf8pey+Af0Zxyw+na3mlG2WmAyOCnwXKJ/9TqLpYiCUHhTR4wgmgZpLWpSyyHYZhGP951ozP /home/ting/.ssh/id_rsa
    ting@core[0][09:14:17]:~$ ssh -v chibi
    OpenSSH_5.5p1 Debian-4ubuntu5, OpenSSL 0.9.8o 01 Jun 2010
    debug1: Reading configuration data /etc/ssh/ssh_config
    debug1: Applying options for *
    debug1: Connecting to chibi [192.168.1.2] port 22.
    debug1: Connection established.
    debug1: identity file /home/ting/.ssh/id_rsa type 1
    debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
    debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
    debug1: identity file /home/ting/.ssh/id_rsa-cert type -1
    debug1: identity file /home/ting/.ssh/id_dsa type -1
    debug1: identity file /home/ting/.ssh/id_dsa-cert type -1
    debug1: Remote protocol version 2.0, remote software version OpenSSH_5.5p1 Debian-4ubuntu5
    debug1: match: OpenSSH_5.5p1 Debian-4ubuntu5 pat OpenSSH*
    debug1: Enabling compatibility mode for protocol 2.0
    debug1: Local version string SSH-2.0-OpenSSH_5.5p1 Debian-4ubuntu5
    debug1: SSH2_MSG_KEXINIT sent
    debug1: SSH2_MSG_KEXINIT received
    debug1: kex: server->client aes128-ctr hmac-md5 none
    debug1: kex: client->server aes128-ctr hmac-md5 none
    debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
    debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
    debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
    debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
    debug1: Host 'chibi' is known and matches the RSA host key.
    debug1: Found key in /home/ting/.ssh/known_hosts:37
    debug1: ssh_rsa_verify: signature correct
    debug1: SSH2_MSG_NEWKEYS sent
    debug1: expecting SSH2_MSG_NEWKEYS
    debug1: SSH2_MSG_NEWKEYS received
    debug1: Roaming not allowed by server
    debug1: SSH2_MSG_SERVICE_REQUEST sent
    debug1: SSH2_MSG_SERVICE_ACCEPT received
    debug1: Authentications that can continue: publickey,password
    debug1: Next authentication method: publickey
    debug1: Offering public key: /home/ting/.ssh/id_rsa
    debug1: Server accepts key: pkalg ssh-rsa blen 279
    debug1: Authentication succeeded (publickey).
    debug1: channel 0: new [client-session]
    debug1: Requesting [email]no-more-sessions@openssh.com[/email]
    debug1: Entering interactive session.
    debug1: Sending environment.
    debug1: Sending env LANG = en_US.utf8
    .bashrc executed.
    .bash_aliases executed.
    ting@chibi[0][14:14:41]:~$ 

```
Diff between the two sessions:

```
    ting@core[0][09:20:47]:~$ diff ssh1.txt ssh2.txt 
    36,39c36,37
    < debug1: Authentications that can continue: publickey,password
    < debug1: Trying private key: /home/ting/.ssh/id_dsa
    < debug1: Next authentication method: password
    < debug1: Authentication succeeded (password).
    ---
    > debug1: Server accepts key: pkalg ssh-rsa blen 279
    > debug1: Authentication succeeded (publickey).
    53,54c51,52
    < Transferred: sent 2216, received 8360 bytes, in 11.2 seconds
    < Bytes per second: sent 198.2, received 747.7
    ---
    > Transferred: sent 2712, received 7464 bytes, in 9.1 seconds
    > Bytes per second: sent 298.4, received 821.3
```

---

### Post by AncientPC on 2011-03-31
Turns out that since I was running encryptfs on my SD card, the first session mounts the SD card allowing all subsequent sessions to use pubkey correctly.

I just moved the authorized_key to the hdd and updated it accordingly within `/etc/ssh/sshd.conf`.

---

