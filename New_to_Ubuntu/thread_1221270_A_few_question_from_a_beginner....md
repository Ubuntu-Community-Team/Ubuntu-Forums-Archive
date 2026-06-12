---
title: "A few question from a beginner..."
date: 2009-07-23
forum: New to Ubuntu
---

### Post by skaldicpoet9 on 2009-07-23
Recently I installed Jaunty on my laptop. I am still in the process of updating everything and getting things configured. So, far I am have some minor problems but nothing too big. I was hoping that you guys could help me out with a couple of issues I have been having. 

The first issue I have is that Java seems to not be enabled in Firefox. I have had this issue in Slackware before and remembering having to link two files together but the details of this elude me. I am running the 64bit version of Jaunty right now and have heard that there have been people having some issues with getting Java to run properly. 

The second issue is downgrading Wine. When I first installed Ubuntu on this computer Wine was at version 1.0.1. I upgraded it assuming that the newest version would be the most stable and didn't figure that I would have some issues with games that were working in 1.0.1. I used this page: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) as a reference to upgrade wine. I tried uninstalling and reinstalling Wine through the package manager but it seems to still be the same version. I would very much like to be able to use 1.0.1 again. 

The third thing is my partitions. When I installed Ubuntu I manually created partitions for /, /home and /swap. I did this because I had been using Slackware for awhile so it was almost reactionary when the prompt came up. I used 10gb for /, 5 for /swap, and 200gb for /home. However, now my root is almost full with only this page~3gb left or so. I have installed a few programs from the package manager but I don't know how I could almost be approaching capacity. Is this a bad thing or is there a way to create more space for / from /home? 

On the note of my /swap partition. It seems that I very rarely use my swap and when I have I was only utilizing 450kb of 5gb. I do use hibernate though, which I heard uses swap and needs a little over your total ram. Do I have too much swap? And is there a way to solve this?

My last question has to do with upgrading Firefox to 3.5. I googled this a few days ago and read that you could do this through Synaptic. I installed the relevant packages but Firefox is still version 3.0.12. How do I enable 3.5? Do I have to uninstall 3.0.12 first?

Thanks in advance for any help you guys can provide :)

---

### Post by shifty_powers on 2009-07-23
firstly java:

```
sudo aptitude install ubuntu-restricted-extras
```

should be your first port of call...

and then wine..

```
sudo aptitude purge wine
```

then install the deb.

use the gparted livecd (google it) to resize your root partition.

as for swap, yes it is a little big, but there is no harm in leaving it alone.

with firefox

```
sudo aptitude install firefox-3.5
```

and then look for shiretoko in applications>internet.

:D

---

### Post by Master_Odin on 2009-07-23
For the third issue, just go into terminal, and type:
```

sudo apt-get install firefox-3.5

```
Let it run through, and after that, you'll see "Shiretoko Web Browser" in your Internet Menu under Applications. It's named that so for easy distinction between Firefox 3.0 and 3.5 (shiretoko was the code named) and so you could run the two side by side.

---

### Post by shifty_powers on 2009-07-23
beat you on that :P

---

### Post by raymondh on 2009-07-23
> **skaldicpoet9 said:**
> 

The third thing is my partitions. When I installed Ubuntu I manually created partitions for /, /home and /swap. I did this because I had been using Slackware for awhile so it was almost reactionary when the prompt came up. I used 10gb for /, 5 for /swap, and 200gb for /home. However, now my root is almost full with only this page~3gb left or so. I have installed a few programs from the package manager but I don't know how I could almost be approaching capacity. Is this a bad thing or is there a way to create more space for / from /home? 

On the note of my /swap partition. It seems that I very rarely use my swap and when I have I was only utilizing 450kb of 5gb. I do use hibernate though, which I heard uses swap and needs a little over your total ram. Do I have too much swap? And is there a way to solve this?


Welcome and congratulations on your Ubuntu install.

I have loaded a bunch of apps but only managed 5GB in root.  Check 

```
df -h
```

from terminal as well as have a look in synaptic for installed applications.  If you're ok with your installed apps, you may need to grab more space from /home.

Re SWAP :  

You are correct in noting that it rarely uses much swap space because you may have adequate, or a lot of, RAM.  Sometimes, I use a resource-intensive app (video editing) and hibernate.  Even then, I don't see my swap being used as I have 4GB ram. It would'nt hurt to bring it down to about 1.5GB.  Then again, it also would not hurt to leave it alone unless you are really pressed for space.

I'll be more concerned on why your root is filling up fast.

