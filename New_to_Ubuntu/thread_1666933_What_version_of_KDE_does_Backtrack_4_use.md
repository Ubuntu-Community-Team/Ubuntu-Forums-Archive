---
title: "What version of KDE does Backtrack 4 use?"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by cyb3r_sn4k3 on 2011-01-14
Hi everybody so I tried KDE in ubuntu and its kinda laggy but when I use Backtrack 4 it doesn't lag at all and it is as fast as gnome. So which version of KDE does it use or how can I make Ubuntu like that?

(Don't know whether this is the correct place feel free to move :) )

---

### Post by hansolo4949 on 2011-01-14
The reason KDE is lagging in Ubuntu is that Ubuntu is a much heavier-weight OS than backtrack, so it is naturally going to lag. I don't know how you could make Ubuntu non-laggy, but you should try using that enviroment with Xubuntu, which is a lighter version of Ubuntu.

---

### Post by hansolo4949 on 2011-01-14
The reason KDE is lagging in Ubuntu is that Ubuntu is a much heavier-weight OS than backtrack, so it is naturally going to lag. I don't know how you could make Ubuntu non-laggy, but you should try using that enviroment with Xubuntu, which is a lighter version of Ubuntu.

---

### Post by hansolo4949 on 2011-01-14
The reason KDE is lagging in Ubuntu is that Ubuntu is a much  heavier-weight OS than backtrack, so it is naturally going to lag. I  don't know how you could make Ubuntu non-laggy, but you should try using  that enviroment with Xubuntu, which is a lighter version of Ubuntu.

---

### Post by hansolo4949 on 2011-01-14
Quadruple post, so sorry :(

---

### Post by Simian Man on 2011-01-14
You can see what versions of everything distros have on [distrowatch]("http://distrowatch.com/table.php?distribution=backtrack").  According to them, it's KDE 3.5.10.  That was the last version in the KDE3 line.  Most distros now use KDE4 which is awesome, but may be slower on older machines.

---

### Post by wojox on 2011-01-14
I have kde3 on the bt4 disk. I remember reading on their site they tried kde4 but had to many issues. Maybe in bt4 r1 or r2.

---

### Post by cyb3r_sn4k3 on 2011-01-17
So is their anyway to replicate it in Ubuntu ?

---

### Post by kaldor on 2011-01-17
> **cyb3r_sn4k3 said:**
> So is their anyway to replicate it in Ubuntu ?

The old KDE 3.x stuff? Kinda, yes :)

You can either use a Kubuntu 8.04 disc (old, but still LTS) or install TDE. TDE is a fork of KDE 3.5 which is essentially just updates and patches.

[http://trinity.pearsoncomputing.net/](http://trinity.pearsoncomputing.net/)

Hope this helps.

[quote=TDE Website]
(K)ubuntu Trinity Repository Installation Instructions
1. Add these lines to your /etc/apt/sources.list file: 
For Maverick [STABLE] (4 lines): 
deb [http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity/ubuntu](http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity/ubuntu) maverick main
deb-src [http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity/ubuntu](http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity/ubuntu) maverick main
deb [http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-builddeps/ubuntu](http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-builddeps/ubuntu) maverick main
deb-src [http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-builddeps/ubuntu](http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-builddeps/ubuntu) maverick main
2. Add the GPG signing key:
sudo apt-key adv --keyserver keyserver.quickbuild.pearsoncomputing.net --recv-keys 2B8638D0

3. Install KDE 3.5:
sudo apt-get update
sudo apt-get install kubuntu-default-settings-kde3 kubuntu-desktop-kde3
[/quote]



EDIT: Click [_here_]("http://apt.pearsoncomputing.net/cdimages/") to get a Kubuntu remix with TDE instead of KDE.

---

