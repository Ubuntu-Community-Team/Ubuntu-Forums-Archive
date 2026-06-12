---
title: "Software and its dependencies."
date: 2011-01-22
forum: New to Ubuntu
---

### Post by LinuxFox on 2011-01-22
I use to use Banshee as a music player on Ubuntu 8.04, and I'm thinking about installing it again.  I know how to install software and use Synaptic, but I'm looking at the properties (by right-clicking and choosing properties).

Under the Dependencies tab, there's a list of dependencies.  What's new to me are the words "depends", "suggests", and "recommends".

I'm thinking about installing Banshee again, but does this means that some dependencies are optional (or I'm getting that impression)?  If it is, is it possible to install software with the optional items disabled?

Please answer and thanks.

---

### Post by Smart Viking on 2011-01-22
Yes that is correct.
To install only what you actually need:
```
sudo apt-get install --no-install-recommends banshee
```
But in the case of installing banshee, it won't make much difference.

---

### Post by JKyleOKC on 2011-01-22
The "depends" entries are mandatory. The others are optional, but may improve performance.

If you install via Synaptic, the dependencies are normally taken care of automatically. That is, they are downloaded if you do not already have them on your system, with no need for any additional action on your part. The listing that you are seeing is mostly for information so that you have an opportunity to decide whether you want to install the package. When you mark the package to be installed, you'll get a dialog about any additional packages that would be needed, and again when you click "apply" you have a final opportunity to see what will happen.

---

### Post by LinuxFox on 2011-01-22
> **Smart Viking said:**
> Yes that is correct.
To install only what you actually need:
```
sudo apt-get install --no-install-recommends banshee
```
But in the case of installing banshee, it won't make much difference.Ok I see what you mean, can that work with the "suggests" too?

@JKyleOKC, thanks for explaining it more.  This is actually nice, being able to see what gets installed to my system before I install it.

Edit: I tried the command above and it installed banshee without the recommended or suggested packages.  Thanks a lot for your help guys. 8)

---

