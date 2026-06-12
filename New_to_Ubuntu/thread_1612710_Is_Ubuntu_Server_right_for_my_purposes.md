---
title: "Is Ubuntu Server right for my purposes?"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by Prodigal Helix on 2010-11-03
Let me start off by saying that I am an IT professional, consider myself an expert, and have for years.  That being said the vast majority of my experience is with Windows based PC's, although I could do just about anything I wanted to with DOS back in the day.

Currently I have 3 PC's at home, a high end gaming desktop, a mid range gaming laptop, and a netbook that I take to school.  I also have a mid range business laptop for work, but it doesn't typically interact with my network outside of getting on the wireless for internet access.

This weekend I added to my collection an old Gateway desktop PC my mother gave to me from her office after it's HDD failed and was since replaced in its entirety.  I've been wanting to build myself a server for some time, and I figured that now is as good a time as any to try learning linux.

My goals for this machine are fairly modest I think, but my considerable lack of experience is complicating matters thoroughly, and before I wander too far in I thought I should touch base with some people that know what they're talking about and see if what I want to do is plausible.

The PC's hardware is a single core 3.2Ghz P4-HT with 2GB of DDR2 RAM and integrated audio/video/LAN/etc.  I added a 74GB Raptor for the OS HDD, and a 320GB secondary HDD for storage.  I downloaded the ISO's for both Desktop & Server of Ubuntu 10.10 x64 and last night I installed the server edition onto it.  It took some doing but I manged to find instructions to get the GUI installed as well, and shortly thereafter called it a night.

My goals for this endeavor are as follows:

1) To learn the OS, get familiar with it and be able to make it do anything I want to within the capabilities of the hardware.

2) Set up a local file server.  I want to be able to offload data from  my other machines onto this one as necessary.  Something akin to a  glorified external HDD but centralized and accessible from multiple  places simultaneously.  All of my other machines run Win7, so I'm not  sure if that means I need to format these partitions in NTFS or exactly  what's involved.

If I can stream video to my PS3/Xbox360 from this thing that would be  even better.  Something similar to the [Tversity]("http://tversity.com/") software I use on my Win7 desktop would be ideal...if it exists.

3) Set up an SSH server for secure tunneling.  Basically if I need to burn through a firewall to remote into my desktop system, or do some remote port forwarding to play online games somewhere the network has the ports  blocked.  A friend once helped me with this a couple years ago, and while I don't anticipate using it often, it's nice to have the ability, and I'm sure I'll learn a thing or two along the way.

In the future I might want to run a website, email server, MySQL database, or something else on it, once I've gotten a better feel for things, but for the moment the above is most of it.

The "server" is behind my cheap wireless router's firewall, and aside from needing to be able to accept an incoming properly authenticated ssh tunnel, won't really be seen to the outside world.  I think this negates a lot of the security concerns of many servers, but I'm really not sure.  I'm not even sure if that's possible considering the nature of the network.

Gripes:

