---
title: "[SOLVED] help with samba"
date: 2008-09-02
forum: Networking &amp; Wireless
---

### Post by porchrat on 2008-09-02
I am attempting to share from an ubuntu machine running 8.04 with multiple windows machines (some xp and one Vista). I thought I had setup my samba server properly on my ubuntu machine, however it seems that I haven't.  I'm sure I have missed some sort of comment in the samba config file.

I can see the ubuntu machine from vista and I can ping to its IP address, but not to the hostname.  I can't browse the shares from the Vista machine.  I haven't tried anything regarding accessing from the ubuntu side yet, but baby steps first.

---

### Post by dmizer on 2008-09-02
Do you have any firewalls in place either on the vista machine or on the ubuntu machine?

On the off chance ... are the usernames for vista and ubuntu the same?

---

### Post by porchrat on 2008-09-02
usernames and passwords for the vista and ubuntu machines are the same (I've been told that can make a difference)

I do indeed have a firewall up on the vista machine and I run firestarter on the ubunty machine, but there is no inbound policy set.  Do you recommend I deactivate the firewalls for the time being?

That isn't a permanent solution as these machines are work machines and can't be left exposed (not that I have much faith in these firewalls anyway).

Thank you for your response by the way

---

### Post by porchrat on 2008-09-02
I turned off firestarter and got a connection straight away!

Awesome...thank you

Now I just need to create policies to allow the machine through when the firewall is on and bingo it'll run.

Nice to know it was something simple.

---

