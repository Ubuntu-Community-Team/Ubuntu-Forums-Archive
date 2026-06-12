---
title: "Trusted SSH works under Debian, not under Ubuntu"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by mitchx3 on 2008-08-14
Im setting up trusted (no password) ssh using the following commands:

    user1@comp1: ssh-keygen -t rsa 

    user1@comp1: ssh user2@comp2 mkdir -p .ssh

    user1@comp1: cat .ssh/id_rsa.pub | ssh user2@comp2 'cat >>         .ssh/authorized_keys'

    user1@comp1: ssh user2@comp2

The commands complete successfully (and passwordless login is possible) when executed from my ubuntu desktop to my debian laptop. But when I execute them on my ubuntu desktop from my debian laptop I get "bash: .ssh/authorized_keys: Permission denied". Then tried changing the 2nd to last command to  
    cat .ssh/id_rsa.pub | ssh root@comp2 'cat >> /home/user2/.ssh/authorized_keys'
which completed successfully, but then still required a password for the last command. I tried "chmod -R 777" before and after trying the root/explicit path version. 

Thanks, Mitchx3

---

### Post by dannyboy79 on 2008-08-14
what does the sshd_config file look like on your debian machine?

---

### Post by mitchx3 on 2008-08-14
I forgot about that config file.

everything was identical between the two except:

debian: 
RhostsRSAAuthentication no
HostbasedAuthentication no
PermitEmptyPasswords no

ubuntu:
RhostsRSAAuthentication yes
HostbasedAuthentication yes
PermitEmptyPasswords yes

I think I may have changed that a while ago working on the same project from another angle. Just changed back checking functionality, will post results.

---

### Post by mitchx3 on 2008-08-14
Did not fix problem. I wonder if PAM settings I was changing while trying to connect to a domain would do this?

---

