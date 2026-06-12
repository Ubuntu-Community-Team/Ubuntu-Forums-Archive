---
title: "Network booting feisty"
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by mvsjes2 on 2007-06-14
I've been trying to network boot my feisty system and am very close.

The boot up appears normal up to the point of "Configuring network interfaces". After that things appear to go south. Avahi initialization times out, a samba share I have set up fails to connect, and I seem to loose my root file system since the startup scripts complain that they can no longer find "sed". I can't do anything with the system after that, it just hangs.

I'm unable to capture the boot messages since there's an outstanding bug in feisty with logd, so I'm pretty limited as to what I can check.

I have the eth0 network interface commented out of /etc/network/interfaces.

Can anyone suggest what might be wrong? I can boot successfully off my local drive, and the root file system for the netboot is a copy of this, with /etc/network/interfaces and /etc/fstab adjusted.

client network:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

```

client fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>       <type>  <options>       <dump>  <pass>
proc            /proc               proc    defaults        0       0
/dev/nfs        /                   ext3    defaults,errors=remount-ro 0       0
mythtv-master.local:/home     /home nfs     defaults        0       0
/dev/sda6       none                swap    sw              0       0
/dev/sda7       /data               ext3    defaults        0       0
//mythtv-master/myth  /var/lib/myth cifs credentials=/root/.smbcredentials,dmask=777,fmask=777  0        0

```

client pxe config:
```
LABEL feisty
       kernel feisty/vmlinuz-2.6.20-15-generic
       append root=/dev/nfs nfsroot=192.168.2.10:/var/lib/myth/bootimages/mythtv-front1 ip=dhcp initrd=feisty/initrd.img-2.6.20-15-generic rw  --

```

---

### Post by Twigathy on 2007-06-14
I am having the exact same problem - I've posted a bug here, because I'm not too sure about it...

[https://bugs.launchpad.net/ubuntu/+bug/120483](https://bugs.launchpad.net/ubuntu/+bug/120483)

---

### Post by mvsjes2 on 2007-06-14
Thanks Twigathy,

I have a little more data. I added "single" to the boot options of my nfs bootup, and successfully got to a root prompt. The only problem I had during the boot (that I could catch) was a timeout trying to mount my samba share. From there I could do pretty much anything that I wanted. The network was up, I had internet access, I could nfs share other file systems, I could start X and get a full desktop etc.

Once I verifiied everything was looking good, I went back to the root prompt and entered "telinit 2". From there it was all bad. Avahi timed out, so I removed that from the startup and tried again, and next the "network manager" (i think it was called) failed after that. Once that happened I got a flash of messages, and the last screen was full of startup script failures complaining they couldn't find "sed" (it's in /bin and does exist on the system). Since the system hangs at that point I can only guess what went wrong. I assume something is blowing away my root file system.

I'll probably start manually running the rc2.d scripts and see if I can narrow down what's causing all the fuss. Maybe you can try something similar and we can compare notes.

I sure hope the logd bug will be solved soon!

---

### Post by mvsjes2 on 2007-06-14
I'm new at this, so take this with a grain of salt, but you might try:
cp -ax /dev/. /mnt/edam/dev/.
to your setup. I read that in one of the many procedures I've been working with.

---

### Post by mvsjes2 on 2007-06-14
I cut/pasted my stuff in the bug report. Do you want to keep updating this or use the bug report?

---

### Post by Twigathy on 2007-06-14
Regarding the copying of /dev/, I think that should have been handled okay by the big root copy - I don't have a seperate partition for /dev/ like with /boot, which requires some "special" treatment...

