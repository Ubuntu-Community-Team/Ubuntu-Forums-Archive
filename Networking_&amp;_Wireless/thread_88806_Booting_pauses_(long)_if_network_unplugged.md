---
title: "Booting pauses (long) if network unplugged"
date: 2005-11-11
forum: Networking &amp; Wireless
---

### Post by schilcha on 2005-11-11
Hi there!

I just installed breezy on my notebook. I obtain IP-adresses automatically via dhcp -- no problem. However, if I boot without connection to the network (offline), booting takes a long pause when configuring the network devices -- presumably waiting for an answer from dhcpd. 

Looking at the man-page of dhclient, the options "-nw" seem to be a solution for this. Sadly, I can't try it, since I don't know, where to supply these options. 

So, two questions:
How do I tell dhclient not to wait too lonk or to wait in the background?
If the "-nw" command line parameter is a good solution, where do I activate them for next boot?

Thanks!

---

### Post by floe-de on 2005-11-11
Hi,
I don't know exactly if you have the same problem I have, but you can try it.

In removed the service /etc/init.d/hotplug-net from the startup routine by
entering the command "sudo update-rc.d -f hotplug-net remove" in the folder of the file.

Because in this startup file you see a very long timeout that blocks the boot process when no network cable is connected.

Bye
Flo

---

### Post by schilcha on 2005-11-11
Thanks for this hint.

I removed the hotplug-net entries in the rc?.d directories, rebooted and had the same pause in the boot process.

I used to have SuSE (9.2), which explicitly said, that dhcp-client is being backgrounded after ~10 seconds (this even happened on slow dhcp servers). I would like to get to this setup with ubuntu as well.

---

### Post by BRODEL on 2005-11-12
I think I have the same issue. I timed my boot up this morning on my laptop. It took about 2 minutes from the time I hit enter in Grub to load ubuntu to the time it showed me the login screen. About half of this time it was sitting at "configuring network devices" I guess it would of went faster if I turned off my built in ethernet card. That is kind of a pain though because I take this laptop to a lot of different places. Most ot the time, I just use wireless, but sometimes I use the wired connection so I don't want to just disable it all together. I could see waiting 10 seconds or so, but a whole minute or more is a bit much. I am going to try rebooting after disabling the connection and see if that helps. I just thought about trying that after reading your thread.

---

### Post by spizkapa on 2005-11-12
A cheap solution is to press "control C" when the computer is trying to raise the netowrk interface. It will interrupt the network setup which is fine if you're going to be off-line anyway and you can start it manually afterwards when already booted.

This is particularly useful for ntp updates which take a long time to fail on their own.

---

### Post by spizkapa on 2005-11-12
[QUOTE=schilcha]I removed the hotplug-net entries in the rc?.d directories, rebooted and had the same pause in the boot process.[/QUOTE]

You really should not be fiddling with the entries in rcX.d manually. They are best handled by the update-rc.d command. Do:

man update-rc.d

to see what it does. It is complicated but safer than removing scripts manually.

For quick reference, all scripts that are run at start-up take a start, stop, restart option and live in /etc/init.d/. They are then symlinked by updated-rc.d into /etc/rcX.d/ where X is a number for the runlevel. rcS.d is the only place where you have actual symlinks made by hand and which you could remove.

Do not remove anything from /etc/init.d/, those scripts are not run from that directory, only from symbolic links.

---

### Post by BRODEL on 2005-11-12
[QUOTE=spizkapa]A cheap solution is to press "control C" when the computer is trying to raise the netowrk interface. It will interrupt the network setup which is fine if you're going to be off-line anyway and you can start it manually afterwards when already booted.

This is particularly useful for ntp updates which take a long time to fail on their own.[/QUOTE]

Thanks for the tip. I didn't know that. 

I just rebooted and it took a little less than a minute for it to boot after disabling the onboard NIC. That's good enough for me. :)

---

### Post by spizkapa on 2005-11-12
Oops, forgot to leave an example, silly of me. If, for example, you had already booted your computer and then changed some networking settings fom the networking applet in gnome, when you apply the settings, it will basically be doing:

sudo /etc/init.d/networking restart

in the background. You can often do that yourself without bothering with the applet.

Another very useful one is:

