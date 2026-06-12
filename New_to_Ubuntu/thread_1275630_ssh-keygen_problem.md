---
title: "ssh-keygen problem"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by memecs on 2009-09-26
Hello everyone,

i am to access my account on the server of the university using a passphrase  without success... 

this is what i have done:
```

ssh-keygen -t dsa
chmod 0600 ~/.ssh/id_dsa


cat ~/.ssh/id_dsa.pub | ssh hostname 'cat >> ~/.ssh/authorized_keys'
```

at this point everything shoud be fine, but when i ssh to the host it still ask me for the password...

and this is the output of ssh hostname -v:

```
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /home/memecs/.ssh/config
debug1: Applying options for weh
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to weh5336-s.intro.cs.cmu.edu [128.2.185.186] port 22.
debug1: Connection established.
debug1: identity file /home/memecs/.ssh/identity type -1
debug1: identity file /home/memecs/.ssh/id_rsa type -1
debug1: identity file /home/memecs/.ssh/id_dsa type 2
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3
debug1: match: OpenSSH_4.3 pat OpenSSH_4*
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
debug1: Host 'weh5336-s.intro.cs.cmu.edu' is known and matches the RSA host key.
debug1: Found key in /home/memecs/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,gssapi-with-mic,password
debug1: Next authentication method: gssapi-with-mic
debug1: Unspecified GSS failure.  Minor code may provide more information
No credentials cache found
debug1: Unspecified GSS failure.  Minor code may provide more information
No credentials cache found
debug1: Unspecified GSS failure.  Minor code may provide more information
debug1: Next authentication method: publickey
debug1: Offering public key: /home/memecs/.ssh/id_dsa
debug1: Authentications that can continue: publickey,gssapi-with-mic,password
debug1: Trying private key: /home/memecs/.ssh/identity
debug1: Trying private key: /home/memecs/.ssh/id_rsa
debug1: Next authentication method: password
```

any help?

thanks a lot

---

### Post by wojox on 2009-09-26
Look here: [http://www.debian-administration.org/articles/152](http://www.debian-administration.org/articles/152)

---

### Post by scorp123 on 2009-09-26
> **memecs said:**
>  at this point everything shoud be fine, but when i ssh to the host it still ask me for the password... It may ask the first time you connect, yes. But if done correctly it should not do it anymore. Are you sure you're connecting to a Linux system with the OpenSSH package?

Because if you are connecting to a commercial UNIX system such as HP-UX, Solaris or whatever they might be running the commercial "SSH2" server instead of OpenSSH ... and on "SSH2" (not to be confused with the protocol) the files might be named in a different way and the keys have a different format.

The other thing that caught my attention: "GSS failure". Is that remote system set to Kerberos authentication? In that case it might very well be that it will ignore all keys until you successfully supply at least one password.

---

### Post by memecs on 2009-09-26
> **scorp123 said:**
> It may ask the first time you connect, yes. But if done correctly it should not do it anymore. Are you sure you're connecting to a Linux system with the OpenSSH package?

Because if you are connecting to a commercial UNIX system such as HP-UX, Solaris or whatever they might be running the commercial "SSH2" server instead of OpenSSH ... and on "SSH2" (not to be confused with the protocol) the files might be named in a different way and the keys have a different format.

The other thing that caught my attention: "GSS failure". Is that remote system set to Kerberos authentication? In that case it might very well be that it will ignore all keys until you successfully supply at least one password.

Yeah, the remote is set to Kerberos Authentication... so probably that is the problem...

---

