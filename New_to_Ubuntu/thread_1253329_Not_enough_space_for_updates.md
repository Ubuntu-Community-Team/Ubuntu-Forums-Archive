---
title: "Not enough space for updates"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by Gulfvet91 on 2009-08-30
So now I have 160 updates waiting to be installed.  The problem is that when I try to install them, Update Manager tells me I need 382MB of space to run the updates. I am supposed to clear 241 MB of space.  Which disk is it?  What can I safely remove?  Who is the genius that programmed Update Manager so you can't selectively download?  Every time I try to select updates to leave out, such as bluetooth crap for a bluetooth I don't have, the Manager closes on me.  

My sudo fdisk -l shows:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2917    23430771   83  Linux
/dev/sda2            2918        3648     5871757+   5  Extended
/dev/sda5            3570        3648      634536   82  Linux swap / Solaris
/dev/sda6            3244        3547     2441817   83  Linux
/dev/sda7            3548        3569      176683+  82  Linux swap / Solaris
/dev/sda8            2918        3221     2441817   83  Linux
/dev/sda9            3222        3243      176683+  82  Linux swap / Solaris

---

### Post by bboston7 on 2009-08-30
Why do you have seven partitions?

Also, fdisk -l tells us nothing about the size of your partitions.

---

### Post by bboston7 on 2009-08-30
Can you paste the result of
```
df -h
```

---

### Post by Gulfvet91 on 2009-08-30
Got most of my updates by doing:

sudo apt-get update
sudo apt-get upgrade

But a stubborn few are holding out.  Even re-running the above doesn't work.  It gives:

ken@ken-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
  linux-restricted-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

Now what?

---

### Post by Gulfvet91 on 2009-08-30
> **bboston7 said:**
> Can you paste the result of
```
df -h
```


ken@ken-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8             2.3G  2.2G   39M  99% /
tmpfs                 106M     0  106M   0% /lib/init/rw
varrun                106M  104K  106M   1% /var/run
varlock               106M     0  106M   0% /var/lock
udev                  106M  180K  106M   1% /dev
tmpfs                 106M     0  106M   0% /dev/shm
lrm                   106M  2.4M  104M   3% /lib/modules/2.6.28-11-generic/volat

---

### Post by 3rdalbum on 2009-08-30
> **Gulfvet91 said:**
> Who is the genius that programmed Update Manager so you can't selectively download?

I wouldn't go criticising other people's computing work when you're the one who told Ubuntu to install itself into the absolute minimum amount of space possible (2.3 gigabytes). You needed to move the slider on the partitioning screen to the left, to allocate more space.

You can selectively download updates, but maybe you've hit a bug exposed by your system running so close to the edge of hard disk space.

It's sometimes possible to resize the partition in Partition Editor (from the live CD) but depending on the state of your partitions before installing Ubuntu, you might not be able to. Reinstalling Ubuntu may be a better option. And this time, move the slider to the left on the partitioning screen.

---

### Post by Gulfvet91 on 2009-08-30
I don't get it.  When I re-installed Xubuntu I saw my 30 GB hard drive and now it is nowhere to be seen.  What do I have to do to get all my memory space?

---

### Post by bboston7 on 2009-08-30
wow.  I've never seen anything like this before.  2.3 Gb for the operating system yet you have 3 swap partitions?

I almost never say this, but I recommend that you tell xubuntu to use all of the disk and DON'T MANUALLY PARTITION.

---

### Post by neo.patrix on 2009-08-30
Partitioning always the first big hitch for any new linux users... 

I do not deny it has become much easier then old days when I used to install RedHat 7.3, but still lot of work is needed in that direction.

I would suggest you try Youtube , there are some excellent uploads on how to install Ubuntu safely, even as dual boot with Windows vista , if need be.

---

### Post by halitech on 2009-08-30
try reading up here on how to get a working dual boot system

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Chris Edgell on 2009-08-30
I MUST say, we see so very little sarcasm here, it WAS quite shocking.  (Now let me shine this light on my personal life...)  We do see some anger and extreme frustration is acceptable...
I love the calm and measured approach that so many use...it reminds me of the intelligence of a good bedside manner of an excellent physician.  [I know it's off-topic, just want to make this comment.  Is it okay??]

---

### Post by Paqman on 2009-08-30
> **neo.patrix said:**
> Partitioning always the first big hitch for any new linux users... 


That's why we have Wubi. Nobody needs to partition at all if they don't want to.

---

### Post by Gulfvet91 on 2009-08-31
> **neo.patrix said:**
> 
I would suggest you try Youtube , there are some excellent uploads on how to install Ubuntu safely, even as dual boot with Windows vista , if need be.

There is a problem with this.  I can't view any YouTube videos because I don't have flashplayer for some reason and when I try to install it, the system gives me all kinds of crap about some library files flashplayer apparently depends on and I don't have.

---

### Post by Gulfvet91 on 2009-08-31
> **halitech said:**
> try reading up here on how to get a working dual boot system

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Thanks, but I'm not going dual.  I hope to get Wine going for any Windows apps I need for the internet.  Otherwise I am going straight Linux.

---

### Post by Gulfvet91 on 2009-08-31
About my comment about Update Manager, I do apologize for my tone but I still would like to see it become easier to opt out of certain updates.

I have since taken several people's suggestions and re-loaded, giving Xubuntu my entire 30 GB disk.  Things are going much more smoothly now and I thank you all.  I got all my updates today in one try with no trouble.  Now for the next problem.  I need to figure out how to use Synaptic to install flashplayer and Wine.

---

### Post by rockerphil on 2009-08-31
flashplayer & wine are pretty easy to install. just open up a terminal and rune these commands:

```
sudo apt-get install flashplugin-nonfree
```

and

```
sudo apt-get install wine
```

and that should do it. if in the event that Flash doesn't install you can always install it the "Windows way" by downloading it from the web site and double clicking the .deb file. just be sure you download the right file for your release. hope this helps, 

Phil

---

### Post by LewRockwell on 2009-08-31
> **Gulfvet91 said:**
> About my comment about Update Manager, I do apologize for my tone but I still would like to see it become easier to opt out of certain updates.

I have since taken several people's suggestions and re-loaded, giving Xubuntu my entire 30 GB disk.  Things are going much more smoothly now and I thank you all.  I got all my updates today in one try with no trouble.  Now for the next problem.  I need to figure out how to use Synaptic to install flashplayer and Wine.

once you've gotten past the learning curve to proper partitioning and grub bootloader administration, then *nix distros become much more entertaining

check this thread out to see some screenshots of just one particular partitioning layout

[http://ubuntuforums.org/showthread.php?t=1222961](http://ubuntuforums.org/showthread.php?t=1222961)

.

---

### Post by Gulfvet91 on 2009-09-01
Solved.

---

