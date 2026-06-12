---
title: "Remote Desktop Installation through SSH"
date: 2007-11-28
forum: Networking &amp; Wireless
---

### Post by Gyorn on 2007-11-28
Hi there. I've got a server running Ubuntu 6. I want to set up some remote desktop action to this server so I don't have to do everything through SSH. I've looked through a few of the guides on this forum, but I've got one problem.

I've only got SSH access to this server, **nothing else**

I have full root access to this server and can install anything needed. Is it possible for me to set up remote desktop on this machine using only SSH to install it? Any help would be greatly appreciated.

Thanks.

---

### Post by cherry316316 on 2007-11-29
where can I find my ip address, I use the wireless network provided to me by my college.
when I do
“ifconfig”
I get
eth1 inet addr:10.XXX.XXX.XXX
and
lo inet addr:XXX.XXX.XXX.XXX

now from remote, when I try
ssh @10.XXX.XXX.XXX
its refuse to except my password.

also, from the other blog, i edited /etc/ssh/sshd_config file and I added line
AllowUsers

but its still not working. which IP address I am suppose to use.
also, when I open a website, which gives IP address, it shows my IP address as
127.XXX.XXX.XXX
which is different from 10.XXX.XXX.XXX which i get using “ifconfig”
Thanks

---

### Post by Gyorn on 2007-11-29
I already have SSH set up, that's not what I'm asking. I'd like to know if it's possible to install remote desktop capabilites into the server using ONLY SSH. Not a *total* noob here :)

---

