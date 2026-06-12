---
title: "[SOLVED] Network freeze when using SMB"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by Menelian on 2007-10-21
Hello everyone.

I'm pretty new to linux and have run into a problem that I haven't been able to find any information about.  I've recently installed Ubuntu 7.10 on a desktop box and everything seems to be working fine after a little configuring/customizing with one exception:

Whenever I attempt to pull  files from a windows share on my network (wired) , my network adapter on ubuntu seems to freeze / lockup.  I can almost always pull several files before this happens, but I'm not even close to halfway through transferring my mp3's after 10+ attempts.  The only way I've found to fix the problem is to restart.  I've tried ifdown/up as well as networking stop/start nothing seems to affect the adapter once it freezes.

Here's some additional information that may help.

results of lspci |grep Ethernet
Ethernet controller:  VIA Technologies, Inc.  VT6102 [Rhine-II] (rev 78 )

After the ethernet adapter freezes, I don't receive any packets from the network, and all pings fail.  Interestingly the activity led still blinks on my switch so it seems like information is still being transmitted, just not received.  I can however ping the loopback adapter (127.0.0.1) without problems.

I can view web sites and download files all day with no problem, but SMB file transfers will kill me every time.

Well, thats it..  I'm stumped.  I'm hoping someone else out there will have an answer for me.

Thanks.

---

### Post by dmizer on 2007-10-22
how are you mounting/browsing your shares (fstab, nautilus)?

if you wait long enough:
1) does the file eventually copy?
2) do you regain controll of the adapter?

---

### Post by Menelian on 2007-10-22
Generally I am accessing shares hosted on an XP machine via the GUI  (Places --> Connect to server...)

I have also created a share on the Ubuntu machine and tried to paste files to it from the windows machine with the same results.

Once the adapter freezes I've found no way to regain control of it short of a reboot.  No amount of waiting (tried several hours) returns the adapter to a usable state.  :(

*EDIT*

Also, to answer your question about the file eventually copying:  After a reboot I can attempt to copy the same file that the transfer failed on.  It may complete, or it may not.  If it does the adapter will lockup on subsequent file.  I've tried this many times now, and sometimes I can transfer over 100MB of music files before it freezes.  Other times I'm unable to successfully transfer a single file.  It appears to be completely random.

---

### Post by dmizer on 2007-10-22
try mounting the share using the technique outlined in the second link in my sig (mount windows/samba shares ...) and see if that improves the situation.

---

### Post by Menelian on 2007-10-22
No dice.  I mounted it as suggested and selected a bunch of files to transfer.  Froze (timed out) on #25 of 144 files selected.  Network dead.

---

### Post by dmizer on 2007-10-22
okay ... try moving a file via command line and see if you get any errors:

for example:
```
cd /media/server/file.yours
cp -v file.yours /home/you
```

check dmesg and /var/log for errors as well.

open a terminal window and type:
```
top
```
and take a look at what's using resources.  (shift + 'F' - then 'n')

---

### Post by Menelian on 2007-10-22
Ok I'll give it a shot after work and let you know the results.  Thanks for your help.

---

### Post by Menelian on 2007-10-22
Ok, still no good.

I didn't save the error message given from the command line copy, but it was something like "Host not available" or "Host down."  Basically a timeout.

dmesg has the following to say:

```

[  615.904127]  CIFS VFS: server not responding
[  615.904137]  CIFS VFS: No response to cmd 46 mid 434
[  615.904144]  CIFS VFS: Send error in read = -11
[  665.814219]  CIFS VFS: Error 0xffffff90 on cifs_get_inode_info in lookup of \Scott\My Documents\My Music\Music\Need to sort\[NoDRM]-Enya - Aldebaran.wma
[  669.899648]  CIFS VFS: Error 0xffffff90 on cifs_get_inode_info in lookup of \Scott\My Documents\My Music\Music\Need to sort\[NoDRM]-Enya - Amarantine (album version).wma
[  670.769289] NETDEV WATCHDOG: eth0: transmit timed out
[  670.769460] eth0: Transmit timed out, status 1003, PHY status 786d, resetting...
[  670.770077] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  694.726134] NETDEV WATCHDOG: eth0: transmit timed out
[  694.726284] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
[  694.726907] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  710.697362] NETDEV WATCHDOG: eth0: transmit timed out
[  710.697514] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
[  710.698149] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  720.679383] NETDEV WATCHDOG: eth0: transmit timed out
[  720.679532] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
[  720.680141] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  738.647014] NETDEV WATCHDOG: eth0: transmit timed out
[  738.647163] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
[  738.647772] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  754.618245] NETDEV WATCHDOG: eth0: transmit timed out
[  754.618394] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
[  754.619004] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  772.585878] NETDEV WATCHDOG: eth0: transmit timed out
[  772.586026] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...

```

On this test, the first file I copied completed sucessfully, but failed on the second and every subsequent file.  The list continued on with about 20 more eth0: transmit timed out messages.

---

### Post by dmizer on 2007-10-22
looks like your internet adapter keeps dropping connection.

try rebooting your router.  also, if you have a spare ethernet adapter, try it instead.  what adapter are you using (post the output of lspci)?

---

### Post by Menelian on 2007-10-22
lspci output was in my original post :)

It appears that only the adapter on the ubuntu machine that is having problems.  I have a XP laptop on the same subnet which maintains connectivity after the ubuntu net adapter craps out.

FYI, this is an integrated lan adapter on my motherboard that works fine under windows.  I'll pick up another NIC tomorrow and see if it suffers from the same problems.

---

### Post by dmizer on 2007-10-22
just because other machines on your network don't suffer problems doesn't mean that rebooting your router won't fix the problem.  i still suggest a router reboot, it's quick and easy and its an unbelievably common problem.

sorry i missed the lspci output earlier.  a quick search on google with your chipset shows a number of other people with your problem.  could just be that the adapter doesn't cooperate with linux ... wouldn't be the first time, though it's more rare than wireless adapters not cooperating.

edit:
it could be happening under windows as well.  but since samba is a windows protocol, it can handle the drop more cleanly.

---

### Post by Menelian on 2007-10-22
Interesting.  What did you search for w/Google?  I had given up on finding any information on others with this adapter before I posted here...

---

### Post by Menelian on 2007-10-22
Problem solved!

On a whim I decided to load the failsafe settings in my system BIOS setupl.  After this my problem completely disappeared.  I just transfered about 1 gig of music files via SMB with no problems.

Thanks for your help.  Now I can focus on enjoying Ubuntu! :popcorn:

---

### Post by dmizer on 2007-10-22
glad you got it working!

just fyi, my search was extremely simple: VT6102 samba

---

### Post by wasutton3 on 2008-07-04
i know this thread is long closed but i have a similar problem when using samba over a hamachi vpn it will run for some time then sporadically cut out. both systems are ubuntu hardy. restarting hamachi seems to get it working again. on the computer trying to access the files i get 
"Jul  4 18:10:42 Manasa kernel: [ 7232.946524]  CIFS VFS: Error 0xffffff90 on cifs_get_inode_info in lookup of /Music/S"
but the other machine shows no change whatsoever
is this problem hamachi related or would it be with my network adapter?

---

