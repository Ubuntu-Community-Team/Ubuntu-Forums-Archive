---
title: "SSH Help"
date: 2008-09-21
forum: Networking &amp; Wireless
---

### Post by PreviousN on 2008-09-21
Hi fellow ubuntuers...

In short, I'm trying to tunnel via SSH. For me this is the preferred method for various reasons...

I've followed this guide on how to set it up: 
[https://help.ubuntu.com/community/SSH_VPN](https://help.ubuntu.com/community/SSH_VPN)

in short it has me entering this command: 
sudo ssh -w 0:0 [email]root@anonymous.servebeer.com[/email]

But...

I encounter an error that I can't for the life of me figure out...:
 
[B][U]Tunnel device open failed.
Could not request tunnel forwarding.[/U][/B]

Under the section: "The SSH command" it reads...
"If no errors occur, then you should be able to see a tun0 interface on both systems as existing..." 

But I *do* see an error... "Tunnel device open failed...Could not request tunnel forwarding..." 

I've checked my sshd_config (both computers) and both allow tunneling. The guide says nothing about what to do on encountering an error, though it does mention errors. 

Please help me?

---

### Post by dmizer on 2008-09-22
In order for the howto to work, you will need to enable the root account on the SSH server. But, this has enough drawbacks that I've not tried it.

---

### Post by PreviousN on 2008-09-22
Thanks for the attempt. I've already enabled the root account. I'm not worried much about security. This box is essentially a DMZ exposed server that is a P3...not important. The rest of my network is locked down...

I've enabled the root account by:

sudo su
passwd
ctl-D

Any other suggestions? Thanks in advance :-)

---

### Post by PreviousN on 2008-09-22
Should also mention...

The client is OSX, the server is Ubuntu Hardy...

---

### Post by dmizer on 2008-09-22
Alright, I've been wanting to try this for quite some time anyway. I'll work on this over the next day or two and see if I can't come up with a working solution for you.

Since I haven't actually done this yet, all I know is that the howto looks like it should work when compared to other SSH VPN tunneling howtos.

What version of SSH is on your OSX client?

---

### Post by Greyed on 2008-09-22
I got this working just last week in a VBox VM to my home machine.  Even went so far as to write a quick script to bring up the tunnel and push all traffic over the tunnel.  I just need to enter a few passwords (sudo, ssh password on local machine, root password on remote machine, sudo on remote machine).  Here's the script (sanitized, of course)

```

#!/bin/sh
sudo ssh -f -N -w 0:0 my_server
sudo ifconfig tun0 192.168.1.102 pointopoint 192.168.1.101
ssh my_server sudo ifconfig tun0 192.168.1.101 pointopoint 192.168.1.102
ssh my_server sudo arp -n
sudo route add 123.456.789.123 gw 10.0.2.2 eth0
sudo route add default gw 192.168.1.101 tun0
sudo route del default gw 10.0.2.2 eth0

```

Things you will need to change...
my_server = my server's name
123.456.789.123 = my server's ip
10.0.2.2 = GW in this virtual machine, yours will differ.

It's not pretty but it works for my needs.  Oh, and the arp line is there to verify that the arp entry for 192.168.1.102 is still configured on the server side.  You may need to add it as explained in the tutorial you're following (same tutorial I was following).

---

### Post by PreviousN on 2008-09-22
Thanks :-) Though I got an error message after ssh -w...

I'll try your script out the next time I get a chance though :-) 

I'm using on my ubuntu server...
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007

Can't get the version of osx till later today. 

**_Though it should be mentioned that when I do..._**

"sudo ssh -f -N -w 0:0 localhost" on my ubuntu box...

previousn@flipper:~$ channel 0: open failed: administratively prohibited: open failed


Here's an excerpt from my sshd_config:

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
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
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
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

#Added Sept 21
PermitTunnel yes
```

---

### Post by dmizer on 2008-09-22
Ah ha! I think I see your problem. You said that this command does not work:
```
sudo ssh -f -N -w 0:0 localhost
```
Does this command work?
```
sudo ssh -f -N -w 0:0 [COLOR="Red"]root@[/COLOR]localhost
```

---

### Post by Greyed on 2008-09-22
> **PreviousN said:**
> "sudo ssh -f -N -w 0:0 localhost" on my ubuntu box...

previousn@flipper:~$ channel 0: open failed: administratively prohibited: open failed


Er, first off I hope you're not trying to tunnel into localhost.  If so that's your problem.  From the client you'll want to use that command to connect to the server.  

Also, what does the following yield?

```

sudo ssh -v -f -N -w 0:0 server_ip

