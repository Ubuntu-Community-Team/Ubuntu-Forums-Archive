---
title: "How do I upgrade server using the alternative cd?"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by agreenbhm on 2009-04-23
Seems simple enough.  The Ubuntu website only has instructions for machines with Gnome or KDE installed.  I've got a pure server install.  I tried: 

sudo apt-cdrom add
sudo apt-get update
sudo apt-get dist-upgrade

but it just goes and starts to download from the online repos.  Help!

---

### Post by agreenbhm on 2009-04-23
I got impatient so I just went into my repo list and commented out everything except for the CD.  Hopefully that wasn't wrong...

---

### Post by MuddBuddha on 2009-04-23
Try: Alt+F2:

gksu "sh /cdrom/cdromupgrade"

---

### Post by agreenbhm on 2009-04-23
> **MuddBuddha said:**
> Try: Alt+F2:

gksu "sh /cdrom/cdromupgrade"

NO.  That's not it.  I get a message saying that it can't launch the gui or something like that b/c I have server, not desktop.

---

### Post by MuddBuddha on 2009-04-23
Try this:

[https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)

The recommended server upgrade is through Update Manager via network, but it does list upgrade via ALT CD.

---

### Post by agreenbhm on 2009-04-24
> **MuddBuddha said:**
> Try this:

[https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)

The recommended server upgrade is through Update Manager via network, but it does list upgrade via ALT CD.

Once again, that is the same "gksu" method posted everywhere else.  Doesn't help for someone without X.

---

