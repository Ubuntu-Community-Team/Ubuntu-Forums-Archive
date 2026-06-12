---
title: "I need help setting up zydas driver"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by oldcpu on 2007-06-20
Same problem as here:
[http://ubuntuforums.org/showthread.php?t=403419](http://ubuntuforums.org/showthread.php?t=403419)

This how-to supposedly fixes it:
[http://ubuntuforums.org/showthread.php?t=195259&highlight=Zd1211](http://ubuntuforums.org/showthread.php?t=195259&highlight=Zd1211)

Stuck at Step 4.  How am I suppose to do that without a connection?

Are the 2 packages available on the Feisty server CD?  If so, how do I get apt-get to find it in the CD?

---

### Post by chili555 on 2007-06-20
> Are the 2 packages available on the Feisty server CD?Probably. Note that the howto is written for an older version of Ubuntu than Feisty. You can get around this by substituting `uname -r` for 2.6.15-23-386 in the howto, thus:```
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r` linux-source-`uname-r`
```That's backtick; the symbol up by the 1 on your keyboard.

> how do I get apt-get to find it in the CD?```
sudo apt-cdrom add
sudo apt-get update
```Do this *before* you do the commands above. Post back if you get stuck.

---

### Post by oldcpu on 2007-06-21
Update did not go through since I did not have a connection.
```
E: Some index files failed to download, they have been ignored, or old ones used isntead.
```
That was expected.  But I was trying to just update it to include the CD-ROM too.

So I went on ahead with the installation, but that did not go through either.
```
Reading package list... Done
Building dependency tree
Reading state information... Done
Package linux-source-2.6.20 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsolete, or is only available from another source.
E: Package linux-source-2.6.20 has no installation candidate.
```
May contain typo since I am using another computer with a connection to communicate now.  Therefore, I can not copy-and-paste the exact code.

The CD should have the packages since I installed from it and did not update the kernel.  But I do not know why it failed to find it.

Also, the how-to does not provide information on how those 2 packages are fetched since there is not suppose to be a connection until the end of the how-to when the driver is installed and working.

So I assume they are fetched from another system, put on a CD, then transfered to the driverless system.  But then there is the dependencies nightmare one might have to go through.

If that is how the 2 packages are fetched, then I will try it out later.  Hopefully, no dependencies nightmare.

---

### Post by chili555 on 2007-06-21
I really think this will compile without linux-source. Please try:```
sudo apt-get install build-essential linux-headers-`uname -r`
```Thanks.

---

### Post by oldcpu on 2007-06-22
Thanks!

This time, I excluded the linux-source, and the rest did compile.  But the linux-source still failed after that.

*sigh*

Wireless is really complicated in Linux.  But landlord said no drilling the walls.  I have already spent more wireless cards than what my computer is worth.

EDIT: 

Okay, I have downloaded the linux-source in *.deb from the Ubuntu Package site and installed it.  But now stuck at Step 6.

While trying to
```
sudo ln -s /usr/src/linux-headers-2.6.20-15-server /usr/lib/2.6.20-15-server/build
```
it returns with
```
ln: creating symbolic link '/usr/lib/2.6.20-15-server/build' to '/usr/linux-headers/2.6.20-15-server': No such file or directory
```
I checked with 'ls' and indeed there is no 2.6.20-15-server in /usr/lib.  At what point was that made?

---

### Post by oldcpu on 2007-06-24
Please help.  Or is this the dead end?

---

### Post by logos34 on 2007-06-25
> **oldcpu said:**
> Please help.  Or is this the dead end?

> ln: creating symbolic link '/usr/lib/2.6.20-15-server/build' to '/usr/linux-headers/2.6.20-15-server': No such file or directory

Could it be that the directories have changed since the howto was written?  (it was written for dapper a year ago).  Just a guess. 

maybe 

**/lib/modules/2.6.20-15-server/build**

instead???

Try sending the author of the howto a message.

best of luck getting your wireless going!

some links that might help you (you've probably seen them already):
[https://help.ubuntu.com/community/WifiDocs/Device/Airlink101_AWLL3026](https://help.ubuntu.com/community/WifiDocs/Device/Airlink101_AWLL3026)
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_(ZyDas_zd1211b_driver](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_(ZyDas_zd1211b_driver))

---

### Post by oldcpu on 2007-06-26
> maybe

/lib/modules/2.6.20-15-server/build

instead???
Thanks.  That worked.

However, the next step totally killed it.  There are no drivers for zd1215.

---

### Post by logos34 on 2007-06-26
> There are no drivers for zd1215

None? Is that the 'bad' chipset?

---

### Post by oldcpu on 2007-06-26
Yes.  It is one of those cards that changed its chipset but kept the model number.

At the end of this thread:
[http://ubuntuforums.org/showthread.php?t=403419&page=2](http://ubuntuforums.org/showthread.php?t=403419&page=2)

I had the false impression that it worked, because the user did not post another help message again.

I thought if I swapped the Linux version and the zd1211 driver for the zd1215 I might be able to get it to work.  But appearantly, not.

---

### Post by logos34 on 2007-06-26
> **oldcpu said:**
> Yes.  It is one of those cards that changed its chipset but kept the model number.

At the end of this thread:
[http://ubuntuforums.org/showthread.php?t=403419&page=2](http://ubuntuforums.org/showthread.php?t=403419&page=2)

I had the false impression that it worked, because the user did not post another help message again.

I thought if I swapped the Linux version and the zd1211 driver for the zd1215 I might be able to get it to work.  But appearantly, not.

I went through all this last month while trying to get an airlink awll3026 wireless g usb adapter to work in edgy...I faintly remember the problems some had with the 1215 variation...I guess I lucked out because mine used the zd1211 and I was able to download the community version of the driver listed in the links I gave.  I'm surprised you're having trouble in feisty, though, because wireless worked out of the box on a test install I did at the time.

What make and model wireless card/device is this?  The exact same one?

---

### Post by logos34 on 2007-06-26
Did you try the latest revision of the zd1211, zd1211-driver-r85.tgz?
[http://www.mirrorservice.org/sites/www.ibiblio.org/gentoo/distfiles/%5Bpage=165%5D](http://www.mirrorservice.org/sites/www.ibiblio.org/gentoo/distfiles/%5Bpage=165%5D)

When you compile it you end up with two modules, zd1211 and zd1211b.  If you haven't done this give it a shot, one of them may miraculously work for the 1215 chipset.  Wish I had the answer.

---

### Post by mattg89 on 2007-06-26
I have just set up a zydas chip myself. Which model is it (belkin, netgear...)
The zd1211rw driver is included with the feisty kernel, so you probably shouldn't need to d/l anything - I didn't.
With it connected, type in console "iwconfig" - no quotes, and post the output, that will tell us if it is recognised by the system.

---

### Post by oldcpu on 2007-06-27
> I'm surprised you're having trouble in feisty, though, because wireless worked out of the box on a test install I did at the time.
There should be no surprised.  Because that is only true for the AWLL3026 with a zd1211 chipset.
> What make and model wireless card/device is this? The exact same one?
AirLink101 USB 802.11G (AWLL3026)

zd1215 chipset.

> Did you try the latest revision of the zd1211, zd1211-driver-r85.tgz?
Yes, and failed.
> With it connected, type in console "iwconfig"
```
eth0 802.11 b/g  ESSID: off/any  Nickname:"zd1211"
Mode: Manged  Access Point: Invalid
Link Quality: 0  Signal level: 0  Noise level: 0
Rx invalid nwid: 0  Rx invalid cript: 0  Rx invalid frag: 0
Tx excessive retries: 0  Invalid misc: 0  Missed beacon: 0
```
Note that this is after trying to install the 1211 drivers as suggested by logos34.  So the code may be deceiving.

'lsusb' reads the wireless card as "1215 ZyDAS"

---

