---
title: "Compiz repositories not loading"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by SandyM on 2009-04-30
I wanted to to have latest version of compiz, but there seem to be some problem with Ubuntu Compiz repositories as they are showing error messages like following

[B]W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2ED6BB6042C24D89
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2ED6BB6042C24D89[/B]

I have added the following compiz repositories:-

[B]deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) jaunty main 
#deb-src [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) jaunty main [/B]

I think there are some problems relating to public key which I don't have, please help

---

### Post by abhiroopb on 2009-04-30
in a terminal type in the following (one after another...)

```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2ED6BB6042C24D89
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2ED6BB6042C24D89
sudo apt-get update && sudo apt-get upgrade

```

Cool?

---

### Post by Cincinnatux on 2009-10-09
Many thanks for this bit of CLI assistance.  I wasn't having problems with Compiz, but I am having a bit of a pain with Linux Mint x64 7, and your suggestion has helped tremendously.  Thanks for taking the time to share knowledge.:guitar:

---

### Post by ronenp on 2009-10-31
hi,

i've tried to paste the specified commands in terminal, but nothing id happning.

pls, help

---

### Post by ronenp on 2009-10-31
sorry. it worked !! tnx

---

