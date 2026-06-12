---
title: "SSH Slow Login"
date: 2007-10-13
forum: Networking &amp; Wireless
---

### Post by Pennycook on 2007-10-13
Hi guys,

I know this seems to be a common problem, but I've already tried all of the suggestions I've found in the forums and have had no luck.  If I run ssh to a server on my LAN, it hangs for a while before asking me for my password.  I've tried adding UseDNS no, commenting out all of my ssh_config, setting the GSSAPIAuthentication=no (which did at least clear some of my -v problems, but hasn't sorted the delay) and still the problem persists.

I've also tried adding the computer I'm trying to connect to (192.168.1.15) to /etc/hosts.

Here's the output of my ssh -vvv, with where the hanging occurs marked:

> ssh -vvv  192.168.1.15
OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.15 [192.168.1.15] port 22.
debug1: Connection established.
debug1: identity file /home/john/.ssh/identity type -1
debug1: identity file /home/john/.ssh/id_rsa type -1
debug1: identity file /home/john/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.6p1 Debian-5build1
debug1: match: OpenSSH_4.6p1 Debian-5build1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: mac_init: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_init: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 136/256
debug2: bits set: 488/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /home/john/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 7
debug1: Host '192.168.1.15' is known and matches the RSA host key.
debug1: Found key in /home/john/.ssh/known_hosts:7
debug2: bits set: 510/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/john/.ssh/identity ((nil))
debug2: key: /home/john/.ssh/id_rsa ((nil))
debug2: key: /home/john/.ssh/id_dsa ((nil))

<<HANG OCCURS HERE>>

debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/john/.ssh/identity
debug3: no such identity: /home/john/.ssh/identity
debug1: Trying private key: /home/john/.ssh/id_rsa
debug3: no such identity: /home/john/.ssh/id_rsa
debug1: Trying private key: /home/john/.ssh/id_dsa
debug3: no such identity: /home/john/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password

I'm running Kubuntu, Feisty.  Any help would be greatly appreciated.

---

### Post by wieman01 on 2007-10-13
Just to say that I have the same problem. SSH log-in has become considerably slower in Feisty, much slower than it used to be in Dapper. The remaining bit is about the same.

---

### Post by Pennycook on 2007-10-13
Interestingly, I've just learnt that stopping my Firestarter firewall solves the problem, but I can't see why; my outbound traffic is set to permissive by default. With this in mind, does anybody have any ideas?

---

### Post by beerfan on 2007-10-13
It sounds like you're experiencing this issue.

[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/111553](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/111553)

Installing krb5-config resolved the issue for me.

---

### Post by Pennycook on 2007-10-14
> **beerfan said:**
> It sounds like you're experiencing this issue.

[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/111553](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/111553)

Installing krb5-config resolved the issue for me.

I tried installing krb5-config, no change.

---

### Post by Hopworks on 2007-10-15
> **Pennycook said:**
> I tried installing krb5-config, no change.Same for me too. I have exactly six seconds delay between hitting enter after "login as:" and the appearance of the password prompt. I'm using putty to log into my Linux machine, Ubuntu 7.04 Feisty, using SSH.

---

### Post by popie on 2007-12-20
I have two Ubuntu servers and experienced the delayed password prompt when SSH'ing into one of them (the Gutsy v7.10 server) but not when accessing the other (Feisty) server.

The fix was to modify the file **/etc/nsswitch.conf** on the Gutsy remote machine

*Change the hosts line as follows:

OLD
hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4

NEW
hosts: files dns mdns 

(these new values are the values I found on the Feisty v7.04 server)

After rebooting the delay was gone!

If someone understands the ramifications of making this change please respond. I found this advice, among tons of other suggestions, on the Canonical bug reporting site.

I hope this helps.

---

### Post by netztier on 2007-12-21
> **popie said:**
> 
After rebooting the delay was gone!

If someone understands the ramifications of making this change please respond. I found this advice, among tons of other suggestions, on the Canonical bug reporting site.


AFAIK, like many other services on unixoid operating systems, the SSH deamon (sshd) tries to do a reverse lookup of the IP address it sees "coming in".  /etc/nsswitch.conf defines which name resolution services are available and in which sequence they should be used.

