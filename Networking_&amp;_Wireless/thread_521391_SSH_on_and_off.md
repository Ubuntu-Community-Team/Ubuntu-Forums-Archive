---
title: "SSH on and off"
date: 2007-08-09
forum: Networking &amp; Wireless
---

### Post by petit.padavoine on 2007-08-09
As the title suggests, ssh works on and off...

 have two Ubuntu machines, one laptop and one desktop. Both have an ssh client and an ssh server

From time to time, everything works, and both machines can ssh into each other.

However, sometimes, I can only ssh from the desktop into the laptop and not from the laptop into the desktop.

This happens randomly, the settings are left untouched, so I have no idea what's causing it.

I doubt that the desktop's ssh server is at fault because even when I can't ssh from the laptop to the desktop, I CAN ssh from my PSP to the desktop (there's an ssh client on the PSP).

How can I fix that?

---

### Post by petit.padavoine on 2007-08-09
I forgot to specify what happens when SSH doesn't work.

If from the laptop I run ssh <user>@<desktopname>, it just hangs, and doesn't return any error message.

On the desktop /var/log/auth.log doesn't show anything, it's totally oblivious to the laptop's attempt.

---

### Post by dreadlord_chris on 2007-08-09
This sounds like a networking issue
How is your network set up?

---

### Post by petit.padavoine on 2007-08-09
I really doubt it's a networking issue. I always have a connection to the net from both machines and I can always ping the other machine, even if I can't ssh to it.

Anyway the setup is the following:

```


Laptop  -- Wifi -- Router -- USB -- Desktop
                     |
                     |
                 Internet


```

---

### Post by petit.padavoine on 2007-08-09
UPDATE!

Something else of interest, it may be related to the problem.

I just noticed that NFS and rsync are also on and off.

It's exactly the same problem as with ssh.

So basically most of the time everything works in either direction.

Sometimes, nothing works from the laptop to the desktop. Can't rsync, can't nfs, can't ssh. It's always all three at the same time...

---

### Post by petit.padavoine on 2007-08-09
Another UPDATE!

I let the nfs mount command and ssh command hang very long and finally they returned an error message.

NFS:
```
mount to NFS server '<desktopcomputername>' failed: server is down.
```

Note: I DID try restarting the NFS server on the desktop, but to no avail...

SSH:
```
ssh: connect to host <desktopcomputername> port 22: Connection timed out
```

---

### Post by dreadlord_chris on 2007-08-09
There being nothing in the desktop's logs indicates no connection attempts received. This, along with NSF & rsync also failing on the laptop, tells me there's a network problem - *probably* on the laptop.
You say you can ping the desktop - have you tried pinging it _at the same time_ that an ssh connection is hanging? How about pinging the laptop from the desktop during a hang?
Are you using DHCP on either the laptop or the desktop?

---

### Post by petit.padavoine on 2007-08-09
Both use DHCP to connect to the router.
Pinging during a hang worked perfectly (in both directions).

---

### Post by petit.padavoine on 2007-08-09
Bump.

---

### Post by dreadlord_chris on 2007-08-09
Since you only have 2 computers to deal with I would recommend setting static IPs for both.
are you pinging by hostname or by IP?

---

### Post by petit.padavoine on 2007-08-10
They have static IPs already.
I tried pinging both by hostname AND by IP. Both worked.
I REALLY doubt it's a networking issue...

---

### Post by dreadlord_chris on 2007-08-10
> **petit.padavoine said:**
> They have static IPs already.
I tried pinging both by hostname AND by IP. Both worked.
I REALLY doubt it's a networking issue...

You said they both use DHCP to connect to the router...
now, which is it?

---

### Post by petit.padavoine on 2007-08-11
Yeah sorry, not clear.
By saying static IPs I meant that they always get the same IPs, but they DO use DHCP to connect to the router.
Anyway, the problem is not networking.
I can always ping.
I can always connect to the net.

---

### Post by dreadlord_chris on 2007-08-12
> **petit.padavoine said:**
> Yeah sorry, not clear.
By saying static IPs I meant that they always get the same IPs, but they DO use DHCP to connect to the router.
Anyway, the problem is not networking.
I can always ping.
I can always connect to the net.
hmm... ok, let's clear up a few points then...
when I say "static IP" I'm using the *standard* definition:
[http://en.wikipedia.org/wiki/Static_IP#Static_and_dynamic_IP_addresses](http://en.wikipedia.org/wiki/Static_IP#Static_and_dynamic_IP_addresses)
an important distinction since our definitions are opposite...

the ability to ping & surf does not mean there are **no** network problems...

but you know it's not a network thing...

uh, I don't know then....

---

### Post by eentonig on 2007-08-12
did you configure a firewall or something?

How's cpu usage on the unresponsive machine when you can't connect?

---

