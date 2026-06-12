---
title: "How do I determine the UUID's of hard drive partitions?"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by bwallum on 2010-01-05
I'm looking for a quick piece of code to look up UUIDs. I want to specify bootable partitions in Grub2. I have found ```
sudo blkid -o full -s UUID
``` but would like the output related to other information such as drive/partition volume, and if possible manufacturer and serial number. At the moment it simply returns a list of UUIDs related to dev (hd0,1 style). ```
sudo lshw -class disk
```gives me most of what I want, if it could output UUID as well that would be great.

---

### Post by bwallum on 2010-01-05
Answered my own question, sort of. I used> sudo blkid and got device, label, uuid and TYPE returned. It isn't perfect but it helps. Typical output is > /dev/sda1: LABEL="Ubuntu0" UUID="5e2f35bf-4894-4586-ad64-8da2ca9c61bd" TYPE="ext4" 
/dev/sda5: UUID="4bde0f88-f4a2-4405-b895-d16c06e01764" TYPE="swap" 
/dev/sdb1: LABEL="VideoHD" UUID="1d278a93-d076-4f66-9d75-d559b9398df5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: LABEL="HomeHD" UUID="641b027f-a8c8-4153-a70f-9f5e77490e2e" TYPE="ext3"

---

### Post by slakkie on 2010-01-05
> **bwallum said:**
> I'm looking for a quick piece of code to look up UUIDs. I want to specify bootable partitions in Grub2. I have found ```
sudo blkid -o value -s UUID
``` but would like the output related to other information such as drive/partition volume, system reference (hd0,1) style and if possible manufacturer and serial number. At the moment it simply returns a list of UUIDs. ```
sudo lshw -class disk
```gives me most of what I want, if it could output UUID as well that would be great.

Think you should write something yourself to get all the information needed. Probably only a few lines of shell in a function will do the trick.

---

### Post by audiomick on 2010-01-05
Hi.
Those two commands give your what you need, I think. You just need to put it together.

Here is what I get from the first one:
```
mick@ubuntu-desktop:~$ sudo blkid -o full -s UUID
[sudo] password for mick: 
/dev/[COLOR="Red"]sda1[/COLOR]: UUID="97201036-c514-47b5-aeb1-7ce98a8711ff" 
/dev/[COLOR="Red"]sda3[/COLOR]: UUID="a8b6c85c-65da-4ffa-9d2e-8356e5c26bd2" 
/dev/[COLOR="Red"]sda5[/COLOR]: UUID="e7d97bbe-adf2-4ad8-8d3e-c9f56adeed60" 
/dev/[COLOR="Red"]sda6[/COLOR]: UUID="aafe7a68-6945-48cf-b28a-f22b963d5fa6" 
/dev/[COLOR="Red"]sda7[/COLOR]: UUID="4772ec87-6f08-40b9-a274-64e930e7c336" 
/dev/[COLOR="Lime"]sdb1[/COLOR]: UUID="aa6c721e-d06e-4756-bac9-b3849e1a9195" 
/dev/[COLOR="Lime"]sdb2[/COLOR]: UUID="96004184-5efc-490d-9280-0e1ab845a142" 

```
and from the second one
```
mick@ubuntu-desktop:~$ sudo lshw -class disk
  *-cdrom                 
       description: DVD-RAM writer
       product: DVD-RAM GSA-H58N
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.00
       serial: [HL-DT-STDVD-RAM GSA-H58N1.0007/08/17 7U02
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: ATA Disk
     [COLOR="Red"]  product: SAMSUNG HD082GJ[/COLOR]
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
      [COLOR="Red"] logical name: /dev/sda[/COLOR]
       version: JE10
       serial: S0VPJ9CPA13399
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=c3f8aac4
  *-disk
       description: ATA Disk
     [COLOR="Lime"]  product: SAMSUNG HD501LJ[/COLOR]
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
     [COLOR="Lime"]  logical name: /dev/sdb[/COLOR]
       version: CR10
       serial: S0MUJ1EPC25858
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=63eba0e6
```

I have coloured the info that you have to match up. In the second block you can see the disc at /dev/sda1, in the first the partitions on it, and like wise for the second disc.

Another command, that gives a slightly different result, is
```
sudo blkid -c /dev/null
```
That will give you the partition name and file system type as well as the UUID.

---

### Post by slakkie on 2010-01-05
lshw -short gives the same information, but more compact:

```

$ sudo lshw -short | egrep "disk"
/0/100/1f.1/0.0.0      /dev/cdrom  disk        CDRW/DVD GCCT10N
/0/100/1f.2/0.0.0      /dev/sda    disk        80GB ST980310AS

```

---

### Post by bwallum on 2010-01-05
> **slakkie said:**
> Think you should write something yourself to get all the information needed. Probably only a few lines of shell in a function will do the trick.

Could you help me a bit with this. Very interested but have no idea what 'a few lines of shell' and 'in a function' mean. 

I'm assuming I write some kind of script and name it but pretty much lost from there on.

---

### Post by slakkie on 2010-01-05
Helping a bit with shell scripting.. I would not know where to start :) I do have a link for you where you can find out all the information you want:

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

[http://www.gnu.org/software/bash](http://www.gnu.org/software/bash)
[http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)

[http://www.opensolaris.org/os/community/on/shellstyle](http://www.opensolaris.org/os/community/on/shellstyle)

[http://zsh.sunsite.dk/Guide/zshguide.html](http://zsh.sunsite.dk/Guide/zshguide.html)
[http://www.bashscripts.org](http://www.bashscripts.org)

---

### Post by bwallum on 2010-01-07
This is the definitive map of hard drives and UUIDs it seems, really good if you are having Grub2 problems too.

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