> **popie said:**
> 
OLD
hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4

NEW
hosts: files dns mdns


Moving mdns (aka "avahi" or "Bonjour" on Mac OS X) to last-in-list seems to have helped. Probably mdns did fail (hence the wait period) while DNS delivered an acceptable answer (although not necessarily a correct one) to the sshd.

You might have fixed this issue also by adding your ssh-client's IP and hostname to the server's /etc/hosts.

regards

Marc

---

### Post by Hopworks on 2007-12-21
Oh man, that isn't what fixed it for me, and now I can't remember what I did. I'll have to check my notes and post a reply. I thought this thread was dead.

I got the solution here in ubuntuforms. Just can't remember the fix.

I hate that! I should have printed and framed the solution, it bothered me so much, and for so long.

---

### Post by popie on 2007-12-21
Hopworks,

It seems that some folks were having trouble with their **client**  connecting slowly to all(?) ssh servers, and others, like myself, with slowness with only one of several servers. My fix was an adjustment on the server, and others found adjustments for their client. So I think there were at least two different problems, that were easily confused.

BTW, to keep track of fixes like this I use TiddlyWiki. :)

---

### Post by Hopworks on 2007-12-24
> **popie said:**
> Hopworks,

It seems that some folks were having trouble with their **client**  connecting slowly to all(?) ssh servers, and others, like myself, with slowness with only one of several servers. My fix was an adjustment on the server, and others found adjustments for their client. So I think there were at least two different problems, that were easily confused.

BTW, to keep track of fixes like this I use TiddlyWiki. :)
Awesome, thank you! I certainly needed something like that as I stumbled through configuring my LAMP and learning Linux in the process.

---

### Post by 8f27e956 on 2007-12-25
On the machine being connected to (remote side/server side)

/etc/ssh/sshd_config

UseDNS no

if the remote side is another linux, then /etc/ssh/ssh_config
in the host * section

CheckHostIP no

/Scott

---

### Post by Hopworks on 2007-12-26
> **popie said:**
> Hopworks,

It seems that some folks were having trouble with their **client**  connecting slowly to all(?) ssh servers, and others, like myself, with slowness with only one of several servers. My fix was an adjustment on the server, and others found adjustments for their client. So I think there were at least two different problems, that were easily confused.

BTW, to keep track of fixes like this I use TiddlyWiki. :)
Hey Popie, just set up that TidlyWiki, after solving a couple of issues on my Windows using Firefox. That is a really neat tool! Just wanted to say thanks again. I'll use it big time! :D

There isn't a 'beer' smilie here like there is on Anandtech, or I'd offer you one. So a Big Smile will have to do. =)

---

### Post by popie on 2007-12-26
> **Hopworks said:**
> Hey Popie, just set up that TidlyWiki, after solving a couple of issues on my Windows using Firefox. That is a really neat tool! Just wanted to say thanks again. I'll use it big time! :D


Glad you like it Hopworks. :) I keep the wiki files on a server and access them from multiple PCs. Works great. Cross platform too.

---

### Post by Hopworks on 2007-12-27
> **popie said:**
> Glad you like it Hopworks. :) I keep the wiki files on a server and access them from multiple PCs. Works great. Cross platform too.
Yessir! As soon as I am (hopefully) successful moving my LAMP server over to the new hardware, it's going on there big time. I'll have to write a script or explore the options to allow syncing, because I want to use it on my laptop when away from my wireless LAN.

Sorry about the off-topic folks.

---

### Post by abradner on 2007-12-29
> **8f27e956 said:**
> On the machine being connected to (remote side/server side)

/etc/ssh/sshd_config

UseDNS no

if the remote side is another linux, then /etc/ssh/ssh_config
in the host * section

CheckHostIP no

/Scott


I only changed daemon config file, then sudo /etc/init.d/ssh restart and instantly fixed. Thanks!

---

### Post by SjRaptor on 2007-12-29
I once experienced very slow SSH login after one of my servers had restarted due to a power loss one night. Turned out, it never had a default gateway set on the interface it was booting up too.

---

