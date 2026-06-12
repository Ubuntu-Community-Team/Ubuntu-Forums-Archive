---
title: "CIFS mount on boot failing on 20.04 server, running out of things to try."
date: 2021-03-16
forum: Networking &amp; Wireless
---

### Post by kimmoj on 2021-03-16
So I installed Server 20.04 LTS on a Pi 4 for some home use. I absolutely cannot get the thing to automount CIFS on boot.

Note, typing a simple sudo mount -a on the command line after a boot  works fine, mounts all three CIFS mounts with no errors logged. But that's not helpful, I need those shares up after patches or other reboots without user intervention.

I've googled and found multiple proposed solutions, none of which seem to do diddly, or what I want when they do something.

- add the entry _netdev to the fstab entry. Does nothing.
- create a batch file in /etc/network/if-up.d/ - I called it mountall - that contains just #!/bin/sh and "mount -a" on a new line. I made it executable with chmod. Does nothing.
- Make a cron entry that contains @reboot and the above script. Does nothing.
- add x-systemd.automount,noauto to the fstab as well. This mounts a couple of the mounts if I try to access them - like doing an ls of /mnt/transfer - but they still don't automount before that. 

The entries all look like this:

//192.168.0.5/transfer/ /mnt/transfer cifs vers=3.0,_netdev,uid=1000,gid=1000,credentials=/etc/cifspasswd 0 0

Or //192.168.0.5/transfer/ /mnt/transfer cifs vers=3.0,x-systemd.automount,noauto,uid=1000,gid=1000,credentials=/etc/cifspasswd 0 0

The credentials file has proper permissions (read only for root) and as I said this mounts fine off the command line. 

None of the above work out, and you can see in dmesg that the network seems to come up well after trying to mount.

[   18.013716] Key type cifs.spnego registered
[   18.013728] Key type cifs.idmap registered
[   18.015452] CIFS: Attempting to mount //192.168.0.5/transfer/
[   18.015622] CIFS VFS: Error connecting to socket. Aborting operation.
[   18.022401] CIFS VFS: cifs_mount failed w/return code = -2
[   18.143841] CIFS: Attempting to mount //192.168.0.5/transfer/
[   18.143982] CIFS VFS: Error connecting to socket. Aborting operation.
[   18.150586] CIFS VFS: cifs_mount failed w/return code = -2
[   18.183438] CIFS: Attempting to mount //192.168.0.5/transfer/
[   18.183576] CIFS VFS: Error connecting to socket. Aborting operation.
[   18.190189] CIFS VFS: cifs_mount failed w/return code = -2
[   18.223329] CIFS: Attempting to mount //192.168.0.5/transfer/
[   18.223468] CIFS VFS: Error connecting to socket. Aborting operation.
[   18.230066] CIFS VFS: cifs_mount failed w/return code = -2
[   19.262386] CIFS: Attempting to mount //192.168.0.5/transfer/
[   19.262522] CIFS VFS: Error connecting to socket. Aborting operation.
[   19.269203] CIFS VFS: cifs_mount failed w/return code = -2
[   19.326664] bcmgenet fd580000.ethernet eth0: Link is Up - 1Gbps/Full - flow control rx/tx
[   19.326697] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

I've run out of fixes to try except abominations like having cron fire a mount -a every minute or some crazy nonsense like that.

How the actual (censored) are you actually supposed to reliably mount remote CIFS shares on boot in Server 20.04?

---

### Post by TheFu on 2021-03-16
Is  //192.168.0.5/transfer/  up and already mounted on /transfer?
I use autofs, which delays mounting until actually requested.

Another idea ... rather than using cron every minute, perhaps use the @reboot time-spec in the crontab?
I'm guessing here. The stuff showed above all looks reasonable and correct to me.  I've never run ubuntu on a pi.

---

### Post by Morbius1 on 2021-03-17
> - add x-systemd.automount,noauto to the fstab as well. This mounts a  couple of the mounts if I try to access them - like doing an ls of  /mnt/transfer - but they still don't automount before that. 
Yep, that has become the standard way of doing things these days. It works as you stated but only when accessed.

The only thing I would suggest is doing something systemd should be doing by default and explicitly tell the system to execute the cifs mount declaration only after a routable ip address is attained. Something like this:
>  //192.168.0.5/transfer/ /mnt/transfer cifs  vers=3.0,[COLOR=#ff0000]**x-systemd.after=network-online.target**[/COLOR],uid=1000,gid=1000,credentials=/etc/cifspasswd 0 0 

This may add a bit to your boot time so ....

---

### Post by TheFu on 2021-03-17
x-systemd.after=network-online.target vs _netdev?