---

### Post by skaldicpoet9 on 2009-07-23
> **shifty_powers said:**
> firstly java:

```
sudo aptitude install ubuntu-restricted-extras
```

should be your first port of call...


Hmm, I already have installed that package. I looked in my package manager and Java is installed, the Java website confirms my installation but recommends that I update to the newest version. Is there an easy way of updating to the newest version (such as apt-get) or should I just get the file from the Java website? By the way I discovered that Java is indeed working, but for some reason one app in particular won't work ([http://www.minecraft.net/](http://www.minecraft.net/)). 

> **shifty_powers said:**
> 
```
sudo aptitude install firefox-3.5
```

and then look for shiretoko in applications>internet.

:D

Ha, I guess it is already there then. I just didn't recognize "shiretoko". Right, on. 

Thanks a lot for the responses. That solves everything for right now. 
...oh, actually I had a question about Pidgin (it's not too important since I rarely use the feature). I accepting a file transfer from a friend but was unable to download it. He and I both use Yahoo as our IM provider and I did come across some tidbits that eluded to it being a Yahoo Messenger issue. Is there anyone that knows how to solve this problem?

Anyways, thanks a lot shifty and odin :)

---

### Post by skaldicpoet9 on 2009-07-23
> **raymondhenson said:**
>  I'll be more concerned on why your root is filling up fast.

well the only thing I can tell from the packages installed in Synaptic is that a lot of libraries for various apps were installed. I don't know if that would effect root but all I know is that all I have installed is about 7 or so games (Open Arena, Free Civ, Battle for Wesnoth to name a few) the Eclipse IDE, Blender and the updates that Ubuntu has prompted me with. I also installed VMWare and Windows XP professional but I assumed that those were installed to /home. Where do the VMware and XP installations reside? Because I know that I am using 8gb for XP alone, that wouldn't make much sense though because I still have 3gb of 10gb left which only indicated 7gb is full. I don't know, but here are the results of df -h, if necessary:

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             9.4G  6.0G  3.0G  67% /
tmpfs                 1.9G     0  1.9G   0% /lib/init/rw
varrun                1.9G  248K  1.9G   1% /var/run
varlock               1.9G     0  1.9G   0% /var/lock
udev                  1.9G  156K  1.9G   1% /dev
tmpfs                 1.9G   88K  1.9G   1% /dev/shm
lrm                   1.9G  2.5M  1.9G   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sda3             216G   24G  182G  12% /home

```

I also have another quick question: how do I retrieve my Applications>Wine folder? It is no longer there after I reinstalled Wine. Wine is installed but the menu entry is gone. I would edit the menu manually but I am unsure as to how that works exactly.

---

### Post by llamabr on 2009-07-23
Your root looks ok.  You can run

```
sudo apt-get clean
```

to clear out all those .deb files, which will help a bit.

---

### Post by sXeChris on 2009-07-23
If it helps, you can check your Wine version by opening a terminal and typing "wine --version".

---

### Post by CatKiller on 2009-07-23
> **skaldicpoet9 said:**
> I tried uninstalling and reinstalling Wine through the package manager but it seems to still be the same version. I would very much like to be able to use 1.0.1 again. 

It's going to still be the same (newest) version as long as you've got the Wine repository enabled.

The easiest way to force a package to be a certain version is to go into Synaptic, find the package in the list, and select Package &#8594; Force version. Then you can select the version that you want. As an optional second step, you can lock the version to prevent future upgrades, but you shouldn't need to in this case. Just disable the Wine repository and you'll only get official security updates.

---

### Post by skaldicpoet9 on 2009-07-23
> **llamabr said:**
> Your root looks ok.  You can run

```
sudo apt-get clean
```

to clear out all those .deb files, which will help a bit.

That did help out quite a bit, it freed up an extra gb. Thank, man.

> **sXeChris said:**
> 
If it helps, you can check your Wine version by opening a terminal and typing "wine --version".

Yeah, that does help, thanks. Apparently I was still using the latest version.

> **CatKiller said:**
> 
The easiest way to force a package to be a certain version is to go into Synaptic, find the package in the list, and select Package &#8594; Force version.

Awesome, thanks a lot. I just checked my version and it is back to 1.0.1. Now I just need to figure out how to add the Wine menu icons back to my Application menu...

---

### Post by raymondh on 2009-07-23
another tip from the community documentation ... [recover disk space]("https://help.ubuntu.com/community/RecoverLostDiskSpace") ... see notes about trash.

---

