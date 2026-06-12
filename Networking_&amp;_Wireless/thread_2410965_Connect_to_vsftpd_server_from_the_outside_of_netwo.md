---
title: "Connect to vsftpd server from the outside of network"
date: 2019-01-22
forum: Networking &amp; Wireless
---

### Post by willrock2850 on 2019-01-22
Hello everyone,

I'm a new one to ubuntu. I setup an vsftpd server for my computer and connect from another computer in my network, everything was so good, but when I tried to connect from the outside of my network I got this error and I don't understand why.
So if you know how to fix this please help me, thank a lot.  


```
Status:	Connecting to 14.161.6.51:3389...Status:	Connection established, waiting for welcome message...
Response:	220 (vsFTPd 3.0.3)
Command:	AUTH TLS
Response:	530 Please login with USER and PASS.
Command:	AUTH SSL
Response:	530 Please login with USER and PASS.
Status:	Insecure server, it does not support FTP over TLS.
Command:	USER bloom-linuxftp
Response:	331 Please specify the password.
Command:	PASS *********
Response:	230 Login successful.
Status:	Server does not support non-ASCII characters.
Status:	Logged in
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/" is the current directory
Command:	TYPE I
Response:	200 Switching to Binary mode.
Command:	PASV
Response:	227 Entering Passive Mode (14,161,6,51,177,144)
Command:	LIST
Error:	Connection timed out after 20 seconds of inactivity
Error:	Failed to retrieve directory listing
```

---

### Post by TheFu on 2019-01-23
I cannot help with plain FTP though routers and firewalls. Too hard and my router isn't smart enough.

But plain FTP isn't safe. No encryption happens, so sending logins can be seen just like reading a postcard - userid/password - in plain sight.

Plain FTP uses inbound and outbound network connections.  This means that a firewall has to know to dynamically open ports, which are usually randomized, for every connection.  You can read more about the FTP protocol either on wikipedia or in the formal RFCs. [https://tools.ietf.org/html/rfc959](https://tools.ietf.org/html/rfc959)  It was designed for a different time, when the internet was relatively safe - 30 yrs ago.

For file transfers over the internet, there is a better, more secure protocol, sftp.  Every platform has great sftp clients. It is designed to work using exactly the same commands as plain FTP. In fact, I've swapped out the FTP client binary for the sftp binary for some systems where we didn't have the code, but they called ftp and sent commands. It all worked perfectly.
 Linux file managers have sftp support built-in.  Best of all, sftp only uses 1 open port, the ssh port, which is easily controlled, and encrypts all traffic, including the login credentials. There are very simple tools to prevent brute force attacks.  Anyways, if you are interested in using sftp, I'm happy to help.  

Sorry I can't help with any plain FTP server. Haven't run one of those since 1995.

---

### Post by willrock2850 on 2019-01-23
Hi TheFu,
I'm so happy to hear that you can help me about sftp.
If you can, please give me an step by step setup.

Thank you so much.

---

### Post by TheFu on 2019-01-24
If you have ssh setup, then you get sftp for free.  So, you can follow any ssh setup guide.  The overview is:
* **sudo apt install openssh-server fail2ban** (on the server)
Then use any sftp client you like to connect via IP, hostname, DNS - whatever name resolution you've configured for the network.

openssh-server enables ssh, scp, and sftp services over the default port. 22/tcp.

fail2ban blocks multiple brute-force attempts to hack in on the standard port for ssh.  If you change from 22/tcp, then you need to modify fail2ban ssh-protection to the new port.  This protection is for any ssh-based connection, including sftp.

If you want to allow internet access for ssh, scp, sftp, then the router will need to forward some external port to the static IP for the ssh-server on port 22/tcp.  If your server doesn't have a static IP, set one.

Over the internet, you shouldn't allow passwords to be used.  Only ssh-keys should be allowed.  The same key works for any ssh-based connection. There must be 50+ useful ways to leverage ssh and the keys.  ssh-keys are one of the few things in this world that are both more convenient AND more secure.  

ssh-keys are created on the clients.
* **ssh-keygen**  # to make a default RSA key.  You might want to force an elliptic key for more security.
* **ssh-copy-id userid@server**   # to push the public key to the userid on the remote server.  Ignore any other instructions that show how to copy the key over. ssh-copy-id does the right thing correctly.
* Lastly, you should work through any ssh-security settings guide to lock down some of the settings, block remote root, white-list 1-2 userids to have access, force the use of keys-only for any connections over the internet.  Stuff like that. These would be made inside the sshd server config file - it is in /etc/ssh/sshd_config.  There is a manpage for that file - **man sshd_config**
That last thing is the last 20% of the security. fail2ban does a reasonable job, but it has been known to fail.  Just moving off the default port for the internet connect to some really high port will almost completely solve the hacking. Almost.  I leave the sshd running on the default port on the servers here, just the WAN router translates a non-default port for sshd.

I've written a few ssh articles over the years.  Others have done it better, I'm certain, but here they are:
[http://blog.jdpfu.com/2011/07/14/easy-key-based-ssh-authentication](http://blog.jdpfu.com/2011/07/14/easy-key-based-ssh-authentication)
[http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)
[http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)
[http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh](http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh)

ssh is amazing.  Unix people use it daily, constantly.  I have 9 terminals open now into 8 other systems, 1 is a local terminal.  ssh is how my backups work.
ssh is how the remote desktop tool I use on travel works.
ssh is used by rsync, rdiff-backup, vim, sshfs.
ssh is how I safely browse the internet from cafes by using a SOCKS proxy, that goes over an ssh tunnel. Effectively, my web traffic appears to come from my house connection, regardless of where I am in the world.  This same connection let's me stream video, audio, and access other internal web-services on the house LAN, securely. None of those other services are available on the internet.

ssh rocks!   and you get sftp for free.

---

### Post by willrock2850 on 2019-01-24
Hi, 
While I was waiting for your support today, I searched on google to find out how to install sftp like you said
A lot of tutorial and I followed one of them to install but it still can't connect from outside
I have already setup port redirection on my router.

---

### Post by willrock2850 on 2019-01-24
JESUS I made it, I MADE IT
suddenly don't know why I fixed it today, using ssh-server like you said

Thank for your support dude \\:D/

---