Also - one of the init scripts is nuking progress. Grumble. (As you'd found out on the bug report thing :0)


I should probably add that I'm doing a semi-diskless boot. /boot is staying on the client (Eventually a CompactFlash card in a CF -> IDE reader) and the rest of / is on the server. But that ought not make any difference, seeing as we both get past the NFS boot stage and the bit that fails is services later on...

---

### Post by mvsjes2 on 2007-06-14
If you don't mind my asking, what's the advantage to keeping /boot separate? It may be something that I might find useful...

---

### Post by thecure on 2007-06-15
[QUOTE=mvsjes2;2843473]
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0                                         
#iface eth0 inet dhcp
[/CODE]


Try uncommenting out the eth0 entries...

auto eth0  
iface eth0 inet dhcp

---

### Post by Twigathy on 2007-06-15
Sadly if you do that the machine will lose connection to the NF S server and all kinds of splode and doom happen (IE. no files can be found.). With "ip=dhcp" added to the kernels boot options it picks up the IP address itself just fine. With that bit of /etc/network/interfaces uncommented, connection is indeed lost - "nfs: server 192.168.0.15 not responding, still trying"..... forever.

Regarding keeping /boot seperate, I want it like this because my networking kit doesn't support PXE boot and having a small partition on a CompactFlash card holding kernel, initramfs and grub to kick off the boot process seems far easier than mucking around with etherboot and other such trickery. I may well be wrong here, but it seems to work for me! :) (Well. "Work". In that it gets halfway through the boot process and then explodes!!)

---

### Post by mvsjes2 on 2007-06-15
The problem occurs in /etc/rc2.d/S12dbus. Network manager deactivates eth0 and tries to reactivate it and that's the end of that.

I'll (manually, sigh) enter the tail of the log into your bug report.

---

### Post by Twigathy on 2007-06-16
Have you had any luck with network-manager yet? I found [This Bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/92338") but it isn't yet a confirmed one, so I guess the devs don't know about it... :-(.

---

### Post by Twigathy on 2007-06-16
[https://help.ubuntu.com/community/Installation/OnNFSDriveWithLocalBoot](https://help.ubuntu.com/community/Installation/OnNFSDriveWithLocalBoot)

I managed to get it working perfectly :)

---

### Post by mvsjes2 on 2007-06-18
I like the workaround you found better than a lot of others I've seen - it will be much easier to backout later when networkmanager is fixed.

I'm writing this from my network booted client, so everything's working, however, my other nfs drives aren't mounted on bootup. I have to boot to single user, then enter "mount -a" then "telinit 2". Other than that it's fine.

---

### Post by Twigathy on 2007-06-18
hmm, a way around that might be to write a .sh script to mount your NFS shares and then have that run when you login to Gnome. By that time, the network will be up and running okay. (Take a peek at System->Preferences->Sessions->Current Session and the "Startup Programs" tab). Of course, this won't be of any use at all if the NFS share you want to mount is for your home directory...

Just a thought :)

---

### Post by mvsjes2 on 2007-06-18
Actualy it is for my home dir ;) as well as a dir that mythtv uses.

I think a large part of the reason it's not connecting automatically is because I disabled network manager. If you follow the boot logic, when network manager enables the network interface, dbus detects this event and starts a bunch of other things, some of which is mounting any network attached file systems. So now that I've disabled network manager it makes sense that my network mounts aren't being mounted.

There's still something puzzling however: on a regular bootup I can see a message stating that it is mounting /var/lib/myth and it scrolls right on by, whether or not it's successful (I have no idea which). On my network boot, the boot process hangs at this point for a couple of minutes, then times out and carries on. I don't get it because I also nfs mount my home dir in fstab and I don't see any pause for this.

```

/dev/nfs        /                   nfs     rw,hard,intr,rsize=8192,wsize=8192,errors=remount-ro 0       0
192.168.2.10:/home /home     nfs	    rw,hard,intr,rsize=8192,wsize=8192        0       0
192.168.2.10:/var/lib/myth   /var/lib/myth  nfs  rw,hard,intr,rsize=8192,wsize=8192        0       0

```

Anyway, I'm still playing around with it to see if I can get around this last gocha. Things would be a lot easier if I could somehow capture and compare my boot messages...

---

### Post by WattoDaToydarian on 2007-07-11
I am trying to accomplish this with a distro called [[COLOR="Blue"]Mythbuntu[/COLOR]]("http://www.mythbuntu.org/") which is based off of 7.04.
I am trying to have two different distros boot over PXE, one is in /media/frontend and the other is in /media/wattopvr and my tftproot is in /media/frontend.
I copied the files from boot in "wattopvr" to the boot in "frontend" so the client can access the kernel and initrd over tftp then mount the root filesystem located elsewhere.
I changed BOOT=local to BOOT=nfs in initramfs.conf on "wattopvr" and updated the initrd before I copied it to "frontend"

The problem I am having is while it is booting it starts saying it cant access different files and dirs, then it asks for the root password for maintenance I tried my password it it didn't work. At that point I hit control+D and it asks me to login, my user and pass don't work either so I think it is unable to access my username and pass from the server.
I suspect that one or more of the init scripts is causing it to loose connection somehow:confused:

Here is my pxelinux.cfg file from the server for mythbuntu, it is located in "/media/frontend/pxelinux.cfg":
```
LABEL linux
        KERNEL /boot/vmlinuz-2.6.20-16-generic
        APPEND root=/dev/nfs nfsroot=192.168.0.4:/media/wattopvr ip=dhcp initrd=boot/initrd.img-2.6.20-16-nfs single rw
        TIMEOUT 300

```
Here is the fstab for mythbuntu located in "/media/wattopvr/etc":
```
proc            /proc           proc    defaults        0       0
192.168.0.4:/media/frontend     /       nfs defaults,auto,noatime 0 2
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```
Here is my dnsmasq.conf located on my inet server which has an IP of 192.168.0.1:
```
bogus-priv
conf-file=/etc/dnsmasq/dhcp.conf
dhcp-authoritative
dhcp-boot=pxelinux.0,watopia,192.168.0.4
dhcp-lease-max=1000
dhcp-option=17,/media/frontend
domain-needed
domain=***************
expand-hosts
no-negcache
strict-order
user=nobody

```

