---
title: "Samba fails to start at boot"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by Alien.col on 2008-04-03
Hello:

I'm using a gutsy 64 bit installation. I recently enabled "show text during bootusing the start-up manager tool. Everything goes fine until it says the following:

[INDENT]* Starting Samba daemons                                                [ FAILED ] frequency scaling not supported[/INDENT]

I got a USB wireless card that works well with the rt2570 drivers. 

After I log in I use this command at the terminal:

[INDENT]
sudo /etc/init.d/samba start

 * Starting Samba daemons                                                [ OK ] 
[/INDENT]

Any ideas what's going on, should I worry?

Thanks

---

### Post by njparton on 2008-04-03
Is the samba daemon ticked under Administration > Services?

---

### Post by Alien.col on 2008-04-03
Yes sir, its ticked.

> **njparton said:**
> Is the samba daemon ticked under Administration > Services?

---

### Post by njparton on 2008-04-03
The "frequency scaling not supported" bit is confusing as that sounds like it's related to your CPU.  What hardware do you have?

---

### Post by Alien.col on 2008-04-03
That message appears at the same time that the Samba daemons fail to start. 

I recently had to uninstall NFS, now that I remember, because Ubuntu was taking like 5 minutes to boot. I think that nfs was attempting to establish some connections at boot up with some ips that were not present, so i decided to uninstall the nfs-common package. Ubuntu booted fine after that. 

My Hardware:
MSI K8N Neo4 Platinum Motherboard wth nvidia nforce4 chipset
AMD Athlon 64 3500+ (socket 939 venice)
2 Gb Kingston PC3200 RAM 
ATI RAdeon x1600 pro 512 mb Video Card

> **njparton said:**
> The "frequency scaling not supported" bit is confusing as that sounds like it's related to your CPU.  What hardware do you have?

P.S. I'm using the 64 bit version of linux.

---

### Post by Eiríkr on 2008-04-03
Have a look in your /var/log/syslog file for any mention of strangeness during boot.  Also have a look at your /var/log/samba/log.smbd file for messages specific to the Samba daemon.

Cheers,

Eiríkr

---

### Post by Alien.col on 2008-04-03
> **Eiríkr said:**
> Have a look in your /var/log/syslog file for any mention of strangeness during boot.  Also have a look at your /var/log/samba/log.smbd file for messages specific to the Samba daemon.

Cheers,

Eiríkr

LOL, Ok I found this on the log.smbd file

[INDENT][2008/04/03 10:22:04, 0] smbd/server.c:main(944)
  smbd version 3.0.26a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2007
[2008/04/03 10:22:04, 0] lib/interface.c:load_interfaces(201)
  ERROR: Could not determine network interfaces, you must use a interfaces config line
[/INDENT]

Also in te other log, ubuntu seems to be establishing a connection several times and throws this warnings

[INDENT]: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! [/INDENT]

I also found this: 

[INDENT]Apr  3 10:22:00 ubuntu kernel: [   16.775454] Checking aperture...
Apr  3 10:22:00 ubuntu kernel: [   16.775458] CPU 0: aperture @ 520000000 size 32 MB
Apr  3 10:22:00 ubuntu kernel: [   16.775460] Aperture too small (32 MB)
Apr  3 10:22:00 ubuntu kernel: [   16.780366] No AGP bridge found
[/INDENT]

does this mean my agp aperture size should be increased? I'm using PCI express.?

---

### Post by Eiríkr on 2008-04-03
The interfaces config line belongs in the [global] section of your smb.conf file, and should look something like this:
```
interfaces = lo, eth0
```
Try that and see if it helps.  Though something else might be wrong with your OS setup if Samba can't find the interfaces on boot.  

Cheers,

Eiríkr

---

### Post by Alien.col on 2008-04-03
> **Eiríkr said:**
> The interfaces config line belongs in the [global] section of your smb.conf file, and should look something like this:
```
interfaces = lo, eth0
```
Try that and see if it helps.  Though something else might be wrong with your OS setup if Samba can't find the interfaces on boot.  

Cheers,

Eiríkr

Ok, I think i need more info: where do i locate de smb.conf file?