```

Also you said you set the root password to clear?

> ```
# Package generated configuration file
PermitEmptyPasswords no
#PasswordAuthentication yes

```

You might want to explicitly allow password auth as well as empty passwords if, indeed, your previous message was meant to say you set an empty password for root.

> **dmizer said:**
> Ah ha! I think I see your problem. You said that this command does not work:
```
sudo ssh -f -N -w 0:0 localhost
```
Does this command work?
```
sudo ssh -f -N -w 0:0 [COLOR="Red"]root@[/COLOR]localhost
```

That won't be it.  Since he is running "sudo ssh" he is running ssh as root.  That means ssh is trying to connect to the remote machine as root.

---

### Post by PreviousN on 2008-09-22
When I enter...
ssh -v -f -N -w 0:0 anon.servebeer.com

```
 ssh -v -f -N -w 0:0 previousn@anon.servebeer.com
OpenSSH_4.7p1, OpenSSL 0.9.7l 28 Sep 2006
debug1: Reading configuration data /etc/ssh_config
debug1: Connecting to previous.servebeer.com [68.6.123.111] port 22.
debug1: Connection established.
debug1: identity file /Users/**/.ssh/identity type -1
debug1: identity file /Users/**/.ssh/id_rsa type 1
debug1: identity file /Users/**/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7
debug1: Miscellaneous failure
No credentials cache found

debug1: Miscellaneous failure
No credentials cache found

debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'anon.servebeer.com' is known and matches the RSA host key.
debug1: Found key in /Users/**/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /Users/**/.ssh/identity
debug1: Offering public key: /Users/**/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /Users/**/.ssh/id_dsa
debug1: Next authentication method: password
previousn@anon.servebeer.com's password: 
debug1: Authentication succeeded (password).
debug1: Requesting tun unit 0 in mode 1
debug1: sys_tun_open: /dev/tun0 open failed: No such file or directory
Tunnel device open failed.
Could not request tunnel forwarding.
debug1: Entering interactive session.

```

Not sure what you mean about root password to clear, but sshd_config DOES say:
PermitRootLogin yes

The password is not an empty password. 

You may be curious why I'm doing all this instead of a vpn...well, I'm trying to make a virtual vpn with my family at home. They use satellite and the satellite blocks vpns...but for some reason *all* ssh works.

Also, SSH -D works. Is there a way to do it using the -D switch instead of the -W switch?

Lastly, the Mac Os X version of ssh is:
OpenSSH_4.7p1, OpenSSL 0.9.7l 28 Sep 2006

---

### Post by Greyed on 2008-09-23
> **PreviousN said:**
> 
```
 ssh -v -f -N -w 0:0 previousn@anon.servebeer.com

```

sudo ssh -v -f -N -w 0:0 anon.servbeer.com

Has to be run as root locally (hence sudo) and it has to connect to root remotely.  This is because it has to create the device in /dev and only root can do that.

> Not sure what you mean about root password to clear, but sshd_config DOES say:
PermitRootLogin yes


It is because in a previous message you wrote...

> 
I've enabled the root account by:

sudo su
passwd
ctl-D


Which shows you changed the password without indication that it was changed to anything.  I was just covering all bases as I, for some reason, thought you had set to to nothing.  ;)

> You may be curious why I'm doing all this instead of a vpn...

Actually, nope.  I stumbled on the SSH method and had it up and running in like 2 hours.  It was dead simple for me to understand.  After I did it manually 2 nights in a row I just took my command history, C&P it into a script and slapped #!/bin/sh in front of it.  Since then I have tried to get Openswan working for a "real" VPN.  Wasted a whole night on it banging my head against a wall because they can't just name stuff naturally (left, right?  Left is local, right is remote?  Then name them LOCAL AND REMOTE!!!) nor do they ever explain how to do anything with X.509 certs even though they're supported!  The documentation is abysmal, all the walkthroughs presume non-X.509 certs.  So based on my experience I would question anyone getting Openswan (or any other "traditional" VPN) working for simple point-to-point VPNs where one controls both ends when this clearly is easier to set up and obviously works.

Besides, if you know most of your traffic is going to be text based you can always add -C to the first command and compress the traffic (I presume) before it gets into the tunnel so you're tunnelling less traffic overall.  I don't think that is possible on other traditional VPN setups.


> Also, SSH -D works. Is there a way to do it using the -D switch instead of the -W switch?

No.  -D works because it doesn't require root to bind to any port over 1024.  However it only tunnels one port on the local machine to one port on the remote machine.  A VPN tunnels all traffic, not just a single port.

---

### Post by PreviousN on 2008-09-23
gotcha. Thanks for all the tips. To rule out everything I've followed your advice:

imac:/Users/anonymous root# ssh -v -f -N -w 0:0 [email]root@anon.servebeer.com[/email]

```
imac:/Users/anonymous root# ssh -v -f -N -w 0:0 root@anon.servebeer.com

