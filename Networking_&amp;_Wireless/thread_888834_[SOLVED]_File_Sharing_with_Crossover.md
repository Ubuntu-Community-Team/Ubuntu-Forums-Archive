---
title: "[SOLVED] File Sharing with Crossover"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by irishdunn on 2008-08-13
About 3 weeks ago I discovered that I really loved Linux, since then I built another machine with a 2TB Raid 5 Array.

Both my Desktop and my Raid Array have 2x1000MB NIC's, so I bought 2 of the most expensive 7 foot crossover cables I could find... Thinking that I would be in file sharing heaven.

My question is regarding this specific setup:

 [IMG]http://img29.picoodle.com/img/img29/3/8/13/f_Testm_519a06a.jpg[/IMG]

I set up samba on the RAID Box, and I can connect to it from both the laptop and the Main Box... however my transfers between RAID Box and Main Box always happen over wireless. I dont think that I set up the wired networking properly, and I dont know if there is a way to force traffic through a specific interface.

Ideally I would like to force all transfers between RAID Box and Main Box through either of the Gigabit network interfaces.:KS

Thanks in advance!

---

### Post by jimv on 2008-08-13
You need to add a route to the machines so that any traffic between them uses the gigabit nic.  I think the command is like this, but someone can correct me if I'm wrong:

route add -net 192.168.0.0 netmask 255.255.255.0 dev eth0

OR

route add -net <address-for-other-machine> netmask <subnetmask> dev <gigabit-NIC>