There's nothing I can't do on a Windows box (at least anything I've ever  been inclined to do), but I'm having difficulty with even the most  basic tasks in Ubuntu.  I'm sure a lot of this is because I'm unfamiliar  with it.  For example I cannot for my life find something akin to the  windows Device Manager.  My understanding is that I still need to mount my secondary HDD, but I don't have the first idea of how to go about it, or if it's even a good idea before I start playing with Samba (I think that's what the windows file server thing is called).    It took me the better part of half an hour to  set the thing up for remote desktop, although once I got it working I've  been quite impressed with its performance.

Something annoys me to no end is the whole root/superuser setup.  I  don't like being asked for permission every time I want to change a  system setting (Disabling UAC in Win7/Vista is the first thing I do on a  new Windows install), and half the time it rejects my password which is  infuriating.   I read somewhere that Ubuntu might disable root by  default, and if that's the case how am I supposed to change anything  that requires those permissions?

The Linux "app store" seems awesome...in theory.   All kinds of free apps  for pretty much anything you can think of, that are routinely updated.    Until you actually try to find one.  I was trying to find & install  the SSH server last night, couldn't find it, and did some digging on  google.   Apparently its included on the ISO, but even popping in the  disc I didn't have the first idea of how to instruct the OS to install  it.   Did a search on the "app store" and came back with a few hundred  results, many of which were remote desktop viewing clients that support  SSH.

I understand that likely the majority of my frustration is simply from  the fact that it is so very different from what I'm accustomed to; but  in the several years I've been doing this I've always been able to teach  myself most of what I needed through trial and error, and it doesn't  seem to be working for me in this case.

Hints, tips, advice, and anything else that might be helpful is very much appreciated.

Thanks in advance!

---

### Post by Zzl1xndd on 2010-11-03
Welcome to Ubuntu.

The computer should suit your needs. Setting up Samba will be all you need to do for the File server, just when you share a folder make sure you apply the permissions to everything in the folder. 

PS3 Media Server should let you stream to your PS3.

[http://code.google.com/p/ps3mediaserver/downloads/list](http://code.google.com/p/ps3mediaserver/downloads/list)

As for the Frustrating parts it comes with time. I was/am something of a Windows guy myself as you can probably see in my Sig, but after 4 years with Ubuntu I find Windows to be the awkward OS. 

Best of Luck and I am sure you will find lots of help here in the forums.

---

### Post by cgroza on 2010-11-03
Give it a try...

---

### Post by CharlesA on 2010-11-03
> **Prodigal Helix said:**
> 
The PC's hardware is a single core 3.2Ghz P4-HT with 2GB of DDR2 RAM and integrated audio/video/LAN/etc.  I added a 74GB Raptor for the OS HDD, and a 320GB secondary HDD for storage.  I downloaded the ISO's for both Desktop & Server of Ubuntu 10.10 x64 and last night I installed the server edition onto it.  It took some doing but I manged to find instructions to get the GUI installed as well, and shortly thereafter called it a night.

If you are just starting out, you can probably just install Ubuntu Desktop and learn the OS first instead of jumping head first in the terminal.

> My goals for this endeavor are as follows:

1) To learn the OS, get familiar with it and be able to make it do anything I want to within the capabilities of the hardware.

You can do it. Linux is very versatile in that respect.

> 2) Set up a local file server.  I want to be able to offload data from  my other machines onto this one as necessary.  Something akin to a  glorified external HDD but centralized and accessible from multiple  places simultaneously.  All of my other machines run Win7, so I'm not  sure if that means I need to format these partitions in NTFS or exactly  what's involved.

You'd need to use Samba to share with a Windows machine. It's easy to install, but can be a bit of a pain to configure. There's a ton of howtos around for that tho.

> If I can stream video to my PS3/Xbox360 from this thing that would be  even better.  Something similar to the [Tversity]("http://tversity.com/") software I use on my Win7 desktop would be ideal...if it exists.

I'd say go for PS3mediaserver, works great. :)

> 3) Set up an SSH server for secure tunneling.  Basically if I need to burn through a firewall to remote into my desktop system, or do some remote port forwarding to play online games somewhere the network has the ports  blocked.  A friend once helped me with this a couple years ago, and while I don't anticipate using it often, it's nice to have the ability, and I'm sure I'll learn a thing or two along the way.

While we don't support using SSH to bypass firewalls, it can be a great tool for encrypting yer internet traffic.

> In the future I might want to run a website, email server, MySQL database, or something else on it, once I've gotten a better feel for things, but for the moment the above is most of it.

Google is yer friend. It will give you a place to start at least, since there are many ways to go about installing and configuring those services.

> The "server" is behind my cheap wireless router's firewall, and aside from needing to be able to accept an incoming properly authenticated ssh tunnel, won't really be seen to the outside world.  I think this negates a lot of the security concerns of many servers, but I'm really not sure.  I'm not even sure if that's possible considering the nature of the network.

As long as you secure SSH, and only have that open to the internet, you'll be fine.


