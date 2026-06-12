---
title: "Help with DNS - Obsolete IRIX 6.2 ... HEY - dont laugh!"
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by professor-g on 2007-07-18
Dont laugh ... need help with Irix 2.6 ... hehhe (story at bottom).

Cant get DNS working ... not sure what to do.
Have tried everything.

/etc/resolv.conf

has 2 nameservers defined that I definately know work
CAN get netwrok up and running, can :
-ping selfs' IP
-ping gateway's IP
-ping the nameservers' IPs

CANNOT :
-ping anything without IPs 
(because DNS aint' working - obviously)

Please advise,

G.

The story (if you want to know):
---------------------------------------
Hard to believe people were throwing these out - they can still compute stuff - and visualise other things.
Anyways, I recently found 2 old SGI machines in the building next door to where I work ... noone wanted them - all peripherals included and working (even an old school CD drive and printer).

octane (3 CPUs), 256 MB RAM
octane 2 (2 CPUs), 512 MB RAM

Anyways, they are somewhat useful for low-level 'in silico' quantum mechanical characterisations of the molecular systems I look at.

---

### Post by tgalati4 on 2007-07-18
Octanes were great machines in their time.  A true 64-bit operating system.  You could do quad precision math which ran as fast as double precision on other machines.  Definitely a keeper.

The chassis had a funky slot configuration.  I remember that (at the time) it was difficult to get the bus to run at 200 MHz reliably.  They had to resort to an expensive, gold-pin slot configuration to reduce the capacitance of the bus that was causing throughput errors.

Set your DNS to the gateway address or to *.0 address on the subnet.  You might have to set a static IP because routers today use a slightly different DHCP protocol than was available back in the day.  You might have to use an IRIX patch (if you can find it) to get DNS to work with modern routers.

More importantly, can you get Ubuntu to run on them?

---

### Post by professor-g on 2007-07-18
Thanks for the quick reply.
Ill try the suggestion for the DNS issue.

Acknowledged and agreed - regarding the Octanes being good pieces of hardware ahead of their time.

Is it possible to get Ubuntu going on these ... ?!?
Am definately willing to try to get Ubuntu going on them - but will definately need some help.

Pretty cool computations on Traditional Chinese Medicines (TCMs) and other interesting natural systems (i.e. spider silk, among others).

Thanks,

G.

---

### Post by professor-g on 2007-07-18
It was recommended to try and get Ubuntu going on the 2 SGI Octane 'orphan 'machines I have here.
Apparently they have some of the original/first 64-bit architectures.

Would I be trying to install the 7.04 (or some other 64-bit) version ?!?
Any recommendations for what distribution I should/could install ?

They are an Octane (pre-1997) and an Octane 2 (circa ~1999-2000)

Thx.

---

### Post by tgalati4 on 2007-07-18
I would start with Dapper LTS.  The newer versions have stuff for newer hardware which will just choke on the Octane.

If Dapper fails, then I would do a google search on Debian and Octane to see if there is a decent port of Debian on the MIPs 4000/10000 platform.  You want to find the version of the chip that you have in your Octanes then find the architecture port.  Hopefully precompiled.

The alternative is to stick with IRIX and then post the things that you would like to do but can't.  I'm sure a lot of packages can compile under IRIX, but it will take a little tweaking.

Either way, it's going to take some time to get them set up.

---

### Post by doodaa on 2007-07-18
Just a shot in the dark but did you try adding the DNS machines to the hosts file too? Is NIS on? As a last resort use my favorite *nix command - man. In this case man resolver and double check that all the config files are where they should be, they weren't always in the same place from release to release in the old days.. ;) 

fwiw - I also seem remember we had some sort of trouble with Irix machines that related to the gateway address or the hostname not being entered in a configuration file... I'm fighting my oldtimers disease as best I can but it's winning today and I can't recall the exact problem.

---

### Post by tgalati4 on 2007-07-18
More importantly you need to start a DNS server and have it running on the IRIX machine so it will internally resolve addresses.  I remember setting one up and it worked fine, but I can't remember all of the config files required--I have the same old-timer's disease.

Setting up a DNS server is not difficult, but it does require reading thick manuals and setting up a few config files.

---

### Post by doodaa on 2007-07-18
> **tgalati4 said:**
> More importantly you need to start a DNS server and have it running on the IRIX machine so it will internally resolve addresses.....

I'd think this is not such a good idea? OP says he's got 2 DNSs running on the network already that he can ping. Adding a secondary on the local machine would just add to what I call "administrative burden". And there are those manuals.... :) 

If I'm getting the Google (Irix name resolution) results right,  Irix defaults to using NIS as it's name service and doesn't "autoswitch" to the DNS or local methods. You need to tell it the order in which to use nameservices. The config file location changed at version 5 and up from the earlier ones too...

---

