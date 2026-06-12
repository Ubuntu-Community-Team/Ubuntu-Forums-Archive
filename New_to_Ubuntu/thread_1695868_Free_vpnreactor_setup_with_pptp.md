---
title: "Free vpnreactor setup with pptp"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by hdanap on 2011-02-26
Hi,

I read a post here and found the vpnreactor, but i found that the  instruction given on the site is only for the paid service using openvpn as the connection type but for the free service one can only use pptp as the connection type.

Pls can  someone give me detailed instruction of how to set up with the pptp  option, 

I have been sent a user name from vpnreactor and i have a password.

After i setup the way i think it should be done, i get connection failed.

I have already done the sudo apt-get install network-manager-openvpn.

Thank you

---

### Post by stmiller on 2011-02-26
openvpn is something different from pptp, if that helps. :/

VPN settings are the same for all, just the how-tos different. 

( [https://www.vpnreactor.com/setup_tutorials.html](https://www.vpnreactor.com/setup_tutorials.html) )

pptp should just need a server name, username and password to work. :/

Otherwise you may have to contact that company's support for help with their service offering...

---

### Post by hdanap on 2011-02-26
Thanks for the reply, but that still didnt work, thanks thou

---

### Post by spl7 on 2012-09-28
I just went through the pain of doing it.  Its similar to the openvpn under ubuntu, but:
click create vpn,
then choose pptp as the connection type
the gateway must be vpn.vpnreactor.net for the free accounts
put in your user name and your password
under advanced, choose "use point-to-point encryption (mppe)
uncheck allow bsd data compression
uncheck allow deflate data compression
uncheck use tcp header compression

---

### Post by overdrank on 2012-09-28
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

