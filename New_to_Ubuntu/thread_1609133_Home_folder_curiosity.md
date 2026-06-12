---
title: "Home folder curiosity"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by VinnyJ1701 on 2010-10-30
Hey all,

First off, this is a very naive question.  You have been warned :P

I've been reading about other distros, and how some make a separate partition for the Home folder. I think this is a very good thing and may attempt it someday if I can find a easy enough to follow set of directions.  

Here is the naive part.  Is it possible to just copy the home folder and its contents to another drive, or even a USB stick?

Thanks

Vince

---

### Post by BugBuster on 2010-10-30
> Is it possible to just copy the home folder and its contents to another drive, or even a USB stick?
yes!!!

---

### Post by VinnyJ1701 on 2010-10-30
> **BugBuster said:**
> yes!!!

Thank you :)

My question was just a curiosity.  I have no plan to attempt anything that might (likely would) screw up my system.  If I were to backup/copy/partition my home folder is would be to keep it safe from any accidental screw-ups I may make.   As I said, I'm planning no changes...  just asking a question.

Thanks Everybody..  This is a great community!

---

### Post by trikster_x on 2010-10-30
Are you talking about setting up a usb stick to be a traveling home folder?  In theory, I suppose you could, since you would simply need to tell Ubuntu where to look for the partition to mount as /home.

The problem you are going to run into is that each machine you use will have to be configured to mount the usb device as /home.  This means you would only be able to use that install of Ubuntu while the usb device is present.  I suppose this would be okay if you were only using it for a limited purpose, such as laptop security.  But on multiple machines it would probably be more of a bother than it is worth in the long run.

EDIT:  Sorry, I guess I misunderstood what you were asking.  But now you have my mind going about an external /home, so maybe...

---

### Post by sarum on 2010-10-30
[http://ubuntuforums.org/showthread.php?t=1421887&highlight=seperate+home+dir](http://ubuntuforums.org/showthread.php?t=1421887&highlight=seperate+home+dir)
The above is full of helpful stuff. But not for me. I parted a 15GB partition and followed instructions to the letter - copying and pasting. Starting with:- [COLOR="Black"]sudo mkdir /old[/COLOR].On getting to [COLOR="Black"]find. -depth.......[/COLOR]all went wrong and I gave up after many tries. No big deal for me, but I would add that this forum has helped me so often that, I'd have gone back to you-know-where long ago.
Good luck.

---

### Post by Boondoklife on 2010-10-30
Why are you looking to separate your home partition from the rest? Is this a multi user system? If it is not a multi user system then there really is no point as only you will be using the space. Sectioning off the home partition allows you to control how much space can be used by the systems users, but in a single login environment it really is pointless.

---

### Post by dapperdanny77 on 2010-10-30
> **Boondoklife said:**
> If it is not a multi user system then there really is no point as only you will be using the space.  

having a separate filesystem for /home gives me the possibility to reinstall ubuntu/whatever without harming my personal data.

---

### Post by VinnyJ1701 on 2010-10-30
> **dapperdanny77 said:**
> having a separate filesystem for /home gives me the possibility to reinstall ubuntu/whatever without harming my personal data.


A good thought...  something to think about when say, going from 8.04 10.04 LTS..?  Hmmm

---

### Post by Boondoklife on 2010-10-30
Why not just backup your files? You can run into all kinds of crazy issues if you simply use your old home folder. You have to remember each program puts configuration data in your home folder and if you upgrade, especially a huge one like 8.04 -> 10.10 you are putting yourself in a very precarious situation where any number of crazy bugs could show up due to the old config files.

A much better solution is to just have a data partition that you store your data on (files, music, videos etc.) and then just mount that to a usable location on the system. This way you can do that huge update with out worry of config files and what not getting in the way.

---

### Post by A_M_S on 2010-10-30
Its a good policy to have a separate Home partition (in my opinion). 
It's easier to upgrade your system.

The best way of doing this is with a clean install. 

Moving the home folder to a new partition may cause you problems if your system and home folder are initially in the same partition.

---

### Post by Boondoklife on 2010-10-30
> **A_M_S said:**
> Its a good policy to have a separate Home partition (in my opinion). 
It's easier to upgrade your system.

The best way of doing this is with a clean install. 

Moving the home folder to a new partition may cause you problems if your system and home folder are initially in the same partition.

Actually, moving it to another partition is not an issue. All you need to do is:

[LIST=1]
[*]copy the files to the new partition
[*]remove the contents of the old home folder (live cd works great for this)
[*]edit /etc/fstab to mount the new parition at boot
[*]reboot your done
[/LIST]
Again this can cause issues on re-installations as you will still have the configuration files for the various apps in the home folder even after a fresh install.

---

### Post by lotharmat on 2010-10-30
If it is not a core program you can just remove it with:

```
sudo apt-get remove --purge [programname]
```

and then 

```
sudo apt-get install [programname]
```

This will wipe out any config!

---

### Post by Boondoklife on 2010-10-30
> **lotharmat said:**
> If it is not a core program you can just remove it with:

```
sudo apt-get remove --purge [programname]
```and then 

```
sudo apt-get install [programname]
```This will wipe out any config!

This is true, but then what would be the advantage of keeping all that data and not just saving your important files to a different partition. If you are going to "purge" your config files each time then you would be left with just the data I said to backup in the first place. Kinda a long and cluttered road that is being taken for no apparent reason.

I prolly will not post again unless someone makes a good point as to why to use a home dir partition short of space management, which is the only real reason I see to do it. Before someone says encryption, you can do this with out partitioning your drive too.

---

### Post by lotharmat on 2010-10-30
I agree with you. - Much better just to back up any important files and copy them back once upgrade has taken place!

Cleaner and much more elegant!

Is there a way of just clearing config files for an application?

---

### Post by jaycee23 on 2010-10-30
> **Boondoklife said:**
> Why not just backup your files? You can run into all kinds of crazy issues if you simply use your old home folder. You have to remember each program puts configuration data in your home folder and if you upgrade, especially a huge one like 8.04 -> 10.10 you are putting yourself in a very precarious situation where any number of crazy bugs could show up due to the old config files.

A much better solution is to just have a data partition that you store your data on (files, music, videos etc.) and then just mount that to a usable location on the system. This way you can do that huge update with out worry of config files and what not getting in the way.
I have a separate /home partition which has worked well with fresh installs but I have now also got a separate Data partition which I can mount on which ever flavour of Linux I choose to install.

---

### Post by lotharmat on 2010-10-30
Dropbox was a real PITA when I fresh installed 10.10 leaving my /home partition intact - I had tried to re-install it but it wasn't having any of it until I removed its config files!

---

### Post by A_M_S on 2010-10-30
> **Boondoklife said:**
> Actually, moving it to another partition is not an issue. 

I never said it was.

> **Boondoklife said:**
> 
Again this can cause issues on re-installations as you will still have the configuration files for the various apps in the home folder even after a fresh install.
You can remove the problematic configurations ;)

