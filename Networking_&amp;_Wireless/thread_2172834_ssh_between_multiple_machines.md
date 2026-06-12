---
title: "ssh between multiple machines"
date: 2013-09-06
forum: Networking &amp; Wireless
---

### Post by Scooby-2 on 2013-09-06
There are hundreds of posts like [this]("http://en.wikipedia.org/wiki/Public-key_cryptography") explaining how key exchange works literally thousands of excellent posts like [this one]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") helping us to set up password-less ssh logins between two machines. But if you've got more than one machine and you can't get your head round the theory (and I admit that I can't) there's no meaningful help. I have three machines - a desktop, a laptop and a headless Raspberry Pi. The Pi is the heart of a monitoring system and I use password-less ssh in scripts to copy the files it collects to either of the other two machines for processing. When I first set the systems up I quickly learned that you can't just keep on generating key pairs between the machines (as each one is connected to two others, and the 2nd process trashes the the first (I managed to get that bit!) However, when you run different OSs as well it all gets really hairy. I did manage to get it all working but then my desktop blew up. After deciding to run Linux Mint on the replacement (I have Xubuntu 12.04LTS on the laptop and arch Linux on the Pi) I am unable to get password-less logins between the desktop and the laptop, which I'm guessing is something to do with the different OS's, but all other permutations are OK.

Does anybody have enough understanding to cobble together a how-to for setting up ssh between multiple machines? While I did partially succeed it was all trial and error and all the files in ~.ssh/ are huge as a result. Even now I don't know how I got to where I am now and I refuse to try to finish it as I keep breaking things I just fixed!

Thanks in advance.

P.S. Here's my latest debug code - it starts to fail on line 7 with "Incorrect RSA1 identifier" but what does that mean?

> ~$ ssh -vvv myuserID@desktop -p 2209
OpenSSH_5.9p1 Debian-5ubuntu1.1, OpenSSL 1.0.1 14 Mar 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to desktop [10.247.144.76] port 2209.
debug1: Connection established.
debug3: Incorrect RSA1 identifier
debug3: Could not load "/home/myuserID/.ssh/id_rsa" as a RSA1 public key
debug1: identity file /home/myuserID/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-4096
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-4096
debug1: identity file /home/myuserID/.ssh/id_rsa-cert type -1
debug1: identity file /home/myuserID/.ssh/id_dsa type -1
debug1: identity file /home/myuserID/.ssh/id_dsa-cert type -1
debug1: identity file /home/myuserID/.ssh/id_ecdsa type -1
debug1: identity file /home/myuserID/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.1p1 Debian-4
debug1: match: OpenSSH_6.1p1 Debian-4 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1.1
debug2: fd 3 setting O_NONBLOCK
debug3: put_host_port: [desktop]:2209
debug3: load_hostkeys: loading entries for host "[desktop]:2209" from file "/home/myuserID/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/myuserID/.ssh/known_hosts:21
debug3: load_hostkeys: loaded 1 keys
debug3: order_hostkeyalgs: prefer hostkeyalgs: [email]ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com[/email],ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: [email]ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-rsa-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com[/email],ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss,ecdsa-sha2-nistp256
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-ctr hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA 7f:7c:d4:06:6c:ce:3b:61:54:56:20:5d:50:86:79:d9
debug3: put_host_port: [10.247.144.76]:2209
debug3: put_host_port: [desktop]:2209
debug3: load_hostkeys: loading entries for host "[desktop]:2209" from file "/home/myuserID/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/myuserID/.ssh/known_hosts:21
debug3: load_hostkeys: loaded 1 keys
debug3: load_hostkeys: loading entries for host "[10.247.144.76]:2209" from file "/home/myuserID/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/myuserID/.ssh/known_hosts:22
debug3: load_hostkeys: loaded 1 keys
debug1: Host '[desktop]:2209' is known and matches the ECDSA host key.
debug1: Found key in /home/myuserID/.ssh/known_hosts:21
debug1: ssh_ecdsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/myuserID/.ssh/id_rsa (0xb8beea38)
debug2: key: /home/myuserID/.ssh/id_dsa ((nil))
debug2: key: /home/myuserID/.ssh/id_ecdsa ((nil))
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/myuserID/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/myuserID/.ssh/id_dsa
debug3: no such identity: /home/myuserID/.ssh/id_dsa
debug1: Trying private key: /home/myuserID/.ssh/id_ecdsa
debug3: no such identity: /home/myuserID/.ssh/id_ecdsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
myuserID@desktop's password: 




---

### Post by SeijiSensei on 2013-09-07
I use SSH to connect to a variety of machines using the same public key on all of them.  I have my public key entered in each machine's /root/.ssh/authorized_keys file.  

What am I missing?

---

### Post by Scooby-2 on 2013-09-07
> **SeijiSensei said:**
> I use SSH to connect to a variety of machines using the same public key on all of them.  I have my public key entered in each machine's /root/.ssh/authorized_keys file.  

What am I missing?

