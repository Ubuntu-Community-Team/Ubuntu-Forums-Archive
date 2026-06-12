---
title: "Karmic Sound problems on HP mini, can't access keyserver"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by DavidShor on 2009-11-06
I'm running Ubuntu Karmic 9.10 on an hp mini 1000 and am unable to get sound to work at all(Not even with headphones). I tried to go through the guide at [http://www.codealpha.net/193/jaunty-getting-the-sound-working-on-the-hp-mini-1000-or-1120nr/comment-page-1/#comment-102](http://www.codealpha.net/193/jaunty-getting-the-sound-working-on-the-hp-mini-1000-or-1120nr/comment-page-1/#comment-102) , which tells me to load 
deb [http://ppa.launchpad.net/minichoco-team/ppa/ubuntu](http://ppa.launchpad.net/minichoco-team/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/minichoco-team/ppa/ubuntu](http://ppa.launchpad.net/minichoco-team/ppa/ubuntu) jaunty main

as repositories and update my alsa drivers. But when I run apt-update, I get

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0B47F0A6B88A1AA8

I looked around and it was reccomended to run: 

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 9220067F

But when I do that, I get 

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 9220067F
gpg: requesting key 9220067F from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

The internet is working(I'm posting on it), and I can ping keyserver.ubuntu.com without problem( ping of around 125 and packet loss of 8%)

I originally installed UNR Netbook remix edition 9.02, and sound was working. The problem occurred after the upgrade.

What should I do to fix things?

[On another note, I occasionally get a "black screen of death" while running processes, help on that would be appreciated too[

---

