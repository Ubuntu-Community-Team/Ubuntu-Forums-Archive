---
title: "Synaptic not refreshing?"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by CaptainMark on 2009-05-24
Whenever I try to update Synaptic package manager I get the following error message

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7

Does this mean Packages are not being refreshed, if so, what have I done wrong and how do I fix it?  If they are still being refreshed then how do I stop this error message from popping up?

I run the refresh in a terminal and get the same message

```
mark@mark-desktop:~$ sudo apt-get update
[sudo] password for mark: 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Translation-en_GB
Get: 1 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-security Release.gpg
Get: 2 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.7kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-security/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-security/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-security/universe Translation-en_GB
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-security/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-security Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-security/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-security/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-security/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-security/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-security/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-security/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-security/multiverse Sources
Fetched 308B in 0s (545B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7
W: You may want to run apt-get update to correct these problems
```Beginner talk would definatley help.
Thanks

---

### Post by 67GTA on 2009-05-24
The key it is complaining about is a security signature key for that repository. You need to import the key before apt/synaptic will use it. It is for security. Open a terminal and copy paste these commands one at a time.

```
gpg --keyserver keyserver.ubuntu.com --recv 4874D3686E80C6B7  

```

```
gpg --export --armor 4874D3686E80C6B7 | sudo apt-key add -
```

```
sudo apt-get update
```

More on the subject here: [https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

---

### Post by CaptainMark on 2009-05-24
Seems to work now just like it did before, I only got the problem after updating to 9.04
Problem Solved though,
Thanks

---

### Post by 67GTA on 2009-05-24
PPA repo keys aren't installed by default. You have to add them manually when you add a third party repo. When you upgraded, all but the default Ubuntu repo keys were overwritten.

---

