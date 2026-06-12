---
title: "SSH is acting weird."
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by cactaur on 2007-05-29
I recently set up my desktop to be an SSH server. However, sometimes when I try to access it via the internet (IP address and Dynamic DNS host), I can't connect. I use no-ip as the Dynamic DNS host, and there are some occasions where it works. However, I don't think the problem lies there, because I can't even connect directly via my IP address (as reported by [IP Chicken]("http://www.ipchicken.com")). Heck, I can't even ping my IP address when that happens. I have verified that sshd is running and is listening to port 22. Does anyone know what the problem could be?

EDIT: I don't think it's actually a problem with SSH. Since I'm unable to ping my own ip address, I think it's a problem with the connection. I tried flushing iptables (sudo iptables -F), but that does not help. I'm still thinking of what the problem could possibly be.

---

### Post by mbradlcu on 2007-05-29
just to make sure sshd is running and accepting connections ssh to localhost on the box.. I suspect this will work.. if so then make sure your default iptable policies are all accept.. I suspect they will be,, if so then if you can , test connecting via lan,  again I suspect this will work too.. in that case does your ISP allow connections to port 22? Please let me know your findings.
thanks

---

### Post by cactaur on 2007-05-29
Thank you.

SSHing localhost DOES work. And my iptables does accept all. And yes, I can connect through LAN.

I'm not too sure if my ISP blocks the port. However, I did set SSHD to listen to port 2200 in addition to 22, and tried to connect via port 22, but I still cannot make a connection there. So I suspect that it's not a port-blocking issue.

---

### Post by kilroy423 on 2007-05-29
> I'm not too sure if my ISP blocks the port. However, I did set SSHD to listen to port 2200 in addition to 22, and tried to connect via port 22, but I still cannot make a connection there. So I suspect that it's not a port-blocking issue.

It is very likely a port-blocking issue if you run behind a router and if not then the isp can be blocking it which will result in you being able to connect locally and still being able to ping from an outside address.  I don't believe that your ISP will block port 2200 though it is possible, maybe try using a random port and connecting from an outside address.

dan

---

### Post by cactaur on 2007-05-29
> **kilroy423 said:**
> It is very likely a port-blocking issue if you run behind a router and if not then the isp can be blocking it which will result in you being able to connect locally and still being able to ping from an outside address.  I don't believe that your ISP will block port 2200 though it is possible, maybe try using a random port and connecting from an outside address.

dan

Nope, I tried several different ports at random and from another computer. None of them work.

---

### Post by rcmiv on 2007-05-30
> I recently set up my desktop to be an SSH server. However, sometimes when I try to access it via the internet (IP address and Dynamic DNS host), I can't connect. I use no-ip as the Dynamic DNS host...

I am having the same problem with the same setup, and it just started this morning.  I can ssh from within the lan, but if try to connect via the internet, the machine simply drops the connection.  

I was also using denyhosts, and my lan pc's ip and work ip both kept ending up in hosts.deny.  I removed denyhosts, but it still isn't working.  The last log provided by denyhosts shows very large blocks of ip's being banned at once, which is odd behavior.

Any more info would be greatly appreciated.

-rcmiv

---

### Post by mbradlcu on 2007-05-30
denyhosts can be configured to get a ban list from a master server, maybe you have it configured that way?
ok back to the ssh issue.. I would do a tcpdump of port 22 and see what's hitting the box, eg:
```
sudo tcpdump -t -i eth{your_card} tcp port 22
```

---

### Post by rcmiv on 2007-05-30
> denyhosts can be configured to get a ban list from a master server, maybe you have it configured that way?
ok back to the ssh issue.. I would do a tcpdump of port 22 and see what's hitting the box, eg:

Thanks for the reply.  Just checked, and removing denyhosts has solved my connectivity issues.  What changed from yesterday to today is my now my main concern, of course.

Plan to reinstall denyhosts, and do a thorough check of the config file, am running rkhunter as I type, and will do your suggested tcpdump as well.  Security is a process, after all :\

Also, cactaur, didn't mean threadjack you.  Hopefully some of this info will be helpful.

-rcmiv

---

### Post by cactaur on 2007-05-30
> **mbradlcu said:**
> denyhosts can be configured to get a ban list from a master server, maybe you have it configured that way?
ok back to the ssh issue.. I would do a tcpdump of port 22 and see what's hitting the box, eg:
```
sudo tcpdump -t -i eth{your_card} tcp port 22
```