### Post by JoshuaRL on 2009-04-24
[http://www.itwire.com/content/view/23867/1141/1/1/](http://www.itwire.com/content/view/23867/1141/1/1/)

---

### Post by agreenbhm on 2009-04-24
> **JoshuaRL said:**
> [http://www.itwire.com/content/view/23867/1141/1/1/](http://www.itwire.com/content/view/23867/1141/1/1/)

Did you not read any of this thread?

---

### Post by JoshuaRL on 2009-04-24
> **agreenbhm said:**
> Did you not read any of this thread?

Did you read the link?  If you go to the bottom of the first page, it talks about having an easy CLI upgrade method on the second page.

I found that page by searching Google for "upgrade server ubuntu cli jaunty", just in case you were wondering.

---

### Post by agreenbhm on 2009-04-24
> **JoshuaRL said:**
> Did you read the link?  If you go to the bottom of the first page, it talks about having an easy CLI upgrade method on the second page.

I found that page by searching Google for "upgrade server ubuntu cli jaunty", just in case you were wondering.

sudo apt-get dist-upgrade

That?

That uses the network.  I need it straight from the CD.

---

### Post by JoshuaRL on 2009-04-24
If you have your repos set to pull just from the CD, then it should do just that.

---

### Post by meganox on 2009-04-24
You can try

```
$ sudo sh /cdrom/cdromupgrade
```

but that might only work from the alternate cd.

Or give it a go with your sources.list with everything but the CD commented out.

[http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD](http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD)

---

### Post by Partyboi2 on 2009-04-24
I did not think you could upgrade ubuntu server version by using the alternate cd.

---

### Post by agreenbhm on 2009-04-24
I think my initial solution was correct bc even sudo sh /cdrom/cdromupgrade tries to pull from the repos a little bit unless they're commented out.

---

### Post by SabreWolfy on 2009-05-01
So what was the final solution to this? Update sources.list?

I've recently installed Jaunty Server onto a machine at home and I'd like to be able to upgrade it with each release. I don't, however, want to download the entire upgrade every 6 months, when I can easily download the Alternate CD elsewhere. I hope that upgrading server works from the Alternate CD ...

---

### Post by agreenbhm on 2009-05-01
> **SabreWolfy said:**
> So what was the final solution to this? Update sources.list? I've recently installed Jaunty Server onto a machine at home and I'd like to be able to upgrade it with each release. I don't, however, want to download the entire upgrade every 6 months, when I can easily download the Alternate CD elsewhere. I hope that upgrading server works from the Alternate CD ...

Yes, add the cd to sources.list by running "sudo apt-cdrom add", comment out everything from sources except the cd, run the upgrade, then uncomment the repos.

---

### Post by SabreWolfy on 2009-05-01
Ok, thanks. I'll give it a try in 6 months when Karmic Koala is released!

It's quite strange that there is not a more elegant / automated / official way of doing this.

---

### Post by agreenbhm on 2009-05-01
> **SabreWolfy said:**
> Ok, thanks. I'll give it a try in 6 months when Karmic Koala is released!

It's quite strange that there is not a more elegant / automated / official way of doing this.

Tell me about it. I think that if you add a cd to the repos, it should default to that to d/l content, or at least ask you.  On release day, I d/l'd the torrent of the alt cd at blazing speeds, only to have 8.10 default to d/l the content at 40kb/s when trying to upgrade, even though the cd was mounted AND in my sources.list.  Apt just loves those interwebs.

---

### Post by nandemonai on 2009-05-01
```
Install update-manager-core if it is not already installed:

sudo apt-get install update-manager-core

Launch the upgrade tool:

sudo do-release-upgrade

Follow the on-screen instructions. 
```

That's the preferred method.

If you've edited your sources.list to only include the CD then you should be sweet.

And you really should be using the server CD, not the alternate one.

---

### Post by agreenbhm on 2009-05-01
> **nandemonai said:**
> ```
Install update-manager-core if it is not already installed:

sudo apt-get install update-manager-core

Launch the upgrade tool:

sudo do-release-upgrade

Follow the on-screen instructions. 
```

That's the preferred method.

If you've edited your sources.list to only include the CD then you should be sweet.

And you really should be using the server CD, not the alternate one.


Two things:

1. Why should you be using the server CD for an upgrade?  It shouldn't matter.

2. Sudo do-release-upgrade always tried to d/l the content rather than adding the cd, even though it was in the sources.list file.

---

### Post by SabreWolfy on 2009-05-01
> **nandemonai said:**
> <snip>
And you really should be using the server CD, not the alternate one.

Ah! Thanks -- very good point. Are you confirming that an upgrade can be completed from the Server CD? The reason I ask is that once before I tried to upgrade a non-server installation from the Live/Desktop CD, only to find that I needed the Alternate CD in order to upgrade. I'm presuming though that the Server CD allows for fresh installations as well as upgrades.

---

### Post by agreenbhm on 2009-05-01
> **SabreWolfy said:**
> Ah! Thanks -- very good point. Are you confirming that an upgrade can be completed from the Server CD? The reason I ask is that once before I tried to upgrade a non-server installation from the Live/Desktop CD, only to find that I needed the Alternate CD in order to upgrade. I'm presuming though that the Server CD allows for fresh installations as well as upgrades.

It's my understanding that the alt. cd would be the proper upgrade choice for either server or desktop.  According to [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) the recommended upgrade options are the network installations, but for us, that's not an option in this scenario. The page clearly states that the upgrade option from physical media involves using the alternate cd.

---

### Post by JoshuaRL on 2009-05-01
Let me first say that I haven't tried this myself.  I have an Intrepid server running and haven't needed to upgrade it to Jaunty yet.  Maybe if I get into clustering, who knows.  But I'm going to offer suggestions from what I know.

> **agreenbhm said:**
> Two things:

1. Why should you be using the server CD for an upgrade?  It shouldn't matter.

2. Sudo do-release-upgrade always tried to d/l the content rather than adding the cd, even though it was in the sources.list file.

1).  It does matter.  The reason the server is a different version is because things are packaged different for it.  Otherwise, you could just have an Alternate CD and not install X or a DE.  That's pretty much what a server OS is anyway.  For instance, the kernels are different from the Alternate CD and different packages necessary for a server are included too.

2).  The answer to this question was answered before, but I'll discuss it below, with the instructions themselves.

> **SabreWolfy said:**
> Ah! Thanks -- very good point. Are you confirming that an upgrade can be completed from the Server CD? The reason I ask is that once before I tried to upgrade a non-server installation from the Live/Desktop CD, only to find that I needed the Alternate CD in order to upgrade. I'm presuming though that the Server CD allows for fresh installations as well as upgrades.

I can't confirm this, but I'm pretty sure that it's true.

> **agreenbhm said:**
> It's my understanding that the alt. cd would be the proper upgrade choice for either server or desktop.  According to [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) the recommended upgrade options are the network installations, but for us, that's not an option in this scenario. The page clearly states that the upgrade option from physical media involves using the alternate cd.

