---
title: "Ok brand new linux usr - questions after a few days of xubuntu."
date: 2009-01-21
forum: New to Ubuntu
---

### Post by Jynks on 2009-01-21
Hi there...

I recently tried out xubuntu as i heard it was a great laptop os. Light, fast and stable. So far i have been totally blown away. I havn't logged into vista for almost a week. 

After getting everything working (mostly) I just have a few questions.

1) How do i mount my CD-ROM. 

```
mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)

```

2) How can i get xubuntu to automatically mount the CD-ROM and my other windows network shares. At the moment I use this script.
```
#!/bin/bash
mount.cifs //10.1.1.3/Archive ~/Network/Showreel-Archive01
mount.cifs //10.1.1.3/D ~/Network/Showreel-Archive02
```

I right click and run each time i wish to access the other ocmputers windows shares.

So how do I make these network shares and the cdrom auto mount on boot?

3) I am using a COMPAQ Presario c700. Sound is working but the built in Mic is not... any ideas how i would go about getting that to run.

4) I have wireless networking up and running but when ever i boot i get asked for a password "keyring" before the wireless tries to connect. This is not  the wireless network password. But a password to initilise the wireless networking on the leptop... once entered it auto connects to my network.

5) My windows system can see the shares I have set up on xbuntu, but when i try to write to them I get no permission... hwo do i fix that?


Thanks in advance

---

### Post by northern lights on 2009-01-21
> **Jynks said:**
> 1) How do i mount my CD-ROM.The cd-rom should automount as soon as a CD is inserted in the drive. Can you please post the output of```
cat /etc/fstab
```
> **Jynks said:**
> 3) I am using a COMPAQ Presario c700. Sound is working but the built in Mic is not... any ideas how i would go about getting that to run.
Please also post the output of```
sudo lshw -C multimedia
```
> **Jynks said:**
> 5) My windows system can see the shares I have set up on xbuntu, but when i try to write to them I get no permission... hwo do i fix that?Is this an internal share (accessed when booting into Windows) or a network share?
If it's internal, you'd need to have the shared partition formatted as either FAT or ntfs for native Windows support. If it's a network share, modify permissions on the shared folder either via ```
chmod -R 776 /path/to/share
```or via thunar's GUI (if the share is not in /home, the above command would have to be run as root (i.e with sudo))

---

### Post by Jynks on 2009-01-21
> **northern lights said:**
> The cd-rom should automount as soon as a CD is inserted in the drive. Can you please post the output of```
cat /etc/fstab
```

OH.. wait i got this sorted now. I am so sorry but i was just stupid. <feels dump>


> **northern lights said:**
> Please also post the output of```
sudo lshw -C multimedia
```

```
 sudo lshw -C multimedia
[sudo] password for thisisme: 
  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

```

Is this an internal share (accessed when booting into Windows) or a network share?

> **northern lights said:**
> If it's internal, you'd need to have the shared partition formatted as either FAT or ntfs for native Windows support. If it's a network share, modify permissions on the shared folder either via ```
chmod -R 776 /path/to/share
```or via thunar's GUI (if the share is not in /home, the above command would have to be run as root (i.e with sudo))

It is a share on the xubuntu box to read in widnows. I used to be able to browse to xbuntu computer from my Xp box, see teh sahre, open the share, but I couldn't write into it .... I ran that chmod command and not I can see the computer browse onto it and see teh shares but i get a permition error when trying to open the share.

---

### Post by Jynks on 2009-01-22
any help?

---

### Post by Jynks on 2009-01-22
any help?

---

### Post by cardinals_fan on 2009-01-22
I suppose you could try going all-out with ```
chmod -R 777 /path/to/dir
```

---

### Post by Jynks on 2009-01-23
> **cardinals_fan said:**
> I suppose you could try going all-out with ```
chmod -R 777 /path/to/dir
```

still dosn't work... dose the share on the window drive need to be formated as FAT32 or NTFS?

---

### Post by bgerlich on 2009-01-23
Can you mount the share in windows using the mount network drive option?

///10.0.1.1/share    

where 10.0.1.1 is your LAN ip address and "share" is your share name ?

Also post your: /etc/samba/smb.conf

---

### Post by hyper_ch on 2009-01-23
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by HittingSmoke on 2009-01-23
> 3) I am using a COMPAQ Presario c700. Sound is working but the built in Mic is not... any ideas how i would go about getting that to run.

I've never used Xfe so I don't know the layout but you might try checking which capture device is set as default. In Gnome its System>Preferences>Sound. There's options there for input and output devices and test buttons. You should also double check your mixer to make sure your input isn't muted.

---

