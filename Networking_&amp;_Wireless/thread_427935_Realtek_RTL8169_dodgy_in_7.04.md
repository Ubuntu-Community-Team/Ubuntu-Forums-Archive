---
title: "Realtek RTL8169 dodgy in 7.04"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by bearNeedsCookies on 2007-04-29
Having pain with a PCI based RTL-8169.  It appears to be connected properly, but downloads are dodgy, and copying large files via samba says it'll take 12 hours (for files that should take 12 minutes), then promptly time out.  Runs fine in Windows, but in Feisty, no goodness.

I've seen some posts complaining of similar symptoms in previous versions of Ubuntu, but that (as far as I can tell) was prior to a 8169 driver being included.

Anyone else had similar symptoms?  Or got any ideas of how the further diagnose?

---

### Post by kubug on 2007-05-11
Ditto on that one... it's connecting at 10Mbit/s and poorly at that....

I am running Kubuntu 7.04 and it's TP-Link with a RTL-8169 card.

I haven't tried install any drivers or changing any settings.

---

### Post by kubug on 2007-05-11
Ok, now I got it work (me thinks).....

All I did was enter this in a terminal and it brought the card down and back up with full 1000Mbps.....
[I]
sudo ethtool -s eth1 speed 1000 duplex full autoneg on
[/I]

Now, I did try to download the drivers from either Realtek or TP-Link, and I was not able to compile either one. The instructions in there were from 2004, while the driver was marked as late 2006. I didn't even get the first step done on it. Some real crappy documentation there.

Anyways, I will post again should this not have solved the problem. Otherwise I will blissfully use my Gigabit network.

---

### Post by kubug on 2007-05-11
Ok... well.....

it's better now, but it takes up 100% CPU and is still only about as fast as a 100Mbit connection. 

BTW, I am testing this between two computers which have Gigabit cards and Raid 0 HDD's. I should be getting at least 45MB/s throughput. I am only seeing 5MB/s

Back to the drawing board.

---

### Post by jubxie on 2007-05-15
same here. I would avoid this card if possible. without the driver from realtek, i was getting 100-500 kbps. After using the driver from realtek, it peaks at 5MB/s(megabytes not megabits). funny thing is, going in the other direction, the server gets files from the machine with the realtek card at 12-30MB/s(server has m/b nvidia gigabit).  if anyone can point me towards a linux gigabit success story (including hardware specs) i would be eternally grateful. I'm gonna buy another gigabit card, so I need suggestions. something in the range of 30-50 MB/s would be great. I have good newer hardware(raptor drive on main machine, sata others, dual core opteron exc) if that matters. thanks

---

### Post by jubxie on 2007-05-18
SOLVED!! Well, if any body is curious, NFS is what I needed. I don't have any windows boxes that are used, so I thought I'd try it. I got samba to max out at 10-14MB/s. NFS on the first try was at 35MB/s. My hardware and samba seemed to be what was slowing me down, not the realtek RTL8169. I DID install the driver off the realtek site(r1000), so that may be the real answer to this thread.

This guide works great for using NFS!!!

[http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+vs+smbfs](http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+vs+smbfs)

---

### Post by analogue on 2007-07-30
Ditto. Realtek 8169 + Samba = Slow,  Realtek 8169 + NFS = OK.  I think the Realtek driver is at fault given the amount of digging I have done. Samba appears to exercise network traffic/operations in such a way that it exposes some serious performance problems w/ the Realtek drivers.  Realtek just issued updated drivesr on their website (dated 7/2007) so it might be worth building a kernel w/ those to  see if this Samba problem goes away...

BTW, what are the alternatives for reasonably prices Gigabit ethernet NICs w/ excellent Linux support not based on RT8169?

---

### Post by zimdba on 2007-07-30
1) I was unable to get my netgear G311 working at gigabit speeds.  Manually running "ethtool eth0 -s 1000 duplex xxx autoneg xx" resulted in the interface running at 10Mbps.  Running the command again changed it to 100Mbps.

2) I updated the driver to version 6.002.00 from the realtek website.  The interface will only run at 100Mbps.  Now, mii-tool and mii-diag no longer work.

Are there recommended cards that work at Gigabit ethernet speeds?  Is there a way to downgrade the driver to the original install (7.04 Server) as I didn't make a backup :(

Thanks.

---

### Post by kubug on 2007-12-09
Just to let everyone know, I gave up on that card. It could be a bad card (maybe a problem we all a re having), but I decided it wasn't worth my time anymore. 

I tried one more time with Ubuntu Gutsy, and it seemed to connect fine (1000mbit) but everything was dodgy and slow. I even tried Fedora 7 + 8. I actually set up another server with the same card (same model, not exactly that one card) and it work fine in Fedora.

Anyways, no go.

I went and got an Intel DeskPro 1000 for ~$30. Well worth the money!

---

