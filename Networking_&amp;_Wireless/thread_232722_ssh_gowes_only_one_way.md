---
title: "ssh gowes only one way"
date: 2006-08-09
forum: Networking &amp; Wireless
---

### Post by philippjosefrichard on 2006-08-09
Hallo

I have got kubuntu 6.06 at the one side and Fedora Core 3 at the other side.

From ubuntu I can do a ssh 192.168.1.10, i does work
But I cannot do a 
ssh 192.168.1.20 from FC3 to ubuntu

[erwin@philipp ~]$ ssh 192.168.1.20
ssh: connect to host 192.168.1.20 port 22: Connection refused


Is this due to a firewallproblem?

How can I solve it?
thanks
Philipp

---

### Post by scxtt on 2006-08-09
what firewall are you using?

---

### Post by philippjosefrichard on 2006-08-09
what firewall? 


on FC3, which is the PC from which the login onto ubuntu does not work):

in the services-List I found iptables, but it is stopped

in UBUNTU I could not find iptables or something similar
I do not know, how to search for it.

How can I check it in UBUNTU?
Thanks 
philipp

---

### Post by scxtt on 2006-08-09
if you haven't explicitly installed a firewall frontend (either firestarter {gnome} or kmyfirewall {kde}) then a firewall shouldn't be the issue ...

try **ps -ef | grep ssh** on the ubuntu box, and you should get something akin to:
[html]:> ps -ef | grep ssh
root      4712     1  0 01:42 ?        00:00:00 /usr/sbin/sshd
scxtt     6728  6695  0 02:12 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager
scxtt    10603  9151  0 05:33 pts/1    00:00:00 grep ssh[/html]if you don't, you most likely need to install a SSH server (not done by default) - a **sudo aptitude install openssh-server** will solve that problem ...

---

### Post by philippjosefrichard on 2006-08-09
Oh, I am silly!  On UBUNTU sshd does not run.

In services I cannot find sshd



typing the command sshd or  "man sshd" does not work. So I suppose, sshd is not installed.

but:
sudo apt-get install sshd  does not find sshd

in Fedora I would do yum update yum to get the recent repositories and then
yum install sshd  to get sshd with all dependencies installed.

Do I have to prepare apt-get before I can use it? (something like yum update yum)


Thanks for hints
Philipp

---

### Post by SkynetNZ on 2006-08-09
when i installed SSH in ubuntu i used the command 

sudo apt-get install **SSH**

Not sshd 

hope that helps

---

### Post by philippjosefrichard on 2006-08-09
OK, Thanks a lot.
:D

sudo apt-get install ssh finds openSSH-server !!!, not sshd

It is OK now 

Thank you

Have a nice Day

Philipp

---

### Post by SkynetNZ on 2006-08-09
Happy to help

---

