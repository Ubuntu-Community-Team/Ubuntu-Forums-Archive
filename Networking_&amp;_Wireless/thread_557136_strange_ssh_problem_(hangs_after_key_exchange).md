---
title: "strange ssh problem (hangs after key exchange)"
date: 2007-09-22
forum: Networking &amp; Wireless
---

### Post by funkycoder on 2007-09-22
hello, I've got a strange problem with ssh. that is: after the key exchange the remote server and my client exchange one packet each (server 1, client 1) and then just nothing happens.

this is the log (-vvv does not tell more):

```
$ ssh -vv cdann.de
OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to cdann.de [81.169.157.6] port 22.
debug1: Connection established.
debug1: identity file /home/pascal/.ssh/identity type 0
debug1: identity file /home/pascal/.ssh/id_rsa type 1
debug1: identity file /home/pascal/.ssh/id_dsa type 2
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-9
debug1: match: OpenSSH_4.3p2 Debian-9 pat OpenSSH*
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
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
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
debug2: dh_gen_key: priv key bits set: 149/256
debug2: bits set: 520/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'cdann.de' is known and matches the RSA host key.
debug1: Found key in /home/pascal/.ssh/known_hosts:3
debug2: bits set: 508/1024
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
```

and after the last line it just stops.

It does not seem to be a version issue, I've compiled ssh from source and it gives me the same. version is:
```
$ ./ssh -V
OpenSSH_4.7p1, OpenSSL 0.9.8c 05 Sep 2006
```

the conversation looks like:

```
client->server Protocol: SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1
client->server: Key Exchange Init (20)
server->client: Key Exchange Init (20)
client->server: Diffie-Hellman GEX Request (34)
server->client: Diffie-Hellman Key Exchange Reply (31)
client->server: Diffie-Hellman GEX Init (32)
server->client: Diffie-Hellman GEX Reply (33)
client->server: New Keys (21)
client->server: encrypted request packet len=48
server->client: encrypted response packet len=48
```

and that's it! my computer sends an ACK and nothing happens anymore.

Notable thing may be that seemingly every TCP-checksum for packets my computer sends is invalid if the packet contains data (thus: all the client->server stuff in the list, not the acks)

So maybe it is a system-problem (the same version of ssh, from source, works on my debian-ibook. and I also used the ibook as server with debug output and tried to ssh into it but nothing interesting was logged... could post this in a reply if anyone wants it)

in case it is a hardware problem: (abridged output)

```
$ lsmod
Module                  Size  Used by
nls_iso8859_1           5120  0 
nls_cp437               6784  0 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
tc1100_wmi              8068  0 
sony_acpi               6284  0 
pcc_acpi               13184  0 
dev_acpi               12292  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
ipv6                  268960  12 
sbp2                   23812  0 
af_packet              23816  2 
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
sg                     36252  0 
sd_mod                 23428  5 
sr_mod                 17060  0 
e1000                 126016  0
```

and

[CODE]$ lspci
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)[/CODE

the /etc/ssh/ssh_config is the unchanged version that came with the packet:


to sum up: ssh does not work on any server I tried (that cdann.de one, the mentioned openssh version from source on the ibook, shell.sf.net and the ssh-server of openssh.org itself).
but I need ssh, so: can anyone help?!

---

### Post by Maxtorm on 2007-09-22
How long have you left it before assuming the process is hung? I had a similar problem in that ssh appeared to hang, but if left for a minute or so, the login prompt eventually appeared. I have to admit, I did not troubleshoot to anywhere near the degree that you have, so the problem may be completely different. However, if it is of any help, in my case it was because the ssh server could not resolve my IP address. When I added a host entry to the server for the client, the connections went immediately to the login prompt. Is there any way this is the same problem?

---

### Post by funkycoder on 2007-09-22
I left it in the "hang"-state for an hour already (tried it often, course...). Also dis- and reconnected multiple times. (I'm behind a NAT router). I once configured the router to forward the WAN-port 22 to my computer so that I could ssh into it from outside but already reset this, too (and I hardly believe it to be a router problem as it works perfectly with the debian-ibook and the same router)

The SSH-server seems to be able to resolve my WAN-IP, it's something with my computer...

There is no problem with logging in, too: I've tried it with several credentials that are known to work (with the ibook), also created new accounts on the server and tried non-existant bogus-accounts -> always the same, hangs after that last debug-line. So it's something that happens before logging in.

Is there a way to more deeply inspect the SSH-communication? maybe the two encrypted packets that are sent will give some knowledge if decrypted...

That's the funny thing anyway, all other ssh-problems I found had some issue with client and server not talking to each other at all, but in my case they *do* the key exchange and first two packets...

Could it be a rootkit that intercepts my ssh-communication for some man-in-the-middle-ish attacks? (also: from the same computer communication over all other ports works with the servers I tried to ssh into)

And: when I run an ssh-server on my computer and log into it from the ibook, it works perfectly.

:confused:

---

### Post by Maxtorm on 2007-09-22
You seem quite versed in the ins and outs of ssh, so I'm sure I'm not going to be telling you anything you don't know or haven't already tried.

Ettercap will allow you to sniff the traffic in byte-level detail.

Though I've just started playing with it today, perhaps lsof could be of assistance? 
```
lsof -r -i :22
```

---

### Post by funkycoder on 2007-09-22
ah, I keep forgetting that name... could have been of so much use sometimes... :)

the output is repeating, seemingly the connection is not closed on the client side when it "hangs"?
```
COMMAND  PID   USER   FD   TYPE  DEVICE SIZE NODE NAME
sshd    4933   root    3u  IPv6 4860056       TCP *:ssh (LISTEN)
ssh     8585 pascal    3u  IPv4 4889950       TCP pascal-desktop2.local:57996->cdann.de:ssh (ESTABLISHED)
```

after killing ssh, the connection is closed of course (and RST packets sent. who does this anyway? the kernel or a kill-handler of ssh?)

---

### Post by Giblet5 on 2007-11-01
As posted in another thread:
[http://ubuntuforums.org/showthread.php?p=3684894#post3684894](http://ubuntuforums.org/showthread.php?p=3684894#post3684894)

SSH will hang with Feisty or Gutsy when the server is outside the NAT router.

It hangs in the handshake, even after building the Dapper openssh:
...
debug1: Remote protocol version 2.0, remote software version OpenSSH_3.7.1p2
debug1: match: OpenSSH_3.7.1p2 pat OpenSSH_3.*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent

SSH from Dapper, through that same router, works great.

Recap: Three systems with identical MTUs, going through the same NAT router; one Gutsy, one Feisty, and one Dapper. Dapper works, but Feisty and Gutsy both hang at the same point.

OpenSSL? CA-certs?

---

### Post by funkycoder on 2007-11-02
In my case it seemed to be the kernel.
I updated it to a newer version and it just works... On the ibook it was an older one, so it seems to be a problem with just that release (or a ubuntu patch for that release?)... Well, newer kernel is always a good thing...

(updating breaks the nvidia proprietary CUDA-enabled driver however, I have to reinstall it *twice* after each kernel update or else X dies when creating GLX contexts. but that's another problem I can live with...)

---

### Post by Giblet5 on 2007-11-05
There is a large kernel difference between Feisty and Gutsy...

I'm skeptical that this is the real problem; it may be that your newer kernel (version?) fixed something as much as it may have compensated for another problem.

I'm looking at OpenSSL all squinty-eyed and distrusting...

---