Maybe it's just me, then? For background info, I connect on a daily basis to the Pi from both the laptop and the desktop. I want to be able to log in without a password, simply because it's a pain. I log on to the Pi and run a script to initiate downloading from the Pi to whichever machine I choose (depends where I'm working). I need the scripts to run without stopping for a password. FYI I have tried running ftp server software on the Pi, so it can all be handled from the client but unfortunately the Pi's implementation of the software does not maintain the exact date and time of the original files (it puts all zeroes for the seconds) and since the files are jpg's from security cameras, accurate times are necessary.

OK, so following this procedure [here]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") - assume starting from scratch - I generate a key pair on the Pi so I can connect from my laptop. All works. Then I want to do the same to connect in the opposite direction (so the file transfer scripts will work non-interactively - that works too, apparently without breaking anything. Follow the procedure again to set up the connections between the desktop and the Pi. That works too - but it breaks the setup for the laptop. I have only got it working by trial and error without understanding what I'm doing. I don't think I'm the only one a there are plenty of people having problems with only two machines.
> I use SSH to connect to a variety of machines using the same public key... 
I cannot see how to generate key pairs so that the public key will be the same as that used on other machines. Hence the first sentence of the second paragraph of my first post:
> [COLOR=#000000]Does anybody have enough understanding to cobble together a how-to for setting up ssh between multiple machines?[/COLOR]

---

### Post by SeijiSensei on 2013-09-07
Since this concerns file transfers, I'll assume we are creating keys for the root user.

On the Pi, become the root user and generate a key pair.  Copy /root/.ssh/id_rsa.pub to /root/.ssh/authorized_keys so remote clients can connect with the same credentials. On each client, copy the contents of the Pi's /root/.ssh directory into the client's /root/.ssh.  When you're done, all the machines should have identical content in /root/.ssh (except the known_hosts file which will be generated the first time you make a connection).  You should now be able to make password-less connections in both directions since all the machine's use the same key pair.

---

### Post by Scooby-2 on 2013-09-07
@SeijiSensei

Thanks for the advice - I'll try your suggestion next week (got a busy weekend/start to this coming week).

I'll post back asap.

---

### Post by Scooby-2 on 2013-10-28
I hate it when people don't come back with the results after someone has taken the trouble to give advice. That'll be me, then, and I apologise for it.

[COLOR=#000000]@SeijiSensei - I did try your solution but when I tried to log in I got the following:

[/COLOR]> ssh pi@pi
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the ECDSA key sent by the remote host is
de:80:d1:e7:70:e9:a9:95:d0:54:90:1f:ad:47:60:85.
Please contact your system administrator.
Add correct host key in /home/user/.ssh/known_hosts to get rid of this message.
Offending ECDSA key in /home/user/.ssh/known_hosts:13
  remove with: ssh-keygen -f "/home/user/.ssh/known_hosts" -R [pi]
ECDSA host key for [pi] has changed and you have requested strict checking.
Host key verification failed.


I ran
```
ssh-keygen -f "/home/user/.ssh/known_hosts" -R [pi]
```to remove the offending entry. It returned the following:
```
ssh-keygen -f "/home/user/.ssh/known_hosts" -R [pi]/home/user/.ssh/known_hosts updated.
Original contents retained as /home/user/.ssh/known_hosts.old
```I then logged out and in again, but this time I got:
```
ssh pi@piWarning: the ECDSA host key for '[pi]' differs from the key for the IP address '[xxx.xxx.xxx.xxx]'
Offending key for IP in /home/user/.ssh/known_hosts:13
Are you sure you want to continue connecting (yes/no)? yes
pi@pi's password:
```
I get this every time, but I just put up with it and enter the password. Thanks again to [COLOR=#000000]SeijiSensei for your efforts.[/COLOR]

---

### Post by Habitual on 2013-10-29
```
vi +13 /home/user/.ssh/known_hosts
```
press d twice "dd" and then ZZ to save and exit. retry the connection.

---

### Post by Scooby-2 on 2013-10-30
> **Habitual said:**
> ```
vi +13 /home/user/.ssh/known_hosts
```
press d twice "dd" and then ZZ to save and exit. retry the connection.
@[COLOR=#000000]Habitual - Thanks for your suggestion. I followed the instructions you gave which removed line 13 from the known_hosts file. I logged in to the pi again and I no longer get the message about the remote host identification, but I still have to enter the password every time I log in. This is a step forward as it means I have less to type! Any idea how I can get around having to enter the password? I know I can generate new key pair, but as I said in my first post this action breaks key pairs that were previously set up with other machines.

The situation is a little different because I had to reinstall the Pi's OS when the SD card decided it wasn't going to play any more. Compounding my situation still further is the fact that I also have another machine (another Pi), to which I can ssh without needing a password. However, it took a friend and I two evenings to get it to get it to work and it seemed like we tried everything. We don't know enough to say exactly how we achieved it - it was all trial and error using procedures we found on the Internet. Neither of us can understand the key exchange properly so at least I'm pleased to know it's not just me![/COLOR]

---