> There's nothing I can't do on a Windows box (at least anything I've ever  been inclined to do), but I'm having difficulty with even the most  basic tasks in Ubuntu.  I'm sure a lot of this is because I'm unfamiliar  with it.  For example I cannot for my life find something akin to the  windows Device Manager.  My understanding is that I still need to mount my secondary HDD, but I don't have the first idea of how to go about it, or if it's even a good idea before I start playing with Samba (I think that's what the windows file server thing is called).    It took me the better part of half an hour to  set the thing up for remote desktop, although once I got it working I've  been quite impressed with its performance.

I don't think there is really a "all-in-one" device management tool for Ubuntu, but I could be wrong, since I don't really use the desktop edition all that much.

You can find info about disks by running this:

```
sudo fdisk -l
```

Then add an entry to [fstab]("https://help.ubuntu.com/community/Fstab") where you want it to be mounted.

> Something annoys me to no end is the whole root/superuser setup.  I  don't like being asked for permission every time I want to change a  system setting (Disabling UAC in Win7/Vista is the first thing I do on a  new Windows install), and half the time it rejects my password which is  infuriating.   I read somewhere that Ubuntu might disable root by  default, and if that's the case how am I supposed to change anything  that requires those permissions?

Ubuntu has the root account disabled by default and uses "sudo" to perform admin tasks.

You can modify the sudoers file to not prompt for the password, but I'd recommend against it - being prompted for yer password makes you take a moment to think about what you are about to do.

See [here]("https://help.ubuntu.com/community/RootSudo").

> The Linux "app store" seems awesome...in theory.   All kinds of free apps  for pretty much anything you can think of, that are routinely updated.    Until you actually try to find one.  I was trying to find & install  the SSH server last night, couldn't find it, and did some digging on  google.   Apparently its included on the ISO, but even popping in the  disc I didn't have the first idea of how to instruct the OS to install  it.   Did a search on the "app store" and came back with a few hundred  results, many of which were remote desktop viewing clients that support  SSH.

Most stuff is included in the online repositories and not on the ISO. You can just point and click to install it.

Normally if you are going to tunnel RDP or VNC over SSH, you create the tunnel first and point the client to localhost.

> I understand that likely the majority of my frustration is simply from  the fact that it is so very different from what I'm accustomed to; but  in the several years I've been doing this I've always been able to teach  myself most of what I needed through trial and error, and it doesn't  seem to be working for me in this case.

The only way to really learn is to play around with it, make mistakes and learn from them.

---

### Post by arpanaut on 2010-11-03
> I read somewhere that Ubuntu might disable root by  default, and if  that's the case how am I supposed to change anything  that requires  those permissions?[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

First things first, Read the link above, learn it, get used to it!
In the long run it will make things easier on you and for all of us trying to help too.
Permissions and passwords are the linux way, that's why it works so much better and securely in a multi-user and networked environment.

Most all you want to do can be done, the learning curve is steep but really not so hard if you accept and embrace the conventions of Linux, and not expect things to work "like" they do in windows.

---

### Post by bioterror on 2010-11-03
> **Prodigal Helix said:**
> Let me start off by saying that I am an IT professional, consider myself an expert, and have for years.  That being said the vast majority of my experience is with Windows based PC's, although I could do just about anything I wanted to with DOS back in the day.

Currently I have 3 PC's at home, a high end gaming desktop, a mid range gaming laptop, and a netbook that I take to school.  I also have a mid range business laptop for work, but it doesn't typically interact with my network outside of getting on the wireless for internet access.

This weekend I added to my collection an old Gateway desktop PC my mother gave to me from her office after it's HDD failed and was since replaced in its entirety.  I've been wanting to build myself a server for some time, and I figured that now is as good a time as any to try learning linux.

My goals for this machine are fairly modest I think, but my considerable lack of experience is complicating matters thoroughly, and before I wander too far in I thought I should touch base with some people that know what they're talking about and see if what I want to do is plausible.

The PC's hardware is a single core 3.2Ghz P4-HT with 2GB of DDR2 RAM and integrated audio/video/LAN/etc.  I added a 74GB Raptor for the OS HDD, and a 320GB secondary HDD for storage.  I downloaded the ISO's for both Desktop & Server of Ubuntu 10.10 x64 and last night I installed the server edition onto it.  It took some doing but I manged to find instructions to get the GUI installed as well, and shortly thereafter called it a night.


Usually Pentium 4 is 32bit, but Prescott can perform as 64bit, if I'm remembering right. But as you're having only 2GB of ram, there's really no huge benefit for the X64 version of Ubuntu.

> 
My goals for this endeavor are as follows:

1) To learn the OS, get familiar with it and be able to make it do anything I want to within the capabilities of the hardware.


You really should have read this url in the first place, it explains a lot.
[https://help.ubuntu.com/10.10/serverguide/C/index.html]("https://help.ubuntu.com/10.10/serverguide/C/index.html")

> 
2) Set up a local file server.  I want to be able to offload data from  my other machines onto this one as necessary.  Something akin to a  glorified external HDD but centralized and accessible from multiple  places simultaneously.  All of my other machines run Win7, so I'm not  sure if that means I need to format these partitions in NTFS or exactly  what's involved.

If I can stream video to my PS3/Xbox360 from this thing that would be  even better.  Something similar to the [Tversity]("http://tversity.com/") software I use on my Win7 desktop would be ideal...if it exists.


[https://help.ubuntu.com/10.10/serverguide/C/samba-ldap.html]("https://help.ubuntu.com/10.10/serverguide/C/samba-ldap.html") explains about samba and how to configure it.

If you want to watch movies/photos or what so ever with your PS3 (xbox360 likes media player becouse of the codecs) from your Ubuntu server, you really should consider running a UPnP server, like [http://mediatomb.cc/]("http://mediatomb.cc/") or just use plain samba shares like I do.

> 
3) Set up an SSH server for secure tunneling.  Basically if I need to burn through a firewall to remote into my desktop system, or do some remote port forwarding to play online games somewhere the network has the ports  blocked.  A friend once helped me with this a couple years ago, and while I don't anticipate using it often, it's nice to have the ability, and I'm sure I'll learn a thing or two along the way.


Command to do this is: ```
sudo apt-get install openssh-server

```

That's explained in the URL I provided earlier ;)

> 
In the future I might want to run a website, email server, MySQL database, or something else on it, once I've gotten a better feel for things, but for the moment the above is most of it.


So, you're interested to try LAMP (Linux Apache MySQL PHP)
My dear mentor PhillW has made an awesome guide for this [https://wiki.edubuntu.org/phillw/draft]("https://wiki.edubuntu.org/phillw/draft")

> 
The "server" is behind my cheap wireless router's firewall, and aside from needing to be able to accept an incoming properly authenticated ssh tunnel, won't really be seen to the outside world.  I think this negates a lot of the security concerns of many servers, but I'm really not sure.  I'm not even sure if that's possible considering the nature of the network.


As you gain more experience with Ubuntu Server Edition, you really should consider changing your router from NAT mode to bridged and use your server as your Firewall/Router/DNS/NAT and everything what you can dream about.

More information about that can be found from here [http://bodhizazen.net/Tutorials/iptables/]("http://bodhizazen.net/Tutorials/iptables/")

> 
Gripes:

There's nothing I can't do on a Windows box (at least anything I've ever  been inclined to do), but I'm having difficulty with even the most  basic tasks in Ubuntu.  I'm sure a lot of this is because I'm unfamiliar  with it.  For example I cannot for my life find something akin to the  windows Device Manager.  My understanding is that I still need to mount my secondary HDD, but I don't have the first idea of how to go about it, or if it's even a good idea before I start playing with Samba (I think that's what the windows file server thing is called).    It took me the better part of half an hour to  set the thing up for remote desktop, although once I got it working I've  been quite impressed with its performance.


More information shared to us by Bodhi [http://bodhizazen.net/Tutorials/Understandingfstab.pdf]("http://bodhizazen.net/Tutorials/Understandingfstab.pdf")

> 
Something annoys me to no end is the whole root/superuser setup.  I  don't like being asked for permission every time I want to change a  system setting (Disabling UAC in Win7/Vista is the first thing I do on a  new Windows install), and half the time it rejects my password which is  infuriating.   I read somewhere that Ubuntu might disable root by  default, and if that's the case how am I supposed to change anything  that requires those permissions?


I'm really sorry for providing urls, but those questions are explained well already. I dont have to invent a wheel again ;)
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

> 
The Linux "app store" seems awesome...in theory.   All kinds of free apps  for pretty much anything you can think of, that are routinely updated.    Until you actually try to find one.  I was trying to find & install  the SSH server last night, couldn't find it, and did some digging on  google.   Apparently its included on the ISO, but even popping in the  disc I didn't have the first idea of how to instruct the OS to install  it.   Did a search on the "app store" and came back with a few hundred  results, many of which were remote desktop viewing clients that support  SSH.

I understand that likely the majority of my frustration is simply from  the fact that it is so very different from what I'm accustomed to; but  in the several years I've been doing this I've always been able to teach  myself most of what I needed through trial and error, and it doesn't  seem to be working for me in this case.

Hints, tips, advice, and anything else that might be helpful is very much appreciated.

Thanks in advance!

Ahh, awesome to hear that you already enjoy the fruits of opensource software which is easily downloadable from the servers. One best thing about Linux compared to Windows is that, those softwares are managed with package manager and you really dont have to upgrade them manually, like in windows. You just update your repository and let the manager check if there's anything to update. 

And once again, welcome and I hope you really enjoy your Linux/Ubuntu journey with us.

If you have anything else in your mind, don not hesitate to ask.

---

### Post by Megaptera on 2010-11-03
Hi Prodigal Helix,
i'm no expert but I've various links I find useful, I hope they're a help to you too:

Lots of links within this link & some useful basic commands:
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

Other stuff:
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)  why not to disable!!

Loads of desktop tutorials but no index despite excellent screenshot sequences:
[http://www.liberiangeek.net/](http://www.liberiangeek.net/)

---

### Post by CharlesA on 2010-11-03
> **bioterror said:**
> 
If you want to watch movies/photos or what so ever with your PS3 (xbox360 likes media player becouse of the codecs) from your Ubuntu server, you really should consider running a UPnP server, like [http://mediatomb.cc/]("http://mediatomb.cc/") or just use plain samba shares like I do.


A PS3 will play stuff from a Samba share? I always had to use PS3media server for it to be able to see the media.

---

### Post by bioterror on 2010-11-03
> **CharlesA said:**
> A PS3 will play stuff from a Samba share? I always had to use PS3media server for it to be able to see the media.

Well, I might be wrong. (I'm a NMT user myself, I dont want my kids to play games ;)

I had to google and I stand corrected! ;D

---

### Post by 3Miro on 2010-11-03
If you really want to learn the "under the hood" workings of Linux, learn the terminal and its commands. An experienced user can be more efficient with the terminal than a graphical tool. Furthermore, the shell is independent of the distribution, if you know the shell in Ubuntu, you pretty much know all the distributions.

Also, a good first step is to stop using the Ubuntu Software Center and start using Synaptic Package Manager. The USC is deliberately designed to shield you from some things, if you want to learn use SPM.

---

### Post by Prodigal Helix on 2010-11-03
Much thanks for all the replies thus far.  I have done some searching and looked at some stickies, but the things that I had found didn't really seem to apply at what I was looking for.  Some of those that you all have posted seem more on target so far, what few I've been able to look at anyway.

> As you gain more experience with Ubuntu Server Edition, you really  should consider changing your router from NAT mode to bridged and use  your server as your Firewall/Router/DNS/NAT and everything what you can  dream about.

More information about that can be found from here [http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

This hadn't even occurred to me, but just made it onto my list of things I want to do with the server.  That's just crazy awesome.

---

### Post by CharlesA on 2010-11-03
Just a note on the whole "one server for everything" thing - if you do decide to use it as a network gateway, and it gets compromised, you've put all yer eggs in one basket, so to speak.

I've thought of doing that before and just stuck with my normal router flashing with DD-WRT to do NAT and the normal server for everything else.

---

### Post by Prodigal Helix on 2010-11-03
Good to know that there's an available option for streaming to the PS3, but nothing for the Xbox360?  The 360 will play just about everything the PS3 will (DivX, etc. I avoid media player like the plague), my Win7 box currently streams to both using the same server app and I'm really hoping to be able to do so with the server as they're connected to different TV's in different rooms.

Although I suppose I could just keep running my current app from the desktop and point it to the network drive on the server.

---

### Post by Prodigal Helix on 2010-11-03
> **CharlesA said:**
> Just a note on the whole "one server for everything" thing - if you do decide to use it as a network gateway, and it gets compromised, you've put all yer eggs in one basket, so to speak.

I've thought of doing that before and just stuck with my normal router flashing with DD-WRT to do NAT and the normal server for everything else.

Is a linux server acting as the router somehow more likely or able to be compromised than my $40 Netgear router?  I've thought about replacing the firmware on my router previously, but I don't think this particular one has the capability, and am still very much a linux novice.

---

### Post by CharlesA on 2010-11-03
> **Prodigal Helix said:**
> Is a linux server acting as the router somehow more likely or able to be compromised than my $40 Netgear router?  I've thought about replacing the firmware on my router previously, but I don't think this particular one has the capability, and am still very much a linux novice.

You can always check the router database on [www.dd-wrt.com](www.dd-wrt.com) to see if yer router supports it.

In a perfect world, if you had no services listening on the external interface, it would be safe, but it's still a matter of putting all yer eggs in one basket.

Note: The multiquote and edit buttons are yer friend. :)

---

### Post by Prodigal Helix on 2010-11-03
> **CharlesA said:**
> You can always check the router database on [www.dd-wrt.com]("http://www.dd-wrt.com") to see if yer router supports it.

In a perfect world, if you had no services listening on the external interface, it would be safe, but it's still a matter of putting all yer eggs in one basket.

Note: The multiquote and edit buttons are yer friend. :)

I checked and my router is listed as in the works, so I'll have to keep my eye on that.

I'm still not quite getting the "all your eggs..." thing though.  Presently my router listens on a couple of ports and forwards them to my desktop, RDP, a couple online games, bit torrent, etc.  What makes it any less vulnerable than the server running the NAT/DHCP/Firewall with similar settings?

Apologies for the naivete, I don't want to take unnecessary risks, I just don't understand the difference at the moment.

---

### Post by CharlesA on 2010-11-03
It would work fine if you are running NAT/DHCP/DNS/firewall.

It starts to get iffy once you add stuff like VMs, Samba, FTP, Apache, etc.

Does that make sense now?

If I was going to use a dedicated machine for a firewall/router, I'd use something like Smoothwall, IPcop, or pfSense instead of Ubuntu, but that's just me.

---

### Post by Prodigal Helix on 2010-11-03
Oh okay, that makes sense now.  I hadn't been thinking in those terms.

Such a different way of looking at things hehe...

---

### Post by bioterror on 2010-11-03
> **CharlesA said:**
> 
If I was going to use a dedicated machine for a firewall/router, I'd use something like Smoothwall, IPcop, or pfSense instead of Ubuntu, but that's just me.

My word goes for the pfSense.
Loving it, but I've migrated from FreeBSD to pfSense as I'm not running a shell machine at my home anymore.

I've tried most of the linux competitors, but I've never liked them as much as pfSense.

And [http://www.zentyal.com/en/products/server/]("http://www.zentyal.com/en/products/server/") this is too interesting, tried it but I had some problems with dns in my homenetwork, other wise it was a gift from the god himself :D

---

### Post by CharlesA on 2010-11-03
> **Prodigal Helix said:**
> Oh okay, that makes sense now.  I hadn't been thinking in those terms.

Such a different way of looking at things hehe...

If you've got any more questions, feel free to post them. :)

@bioterror: From my limited work with pfSense, I like it better then some of the others. If I ever decided to get rid of my crappy Dlink router, I'm going to be running that.

---

### Post by Prodigal Helix on 2010-11-03
> **3Miro said:**
> If you really want to learn the "under the hood" workings of Linux, learn the terminal and its commands. An experienced user can be more efficient with the terminal than a graphical tool. Furthermore, the shell is independent of the distribution, if you know the shell in Ubuntu, you pretty much know all the distributions.

Also, a good first step is to stop using the Ubuntu Software Center and start using Synaptic Package Manager. The USC is deliberately designed to shield you from some things, if you want to learn use SPM.

So I'm trying to use the Synaptic Package Manager and it keeps asking for my password.  I provide it, but doesn't accept it.  I pulled up the documentation here [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto) and it doesn't say anything about prompting for a password to launch it.  I'm guessing that it's asking for the root password, but as the root account is disabled...how exactly should I proceed?

---

### Post by CharlesA on 2010-11-03
> **Prodigal Helix said:**
> So I'm trying to use the Synaptic Package Manager and it keeps asking for my password.  I provide it, but doesn't accept it.  I pulled up the documentation here [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto) and it doesn't say anything about prompting for a password to launch it.  I'm guessing that it's asking for the root password, but as the root account is disabled...how exactly should I proceed?

You would enter the password you use for your user account. That's cause the sudo password, which is what Ubuntu uses instead of the root account.

3Miro is right, Software center is a bit more "we'll just install whatever you select and don't tell you all the "behind the scenes" stuff, where Synaptic will tell you what's going on.

The same is said for apt-get.

---