Ok, when I ssh the box while running tcpdump, this is what's reported over and over. However, ssh still doesn't get in.

```
IP gregory-desktop.local.1556 > adsl-76-208-151-132.dsl.lsan03.sbcglobal.net.ssh: S 221091017:221091017(0) win 5840 <mss 1460,sackOK,timestamp 1062022 0,nop,wscale 2>

```

I hope this can help you.

And no problem rcmiv. It's just good your issue was resolved.

---

### Post by mbradlcu on 2007-05-31
humm, I'm not sure at this point, my suspect was it wouldn't have any connectivity.. did you alter the sshd_config? if so I'll post my sshd_conf

---

### Post by cactaur on 2007-05-31
Well, I don't think I made any big changes to it. I just changed a few small things. However, I'll put mine up, so you can see if something is changed which shouldn't be. Here it is:

```
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel VERBOSE

# Authentication:
LoginGraceTime 120
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

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
Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes
```

---

### Post by mbradlcu on 2007-05-31
yea that looks the same as my working system ; (
I'm out of ideas at this point, sorry

---

### Post by wirelessmonkey on 2007-05-31
Do this for me... 

# cat /var/log/messages | grep ssh

We're looking for ssh errors, and failed connection notices in the log. 
Are you using proper syntax to ssh in to your machine?   i.e. ssh wirelessmonkey@192.168.0.1 (your ip of course)

---

### Post by merlinus on 2007-05-31
ssh wirelessmonkey@192.168.0.1 (your ip of course)

This works for both my own computer and the other one one my lan, so ssh is definitely working.

But with Gnome/Places/Connect to Server, it craps out after asking for my password, so I cannot get a gui.

Help very much appreciated!

-merlin

---

### Post by merlinus on 2007-05-31
OK now.  A power-off restart got it working again.

I thought it was due to the kernel upgrade.

Weird....

-merlin

---

### Post by mbradlcu on 2007-05-31
good to hear,,, that reminds me last week I actually had the same problem,, I did an /etc/init.d/ssh restart and it fixed it on the debian system.. sorry I didn't remember seeing the elephant in the living room until after you mentioned it... alas

---

### Post by cactaur on 2007-05-31
> **wirelessmonkey said:**
> Do this for me... 

# cat /var/log/messages | grep ssh

We're looking for ssh errors, and failed connection notices in the log. 
Are you using proper syntax to ssh in to your machine?   i.e. ssh wirelessmonkey@192.168.0.1 (your ip of course)

Well, I ran this:

```
gregory@gregory-desktop:~$ ssh -v gregory@76.208.133.25 
OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 76.208.133.25 [76.208.133.25] port 22.
debug1: connect to address 76.208.133.25 port 22: Connection timed out
ssh: connect to host 76.208.133.25 port 22: Connection timed out

```

That was the output of my command (I think I wrote it right). And this is the log entries:

```
gregory@gregory-desktop:~$ cat /var/log/messages | grep ssh
gregory@gregory-desktop:~$ 

```

none, which seems kinda weird.

---

### Post by wirelessmonkey on 2007-06-01
It seems like your ssh daemon might not be running.... 
try: 
ps aux | grep sshd

After, try:
sudo sshd &


....
Keep me posted.

---

### Post by cactaur on 2007-06-01
Well, this is even weirder because it is on.

```
gregory@gregory-desktop:~$ ps aux | grep sshd
root      5274  0.0  0.1   5084   944 ?        Ss   16:23   0:00 /usr/sbin/sshd
gregory   6861  0.0  0.1   2884   744 pts/1    R+   16:28   0:00 grep sshd
gregory@gregory-desktop:~$ ssh -v gregory@76.208.133.23
OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 76.208.133.23 [76.208.133.23] port 22.
debug1: connect to address 76.208.133.23 port 22: Connection timed out
ssh: connect to host 76.208.133.23 port 22: Connection timed out
gregory@gregory-desktop:~$ cat /var/log/messages | grep ssh
gregory@gregory-desktop:~$ 

```

This seems to be getting weirder every day.

---

### Post by cactaur on 2007-06-03
Well, if no one can fix this, can anyone direct me to somewhere where I could get it fixed?

---

### Post by NiceGuy on 2007-06-03
I'm having the same problem, I can't connect to my server through ssh from my desktop running fiesty. I can still connect fine through other machines and, which is really odd, I can still connect if I use gFTP and I can sometimes connect through nautilus (about 50% of the time it times out)... which is nice and all, but what I really need is command line access - if anyone has any ideas how to fix it...

---

