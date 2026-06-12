---
title: "Reads over NFS and AFP shares behaving weirdly since upgrading motherboard"
date: 2014-04-08
forum: Networking &amp; Wireless
---

### Post by Owen_Mehegan on 2014-04-08
I'm running Ubuntu 12.04/Precise with the 3.5.0-47-generic kernel as a home file server. Last week I swapped the 7 year old Celeron system in it for a new Intel Atom, keeping the same drives and OS install. Everything worked fine on boot, other than the network interface (Realtek 8101), which didn't seem to have a driver in the existing kernel. I downloaded and compiled that from the Realtek site, per advice I found in a different ubuntuforums thread, and everything seemed fine. But now I'm realizing that there's something wrong with the file sharing setup.

I have both NFS and AFP configured - I use AFP to allow this system to act like a Time Capsule for my MacOS laptops to back up to. I use NFS to share MP3s and video from the file server to my Macs and an Apple TV. The first thing I noticed was that my Apple TV started having problems playing MP3s from the file server. It could list the files, but playback either didn't work, or had lots of skips and other decoding artifacts. I mounted the share on my Mac laptop, and discovered that if I ran 'file *' on a folder of MP3s, some would show up as MP3s, while others would show up as 'ASCII text, with very long lines, with no line terminators.' The same files all list fine when I check them on the server side. I also had the same playback issues on the Mac. As a further test, I tried sharing the media files over AFP instead of NFS, and encountered essentially the same issues. Although running 'file' on the MP3s gave valid file data, I still couldn't play them back either on the Mac or the Apple TV. All of this worked for several years prior to the motherboard swap.

This is all over a local wired/wireless LAN, and I am seeing latencies of less than 5ms and no packet loss between the file server and clients. I have confirmed that the files are not corrupted by looking at them on the file server itself. And strangely enough, I can even scp multi-gigabyte files from the file server to a client, and they come across fine. There's no packet loss and only slightly increased latency to the system during a copy like this.

So there's my weird problem. I'm a generally competent Linux admin but this has me stumped. I don't even see anything in the logs that would give a hint, although maybe I need to increase logging somewhere. Feel free to tell me to run tcpdump, but only if you're willing to help me dissect the output - lower-level networking is not one of my strong suits. Thanks in advance :)

---

### Post by TheFu on 2014-04-08
Great writeup - I'm stumped.

Just a few things to check into - might mean nothing.
* check that the LANG settings match - UTF8?
* check the versions of NFS used on the server and client are compatible.
* do you use soft or hard mounts?
* wifi sucks with NFS. Just sayin'  - consider wired/powerline ... anything except wifi.
* turn up logging levels for NFS on both sides.

Might help if you clarified exactly which systems have which networking and how the problems happen. Also, using wired ethernet only to remove wifi crap connection issues. Wifi issues are too hard to diagnose mixed with other stuff.

---

### Post by SeijiSensei on 2014-04-08
I use "rsize=32768,wsize=32768" in the mount options in /etc/fstab.  These increase the size of the NFS packets and improve performance.  The default settings come from long ago when networks were largely 10 Mbit Ethernet.  Also try adding "nosync" to the list of server options in /etc/exports.  This subjects you to the small possibility that you might lose data while writing to the NFS server if it loses power, but it will improve transfer performance considerably, particularly over wifi.

TheFu makes a good point about compatibility between NFS versions.  On my Linux clients I specify "vers=3" in the mount options to force an NFSv3 connection.  

Still, given your writeup, I'm not sure transfer speeds are the issue.

Let me make one other wacky suggestion.  Trying ripping a CD to FLAC rather than MP3 and see how that works.  I assume Apple is not so brain-dead as to not play FLAC files on AppleTV.

---

### Post by Owen_Mehegan on 2014-04-09
Thanks a lot for the replies! To clarify the network setup, the file server is connected over wired ethernet to my router, all other clients connect to it over wireless. But given that this has never been a problem before, I don't think the wireless is the issue. I can switch the Apple TV to wired easily though, just to rule it out. I'll try. As for the NFS settings, I'm up for tuning those a bit to see if that helps, but given that I have the same issues over AFP, that also doesn't seem like a likely culprit. My suspicion is that there might be a bug in the new network card driver on the file server. That's the only software component that has changed at all in this scenario. 

I just thought of and tried another quick test: when I copy an MP3 off the server using SCP, it plays fine, and 'file' says it's an MP3. When I copy it over using 'cp' from an NFS mount, it won't play at all and 'file' says it's 'data.' When I do the same copy using an AFP mount, 'file' says it's an MP3, but the playback is full of skips and glitches. The file sizes are identical to the byte on client and server, but the MD5s do not match! How weird is that? It's as if the file is getting sent across and assembled in the wrong order.

