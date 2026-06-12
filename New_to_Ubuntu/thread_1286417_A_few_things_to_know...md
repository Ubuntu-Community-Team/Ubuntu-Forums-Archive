---
title: "A few things to know.."
date: 2009-10-08
forum: New to Ubuntu
---

### Post by 10Digits on 2009-10-08
Hi,
I have been using gnome for the last few months and now that I have switched to KDE I seem entirely lost.

Firstly, Gnome used to detect my graphics card and wifi out of the box and as soon as I would connect to the internet I would install them.But KDE cannot detect any of these two..

Secondly, I could find how to install other softwares through add or remove programs or synaptic but it seems there is no synaptic in KDE..!!Or it is there in some other name that I am not aware of...

There is no third point but I would like to know if all this is because I am using the beta version of Kubuntu Netbook Remix 9.10??

I am using it on my Compaq CQ50-106AU notebook.

P.S: the jockey-kde applet just crashed,twice!!Can you tell me what that is??

Thanks in advance..

---

### Post by Perfect Storm on 2009-10-09
9.10 is still development phase, why not try 9.04

With 9.04 and latest KDE4

```
sudo apt-get update && sudo apt-get upgrade
```


Then grab the latest KDE for kubuntu 9.04: 
```
sudo nano /etc/apt/sources.list
```


add in the bottom:
[b]## Kubuntu Backports
deb [http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) jaunty main

## Kubuntu Beta Backports
deb [http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu) jaunty main
[/b]

Save: [ctrl]+[o]
Exit: [ctrl]+[x]

```
gpg --keyserver keyserver.ubuntu.com --recv 2836CB0A8AC93F7A
gpg --export --armor 2836CB0A8AC93F7A | sudo apt-key add -
```



I usually use synaptic in my Kubuntu, get it like this:
```
sudo apt-get install synaptic
```

While in synaptic, grab all the new updates.
Reboot requires after that.

---

### Post by 10Digits on 2009-10-09
Thank you Artificial Intelligence for the reply....


1)I already have 9.10 beta KNR so will it be a problem if I upgrade now???

2)Kubuntu is not letting me install synaptic...this is what came out at the konsole:

sayan@infinity-gateway:~$ sudo apt-get install synaptic
[sudo] password for sayan:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package synaptic has no installation candidate


3)I have not yet edited my sources list, but will it be safe if I do??

My whole OS is behaving sluggishly the mouse responds really slow like its moving through molasses and Konqueror is clipping the web pages...

So, please help me out its urgent...I installed this today morning only a few hours before....


Thank you.

---

### Post by parminder_mangat on 2009-10-09
i am using ubuntu 9.04. Should i change it to kubuntu or ubuntu is better? Else i install kde on ubuntu? which one is easy and better? Please guide me.

---

### Post by 10Digits on 2009-10-09
@Parminder_Mangat:{sorry if I spelled ur name incorrect} From my personal experience the few years that i have been using linux I found gnome to be much easier to handle around...


KDE, on the other hand has a very polished interface built to impress but has done nothing more than that....

@Artificial Intelligence: even after adding all that stuff to my sources list I am still suffering from clipping and horrible slowdowns so I have decided to put kubuntu beta on ice and use my ubuntu jaunty distro instead...

can anyone tell me whether it is possible to install the karmic ubuntu netbook interface on jaunty??

---

### Post by Perfect Storm on 2009-10-09
> **10Digits said:**
> Thank you Artificial Intelligence for the reply....


1)I already have 9.10 beta KNR so will it be a problem if I upgrade now???

2)Kubuntu is not letting me install synaptic...this is what came out at the konsole:

sayan@infinity-gateway:~$ sudo apt-get install synaptic
[sudo] password for sayan:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package synaptic has no installation candidate


3)I have not yet edited my sources list, but will it be safe if I do??

My whole OS is behaving sluggishly the mouse responds really slow like its moving through molasses and Konqueror is clipping the web pages...

So, please help me out its urgent...I installed this today morning only a few hours before....


Thank you.



[COLOR="Red"]*1)I already have 9.10 beta KNR so will it be a problem if I upgrade now???*[/COLOR]
9.10 is the latest but not stable/ready (hence it's marked as beta).
9.04 is the latest stable version which is recommendable for new users. Alpha/beta versions are to those who knows the system and can crunch troubles and report back to the developers.
My suggestion is to burn kubuntu 9.04 you can always upgrade the 9.04 to 9.10 when 9.10 is ready for public.

[COLOR="#ff0000"]*2)Kubuntu is not letting me install synaptic...this is what came out at the konsole:*[/COLOR]
It looks like your sourcelist is disable, you can correct it by editing the source list (as previous posted) and remove # infront of every source listed in the list.

[COLOR="#ff0000"]*3)I have not yet edited my sources list, but will it be safe if I do??*[/COLOR]
On the safe side backup the info of the sourcelist first.

---

### Post by Perfect Storm on 2009-10-09
> **10Digits said:**
> 
 even after adding all that stuff to my sources list I am still suffering from clipping and horrible slowdowns so I have decided to put kubuntu beta on ice and use my ubuntu jaunty distro instead...

Properly needs the 3D driver.

> 
can anyone tell me whether it is possible to install the karmic ubuntu netbook interface on jaunty??

I suggest you make a new thread for that.

---

### Post by 10Digits on 2009-10-09
@Artificial Intelligence: It seems I have found out about beta the hard way....

My jockey-kde applet was behaving erratically ....


Anyways, it seems I will be installing Ubuntu 9.04 after a few minutes..

Thanks for your patience..

---

### Post by Perfect Storm on 2009-10-09
> **parminder_mangat said:**
> i am using ubuntu 9.04. Should i change it to kubuntu or ubuntu is better? Else i install kde on ubuntu? which one is easy and better? Please guide me.

You can't really put it up like that. It's different from user to user. It's all about taste and what the users are familiar with. Of cause there will be a period of adjusting to a new DE. The good thing with Linux is that there's many kind and different of DEs and/or WMs for every fit and taste. You just have to learn a new interface.

You can install KDE4 (kubuntu) along with Ubuntu and switch between them (you change between them in the login screen).

```
sudo aptitude install kubuntu-desktop
```

---

