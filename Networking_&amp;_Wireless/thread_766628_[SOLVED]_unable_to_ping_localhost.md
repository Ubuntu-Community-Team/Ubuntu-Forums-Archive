---
title: "[SOLVED] unable to ping localhost"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by commonplace on 2008-04-25
I feel stupid for asking this, but I've tried everything I know and can't figure it out.

I can't ping 'localhost'.

My /etc/hosts file:

```
127.0.0.1 localhost ubun2

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```


My nsswitch.conf file:

```
passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      files
services:       files
ethers:         files
rpc:            files

netgroup:       nis

```


nslookup localhost:

```
Server:         192.168.1.254
Address:        192.168.1.254#53

Non-authoritative answer:
Name:   localhost
Address: 127.0.0.1

```


ping localhost:

```
ping: unknown host localhost
```


What am I missing? It's like it's totally ignoring my hosts file, but why? nsswitch lists 'files' as the first option for hosts, so it should hit my hosts file first, right? This just started this week and I don't remember changing a single thing (but I won't deny the possibility).

I first became aware of the problem when I tried to access the machine via NX and it connected and authenticated but then wouldn't finish loading, saying 'nxssh: localhost: Name or service not known'. I approached it as a problem with NX until I noticed that I couldn't even ping localhost on that machine.

So, what's wrong? :-)

/Kevin

---

### Post by csat on 2008-04-25
> **commonplace said:**
> I feel stupid for asking this, but I've tried everything I know and can't figure it out.

I can't ping 'localhost'.

My /etc/hosts file:

```
127.0.0.1 localhost ubun2

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

/Kevin

I have this one and I can ping.  Using Hardy Heron 8.04.

127.0.0.1	localhost
127.0.1.1	ubu804dt

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by commonplace on 2008-04-25
Okay, I made that change and it didn't help.

One interesting thing: if I do "sudo ping localhost", it works. Pinging localhost without sudo does not. So it seems to be a permissions thing... what would cause sudo to access the hosts file but not work otherwise? Do I need to chmod the hosts file or nsswitch.conf file? I did come across something that suggested doing a chmod 644 nsswitch.conf but a) I don't know if/why that's necessary and b) if it is necessary, why has it worked all along until now?

/Kevin

---

### Post by Monicker on 2008-04-25
> **commonplace said:**
> Okay, I made that change and it didn't help.

One interesting thing: if I do "sudo ping localhost", it works. Pinging localhost without sudo does not. So it seems to be a permissions thing... what would cause sudo to access the hosts file but not work otherwise? Do I need to chmod the hosts file or nsswitch.conf file? I did come across something that suggested doing a chmod 644 nsswitch.conf but a) I don't know if/why that's necessary and b) if it is necessary, why has it worked all along until now?

/Kevin

/Kevin

Very strange.  I did some searching around, because its an intriguing problem.  :)

Take a look at this thread:  [http://ubuntuforums.org/showthread.php?t=687637]("http://ubuntuforums.org/showthread.php?t=687637")

---

### Post by commonplace on 2008-04-25
> **Monicker said:**
> Very strange.  I did some searching around, because its an intriguing problem.  :)

Take a look at this thread:  [http://ubuntuforums.org/showthread.php?t=687637]("http://ubuntuforums.org/showthread.php?t=687637")

Yep, I'd seen that thread. That's what got me on the path of checking nsswitch.conf. Mine seems to be setup okay.

This thread ([http://ubuntuforums.org/showthread.php?t=666433]("http://ubuntuforums.org/showthread.php?t=666433")) is what talks about doing a chmod 644 on the nsswitch.conf file. And honestly, I have a feeling that will fix it, but it worries me that I'm not sure it's supposed to be that way.

Can anyone post the results of this for me?

```
stat -c "%a %n" /etc/nsswitch.conf
```

That should return the octal permissions for your nsswitch.conf file (e.g. 600 instead of -rw-------).

Mine is 600. The thread I referenced says to change it to 644. I'm curious to see if others have theirs as 644 or not before I change mine. Thank you everyone!

/Kevin

---

### Post by Monicker on 2008-04-25
Just checked that on Hardy Heron, which was freshly installed yesterday.


644 /etc/nsswitch.conf

---

### Post by commonplace on 2008-04-25
> **Monicker said:**
> Just checked that on Hardy Heron, which was freshly installed yesterday.


644 /etc/nsswitch.conf

Thank you so much! So apparently, 644 is the proper permission for that file. Mine was set to 600. I KNOW I didn't do that. I wonder if something I installed changed it 'for me' -- I recently installed Citadel. Makes me wonder.

At any rate, I changed mine to 644 (sudo chmod 644 nsswitch.conf) and that fixed my problem, both ping and NX. Thanks again for checking that for me!

/Kevin

---

### Post by TKBuisan on 2008-04-27
I had this same issue... and I recently installed Citadel.
TKBuisan

---

