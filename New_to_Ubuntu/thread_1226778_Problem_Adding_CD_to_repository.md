---
title: "Problem Adding CD to repository"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by djmac on 2009-07-29
I somewhat stupidly remove the network-manager (after having some trouble with it) with the intention of re-installing it (from CD). Unfortunately, I can't seem to add the CD to the repository. I tried in synaptic and it didn't seem to recognize that there was anything in the drive. 

 I then tried to manually add the CD via

```
sudo apt-cdrom add
```

And the output was:

```
E: Failed to mount the CD-ROM
```

 The CD is mounted and I can explore it

---

### Post by djmac on 2009-07-29
More info:

As Soon as I type sudo 

```
sudo apt-cdrom add
```

I get

```
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...

```

Before I get the error

And my fstab file has this in it (for the CD):

/dev/sdc0      /media/cdrom0 udf, iso9660 user, noauto, exec, utf8 0 0 

If that helps

Thanks

---

### Post by llamabr on 2009-07-29
Where did you get this disk?  Or, what's on it, when you mount it and navigate around?

Does this machine not have net access?

---

### Post by MasterNetra on 2009-07-29
Make sure your Ubuntu CD is still in the Drive then go to System>Administration>Software Sources, there under the first tab "Ubuntu Software" and under "Installable from CD-ROM/DVD" check the "Cdrom with Ubuntu..." afterwards go to close and when it asks, select "Reload" you should have access to what is on the Ubuntu CD.

If not you could click add CD-ROM under the Third Party tab.

> **llamabr said:**
> Where did you get this disk?  Or, what's on it, when you mount it and navigate around?

Does this machine not have net access?

The OP stated he accidentally removed network manager, no network manager no connecting to net.

---

### Post by djmac on 2009-07-30
Well I successfully added the CD-ROM from the third party tab. Unfortunately, the CD does not appear to have the Network Manager on it!! God-damn. I've tried the Ubuntu 8.04 LTS DVD, the 8.10 installation CD and the 9.04 installation CD. It's not there!! Should it be? Am I just looking in the wrong spot?

Thanks

---

