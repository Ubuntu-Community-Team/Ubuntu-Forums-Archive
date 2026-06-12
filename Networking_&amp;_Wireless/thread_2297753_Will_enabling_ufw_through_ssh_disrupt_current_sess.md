---
title: "Will enabling ufw through ssh disrupt current session?"
date: 2015-10-06
forum: Networking &amp; Wireless
---

### Post by somebody3 on 2015-10-06
I have an ubuntu server that I access through SSH. I've changed  standart port (22) to something else. I want to enable ufw on this  machine. However, I'm afraid of the possibility of the following  scenario occuring: as soon as I enable ufw, it'll start with default  settings blocking connections and kicks me from server, especially since  I'm connecting through non-standart port. Will that happen? Should I  prepare some configuration first or start ufw right away? SSH is the  only way of accessing my server, so loosig this due to firewall would be  a disaster.


  I also have some applications using some ports for UDP and TCP  connections. Will these ports be automatically blocked after I enable  ufw? Will I need to add exceptions for them after enabling it?

I haven't enabled ufw yet, but this is what I did so far: First I did ```
sudo ufw ssh
``` Second ```
sudo ufw  my_new_ssh_port_here
```

Then I had a look at /lib/ufw/user.rules

This is part of the file:

```
### RULES ###

### tuple ### allow any 22 0.0.0.0/0 any 0.0.0.0/0 in
-A ufw-user-input -p tcp --dport 22 -j ACCEPT
-A ufw-user-input -p udp --dport 22 -j ACCEPT

### tuple ### allow any 1111 0.0.0.0/0 any 0.0.0.0/0 in
-A ufw-user-input -p tcp --dport 1111 -j ACCEPT
-A ufw-user-input -p udp --dport 1111 -j ACCEPT

### END RULES ###

```
Have I already set it up to allow ssh connection through my new port  successfully? Is it safe to start now or do I need to configure anything  else?


  I'm still not sure, because ```
sudo ufw show raw
``` doesn't seem to show anything helpful and ```
sudo ufw status verbose
``` still shows Status: inactive only

---

### Post by Habitual on 2015-10-06
It's inactive because you have to 
```
sudo ufw enable
```

See also [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by somebody3 on 2015-10-06
I am aware that it is inactive, I'm not going to activate it until I make sure that I won't lose access to my server if I do so. But the problems is that it won't show me information needed while being inactive. So I'm stuck at this point. I'm asking whether I already did enough to prevent it from blocking ssh access and if anything else is needed to be configured.

---

### Post by Lars Noodén on 2015-10-06
It *should* work but if you want to be extra safe, you can use [at](http://manpages.ubuntu.com/manpages/trusty/en/man1/at.1.html) to disable UFW at a future time.  

For example,

```

$ sudo at now +3 minutes
warning: commands will be executed using /bin/sh
at> ufw disable
at> <EOT>
job 1 at Tue Oct  6 16:30:00 2015
$ sudo ufw enable

```

Give at a try a few times with something else first to get the hang of it.

---

### Post by somebody3 on 2015-10-06
> **Lars Noodén said:**
> It *should* work but if you want to be extra safe, you can use [at]("http://manpages.ubuntu.com/manpages/trusty/en/man1/at.1.html") to disable UFW at a future time...  


Thanks, this was very helpful! That command is perfect for test like this. I've enabled ufw, everything seems to be okay so far.

Do I need to reboot my server after enabling it? This particular message brought this question: > Firewall is active and enabled on system startup

Also, do I need to apply any additional "deny" rules, or judjing by the the following configuration only traffic (incoming and outgoing) that is allowed is from these two ports:

```
To                         Action      From
--                         ------      ----
22                         ALLOW IN    Anywhere
1111                       ALLOW IN    Anywhere
22 (v6)                    ALLOW IN    Anywhere (v6)
1111 (v6)                  ALLOW IN    Anywhere (v6)


```

---

### Post by Lars Noodén on 2015-10-07
You don't need to reboot your server after such a change.  The changes take effect immediately.  That line is just so that you know that the changes will be there even after reboot.  

At the top of your *sudo ufw status verbose* output you'll see the defaults: deny (incoming), allow (outgoing), disabled (routed)
The rules are in [chains](http://rlworkman.net/howtos/iptables/iptables-tutorial.html#TRAVERSINGOFTABLES) and the order matters.  With UFW it is harder to get the rules in the right order, unless you clear them and start over and then add everything in the right order in one go.
By default UFW blocks incoming connections and allows outgoing.  I wouldn't try tightening down the outgoing ones.  That'll be much harder and greatly increases the risk of getting locked out.  

If you want to see the details of your settings, then try

```

sudo iptables-save | less

```

It'll be rather long though and you'll have to hunt for the rules you added to their boilerplate.  Your rules will be in the chains "ufw-user-input" and "ufw-user-output"

---

