---
title: "wireless randomly dies"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by ljp37 on 2007-08-20
I'm hoping some has seen this before--

I'll be using my wireless network, and then all of a sudden
the connection will drop dead.  The network-manager applet then
proceeds to do its "connecting..." animation ad infinitum, and the
connection never returns.  This happens seemingly at random; I'm not
moving, the AP isn't moving, and my other laptop's wifi continues to work
just fine.  It doesn't correlate with inactivity, either. 

iwlist -scan shows that the AP's signal is still strong.

dmesg reveals that the wifi is being constantly restarted when this happens:

[103818.396000] bridge-eth0: disabling the bridge
[103818.416000] bridge-eth0: down
[103818.420000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[103818.420000] bridge-eth0: enabling the bridge
[103818.420000] bridge-eth0: is a Wireless Adapter
[103818.420000] bridge-eth0: up
[103921.548000] bridge-eth0: disabling the bridge
[103921.560000] bridge-eth0: down
[103921.568000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[103921.568000] bridge-eth0: enabling the bridge
[103921.568000] bridge-eth0: is a Wireless Adapter
[103921.568000] bridge-eth0: up
[103964.684000] bridge-eth0: disabling the bridge
[103964.696000] bridge-eth0: down
[103964.704000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[103964.704000] bridge-eth0: enabling the bridge
[103964.704000] bridge-eth0: is a Wireless Adapter
[103964.704000] bridge-eth0: up
[103985.660000] bridge-eth0: disabling the bridge
[103985.672000] bridge-eth0: down
[etc...]


Does anyone know even how I would begin to debug this?  Is it the
wireless driver, or the network manager gone mad?

I'm using a Toshiba Portege M400 with Feisty.  The wireless chipset as shown by
lspc, is Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

Thanks for your attention =)

---

### Post by wickstopher on 2007-08-21
I'm not all that technically inclined, but I've had the same problem with my wireless connection on my desktop.  I have since disabled the network-manager applet in sessions, and am experiencing 90% fewer or better disconnects.  I'm not sure why, but it just seems to work for me.  Before, I was getting disconnected every 30 minutes or so.  Perhaps there is some sort of conflict between the applet and the base network-manager?  Any thoughts on this would be appreciated.  Let me know if this works for you.

---

### Post by ljp37 on 2007-08-21
I've been hesitant to nuke the nm-applet (when it works it's useful), but now that I think about it, this didn't happen when I was using KDE...

---

### Post by wickstopher on 2007-08-22
Well, it's worth a try, I suppose.  You can always get the applet back. ;)

Let me know if it works for you...it SEEMS to be working for me.  I'm getting far fewer disconnects thus far, like maybe one or two a day, as opposed to before when I was getting 10 or more a day.  Perhaps it's just a placebo effect, but hey, at least I'm happy.  This is definitely something that needs to be addressed by the developers, however.  It should be coded so that if the network disconnects, it automagically reconnects without all the fuss and muss of unclicking and reclicking your wireless network in the System > Administration > Network window.  I wish I was a bit more technically inclined to better describe and research the problem myself, and report a better worded techincal account of the problem to the developers (anyone out there who is capable of such action, take note!), but this solution is all I've got for now.

---

### Post by ljp37 on 2007-08-28
I experience fewer disconnects without nm-applet, but they still happen. It is worth mentioning that this seems to happen more often when there is more wireless traffic (e.g. my roommate watching youtube) and also worth mentioning that even though my signal is the strongest, there are always several other wireless networks visible from here and possibly interfering (tho none are on the same channel)

---

### Post by wickstopher on 2007-08-28
I just installed wicd (and, as a result, uninstalled network-manager), so we'll see where that gets me.  I'll report back here in a couple of days to let you know how it's been with the disconnects and whatnot.  So far so good, wireless is working.  There's an option to "automatically reconnect on connection loss," which is somewhat encouraging.  It is also the first time ever in linux a wireless applet has shown my correct signal strength.  Well, I suppose that there's no way of knowing for sure that it's correct, but 87% signal strength sounds a bit more accurate than "0%" or "-1%" when I'm obviously downloading files at 500-800k/second. ;)

simple instructions for downloading and installing it in ubuntu (it's not in the repos) can be found here: [http://wicd.sourceforge.net/download.php]("http://wicd.sourceforge.net/download.php")

On a slightly off-topic (but not so enough/not important enough to start a new thread) tip, I've been fooling around with Cassandra (LinuxMint) on another partition, and despite being based on Feisty, I can't get wireless working at all.  I've tried identical setups with network-manager and also wicd, and it just won't connect to my network.  It sees it, and a few other wireless networks in my neighborhood, but won't connect.  A tad perplexing, but, like I said, I'm not switching over to LinuxMint anytime soon (if ever).  Just was wondering if anybody has a clue as to why that is.

---

### Post by kevdog on 2007-08-28
What driver are you using??? I have a broadcom 4306 chipset with ndiswrapper/bcmwl5 driver and have noticed spontaneous drops about 30 minutes or so (a very rough estimate).  I made a script that attempts to ping the router every 5 minutes (cron daemon), and if no response occurs (ie a timeout), it automatically brings up and down the network.  I made a log for this, and after initiating this script, Im not seeing as many dropped connections as usual.  Maybe its just the outgoing ping every 5 minutes that helps.  Im not sure.  Again I only notice the drops when the network is idle, not active.

---

### Post by wickstopher on 2007-08-28
I don't have any experience with ndiswrapper (well, actually, I've just never been able to get the damn thing to work, but my WUSB54G works out of the box with Ubuntu....no other distros, though, and ndiswrapper has, thus far, failed me miserably).  I'm pretty sure with your card, though, there is no other option.  Apparently you can use ndiswrapper through wicd by clicking on the "Preferences" button and choosing ndiswrapper as your WPA Supplicant driver (my driver is wext).  If you haven't tried wicd yet, give it a shot.  This advice is based on my own (admittedly very little) experience thus far with wicd, but if you're having problems, I would say it's worth a try.  I can't wait for the day when this whole wireless issue with Linux is under control!

---

### Post by wickstopher on 2007-08-30
Well, since installing wicd I've gone 1 day and 30 minutes straight without a disconnect.  Or at least, without a noticeable, annoying, productivity-halting disconnect where I have to go back to Network, enter my password, turn my wireless connection off, then on again.  Et cetera.  That's probably the longest I've ever gone since installing Ubuntu.  I'll let it go another couple of days and see how it goes, and report back here again, just in case anybody is curious.

---

### Post by wickstopher on 2007-09-02
After several days of using wicd in place of network-manager, I have to say that it is a vast improvement to the overall experience of wireless linux.  Whereas before I was getting 10-20 instances per day in which my wireless would cut out and I would have to reset the connection via System>Administration>Network, this has been reduced to on average once every day or two, if not less.  On top of that, the notification area applet for wicd allows me to much more easily restart the connection if it does drop.  Just right click on the applet, and hit connect, and you're going again in 5 seconds, as opposed to the 1-2 minutes it takes via the previous method.  So, in conclusion, anyone with issues using their wireless in Ubuntu should definitely give wicd a try.  This is, of course, assuming you have wireless up and functional to a certain degree given the provided tools with the distribution.  I'd be interested to hear about other people's experiences with wicd, so feel free to post here and share.

---

### Post by wickstopher on 2007-09-12
I just wanted to update here and report that, since installing Kubuntu 7.04, I have not been experiencing any such problems with knetworkmanager.  Very nice.

---