EDIT:  Routes aren't persistent, so if you reboot, you'll have to re-enter them unless you put them in your /etc/network/interfaces file.  Here's a thread:
[http://ubuntuforums.org/showthread.php?p=217263](http://ubuntuforums.org/showthread.php?p=217263)

---

### Post by irishdunn on 2008-08-13
Would it be possible to use machine names, like FILEBEAST.LOCAL, instead of using a specific address?

Also, since there is 2 NIC's present, can I set up some load balancing? Dont know if I would need to, but the files I am sending back and forth are quite large ~>4GB


Thanks for the quick reply!

---

### Post by irishdunn on 2008-08-14
Ok I have a question regarding the setup of this environment.

This is what I did last night:

Main Box:
    NIC 1: 192.168.7.2 GW 192.168.7.1
    NIC 2: 192.168.7.3 GW 192.168.7.1
    WLAN: 192.168.1.8 GW 192.168.1.1

RAID Box:
    NIC 1: 192.168.7.4 GW 192.168.7.1
    NIC 2: 192.168.7.5 GW 192.168.7.1
    WLAN: 192.168.1.7 GW 192.168.1.1

Then I tried to add routes in my /etc/network/interfaces file

On Main Box:
    up route add -host 192.168.7.4 gw 192.168.7.1 dev eth0

On RAID Box:
    up route add -host 192.168.7.2 gw 192.168.7.1 dev eth0

but then I couldn't even ping each box :(

Please help!

---

### Post by bab1 on 2008-08-14
I believe if you use the 4 port switch and straight cabling (not X-over) built into the router, all the hosts will see each other.  It's unfortunate that the switch is ony 100 Mb/s but it will work.

---

### Post by irishdunn on 2008-08-14
The issue is not seeing eachother, I can do that through the crossover cables just fine. What I want to do is make sure that when I access the RAID Box, I do it over the Gigabit connection and not through the wireless connection.

---

### Post by bab1 on 2008-08-14
And you know this is not happening?

---

### Post by irishdunn on 2008-08-14
I believe it is defaulting to communicate over the wlan connections, I experience transfer rates at max of 1Mb... sometimes worse.

When I initially setup the environment I was streaming 10GB 1080P movies to my Main Box with no issues, but that was before I had the wlan's enabled.

I dont know for sure, that this is occurring... it is my hunch from the details above.

---

### Post by bab1 on 2008-08-14
So you are using an application and allowing it to find any IP address it wants?  BTW you can use name.local on the LAN -- Not the internet.

---

### Post by irishdunn on 2008-08-14
Maybe this is just as simple as mapping the drive off properly, previously I had been going into System>Network to find the Raid Box...

What is the proper way to map the Drive off, the system is named FILEBEAST, so I am assuming I will be Mapping by FILEBEAST.LOCAL

Even with doing this, wont I have to establish route's on each of the machines to tell them to communicate using eth0 or eth1?

---

### Post by bab1 on 2008-08-14
Well, where do I start?  The router can find it's own route.  You normally don't have to do that.  Mapping a drive is a windows term, do you browse to the files?  Are you using Samba?  Why the need for 2 NIC's?

---

### Post by irishdunn on 2008-08-14
> **bab1 said:**
> Well, where do I start?  The router can find it's own route.  You normally don't have to do that.  Mapping a drive is a windows term, do you browse to the files?  Are you using Samba?  Why the need for 2 NIC's?

Popping off the stack:

Two NIC's is a novelty, I will ofcourse be using a single one right now for sharing, but there is no LAN in my current apartment. I am only connected through wireless to the outside world. In the future one NIC on each machine will be connected to the LAN while the second NIC will be used for transfer between the two devices. Essentially RAID Box is an extension of MAIN Box, I wish to run all my VM's and all my media through RAID Box, while using Main Box as my gaming/surfing/email/etc. machine.

I am using Samba, I am new to linux so I didnt know of any other alternative... Main Box is a dual boot system, there is a need to access the resources of RAID Box from windows machines. 

I am unfamiliar with file sharing in Linux, so pardon my jargon. I have been browsing to the machine through System>Network, I don't know how to access the machine directly... like how you would with windows explorer's address bar: '//Machine'

I would like to do this using the X-Over cables instead of buying a gigabit switch or router... which I will do in the future, but don't wish to right now.

---

### Post by bab1 on 2008-08-14
> two NIC's is a novelty, I will ofcourse be using a single one right now for sharing, but there is no LAN in my current apartment. I am only connected through wireless to the outside world. In the future one NIC on each machine will be connected to the LAN while the second NIC will be used for transfer between the two devices.
Ahhhh, but you do have a LAN.  The LAN you have is your own with your 3 hosts (machines).  You should think of it in that way.  Outside of that is either a WAN or if it is just building wide, a MAN.
IMHO, you are only creating needless complications with the multi-homed hosts (multiple NIC's).  See if you can bond the 2 gig NIC's together if you want more bandwidth.  You would have to do that at both ends (hosts).

> Essentially RAID Box is an extension of MAIN Box, I wish to run all my VM's and all my media through RAID Box, while using Main Box as my gaming/surfing/email/etc. machine.
Think of it more as if you have created a NAS without it appearing as a NAS on you LAN.  I would not run any visualization on this host just yet.

> am unfamiliar with file sharing in Linux, so pardon my jargon. I have been browsing to the machine through System>Network,

When you use Samba via the GUI it's not fully configured (soft mount of the partitions).  I never used the GUI, But I do use Samba. You will be better served and will learn a lot by manually configuring your system.  Besides yours is an unusual configuration.

[COLOR="DarkGreen"]I feel like I am letting you down here, but I also feel you will not have success until you use a switch in your LAN.  Every time I try and come up with a solution it ends due to the lack of the switch.  I recommend you use the switch in your wireless router to setup the system and swap it out for a gig switch later.  If you do that you can make the RAID a full Samba server with proper shares.[/COLOR]

---

### Post by irishdunn on 2008-08-14
You are saying there is no way that I can share files between RAID Box and Main Box without purchasing a mitigation layer? I thought that using crossover cables with two computers was a perfectly legit way to transfer files.

I would like RAID Box to know when it is accessed from a specific machine:

From laptop: use wlan0 (this is the only option because the laptop is not connected via crossover)

From Main box: use eth0 (this is a crossover connection between the two machines)

And likewise would like Main Box to know when it wants to browse to RAID Box, it should use a specific interface.

It seems like setting up routes would do this, but I am not familiar enough with routing to know how to properly set this up.


The router in question is inaccessible by cable for me, and I do not wish to purchase another router.

Sorry if I am making this difficult, it is a peculiar situation and I do appreciate you working with me through this.

---

### Post by bab1 on 2008-08-14
Right off the bat; are you saying you don't administrate (control) the wireless router in your drawing?

> From laptop: use wlan0 (this is the only option because the laptop is not connected via crossover)

One of the reasons for the switch.  Also we can't remove the wlan0 from the RAID box.

> And likewise would like Main Box to know when it wants to browse to RAID Box, it should use a specific interface.
Maybe through careful configuration of Samba.

I'll help if I can but I feel we should not bang our heads against the wall needlessly.  :D

---

### Post by irishdunn on 2008-08-14
I control the wireless router, its a novel situation:

I moved to a new city for an internship, I moved into a loft above a coffee shop and offered the owners of the shop to assist with all of their computers if they would let me use the wireless. Turned out that they had hired a contractor to set everything up and had not heard from him since, so I went in and cleaned everything up and now I control their network. :)

I would really like to take advantage of these crossover cables, the intention was to be able to move this little set of machines anywhere and get the same functionality.

I know I could easily set this up using a router, I just like the idea of using these crossovers...

How would buying a router/switch: [I have one of these at a Business I consult for]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833124091") be any different then using these crossovers?

I would still be up against the issue of specifying which interface I wanted the machines to use when they were communicating.

---

### Post by bab1 on 2008-08-14
Two things come to mind.  First your x-over cables create a switch; but it only has 1 port!  Lets define the terms:
Router = routes packets between different networks (it can even be 2 LAN's)
Switch = replicates the incoming packets on ALL other ports. Creates 1 to 1 conversations between the NAMED (or addressed) hosts.  At this time you don't need a router, just a cheap switch.

Your problem (and reluctance) might be: How do I get the cable from the coffee shop to my loft?  Yes...?  The switch does not have to be an expensive one.  You can get a 4 port switch for under $20.  I have one holding the door open to my porch :D (just kidding)

You still can do the moving bit and you will (should) always use a switch when you have multiple hosts.  If you still do not want to get a switch, then string 3 wires up to the loft!

You can bind Samba to a specific IP address and therefore DNS names.  See[[COLOR="Magenta"]here[/COLOR]]("http://samba.org/~tpot/articles/multiple-interfaces.html").

Edit:  If you really can't string cable, then think about a wireless extender (AP).  The you would have a port to the router in your loft.

---

### Post by irishdunn on 2008-08-14
The interfaces thing looks like exactly what I need to do. Now I set up the share by right clicking on the folder in gnome and enabling share... that did not add an entry in my smb.conf....

so i disabled that.

---

### Post by bab1 on 2008-08-14
Correct on both counts.  You need to manually configure Samba.  Not  baby GUI Samba.  It's all in the setup of the smb.conf file and proper positioning of the mounted directories.  I use /smb as the basic starting point.  I have /smb/home and /smb/public and /smb/backup.  

Just one last question, how many partitions do you have on your raid array.  If there is only one then no biggie.  I made a partition only for /smb.  Everything else is on different partitions.  

You can do as you wish about the switch later.

Good luck.

---

### Post by irishdunn on 2008-08-14
When trying: smbclient //localhost/username and my password

I get this:

tree connect failed: NT_STATUS_BAD_NETWORK_NAME


Any Ideas? Would you like me to post my smb.conf?

---

### Post by bab1 on 2008-08-14
Don't post it for me.  I think at this point you should acquaint yourself with the documentation for Samba.  Read it all.  This is all a learning process. Then come back and ask questions about details.

Edit: Maybe that's a little harsh.  But I think you should have specific questions or at the least be able to tell us what you did and what your configuration is like.  Nobody likes to look at 100's of lines of meaningless conf files to get at a problem.

---

### Post by jimv on 2008-08-15
> **irishdunn said:**
> Ok I have a question regarding the setup of this environment.

This is what I did last night:

Main Box:
    NIC 1: 192.168.7.2 GW 192.168.7.1
    NIC 2: 192.168.7.3 GW 192.168.7.1
    WLAN: 192.168.1.8 GW 192.168.1.1

RAID Box:
    NIC 1: 192.168.7.4 GW 192.168.7.1
    NIC 2: 192.168.7.5 GW 192.168.7.1
    WLAN: 192.168.1.7 GW 192.168.1.1

Then I tried to add routes in my /etc/network/interfaces file

On Main Box:
    up route add -host 192.168.7.4 gw 192.168.7.1 dev eth0

On RAID Box:
    up route add -host 192.168.7.2 gw 192.168.7.1 dev eth0

but then I couldn't even ping each box :(

Please help!

I don't know why that bab1 guy who was "helping" was so cranky, but I think we can go back to what we were doing here.

You don't need a gateway on any of the gigabit adapters, since a gateway is only for connecting to another network, like the internet.
So take that part out.

Then use this command to add the routes:

Main box:
up route add -net 192.168.7.4 netmask 255.255.255.0 dev eth0

RAID box:
up route add -net 192.168.7.2 netmask 255.255.255.0 dev eth0

---

### Post by irishdunn on 2008-08-15
Thanks for your quick reply, I first have to resolve the samba issues I am having... but unfortunately I have to help a buddy move this weekend so I wont get any time with my little farm here.

First thing sunday night I will resolve the samba thing, then I would greatly appreciate the help with routing.

---

### Post by bab1 on 2008-08-15
jimv,

Not cranky at all.  I think advice is great.  hand holding is not my bag.  Irishdunn is correct.  He needs to do some reading on how Samba works so he can ask direct questions.  I will help.  I'm just not into: [COLOR="DarkOrchid"]"what do I do now?"[/COLOR].  ;-)

irishdunn,

Don't be afraid to ask questions and even post PARTS of your smb.conf file if needed.  Make it more specific.  As a suggestion, I made a copy of my smb.conf file.  i called it smb.conf.orig.  Then I hacked off the stuff that wasn't needed.

---

### Post by jimv on 2008-08-15
@irishdunn

Cool.  And something else for you to tinker with...look up "Ubuntu NIC bonding" on Google.  Basically makes two NICs act as one NIC...which seems like it would be awesome for two gigabit NICs.

@bab1

It's fine if you don't want to hold someone's hand or walk them through something.  You don't have to.  But don't chastise someone who does want that kind of help, because there are plenty of us on the board who don't mind.

---

### Post by bab1 on 2008-08-15
jimv,

I neither criticized nor reprimanded irishdunn.  You are the one who sees that.  You also never bothered to read all the posts.  I mentioned bonding in post #13.   Take a chill pill and lighten up.

---

### Post by y@w on 2008-08-15
If you're concerned about performance and both machines are Linux, there's no way I'd run Samba to connect them. Use NFS. If you're pushing large files back and forth you'll notice a difference. Plus, it's much easier to configure.

---

### Post by irishdunn on 2008-08-19
> **y@w said:**
> If you're concerned about performance and both machines are Linux, there's no way I'd run Samba to connect them. Use NFS. If you're pushing large files back and forth you'll notice a difference. Plus, it's much easier to configure.

I set up NFS last night and it does everything that I wanted:

Access over specified interfaces
Very fast communication (from the Raid5 array to my Raptor 10k I get around 60M/s sustained read)
supposedly very secure, because I specified the interfaces... they are local to the machine so someone would have to plug into my box to get access...


I would like to restrict by user, buy I couldn't get that to work last night and I just wanted to get access to my media ASAP.

I think that I will still set up samba to make a couple of read only shares for people who come over to nab files from me.


thanks a ton, all of you.

---

