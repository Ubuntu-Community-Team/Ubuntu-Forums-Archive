---
title: "[SOLVED] ssh just not working"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by antm88 on 2008-08-11
Hi,
I'm trying (ultimately) to set up a ssh server on my desktop computer at home so I can connect to it from wherever. The problem is I'm having difficulties with getting it to accept even local connections!

Desktop computer:
IP 10.0.0.202, username ant
Laptop:
IP 10.0.0.209, username ant

OK so I had no luck so I decided to remove all config settings and start again:

On both computers, I ran "sudo apt-get purge openssh-*; sudo rm -R /etc/ssh; sudo rm -R /home/ant/.ssh; sudo iptables -F"

Then on the laptop, "sudo apt-get install openssh-client"
On the desktop, "sudo apt-get install openssh-server"

Now, on the desktop I can run "ssh localhost", enter my password and it connects

So on my laptop, I try to run "ssh 10.0.0.202", it asks me for password of ant@10.0.0.202 and then just freezes!

I had ssh sort of working before i removed all of the settings - I reinstalled it about 4 times and each time it worked until one of the computers rebooted and then just stopped working!

It seems to be really temperamental, am I just being stupid?? I'm thinking of running this computer without a monitor/keyboard/mouse and so far this doesn't seem possible if I can't login half the time because my computer feels like not letting me in!

Thanks for any help!

Ant


Edit: Just noticed: it acknowledges when I type the wrong password for logging in, but just does nothing when I type the correct one

---

### Post by Iowan on 2008-08-11
I've been looking through the **man** pages for **ssh_config** and **sshd_config**, looking for something to explain why your machine hangs on "successful" password.  So far, I've found nothing.  I saw mention of a shell or command after successful login.  If the user's shell were messed up, it wouldn't seem that the "localhost" login would work.  If it's the client messing up, it *might* be in this section (extracted from my workstation):```
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no
```I use it to log into my headless server frequently (and reliability - albeit a Breezy Badger machine).

---

### Post by Joeb454 on 2008-08-11
You know that your password won't be displayed when you type it don't you?

Just want to make sure that's not the issue here :)

---

### Post by jerome1232 on 2008-08-11
you may also want to try connecting like this and posting the output
```
ssh -v username@host
```

---

### Post by antm88 on 2008-08-11
ant@ant-laptop:~$ ssh -v ant@10.0.0.202
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 10.0.0.202 [10.0.0.202] port 22.
debug1: Connection established.
debug1: identity file /home/ant/.ssh/identity type -1
debug1: identity file /home/ant/.ssh/id_rsa type -1
debug1: identity file /home/ant/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '10.0.0.202' is known and matches the RSA host key.
debug1: Found key in /home/ant/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/ant/.ssh/identity
debug1: Trying private key: /home/ant/.ssh/id_rsa
debug1: Trying private key: /home/ant/.ssh/id_dsa
debug1: Next authentication method: password
ant@10.0.0.202's password: 
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_GB.UTF-8


And thats it, it just stops there :| no prompt, just a new blank line which I can't type in.

I just reinstalled ubuntu a couple of days ago! and im fairly sure I haven't done anything to mess it up! very confused!!

---

### Post by antm88 on 2008-08-11
@Iowan, my /etc/ssh/ssh_config file contains exactly the lines you wrote down, is there anything wrong with it?

@Joeb454, I would probably go buy Vista right now if I discovered that was the case :P

---

### Post by y@w on 2008-08-11
Does your user have a valid shell on the remote end?

---

### Post by antm88 on 2008-08-12
yep

---

### Post by antm88 on 2008-08-12
Two more things to make it even stranger:

I can connect to the ssh server with the same command from another computer on the network (IP 10.0.0.210)

I can connect to the ssh server if I plug my laptop into ethernet

So it's a problem with the network card??

---

### Post by jerome1232 on 2008-08-12
I noticed this thread that seems to be dealing with the same issue, I see a link to a purposed solution, hopefully that'll help you [http://ubuntuforums.org/showthread.php?t=838873&highlight=ssh+wireless&page=2](http://ubuntuforums.org/showthread.php?t=838873&highlight=ssh+wireless&page=2)

---

### Post by antm88 on 2008-08-12
I have it working now! Thanks all for help, I just reverted back to older drivers for my network card and everything works perfectly.

I don't really understand how the new drivers let everything work EXCEPT vnc and ssh but hey, I'm happy now!

(using bcm4312 rev 02 btw)

---

### Post by Iowan on 2008-08-12
I'm still confused - cuz it looked like it connected/authenticated - just returned no prompt.  Anyway, glad it's working! Mark this one [SOLVED] (under Thread Tools).

---

### Post by chunkyq on 2008-08-13
edit: Nevermind. I misunderstood the problem. Ignore me.

---

