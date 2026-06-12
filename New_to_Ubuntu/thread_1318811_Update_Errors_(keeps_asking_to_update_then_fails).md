---
title: "Update Errors (keeps asking to update then fails)"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by fiver22 on 2009-11-07
Hello,
      I keep getting Update Manager notifications that I need to update. I tell it to proceed and it returns the following error:

"PG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7FB8BEE0A1F196A8Failed to fetch [http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/karmic/main/source/Sources.gz](http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/karmic/main/source/Sources.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead."

It then tells me what (if any) updates are available and I dl what is needed. -But then it comes back (the Update Manager notification) seemingly at least once an hour.

Any help would be appreciated.

PC Details:
OS:          Ubuntu 9.10
MOBO:        Intel D865GLC
BIOS:        Intel Corp. version BF86510A.86A.0077.P25.0508040031 (08/04/2005)
CPU:         Intel P4 2.8GHz
RAM:         1GiB (4X256MiB) DDR 320MHz
VIDEO:       ATI Radeon 9600 (RV350)
AUDIO:       Intel 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
NETWORK:     82547EI Gigabit Ethernet Controller 
HDD:         Seagate ST340810A 37GiB
             volume:0 EXT3 /dev/sda1 35GiB,1 Extended partition /dev/sda2 1608MiB
                    logicalvolume Linux swap /dev/sda5 1608MiB
CDROM:       HL-DT-ST DVD-RAM writer: cd-r cd-rw dvd dvd-r dvd-ram
USB STORAGE: Maxtor 114GiB EXT3 /dev/sdb (/media/disk)

---

### Post by phillw on 2009-11-07
> **fiver22 said:**
> Hello,
      I keep getting Update Manager notifications that I need to update. I tell it to proceed and it returns the following error:

"PG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7FB8BEE0A1F196A8Failed to fetch [http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/karmic/main/source/Sources.gz](http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/karmic/main/source/Sources.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead."

It then tells me what (if any) updates are available and I dl what is needed. -But then it comes back (the Update Manager notification) seemingly at least once an hour.

Any help would be appreciated.

PC Details:
OS:          Ubuntu 9.10
MOBO:        Intel D865GLC
BIOS:        Intel Corp. version BF86510A.86A.0077.P25.0508040031 (08/04/2005)
CPU:         Intel P4 2.8GHz
RAM:         1GiB (4X256MiB) DDR 320MHz
VIDEO:       ATI Radeon 9600 (RV350)
AUDIO:       Intel 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
NETWORK:     82547EI Gigabit Ethernet Controller 
HDD:         Seagate ST340810A 37GiB
             volume:0 EXT3 /dev/sda1 35GiB,1 Extended partition /dev/sda2 1608MiB
                    logicalvolume Linux swap /dev/sda5 1608MiB
CDROM:       HL-DT-ST DVD-RAM writer: cd-r cd-rw dvd dvd-r dvd-ram
USB STORAGE: Maxtor 114GiB EXT3 /dev/sdb (/media/disk)


Hi, the best I can come up with is over here -->> [http://ubuntuforums.org/showthread.php?t=1252279](http://ubuntuforums.org/showthread.php?t=1252279)

It discusses adding on a key, amongst other things to with WINE (Which you may, or not, be using)

Phill.

---

### Post by Old_Grey_Wolf on 2009-11-07
Enter this in the terminal, it should sort you out.

```
gpg --keyserver keyserver.ubuntu.com --recv 7FB8BEE0A1F196A8

gpg --export --armor 7FB8BEE0A1F196A8  | sudo apt-key add -

```

---

### Post by fiver22 on 2009-11-07
Thanks for the reply,
   I no longer get the 'PG error' but am left with:

"Failed to fetch [http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/karmic/main/source/Sources.gz](http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/karmic/main/source/Sources.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead."

I take it these are repositories that I had enabled for some reason? If so is there a way to find out what I thought I wanted them for? 
Thanks again.

> **Old_Gray_Wolf said:**
> Enter this in the terminal, it should sort you out.

```
gpg --keyserver keyserver.ubuntu.com --recv 7FB8BEE0A1F196A8

gpg --export --armor 7FB8BEE0A1F196A8  | sudo apt-key add -

```

---

### Post by fiver22 on 2009-11-07
Thanks, I believe that that thread is for a similar issue in that it involves keys and repositories but it doesn't seem to be about the specific errors I'm receiving.
Thank you for trying, though.

> **phillw said:**
> Hi, the best I can come up with is over here -->> [http://ubuntuforums.org/showthread.php?t=1252279](http://ubuntuforums.org/showthread.php?t=1252279)

It discusses adding on a key, amongst other things to with WINE (Which you may, or not, be using)

Phill.

---

### Post by phillw on 2009-11-08
> **fiver22 said:**
> Thanks for the reply,
   I no longer get the 'PG error' but am left with:

"Failed to fetch [http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/karmic/main/source/Sources.gz](http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/karmic/main/source/Sources.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead."

I take it these are repositories that I had enabled for some reason? If so is there a way to find out what I thought I wanted them for? 
Thanks again.

The 404 errors are because the files your system is looking for are no longer there.

This thread will talk you through re-setting your apt-get system for you (The bit that does the foot-work for you). 

[http://maketecheasier.com/become-an-apt-guru/2009/02/24](http://maketecheasier.com/become-an-apt-guru/2009/02/24)

Phill.

---

### Post by fiver22 on 2009-11-08
Wow -That's a great reference for Apt. Thanks for sharing it. It's already showed me alot.
Thanks again.

> **phillw said:**
> The 404 errors are because the files your system is looking for are no longer there.

This thread will talk you through re-setting your apt-get system for you (The bit that does the foot-work for you). 

[http://maketecheasier.com/become-an-apt-guru/2009/02/24](http://maketecheasier.com/become-an-apt-guru/2009/02/24)

Phill.

---

### Post by phillw on 2009-11-08
> **fiver22 said:**
> Wow -That's a great reference for Apt. Thanks for sharing it. It's already showed me alot.
Thanks again.

Posting it as solved would be kewl ... help others :lolflag:

If you are still having issues, I'll go dig  a bit further for you.

In my sig, are a couple of links - the info one will take you to my updated one for things that I come accross. 

It's direct link is here -->  [http://www.vpolink.com/showthread.php?t=2756](http://www.vpolink.com/showthread.php?t=2756)

But, do have a wander thru the info link and my blog, they're there to help people. 

Phill.

---

