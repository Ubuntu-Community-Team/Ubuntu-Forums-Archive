---
title: "upgrading from Intrepid to Jaunty"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by aravindc26 on 2009-06-05
I got Jaunty cd from shipit. I use Intrepid, is there any way to upgrade from Intrepid to Jaunty without erasing my entire hard disk using the cd ?

---

### Post by Therion on 2009-06-05
I'm pretty sure the only way to upgrade from a CD is by using the Alternate Install CD.

You don't want to do an online upgrade?  Not that I blame you, but that IS how most people would approach this...

---

### Post by Cypher on 2009-06-05
If the CD you got is the Alternate CD, then it as simple as mounting the CD (just inserting the CD should do this for you) and then hit ALT-F2 and type "gksu "sh /cdrom/cdromupgrade" to start the upgrade..

---

### Post by tiyowan on 2009-06-05
What you need is the alternate CD (from [http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading")):

> Upgrading Using the Alternate CD/DVD

Use this method if the system being upgraded is not connected to the Internet.

Download the alternate installation CD
Burn the ISO to a CD and insert it into the CD-ROM drive of the computer to be upgraded.
If the ISO file is on the computer to be upgraded, you could avoid wasting a CD by mounting the ISO as a drive with a command like:

```
sudo mount -o loop ~/Desktop/ubuntu-9.04-alternate-i386.iso /media/cdrom0
```

A dialog will be displayed offering you the opportunity to upgrade using that CD.
Follow the on-screen instructions.
If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:

```
gksu "sh /cdrom/cdromupgrade"
```



---

### Post by Skrean on 2009-06-05
> **Cypher said:**
> If the CD you got is the Alternate CD, then it as simple as mounting the CD (just inserting the CD should do this for you) and then hit ALT-F2 and type "gksu "sh /cdrom/cdromupgrade" to start the upgrade..

What is the 'Alternate CD' and how to get it?

---

### Post by Cypher on 2009-06-05
You can download the Altenrate CD from [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate) directly from a mirror or through Bittorrent (the better way to get a fast rate)..

---

### Post by There Was A Time on 2009-06-07
I'm in exactly the same situation as the OP, as I have a poor internet connection, so downloading the Alternate Installation Disc or doing the update via the update manager is not really an option.

Surely there's some way to do it from the normal install CD...

---

### Post by kwacka on 2009-06-07
I haven't tried this, so can't guarantee it.

Open terminal, type ```
sudo apt-cdrom add
```

insert CD, press 'Enter'. refuse when asked for further CDs. 

Open Synaptic and clear all repositories except the CD you've just added (or do this by adding a # at the start of every clear line except the CD in /etc/apt/sources.list).

Enter:
```
sudo apt-get update
```

Update manager should open, click 'upgrade' and it hopefully it will upgrade from CD.

You will need to change all your repositories from Intrepid to Jaunty; and then upgrade new security updates etc.

As I said, no guarantees.

Final point - why upgrade? What is the problem with Intrepid? Why not do a clean install from the jaunty CD if you really want to upgrade?

---

