---
title: "fstab no longer mounting nfs shares at boot"
date: 2020-09-20
forum: Networking &amp; Wireless
---

### Post by scottbomb on 2020-09-20
After years of arm-wrestling with samba, I finally gave up and gave NFS a try, which I think is superior in a pure Linux network like I have now.

The problem is, the shares won't mount at boot, even though they're defined in fstab.

if I wait until the system is done booting, I can execute ```
sudo mount -a
``` and the shares from the server mount perfectly. My question is, why won't this work at boot time?

Here's what their lines look like in fstab:

192.168.1.2:/media/Romulus/Television /media/Television nfs defaults,timeo=30,retry=10,auto 0 0
192.168.1.2:/media/Kronos/Movies /media/Movies nfs defaults,timeo=30,retry=10,auto 0 0

And like I said, they mount just fine if I do it manually with mount -a, but they won't mount at boot. It's like systemd is just ignoring the entries. All of my internet searches lead me to results that discuss using systemd to mount them (with various methods that are a bit confusing) but I'd prefer to just keep things simple and do it in fstab like I mount my hard drives. 

Any ideas of what I can do to make the system actually mount these at boot time? Is it because network manager isn't running yet? If so, is there something else I need to do to force that first?

---

### Post by TheFu on 2020-09-20
If the NFS mounts are being attempted before networking is up, they will fail.  There are mount options to let the mount subsystem (now systemd.mount) know that the mounts need networking first. 

I don't mount NFS using the fstab. I use **autofs** for NFS, Samba and USB storage which mounts those each only on-demand, the umounts them when they are unused. On the nfs server side, there aren't any changes. 

On the NFS client side, I use the line below in my auto.nfs config file to mount on disk.
```
/d/D1 -fstype=nfs,proto=tcp,intr,rw,async  istar:/d/D1
```
There are 7 nfs mounts in that file. 

There is a how-to for **autofs** somewhere on help.ubuntu.com. Google finds it easily.

---

### Post by scottbomb on 2020-09-22
autofs, I'll check it out, thank you.

---

### Post by TheFu on 2020-09-22
autofs was an option AFTER you added the options to the nfs mounts in the fstab telling it that it is a network device.  It was not meant as the first option. Sorry if that wasn't clear.  I think it is _netdev as the option, but don't recall exactly. Check the manpages.```

       _netdev
              The filesystem resides on a device that requires network  access
              (used  to  prevent  the  system  from  attempting to mount these
              filesystems until the network has been enabled on the system).
```
that's from the mount manpage.

---

### Post by scottbomb on 2020-09-24
I tried autofs (before reading the previous post) and found it frustrating. I'd really rather just keep using fstab and nfs as normal. Perhaps I can just make a cronjob to run mount -a after a full boot. I guess we can thank systemd for not loading networking before reading fstab?

---

### Post by TheFu on 2020-09-24
There's only 2 tricks to autofs.  

The auto.master controls the top level directory for each sub-file which holds the configs.  
If you use an auto.master like this:
```
/-      /etc/auto.nfs
```
Then the configs inside /etc/auto.nfs specify the full path. That's what the **/-** does.

The other trick is never, ever, ever, mix directories where autofs manages mounts and where other mounting systems manage mounts .... so don't use /mnt/ or /media/ for autofs stuff. I don't know if this is still an issue or not.

But if this stuff isn't working, I suspect there's something else wrong on the system, somehow.  Only looking through the log files will lead to an answer.  NFS sorta "just works."  When it doesn't, there's a dependency issue or a startup order problem.  There is a specific order that rpc and mount and nfs each need to start for things to work.  I always have to look those up if there's an issue.  Happened in the 1990s and happened again a few months ago on a 16.04 client box here. A reboot didn't fix it.  At the time, I was screwing around with internal DNS and thought that was the issue. I wasn't using FQDN and the DNS server was always returning the FQDN for any requests. It was a pain.  Then the stars aligned and it worked again.  1 issue in 20+ yrs, not bad.

---

### Post by Tadaen_Sylvermane on 2020-09-26
Use systemd automount? Stays in the fstab. I had a bunch of difficulty with autofs, after awhile it just didn't work. Hung on shutdowns / reboots.

```
/nfs/share /local/mount nfs defaults,noauto,x-systemd.automount,x-systemd.idle-timeout=30 0 0
```

This is the template line I use for my nfs shares and my snapraid usb parity drives.

---

### Post by SeijiSensei on 2020-09-26
I was just about to make the same suggestion.  My fstab entries include _netdev in the options list.
```
server:/home /media/server nfs noauto,x-systemd.automount,x-systemd.mount-timeout=30,_netdev   0 0 
```

