---
title: "STARtech 4 port PCI RAID controller Issues ( Silicon Image 3114)"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by mancdan on 2009-04-21
Hello all,

First of all can I just say I am a complete newbie to Linux! I have literally followed this basic step by step of how to create a fileserever:
[http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1)

I am using the following hardware

Dell Optiplex GX270
40GB IDE hard disk which is running Xubuntu.
1 Startech 4 port PCI raid controller which is based on the Silicon Image 3114 chipset.
with two 1TB Seagate barracudas attached.

To give you some context, the first problem I had was the PCI card was not being recognized and I could not access the RAID utility. 
(Whilst I had this problem I needed to use one of the HDs for some quick storage so I stuck it into a USB caddy and used it for some temporary storage). 

I then updated the BIOS on the GX270 and the RAID card. This seemed to work and gave me access to the raid utility! Great! Then I connected the first drive (the one that was in the caddy - the data on it is now not needed, and a fresh out of the box second drive (unformatted)). I entered the RAID utility and created a RAID1 set. It asked me if I wanted to copy the first drive to the second I said yes (even though the second was not formatted - I don't know if this makes a difference). This seemed to work after a while. However when I enter Xubuntu the drives are not detected at all.

As I said I am an ABSOLUTE beginner. I just need some basic help and a bit of patience to try and get this up and running. I have looked around and found that some people seem to have this card running with Ubuntu no problems and some are having real issues. If any one can help it is much appreciated. If I need to format both of the SATA drives thats fine I just don't know how to go about it in Xubuntu. Yeah I know that is seriously beginner territory but I did warn you guys!

BR

Dan

---

### Post by cariboo on 2009-04-22
Do the drives show up when you run in a terminal:

```
sudo fdisk -l
```

have a look at the [FakeRaid Howto]("http://help.ubuntu.com/community/FakeRaidHowto")

Even though you have a real raid adapter, it should help get your raid array up and running.

---

