---
title: "Slow LAN Upload (wired)"
date: 2018-10-03
forum: Networking &amp; Wireless
---

### Post by dblegend on 2018-10-03
I'm experiencing very slow LAN upload speeds over a gigabit wired connection to my NAS in Ubuntu Studio 16.04 LTS.  Download speeds from the NAS are around 116 MB/s.  Renaming and re-uploading that same file runs at about 13 MB/s.  Performing the same test in Windows yields generally equal upload / download speeds.

I did quite a bit of searching on this topic, and everything pointed to either an issue with IPV6, or a buggy Realtek driver.  I tested the disabling of all things IPV6 from various solutions, and nothing helped.  Then I moved to fighting with the driver for about a day, to no avail.  As a result, I just went and purchased an Intel EXPI9301CT, which claims Linux compatibility in the Kernel since 2.6.  I disabled the onboard adapter via the BIOS, and confirmed via lsmod that there is nothing "Realtek" loaded.  None of that has helped, and at this point, I'm at a loss.  Here is some output that I know might be helpful, but please let me know what else to pull.  Thanks for any help that anyone is willing to provide.

Output from LSPCI:
```
06:00.0 Ethernet controller: Intel Corporation 82574L Gigabit Network Connection
```

Output from uname -a:
```
Linux JoeCabot 4.15.0-36-lowlatency #39~16.04.1-Ubuntu SMP PREEMPT Tue Sep 25 11:10:31 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```

Output from ifconfig:
```
enp6s0    Link encap:Ethernet  HWaddr 68:05:ca:89:76:86  
          inet addr:192.168.1.249  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1510228 errors:0 dropped:0 overruns:0 frame:0
          TX packets:314600 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2073142159 (2.0 GB)  TX bytes:264533568 (264.5 MB)
          Interrupt:18 Memory:f45c0000-f45e0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1536 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1536 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:169325 (169.3 KB)  TX bytes:169325 (169.3 KB)
```

Output from ethtool enp6s0:
```
Settings for enp6s0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: off (auto)
Cannot get wake-on-lan settings: Operation not permitted
	Current message level: 0x00000007 (7)
			       drv probe link
	Link detected: yes
```

---

### Post by johnruck on 2018-10-03
I am having the same issue (thought I had figured it out when rebuilding one of the two servers I am seeing the issue on only to discover that Samba is smart enough to avoid the network if the source and destination shares are from the same machine).  

I have been using ubuntu for file servers since the 8.04 days, and I am only seeing this problem on two newly built (and in one case rebuilt) 18.04 servers.  In both cases I can only push to the servers at 100mb speeds while I can then read those same files back at gigabit speeds.  In both cases the servers had Realtek motherboard gigabit chips that I have now bypassed with Intel gigabit pci-x adapters, and in the case of one machine (where I had the original boot disk die) it was completely rebuilt with a new boot disk after the onboard ethernet had been disabled, so the ubuntu install shouldnt have activated any of the realtek drivers.

I have also tried the dmks (? might be misspelled - it was a while ago) driver to no obvious effect.  I have replaced the switch between the 4 machines (2 machines that are sending the files - a Win 7 and a Win 10) and the two ubuntu servers, as well as switched in new ethernet cables for all 4 machines so I am pretty sure it is not a hardware issue.

I suspect it is some default that was changed between 16.04 (where the servers worked) and 18.04 in the networking layers, but I generally dont keep up with the linux world these days to know what might have changed.  In my case one of the servers is also setup as a qemm/kvm server, and the other is a docker server so the bridged networking layer is getting activated in both cases.

Like you both of my machines show that the machine knows it is a gigabit connection (and reading from them proves it) but for some unknown reason I am guessing the 18.04 machines are signalling that they cant take a gigabit connection during the connection establishment which is why they are only getting a 100mb feed.  I can simultaneously send gigabit to another 16.04 machine at the same time without issue from these originating machines, so it is not a problem from the sending side.  (And the senders are reading from ssds so I know they arent disk throughput limited).

I will be happy to provide any diagnostics to anyone that knows enough about netplan and whatever else was added in 18.04 to help identify what is going on.

---

### Post by johnruck on 2018-10-03
One thing I forgot to mention - one of these machines (oddly enough the one I had the boot disk fail on) is a new build with new hardware, the other is a machine that used to have ubuntu 12.04 on it (it was a clean rebuild to 18.04) that didnt show this networking oddity before (at least not that I remember).

