---
title: "Compiz?"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by KN0MAD on 2009-04-17
Hello, I would like to try out the Compiz effects?
I just downloaded now I don't know what to do XD

---

### Post by stalkier on 2009-04-17
> **KN0MAD said:**
> Hello, I would like to try out the Compiz effects?
I just downloaded now I don't know what to do XD

A lot more info is needed such as machine specs, OS version, etc. You have to help us help you.

---

### Post by BoneSaw on 2009-04-17
if you are running a newer version of ubuntu (i forget which version they actually started doing this in) compiz should be installed by default. just click

system>preferences>appearance

then click the visual effects tab. you can then select what all you would like to enable there. if your hardware cant handle the compositing effects, they wont start.

---

### Post by leonardo_neo on 2009-04-17
Have you installed compizconfig setting manager? If not here is the command for that.....

> sudo aptitude install compizconfig-settings-manager

Install this, and do various experiments. :)

---

### Post by KN0MAD on 2009-04-17
HP Pavilion DV5-1007TX Laptop
4GB RAM
2.53 Ghz 
Ubuntu 8.10.

Is that what you want?

---

### Post by James_Lochhead on 2009-04-17
Compiz effects are there by default in Ubuntu. You need to install your graphics card driver in order to use them though. They can then be enabledin System > Preferences > Appearance > Desktop Effects.

If you install compizconfig-settings-manager (like above) you can configure what is shown.

---

### Post by KN0MAD on 2009-04-17
Computer, I command you to "sudo aptitude install compizconfig-settings-manager"

Lol...?

---

### Post by James_Lochhead on 2009-04-17
Go to Applications > Accessories > Terminal, type: 

sudo apt-get -y install compizconfig-settings-manager

Then type enter.

Wait for it to download and install and it will then be under System > Preferences > Compizconfig.

If someone tells you to type something like that they generally mean do it in the terminal program ;).

---

### Post by James_Lochhead on 2009-04-17
sudo apt-get install is a way of installing things from the terminal (techies like doing this). If you are not such an advanced user you can also use Applications > Add/Remove Programs or (a little harder) System > Administration > Synaptic Package Manager.

---

### Post by KN0MAD on 2009-04-17
Bah...Can't do this on the CD? have to install Ubuntu?
Thanks for the help =)

---

### Post by CatKiller on 2009-04-18
> **KN0MAD said:**
> Bah...Can't do this on the CD? have to install Ubuntu?

If you're using Intel graphics then you can; they make a decent open source driver, which means it can be included on the cd. Since Ati and NVidia have chosen to keep their driver closed, it can't be included on the cd, which means you need to install Ubuntu and reboot before you install their drivers.

---

### Post by KN0MAD on 2009-04-20
Hi, so I have compizconfig-settings-manager installed.
I also have wobbly windows and the cube (amongst others) enabled but nothing happens, how to apply? Is there a key to start them?
I feel stupid having to come here every time lol...
Also, I am running this (Ubuntu 8.10) on Virtualbox if that means anything...

---

### Post by Paqman on 2009-04-20
> **KN0MAD said:**
> 
Also, I am running this (Ubuntu 8.10) on Virtualbox if that means anything...

You're not likely to get desktop effects from a VM. They just don't have enough power. Specifically, they have only basic support for hardware graphics acceleration (or none at all if you're using Virtualbox OSE)

So no, you won't get Compiz effects.

---

### Post by mlentink on 2009-04-20
VirtualBox does not support 3d. Sorry.

So you're running a liveCD in a virtual machine? Any particular reason?

---

### Post by KN0MAD on 2009-04-20
Ok thanks. I am running it on VB becausee I was scared to partition my HD lol. Not from LiveCD, I installed it.
I have tried Wubi, LiveCD, and now Virtualbox but now I think it is time to install it to my HD...

So you'll probably hear from me very soon ^_^

---

### Post by Paqman on 2009-04-20
Wubi would have given you desktop effects. Performance-wise it's just the same as a dual-boot.

---

### Post by KN0MAD on 2009-04-20
I can't remeber why exactly I uninstalled Wubi, I think I couldn't connect to the net with it so I got a tad frustrated and looked for a different way...
Wubi can do everything the same as installing to HD?
What do you mean 'Performance-wise it's just the same as a dual-boot'?

---

### Post by Paqman on 2009-04-20
> **KN0MAD said:**
> 
What do you mean 'Performance-wise it's just the same as a dual-boot'?

This:
> 
Wubi can do everything the same as installing to HD


Except: hibernate. Also, it doesn't like power cuts. The latter is never a problem on a laptop (since they have batteries).

---

### Post by daveedking on 2009-05-16
i installed from wubi ,im not runnin in a VM. and i installed compiz but i cant get effects 2 work like wobbly windows.. i have a 3 gig ram 250 hd intel core 2 duo acer aspire 5720 laptop..help

---

