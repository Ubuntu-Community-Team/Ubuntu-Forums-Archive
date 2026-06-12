---
title: "SSH login takes long time"
date: 2007-12-03
forum: Networking &amp; Wireless
---

### Post by mddiligent on 2007-12-03
Hello folks!

i am using ubuntu 7.10 server. i have the basic ssh install, i didnt change any ssh config files. when i log in via ssh when the server is connected to a network with an internet gateway everything is fine. once i move the server over to a network without a internet gateway, whenever i log in via ssh, i have to wait for about 20-30seconds after entering the username before i can enter the password. it seems to me ssh tried to make some lookup which is not possible due to the missing internet gateway, then gets a timeout and then continues with the login. i checked the /var/log/auth.log file and entries only appear in there once the "timeout" occurs, before that noting is printed to the logfile. 
does anyone know this problem. what d i have to change to get rid of this behaviour? thanks  in advance. 

cheers,
marc

---

### Post by mellowd on 2007-12-03
What application are you using to SSH in? I use putty and it has a log as well. Right click the heading and click event log. That can give you an idea of what's happening

---

### Post by mddiligent on 2007-12-03
the event log from putty is not really of use

> 2007-12-03 22:10:21	Looking up host "192.168.100.221"
2007-12-03 22:10:21	Connecting to 192.168.100.221 port 22
2007-12-03 22:10:21	Server version: SSH-2.0-OpenSSH_4.6p1 Debian-5build1
2007-12-03 22:10:21	We claim version: SSH-2.0-PuTTY_Release_0.60
2007-12-03 22:10:21	Using SSH protocol version 2
2007-12-03 22:10:21	Doing Diffie-Hellman group exchange
2007-12-03 22:10:21	Doing Diffie-Hellman key exchange with hash SHA-256
2007-12-03 22:10:21	Host key fingerprint is:
2007-12-03 22:10:21	ssh-rsa 2048 61:e6:41:a7:e6:0b:5f:51:1c:bf:66:94:3d:06:b1:56
2007-12-03 22:10:21	Initialised AES-256 SDCTR client->server encryption
2007-12-03 22:10:21	Initialised HMAC-SHA1 client->server MAC algorithm
2007-12-03 22:10:21	Initialised AES-256 SDCTR server->client encryption
2007-12-03 22:10:21	Initialised HMAC-SHA1 server->client MAC algorithm
2007-12-03 22:11:05	Sent password
2007-12-03 22:11:05	Access granted
2007-12-03 22:11:05	Opened channel for session
2007-12-03 22:11:05	Allocated pty (ospeed 38400bps, ispeed 38400bps)
2007-12-03 22:11:05	Started a shell/command
2007-12-03 22:11:45	Network error: Software caused connection abort


i can just see a 45 second break before sending the password after i entered the username. any ideas?

---

### Post by p2im0 on 2007-12-09
I'm having the exact same issue but with about a 10-15 second pause.

I'm using an Ubuntu Gutsy server behind a "home" router with SSH forwarded to the box, connecting with PuTTY.  The worst part is, I can't remember ever having this issue on Dapper, Edgy, or Feisty.  The box has been upgraded through all disto releases.

I have MySQL running, Apache 2 with two tiny websites hosted, and there's almost never any load on the box.

I can't pinpoint exactly when it happened, but it was sometime after the Gutsy upgrade.

-P2iM-0

---

### Post by Lostincyberspace on 2007-12-09
how new is the install if it is old 6+months just backup and reinstall that would most likely fix it. I will have to think about the problem to figure out another fix.

---

### Post by p2im0 on 2007-12-09
Well, backup, format, and re-install is more of a "Windows" approach in my opinion.  That's not how I'd like to approach this one.  It's a file/web/MySQL server I've had running for over a year now on a PIII 996MHz system.  I've had ZERO issues with it to this point, and waiting 10 seconds every time I log in isn't enough of a reason to reformat.

Does anyone know if there is a way to have an accepted key so I just don't have to type my password in anymore?  I'll usually be coming from a Windows machine and will be using PuTTY on my end.  I know it's possible *NIX-to-*NIX but wasn't sure if you could do it from Windows-to-*NIX


Thanks,
-P2iM0

---

### Post by conjur3r on 2007-12-09
Add the following to /etc/ssh/sshd_config on your SSH server

UseDNS no

Then restart the ssh daemon and your pauses should be gone.

---

### Post by p2im0 on 2007-12-09
> **conjur3r said:**
> Add the following to /etc/ssh/sshd_config on your SSH server

UseDNS no

Then restart the ssh daemon and your pauses should be gone.

Conjur3r, My HERO!

Using the above method solved my problem and the server prompts for the password instantly.

So it was the name resolution that was slowing it down all along?  Did releases previous to Gutsy not use this option?

Thanks,
-P2iM0

---

### Post by conjur3r on 2007-12-09
Not sure about all other releases but I had to do it to Feisty and Edgy.  I also have to do it to other distributions I'm playing around with (Red Hat, SuSE & FreeBSD) so I doubt it's specifically an Ubuntu issue.