OpenSSH_4.7p1, OpenSSL 0.9.7l 28 Sep 2006
debug1: Reading configuration data /etc/ssh_config
debug1: Connecting to previous.servebeer.com [68.6.123.111] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /var/root/.ssh/identity type -1
debug1: identity file /var/root/.ssh/id_rsa type 1
debug1: identity file /var/root/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7
**debug1: Miscellaneous failure**
No credentials cache found

**debug1: Miscellaneous failure**
No credentials cache found

debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'anon.servebeer.com' is known and matches the RSA host key.
debug1: Found key in /var/root/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /var/root/.ssh/identity
debug1: Offering public key: /var/root/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /var/root/.ssh/id_dsa
debug1: Next authentication method: password
root@previous.servebeer.com's password: 
debug1: Authentication succeeded (password).
debug1: Requesting tun unit 0 in mode 1
debug1: sys_tun_open: /dev/tun0 open failed: No such file or directory
Tunnel device open failed.
Could not request tunnel forwarding.
debug1: Entering interactive session.
```


So, I think that its either "Miscellaneous failure" or "sys_tun_open: /dev/tun0 open failed: No such file or directory"

To try to address the "tun0 open failed" I've added to my server's /etc/network/interfaces (per this guide- *[http://www.debian-administration.org/articles/539](http://www.debian-administration.org/articles/539)*):
iface tun0 inet static
      address 10.254.254.1
      netmask 255.255.255.252
      pointopoint 10.254.254.2

Sadly, on the client side, /etc/network/interfaces doesn't exist since its a mac. Any thoughts?

---

### Post by PreviousN on 2008-09-23
(sorry, accidentally double posted...)

---

### Post by PreviousN on 2008-09-23
You know, I think that the problem is on my ubuntu server, despite not knowing where /etc/network/interfaces is on a mac. 

I tried connecting my Hardy ubuntu laptop (following the client instructions on the debian admin website) to a wireless network and am getting the same error...


previousn@flipper:~$ sudo ssh -v -w 0:0 192.168.1.101
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.1.101 [192.168.1.101] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/identity type -1
debug1: identity file /root/.ssh/id_rsa type 1
debug1: identity file /root/.ssh/id_dsa type -1
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
debug1: Host '192.168.1.101' is known and matches the RSA host key.
debug1: Found key in /root/.ssh/known_hosts:6
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /root/.ssh/identity
debug1: Offering public key: /root/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /root/.ssh/id_dsa
debug1: Next authentication method: password
root@192.168.1.101's password: 
debug1: Authentication succeeded (password).
debug1: Requesting tun unit 0 in mode 1
[B]debug1: sys_tun_open: failed to configure tunnel (mode 1): Device or resource busy
Tunnel device open failed.[/B]
Could not request tunnel forwarding.
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
Last login: Mon Sep 22 21:44:53 2008 from 192.168.1.117
Linux raptop 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)
root@raptop:~#

---

### Post by Greyed on 2008-09-23
> **PreviousN said:**
> 
Could not request tunnel forwarding.


Here's the problem.  You're on root, you're connecting as root.  SSHD is not allowing your client to request a tunnel.  Did you restart your SSH daemon after allowing tunnels?

---

### Post by PreviousN on 2008-09-23
Yes, I saved the config file, then did:

sudo /etc/init.d/ssh restart

But, for good times, I'll restart my computer anyways... brb :- )

....

So I've restarted my computer, and now to make things easier, I'm on my Ubuntu laptop...I first got (without sudo)
Tunnel device open failed.
Could not request tunnel forwarding.

I'm now getting (with sudo):
channel 0: open failed: administratively prohibited: open failed

Here's my servers dmesg | tail:```
[   90.577577] NET: Registered protocol family 17
[   94.865895] hda-intel: Invalid position buffer, using LPIB read method instead.
[   99.117092] eth0: no IPv6 routers present
[  113.071655] eth0: no IPv6 routers present
[  234.175937] tun: Universal TUN/TAP device driver, 1.6
[  234.175943] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[  234.176954] tun0: Disabled Privacy Extensions
[  280.700862] tun0: Disabled Privacy Extensions