Did systemd decide to ignore long-time options .... again?

---

### Post by Morbius1 on 2021-03-17
On a personal rant / note systemd has decided to "ignore long-time options" by design.

Don't ask me why or when but _netdev hasn't worked the way it used to work for years. It may be coincident with systemd but I vaguely remember it stopping to function properly before then. All of my cifs mounts used to have them and then things just didn't work anymore. 

I moved to autofs then systemd-automount instead. Although it's technically correct that either doesn't automount it really is fairly seamless to have it mount either by a user explicitly or by any process, application, or utility that has to access the mount point.

---

### Post by TheFu on 2021-03-17
Last summer, I switched from autofs to systemd-automount on a bunch of systems for a few months.  It would never un-mount unused storage, which is something I like, especially for laptops and USB connected storage.  As long as autofs still works, I'm fine.

The main storage-related issue I have with systemd is the removal of the **sudo touch /forcefsck** method. So simple. So elegant. Can be done on remote systems easily.  The replacement answers all demand console access, which means a real "server" and DRAC/RIBLO/IPMI capability are required .... er ... or a serial connected console switch. None of those things are cheap for a small business.  Broken by design.

---

### Post by kimmoj on 2021-03-19
Tried this too - ie [COLOR=#ff0000]**x-systemd.after=network-online.target**[/COLOR], and Ubuntu 20 still insists on trying to bring up the CIFS mounts before it has an active network. This is just strange.

Even tried adding this to root's crontab: @reboot sleep 60 && /network/if-up.d/mountall

Apparently that doesn't trigger either.

How can it be this borderline impossible in Ubuntu 20 to do something as fricking pedestrian as mounting network drives on reboot so **** works without me manually having to log on every time to do it? I mean... wow. Maybe I'll switch distros.

---

### Post by Morbius1 on 2021-03-19
You may have given up on Ubuntu at this point but I have been finding different references to this problem like this one: [http://www.elgatoguiri.com/diy/how-to-mount-network-share-on-ubuntu-linux/](http://www.elgatoguiri.com/diy/how-to-mount-network-share-on-ubuntu-linux/)

There are some questionable steps in that HowTo but there is a section labeled [highlight]Raspberry WiFi auto-mount problem[/highlight] as though this is a known problem with Pi. One is a script that is essentially a sleep 20 followed by a mount -a in rc.local and the other uses a built in ( for the debian based OS ) raspi-config utility:
[ATTACH=CONFIG]288153[/ATTACH]
I don't know if this is just about WiFi or if it is about the pi network stack in general.

---

### Post by TheFu on 2021-03-19
As for the crontab, 
@reboot sleep 60 && /network/if-up.d/mountall
is incorrect.  Assuming sudo crontab -e is used, then on my 20.04 systems, /network/if-up.d/mountall doesn't exist (/network doesn't exist), so that would be why it doesn't work. Always verify all paths - that's why tab-completion is so great. Basically, using that won't allow us to make mistakes like this.

The answer should be in the remote-fs unit file.  /usr/lib/systemd/system/remote-fs.target seems to have a flaw.  It doesn't depend on the networking being up.  I didn't trace the entire dependency tree, but the After=remote-fs-pre.target inside it doesn't have any dependencies, which I think is the flaw, but I'm not 100% certain. Seems that remote-fs should depend on network-online.target. 

I'd guess that adding _network-online.target_ to the /usr/lib/systemd/system/remote-fs.service unit file should fix it. The line is:
```
After=remote-fs-pre.target network-online.target
```
after modification. I didn't test it either.

Or just use autofs.  I'm positive that autofs on a r-pi (running a light debian) works. I use autofs with NFS mounts on my r-Pis. I use wired ethernet for my r-pi networking too. One of them uses powerline ethernet as a bridge from opposite sides and different floors of the house.

---

### Post by Morbius1 on 2021-03-19
File this in your "For what it's worth" folder:

I have the debian based raspberry OS installed in a VBox guest.

I edited its fstab to include a cifs mount of the Public folder of my VBox host ( Linux ) nothing fancy here:
```
//host.local/Public /home/pi/Public cifs guest,uid=1000 0 0
```
Rebooted the pi.

Did not mount the share.

Opened up a terminal on the pi and ran [highlight]sudo raspi-config[/highlight] then > System Options > S6 Network on Boot.

Rebooted the pi.

Automounts.

It does take a bit longer to boot but it's seconds not minutes. I think you would be happier installing the OS designed for the pi. Or find out what "S6 Network on Boot" is doing and try to replicate this in Ubuntu.

---