sudo /etc/init.d/gdm restart

which is something you'd run from a terminal if your X session dies or the graphics or something is screwed up. It will take down gdm (and the X server that gdm namanges) and then restart it cleanly and leave you at log in.

HTH.

---

### Post by spizkapa on 2005-11-12
Darn, just missed your reply. I believe your problem is the ntp update which takes place from rcS.d. For this one, it is safe to do:

sudo rm /etc/rcS.d/ntpdate

because it's only a symlink to the actual script as described above. I'm not really sure why it's necessary to update the clock anyway,  I tend to disable it on my work laptop which needs to authenticate itself first before it can connect to the internet.

---

### Post by BRODEL on 2005-11-12
really? Even though it says configuring network devices? I thought it was just waiting on a DHCP address or something. I was wondering if there was a way to set the wait to like 10 secs, but I can either leave it disabled, or just enable it again and hit control C since you said it would force it to move along.

---

### Post by ninja_indiano on 2005-11-12
[QUOTE=spizkapa]
because it's only a symlink to the actual script as described above. I'm not really sure why it's necessary to update the clock anyway,  I tend to disable it on my work laptop which needs to authenticate itself first before it can connect to the internet.[/QUOTE]

Having same problemes with the boot....it take to longs....(my friends are now asking why not use windows that it's way faster LOL)

New in the linux word..how can I disable de clock update? I tinhk I don't need it...?

Can you give me some more info on how to mess around de start up stuff?  I mostly use wirelless, some times ethernet card.  What stuff do I need in the Start up?

P.S What is the clock for? in may case it always fails.....

---

### Post by schilcha on 2005-11-12
For now, I think I'll live with CTRL-C while booting and restart the network as soon as I plugin the cable. It's not really a clean solution, but it works. Additionally I decreased the timeout parameter in dhclient.conf to 20, so unsupervised booting should work in a more reasonable time.

However, I've been looking further for a solution and found two threads that deal with the same topic:

*)[http://www.ubuntuforums.org/showthread.php?t=60486]("http://www.ubuntuforums.org/showthread.php?t=60486")
*)[http://www.ubuntuforums.org/showthread.php?t=13461]("http://www.ubuntuforums.org/showthread.php?t=13461")

The suggestions there were to use ifplugd (additionally to dhclient?) or dhcpd instead of dhclient. I installed dhcpd (which is also used by suse), but when I tried to remove dhclient, the package manager said I should also remove ubuntu-miminal (or something like this), which I didn't dare. Furthermore, I wouldn't know how to tell ifup to use dhcpd instead of dhclient (would I have to). 

Anyways, this seems to be too much efforts for this issue.

---

### Post by schilcha on 2005-11-12
[QUOTE=ninja_indiano]Having same problemes with the boot....it take to longs....(my friends are now asking why not use windows that it's way faster LOL)

New in the linux word..how can I disable de clock update? I tinhk I don't need it...?

Can you give me some more info on how to mess around de start up stuff?  I mostly use wirelless, some times ethernet card.  What stuff do I need in the Start up?

P.S What is the clock for? in may case it always fails.....[/QUOTE]
I guess you mean the clock update via the network-time protocoll. Ubuntu tries to synchronise your hardware clock with some external time-server. It is defined in the file /etc/defaults/ntpdate. By default, the server is ntp.ubuntulinux.org. Maybe a firewall blocks synchronizing activities. 
If you want to get rid of this, run "update-rc.d -f ntpdate remove". Alternatively you can try to set to a different server or reconfigure your firewall rules (if you have access).

---

### Post by schilcha on 2005-11-12
Finally!

Finally, I found a satisfying solution. Since I didn't manage to configure dhclient to accept the -nw flag, I rebuilt ifup, which calls dhclient with hard-coded command line parameters. I added the "-nw" flag to the dhclient- and dhclient3-calls in inet.defn, built ifup, replaced the executable in /sbin and now it works:

Booting without network connection does no longer pause upon configuration of networks.
When I replug the cable, the IP-address is assigned automagically (no need to restart networking!)

I hope this doesn't skrew up something else, but up to now everything seems to work as before.

---

### Post by hw-tph on 2005-11-12
Edit: Never mind.

---

