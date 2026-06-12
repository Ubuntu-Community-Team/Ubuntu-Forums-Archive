---
title: "is it right for me"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by degarb on 2009-12-27
I am a vector linux light user. Well kinda, installed on wife's computer.  I like their forum, where puppy had a dead unhelpful forum.  I got all to work except, I cant get linux to access xp files as it is asking me for some password that doesn't exist and no help there.

Now I have a 1.6 gighz 1 meg ram 10 gig harddrive with belkin wireless card.  I have windows me on it but not happy as it is riddled with bugs.  I want office, internet, and vlc and winamp 2 on this machine.  But neither live cds could get card working.  So shy to wipe hard drive and install linux.  I also want this to be painless and a short process that doesn't tie me down as so many things do on a computer because the designers don't do their job.

So, is this forum good for newbies?  And which version of ubuntu will work on a machine with only 10 gigs?

---

### Post by Cam42 on 2009-12-27
First off, winamp doesn't work in Linux.
Secondly, if the WiFi doesn't work in the LiveCD, it probably won't work on a local install.

---

### Post by halitech on 2009-12-27
welcome to the forum :)

This is a great place to get help as most everyone is friendly and willing to help out. 

10gigs of hard drive space will limit you some but certainly will allow you to install. Minimum amount of space required is around 4gigs so you should be fine. I'm guessing you made a typo on the amount of ram as I haven't seen a system with 1meg of ram in decades ;) Depending on the actual amount of ram you have, you should be able to run pretty much any version of Ubuntu. Open Office is available to you as is vlc but no winamp but there are equal programs that are native that will work just as well.

The wireless could be tricky but wireless is getting better all the time. If you want to try it, download a Live cd and fire it up and see if it works. If it works in the live cd then it should work after installing.

---

### Post by diablo75 on 2009-12-27
You're going to be surprised how many replies you'll get in here.  But in short, Ubuntu will meet all your needs.

Open Office for word processing, spreadsheet and presentation software (among other things) is included by default.

For Internet, you have Firefox and a wide selection of Email client software (similar to Outlook Express, but better, like Mozilla Thunderbird or Evolution).

VLC can be installed with the Add/Remove software applet, or Synaptic Package Manager, or with the command:

```
sudo apt-get install vlc
```

Winamp... well, there isn't a Winamp out there per se, but I personally use VLC for all my streaming media needs, but other killer apps like Amarok are out there.  You can also install some extra proprietary video and audio codecs with the command:

```
sudo apt-get install ubuntu-restricted-extras
```

Or, again, by clicking Applications>Add/Remove and search for "restricted extras" and you can just check it off and click apply to install.  Pretty simple.

You've got a pretty decent hardware setup with your computer so you shouldn't have any major performance issues.  If you're having video card problems you can attempt to use the Alternate installation CD instead of the Live CD.  This will load a text-based install utility that is more compatable with older hardware.

---

### Post by Leprachaun on 2009-12-27
This is a Great community for newbies with the couple of problems ive had. Ive gotten help pretty quickly.

---

### Post by degarb on 2009-12-27
Thanks.

I will google the live cd download page if You don't post in next few minutes.

Yes, 1 gig ram. (winamp 2 is about perfect; but will take replacement)  I intend to wipe harddrive and do full linux partition.  I think now, it is partitioned into two parts.  I hope that isnt a problem.  

If I can't get belkin wireless card to work, what should I buy?

---

