---
title: "Problem trying to install moblock (blockcontrol)"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by &#999;&#978;&#625;&#595;&#9786;l on 2009-09-20
The steps I have done;

Add @ terminal
gpg --keyserver keyserver.ubuntu.com --recv 9C0042C8
gpg --export --armor 9C0042C8 | sudo apt-key add -

Add @ /etc/apt/sources.list

[FONT=Verdana]deb [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) jaunty main
deb [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty main universe

@ terminal
[/FONT]sudo aptitude update
sudo apt-get install blockcontrol mobloquer

results?
```
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 620396F19C0042C8

```-- I also tried sudo apt-get update
```

sudo apt-get install blockcontroller mobloquer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package blockcontroller

```I also tried aptitude install, and package manager, but the key is the problem.

Thanks in advance for troubleshooting. :]

---

### Post by jre on 2009-09-20
Please try again the key adding part ```
gpg --keyserver keyserver.ubuntu.com --recv 9C0042C8
gpg --export --armor 9C0042C8 | sudo apt-key add -
```. I just tried here and it failed because of an timeout. So you have to check the output to see if it succeeds! You may do this alternatively with
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 9C0042C8
```

> **&#999 said:**
> E: Couldn't find package blockcontrol**ler**
I guess that´s just a typo of yours!? If not, that´s really strange. (The packages are called moblock, mobloquer and blockcontrol).

---

### Post by &#999;&#978;&#625;&#595;&#9786;l on 2009-09-21
Thanks. Solved. :]

---

### Post by Dr Mac 24 on 2009-11-24
I have a similar problem, Symaptic returning error containing "NO_PUBKEY 620396F19C0042C8" after Reload.

Solved when running:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 9C0042C8

In terminal. 

Thanks.

> **jre said:**
> Please try again the key adding part ```
gpg --keyserver keyserver.ubuntu.com --recv 9C0042C8
gpg --export --armor 9C0042C8 | sudo apt-key add -
```. I just tried here and it failed because of an timeout. So you have to check the output to see if it succeeds! You may do this alternatively with
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 9C0042C8
```


I guess that´s just a typo of yours!? If not, that´s really strange. (The packages are called moblock, mobloquer and blockcontrol).

---

