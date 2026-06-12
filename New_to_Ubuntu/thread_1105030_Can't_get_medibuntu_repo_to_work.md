---
title: "Can't get medibuntu repo to work"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by simiot on 2009-03-24
I just reinstalled Ubuntu Intrepid 64bit (kept settings) & I had to add the medibuntu repository again. I use the command line to add this, & the key but, I got this error:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
username~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

I tried to find software, which I know is there with medibuntu in synaptic but nothing was there. Anyone got any ideas how to fix this?

Thanks in advance :-)

---

### Post by blazemore on 2009-03-24
```
apt-get update
```
needs to be run as root, which you do by typing
```
sudo apt-get update
```

However, to authenticate, you'll need to install one package:
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

This information is from [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Hospadar on 2009-03-24
well first off, you need to "sudo apt-get update"
If ever you get messages about the package manager not being able to get a lock, it's either because another package manager is running, or you arn't root.  Sometimes if a package manager crashes it won't release the lock properly, but a restart will solve this.

Are you sure you added the GPG key for medibuntu?```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```If that doesn't work, please post a copy (inside "[code]" "[code\]" blocks) of your /etc/apt/sources.list

---

### Post by blazemore on 2009-03-24
I win

---

### Post by simiot on 2009-03-24
I dunno what to do. I have tried most things more than once.

Did you want me to paste what's in sources.list.save ?

I have added this repository before a few times. But, after this new install it won't work. I think maybe I will have to clean install ubuntu again.

---

### Post by drs305 on 2009-03-24
If you are still getting the key error, try running this to import the key:
```

gpg --keyserver keyserver.ubuntu.com --recv 2EBC26B60C5A2783
gpg --export --armor 2EBC26B60C5A2783 | sudo apt-key add -
sudo apt-get update

```

---

### Post by simiot on 2009-03-25
I ended up reinstalling Ubuntu Intrepid 64. I had problems with Win 7 which I was dual booting so, I started from scratch. So, it worked out well for me to do it this way.

I believe I found the problem. Medibuntu was actually installed but, the software 'Skype', which I used to search in synaptic to test the repo, wasn't listing. It was weird because I found it on the Medibuntu site today & installed it with the package manager. I had, in the past, been able to bring skype up in synaptic & install it. I came to the conlusion that I had ticked 'proposed software' in software sources which may have brought Skype up in the past because, Skype doesn't list a version for Intrepid 64. So, I think it may be in beta. Anyway, I apologise that this newbie picked your brains for no good reason.

Thanks for your input

---

### Post by egalvan on 2009-03-25
> **simiot said:**
> Anyway, I apologize that this newbie **picked your brains for no good reason.**

Thanks for your input

Picking brains is always a good endeavor.
The picker learns something,
and the pickee keeps his  brain sharp :)

---