It's pretty much one of the first things I do after installing the ssh server.

---

### Post by conjur3r on 2007-12-09
> **p2im0 said:**
> 
Does anyone know if there is a way to have an accepted key so I just don't have to type my password in anymore?  I'll usually be coming from a Windows machine and will be using PuTTY on my end.  I know it's possible *NIX-to-*NIX but wasn't sure if you could do it from Windows-to-*NIX


Yes this is possible using Putty as well.  You will need to convert your ssh private key using [Puttygen]("http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html"), as putty only recognises its own format.  Once you have it converted, you can use normal Putty to connect passwordless (provided you did not specify a password on your key) to your server.

---

### Post by zhangweiwu on 2008-01-09
I am not sure -> because "UseDNS no" didn't seems to have enhanced speed a lot.

Usually I have to wait 30s to see the prompt for me to type my passphrase.

Some server I connect to is slow here:
```

$ ssh -vvv ...
...
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/zhangweiwu/.ssh/identity ((nil))
debug2: key: /home/zhangweiwu/.ssh/id_rsa (0x80714d8)
debug2: key: /home/zhangweiwu/.ssh/id_dsa ((nil))
[wait 20 seconds here]
debug1: Authentications that can continue: publickey
debug3: start over, passed a different list publickey
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey

```

Some server I connect to is slow here:

```

$ ssh -vvv ...
...
debug3: key_read: missing keytype
debug1: identity file /home/zhangweiwu/.ssh/id_rsa type 1
debug1: identity file /home/zhangweiwu/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-9
debug1: match: OpenSSH_4.3p2 Debian-9 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1
debug2: fd 3 setting O_NONBLOCK
[wait 10 seconds here]
debug1: Miscellaneous failure
No credentials cache found

debug1: Miscellaneous failure
No credentials cache found

debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr

```

---

### Post by Walter_Crankite on 2008-02-22
Thanks a lot. The entry in the sshd config file works like a charm. 
I do not understand why. I ssh to an IP address, so no DNS is used. 
Why does he uses DNS even when it is completely not necessary?
Why is it default enabled? Or why is it not in the config file. 

But anyway, thx a lot conjur3r. Few months ago I had the same problem and read a lot of solutions, but none worked. Now after downgrading from the latest version to the latest LTS version, ssh was extremely slow again. 

br,
Wouter

---

### Post by Iowan on 2008-02-22
Part of the delay might be in the authentication process.  Going from (poor) memory, SSH first attempts to authenticate using keys.  If that fails (hence the delay), it falls back to user/password. Dunno if it's possible to short-circuit the authentication process so it doesn't bother checking keys and starts w/ username/password.

---

### Post by gpowers01 on 2008-03-20
I don't claim to be an ssh configuration expert, but I did run across the same problem in gutsy (log wait for an ssh password prompt).  This is what I did to seemingly correct the issue:

The last poster(Iowan) is correct - the client server will try to exchange keys first in a particular order, then eventually fail over to password authentication if all else fails.  It seems that the ssh client in gutsy hangs for a few moments trying to do this (I don't know ...or care, why this is...I don't use keys for ssh very often, so I don't need this capability on my personal server).  This is shown in the following output when I ran ssh -v <username>@<targetsshserverhere>
[INDENT]------
...
...
debug1: Authentications that can continue: publickey,gssapi-with-mic,password
debug1: Next authentication method: gssapi-with-mic
<HANGS HERE>....
debug1: Unspecified GSS failure.  Minor code may provide more information
No credentials cache found

<HANGS HERE>...
debug1: Unspecified GSS failure.  Minor code may provide more information
No credentials cache found

debug1: Unspecified GSS failure.  Minor code may provide more information


debug1: Next authentication method: publickey
debug1: Trying private key: /root/.ssh/identity
debug1: Trying private key: /root/.ssh/id_rsa
debug1: Trying private key: /root/.ssh/id_dsa
debug1: Next authentication method: password
...
...
[/INDENT]


I simply disabled this login method on the ubuntu client side (/etc/ssh/ssh_config).  To do this, I just uncommented the single line (need to be root to do so...) in the ssh_config file:

[INDENT]GSSAPIAuthentication no[/INDENT]

Once this is done, I see the password prompt immediately.

Hope this helps!

Regards,
==========
gpowers01

To those that will criticize - I don't care about you!!! :)  My solutions work for me.  Don't like it, don't use it! 

"The years passed, mankind became stupider at a frightening rate. Some had high hopes the genetic engineering would correct this trend in evolution, but sadly the greatest minds and resources where focused on conquering hair loss and prolonging erections..."
==========

---

### Post by Mathboy on 2008-04-28
> **conjur3r said:**
> Add the following to /etc/ssh/sshd_config on your SSH server
UseDNS no
Then restart the ssh daemon and your pauses should be gone.

That fixed it for me - awesome, thank you! :)

---

