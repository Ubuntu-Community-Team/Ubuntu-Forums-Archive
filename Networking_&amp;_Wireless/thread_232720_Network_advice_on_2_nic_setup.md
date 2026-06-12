---
title: "Network advice on 2 nic setup"
date: 2006-08-09
forum: Networking &amp; Wireless
---

### Post by caffine_fizz on 2006-08-09
Hi,

I'm a new user to linux and networking and am having some dificultiles configuring my network.

As it stands i have:
[LIST]
[*]Router 1 (wireless with 4 port switch and adsl modem)
[*]Router 2 (wireless with 4 port swich)
[*]Ubuntu 6.06 (lamp server install with 2 nics installed)
[*]Home Network (containing 3 pc's, a mix of xp home and pro)
[/LIST]

What i want to do:
[LIST]
[*]Use one of the nics on the linux server, as a web server
[*]Use the other nic on the linux server as a samber server  and access  SSH (for windows machines only)
[/LIST]

i'm yet to install samba in the linux server as i've hit some strife accessing it through ssh from my windows machine. I can ping each pc from both linux and windows box's (not fire wall issue, unless i have to edit iptables which i havn't yet done) but keep getting "Network error: Connection refused" when i attempt to connect using the ip address of the second LAN designated nic in my server; the log from putty is as follows:

> 2006-08-09 18:46:49	Looking up host "192.168.1.3"
2006-08-09 18:46:49	Connecting to 192.168.1.3 port 22
2006-08-09 18:46:50	Failed to connect to 192.168.1.3: Network error: Connection refused
2006-08-09 18:46:50	Network error: Connection refused
 

Could someone please guide me in checking my network configuration on the server, i've followed the trouble shooting sections but they dont seem to be helping me?

Also should i be subnetting the 2 sections, not doing so, should i be?

cheers in advance

---

### Post by caffine_fizz on 2006-08-09
I should also mention that i havn't "apt-get install SSH" as it already seems to be present in the /ect/SSH from the LAMP install.

---

### Post by alamba on 2006-08-09
What does the following give you?
1. cd /etc/init.d
2. ./sshd restart

Also do the following:
1. apt-get install nmap
2. nmap localhost

Does the ssh port show up?

A

---

### Post by caffine_fizz on 2006-08-09
Thanx for helping

when i try restarting ssh from init.d says "bash: /sshd: no such file or directory" (just incase 'sshd' was a typo i also tried 'ssh' and got the same result).

This is strange because i have the configuration files in /etc/ssh

When i try to get nmap says "couldn't find package nmap".

What should i try now?

---

### Post by caffine_fizz on 2006-08-09
Any Suggestions? As mention i'm a noob to linux and don't know where to go, references read don't seem to help my situation.

---

### Post by caffine_fizz on 2006-08-09
After some further searching i managed to find a post on a similar problem.

To correct it i had to delete lines from the **/etc/apt/apt.conf** file. the lines i deleated refer to the CD rom and a Proxy server either of which i don't require, deleted lines were:

[LIST=1]
[*]Acuire::http::Proxy "false"
[*]APT::Authentication::TrustCDROM "true";
[/LIST]

**Note: if your using a proxy you'll need to leave the first line in and supply the required details.**

After doing this apt-get update started working enableing me to get the openssh-server (not installed in the default LAMP instillation and my original problem).

you may if you also experience a similar problem want to comment out or delete the reference to the CD in the /etc/apt/sources.list at the top of the file to get rid of error messages from the previous delete. 

Hope this helps

---

### Post by alamba on 2006-08-10
Buddy your problem has nothing to do with apt.conf unless u're not able to install stuff from the web. Here's what you need to do:

1. apt-get install sshd
2. /etc/init.d/sshd restart

That should get you up and running.

EDIT: Just saw that u figured it out...good for you!

A

---

### Post by loic_ on 2006-08-10
.

---