```

---

### Post by Greyed on 2008-09-23
> **PreviousN said:**
> Here's my servers dmesg | tail:


Oooh, good call.  I hadn't thought of dmesg.

> 
[  234.176954] tun0: Disabled Privacy Extensions
[  280.700862] tun0: Disabled Privacy Extensions


Hm, this is getting outside my experience.  Of course my server is a Debian system which has been through several upgrades.  So this might be something that has come into Debian/Ubuntu after my last install that I just don't have enabled at all.  

A quick peek at Google doesn't seem to turn up anything.  However I think in a bit of serendipity this is the exact same error I'm experiencing with vpnc as detailed in the first hit from Google.  Neat!

---

### Post by PreviousN on 2008-09-23
Hmmm...

I might just install debian then... though I'd like to find out for sure if ubuntu is the problem. My computer doesn't have a cd drive on it...Imagine trying to install a new os on it! Its a PITA. 

Well, if you find anything, keep me informed. 

I found this: [http://tier.cs.berkeley.edu/wiki/HOWTO:IPTunnelling](http://tier.cs.berkeley.edu/wiki/HOWTO:IPTunnelling)
apparently you can add a tun0 interface by entering into the terminal:
sudo iptunnel add tun0...

---

### Post by Greyed on 2008-09-23
I would advise against that.  The key part I was trying to convey was not that my server is running Debian but that it is running Debian that has been upgraded several times.  A freshly installed Debian system will not behave like mine because of the simple fact that it is going to use a different set of defaults since upgrades generally do not replace configuration files that have been modified.

---

### Post by kevdog on 2008-09-23
Interesting thread here guys, I'd be interested if there is a solution.

---

### Post by PreviousN on 2008-09-23
First of all, good news!
Using info from: [http://prefetch.net/blog/index.php/2008/06/26/opensshs-vpn/](http://prefetch.net/blog/index.php/2008/06/26/opensshs-vpn/) 
and 
[http://gentoo-wiki.com/HOWTO_VPN_over_SSH_and_tun](http://gentoo-wiki.com/HOWTO_VPN_over_SSH_and_tun)

I've been able to tunnel to localhost. While that isn't immediatly useful, its a proof of concept.

Secondly, about installing debian: 'gotcha. 
I've got a router that runs ddwrt/openwrt and might check to see if I can cut off the p3 all together. I doubt ddwrt/openwrt has the full sshd though...

I'll try tunneling on something else (my laptop/parents computer) later. For now I've got some stuff to take care of. It seems that I might have had a typo in my sshd_config...maybe? (I doubt it, but theres no other explanation for why it *just* started working)

Anyways, since the main use for this is my family, I've got to wait until tonight to mess with it. My parents aren't, shall we say, computer savvy. I've been testing everything by having my mom open a terminal in osx and entering:

ssh -R 8080:localhost:22 anon.servebeer.com

Then, on my local machine, I enter:

ssh -p8080 (macuid)@localhost


Then I have a shell on my parents computer. I then try out the tunnel and get the error message...Maybe that's been interfering?

I'll have my mom enter the plain -w command later without the tunnel and see what happens.

Unfortunatly, my parents have their computer to auto turn off at night and turn on in the evenings...so that's why I've got to wait!

---

### Post by edwtjo on 2009-07-09
Sorry for the thread bump but the "Disabled Privacy Extensions" is probably because you haven't added 

```

    Tunnel yes
    TunnelDevice any:any

