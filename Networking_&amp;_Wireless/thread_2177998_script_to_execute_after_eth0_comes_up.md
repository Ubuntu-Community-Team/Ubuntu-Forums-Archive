---
title: "script to execute after eth0 comes up"
date: 2013-10-01
forum: Networking &amp; Wireless
---

### Post by Jaxilian on 2013-10-01
Hi
I got a annoying problem.
**System:**
Ubuntu 12.04 x64 computers with Winbind/samba AD connectivity.

[B]
Problem:[/B]
Winbind cache needs to get cleared often.
I have tried to figure out how to execute a script after eth0 is up, but I am lost. I googled so my hands bleed.

I need to clear /var/cache/samba/*.tdb, but only when eth0 is up and before login. Otherwise laptop users cannot login in offline mode
I tried various scripts (with like if $IFACE then...) in /etc/network/if-up.d but they don't execute.

Anyone know how to fix it? or know a better way of solving this with the Winbind cache?

---

### Post by pqwoerituytrueiwoq on 2013-10-01
I have use a rather dirty way to do it, this is my entire script on one system
after the second while loop eth0 is up and working
```
echo 1 > /proc/sys/net/ipv4/ip_forward
while [ 0`pidof NetworkManager` -eq 0 ]; do
    sleep 1
done
while [ "`ifconfig eth1 | grep 'inet addr:'`" = "" ]; do
    sleep 2
done
while [ "`ifconfig eth1:1 | grep 'inet addr:'`" = "" ]; do
    sleep 2
    ifconfig eth1:1 10.0.0.1 netmask 255.255.0.0
done
#iptables -t nat -A PREROUTING -o eth1 -p tcp -m tcp --dport 80 -j DNAT --to-destination 10.0.0.75:80
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
iptables -P FORWARD ACCEPT
service dhcp3-server start
```

---

### Post by ian-weisser on 2013-10-01
One way is to use an upstart job:

/etc/init/my-upstart-job
```
description "Custom upstart event that does something"

start on net-device-up IFACE=eth0

script
    # Do your actions here
end script

```

---

### Post by Jaxilian on 2013-10-02
> **ian-weisser said:**
> One way is to use an upstart job:

/etc/init/my-upstart-job
```
description "Custom upstart event that does something"

start on net-device-up IFACE=eth0

script
    # Do your actions here
end script

```

I tried this, but it did not run my clean command. Maybe I did it wrong

---

### Post by Ilya80 on 2013-10-02
According to man page for /etc/network/interfaces [http://manpages.ubuntu.com/manpages/hardy/man5/interfaces.5.html](http://manpages.ubuntu.com/manpages/hardy/man5/interfaces.5.html) you can define what to do on after interface is brought up using "post-up command" .

---

### Post by Jaxilian on 2013-10-02
> **Ilya80 said:**
> According to man page for /etc/network/interfaces [http://manpages.ubuntu.com/manpages/hardy/man5/interfaces.5.html](http://manpages.ubuntu.com/manpages/hardy/man5/interfaces.5.html) you can define what to do on after interface is brought up using "post-up command" .

I tried that too, but there was no good way of separating it to only eth0 so I skipped that.

---

### Post by Ilya80 on 2013-10-02
What do you mean "separate it only to eth0"? I`m pretty sure the command in post-up will only be executed when eth0 is brought up.

Ilya.

---

### Post by Jaxilian on 2013-10-02
> **Ilya80 said:**
> What do you mean "separate it only to eth0"? I`m pretty sure the command in post-up will only be executed when eth0 is brought up.

Ilya.

Sorry if I confuse you. I mean once eth0 is active, then I want the script to delete tdb-files in /var/cache/samba
I tried post-up and it sorta of deleted the files even if eth0 was unplugged which made so that none could log in.

If the tdb-files is deleted before login and eth0 is active then when a user logs in, it creates new tdb-files

I guess until Ubuntu comes with a solid AD connectivity on its own, I am stuck with this solution.

---

### Post by ian-weisser on 2013-10-02
> **Jaxilian said:**
> I tried this, but it did not run my clean command. Maybe I did it wrong

Possibly. It has worked very well for me for years.

---

### Post by Jaxilian on 2013-10-03
> **ian-weisser said:**
> Possibly. It has worked very well for me for years.

OK I got it to work now, but with the effect that it runs the script whether a cable is plugged in or not. I only wished it for running the script when it feels that eth0 has a connection with anything.
I probably formulated my question wrong to you from the start.

---

### Post by ian-weisser on 2013-10-03
> **Jaxilian said:**
> it runs the script whether a cable is plugged in or not
If nothing is plugged in, then the interface is not up.

That implies that you have some other trigger criteria, or that eth0 is perhaps different that you expect, or you have a syntax error.

---