I realized that I have a USB wifi card that should work in Ubuntu, so I think I'll try configuring that on the server and see what that gets me. I realize it's not a good long term solution for a file server, but it should suffice to tell me if the problem lies with the network card driver.

By the way, my current NFS export flags are: rw,insecure,no_subtree_check,async,all_squash,anonuid=1000

I'd have to look up how to specify mount options on the Mac clients, but I bet you can't even do that on the Apple TV. At this point I should really switch to AFP for these media mounts anyway, everything I've heard indicates it's a better protocol than NFS. I just need to fix these data transfer problems!

I'll try to experiment more tomorrow and follow up. Thanks again.

---

### Post by TheFu on 2014-04-09
async scares me, especially over wifi.  It is asking for corruption, IMHO.

Don't know anything about AFS or Apple stuff. Tried it for a few weeks, samba access from OSX was broken at the time and gave the system to a friend. It wasn't for me, the GUI just felt "wrong." ;)  Sorta like how Unity just feels "wrong."

---

### Post by SeijiSensei on 2014-04-09
> **TheFu said:**
> async scares me, especially over wifi.  It is asking for corruption, IMHO.

Never happened to me, and I've been using NFS over wifi with async for years.  My server has a UPS, so the possibility of corruption because of power loss is close to zero.

Also, async makes a much bigger difference with NFS over wifi because 802.11 is a half-duplex protocol.  Sync makes the connection "turn the line around" continuously during data transfers so performance suffers.

---

### Post by Owen_Mehegan on 2014-04-11
OK, I can confirm that the problem lies with my wired network on the file server, possibly the driver. After some struggles getting a wireless adapter working on it, I eventually was able to confirm that my problems go away when I connect to the server over that interface. Files copy fine, play back fine, and md5s match up as I would expect. What a strange problem - I can't imagine what could be happening to munge data when it goes over either of two different file sharing protocols, but not when it goes over SCP. I'll be looking to see if I can report a bug to Realtek, and also see if I can get older versions of their driver to test. Thanks for the help!

---

### Post by TheFu on 2014-04-11
Once had a developer on my team who corrupted the software version control DB every time he checked in code.  Every time.

We had him use a different machine - worked.  It wasn't his account.
We swapped out the cable. Didn't work.
We swapped out the NIC. Didn't work.
We validated/reinstalled drivers. Didn't work.
We swapped out the GPU. Didn't work.  Failing GPUs can have really strange affects.
We swapped out the PSU. Didn't work.
After a day of this, we swapped out the MB - fixed. There was a crack in the MB according to a vendor.

NFS is very well tested by driver vendors, but VoIP traffic has been found to break some Intel PRO/1000 NICs.  Break as in "lock up completely."   So ... don't assume it is just the drivers.

Anyway, glad you figured it out.

---

### Post by Owen_Mehegan on 2014-04-14
I'll be damned - I was able to dig a little further and solve this problem, thanks to a tip from one of the network engineers I work with. He suggested that I use 'ethtool' to disable some of the NIC offloading functions and see if any of them cleared up my problem. He particularly thought that if the TX checksumming feature had a bug, it could cause this problem. Sure enough, with TX checksumming on (which is the default), I get incorrect md5 hashes on files over the network share. When I turn it off and remount the share, I see the right hash! So that's cool, I can persist that setting across boots for now, using an init script. Maybe Realtek will fix the bug. Just putting this out there in case anyone else comes across this problem.

---

### Post by TheFu on 2014-04-14
Glad you solved it!  
Posting the exact model and the exact ethtool command might help someone else.

One of the Intel PRO/1000 cards here has a bug with VOIP traffic. It completely locks up the NIC - once-in-a-while.  It is a known bug.

---

### Post by Owen_Mehegan on 2014-04-15
The card: 01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

The driver: Official Realtek r8101 version 1.025.00 from the Realtek site.

The fix: /sbin/ethtool -K eth1 tx off [where eth1 is whatever your NIC is, obviously]

The fix will not persist across reboots. I added it to /etc/rc.local so that it will. 

A little Google research indicates that this problem with TX checksumming in the Realtek cards is well known and has been around for a number of years. It's impressive it hasn't been fixed, given that I think this is a pretty common ethernet chip. Maybe I'm wrong about that. Incidentally, it occurred to me to wonder if it might have the same problem with RX checksumming. I use this host as a Time Capsule for backups of my Mac laptops, and I'd hate for those to get trashed. But I just tested by copying a 100M file to the server over NFS, and it went across fine. So it seems like only TX checksumming is affected.

---

