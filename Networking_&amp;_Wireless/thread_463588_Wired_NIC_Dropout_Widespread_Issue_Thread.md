---
title: "Wired NIC Dropout Widespread Issue Thread"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by Frankenchrist on 2007-06-03
I am just posting this because it seems that many people are having the issue of their WIRED networks dropping connection or not being able to connect at all.  There are many threads under many different headings that seem to all have the same problem and it seems to be spread across all brands of NIC.  Even if people take issue with the word "widespread" I just basically want to get all of these into the same thread so all of the various workarounds/fixes end up in the same thread.   

[http://ubuntuforums.org/showthread.php?t=463374](http://ubuntuforums.org/showthread.php?t=463374)

[http://ubuntuforums.org/showthread.php?t=463025](http://ubuntuforums.org/showthread.php?t=463025)

[http://ubuntuforums.org/showthread.php?t=8668](http://ubuntuforums.org/showthread.php?t=8668)

[http://ubuntuforums.org/showthread.php?t=465423](http://ubuntuforums.org/showthread.php?t=465423)

[http://ubuntuforums.org/showthread.php?t=463758](http://ubuntuforums.org/showthread.php?t=463758)

I know there are wireless problems as well, but this thread is just for the CAT  5 cowboys  :) .

---

### Post by Frankenchrist on 2007-06-04
Anybody?

---

### Post by Frankenchrist on 2007-06-04
hellooooo?

---

### Post by Frankenchrist on 2007-06-05
C'mon people, there are far too many threads on this?!?!?!?  Hook a brotha up!!!

---

### Post by psychoelf on 2007-06-05
Same problem here.  Wired connection works fine in XP, but drops in Ubuntu.  Only since latest update.

---

### Post by Frankenchrist on 2007-06-06
Yeah, and if you watch the forum, you'll see many new threads started on it fairly regularly.  It just gets lost in the complaints about wireless- which is funny because my ethernet connection is just as unreliable as a wireless can be...

---

### Post by DarkGob on 2007-06-06
Well, I can't speak for anyone else, but installing ndiswrapper through Synaptic seems to have done the trick for me (so far at least).  It's worth a shot.

---

### Post by psychoelf on 2007-06-09
Well, still no luck after latest update.  Any other news on this?  Is ndiswrapper still working for you DarkGob?  Booting back to winders for now.

---

### Post by DarkGob on 2007-06-09
It's hard to say.  I've been getting long stretches of time where I would expect to have lost my connection, but I don't.  The latest updates seemed to help, just not entirely.

After I made my last post in this thread, I started having disconnect problems again (clearly I jinxed it), so I guess ndiswrapper didn't do the wonders I thought it did.

At this point, it's good enough that I've put aside my plans to downgrade to Edgy (mainly because no one will tell me if it's safe to do so with Feisty still in place!).

---

### Post by Frankenchrist on 2007-06-09
well at least you told me it didn't work before I tried it. :)

---

### Post by DarkGob on 2007-06-09
It couldn't hurt (but don't quote me on that! Still a Linux newb here).  Install it via Synaptic, if it doesn't fix the problem, uninstall it.

---

### Post by daverich on 2007-06-10
I'm still getting connection dropouts.

'tis bloody irritating.

Is this in the pot of things being looked at?

Kind regards

Dave Rich

---

### Post by daverich on 2007-06-10
I notice there's a new version of network manager at the gnome site - [http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

I'm too much of a noob to confidently install something like that though. - anyone know whether this is going on a repository soon and whether it fixes this problem?

Kind regards

Dave Rich

---

### Post by DarkGob on 2007-06-10
> **daverich said:**
> I'm still getting connection dropouts.

'tis bloody irritating.

Is this in the pot of things being looked at?

Kind regards

Dave Rich

Assuming you're using a 3Com card, yes, it's a [known bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109629").

That actually brings up a good question.  Exactly how many of us affected by this *are* using 3Com cards?

---

### Post by daverich on 2007-06-11
I'm using a realtek onboard job.

I do have a belkin LAN card, but ubuntu wont see it let alone use it.

Kind regards

Dave Rich

---

### Post by daverich on 2007-06-11
hmm just looked at that link and no i think this is a different bug. Mine is not speed dependant. It actually seems to happen after I've been reading a web page for a while.

Kind regards

Dave Rich

---

### Post by Frankenchrist on 2007-06-13
Here's another one...

[http://ubuntuforums.org/showthread.php?t=466821](http://ubuntuforums.org/showthread.php?t=466821)

---

### Post by Frankenchrist on 2007-06-17
Hello?

[http://ubuntuforums.org/showthread.php?t=475476](http://ubuntuforums.org/showthread.php?t=475476)

[http://ubuntuforums.org/showthread.php?t=468941](http://ubuntuforums.org/showthread.php?t=468941)

---

### Post by DarkGob on 2007-06-18
Nobody knows.  It's a bug (low priority, from the looks of it).  We'll have an answer once it's fixed.

---

### Post by Frankenchrist on 2007-06-18
I know it's a bug, but for the life of me I can't tell how it's been determined that it's a low priority.  You need your internet connection.

---

### Post by psychoelf on 2007-06-26
Still no fixes?  Back to XP for awhile then...](*,)

---

### Post by Blackwyr on 2007-06-26
I'm right here with you folks. Ran the update last night, and now the wired connection won't connect at all. Running an integrated NIC through a Linksys router and cable modem to Comcast. Any insights or suggestions? When I try to pull up the connection information, it either says it cannot find the file, or shows me a window with all zeros for my IP, subnet, gateway, etc.

Essentially total Ubuntu n00b here, so any advice would be greatly appreciated. :)

---

### Post by maak on 2007-06-27
Same problems... on board NIC wired to a Netgear router connected to Bell South.  Frequent episodes of loss of connectivity for about 30 sec, and then comes back on.  Really annoying!

---

### Post by Frankenchrist on 2007-06-27
Yeah, the networking and wireless thread really could have this and a wireless dropout thread as a sticky and it would save them forum space.  I would like to get my little file server back online but I'm not wasting time with things like this anymore, I'll just wait for another release or distro.

---

### Post by Dilutu on 2007-06-28
Since one of the latest updates, I sometimes have to reboot to connect to my wired network, and that only happens on my 2 Ubuntu computers....

---

### Post by psychoelf on 2007-06-29
Switched to the latest version of Debian and everything is working fine now.  I hope they fix whatever the problem was soon.  As a linux newb, I like all the easy bells and whistles of Ubuntu.

---

### Post by ap9er on 2007-07-01
My 3com router seems to be unresponsive in Fiesty as soon as I connect to usenet (either through hellanzb or klibido). This is annoying as hell as I either have to reboot or manually disconnect the ethernet jack and hope that it works again, which it doesn't always do.
This only started happening less than a week ago. 

I'm thinking of getting the old Linksys router out of the cupboard and seeing if the problem is between the Ubuntu and the router or the chipset on the motherboard.

---

### Post by ubergeeknz on 2007-07-01
I am having same problems.  My network connection becomes unavailable for about 30 second bursts, seemingly at random.

This is occuring on my HP Compaq nx8220 notebook, which has an onboard NIC.

This was working fine a while ago, so it is probably due to an update.  I will try loading older kernels and see if anything gets fixed.

---

### Post by ubergeeknz on 2007-07-01
Hi .. I have gone all the way back to 2.6.17-11 and this is still happening...  Any clues anyone?  I have even set the NIC to "manual configuration" (DHCP) so it doesn't seem to be network manager.  If I run a continuous PING I don't get any error messages, the pings just seem to get dropped.  ALso there seems to be nothing in syslog, messages etc.

---

### Post by imasickboy on 2007-07-02
I have the same issues as everyone else. I'm using Dapper, and there are some old 2.4 kernels in the repositories, so I'm going to try going that far back and see if it helps. I've tried OpenSuse, with better results, (as in same problem, but less frequently). I'm also going to give ndiswrapper a shot. I'm desperate for a fix, and Windows will not be an option. If none of those options work, I'll keep trying other distros until something works. I guess my next will be the latest Debian, as someone said above that that was working for them.

Edit: I have tried ndiswrapper, no luck. I have tried a 2.4 kernel, and cannot boot. I also have two cards in my machine, one is a Linksys, and the other is a Trendnet with a Realtek chipset. The problem exists with both cards, but it seems that the Linksys drops off much less frequently.

Edit 2: Scratch what I said about the Linksys card dropping less often. Grrrr. I have downloaded Debian, and will be installing it shortly. Hopefully all will go well and I can have a stable connection again.

---

### Post by cunan on 2007-07-04
I'm having the same issue with a Marvell Gigabit onboard NIC. This seems to happen most when I'm transfering large files (I use my ubuntu box as a data server), but that could be completely anecdotal. 

/etc/init.d/networking restart doesn't work, but a full reboot usually does (gah!) This is fairly crippling.

---

### Post by Frankenchrist on 2007-07-04
No fixes as of yet...

---

### Post by ap9er on 2007-07-05
I couldn't get my linksys router to work so no test there (it has problems with the port conections, hence its place in the cupboard).
Anyway, Fedora was handling the situation much better without dropping the connection. Tried the release disk of Fesity, but no luck there; problems seemed even worse. Moved over to Archlinux and it seems to be fine now.

I'll see how things fare with Gusty Gibbon, although I think I've found my new distro of choice now.

---

### Post by simpsonsfan74 on 2007-07-05
I'm having the same issue, too.  eth0 is my wired Gig-E card and eth1 is my wireless 802.11g card.  I usually book with the wired connection plugged in.  Probably two thirds of the time I boot just fine and everything works, but the other 1/3 of the time the DHCP request times out and I get a 169.x.x.x IP address. I can't seem to get NetworkManager to give me a proper address, even if I restart networking and dbus.  Other than a full reboot, I can work around the problem by using wireless- it works with NetworkManager and DHCP even if the wired connection doesn't.

Note: I installed using the alternate CD because I've got a SATA drive on my laptop, and the Ubuntu installation told me it couldn't find my Gig-E network adapter.  It's an Attansic Technology Corp. L1 Gigabit Ethernet Adapter, and I found that it's only supported in the kernel with 2.6.22, I think.  But when I booted for the first time, I got internet with it just fine!  So it may be related to that, but I still don't know what to think about NetworkManager.

Anyone else have any ideas?
Anyone else using an Attansic Gig-E card?

---

### Post by ubergeeknz on 2007-07-06
I set my NIC to static IP.. and the problem seems to be gone.  So I figure it must be somehow related to DHCP.  Didn't seem to matter if I am using dhcp without network-manager installed, or dhcp within network-manager

---

### Post by imasickboy on 2007-07-06
> **ubergeeknz said:**
> I set my NIC to static IP.. and the problem seems to be gone.  

When my problem first began, I was running a static IP. Ever since, I've been using DHCP, with no improvement. On a lark, I switched back to static, and oddly enough, I haven't had any drops for the last two hours. I am not holding my breath that it will stay that way, though. But I am very happy for the moment.

Edit: Never mind. Still drops.

Edit 2: Disabled IPv6 system-wide, and so far so good, but I've said that before...lol

Edit 3: No help. Added a question to launchpad [https://answers.launchpad.net/ubuntu/+question/9400](https://answers.launchpad.net/ubuntu/+question/9400)

---

### Post by ubergeeknz on 2007-07-09
> **imasickboy said:**
> When my problem first began, I was running a static IP. Ever since, I've been using DHCP, with no improvement. On a lark, I switched back to static, and oddly enough, I haven't had any drops for the last two hours. I am not holding my breath that it will stay that way, though. But I am very happy for the moment.

Edit: Never mind. Still drops.

Edit 2: Disabled IPv6 system-wide, and so far so good, but I've said that before...lol

Edit 3: No help. Added a question to launchpad [https://answers.launchpad.net/ubuntu/+question/9400](https://answers.launchpad.net/ubuntu/+question/9400)

Interesting.  Well I will test again when I get the new HDD from HP for my notebook (it died) and run a ping all day to see what happens... it does at least seem to be a bit more stable...

This could be a show-stopper for me, I use a lot of remote desktop and vmware console which are pretty touchy about network dropouts.  Also playing mp3's off the LAN sucks if it drops out :(

---

### Post by imasickboy on 2007-07-11
EGADS! I think I have found the answer!

I started getting concerned that perhaps I was having mobo problems, possibly "losing" the NIC because this was occurring with two different NICs, no matter what pci slot they were in, and it was happening in Dapper, Fiesty, OpenSuse, and Debian. When it happened, the "physically connected" light would go out in my router as if I had unplugged the cable. So I through in an old HDD and tossed WinXP on it...and the problem persisted. However, in XP, I was easily able to check or change the NIC settings, because I was more familiar with them. I DISABLED autosense, and set the NIC to 10baseT. The disconnects stopped immediately. I yanked the HDD, booted into Ubuntu, and started hunting around. I found this:

[http://www.digizenstudio.com/blog/categories/lamp/ubuntu/](http://www.digizenstudio.com/blog/categories/lamp/ubuntu/)

About halfway down the page, with the header My Ubuntu Experience: Networking

NOTE: His post addresses DHCP. I am set for static, but this problem has persisted for me whether I was using a static IP or DHCP.

Add this script to /etc/network/if-pre-up.d:

```
#!/bin/sh

ETHTOOL=/usr/sbin/ethtool

if [ ! -x $ETHTOOL ]; then

exit 0

fi

if [ "$IFACE" = "eth0" ]; then

echo disabling $IFACE auto negotiation

$ETHTOOL -s $IFACE autoneg off

fi

```

Save it as whatever you like, make it executable, and 

```
sudo ifdown -a
```

followed by 

```
sudo ifup -a
```

So far, two hours with no disconnects, which is roughly one hour and 55 minutes longer than I usually go without the connection dropping. If this is the solution, I cannot possibly imagine what would have caused it to start, but I am happy to have some stability for a change.

---

### Post by Zyrshnikashnu on 2007-07-11
I'm afraid your script fails to fix the issue of no connection at all.

---

### Post by slayer666metallica on 2007-07-13
I'm having the same problem too. It doesn't matter if I'm even on the internet or not; the connection just drops out at random and then will come back on immediately and tell me I'm reconnected. 


I'm on a wired Linksys router and my NIC is just the integrated one that came with my MSI K9N4 SLI-F Motherboard;

..and worst of all I'm a total n00b to Linux [used it for only 1 day so far :D] so I don't even know how to go about fixing the problem.....but it's nice to know that I'm not alone :D


..but if it's a bug; I HOPE IT GETS WORKED OUT SOON....because it really stinks when trying to download OS/Prog. updates or just when trying to use the 'net connection in general O_O....


...I hope a solution will arise soon. This is VERY frustrating for n00bs like me..lol...

---

### Post by slayer666metallica on 2007-07-13
I know this might sound like a stupid solution...hell; it may not even BE a solution--just a coincidence...

..but after I stopped using my proprietary nVidia accelerated graphics driver; I haven't experienced any dropouts yet!


Kind of odd; but it's the truth. 


What I'll do though is enable it back and see if dropouts occur again. 

If they do; then I'll know that the nVidia driver is causing something with my internet connection to go awry. 


I know it sounds retarded and crazy; but hey; I'll give it a shot :-k

---

### Post by Frankenchrist on 2007-07-15
I've had this issue without installing a proprietary Nvidia graphics driver...

---

### Post by psychoelf on 2007-08-16
So, I've been using Debian with no problems.  I thought "maybe Ubuntu will be better now".  Did a fresh install today, and you know what?  I'm posting from Windows.  I'm not sure what is going on.  I used the same install CD that I used when Ubuntu was working.  I did not install any updates (unless Ubuntu did itself without my knowledge).  Very strange.  I like Debian though, so I think I'll stick with it.

---

### Post by etstar on 2007-12-05
> **cunan said:**
> I'm having the same issue with a Marvell Gigabit onboard NIC. This seems to happen most when I'm transferring large files (I use my ubuntu box as a data server), but that could be completely anecdotal. 

/etc/init.d/networking restart doesn't work, but a full reboot usually does (gah!) This is fairly crippling.

same here. you aren't running on an xpc shuttle perchance, are you?

i can easily trigger a dropout only fixable with a reboot by transferring a healthy amount of data. as long as i'm just surfing or something with a minimum of traffic it's fine.

and /etc/init.d/networking restart doesn't work either.

---

