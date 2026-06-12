---
title: "Ubuntu 10.10 boots to live, but won't install"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by HHDaedalus on 2011-01-23
I have successfully booted Ubuntu (from a USB,) but both 'Run From CD/DVD' and 'Install to Hard Disk' simply bring up the Desktop without the Installation Wizard. When I try to run 'Install Ubuntu 10.10' from the desktop, it shows the loading cursor, and nothing happens. I am fairly certain it is not a patience issue, as it has hanged as such for over 45 minutes twice.

It is the 64bit version, and I am going to dual-boot with Vista. Already have sufficient space partitioned, but this little issue has got me stuck. What do I do?

---

### Post by Rubi1200 on 2011-01-23
Hi and welcome to the forums :)

I assume you have enough RAM?

From the live desktop, go to Applications > Accessories > Terminal and copy/paste the following command:

```
sudo parted -l
```

Copy/paste the output back here in a new post please.

---

### Post by HHDaedalus on 2011-01-23
> **Rubi1200 said:**
> Hi and welcome to the forums :)

I assume you have enough RAM?

From the live desktop, go to Applications > Accessories > Terminal and copy/paste the following command:

```
sudo parted -l
```Copy/paste the output back here in a new post please.

I assume 8gb of RAM is enough. 

Sorry for the delay, had an errand to do. I cannot seem to connect to the internet on ubuntu, so I will just switch and get that output for you!

---

### Post by HHDaedalus on 2011-01-23
Here is what came up; is it what was wanted?


> ubuntu@ubuntu:~$ sudo parted-1
sudo: parted-1: command not found
ubuntu@ubuntu:~$ sudo parted
GNU Parted 2.3
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) -1                                                               
  align-check TYPE N                        check partition N for TYPE(min|opt)
        alignment
  check NUMBER                             do a simple check on the file system
  cp [FROM-DEVICE] FROM-NUMBER TO-NUMBER   copy file system to another partition
  help [COMMAND]                           print general help, or help on
        COMMAND
  mklabel,mktable LABEL-TYPE               create a new disklabel (partition
        table)
  mkfs NUMBER FS-TYPE                      make a FS-TYPE file system on
        partition NUMBER
  mkpart PART-TYPE [FS-TYPE] START END     make a partition
  mkpartfs PART-TYPE FS-TYPE START END     make a partition with a file system
  move NUMBER START END                    move partition NUMBER
  name NUMBER NAME                         name partition NUMBER as NAME
  print [devices|free|list,all|NUMBER]     display the partition table,
        available devices, free space, all found partitions, or a particular
        partition
  quit                                     exit program
  rescue START END                         rescue a lost partition near START
        and END
  resize NUMBER START END                  resize partition NUMBER and its file
        system
  rm NUMBER                                delete partition NUMBER
  select DEVICE                            choose the device to edit
  set NUMBER FLAG STATE                    change the FLAG on partition NUMBER
  toggle [NUMBER [FLAG]]                   toggle the state of FLAG on partition
        NUMBER
  unit UNIT                                set the default unit to UNIT
  version                                  display the version number and
        copyright information of GNU Parted
(parted) 

---

### Post by HHDaedalus on 2011-01-23
Anyone else?

---

### Post by HHDaedalus on 2011-01-23
Now it gives an error message stating that 'ubiquity-dm' has unexpectedly closed, or something to that affect.

Anybody have any idea how to help?

---

### Post by presence1960 on 2011-01-23
The command is ```
sudo parted -l
```that is a lowercase L at the end not the number (1)

---

### Post by HHDaedalus on 2011-01-24
> **presence1960 said:**
> The command is ```
sudo parted -l
```that is a lowercase L at the end not the number (1)
My apologies.

Either way, I simply formatted the drive and re-downloaded the iso to it, that fixed the problem. Now I am getting an Errno 5: Input/Output error during installation.

---

