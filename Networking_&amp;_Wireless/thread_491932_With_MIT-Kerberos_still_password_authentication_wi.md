---
title: "With MIT-Kerberos still password authentication with ssh,"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by Doc_symbiosis on 2007-07-04
Hi,

I'm just testing Kerberos and wonder, why ssh still wants a password. On both PCs ( server with Ubuntu feisty client with Ubuntu Dapper ), the user has the krbTGT and after running the ssh-command on the client, I also have a host ticket of the server on it.

Here's the output of ssh -v user@server
```

OpenSSH_3.8.1p1  Debian-krb5 3.8.1p1-10, OpenSSL 0.9.7g 11 Apr 2005
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Connecting to nils.bfk.loc [192.168.1.210] port 22.
debug1: Connection established.
debug1: identity file /root/.ssh/identity type -1
debug1: identity file /root/.ssh/id_rsa type -1
debug1: identity file /root/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-8ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-8ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_3.8.1p1  Debian-krb5 3.8.1p1-10
debug1: Mechanism encoded as toWM5Slw5Ew8Mqkay+al2g==
debug1: Mechanism encoded as A/vxljAEU54gt9a48EiANQ==
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'nils.bfk.loc' is known and matches the RSA host key.
debug1: Found key in /root/.ssh/known_hosts:2
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,gssapi-keyex,gssapi-with-mic,password
debug1: Next authentication method: gssapi-with-mic
debug1: Authentications that can continue: publickey,gssapi-keyex,gssapi-with-mic,password
debug1: Authentications that can continue: publickey,gssapi-keyex,gssapi-with-mic,password
debug1: Next authentication method: publickey
debug1: Trying private key: /root/.ssh/identity
debug1: Trying private key: /root/.ssh/id_rsa
debug1: Trying private key: /root/.ssh/id_dsa
debug1: Next authentication method: password

```

I have installed ssh-krb5 on both PCs and set
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials yes
in the ssh_config and in sshd_config I have set
     GSSAPIAuthentication yes
     GSSAPICleanupCredentials yes

Anyone got an idea, what's wrong?
I followed two instructions command by command, but both end in the same result.
Thanks in advance

---

