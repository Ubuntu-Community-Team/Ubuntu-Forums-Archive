---
title: "update manager more space"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by netbook on 2009-06-02
couple of questions, i want to install some updates in the update manager but when i do it tells me i need more space in my fliesystem, can i just delete what is there or is it important?

2nd what are some fun things i may want to try on linux now that i have it installed, screenlets, effefcts, etc. and how can i do so 

thanks

netbook

---

### Post by pspsampsp on 2009-06-02
its safe to delete stuff in your home folder however i wouldnt delete anything from anywhere else , are you running from a flash drive? if so i would buy a larger flashdrive.

---

### Post by netbook on 2009-06-08
no i have installed linux on my hard drive, but when i try to install it says not enough space, linux has 80 gigs so that should be plenty

the file system is the are with too little space i think

---

### Post by cariboo on 2009-06-08
Depending on how much you have installed, the archived packages in /var/cache/apt/archives may be taking up a fair amount of hard drive space. TO clean out the archived packages, open and Applications-->Accessories-->Terminal and type:

```
sudo apt-get clean
```

and to remove unneeded dependencies in the same terminal type:

```
sudo apt-get autoclean
```

So far, there are no gui tools to reclaim hard drive space used by archived packages.

---

### Post by CJ Master on 2009-06-08
> **cariboo907 said:**
> 
So far, there are no gui tools to reclaim hard drive space used by archived packages.

Sorry, but isn't there a GUI tool called "cruft remover" that does this? Please correct me if I'm wrong.

---

### Post by Elfy on 2009-06-08
> **netbook said:**
> no i have installed linux on my hard drive, but when i try to install it says not enough space, linux has 80 gigs so that should be plenty

the file system is the are with too little space i think

Can you open aterminal - run this command and post the results, it will give us a better understanding of how much room you had and now have.

```
df -h
```

If space is that tight that you need to clean out the apt cache to use the system then I would suggest that something needs to be done.

---

### Post by netbook on 2009-06-10
[FONT=monospace]Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             2.3G  2.2G     0 100% /
tmpfs                 497M     0  497M   0% /lib/init/rw
varrun                497M  104K  497M   1% /var/run
varlock               497M     0  497M   0% /var/lock
udev                  497M  156K  497M   1% /dev
tmpfs                 497M   84K  497M   1% /dev/shm
lrm                   497M  2.4M  495M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp
/dev/sda2              74G   12G   62G  17% /media/ACER
/dev/sda5              67G   52M   63G   1% /media/for linux

that is what came up after the command suggested. 
new problems, my background seems to auto reset randomly 

also sometimes i am automatically prompted for a keyring password and other times i have to click the connection applet and put in my wep key the the keyring after selecting my network, why automatic sometimes and others no.

also when i modify my theme and save it doesnt save anywhere.

dont want windows but finding it hard to live with linux too. 

please help
[/FONT]

---

### Post by netbook on 2009-06-10
ok guys total linux melt down, loaded up today, last night at close everyhting seemed fine other than the aforementioned problems, now i load up, my bottom panel is gone the top one is blank except for some stupid applet window chooser ap, no system, applications, places options, my background and theme are gone and back to default what is happeneing please help.

---

### Post by netbook on 2009-06-10
come on anyone some help here

---

### Post by shae on 2009-06-10
For whatever reason, you installed Ubuntu with a very small root partition that is full.  You may need to uninstall some packages to create room there, or expand that partition somehow.  I personally now suggest people to use just a / and swap partition rather than separate partitions to help prevent this kind of problem.

---

### Post by netbook on 2009-06-10
ok so what about the rest of my problems???

---

### Post by Elfy on 2009-06-11
I've seen similar issues with other full root partitions. You need to deal with that first - have you run the commands cariboo907 gave earlier - that will create some free space, assuming there are cached packages to remove, and allow you to boot normally.

---

