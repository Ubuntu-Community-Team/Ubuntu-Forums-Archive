---
title: "issue with ssh"
date: 2014-03-26
forum: Networking &amp; Wireless
---

### Post by Boris_Gershanik on 2014-03-26
Hi,
I'm having some problem with ssh (not sure it is realy a problem).
When my machine ssh a juniper firewall (netScreen) i'm getting exit status (when debug the ssh) of 1
althought the connection succeeded and my script did every thing it supoused to do.

I have some procedurs depending on the exit status of the ssh (i'm checking if the $? is 0).

I don't understand why ssh returns exit status 1.

Here is the debug output: 
I have modified it for security reasons.

```

OpenSSH_5.9p1 Debian-5ubuntu1.1, OpenSSL 1.0.1 14 Mar 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to X.X.X.X [X.X.X.X] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /root/.ssh/id_rsa-cert type -1
debug1: identity file /root/.ssh/id_dsa type 2
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: identity file /root/.ssh/id_dsa-cert type -1
debug1: identity file /root/.ssh/id_ecdsa type -1
debug1: identity file /root/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version NetScreen
[COLOR=#ff0000]debug1: no match: NetScreen[/COLOR]
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1.1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-sha1 none
debug1: kex: client->server aes128-cbc hmac-sha1 none
debug1: sending SSH2_MSG_KEXDH_INIT
debug1: expecting SSH2_MSG_KEXDH_REPLY
debug1: Server host key: DSA DSA-KEY(modified on post)
debug1: Host 'X.X.X.X' is known and matches the DSA host key.
debug1: Found key in /root/.ssh/known_hosts:8
debug1: ssh_dss_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /root/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password
debug1: Offering DSA public key: /root/.ssh/id_dsa
debug1: Server accepts key: pkalg ssh-dss blen 434
debug1: read PEM private key done: type DSA
debug1: Authentication succeeded (publickey).
Authenticated to X.X.X.X ([X.X.X.X]:22).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
debug1: Sending command: exit
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: channel 0: free: client-session, nchannels 1
Transferred: sent 3144, received 1592 bytes, in 0.2 seconds
Bytes per second: sent 16372.8, received 8290.5
debug1: Exit status 1

```

Is it because the marked line? "[COLOR=#FF0000]debug1: no match: NetScreen[/COLOR]"
[COLOR=#FF0000][/COLOR]
Thanks for help!

---

### Post by untrustytahr on 2014-03-26
```
man ssh | grep -i -1 'exit status'
```

will tell you that ssh exits with the code of the remotely executed command.

---

### Post by papibe on 2014-03-26
Hi Boris_Gershanik. Welcome to the forum ):P

It looks like a known NetScreen bug. Take a look at this suggestion: [Cannot SSH to the NetScreen]("http://kb.juniper.net/InfoCenter/index?page=content&id=KB5111&actp=RSS").

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Boris_Gershanik on 2014-03-26
> **papibe said:**
> Hi Boris_Gershanik. Welcome to the forum ):P

It looks like a known NetScreen bug. Take a look at this suggestion: [Cannot SSH to the NetScreen]("http://kb.juniper.net/InfoCenter/index?page=content&id=KB5111&actp=RSS").

Hope it helps. Let us know how it goes.
Regards.

Hi papibe,
Thanks for your replay.
I dont think the suggestion is helpful since I do connect to the netScreen.

---

