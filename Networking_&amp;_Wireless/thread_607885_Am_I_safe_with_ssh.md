---
title: "Am I safe with ssh?"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by shane2peru on 2007-11-09
Ok, I have a home network of 2 hard wired, and one wireless all running Ubuntu (one is dual booting).  I have a DSL modem connected to my Router (D-link).  I have recently discovered the wonderful world of ssh and upkeeping the other two computers.  I'm really the only Linux savvy person here, so I manage the updates, setup printers, make any system settings, matter of fact, I made the rest Desktop users, and I'm the only one with admin rights.  All of them have Firestarter installed.  Am I safe ssh-ing into their computers or does this present some sort of security risk?  Thanks.

Shane

---

### Post by AbsolutIggy on 2007-11-09
nvm, answered that bit too fast..

---

### Post by Bushwack on 2007-11-09
If your router isn't forwarding the incoming ssh port to any of your computers then you're safe (providing you have proper wireless security).

If you can ssh into any of your computers from outside your network then I would take the following measures:
- install denyhosts (apt-get install denyhosts)
- disable ssh root login (PermitRootLogin in /etc/ssh/sshd_config)
- make sure all users have good passwords on that machine

If you really want to be paranoid you could:
- change the incoming ssh port
- require public key authentication
- limit the IP addresses that are allowed to connect to your machine

---

### Post by shane2peru on 2007-11-09
> **Bushwack said:**
> If your router isn't forwarding the incoming ssh port to any of your computers then you're safe (providing you have proper wireless security).

If you can ssh into any of your computers from outside your network then I would take the following measures:
- install denyhosts (apt-get install denyhosts)
- disable ssh root login (PermitRootLogin in /etc/ssh/sshd_config)
- make sure all users have good passwords on that machine

If you really want to be paranoid you could:
- change the incoming ssh port
- require public key authentication
- limit the IP addresses that are allowed to connect to your machine

Ok, I don't think my router is port forwarding, unless it does that out of the box.  I have a D-Link DI524.  Also as far as my wireless goes, it should be secure enough, I live in Peru, and in our little town (Pueblo) there aren't too many wireless devices running around.  I have 64 WEP enabled.  Oh, and I think I do have denyhosts installed because I had read that somewhere.  

If I disable ssh root, when I log in as my user (with admin priviledges) I will still be able to use root?  It only disables someone as root ssh-ing into that machine, which with Ubuntu is 'technically' very difficult anyway because there is not official root account.  

Also the other users I don't think are allowed to use ssh, or if they are how can I disable them?  I can always log with my account (I have an account on all boxes with admin rights) so in all technicality, I don't need nor want them to use ssh.  Nor would they have any desire, or need to use it.  Thanks for the help!

Shane

---

### Post by Bushwack on 2007-11-12
> **shane2peru said:**
> Ok, I don't think my router is port forwarding, unless it does that out of the box.  I have a D-Link DI524.  Also as far as my wireless goes, it should be secure enough, I live in Peru, and in our little town (Pueblo) there aren't too many wireless devices running around.  I have 64 WEP enabled.  Oh, and I think I do have denyhosts installed because I had read that somewhere.

If you haven't explicitly enabled port forwarding then your router won't be forwarding the port.  I would suggest using WAP for your wireless if all your devices support it as I WEP is trivial to break now, but if there's no one around with the tools to access your network then you'll be safe.

> **shane2peru said:**
> If I disable ssh root, when I log in as my user (with admin priviledges) I will still be able to use root?  It only disables someone as root ssh-ing into that machine, which with Ubuntu is 'technically' very difficult anyway because there is not official root account.

Correct, you'll still be able to use sudo after connecting.  All you're really doing is forcing the hacker to guess both a valid username and a password instead of using the known username "root".  Of course if root logins are disabled system wide (the ubuntu default) I guess this step isn't really needed.

> **shane2peru said:**
> Also the other users I don't think are allowed to use ssh, or if they are how can I disable them?  I can always log with my account (I have an account on all boxes with admin rights) so in all technicality, I don't need nor want them to use ssh.  Nor would they have any desire, or need to use it.  Thanks for the help!

Setting the "AllowUsers" setting in /etc/ssh/sshd_config will disabled the accounts you don't want to access the machine from using ssh.  Run "man sshd_config" for more information.

---

### Post by shane2peru on 2007-11-17
> **Bushwack said:**
> If you haven't explicitly enabled port forwarding then your router won't be forwarding the port.  I would suggest using WAP for your wireless if all your devices support it as I WEP is trivial to break now, but if there's no one around with the tools to access your network then you'll be safe.



Correct, you'll still be able to use sudo after connecting.  All you're really doing is forcing the hacker to guess both a valid username and a password instead of using the known username "root".  Of course if root logins are disabled system wide (the ubuntu default) I guess this step isn't really needed.



Setting the "AllowUsers" setting in /etc/ssh/sshd_config will disabled the accounts you don't want to access the machine from using ssh.  Run "man sshd_config" for more information.


Great! Sounds like my default Ubuntu setup out of the box is rather a safe setup.  Of course there is always a little extra I can do, but over all I'm impressed.  Thanks for the info.

Shane

---