```

to /etc/ssh/ssh_config

---

### Post by sqqop on 2009-09-02
Ok, I run across so many of these unfinished threads involving OSX and SSH interface tunneling (VPNs) that I decided to start suggesting the solution I use. For ease of use, I'll avoid describing port and proxy forwarding. Feedback is welcome!

** Drivers**
First, OSX doesn't come with tun/tap drivers. Download them at [SourceForge's TUN/TAP for OSX project]("http://tuntaposx.sf.net"). You'll also need the drivers loaded on any other OS, but most UNIX/Linux flavors have them standard.

** Privileges**
Both the ssh client and the remote login user need enough privileges to configure the tun/tap interfaces. This means running [FONT=Courier New]ssh[/FONT] as root and loging in remotely as root. I will forever be looking for a means around this (setting read/write permissions on the tun/tap device files doesn't cut it), but it's really not a security threat. Just don't leave a root terminal open and you'll be fine.

** Server Configuration**
You must be able to log in as root.  So far, the only user I can get to configure tun/tap interfaces is the root user.  As far as SSH is concerned, [FONT=Courier New]PermitRootLogin[/FONT] should default to [FONT=Courier New]yes[/FONT], but make sure it is indeed set to [FONT=Courier New]yes[/FONT].

You will, however, need to modify the [FONT=Courier New]PermitTunnel[/FONT] line in your [FONT=Courier New]sshd_config[/FONT] file. [FONT=Courier New]man sshd_config[/FONT] explains everything quite well. The acceptable options for this line are [FONT=Courier New]point-to-point[/FONT], [FONT=Courier New]ethernet[/FONT], [FONT=Courier New]yes[/FONT] and [FONT=Courier New]no[/FONT].

[FONT=Courier New]point-to-point[/FONT] means you're using a tun interface. That is, you're only passing IP packets from one source to one destination. This works fine for routing packets between two subnets (meaning a tunnel between two routers).

[FONT=Courier New]ethernet[/FONT] means you're using a tap interface. Any protocol you can pass over ethernet (including IP) will pass over the encrypted link to the other system. At this point, you can bridge either or both of the tap interfaces with their respective system's actual ethernet interfaces. You probably don't want to bridge both unless you have decent bandwidth for the link. This is the easiest method in my opinion, as it doesn't require mucking about with routing tables.

I find this handy for making a single system look like it's on a remote LAN. All that's required is to bridge the LAN-side tap interface with the actual LAN interface and then assign an IP to the remote system's tap interface (DHCP). Except for latency, the system can't tell it's not directly connected that LAN. Magic! ;)

[FONT=Courier New]yes[/FONT] allows the client to specify either layer 3 (tun/point-to-point) or layer 2 (tap/ethernet) interfaces. I believe it defaults to tun/point-to-point if the client doesn't choose.

[FONT=Courier New]no[/FONT] disallows the [FONT=Courier New]-w[/FONT] option altogether, but does not effect port ([FONT=Courier New]-L[/FONT] and [FONT=Courier New]-R[/FONT]) or proxy ([FONT=Courier New]-D[/FONT]) forwarding.

The [FONT=Courier New]yes[/FONT] option has the most flexibility, so use it:

[FONT=Courier New]**sshd_config**:[/FONT][INDENT][FONT=Courier New]      PermitRootLogin yes
PermitTunnel yes[/FONT]
[/INDENT][B]
Client Configuration[/B]
You can specify client options in one of four ways: on the command line ([FONT=Courier New]-o[/FONT]), in the system-wide configuration file ([FONT=Courier New]ssh_config[/FONT] -- note the lack of a 'd'), in a per-user configuration file ([FONT=Courier New]~/.ssh/config[/FONT]) or in some random file of your own choosing ([FONT=Courier New]-F[/FONT] command line parameter). Note that the system-wide and per-user configuration files are ignored when using the [FONT=Courier New]-F[/FONT] parameter; any options you want from those files will need to be copied to the specified file.

Really, there isn't anything you *need* to configure for the client. the [FONT=Courier New]-w[/FONT] option alone will work fine if you want a point-to-point tunnel. Alternatively, specifying the [FONT=Courier New]Tunnel[/FONT] option will imply a [FONT=Courier New]-w[/FONT]. I like to specify [FONT=Courier New]-o Tunnel=ethernet[/FONT] for my own purposes.

** Examples**
_ Remote laptop connecting to home LAN (tap interfaces, layer 2 tunneling)_
In this example, vertigo is the laptop and blotto is the host on the LAN.  The LAN has a 10.0.0.0/16 subnet; the laptop needs to be on a different subnet to prevent routing issues.

First, set up the bridge on the LAN host.  This example uses OpenBSD as the host, which doesn't strictly have tap interfaces, but its tun interfaces in link0 mode are (exactly?) the same.  I create the tun and bridge interfaces and then leave them running between connections so I only have to do it once.[INDENT][FONT=Courier New][blotto:~] sqqop% sudo ifconfig tun0 create link0[/FONT]
[FONT=Courier New] Password: [/FONT]
[FONT=Courier New] [blotto:~] sqqop% sudo ifconfig bridge0 create[/FONT]
[FONT=Courier New] [blotto:~] sqqop% sudo brconfig bridge0 add em0[/FONT]
[FONT=Courier New] [blotto:~] sqqop% sudo brconfig bridge0 add tun0[/FONT]
[FONT=Courier New] [blotto:~] sqqop% sudo brconfig bridge0 up[/FONT]
[/INDENT]Next, start the tunnel.  I prefer to have mine sit in the background ([FONT=Courier New]-fN[/FONT]); use [FONT=Courier New]-w[/FONT] to specify the already configured tun interface on the host.[INDENT][FONT=Courier New][Vertigo:~] sqqop% sudo ssh -fNCw any:0 -o Tunnel=ethernet blotto.domain.bob[/FONT]
[FONT=Courier New] Password: [/FONT]
[FONT=Courier New]root@blotto.domain.bob's password: [/FONT]
[FONT=Courier New] [Vertigo:~] sqqop% [/FONT]
[/INDENT]And finally, give the laptop's tap interface an IP on on the LAN's subnet.[INDENT][FONT=Courier New][Vertigo:~] sqqop% sudo ifconfig tap15 inet 10.0.254.167 netmask 255.255.0.0[/FONT]
[FONT=Courier New] [Vertigo:~] sqqop% ping -c 5 10.0.1.82[/FONT]
[FONT=Courier New] PING 10.0.1.82 (10.0.1.82): 56 data bytes[/FONT]
[FONT=Courier New] 64 bytes from 10.0.1.82: icmp_seq=0 ttl=255 time=21.545 ms[/FONT]
[FONT=Courier New] 64 bytes from 10.0.1.82: icmp_seq=1 ttl=255 time=39.664 ms[/FONT]
[FONT=Courier New] 64 bytes from 10.0.1.82: icmp_seq=2 ttl=255 time=28.125 ms[/FONT]
[FONT=Courier New] 64 bytes from 10.0.1.82: icmp_seq=3 ttl=255 time=30.004 ms[/FONT]
[FONT=Courier New] 64 bytes from 10.0.1.82: icmp_seq=4 ttl=255 time=38.458 ms[/FONT]

[FONT=Courier New] --- 10.0.1.82 ping statistics ---[/FONT]
[FONT=Courier New] 5 packets transmitted, 5 packets received, 0% packet loss[/FONT]
[FONT=Courier New] round-trip min/avg/max/stddev = 21.545/31.559/39.664/6.749 ms[/FONT]
[FONT=Courier New] [Vertigo:~] sqqop% [/FONT]
[/INDENT]You can also use DHCP clients like [FONT=Courier New]dhclient[/FONT] or [FONT=Courier New]dhcpcd[/FONT] to obtain an IP.  I'll leave that up to the respective man pages to explain how.  If someone can enlighten me on how to get a proper DHCP lease on a tap interface in OSX, I'd be extremely grateful. :D

To close the tunnel, [FONT=Courier New]kill[/FONT] the [FONT=Courier New]ssh[/FONT] process used to create the tunnel.

_ Connecting two subnets via routers (tun interfaces, layer 3 routing)_
In this example, I'm going to use "local" and "remote" to distinguish the two routers, but the configuration is really mirrored at both ends.  I'm assuming both routers are already passing packets between physical interfaces (meaning they are internet routers).  The local router has a 172.16.1/24 subnet and the remote router has a 10.0/16 subnet.  The two subnets must differ or there will be routing problems.

Start by building the tunnel.[INDENT][FONT=Courier New] [local:~] sqqop% sudo ssh -Cw 2:3 -o Tunnel=point-to-point remote.domain.bob[/FONT]
[FONT=Courier New] Password: [/FONT]
[FONT=Courier New]root@remote.domain.bob's password: [/FONT]
[FONT=Courier New] remote# [/FONT]
[/INDENT]Both systems should now have their tunnel devices; assign IPs to both ends of the tunnel from both ends.[INDENT][FONT=Courier New] remote# ifconfig tun3 tunnel 192.168.254.1 192.168.254.2 netmask 255.255.255.255[/FONT]
[/INDENT]and[INDENT][FONT=Courier New] [local:~] sqqop% sudo ifconfig tun2 tunnel 192.168.254.2 192.168.254.1 netmask 255.255.255.255
[/FONT][/INDENT]Note that the first IP in those commands is that machine's IP and the second is the other's.  At this point, the two routers can talk to each other, but not to anyone else on the foreign LANs.  Add the foreign LANs' subnets to the routing tables so they know who is where:[INDENT][FONT=Courier New] remote# route add 172.16.1/24 192.168.254.2[/FONT]
[/INDENT]and[INDENT][FONT=Courier New] [local:~] sqqop% sudo route add 10.0/16 192.168.254.1
[/FONT][/INDENT]And that's it.  To close down this tunnel, exit the SSH session like normal, wait a second and then hit Ctrl-C to make it stop waiting for the devices to free.[INDENT][FONT=Courier New] remote# exit
logout
^CKilled by signal 2.
[local:~] sqqop%
[/FONT][/INDENT]This will destroy the tun devices and remove the foreign LANs from the routing tables.

There are many more permutations; use your imagination. ;)

A final note: The examples above work on MacOSX, OpenBSD and probably most BSD-like systems.  Linux's syntax for [FONT=Courier New]ifconfig[/FONT] and [FONT=Courier New]route[/FONT] differs, even between distributions.  Let me know what works on Ubuntu.

** Common Error Messages**
[FONT=Courier New]debug1: Remote: Server has rejected tunnel device forwarding
channel 0: open failed: administratively prohibited: open failed[/FONT]
[LEFT] Configuration options are getting in your way. If all you're doing is bringing up an interface tunnel, then check the [FONT=Courier New]PermitTunnel[/FONT] line in your server's [FONT=Courier New]sshd_config[/FONT]. This can also happen if you're trying to forward ports and have [FONT=Courier New]AllowTcpForwarding[/FONT] set to something other than [FONT=Courier New]yes[/FONT]. I'm sure lots of other situations as well.
[/LEFT]
 
[FONT=Courier New] debug0: sys_tun_open: failed to set /dev/tap15 mode 2: Operation not permitted[/FONT]
Client machine couldn't configure its tun/tap interface. Usually from not running [FONT=Courier New]ssh[/FONT] as root.

[FONT=Courier New] debug1: Remote: Failed to open the tunnel device.
channel 0: open failed: administratively prohibited: open failed[/FONT]
The remote server didn't configure its tun/tap interface; most likely you forgot to login into the server as root.

[FONT=Courier New] debug1: sys_tun_open: /dev/tun0 open failed: No such file or directory
Tunnel device open failed.
Could not request tunnel forwarding.[/FONT]
This happens on OSX when you don't have the tun or tap drivers loaded. Probably the same for other operating systems.

[FONT=Courier New] Disabled Privacy Extensions[/FONT]
I'm guessing it's just notifying you that the tun driver didn't load AH/ESP for your garden variety VPNs. This would be expected behavior for SSH tunnels.

[FONT=Courier New]No error whatsoever, but packets still don't pass[/FONT]
Check for firewalls.  This one causes me no end of headaches. :/

---

### Post by juako on 2010-03-24
I wrote today a script that automates the entire process, you can save it as "sshvpn" and do "sshvpn start/stop". The script takes care of the rest. Beware is somewhat ugly to look, but it's not so after you understand the various escaping and string messing, as i had to do remote regexes, sed and whatnot to configure server and client dinamically.

It takes care of the tap devices and remembers which were used, and in my case it accounts to set up SNAT forwarding into the remote network, though this can be used as a base to full L2 bridging (which i plan to do next).

Note i use $rnet to represent the remote network i want to join, looking at it now i see i harcoded the interface. That's another one to modify to do automatically.

Anyway, i hope this is of use to someone, as it is the more intstantaneous way to true VPN over SSH i could came up with. Enjoy! 

```