---

### Post by Twigathy on 2007-07-11
Which files does it say it is missing? Before messing around and nuking network mangler, I always used to get "/tmp/eth0.tmp not found" and then a kernel panic. I guess you followed at least some of my guide thingy...?

---

### Post by WattoDaToydarian on 2007-07-11
> **Twigathy said:**
> Which files does it say it is missing? Before messing around and nuking network mangler, I always used to get "/tmp/eth0.tmp not found" and then a kernel panic. I guess you followed at least some of my guide thingy...?
I never got the error that you got, I am getting errors that say it cant access files in /var/log, /tmp, and it cant start X.
So I deleted the log files in "/media/wattopvr/var/log" rebooted the client machine, and when it was done, I did "ls /media/wattopvr/var/log" there were no new log files created.
Then I did the same thing for "/media/wattopvr/tmp" and the client did manage to create ".ICE-unix" and ".X11-unix" so at one point it can access the server.
When you say "network mangler" are you meaning "network manager"? I never messed with it.
I did look at your guide and I was unable to find the files "etc/default/NetworkManager and etc/default/NetworkManagerDispatcher" on any of my machines. I tried to make them and add "exit" but that had no effect.

---

### Post by Twigathy on 2007-07-11
heh, yep, network mangler == network manager. Those two files didn't exist for me either; had to create them. If you were not having problems on boot with network manager running, I'd not bother with the "exit;" hack.

Very weird errors there. Not too sure what to suggest.... not being able to write to files in /tmp sounds like either permissions issues (Unlikely, would give "Permission denied" or similar) or the ethernet connection is dropping out while writing files to /tmp. Which is possible, I guess. Not sure.

Have fun :S

---

### Post by WattoDaToydarian on 2007-07-11
I FIGURED IT OUT!!!  The exports file on my server had just this:
```
/                  192.168.0.0/24(rw,async)
/media/frontend/   192.168.0.0/24(rw,no_root_squash,async)
/myth              192.168.0.0/24(rw,async)

```
I forgot to add a line for wattopvr so now it looks like this:
```
/                  192.168.0.0/24(rw,async)
/media/frontend/   192.168.0.0/24(rw,no_root_squash,async)
/media/wattopvr/   192.168.0.0/24(rw,no_root_squash,async)
/myth              192.168.0.0/24(rw,async)

```
After that change I had no filesystem errors and everything loaded perfectly as if it was on the local hdd!
Thanks for the help!

---

### Post by Twigathy on 2007-07-11
Nice one! I guess it's sorta important to add the root FS export before trying to boot from it! ;)

---

### Post by becca1023 on 2007-07-11
lol. I have absolutly NO cluw what so ever. But gl getting your answer!

check out my siggy.

---

### Post by jaripetteri on 2007-08-29
Thanks for the great howto Twigathy. I found one typo on it. 

On *vim etc/network**s**/interfaces* there is one extra "s".  8)

Also on my setup I need to change *root  (hd0,5)* to hd0,0 since I'm using USB memory stick as boot drive and that's only drive I have. Just if anyone having same problem, it took me a while to find out that.  

I still have one problem thought. I manage boot the system up so that I insert LiveCD on drive and then use "boot from first hdd" option. If I try to boot straight from USB the Grub starts but hangs without errors. Any idea what's causing it and how to fix? Should I add some delay or something on Grub?

---

### Post by Twigathy on 2007-08-29
Thanks for the feedback about the typo - fixed that now :-)

Not too sure about the grub stuff - probably something specific to booting from a USB stick though. If you do find a solution, post it back here and I'll add to the wiki.

Also, I found the network block device for swap over ethernet is really, really bad. Caused a lot of weird program crashes and general badness. Now running without swap (Box has 2GB of RAM) and things seem much better. Added a relevant warning to the wiki page

---

### Post by jaripetteri on 2007-08-29
I have also used CF as HDD over a 6 month on one MythTV Frontend laptop without swap and no problem there. So I didin't use swap here also. As far you have enough memory there should be no problem. On that laptop I have 512MB. On netdrive HTPC I have 1BG.

I found something about USB boot I need to check and there is something weird on USB boot on my Pundit anyway, didn't manage to get it work with internal CF or SD card reader which is on MB but still via USB, even those are shown on bios. And it's USB bootable but still not... =)  I'll let you know if I can fix this.

---

