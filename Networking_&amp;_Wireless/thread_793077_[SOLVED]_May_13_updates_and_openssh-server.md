---
title: "[SOLVED] May 13 updates and openssh-server"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by jetsam on 2008-05-13
I just ran into a problem with today's updates and openssh-server.  I got this error message when doing the upgrade on Ubuntu Gutsy 7.10.

> E: /var/cache/apt/archives/openssh-server_1%3a4.6p1-5ubuntu0.3_i386.deb: subprocess pre-installation script returned error exit status 255

I don't know if anyone else is getting this as well, but the following seemed to work for me to revert the upgrade and make ssh install cleanly:

```
sudo apt-get install openssh-client=1:4.6p1-5ubuntu0.2
```
and then:
```
sudo apt-get install openssh-server=1:4.6p1-5ubuntu0.2
```

**Please note**:  The above commands are for **Gutsy 7.10 only**, and will need to be modified with different package versions for different Ubuntu versions.

I needed to revert openssh-client as well, or openssh-server wouldn't install.  

I'm pretty sure this situation will be changing soon if it's widespread, but I thought this might help in the meantime.

**Added:** Reverting may not be necessary.  I just retried the update, and it doesn't actually break openssh-server-- it just looks like it does because of the error message.  The package also gets flagged as broken in Synaptic.  Having a broken package in Synaptic seems to break update manager, too.

---

### Post by herda05 on 2008-05-13
Thanks for the info Jetsam. I simply clicked update and suddenly broke my ssh, then used this to get it back up.

---

### Post by jetsam on 2008-05-13
The problem has been fixed by new updates.  I needed to hit the "Check" button in update manager to get the latest (...ubuntu0.4 version number).

With the new update, I did run into trouble connecting after the new update generated new keys.  If you're using password authentication, on the client system, renaming ~/.ssh/known_hosts will cause it to be regenerated the next time it's needed and allow new key generation and reconnection.

---

