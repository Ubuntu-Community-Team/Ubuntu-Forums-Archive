---
title: "Trying to locate U3 System device name"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by Mossfoot on 2011-06-09
I've read the dmesg in the System log viewer and don't see anything that might be the USB drive being mounted. Fdisk shows the hard drive and the data part of the USB drive, but nothing that might be the psuedo CD drive in the USB. Same for GParted. 

Palimpsest Disk Utility comes closest, saying it's /dev/sr1 but 

mossfoot@HP-G60:~$ sudo u3_tool -u /dev/sr1 

returns this error:

Error opening device: Unknown device name '/dev/sr1', try 'scan' for first available device

Same for:
... sudo u3_tool -u /dev/sr0
... sudo u3_tool -u /media/"U3 System"
and:
... sudo u3_tool -u /dev/sdc0 (the data part of the thumb drive is "sdc1")

I have not been able to chase down how to: "try 'scan' for first ..."

I think I'm going to break for the night.

---

### Post by oldfred on 2011-06-10
See this thread on U3.

[http://ubuntuforums.org/showthread.php?t=803809](http://ubuntuforums.org/showthread.php?t=803809)

I do not think u3_tool is a Linux command??

---

### Post by dcsoldschool53 on 2011-06-10
> **Mossfoot said:**
> I've read the dmesg in the System log viewer and don't see anything that might be the USB drive being mounted. Fdisk shows the hard drive and the data part of the USB drive, but nothing that might be the psuedo CD drive in the USB. Same for GParted. 

Palimpsest Disk Utility comes closest, saying it's /dev/sr1 but 

mossfoot@HP-G60:~$ sudo u3_tool -u /dev/sr1 

returns this error:

Error opening device: Unknown device name '/dev/sr1', try 'scan' for first available device

Same for:
... sudo u3_tool -u /dev/sr0
... sudo u3_tool -u /media/"U3 System"
and:
... sudo u3_tool -u /dev/sdc0 (the data part of the thumb drive is "sdc1")

I have not been able to chase down how to: "try 'scan' for first ..."

I think I'm going to break for the night.

I'm not sure if this is what you want. In a terminal, type```
ls -l /media
```To get a little more information about the mounted drive```
sudo blkid
```The first code gives you the names of the drives that are mounted on your system. The second code gives the /dev/number. along with the drives name.
Hope this helps you:p

---

### Post by Mossfoot on 2011-06-15
> **oldfred said:**
> See this thread on U3.

[http://ubuntuforums.org/showthread.php?t=803809](http://ubuntuforums.org/showthread.php?t=803809)

I do not think u3_tool is a Linux command??

"Command 'u3_tool' from package 'u3-tool' (universe)"

I still cannot find the location.

---

### Post by Mossfoot on 2011-06-15
> **dcsoldschool53 said:**
> I'm not sure if this is what you want. In a terminal, type```
ls -l /media
```To get a little more information about the mounted drive```
sudo blkid
```The first code gives you the names of the drives that are mounted on your system. The second code gives the /dev/number. along with the drives name.
Hope this helps you:p
I don't think it did. 

Without the thumb drive:
mossfoot@HP-G60:~$ ls -l /media
total 4
lrwxrwxrwx 1 root root    6 2010-04-29 08:22 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2010-04-29 08:22 cdrom0

With the thumb drive
mossfoot@HP-G60:~$ ls -l /media
total 10
drwx------ 5 mossfoot mossfoot 4096 1969-12-31 16:00 C180-72B1
lrwxrwxrwx 1 root  root     6 2010-04-29 08:22 cdrom -> cdrom0
drwxr-xr-x 2 root  root  4096 2010-04-29 08:22 cdrom0
dr-x------ 1 mossfoot mossfoot 2048 2007-10-28 04:52 U3 System

mossfoot@HP-G60:~$ sudo blkid
[sudo] password for mossfoot:
/dev/sda1: UUID="9215e284-8372-424a-acbc-753409d68f6e" TYPE="ext4"
/dev/sda5: UUID="320506ca-c95c-4e15-b32c-7f71d042735b" TYPE="swap"
/dev/sdc1: LABEL="" UUID="C180-72B1" TYPE="vfat" 

Four "media" but only three "block ID". The "sdc1" is probably the data part of the thumb drive, right?

---

### Post by oldfred on 2011-06-15
The command you keep looking for is a windows only command. See the link I posted before.

---

### Post by Mossfoot on 2011-06-15
> **oldfred said:**
> The command you keep looking for is a windows only command. See the link I posted before.
 
If you mean "scan", okay, it's not relevant. Flawed error message, Windows only. No sweat. 
 
The thread you linked to assumes the user knows what to call the device. All the instructions I've found so far assume I know what to call the thing, or what path to use to direct the tool to it's target.
 
I have not had any luck figuring that out. 
 
How do I find what to call the device? I've tried all combinations I can think of. 
 
BTW, I think there are two versions of the removal tool around. One is invoked with "u3-tool" and the other with "u3_tool".

---

### Post by oldfred on 2011-06-15
If this is the U3 device it says you have no label. LABEL=""  Normally you do not see an entry if it is empty, so it seems a little strange.

/dev/sdc1: LABEL="" UUID="C180-72B1" TYPE="vfat" 

You can set labels if unmounted with gparted or with Disk Utility.

---

### Post by Mossfoot on 2011-06-15
> **oldfred said:**
> If this is the U3 device it says you have no label. LABEL="" Normally you do not see an entry if it is empty, so it seems a little strange.
 
/dev/sdc1: LABEL="" UUID="C180-72B1" TYPE="vfat" 
 
You can set labels if unmounted with gparted or with Disk Utility.
 
The thumb drives with U3 in them have two "drives" in them. One is the data part (formatted as VFAT), and the other is protected from being changed by being labeled as a CD drive. As it is labeled a CD drive, the computer does not even attempt to alter the contents.
 
The CD drive part is invisible to gparted. I don't recall trying any Disk Utility trying to find the CD part, but I expect a label would be recorded in the protected part of the thumb drive, and thus not subject to change. And there would be no need of a special program to alter it if Disk Utility could do the job.
 
U3 tools was written to get around that protection. I believe I understand how to use U3 tools to get rid of the CD part of the thumb drive, but I cannot figure out where to point the tool. 
 
It *looks* as though /dev/"U3 System" or /media/"U3 System" should work, but no luck. 
 
This *should* unlock the CD part of the thumb drive:
sudo u3_tool -u (variable consisting of path and device)
 
But, no matter what combination of path and device I've tried, I get this error:
Error opening device: Unknown device name '(variable consisting of path and device)', try 'scan' for first available device
 
Okay, the "try 'scan' is not relevant. That still leaves the path and device part. How do I find that?

---

### Post by Mossfoot on 2011-06-15
Ubuntu 9.10

Palimpsest Disk Utility shows /dev/sr1 mounted at /media/U3 System. That's a 101MB file, ISO 9660. 

but **u3_tool -u /dev/sr1** and **u3_tool -u /media/"U3 System"** both return "unknown device name" when I plug that in. I've tried both with the fake CD unmounted and I've tried **u3_tool -u /media/"U3 System"** with the fake CD mounted. 

So, that's where I'm sitting now. It looks like I have the right path, but the U3 Tool returns an error saying I have the wrong path. 

(side note. It seems that there are different versions of U3 tools, one started by "u3_tool" the other by "u3-tool". Just to set aside that possible confusion.)

---

### Post by dcsoldschool53 on 2011-06-16
> **Mossfoot said:**
> Ubuntu 9.10

Palimpsest Disk Utility shows /dev/sr1 mounted at /media/U3 System. That's a 101MB file, ISO 9660. 

but **u3_tool -u /dev/sr1** and **u3_tool -u /media/"U3 System"** both return "unknown device name" when I plug that in. I've tried both with the fake CD unmounted and I've tried **u3_tool -u /media/"U3 System"** with the fake CD mounted. 

So, that's where I'm sitting now. It looks like I have the right path, but the U3 Tool returns an error saying I have the wrong path. 

(side note. It seems that there are different versions of U3 tools, one started by "u3_tool" the other by "u3-tool". Just to set aside that possible confusion.)

Try using a \ behind U3 space then System. Like this```
/media/U3\ System
```There is only one space between \ and System

---

### Post by Mossfoot on 2011-06-16
Thanks. Cool trick.
 
That did not work, either. I'm starting to think that the problem is in a U3-Tools folder of "recognised devices", and not in Ubuntu at all. 
 
However, the number of posts over at Source Forge is low, suggesting people have lost interest in the project, and either learned to avoid this garbage or given up and started using MS to clean out the garbage.
 
Appropriate.

---

