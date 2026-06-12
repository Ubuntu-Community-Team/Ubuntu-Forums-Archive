---
title: "remote desktop not working after 7.04 -&gt; 7.10 upgrade"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by rocket777 on 2007-10-20
I have remote desktop enabled, and was using it just before the upgrade, on port 5900. 

After upgrade, it will not connect. 

I ran the 7.10 upgrade on my 7.04 system. All appeared to work, and it boots up fine.

I ran netstat -an to see if it is listening on port 5900 and it says it is. My ssh connects to port 22 also don't work.
I rebooted the original 7.04 system from a cloned disk, and it works there, so it's not hardware - so I don't know why it's not working. 

The control panel for remote desktop is ok. 

I think I saw something about removing vnc-something at the beginning of the upgrade, but not sure. I'm trying to connect from my windows xp system, and I have both vnc and ultra vnc clients, neither of which will connect to 7.10, but do to 7.04. I can't connect to sshd with a putty client either, and that too was working before the upgrade.

Also, I can ping it, and it can get out on the internet just fine. It's just these 2 servers that are not working as far as I can tell.

---

### Post by jfrorie on 2007-10-26
> **rocket777 said:**
> I have remote desktop enabled, and was using it just before the upgrade, on port 5900. 

After upgrade, it will not connect. 

I ran the 7.10 upgrade on my 7.04 system. All appeared to work, and it boots up fine.

I ran netstat -an to see if it is listening on port 5900 and it says it is. My ssh connects to port 22 also don't work.
I rebooted the original 7.04 system from a cloned disk, and it works there, so it's not hardware - so I don't know why it's not working. 

The control panel for remote desktop is ok. 

I think I saw something about removing vnc-something at the beginning of the upgrade, but not sure. I'm trying to connect from my windows xp system, and I have both vnc and ultra vnc clients, neither of which will connect to 7.10, but do to 7.04. I can't connect to sshd with a putty client either, and that too was working before the upgrade.

Also, I can ping it, and it can get out on the internet just fine. It's just these 2 servers that are not working as far as I can tell.


try removing the package and reinstalling it.

---

