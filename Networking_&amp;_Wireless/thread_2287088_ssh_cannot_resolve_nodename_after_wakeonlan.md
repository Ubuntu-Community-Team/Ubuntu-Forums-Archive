---
title: "ssh cannot resolve nodename after wakeonlan"
date: 2015-07-16
forum: Networking &amp; Wireless
---

### Post by johnny34 on 2015-07-16
Previously, I issued a wakeonlan command to my sleeping debian (wheezy
stable) server from (a mac) within my home network and then ssh in no
problem. Worked like a charm. I could put it to sleep again and wake it
up etc. Perfecto. 

However, for some reason (I must have done something stupid) I can now
only ssh in once the server is rebooted (by physically switching it off
then on again). If I put it to sleep then wake it, it does wake up---
however, ssh cannot then resolve the hostname (unless I physically reboot):
```

ssh -vX johnny[EMAIL="bob@cerberus.local"]@cerberus.local[/EMAIL]
OpenSSH_6.2p2, OSSLShim 0.9.8r 8 Dec 2011
debug1: Reading configuration data /Users/johnny/.ssh/config
debug1: Reading configuration data /etc/ssh_config
debug1: /etc/ssh_config line 20: Applying options for *
debug1: /etc/ssh_config line 102: Applying options for *
ssh: Could not resolve hostname cerberus.local: nodename nor servname
provided, or not known

```

Any help warmly received! [IMG]http://forums.debian.net/images/smilies/icon_smile.gif[/IMG]

Johnny

---

### Post by papibe on 2015-07-16
Hi johnny34. Welcome to the forum ):P

You are using the avahi zeroconf protocol to resolve the address. That is a broadcasting method. In other words, a machine "shouts" its own IP to everybody in the network. Unfortunately, this works only if the machine is up and running.

'cerberus.local' is not resolve because it hasn't been broadcast yet.

I would focus in the fact that the machine is not waking up as before:
What command did you use?
Are you using its MAC address, right?
Did you take a look at [this]("https://help.ubuntu.com/community/WakeOnLan") tutorial?
What is the output of this command on the Debian machie?
```
sudo ethtool eth0
```

Regards.

---

### Post by johnny34 on 2015-07-21
Thanks for your prompt response. I took the machine out of its spot under the stairs, plugged it into a monitor, and found that... it just worked. I then took it back downstairs and now, what do you know:... it works again. I can sleep, wake, ssh, sleep, wake, ssh to my heart's content and switch seamlessly between tmux/vim sessions running on mac and linux. Really not sure why it wasn't working before. I used wakeonlan just like before. How terribly embarrassing! Maybe your moderator aura magically made it better. :oops: Maybe it just wanted some attention after living under the stairs for so long. In any case, cheers!

---

