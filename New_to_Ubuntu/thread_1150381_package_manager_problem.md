---
title: "package manager problem"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by 2roombas on 2009-05-06
I just went to the Synaptic Package  Manager, hit reload and up came this error. What does this mean?

[INDENT]W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220[/INDENT]

---

### Post by Zoowey on 2009-05-06
> **2roombas said:**
> I just went to the Synaptic Package  Manager, hit reload and up came this error. What does this mean?

[INDENT]W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220[/INDENT]

Simply run this command in a terminal.

gpg --keyserver keyserver.ubuntu.com --recv-keys 6AF0E1940624A220 && gpg --armor --export 6AF0E1940624A220|sudo apt-key add -

All it is, is to verify that that's the actual repository. Every repository has its own key so you don't use a fake one. Basicly it's for security purposes.

---

### Post by Zeedok on 2009-05-06
[Here's a video]("http://www.youtube.com/watch?v=UUZOQsNo_ws") which runs you through the whole process so you'll know for next time.

The video shows a more GUI friendly method.

---

### Post by 2roombas on 2009-05-06
Having captions on that video would be helpful... I'm deaf.  Is there a "text" explanation of this anywhere?

---

### Post by 2roombas on 2009-05-06
> **Zoowey said:**
> Simply run this command in a terminal.

gpg --keyserver keyserver.ubuntu.com --recv-keys 6AF0E1940624A220 && gpg --armor --export 6AF0E1940624A220|sudo apt-key add -

All it is, is to verify that that's the actual repository. Every repository has its own key so you don't use a fake one. Basicly it's for security purposes.

thank you, that worked!

---

