---
title: "sudo: unable to resolve host"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by bantucrazed on 2009-10-07
When I enter a command in Ubuntu 9.04 remix for netbooks, the commands will run, but lately, I've been receiving the following prompt before the command runs:  "sudo: unable to resolve host."    I looked at a similar message in the forums and tried to edit the host information by cuttting and pasting and changing icarus lapttop for ria laptop, but it still doesn't work.   Here's my cat /etc/hosts information (someone asked Icarus for it, too): 

ria@ria-laptop:~$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    ria-laptop.wp.comcast.net

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

This is what I took from the Icarus site and posted into the hosts program:

127.0.0.1 localhost
127.0.1.1 ria-laptop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I'm an absolute newbie...thank you!:popcorn:

---

### Post by mac9416 on 2009-10-07
Hey, bantucrazed, could you paste the exact error you get when trying to use sudo and the contents of your /etc/hostname? Thanks.

---

### Post by bantucrazed on 2009-10-07
it's stopped doing it?????   it was reading though, just basically what i typed into the subject line.   pls keep the thread open in case the problem returns.   thanks

---