The reason that the Alternate CD is listed there for offline upgrades is because of the LiveCD.  It's set up to run a full system off of it, and not do any special installs.  The Alternate CD is the one that can act almost like a repo and install whatever you want or need.  That's just the way things are set up.

For servers, the install CD IS an Alternate CD.  There's no need for a LiveCD for servers, and so the Alternate CD abilities are included instead.  Before the LiveCD was invented, this is how Linux CDs worked.

So now let's look very carefully at the proper directions:

> **nandemonai said:**
> ```
Install update-manager-core if it is not already installed:

sudo apt-get install update-manager-core

Launch the upgrade tool:

sudo do-release-upgrade

Follow the on-screen instructions. 
```

That's the preferred method.

If you've edited your sources.list **to only include the CD** then you should be sweet.

And you really should be using the server CD, not the alternate one.

I added the bold to emphasize an important point.  If you have any other sources enabled in sources.list, APT priorities will try to get them from there.  A CD is just a CD, while the repos are trusted and maintained.  Please double or triple check your list to make sure everything is commented out EXCEPT for the CD.

---

### Post by nandemonai on 2009-05-01
Alrighty looks like I was wrong. I suggested server CD because that has the server kernel on it and the instructions on the site give GUI options for upgrading from the alternate CD.

I just tried with a 6.06 LTS VM to 8.04 LTS with the server CD.

It works up to the point where do-release-upgrade just says 'No new releases found'. Perhaps I missed something? I did add the CD via apt-cdrom add and commented out all other entries.

I've had apt-get dist-upgrades go bad in the past hence my original suggestion and sure enough, performing a dist-upgrade has broken things. Lots of device mapper errors due to fstab not being updated with the new /dev/sdX entries rather than /dev/hdX.

Probably some other things that have been left behind too.

Using the recommended server upgrade instructions (network) works so not sure what to tell ya.

Perhaps alternate would work using the do-release-upgrade option but i don't have time to test it now.

I guess they assume your server will be online.

---

### Post by SabreWolfy on 2009-05-01
> **nandemonai said:**
> <snip>
I just tried with a 6.06 LTS VM to 8.04 LTS with the server CD.<snip>

In one step? My understanding was that it is very inadvisable to skip releases when upgrading. You would have to upgrade 6.06 to 6.10, then that to 7.04, etc. So I guess in the real world you would have to do a fresh install to get from 6.06 to 8.04, which defeats having an LTS. Or can you skip versions when using LTS server I wonder.

---

### Post by nandemonai on 2009-05-01
> **SabreWolfy said:**
> In one step? My understanding was that it is very inadvisable to skip releases when upgrading. You would have to upgrade 6.06 to 6.10, then that to 7.04, etc. So I guess in the real world you would have to do a fresh install to get from 6.06 to 8.04, which defeats having an LTS. Or can you skip versions when using LTS server I wonder.

LTS to LTS upgrades are supported. NOT by a apt-get dist-upgrade though ;)

My main point was that apt-get dist-upgrade breaks things. The do-release-upgrade method doesn't (In my experience).

---

### Post by JoshuaRL on 2009-05-01
Okay, well I guess that's a problem then.  Please be aware that if you upgrade with the Alternate CD you won't be getting the server kernel.  You always could try installing it from aptitude once you've upgraded though.

---

### Post by meganox on 2009-05-09
From [http://releases.ubuntu.com/jaunty/](http://releases.ubuntu.com/jaunty/) :-
>   The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:
  
[LIST]
[*]setting up automated deployments;
[*]**upgrading from older installations without network access;**
[*]LVM and/or RAID partitioning;
[*]installs on systems with less than about 256MB of RAM (although note that low-memory systems may not be able to run a full desktop environment reasonably).
[/LIST]
So we're sure do-release-upgrade from the alt cd is the way to go, but is it true that it will install the generic kernel?  I would have thought ubuntu-server depended on linux-image-server and that the alt cd should satisfy that dependency.

I was under the impression the different cds were more for convenience than anything else and that you could convert a desktop to a server installation by uninstalling ubuntu-desktop and installing ubuntu-server, but now I see it's not that simple; ubuntu-server isn't listed as an installable package on my desktop system.  Looks like I will be clean installing.

I think it would be simpler to have only 2 cds: Live desktop cd and an alternate cd which can install and upgrade servers.

And I definitely think swapping the optimised kernel for the generic one during what is supposed to be the official upgrade method is a bug.

---

