---
title: "ssh keys do not overide password at remote login"
date: 2008-04-17
forum: Networking &amp; Wireless
---

### Post by arguellodw on 2008-04-17
In connecting a Gutsy laptop to a Gutsy desktop through a Solaris 5.9 DNS server, I am able to login from the former to the latter with a password.  In attempting to setup a cryptographic key login, I have done the following:

* used ssh-keygen to generate the keypair with passphrase
* placed the .pub key in the ~/.ssh/authoized_keys file of the desktop
* left the private key in the ~/.ssh folder of the laptop

When I then try to remote log from the laptop to the desktop, it still prompts me for a login password instead of the keypair passphrase.  What am I missing in this configuration process?

---

### Post by dmizer on 2008-04-17
you'll need to edit the /etc/ssh/sshd_config file to disable password authentication.

the following two options need to be changed to no:
```
PasswordAuthentication no
UsePAM no
```

restart ssh:
```
sudo /etc/init.d/ssh restart
```
and you should be good to go.

---

### Post by jcostom on 2008-04-17
The process should look more like:

[LIST=1]
[*]ssh-keygen on the client system
[*]ssh-keygen on the server system
[*]append the contents of ~/.ssh/id_dsa.pub (or whatever your public key is stored in) from the client system to ~/.ssh/authorized_keys2 on the server
[/LIST]

Do these, and you should be all set.  Starting ssh with the -v switch will give you verbose mode and help troubleshoot any problems.

---

### Post by dmizer on 2008-04-17
> **jcostom said:**
> The process should look more like:

[LIST=1]
[*]ssh-keygen on the client system
[*]ssh-keygen on the server system
[*]append the contents of ~/.ssh/id_dsa.pub (or whatever your public key is stored in) from the client system to ~/.ssh/authorized_keys2 on the server
[/LIST]

Do these, and you should be all set.  Starting ssh with the -v switch will give you verbose mode and help troubleshoot any problems.

just out of curiosity, why do you recommend performing ssh-keygen on the server?

---

### Post by arguellodw on 2008-04-17
I don't want to disable passwords for all accounts.  According to the O'Reilly book, 2nd edition, performing these steps should cause ssh to prompt me for a passphrase.  However, there seems to be absolutely no effect.

I tried doing the steps advised by jcostom...  this didn't seem to work either.  Any other ideas?

---

### Post by Kensey on 2008-04-17
I just had to do this at work to enable public-key access for putty to an Ubuntu 6.06 server.  In that case the process looked like this:

* keygen on the client
* catenate public key to .ssh/authorized_keys.  Make sure public key is one continuous line, not broken across lines -- this initially tripped me up.
* Make sure the ssh client is using the private key.

A good diagnostic is to use the -v (or -vv) option when you ssh, to try to watch where the negotiation is failing and falling back to user/pass.

---

### Post by arguellodw on 2008-04-18
OK... so here is what ended up working.  What Kensey said to do is what I've pretty much been doing all day long in trying to get this blasted thing to do my evil bidding.  Here's the thing I did differently:

I had been placing the public key on the remote host by emailing it to myself, logging onto the remote host using ssh, then downloading the file to my ~/.ssh folder to append  the authorized_keys file.  This last time, I used scp to transfer the file from my laptop to the remote host, and it works like a charm.

Hmmm...  I don't see why this should make a difference.  Guesses?

---

### Post by Kensey on 2008-04-18
> **arguellodw said:**
> OK... so here is what ended up working.  What Kensey said to do is what I've pretty much been doing all day long in trying to get this blasted thing to do my evil bidding.  Here's the thing I did differently:

I had been placing the public key on the remote host by emailing it to myself, logging onto the remote host using ssh, then downloading the file to my ~/.ssh folder to append  the authorized_keys file.  This last time, I used scp to transfer the file from my laptop to the remote host, and it works like a charm.

Hmmm...  I don't see why this should make a difference.  Guesses?

Your e-mail client is adding line breaks, whereas scp transfers the file intact.  In future you can still e-mail it to yourself when you do this, but make sure you remove the line breaks from the key when you paste it into the authorized_keys file.

---

### Post by arguellodw on 2008-04-18
Kensey,
This seems to be exactly it.  Instead of opening the downloaded public key file into emacs and doing cut and paste, I ran the following command:

$cat authorized_keys id_dsa.pub > temp
$mv temp authorized_keys

Many thanks for everybody's assistance,
Dan

---

