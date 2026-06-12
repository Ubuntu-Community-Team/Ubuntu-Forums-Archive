---
title: "[SOLVED] Ubuntu and my iPod"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by Cadeyrn on 2008-12-20
Long story short: Between me and my brother are two iPods: a 5.5 generation Video and 6 generation Video. We once each had a backup of our 100 GB of music, half of which was retrieved virtually and therefore has no backup besides our two external hard drives.

For certain reasons, both of our backups were wiped and my iPod wasn't current. Our only hope to get it all back is to copy the music files from my brother's iPod. I already have Banshee and Amarok installed, and my brother's iPod is plugged in right now.

The problem is every guide to making Ubuntu recognize my iPod says Ubuntu should already recognize it as some kind of disk or media device. But when I plug it in, nothing happens. The iPod doesn't even give the "Do Not Disconnect" screen. And because all of the guides say Ubuntu should automatically recognize the iPod, I can't find ANY help online for forcing the pod to get the hell on my system.

I already tried dmesg | tail and got this:

```
[  192.977185] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  400.030658] CE: hpet increasing min_delta_ns to 15000 nsec
[  774.384755] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  792.373039] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  801.317826] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  804.457934] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 1846.337689] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 1864.248541] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 1872.664925] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 1875.808826] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready

```

And then nothing happens. How can I make 5.5 and 6 generation iPods be recognized as something that's plugged into the USB port at all???

---

### Post by ComputerHermit on 2008-12-20
I been having problems in my ipod tuch and ubuntu I been flowing this [http://ubuntuforums.org/showthread.php?t=588246&page=2]("http://ubuntuforums.org/showthread.php?t=588246&page=2")

link 

still having problems :confused:

---

### Post by Cadeyrn on 2008-12-20
Argh, what is with Ubuntu and newer iPods?!?!?!

---

### Post by jimmy the saint on 2008-12-20
[http://www.theipodway.com/tag/hash/](http://www.theipodway.com/tag/hash/)
If you read a few of those articles you will get an idea of what is going on.  Essentially, apple locked out Linux users by rehashing the itunesdb.  It was a deliberate move to prevent any non-itunes software from accessing the ituenesdb.  This essentially means that iphones/ipod touches are inaccessible from ANY software except itunes.  You can use a virtual machine to add/remove songs and video, but you cannot upgrade, restore a backup or do any system level operations as the Virtual Machines do not do will with the necessary protocols.  

Don't be suprised here.  Apple makes M$ look like a free loving and open society.  The same thing happened with the last generation, but the hashing mechanism only took three days to reverse engineer.  This time it is taking longer, but we should see some good news around the new year (give or take).  Apple is bullying the devs, but the EFF is involved now and Apple has no leg to stand on because the DMCA specifically allows for projects to create interoperability fixes.  

Have patience.  it will be fixed.  In the future, buy a music player that is less restrictive.  I just bought an iphone and it was my first, and definitely my last apple purchase.  It will work eventually, but for right now, you just have to live with the consequences of purchasing hardware from a company that sees fit to spend lots of time figuring out ways to prevent you from using it with the OS of your choice.

---

### Post by Cadeyrn on 2008-12-20
Screw iPod. They stupidly discontinued the 160G anyway, and my music collection is at 100G and rising extremely fast.

I'm gonna look up alternatives.

---

### Post by cozmicharlie on 2008-12-21
This is a good source of info for anyone looking for an ipod alternative.
[http://www.anythingbutipod.com/](http://www.anythingbutipod.com/)

---

### Post by schnauzer93 on 2008-12-21
> **jimmy the saint said:**
> [http://www.theipodway.com/tag/hash/](http://www.theipodway.com/tag/hash/)
If you read a few of those articles you will get an idea of what is going on.  Essentially, apple locked out Linux users by rehashing the itunesdb.  It was a deliberate move to prevent any non-itunes software from accessing the ituenesdb.  This essentially means that iphones/ipod touches are inaccessible from ANY software except itunes.  You can use a virtual machine to add/remove songs and video, but you cannot upgrade, restore a backup or do any system level operations as the Virtual Machines do not do will with the necessary protocols.  

Don't be suprised here.  Apple makes M$ look like a free loving and open society.  The same thing happened with the last generation, but the hashing mechanism only took three days to reverse engineer.  This time it is taking longer, but we should see some good news around the new year (give or take).  Apple is bullying the devs, but the EFF is involved now and Apple has no leg to stand on because the DMCA specifically allows for projects to create interoperability fixes.  

Have patience.  it will be fixed.  In the future, buy a music player that is less restrictive.  I just bought an iphone and it was my first, and definitely my last apple purchase.  It will work eventually, but for right now, you just have to live with the consequences of purchasing hardware from a company that sees fit to spend lots of time figuring out ways to prevent you from using it with the OS of your choice.

Seconded. Never again will I buy an Apple product.

---

### Post by bren on 2008-12-21
try amarok

it can cope with hash introduced by apple in ipod nano etc

works for me

---

### Post by skathmandoo on 2008-12-22
i thought my ipod(80gb) worked fine with ubuntu until i realised today that it has totally messed up my cover art.all the album covers are mixed up as  well. any way to fix this?

---

### Post by jimmy the saint on 2008-12-22
DO NOT USE AMAROK ON THE NEWEST IPODS AND IPHONES!!  the last gerneration had a hash the was reversed in days, therefore Amarok and other players can handle it.  The newest versions have a new hash that has not yet been reversed.  Until it has, you can use Amarok, but it will frag your database.

---

### Post by cozmicharlie on 2008-12-22
> **jimmy the saint said:**
> DO NOT USE AMAROK ON THE NEWEST IPODS AND IPHONES!!  the last gerneration had a hash the was reversed in days, therefore Amarok and other players can handle it.  The newest versions have a new hash that has not yet been reversed.  Until it has, you can use Amarok, but it will frag your database.

Thanks for the info.  Is their any package (gtkpod, Rythmbox etc) we can use on the new Ipods yet?  It would be helpful to list them if you know what generation Ipods are affected.

Thanks again

---

