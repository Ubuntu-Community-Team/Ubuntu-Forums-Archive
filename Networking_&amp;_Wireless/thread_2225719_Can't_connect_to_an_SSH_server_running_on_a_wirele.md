---
title: "Can't connect to an SSH server running on a wireless connection."
date: 2014-05-22
forum: Networking &amp; Wireless
---

### Post by Broghan on 2014-05-22
I've been trying  to find a solution to this problem for hour and I've decided to ask for help. I have an SSH server running on my laptop but I can't connect to it from LAN or from the internet. I tested if it could be a router setting by putting a server on my desktop and everything worked fine. I've already checked my router for wireless isolation and it was turned off. I'm at a loss. Please help.    Laptop > Desktop: Works  Desktop > Desktop: Works  Desktop > Laptop: Fails  Laptop > Laptop: Fails

---

### Post by jonobr on 2014-05-22
The way your describing it sounds as if you may be sshing to your laptop and it doesnt have openssh on there?

On the laptop try to ssh localhost, if the connection is refused then you need to install openssh on there

---

### Post by Broghan on 2014-05-22
I'm sorry I forgot to mention that I have OpenSSH on my laptop and I can connect to it. It's also not simply giving me a "connection refused message." It simply times out.

---

### Post by beaucoder2 on 2014-05-23
Just a thought. I had SSH difficulties until I added entries in the PUTTY setup of either the ip address or the computer name. If using the computer name I had to make the proper entries in the /etc/hosts file: e.g. "192.168.1.3   New1404Desktop". Once SSH knows the ip address it seems able to always find provided the computer is up and running. PUTTY has a series of config setup entries. I just used the ip address and the hosts entries. Simple and easy to use. 

HTH

Ubuntu Ken in Sugar Creek

---

### Post by Broghan on 2014-05-23
I appreciate your help but I don't think that's it. I copied all of the settings from my laptop on my desktop and I tried connecting the same way. It worked, but I'm not sure what's different. I've mad FTP servers without problems before. Of course, I have no idea if that means anything. Your idea is worth a try. Thanks.

---

### Post by beaucoder2 on 2014-05-23
Hi Broghan,

Nice to know you got it going. Yes, it would have been nice to know what made the difference. This networking business is at times maddening. But so, so nice when it works. Much success.

Ubuntu Ken in Sugar Creek

---

### Post by Broghan on 2014-05-23
There's been a miscommunication here. Sorry for the confusion. My laptop is not working. I meant I had copied the files and put them on my desktop so they would both have the same setting and my desktop works. My laptop times out every time.

---

### Post by beaucoder2 on 2014-05-23
What I meant:  Each computer has to be able to know the ip address of the computer you want to connect to. You can get the ip address by clicking on the Network icon in the tray bar then clicking on Connection Information. The ip address is under IPv4.
Each computer must have a DIFFERENT address AFAIK. From the computer you wish to connect to the other computer you must be able to tell SSH what or where that other computer's ip address is. I use Putty from the Ubuntu Software Center as it is very easy to use. I use either of the ip address as in 192.168.1.11 or the /etc/hosts file content of the computer name and ip address so that SSH can lookup 'New1404Desktop' to get the ip address of 192.158.1.11 via the hosts file entry of '192.168.1.11     New1404Desktop'. Either way works fine provided the ip address and computer name are correct. 

Can you ping laptop to laptop?  

First try to ping the other computer (laptop to laptop or desktop to laptop). Get the ip address as indicated above and ping from one computer to the other. If you can't ping you can't connect. Your router or wireless adapters may be incompatible. If you can successfully ping then you should be able to put the proper address in Putty and then see the other computer. You then have to be able to enter the proper user name and then the password. This has worked for me. 

HTH,

Ubuntu Ken in Sugar Creek

---

### Post by Broghan on 2014-05-23
Pinging the computer was one of the first things I did when I had a problem with it. I can ping it successfully. I've also been using the IP address because I didn't want to go through the trouble of setting up the host file. All of my computers have their own IP addresses. I tried using the terminal on Linux and Putty on Windows. No luck. Example of the command I'm using: ssh 192.168.2.113

---

### Post by beaucoder2 on 2014-05-23
It may be a case of permissions. In one case I ran as best as I can recall: 'smbtree -d3 -vvv' to get debugging info. It was a case of the debugger catching the user/password missing. Not sure of the specifics as I just ran the command and after the password update all was well. Have you run 'net usershare info --long' ? Not sure what SSH will do if no shares exist. 

Ubuntu Ken in Sugar Creek

---

### Post by Broghan on 2014-05-23
Nothing happens when I run the command.

---

### Post by beaucoder2 on 2014-05-23
That exhausts my meagre work with SSH. Have used it for about a week. Past experience has taught me to google any and all possibilities, not just this forum. AskUbuntu, StackOverFlow and other such tech sites sometimes deliver the prized information. Keep at it. 

Ubuntu Ken in Sugar Creek

---

### Post by Broghan on 2014-05-23
Thanks for your help. I've been looking all over the place and I thought I might as well ask. I guess I'll keep looking.

---

### Post by steeldriver on 2014-05-23
If you can connect to the laptop from itself using ssh localhost, but not from a different machine on the same LAN, the first thing I would be checking is the firewall status on the laptop. You can check if the port is open to external connections or only accepts loopback using

```

sudo netstat -nlpt | grep :22

```

(replace the :22 with the appropriate port if you are not using the default one). If you're running UFW then you can also check the current rules with

```

sudo ufw status numbered

```

---

### Post by CharlesA on 2014-05-23
Give that a shot ^.

It would also help if you posted your /etc/ssh/sshd_config file after removing any personal info - put it in code tags (select the text and click on the # button).

---

### Post by jonobr on 2014-05-23
Hello


On the laptop open a terminal window
type

sudo tcpdump - i any -vvv port 22

Then from another client, ssh to the laptop.
Post the results here

---

### Post by Broghan on 2014-05-23
```
# Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
HostKey /etc/ssh/ssh_host_ed25519_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 1024

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile    %h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes
```
[ATTACH=CONFIG]253392[/ATTACH]

---

### Post by CharlesA on 2014-05-23
Turn off ufw and see if it allows you to connect.

```
sudo ufw disable
```

Looks like a firewall problem to me because ufw should deny all incoming connections automatically by default, so you would have to specifically allow port 22 through the firewall.

---

### Post by Broghan on 2014-05-23
Thanks that did it. My only questions now are how can I add a new rule allowing traffic and why wasn't the firewall a problem on my desktop? The funny thing is I thought I had made a new rule allowing it.
I didn't even make exceptions on my desktop.

---

### Post by jonobr on 2014-05-23
Odd, you dont seem to have tcpdump.
You should install it or ngrep or something like that as its very useful for networking issues

[http://en.wikipedia.org/wiki/Tcpdump](http://en.wikipedia.org/wiki/Tcpdump)

---

### Post by CharlesA on 2014-05-23
> **Broghan said:**
> Thanks that did it. My only questions now are how can I add a new rule allowing traffic and why wasn't the firewall a problem on my desktop? The funny thing is I thought I had made a new rule allowing it.
I didn't even make exceptions on my desktop.

Check this out:
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

