---
title: "I dont understand how to get/use new download sources"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by originalsynthesis on 2009-01-16
I could just be a retard, but as much as i try and read about using new repositories in apt and synaptic, i cant get it to work unless someone lists the exact commands.  For example im trying to get packages from this site: 

[https://launchpad.net/~danmbox/+archive](https://launchpad.net/~danmbox/+archive)

He even lists the sources.list entry at the top of the page. I put the deb entry in my sources.list and saved, but i cant get apt or synaptic to show the packages. Do i need to add a key?  Could someone show me how to get this particular one to work and explain what needs to be done with others? Does there have to be a sources entry shown for a user to be able to download from a particular repository or can it be figured out? 

](*,)

---

### Post by taurus on 2009-01-16
Can you post your /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

Otherwise, edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and add these two lines to the end of it, assuming you are running hardy.

```

deb http://ppa.launchpad.net/danmbox/ubuntu hardy main
deb-src http://ppa.launchpad.net/danmbox/ubuntu hardy main

```
Save it and close gedit editing window.  Then, from a terminal, run

```
sudo apt-get update
```
Now, you can install whatever you want from that site either through a terminal or from synaptic.

---

### Post by iaculallad on 2009-01-16
You did the right thing by adding the source path on your sources.list file:

```
gksudo gedit /etc/apt/sources.list
```

and insert the lines of texts below on the end part of the file:

> deb [http://ppa.launchpad.net/danmbox/ubuntu](http://ppa.launchpad.net/danmbox/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/danmbox/ubuntu](http://ppa.launchpad.net/danmbox/ubuntu) hardy main


Save and Close. While on the terminal, issue the command below to initialize your new source:

```
sudo apt-get update && sudo apt-get upgrade
```

From that point, you could now install applications that are linked to the software source you had just added.
An example would be the qtractor app as listed on packages related to that source. (Don't quote me on this, I'm not sure with the application)

---

### Post by HotShotDJ on 2009-01-16
See also: [https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

---

### Post by blueridgedog on 2009-01-16
Perhaps you have a type on the way you entered it in System -> Adminstration -> Software Sources -> third party software.

The site you linked to listed:

deb [http://ppa.launchpad.net/danmbox/ubuntu](http://ppa.launchpad.net/danmbox/ubuntu) hardy main

as the soucce, so I would add:
Type:  Binary
URL: [http://ppa.launchpad.net/danmbox/ubuntu](http://ppa.launchpad.net/danmbox/ubuntu) 
Dist: Hardy main
Components: Free Non-Free Main

---

### Post by originalsynthesis on 2009-01-16
Well i decided not to waste a bunch of space, with my whole sources list, but here's what i did and a bunch of little questions: 

i had added the deb entry but not the deb-src entry to sources.list because i did not want to get source code packs, so i left it out. Do tell me if i should do otherwise,  though.

i did the get update and that seemed to work, so from now on i'll be doing that. (one tiny detail i completely forgot about!) 

now when you do 'get upgrade' will that always download all the new packages that are found when you add a repo? 

what does gksudo do that sudo doesn't?

```
sudo apt-get update && sudo apt-get upgrade
```
small detail: so the && is how you string two commands together in one line? does that work in every case?

and when are authentication keys needed? is that basically just a password so the admins of the source can control who downloads from them?

Sorry about all the questions, this post brought up a bunch of details i've been really curious about.   Thanks a lot ppl!

---

### Post by originalsynthesis on 2009-01-16
man, im really glad that worked, i was able to download a fix to a problem ive been posting about for days in multimedia. Jack can be so frustrating when its broken, i actually forgot to do the simple apt-get update command. gotta remember to keep my zen, y'know? thanks again!

---

### Post by snova on 2009-01-16
> **originalsynthesis said:**
> now when you do 'get upgrade' will that always download all the new packages that are found when you add a repo?

"upgrade" simply looks for newer versions of any packages you have on your system.

> what does gksudo do that sudo doesn't?

It is preferable to use gksudo over sudo when launching GUI programs. I'm not sure of the details, but basically if you use sudo certain file permissions get messed up- people have problems with fixing that all the time. :) (Search for ".dmrc")

> ```
sudo apt-get update && sudo apt-get upgrade
```
small detail: so the && is how you string two commands together in one line? does that work in every case?

Yep! **&&** runs the first command, and if it succeeds, runs the second command. You can string as many together as you want.

> and when are authentication keys needed? is that basically just a password so the admins of the source can control who downloads from them?

Certainly not! That goes against the whole point of open source software, is that it is freely redistributable.

I really don't know, but it probably has something to do with verifying the source of the packages, so you don't accidentally install something nasty...

> Sorry about all the questions, this post brought up a bunch of details i've been really curious about.   Thanks a lot ppl!

No problem. ;)

---

### Post by Paqman on 2009-01-16
> **blueridgedog said:**
> Perhaps you have a type on the way you entered it in System -> Adminstration -> Software Sources -> third party software.


Editing config files by hand is a pain, IMO. That's why we have nice clean GUI tools like Software Sources.

---

### Post by handydan918 on 2009-01-16
> and when are authentication keys needed? is that basically just a password so the admins of the source can control who downloads from them?

The keys are a security feature, placed there for the protection of the end user. Without them, it would be theoretically possible to do a "man-in-the-middle" attack and load rootkits on peoples rigs. 
no on is compiling a list of "enemies of the MicroSoft state". 

At least, no one in the FOSS world....:P

---

### Post by jerome1232 on 2009-01-16
> **originalsynthesis said:**
> 
and when are authentication keys needed? is that basically just a password so the admins of the source can control who downloads from them?


[http://wiki.debian.org/SecureApt](http://wiki.debian.org/SecureApt)

It makes so that apt-get can verify that your computer is downloading packages from the source it thinks it is. 

Basically they give you a public key, they have a private key which is kept secret.

They sign their packages with their private key, your public key can be used to figure out if the package was actually signed by their private key or not. Encryption is done this way too. (except your encrypting/decrypting files with your keys not signing them)

This makes sure the packages actually come from the source your downloading from and of course you should only add sources that your sure they check their software to make sure it's malware free.

---

### Post by originalsynthesis on 2009-01-16
One other thing for future ref., concerning a repositories source.list entry, what if they don't list an entry to add? have i just been rushing around to fast on websites and missing the entry listing? Or is there a way to figure it out from the site or url itself?

---

### Post by iaculallad on 2009-01-16
> **originalsynthesis said:**
> One other thing for future ref., concerning a repositories source.list entry, what if they don't list an entry to add? have i just been rushing around to fast on websites and missing the entry listing? Or is there a way to figure it out from the site or url itself?

Majority (if not All) will list their repository links on their websites as this is needed when installing softwares (Third Party). If repo links were not included, then, we will assume that it resides on either Main, Universe, Restricted or Multiverse repositories.

EDIT:

Here's an additional information regarding repositories:

[Psychocat's Enabling Extra Repositories]("http://www.psychocats.net/ubuntu/sources")

HTH.

---

