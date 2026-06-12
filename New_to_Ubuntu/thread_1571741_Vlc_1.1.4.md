---
title: "Vlc 1.1.4"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by BJones007 on 2010-09-10
I just downloaded a .tar.bz2 file for VLC 1.1.4, extracted the files, but now I dunno how to install it using the Terminal, some help please. (In Lehman's terms preferably...lol)

---

### Post by Saint_ on 2010-09-10
Was updating via Synaptic an option? Also to do this via the terminal, first type ```
cd <directory of VLC here> (so IE /home/vlc-1.1.4 or whatever it is)
``` then ```
sudo ./configure 
sudo make install
```
That should do it

---

### Post by beew on 2010-09-10
Is there a reason why you want to install from a tar ball?

A better way to get vlc 1.1.4 would be to add a PPA to your software source list and use Synaptic to install it. After that it will be integrated into your repositories and Ubuntu's software manager will keep track of the updates and dependencies. If you install from a tar ball manually you will have to update it manually next time.

Visit [ https://launchpad.net/~ferramroberto/+archive/linuxfreedomlucid]("https://launchpad.net/%7Eferramroberto/+archive/linuxfreedomlucid") and add the PPA to your system (open Synaptic, go to setting> repositories > other softwares and click add, then  copy the line they tell you to add  on the lauchpad page and paste it into the box, the reload Synaptic to update the sources and install vlc 1.14)

---

### Post by BJones007 on 2010-09-10
> **beew said:**
> Is there a reason why you want to install from a tar ball?

A better way to get vlc 1.1.4 would be to add a PPA to your software source list and use Synaptic to install it.

I tried that but it kept saying that the version I have is outdated, which was 1.0.6. So I just downloaded 1.1.4 manually

---

### Post by beew on 2010-09-10
That's right. That is the whole point. If you add the ppa you will get 1.14. It will shows that your installed version is outdated, just mark it for update and apply and it will upgrade to 1.14. That is the beauty of PPAs, they are integrated into the repo system so the software manager will keep track of updates.

---

### Post by beew on 2010-09-10
Maybe I should explain a bit more clearly, when Synaptic says you have an outdated program that means it has a more up to date version in one of your repositories (either the official ones or PPAs that you have added) and it is an invitation to upgrading to the latest version in the repos. Now by adding the PPA I linked to the most updated version would be 1.14 so Synaptic would show that your version is outdated and you just have to mark it and click apply and it will be updated automatically with all the dependencies taken care of.

If you install from the tar ball, you will end up with two versions of vlc and you will have to remove the older one.

---

### Post by BJones007 on 2010-09-10
> **beew said:**
> Is there a reason why you want to install from a tar ball?

A better way to get vlc 1.1.4 would be to add a PPA to your software source list and use Synaptic to install it. After that it will be integrated into your repositories and Ubuntu's software manager will keep track of the updates and dependencies. If you install from a tar ball manually you will have to update it manually next time.

Visit [ https://launchpad.net/~ferramroberto/+archive/linuxfreedomlucid]("https://launchpad.net/%7Eferramroberto/+archive/linuxfreedomlucid") and add the PPA to your system (open Synaptic, go to setting> repositories > other softwares and click add, then  copy the line they tell you to add  on the lauchpad page and paste it into the box, the reload Synaptic to update the sources and install vlc 1.14)
Btw the link you posted, what am I s'ppose to do with it? Can't make heads or tails of it :S

---

### Post by BJones007 on 2010-09-10
> **beew said:**
> That's right. That is the whole point. If you add the ppa you will get 1.14. It will shows that your installed version is outdated, just mark it for update and apply and it will upgrade to 1.14. That is the beauty of PPAs, they are integrated into the repo system so the software manager will keep track of updates.
Ok I'll do exactly what you say, will let you know if I encounter any prolems.

---

### Post by beew on 2010-09-10
> Btw the link you posted, what am I s'ppose to do with it? Can't make heads or tails of it :SThe link contains packages in a third party repository. It is like the  Ubuntu repositories except it is maintained by this guy Ferram Roberto  instead of the Ubuntu team and it has not been cleared by Ubuntu's  security team (so there is a bit of risk involved ) The page lists the  packages in the repository and the version. If you go down the list you  will find vlc and the version is 1.14, which is the latest one.

Why use PPAs? Programs in the official repository are "frozen" at the  time when the version of Ubuntu is released, in  other words they won't  get updated except for security patches for 6 months until the next Ubuntu  release comes out. There will be no new features. The idea is that if you have something that works  you don't wreck it by introducing unknowns such as feature updates. Now  this works fine with some people who care about safety and security  above all else. But others would want to have more updated softwares and  wouldn't mind taking a bit of risk (what is life without risk, eh? :))  PPAs are a good way to get up to date softwares even though there is a  bit of risk involved.

So what do you do with the link? Open Synaptic, go to setting >  repositories > other softwares. Click add. A box will appear. Go  to the launchpad link, copy the line **"ppa:ferramroberto/linuxfreedomlucid**"  without quotations as instructed on the web page and paste it into  Synaptic's dialogue box to add the PPA. Then reload synaptic to update  your repositories. Then search for vlc and you will see the box is  gray and it says something like it is outdated. Just mark it for update  and click apply. It will update vlc to version 1.14.

Since there is some risk in using PPA you should use  them only to update end user softwares instead of system stuffs like Linux kernel, drivers and so on.  You may also want to get Ubuntu tweak (google it, too lazy to look it up now). It has a feature called ppa purge. If problems arise from a PPA's packages you can purge the PPA by removing the PPA from your source list and safety downgrading the installed packages from the PPA to the next lower version while taking care of the dependencies.

---

### Post by 0004tom on 2010-09-10
Your to add the PPA.

From terminal it would be 

```
sudo add-apt-repository ppa:ferramroberto/linuxfreedomlucid

sudo apt-get update

sudo apt-get install vlc
```

---

### Post by BJones007 on 2010-09-10
I keep getting this error message whenever I  go into the repository index and click reset >  "The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct"  and >  Failed to fetch [http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.  my network connection is fine :S

Added this into repository >  deb [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) lucid main 

---

### Post by beew on 2010-09-10
That PPA no longer exists. c Korn's  repo is busted. Last time I tried to update vlc from it it tried to remove half of my programs (this is the kind of risk I talked about). I think he was using some libraries which were in conflict with the other already installed ones so upgrading to his version would remove the others. Turns out he has a bit of a bad reputation after some googling. Use the Ferram Roberto one.

---

### Post by BJones007 on 2010-09-10
> **0004tom said:**
> Your to add the PPA.

From terminal it would be 

```
sudo add-apt-repository ppa:ferramroberto/linuxfreedomlucid

sudo apt-get update

sudo apt-get install vlc
```
Dude you're awesome man! It's working like a pro now hehehe thanks alot =D>

And thanks guys for all your help

---

### Post by BJones007 on 2010-09-10
> **beew said:**
> That PPA no longer exists. c Korn's  repo is busted. Last time I tried to update vlc from it it tried to remove half of my programs (this is the kind of risk I talked about). I think he was using some libraries which were in conflict with the other already installed ones so upgrading to his version would remove the others. Turns out he has a bit of a bad reputation after some googling. Use the Ferram Roberto one.
Ok dude, thanks alot :)

---

### Post by andrew.46 on 2010-09-10
Hi BJones,

> **BJones007 said:**
> I just downloaded a .tar.bz2 file for VLC 1.1.4, extracted the files, but now I dunno how to install it using the Terminal, some help please. (In Lehman's terms preferably...lol)

Sounds like you have your problem sorted out now but you might be interested to see what is actually required to build from the tarball you have downloaded:

Howto: Build the development version of vlc under Ubuntu
[http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)

The instructions for 1.1.4 are at the bottom of the guide...

Andrew

---

