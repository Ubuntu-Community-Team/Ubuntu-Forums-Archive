---
title: "SSH: How do I verify RSA key fingerprint?"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by d3dtn01 on 2007-02-14
I've been forced to fiddle with my SSH. When I last tried to log into my server I got the message that says: "The authenticity of host 'XXX.XX.XX.XXX' can't be established." The message then lists an RSA key fingerprint. Is this fingerprint supposed to match the public key saved on my server? If so, I don't think that they match. On my server, I typed the command:

```
ssh-keygen -l -f id_dsa.pub
```

The output didn't match the fingerprint presented to my client. Should I be concerned?

---

### Post by bnuytten on 2007-02-15
On the server, did you derive the fingerprint from the user's ssh key or from the system's ssh key?
In other words, did you:
```
ssh-keygen -l -f /root/.ssh/ssh_host_dsa_key.pub (root user)
```
or
```
ssh-keygen -l -f /etc/ssh/ssh_host_dsa_key.pub (system)
```

The fingerprint your are prompted with at the client should match with the output of ssh-keygen -l -f /etc/ssh/ssh_host_rsa_key

---

### Post by d3dtn01 on 2007-02-16
Hmm. That's a good question. I think that I did the former (executed the command in the /root/.ssh directory). I'd check on it now, but I just lent my server to a friend. I'll take a look when I get it back. You said: 

> The fingerprint your are prompted with at the client should match with the output of ssh-keygen -l -f /etc/ssh/ssh_host_rsa_key

Did you really mean to say "ssh_host_rsa_key" or did you mean "ssh_host_dsa_key"? What's the difference between the two?

---

### Post by bnuytten on 2007-02-17
RSA and DSA are two different encryption algorythms. The input is either the RSA _private _key or its DSA counterpart. The output (fingerprint) is different off course.

Let me show by an example with two machines, one being the client and one the server running sshd. The ssh daemon is (default) setup with RSA fingerprinting so I'll go with that. First I will connect local on the server so I am sure this is really the fingerprint I should normaly see. You will notice it is exactly the same as when I generate it manually from the system's private RSA key. The rest is self-explanatory.

```
[root@server ~]# ssh-keygen -l -f /etc/ssh/ssh_host_rsa_key
1024 66:41:f5:36:01:f9:39:98:13:12:e6:43:65:db:fa:33 /etc/ssh/ssh_host_rsa_key.pub
[root@server ~]# ssh localhost
The authenticity of host 'localhost (127.0.0.1)' can't be established.
RSA key fingerprint is 66:41:f5:36:01:f9:39:98:13:12:e6:43:65:db:fa:33.
Are you sure you want to continue connecting (yes/no)?

[root@client ~]# ssh server
The authenticity of host 'server (172.16.0.161)' can't be established.
RSA key fingerprint is 66:41:f5:36:01:f9:39:98:13:12:e6:43:65:db:fa:33.
Are you sure you want to continue connecting (yes/no)?
```


PS: if you do not het the fingerprint prompt, you can simple remove the entry for that host in ~/.ssh/known_hosts on the machine you are typing ssh.

---