My Board has two LAN jacks that i don't use. The actual connection I use is a wireless usb stick that has the interface "rausb0", should I put that after the "lo" in that line?

---

### Post by Eiríkr on 2008-04-03
The smb.conf file is located at /etc/samba/smb.conf.  You'll need to sudo to edit it.

And yes, after the "lo", put your "rausb0" interface.  You can check that this is the correct one by running ifconfig.

Cheers,

Eiríkr

---

### Post by Alien.col on 2008-04-03
Ok I found the line and it says:

> interfaces = 127.0.0.0/8 eth0

Im changing eth0 to rausb0 and see what happens, should i add anything else?

---

### Post by Alien.col on 2008-04-03
I just rebooted and no change, it still fails and the weird "frequency scaling not supported appears"

---

### Post by Eiríkr on 2008-04-03
Frequency scaling and the mention of the AGP makes me think it has something to do with your monitor, but that's weird if you have a flat panel, as I don't think frequencies apply except for CRTs.  

Does Samba still fail with the same interfaces error?

---

### Post by Alien.col on 2008-04-03
> **Eiríkr said:**
> Frequency scaling and the mention of the AGP makes me think it has something to do with your monitor, but that's weird if you have a flat panel, as I don't think frequencies apply except for CRTs.  

Does Samba still fail with the same interfaces error?

Yes, that's correct, error still appears. I do have a flat lcd panel, i don't use CRT. The weird thing is that i can't really find that "frequency scaling" error on the logs.

 What would the failing to start samba daemons do to my system? I mean everything seems to be working fine and i wouldn't have noticed anything if i had not experienced that weird NFS 5 minute hang at boot problem a couple of weeks ago and activated the text during boot option. I wonder if ubuntu is activating the samba daemons after that, during login or something.

Thanks for the help, I appreciate it.

---

### Post by Eiríkr on 2008-04-03
Samba's failure just means no Samba sharing.  My concern is that Samba for some reason isn't finding your network interfaces on boot, which suggests something is goofy with how your system is handling networking.  This jives with your NFS symptoms as well.  Is your current system an upgrade-in-place of an earlier version, or was it a fresh install on a formatted partition?  I had very weird network issues after upgrading in place from 6.10 to 7.04, and therefore opted to back up and wipe for the move to 7.10.  

Cheers,

Eiríkr

---

### Post by Alien.col on 2008-04-03
This is a fresh install on a wiped out hard drive. I use a drive for storage, one drive for windows/gaming, and a drive for ubuntu, none of the drives has any partitions. 

Ok catch this, at this moment i'm testing my files sharing capabilities and i'm copying files from another ubuntu laptop without any problems. Should i be able to do that if samba wasn't starting????

---

### Post by Eiríkr on 2008-04-03
I just meant failing on boot, as per your first post.  From your description there, it sounded like every time you boot the machine, Samba sharing doesn't work until you manually start the server.  Is this still the case?

---

### Post by Alien.col on 2008-04-03
Uhm no, that''s my point I actually don't have to start Samba manually afterwards. At some point Samba starts on it's own and when i try to start it manually I guess it restarts [ok], but samba works fine without my intervention. My guess now is that there is something in the wireless driver that starts only after ubuntu logs in and for some reason Samba also starts there. It is at boot that it fails.

That's what is bewildering to me because, when i first saw the error I looked for the functions of Samba and i read it was file sharing. But file sharing worked ok, so i let it be until the strangeness of the error message made me post it here.

In a reboot i did this morning the texts also say that nfs-utils unloaded ok and guess what, nfs is not even installed, lol. 

I guess that as long as everything works i shouldn't worry about those text messages, in fact I think that I'm going to untick them.

---

### Post by Eiríkr on 2008-04-03
NFS has various parts to it.  What you uninstalled was likely the server side of things.  Meanwhile, nfs-utils are probably part of the client side of things -- though I'm not sure what this refers to, since there's nothing by this specific name in the nfs-common package.  

Wireless on Linux is still a grey area due to various problems with competing not-quite-standards and funky drivers, so I'm not too surprised that some things might be acting up a little strangely on your system.  But hey, if it works, go with it!  :D

Cheers,

Eiríkr

---

### Post by Alien.col on 2008-04-03
Will do, thanks for all your help.

---