### Post by halitech on 2009-12-27
download page - [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

you can create and delete partitions in the installer as you wish so no issues there. 1gig of ram and you will be fine to run just about anything. Once you run the live cd, if the wireless doesn't work, open a terminal and run 
```
lspci
``` and it will tell us if its possible or not.

---

### Post by Merk42 on 2009-12-27
> **degarb said:**
> Thanks.

I will google the live cd download page if You don't post in next few minutes.

Yes, 1 gig ram. (winamp 2 is about perfect; but will take replacement)  I intend to wipe harddrive and do full linux partition.  I think now, it is partitioned into two parts.  I hope that isnt a problem.  

If I can't get belkin wireless card to work, what should I buy?

The big button that says "Download" on [http://www.ubuntu.com](http://www.ubuntu.com) ....
It doesn't say LiveCD, but that's what it is.

Two partitions are not a problem, you'll just tell it to erase the disk and use all the space.

---

### Post by Leprachaun on 2009-12-27
what belkin wireless card are u using?

---

### Post by sandyd on 2009-12-27
> **degarb said:**
> Thanks.

I will google the live cd download page if You don't post in next few minutes.

Yes, 1 gig ram. (winamp 2 is about perfect; but will take replacement)  I intend to wipe harddrive and do full linux partition.  I think now, it is partitioned into two parts.  I hope that isnt a problem.  

If I can't get belkin wireless card to work, what should I buy?
is your wireless card somehwere on here?
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin)

---

### Post by diablo75 on 2009-12-27
> **degarb said:**
> Thanks.

I will google the live cd download page if You don't post in next few minutes.

Yes, 1 gig ram. (winamp 2 is about perfect; but will take replacement)  I intend to wipe harddrive and do full linux partition.  I think now, it is partitioned into two parts.  I hope that isnt a problem.  

If I can't get belkin wireless card to work, what should I buy?

If you're planing on doing a complete wipe, you'll be fine with completely removing all partitions that are on the hard drive before installing.  When installing, just select "Guided - Use Entire Drive" and it will do the rest for you.

If your wireless card doesn't work out of the box, there is a chance you can get it working using ndiswrapper.  This is an app that allows you to use Windows drivers.  There might also be some Linux based drivers available or some kind of trick done that will get your card working; it depends on the exact model number and the chipset used.  It will help you a great deal if you can use an Ethernet connection to download updates after installing.  About half the time I've setup a laptop with a wireless adapter that didn't work right away, all I had to do was apply the latest updates and the new moduals that came down the wire automatically got the card working without any further hassle.

---

### Post by degarb on 2009-12-27
> **Leprachaun said:**
> what belkin wireless card are u using?

I must say I am blown away with responses.  Thanks.  You all have proved your worth and have given me confidence to go ahead. On so many forums with geekware, the standard response is usually something less useful.

I don't have the computer now, but will check belkin card tomorrow.  I only remember Belkin 801, but that couldn't be right.

On [http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)  is the live cd also the full install and xubuntu?

---

### Post by degarb on 2009-12-27
> **carlee said:**
> is your wireless card somehwere on here?
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin)

I do know it is a pcmcia.  I will need to install updates via CD, as no ethernet pcmcia card locatable.

---

### Post by degarb on 2009-12-28
Best I can figure out in win 98 is that I have a belkin g plus chip set=4318. 

I may need this page : [http://developer.berlios.de/project/showfiles.php?group_id=4547](http://developer.berlios.de/project/showfiles.php?group_id=4547)

or this one: 
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

looks like a lot of work and going deep into linux expertise unfamiliar and alien to a windows user, without translation to windowese speak.

---

### Post by Bartender on 2009-12-28
There's also the Ubuntu HCL website

[http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)

I really like this site.  But it would be a better site if more people spent a few minutes to contribute!

I've found the user reviews at newegg can be helpful.  Linux users will often file reviews that specifically mention compatibility.

---

### Post by degarb on 2009-12-28
I am downloading xubuntu, since I now see that the hardrive is only 6 gigs.

What is downside of xubuntu?  Different or specific forum?

---

### Post by sandyd on 2009-12-28
the only difference betweeeen xubuntu and ubuntu is that xubuntu is a lighthter version.
you still get to post in the same forum, just make sure you select the [xubuntu] prefix.

---

### Post by cartisdm on 2009-12-28
> **Cam42 said:**
> First off, winamp doesn't work in Linux.
Secondly, if the WiFi doesn't work in the LiveCD, it probably won't work on a local install.

I would have to disagree.  90% of the time I run a LiveCD of any linux distro the wireless doesn't work out-of-the-box.  Generally all I have to do is enable restricted drivers or run system updates (using an ethernet cord) and I am in business.  Every release seems to make it easy and faster for me to install systems w/ working wireless so there is always hope

---

### Post by Bartender on 2009-12-28
> **cartisdm said:**
> 90% of the time I run a LiveCD of any linux distro the wireless doesn't work out-of-the-box.

+1  The LiveCD tells you if it'll work out-of-the-box, and from my limited experience even that isn't 100%.  If all it takes is an update or a download or a few quick commands to get you going you won't know that from the LiveCD.

---

### Post by degarb on 2009-12-28
> **carlee said:**
> the only difference betweeeen xubuntu and ubuntu is that xubuntu is a lighthter version.
you still get to post in the same forum, just make sure you select the [xubuntu] prefix.

I know it is lighter, but what does that entail?  Same number of drivers?  Same downloadable apps?   I am guessing it won't install some bloated ap like open office.  But will likelihood of getting hardware to work be the same?

---

### Post by Bucky Ball on 2009-12-28
Main diff desktop environment. Xfce (thus Xubuntu) and Ubuntu uses Gnome. Kubuntu uses KDE. You still access the same Ubuntu repositories so once installed you can install whatever you like. BUT some things will only work in Gnome, not Xfce. nother BUT: you can install Gnome without all the Ubuntu packages coming along with it once you are up and running in Xubuntu. 

Xubuntu doesn't take up as much space because doesn't have as many packages as Ubuntu BUT has everything you need to get going with all you want to do. Thus better for machines with lower specs. Once installed you can _*really*_ customise until your specs can take no more, then you can back off a bit. ;)

Things will become clearer as you move along the learning curve. You might like to read the 'NEVER TRIED LINUX' HOWTO in my signature.

---

### Post by lavinog on 2009-12-29
I find audacious to be a good replacement for winamp.

---

