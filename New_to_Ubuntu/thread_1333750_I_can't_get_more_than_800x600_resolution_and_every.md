---
title: "I can't get more than 800x600 resolution and everything is slow as heck."
date: 2009-11-21
forum: New to Ubuntu
---

### Post by papuccino1 on 2009-11-21
I'm running the latest Ubuntu on VirtualBox to test it out. But so far I'm a bit dissapointed. I can only choose between 800x600 and 680x460 (or something) as resolutions.

Here's what I've done:

[LIST=1]
[*]Create new virtual machine.
[*]Set it to 512MB ram.
[*]Installed Ubuntu from scratch on a brand new virtual hard disk.
[*]Installed all the updates that appear the first time you run Ubuntu.
[/LIST]

I don't know what to do to make the virtual computer run faster and not have it visually hiccup all the time. For instance, I minimize a window and it doesn't go down immidiately it lags for like 0.3 seconds.

My machine has 2GB's ram and I'm running Windows 7.

I also have two other virtual machines installed and they run wonderful even when both Windows XP and Windows Server 2008 are running simultanously.

Right now I'm only running Ubuntu (I'm posting this thread from my virtual machine) and everything is so slow.

**PLEASE HELP GUYS! :D**

---

### Post by papuccino1 on 2009-11-21
bump

---

### Post by Sealbhach on 2009-11-22
Hi, there are a few things you can try to get a better screen. Firstly, you can allocate more memory from your graphics card to the virtual machine. I usually give it half.

Also, you can install [Virtualbox Guest Additions]("http://seogadget.co.uk/how-to-install-virtualbox-guest-additions/"), which will provide much better integration with the host desktop.

.

---

### Post by 3rdalbum on 2009-11-22
Install the Virtualbox Guest Additions to get some degree of video acceleration.

---

### Post by quinnten83 on 2009-11-22
you have to install the guest additions otherwise you can't change the resolution. Hpw much ram did you allocate to the VM and how much of that is video?

---

### Post by papuccino1 on 2009-11-22
Thank you all for trying to help. :)

Here are my configuration settings on VirtualBox. It's in Spanish, but I think it's pretty straight forward:
[IMG]http://imgur.com/Fv6jk.png[/IMG]


Regarding the virtual host additions. I mounted the iso that VirtualBox automatically does for me and this is what I get:

The icon on my desktop:
[IMG]http://imgur.com/WA6Vr.png[/IMG]

Double clicking on the icon, this folder opens. What file do I have to run? If I run the "VBoxLinuxAdditions-x86.run" file, I don't know what to do next. Please give me a play by play! :D
[IMG]http://imgur.com/uJ6e1.png[/IMG]

---

### Post by Sealbhach on 2009-11-22
To install guest additions,  you need to navigate into that folder and run the command:

```
./VBoxLinuxAdditions-x86.run

```That should do it. 

So you open a terminal and use the "cd" command to get there,


Try to allocate more than 16MB to the video card also, if you can spare it, I usually give it 64MB at least.

.

---

### Post by papuccino1 on 2009-11-22
> **Sealbhach said:**
> To install guest additions,  you need to navigate into that folder and run the command:

```
./VBoxLinuxAdditions-x86.run

```That should do it. 

So you open a terminal and use the "cd" command to get there,


Try to allocate more than 16MB to the video card also, if you can spare it, I usually give it 64MB at least.

.

Thank you for trying to help. :)

When I run the command you say, I get: "This program must be run under administrative privaledges."

What do I do? :S

---

### Post by Sealbhach on 2009-11-22
> **papuccino1 said:**
> Thank you for trying to help. :)

When I run the command you say, I get: "This program must be run under administrative privaledges."

What do I do? :S

Sorry, I should have thought of that. You need to invoke sudo which gives you temporary administrator powers.

So just run the command like this:

```
sudo ./VBoxLinuxAdditions-x86.run
```and enter your password when prompted. If for some reason it doesn't like that syntax, invoke sudo by running

sudo su

and entering your password, but remember to switch out of admin mode when you're finished by typing "exit".

.

---

### Post by Dennis N on 2009-11-22
Guest Additions can be simply installed from the Devices Menu on the Main VirtualBox window.

```
Devices > Install Guest Additions
```

It's at the bottom on that menu.

After installation and a restart, you can then resize the VB window or run full screen (Rt-Ctrl + F), and you will have seamless mouse integration (it won't be captured by the VB window).

---

### Post by marshmallow1304 on 2009-11-22
> **Sealbhach said:**
> 
```
./sudo VBoxLinuxAdditions-x86.run
```


It's

```
sudo ./VBoxLinuxAdditions-x86.run
```

---

### Post by Sealbhach on 2009-11-22
> **marshmallow1304 said:**
> It's

```
sudo ./VBoxLinuxAdditions-x86.run
```

OK, thanks, I have edited my post.

.

---

