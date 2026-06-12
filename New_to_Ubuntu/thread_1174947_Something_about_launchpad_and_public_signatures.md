---
title: "Something about launchpad and public signatures?"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by AgentWiggles on 2009-05-31
I'm getting this message in my terminal when i run sudo apt-get update:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5
W: You may want to run apt-get update to correct these problems

This just started happening after I added the sources for AWN to my sources.list.

Sources were gotten from this thread: [http://ubuntuforums.org/showthread.php?t=1146366](http://ubuntuforums.org/showthread.php?t=1146366)

What do I do to fix it?

---

### Post by nandemonai on 2009-05-31
You need to install the public key.

[https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories](https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories)

---

### Post by Tibuda on 2009-05-31
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 7D2C7A23BF810CD5
```would fix it

[s]We need a easier way to do it.[/s]

---

### Post by steeleyuk on 2009-05-31
> We need a easier way to do it.

Not really.

The PPAs are completely unsupported and should only be added if you know what you're doing. Adding a GPG key isn't that difficult now as long as you follow instructions.

---

### Post by Tibuda on 2009-05-31
> **steeleyuk said:**
> Not really.

The PPAs are completely unsupported and should only be added if you know what you're doing. Adding a GPG key isn't that difficult now as long as you follow instructions.

Yeah, you are right. It would be a pain for Canonical to support every PPA in launchpad.

---