Now that I see the edit option I am adding this on here :

Machines that I can copy to at gigabit speeds are running Samba 4.1.6, the newer ones that fail are running 4.7.6 if that helps anybody.

---

### Post by dblegend on 2018-10-03
I had a little bit of a breakthrough this afternoon with the realization that I was focusing on the hardware and software which controls it, without looking into the transfer protocol.  I fired up an SFTP connection to my NAS (rather than SMB), and was able to achieve ~85 MB/s on both the download AND upload.  This is proof that I'm negotiating a gig connection, and that something in either my SMB client or server is to blame.  I'll continue trying to isolate more specifics as I have time and/or will reach out to Synology to see if they've got any feedback for me on the topic.  In the meantime, any suggestions would be welcomed.

---

### Post by johnruck on 2018-10-03
These might help you then - I have tried their advice and so far they havent helped cure my version of the problem:

[https://forums.whirlpool.net.au/archive/461222](https://forums.whirlpool.net.au/archive/461222)

[https://arstechnica.com/civis/viewtopic.php?t=1080976](https://arstechnica.com/civis/viewtopic.php?t=1080976)

[https://www.howtosolutions.net/2013/06/fixing-slow-sending-or-receiving-of-files-through-lan-network-using-windows/](https://www.howtosolutions.net/2013/06/fixing-slow-sending-or-receiving-of-files-through-lan-network-using-windows/)

[https://community.spiceworks.com/topic/724954-slow-file-transfer-over-lan](https://community.spiceworks.com/topic/724954-slow-file-transfer-over-lan)

[https://www.dedoimedo.com/computers/ubuntu-beaver-samba-shares.html](https://www.dedoimedo.com/computers/ubuntu-beaver-samba-shares.html)


it might be something with the encryption stuff that one of those mentions in your case
In my case I am using greyhole disk pooling that requires the transfers be done using samba.

---

### Post by dblegend on 2018-10-04
@johnruck - Thanks for those links!  None of them addressed my particular problem, but your feedback and insights got me thinking about it differently.  As a result, I'm pretty sure I have found the answer to my issue in this thread:

[https://ubuntuforums.org/showthread.php?t=2379232](https://ubuntuforums.org/showthread.php?t=2379232)

Continuing my testing / research yesterday, I determined that GVFS (mounting using smb:// in my graphical file manager) was working at a rate of about 60 MB/s on file transfers in both directions.  That helped me to isolate my problem to the mount command that I've got set up in fstab.  I played around with my fstab CIFS mount options quite a bit, before reading the above thread and ultimately determining that I need to specify cache=loose as one of the parameters.  Once I did that, my upload speeds jumped from 13 MB/s to 90 MB/s.  It's still not as fast as the 116 MB/s that I see on downloads, but it's much more in line with what I'm used to experiencing over a Samba connection.

Although cache=loose was the default until kernel 3.7 (and never caused me file corruption issues), changing the caching coherence methodology certainly comes with some potential penalties.  I'm still going to have to weigh my comfort level with reverting to that setting, or just temporarily mounting via GVFS or SFTP when I need to upload a lot of data.  Either way, I'm in a much better position than I was a couple of days ago, and will mark this thread as solved.  Thanks again!

---

### Post by johnruck on 2018-10-05
Hmm, your sidetrack got me to what seems to be a solution for my problem as well.  Since my problem was not via a mount on linux but from windows machines I had to find a samba solution.  In looking around on caching I found this page [https://www.samba.org/samba/docs/current/man-html/smb.conf.5.html](https://www.samba.org/samba/docs/current/man-html/smb.conf.5.html) and more importantly the 

client ipc signing = 

option, setting this disabled gets me back to the normal gigabit writing speeds and seems to do it for the samba process (so all samba connects).

I think this was done for security based on all of the other links I posted, but since this is all on my home lan security is not an issue.

Thanks for your insight :)

Update - hmm, just found another wrinkle - when I am doing the copies I am doing them via robocopy on the pc side.  Just adding the /Z (recoverable - saves partial copies and allows resume) drops the throughput back to 100mb.  So I guess for now no more /Z for me.

Looks likes the /Z has been an issue for a while, even between windows machines:

[https://serverfault.com/questions/812210/robocopy-is-20x-slower-than-drag-droping-files-between-servers](https://serverfault.com/questions/812210/robocopy-is-20x-slower-than-drag-droping-files-between-servers)

---

