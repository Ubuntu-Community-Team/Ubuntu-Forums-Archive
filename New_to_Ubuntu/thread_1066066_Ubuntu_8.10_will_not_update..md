---
title: "Ubuntu 8.10 will not update."
date: 2009-02-10
forum: New to Ubuntu
---

### Post by prometheus1981 on 2009-02-10
Hello,
I have installed Ubuntu 8.10 into a 2GB flash drive, and I was able to get it running. I was able to install the wireless drivers and get the wireless to work fine. When I tried to run the update with the wireless connection, it downloaded fine, but during the time it was installing, I acted like a noob and ran Firefox to surf the web and this caused the update installer to mess up until it crashed. Now, Ubuntu runs fine, but when I try to run the update manager and I tell it to install the updates It shows a message where it states that I need to run a command to fix the issue. I have ran the command, rebooted and ran the command, ran the command again and rebooted, but the message still comes up. What can I do to resolve this. I have tried to delete the downloaded installer packages thinking that they are corrupt, but it can't because it's blocked. I'm an Ubuntu noob in desperate need of help. Please help me! ](*,)

---

### Post by taurus on 2009-02-10
What is the message?  2GB may not be enough space to update/upgrade anything.

How does your disk space look?

```
df -h
```

---

### Post by markusf21 on 2009-02-10
did you try putting sudo in front of the command?

---

### Post by prometheus1981 on 2009-02-10
> **taurus said:**
> What is the message?  2GB may not be enough space to update/upgrade anything.

How does your disk space look?

```
df -h
```

My flash drive still has 1gb lest of storage.

---

### Post by prometheus1981 on 2009-02-10
> **markusf21 said:**
> did you try putting sudo in front of the command?

I did, but it only came back with a temp file directory where I found the corrupt files (appears that's where the downloaded segments are), unfortunately it does not let me delete them so that it can recreate them.

---

### Post by prometheus1981 on 2009-02-10
> **prometheus1981 said:**
> My flash drive still has 1gb lest of storage.

Sorry, I meant "left". I still have 1Gb left.

---

### Post by Bloch on 2009-02-10
Was all your software installed using the Applications Add/Remove package manager?
Or did you download some .deb files and install them?

If the latter case you can get warning messages that look scary, but are only relevant to that software. For example I get warning messages of conflicts for the Cinelerra movie editing software I installed. It probably doesn't work any more - I haven't used it or bothered to uninstall it.

> It shows a message where it states that I need to run a command to fix the issue. 

What is the exact message you are getting, and what is the command?

---

### Post by taurus on 2009-02-10
If you want to clear out the cache, just run

```
sudo apt-get clean
```

---

### Post by prometheus1981 on 2009-02-10
Well I don't know what the hell happened, but I can swear I saw 1Gb free yesterday, and now it's gone. Today it's showing that I have 10.8Mb of free space, this might be why it was giving me that error.

I'm going to format this flash drive and try a fresh install :icon_frown:.

---

### Post by modmadmike on 2009-02-19
> **prometheus1981 said:**
> Well I don't know what the hell happened, but I can swear I saw 1Gb free yesterday, and now it's gone. Today it's showing that I have 10.8Mb of free space, this might be why it was giving me that error.

I'm going to format this flash drive and try a fresh install :icon_frown:.

mount /tmp to ram, it can be cumbersome with some flash drive installs because it can fill up and not clean it's self for some people and also most computers have an abundance of ram so using it for tmp is generally an ok thing to try (and most temps don't fill past 90mb when they are properly cleared)
add this line to your /etc/fstab (run sudo gedit /etc/fstb)
```
none /tmp tmpfs defaults              1       2
```

---

