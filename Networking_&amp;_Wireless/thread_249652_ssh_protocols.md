---
title: "ssh protocols"
date: 2006-09-02
forum: Networking &amp; Wireless
---

### Post by pauljwells on 2006-09-02
I'm setting up my ubuntu desktop machine for remote ssh access using private/public keys. It works fine for the ssh2 protocol.

I have a Nokia N70 with Pocket PuTTY, which can only handle ssh1 key pairs. I know it works, because I can log into my mac, which supports both protocols 1 and 2, but the ubuntu machine only supports protocol 2, presumably because 2 is more secure than 1

If I comment out the line Protocol 2 in /etc/sshd.config I get an error 

```
Disabling protocol version 1. Could not load host key
Disabling protocol version 1. Could not load host key
```

I've not been able to find anything about key differences for the different protocols - I'm assuming it is refering to the keys ssh_host_rsa_key and 
ssh_host_rsa_key.pub, rather than the keypairs I generated.

Any hints on setting up ssh1 gratefully received


EDIT
found the answer - have to generate an ssh1 hostkey as root

ssh-keygen -t rsa1

with no passphrase and save as /etc/ssh/ssh_host_key

then in /etc/sshd_config add this to the list of keys and change the value of Protocols from 2 to 2,1

then sudo /etc/init.d/ssh restart

So I can now log in to my home ubuntu machine securely (ssh1 vulnerabilities aside...) using a keypair from my Nokia N70 mobile phone from anywhere... and I think that's pretty cool 8)

---

