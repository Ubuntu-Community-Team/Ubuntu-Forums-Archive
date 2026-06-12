---
title: "wifi help for acer 5315 laptop"
date: 2008-01-27
forum: Networking &amp; Wireless
---

### Post by Anime_Wars on 2008-01-27
Hey there.  I have recently purchased an Acer Aspire 5315-2077 laptop, and have had the "joy" of trying to install a wi-fi driver. But, after hours of trying various tutorials and reading pages and pages of information, I have gotten almost absolutely nowhere (except for installing ndiswrapper).

I was wondering if anyone here could help me with my problem. Any step-by-step instructions would be lovely (It would help if I wasn't just linked to tutorials, since thus far they have not been particularly helpful).  It would be much appreciated.

---

### Post by tensop on 2008-01-29
Firstly, confirm which Wireless Network card(NIC) your laptop is using(as i have not heard of this particular sub model of the 5315)

You can do this by typing:

```
lspci | grep "Ethernet"
```

If no hardware issues are occuring, you should be presented with something similar to:

```

db@dblaptop:~$ lspci | grep "Ethernet"
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
06:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
db@dblaptop:~$

```

If your NIC is an Atheros AR5006EG(It's really an AR5007eg) then you should have two choices - madwifi(a project designed for atheros network interface controllers) or ndiswrapper(which uses windows coded drivers)

Once you have conirmed its an atheros network interface controller you should update ubuntu to the latest software versions.

Madwifi is the better option, and appears to be stable as of the current version.

however if it presents issues, then you should try the slightly lengthier process of ndiswrapper.

Firstly, a few pages for reference:

[http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)
[http://forum.ubuntu.pl/showthread.php?t=61317&highlight=5007eg](http://forum.ubuntu.pl/showthread.php?t=61317&highlight=5007eg)

Follow these steps:

1. Disable the restricted driver for the network card in restricted drivers

2. make a directory in your home folder(eg madwifi) and download:

[http://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2756-20071018.tar.gz](http://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2756-20071018.tar.gz)

Plus

[http://madwifi.org/attachment/ticket/1679/madwifi-ng-0933.ar2425.20071130.i386.patch?format=raw](http://madwifi.org/attachment/ticket/1679/madwifi-ng-0933.ar2425.20071130.i386.patch?format=raw)

The second link cannot be downloaded using wget(use firefox to download it)

3. extract the tar.gz file by typing "tar -xvf <<filenamehere>>

4. Install binutils.
```

sudo apt-get install build-essential bin86
```

5. Copy the patch file into the newly created madwifi folder during the tar extraction process


6. Patch the madwifi driver. Eg:

```
patch -p0 < madwifi-ng-0933.ar2425.20071130.i386.patch
```
(you may need to substitute the file name if it is different)

7. Build the madwifi driver by typing:

```
make
```

```
sudo make install
```

8. Reboot the laptop. All should be working. If not, follow this thread:

[http://ubuntuforums.org/showthread.php?t=512828&highlight=madwifi+ar5007eg+patch&page=28](http://ubuntuforums.org/showthread.php?t=512828&highlight=madwifi+ar5007eg+patch&page=28)

---

### Post by IndyGunFreak on 2008-03-30
Wow, can't believe it was that simple.

THank you

IGF

---

### Post by IndyGunFreak on 2008-04-25
Any word on wether this will work in Hardy?  The device isn't detected properly in Hardy either.  Give me an hour or so as I'm backing up, and I'll be the guinea pig.. :)

Edit:  Worked w/ one minor modification.

[http://ubuntuforums.org/showthread.php?p=4790652#post4790652](http://ubuntuforums.org/showthread.php?p=4790652#post4790652)

IGF

---

### Post by pmokgweetsi on 2008-06-08
Chilli555 bear with me for seemingly troubling you but i went as far as detecting my systems' network interface card which ubuntu detected as **06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01.** (whether it is right or wrong im not so sure)and then i disabled HAL (whatever that is) but i ran into trouble while trying to create a directory that i can use to download the two links under step 2. Where did i go wrong? The first link did not even work when i used windows internet explorer or firefox...how do i resolve this one? Again how do i extract tar.gz file from where ever i saved it? I tried typing the name that i gave to the file between "tar -xvf <<filename>>" but that didn't work...  

Many thanks.

---

### Post by ugm6hr on 2008-06-08
> AR242x

This is what Linux now calls the AR5007 Atheros chipset.

Which version of Ubuntu are you using?  I assume Hardy / 8.04, but is it 32- or 64-bit?

The way to get this working depends on this.

There are plenty of how-tos for 32-bit, and a new 64-bit one for madwifi support.

---

### Post by robbro on 2008-06-14
Ok, none of the madwifi links are working, none of the howto's are working now.  How in blue blazes can I get this wireless card to work in Ubuntu currently?

---