The mount man page has this description of the _netdev option:

_netdev
The  filesystem  resides  on  a device that requires network access (used to prevent the system from attempting to mount these filesystems until the network has been enabled on the system).

---

### Post by TheFu on 2020-09-26
> **Tadaen_Sylvermane said:**
> Use systemd automount? Stays in the fstab. I had a bunch of difficulty with autofs, after awhile it just didn't work. Hung on shutdowns / reboots.

```
/nfs/share /local/mount nfs defaults,noauto,x-systemd.automount,x-systemd.idle-timeout=30 0 0
```

This is the template line I use for my nfs shares and my snapraid usb parity drives.

I played with x-systemd.automount and it seemed to work, but it never umounted the mount, which bothered me. When I take a laptop off the home network, I'd like not to worry whether it had NFS mounted something 3 days earlier.  With autofs, if the file system hasn't been used in about 5 minutes, it gets umount'ed.

---

### Post by scottbomb on 2021-01-23
Nothing I've tried works. It's odd because my laptop seems to boot just fine with access to the NFS shares using the exact same fstab options as the computer having the problem. Every time I reboot it, I have to open a command prompt and do sudo mount -a in order to mount the nfs shares. Here's how it reads now:

192.168.1.2:/media/Romulus/Television /media/Television nfs defaults,nofail,x-systemd.after=network-online.target,_netdev 0 2
192.168.1.2:/media/Kronos/Movies /media/Movies nfs defaults,nofail,x-systemd.after=network-online.target,_netdev 0 2
192.168.1.2:/media/Kronos/ownCloud/Music /media/Music nfs defaults,nofail,x-systemd.after=network-online.target,_netdev 0 2

Systemd doesn't seem to care if the network is up or not, it just ignores these lines, every time. My workaround, when I get around to it, is to have mount -a run after the desktop loads (this PC automatically logs into a desktop session). I know Kubuntu has a place for me to put startup applications but don't know if it will run something as root. If not, I'll have to find some other way. There's a cronjob to run something at startup but I've never gotten that to work, either.

Ain't systemd great? How did we ever get along without it?

---

### Post by TheFu on 2021-01-23
Bad options cause the entire line to be ignored in the fstab. Is _x-systemd.after=network-online.target_ allowed?

Also, /media/ is controlled by a different program, so it is best to never mount anything you setup in that directory.  Put tem somewere else.

Yes, systemd sucks in many ways. I use autofs for usb and nfs mounts to avoid it.

---

### Post by scottbomb on 2021-01-29
> **TheFu said:**
> Is _x-systemd.after=network-online.target_ allowed?

I'm not sure. I read about it somewhere and thought I'd try it. I think I've tried x-systemd.automount too but not sure but I'll give it a shot to make sure. If it still doesn't work, I'll go read the systemd documentation, something I've been putting off for as long as I can.

---

### Post by scottbomb on 2021-01-30
I did a test on the laptop. x-systemd.after=network-online.target on the fstab line does indeed get it auto-mounted at boot but x-systemd.automount did not. I started reading through the systemd docs last night. While I already understand the simple stuff like starting and stopping services and checking service status, I'm going to have to dig a little deeper to find the docs that speak to filesystem mounting.

I'm not sure what is meant by "/media/ is controlled by a different program, so it is best to never mount anything you setup in that directory." I've been mounting filesystems in /media for 10 years now and it has always worked find for internal hard drives. My main PC mount 4 HDDs in there on every boot. The only program that I know of that uses this folder is Dolphin, like when I mount a USB drive.

---

### Post by Morbius1 on 2021-01-30
I do not use KDE or NFS but on the /media warning: Let's say I have an internal partition that I do not define in fstab.

When I open up any file manager I will see that partition on the side panel with some sort of special icon that indicates that it is mountable - normally by an ordinary user. When I click on it mounts - in this case to /media/myusername/LABEL if it has a label.

udisks2 does that. It will do the same thing for fstab mounts with the noauto option if the mount point is under /media or your home directory. Normally this isn't an issue. And creating a mount point under /media directly isn't an issue either - although it would be best not to create a mount point under /media/username.

What it does do however is really mess up x-systemd-automount. The automounter senses the udisk2 action as an access and initates the automount process immediately even if you do not access it directly. It also prevents x-systemd.idle-timeout from working because the same udisk2 action makes it appear as though it is always accessed.

If you are doing any kind of systemd automount it is best to do it somewhere udisks2 cannot touch which means not under /media or your home directory.

---

### Post by scottbomb on 2021-02-21
Interesting point, thank you. I'll see if a different mount poing makes a difference on the client machine.

---