#!/bin/bash

# prereqs:
# remote host's sshd_config must have "PermitRootLogin=no", "AllowUsers user", and "PermitTunnel=yes"
# "tunctl", in debians it is found in uml-utils, redhats another (dont remember but "yum provides tunctl" must tell)
# remote user must be able to sudo-as-root 
# can opt by routing as in this case or soft bridge with brctl and you get full remote ethernet segment membership :D
# that last i think i'll implement later as an option
# other stuff to do is error checking, etcetc, this is just as came from the oven

userhost='user@host'
sshflags='-Ap 2020 -i /path/to/some/authkey'
vpn='10.0.0.0/24'
rnet=192.168.40.0/24

# START VPN
if [ "$1" == "start" ]; then
  echo setting up local tap ...
  ltap=$(tunctl -b)
  ifconfig $ltap ${vpn%%?/*}2/${vpn##*/} up

  echo setting remote configuration and enabling root login ...
  rtap="ssh $sshflags $userhost sudo 'bash -c \"rtap=\\\$(tunctl -b); echo \\\$rtap; ifconfig \\\$rtap ${vpn%%?/*}1/${vpn##*/} up; iptables -A FORWARD -i \\\$rtap -j ACCEPT; iptables -A FORWARD -o \\\$rtap -j ACCEPT; iptables -t nat -A POSTROUTING -o eth0 -s ${vpn%%?/*}2 -j SNAT --to \\\$(ip r | grep $rnet | sed \\\"s/^.*src \\\(.*\\\$\\\)/\1/g\\\"); sed -i -e \\\"s/\\\(PermitRootLogin\\\).*\\\$/\1 without-password/g\\\" -e \\\"s/\\\(AllowUsers.*\\\)\\\$/\1 root/g\\\" /etc/ssh/sshd_config; /usr/sbin/sshd -t\"'"
  rtap=$(sh -c "$rtap")

  echo setting up local routes ...
  # since my ISP sucks with transparent filters (i can't opt for another where i live), i'll just use my work net as gateway
  ip r a $(ip r | grep default | sed "s/default/${userhost##*@}/")
  ip r c default via ${vpn%%?/*}1 dev $ltap

  echo bringing up the tunnel and disabling root login ...
  ssh $sshflags -f -w ${ltap##tap}:${rtap##tap} -o Tunnel=ethernet -o ControlMaster=yes -o ControlPath=/root/.ssh/vpn-$userhost-l$ltap-r$rtap root@${userhost##*@} bash -c "\"sed -i -e 's/\(PermitRootLogin\).*\$/\1 no/g' -e 's/\(AllowUsers.*\) root\$/\1/g' /etc/ssh/sshd_config; /usr/sbin/sshd -t\""

  echo connected.

# STOP VPN
elif [ "$1" == "stop" ]; then
  echo searching control socket and determining configuration ...
  controlpath=$(echo /root/.ssh/vpn-$userhost*)  
  ltap=${controlpath%%-rtap*} && ltap=tap${ltap##*-ltap} 
  rtap=${controlpath##*rtap} && rtap=tap${rtap%%-*}
 
  echo bringing the tunnel down ...
  ssh $sshflags -o ControlPath=$controlpath -O exit $userhost
 
  echo restoring local routes ...
  ip r c default $(ip r | grep ${userhost##*@} | sed "s/${userhost##*@}\(.*$\)/\1/g")
  ip r d ${userhost##*@}

  echo restoring remote configuration ... 
  sh -c "ssh $sshflags $userhost sudo 'bash -c \"tunctl -d $rtap; iptables -D FORWARD -i $rtap -j ACCEPT; iptables -D FORWARD -o $rtap -j ACCEPT; iptables -t nat -D POSTROUTING -o eth0 -s ${vpn%%?/*}2 -j SNAT --to \$(ip r | grep $rnet | sed \"s/^.*src \(.*\$\)/\1/g\")\"'"

  echo deleting local tap ...
  tunctl -d $ltap  

  echo disconnected.
fi

```

---

### Post by adamlogan on 2010-09-09
> **sqqop said:**
> Ok, I run across so many of these unfinished threads involving OSX and SSH interface tunneling (VPNs) that I decided to start suggesting the solution I use. For ease of use, I'll avoid describing port and proxy forwarding. Feedback is welcome!

** Drivers**
First, OSX doesn't come with tun/tap drivers. Download them at [SourceForge's TUN/TAP for OSX project]("http://tuntaposx.sf.net"). You'll also need the drivers loaded on any other OS, but most UNIX/Linux flavors have them standard.

** Privileges**
Both the ssh client and the remote login user need enough privileges to configure the tun/tap interfaces. This means running [FONT=Courier New]ssh[/FONT] as root and loging in remotely as root. I will forever be looking for a means around this (setting read/write permissions on the tun/tap device files doesn't cut it), but it's really not a security threat. Just don't leave a root terminal open and you'll be fine.

** Server Configuration**
You must be able to log in as root.  So far, the only user I can get to configure tun/tap interfaces is the root user.  As far as SSH is concerned, [FONT=Courier New]PermitRootLogin[/FONT] should default to [FONT=Courier New]yes[/FONT], but make sure it is indeed set to [FONT=Courier New]yes[/FONT].


.... The quote is just a clip plenty more stuff but trimmed for the sake of decency. This post can be found on page 3. 

@Sqqp 

Thank you finally I understand the source of my tunnel error when using "ssh -f -N -D" - OSX does not come with tun tap, ok! 

Have not been able to figure it out for like 2 or 3 months now. I have installed the tun tap from sourceforge. Before I move forward I have to ask, did you find a way to do this without needing to use Root? As is I have Root account disabled in sshd_conf and I'd rather keep it that way for security reasons. I'm using password login with just one username allowed access. From there I can su to root. Currently I'm using ssh as a proxy to get past the firewall where I intern. I'm glad you shared your finding here I was getting desperate.

Will have to come back and read more.

---

### Post by fessyfoo on 2011-01-08
> **sqqop said:**
> You can also use DHCP clients like [FONT=Courier New]dhclient[/FONT] or [FONT=Courier New]dhcpcd[/FONT] to obtain an IP.  I'll leave that up to the respective man pages to explain how.  If someone can enlighten me on how to get a proper DHCP lease on a tap interface in OSX, I'd be extremely grateful. :D


I stumbled on this for osx: 

```
 ipconfig set tap15 DHCP 
```


I'd like to know how to get these interfaces to show up in the system preferences so that I could enable it there.  :)

---

