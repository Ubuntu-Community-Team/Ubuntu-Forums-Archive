---
title: "Cannot add PPA with firewall enabled"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by Ben Page on 2011-02-22
Hey

I cannot add any new "third party" PPAs with firewall enabled. Software firewall isn't even configured, I'm talking about hardware firewall on my router (Aolynk DR814). When I turn the firewall off, everything is working fine, is this normal? Can't aptitude map it's ports? Is there a specific port I can map myself?

It took me a while to figure this out, but it's still annoying to have to authorize to my router and turn the firewall off every time I want to add new PPA. It looks like it's not getting a response when requesting authorization keys.

Using Ubuntu 10.10, fully updated.

---

### Post by nick_goodfate on 2011-02-22
If your problem is with GPG keys, this may help:

[http://www.webupd8.org/2011/02/launchpad-getkeys-gets-proxy-support.html](http://www.webupd8.org/2011/02/launchpad-getkeys-gets-proxy-support.html)

---

### Post by Ben Page on 2011-02-22
> **nick_goodfate said:**
> If your problem is with GPG keys, this may help:

[http://www.webupd8.org/2011/02/launchpad-getkeys-gets-proxy-support.html](http://www.webupd8.org/2011/02/launchpad-getkeys-gets-proxy-support.html)

Close, but not close enough :(

As far as I understand launchpad-getkeys is only updating the missing keys, but can't get the new PPA with the key. This does work when I'm adding a repository from synaptic GUI and then run the update for the GPG keys trough the terminal additionally (I guess that's one way to avoid dropping the firewall). But I wanted a solution for this specifically:

```
AMDunix:~$ sudo add-apt-repository ppa:nilarimogard/webupd8
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 1DB29AFFF6C70907B57AA31F531EE72F4C9D234C
gpg: requesting key 4C9D234C from hkp server keyserver.ubuntu.com
[B]gpg: keyserver timed out
gpg: keyserver receive failed[/B]: keyserver error
```  

When I drop the firewall everything is working as it should, even if I turn the FW on again, the PPA has the key and can update w/o any errors.

---

### Post by komputes on 2011-02-22
This was discussed in a previous thread. Workarounds are available if you can't unblock port 11371 from your router (forwarding should not be necessary).

[http://ubuntuforums.org/showthread.php?t=1101366](http://ubuntuforums.org/showthread.php?t=1101366)

---

### Post by Ben Page on 2011-02-22
> **komputes said:**
> This was discussed in a previous thread. Workarounds are available if you can't unblock port 11371 from your router (forwarding should not be necessary).

[http://ubuntuforums.org/showthread.php?t=1101366](http://ubuntuforums.org/showthread.php?t=1101366)

That's what I was looking for - SOLVED \\:D/

---

