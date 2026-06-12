---
title: "sshfs driving me nuts!"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by Knacker on 2011-05-14
Hi, I'm in the process of putting an old media server back into active duty. I had this all set up once upon a time so that I could mount folders using SSHFS. Worked very nicely. The problem I'm encountering is that when I hooked everything back up again, I'm getting errors about my key being refused. I don't think anything has changed but I can't be sure. I feel like I vaguely remember adding extra security features to allow/deny certain users and I'm wondering if it's different IP addresses that have triggered a block of some kind. In any case, I have access to the server via telnet and would be immensely grateful for any help. I feel like the easiest thing would be to wipe everything ssh related and start fresh, but I don't know how to begin to do that. Feeling a bit out of my depth... Please help me!

---

### Post by Knacker on 2011-05-14
i've finally found the sshd configuration file and I see nothing there that should keep me from connecting. i've tried replacing publickeys (authorized_keys) on server and everything else I can think of but I'm still getting "Permission denied (publickey,keyboard-interactive)" whenever I try to ssh to the server. Anyone have any suggestions?
Thanks

---

### Post by llamabr on 2011-05-14
so you also cannot ssh into the server?  try it with the verbose flag, and post the output:

ssh -v [email]yourname@yourserver.com[/email]

---

### Post by Knacker on 2011-05-14
I recreated rsa keys, copied them to the server, rebooted and tried again and got this: 

The authenticity of host '[169.254.237.124]:79 ([169.254.237.124]:79)' can't be established.
RSA key fingerprint is 4a:c7:b3:ba:f1:88:1e:44:52:97:f0:b3:2f:b1:22:06.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '[169.254.237.124]:79' (RSA) to the list of known hosts.
Permission denied (publickey,keyboard-interactive).


then tried again with verbose flag and got this: 

OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 169.254.237.124 [169.254.237.124] port 79.
debug1: Connection established.
debug1: identity file /home/justin/.ssh/identity type -1
debug1: identity file /home/justin/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/justin/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.2
debug1: match: OpenSSH_5.2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-6ubuntu2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '[169.254.237.124]:79' is known and matches the RSA host key.
debug1: Found key in /home/justin/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,keyboard-interactive
debug1: Next authentication method: publickey
debug1: Offering public key: /home/justin/.ssh/id_rsa
debug1: Authentications that can continue: publickey,keyboard-interactive
debug1: Trying private key: /home/justin/.ssh/identity
debug1: Trying private key: /home/justin/.ssh/id_dsa
debug1: Next authentication method: keyboard-interactive
debug1: Authentications that can continue: publickey,keyboard-interactive
debug1: No more authentication methods to try.
Permission denied (publickey,keyboard-interactive).

any clues?

---

### Post by Knacker on 2011-05-15
okay. i've tried everything I can think of. checked firewalls. checked through sshd logs (as much as I could) and recreated keys again. still no luck. does any expert eye out there see anything in my last post? does anyone else have any ideas or suggestions?
thanks again!

---

### Post by Knacker on 2011-05-15
Never "bumped" anything before and I hope I'm not breaking any rules by doing it now, but I'm really at my wits end. I'm at the point where I'm just repeating the same cycle of things that don't seem to work.
I posted the output from my attempt to ssh to the server above. If that makes sense to anyone, please help me... 
:confused:

---

### Post by Johnley on 2011-05-15
when stuff like tis happens, i go for the extreme route. have you considered purging all of the ssh config files from both computers? if you can't, it would be best to clear any access controls, and try again. and reboot. always reboot.

---

### Post by Knacker on 2011-05-15
Sigh...well, that was a PITA, but it worked. No idea where the glitch was -- well, my guess is permissions somewhere... -- but full purge of everything SSH related on both machines + careful reinstall and configuration from scratch did the trick. Probably just should have gone with that from the beginning, but...such a pain. 

I was really lost in the SSH juju for a while there. Whew. A million thanks for setting me straight!

---