Using different partitions for your data and your system is always a wise choice. 

You can use a partition only to save your data or save  in that partition the home folder. The two ways are valid

---

### Post by Boondoklife on 2010-10-30
[LIST=1]
[*]> **A_M_S said:**
> I never said it was.
Actually you did:
> **A_M_S said:**
> Moving the home folder to a new partition may cause you problems if your  system and home folder are initially in the same partition.
[*]> **A_M_S said:**
> You can remove the problematic configurations ;)
Again why would you do this when you can just have the data you want to keep instead of all the other stuff you need to remove later? You seen that someone else noted the same issue I said.
[*]> **A_M_S said:**
> Using different partitions for your data and your system is always a wise choice.
You keep saying this over and over but you can not note a single good reason why, other than your claim it aids in reinstallations (which has already been disputed a couple times here). I think my note about disc space limitation is the only valid reason given so far. Not saying there are not other good reasons, but none are listed here.
[*]> **A_M_S said:**
> You can use a partition only to save your data or save  in that partition the home folder. The two ways are validAbout the only thing that I agree with in this entire post.
[/LIST]

---

### Post by A_M_S on 2010-10-30
> **Boondoklife said:**
> [LIST=1]
[*]
Actually you did:
[/LIST]
I was talking of possible problems with you configuration files as you said before. Sorry for not being very clear.

> **Boondoklife said:**
> [LIST=1
[*]About the only thing that I agree with in this entire post.
[/LIST]
Then you agree with the most important part ;)

---

### Post by ironic.demise on 2010-10-30
I recommend making a /home partition.
It's VERY easy, I did it with no instruction.
and you don't need to backup your data (unless you are formatting and either way you REALLY should!)

Just next time you install *buntu (Choose manual partitioning) Choose where to install Ubuntu, (on the edit screen set "mount point" to "/") and then choose where you want to save /home (on the edit screen of the /home partition "mount point" to "/home") Remember DO NOT CLICK FORMAT on the /home partition, always double check that box is UNCHECKED! and remember to set the filesystem on both the / and /home to the same filesystem that they were originally, otherwise it WILL format your data.

Oh but you must set the filesystem to what it was, otherwise it goes as "unused" and that's bad.

---

