---
title: "Amarok"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by Dobbie03 on 2009-08-16
I am so slow at picking this whole terminal thing up, can someone please tell me how to update Amarok to version 2.1.1?

Cheers

---

### Post by gjoellee on 2009-08-16
I don't know if Amarok 2.1.1 is in Kubuntu's repo yet. You can update just by using your update manager, or with this those two commands.

First to check for changes in the repo:
```
sudo apt-get update
```

then to upgrade packages:

```
sudo apt-get upgrade
```

then you can make both commands into one (kind of) by adding "&&" like this:

```
sudo apt-get update && sudo apt-get upgrade
```

You can install Amarok 2.1.1 from source, but I am not sure if you want that since you're not so good a using the terminal yet.

---

### Post by Dobbie03 on 2009-08-16
I tried that and this is what I got:

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2ABD4DE1E855A72E
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  gwibber linux-generic linux-headers-generic linux-image-generic
  linux-restricted-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

---

### Post by Dobbie03 on 2009-08-16
Dont worry I got it.  Cheers.

---

