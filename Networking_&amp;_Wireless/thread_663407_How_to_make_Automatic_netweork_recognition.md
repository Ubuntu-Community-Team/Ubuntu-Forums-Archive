---
title: "How to make Automatic netweork recognition?"
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by losi on 2008-01-10
Hi,
I am new in Ubuntu. (former SUSE user).
I installed Ubuntu 10.1 in a DELL laptop at my home. My friend took it and did not work. I checked and I was not able to set the IP address and the name server automatically nor by manual.
Questions;
1. How to set it automatically?
2. I try to make what was written int  he help. When asked the password in the console I wrote it and was not accepted. Same happened (password was not accepted) when I wrote su. 
Why not accept my password? 
(I installed and I know there is no other password.)
Thanks in advance.
losi

---

### Post by ladjack on 2008-01-10
> I installed Ubuntu 10.1

Where did you get it, dude it is 7.10 current stable :)

> 1. How to set it automatically?

there must be DHCP server in network that gives you dynamical IP address, no other way to get IP address automaticaly.

> 
2. I try to make what was written int he help. When asked the password in the console I wrote it and was not accepted. Same happened (password was not accepted) when I wrote su. 
Why not accept my password? 
(I installed and I know there is no other password.)


you should enter your password instead, not root password, to do something that need root's priv.

good luck.

---

### Post by losi on 2008-01-10
Hi ladjack,
Thanks for the prompt and helpful answer.
Correction....the right number of version is really 7.10 (sorry, this was my mistake)

To write the password is not clear to me. (On my desktop also installed it and will check also) I made the installation. I had to give a password and I am a user with nearly full administrator right. But what password I have to give to get admin right or for me as user? How I set this password first? I prefer not write the different between Ubuntu and SUSE but this make me a little confuse now. 
Thanks.
Best regards,
losi

---

### Post by ladjack on 2008-01-10
When you installing your ubuntu, installer ask you to add ordinary user and set password for him. Then installer ask you for root's password. So later, when you need to do something administrative, like setting up ip-address or dns-server, and system ask you for password you need to enter your "ordinary user" password. Couse, you have been added by installer to sudoers config file.

---

### Post by losi on 2008-01-10
Hi ladjeck, Hi all,
Thanks for the answer. I install Ubuntu 7.10 about 5 times. (only)
But as I remember asked me only once. From here my confusion. I will look on the installation that already exist and will install it again (and again hopefully) 
Will come back in in the next 1-2 days.
Best regards,
losi

---

### Post by lahook on 2008-01-10
the root password is disabled by default
you need to use sudo instead of su-
for example user@ubuntu$ sudo gedit /somefile/youneed/rootpermission/for
                    password for user  (password for main user)
                   user@ubuntu#
i hope this is the infortmation you were looking for.
when i first switched to ubuntu i had a hard time remembering to use sudo

---

### Post by murmel on 2008-01-10
```
sudo passwd
```
first enter your users password and then the password you want root to have (twice!)

---

### Post by losi on 2008-03-29
thanks for all.
This problem solved with a total restart of the router. 
NAturally had to add the user name, passw etc.
It was not mine. 
Thanks again.
Losi

---

