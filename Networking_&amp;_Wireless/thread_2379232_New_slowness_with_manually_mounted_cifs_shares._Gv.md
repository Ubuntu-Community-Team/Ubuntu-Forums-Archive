---
title: "New slowness with manually mounted cifs shares. Gvfs remains wicked fast though."
date: 2017-12-02
forum: Networking &amp; Wireless
---

### Post by Roasted on 2017-12-02
Hi friends. I have a strange issue that came up seemingly out of no where. A little context to share about the setup.

The network is all gigabit and AC wireless. For this scenario, I focused entirely on hard wiring the systems as I was troubleshooting. Even the laptops were hardwired. A 24 port gigabit switch serves our household with wired connectivity. A file server and web server are also on the LAN. Both servers host samba shares that I utilize for different purposes. File server is now 16.04 (was 14.04 when this problem started and I began troubleshooting, later upgraded to 16.04 to rule it out + I've been meaning to upgrade it), and web server has been 16.04 for months.

Client machines are:

Lenovo laptop -- dual boot of Antergos (Gnome) and Ubuntu 17.10
Lenovo laptop (wife's) -- Ubuntu 17.10
Lenovo laptop (work) -- Ubuntu 16.04
Lenovo laptop -- Ubuntu Mate 16.04 (lightly used, admittedly behind on updates)
Custom desktop -- Ubuntu 17.10

Weeks prior I used to use autofs, which would mount the shares automatically using the same process (except automated) of mounting shares in CLI via 'mount -t cifs' etc/etc. In the last 2 weeks I switched to systemd automounts on the 17.10 and Antergos systems. To rule out any shenanigans of systemd automount and autofs, I disabled them completely and focused entirely on manually mounting the shares via 'mount -t cifs' commands. In short, this situation is comparing 'mount -t cifs' command and gvfs directly, no autofs or systemd was involved during troubleshooting.

My issue is this. I took note a few days ago that my speed transferring TO my server was wildly slow. Transfer from server to clients was still very fast through all this. On gigabit wire, average was about 7 MB/s for all systems. I did a number of things to troubleshoot this. Again all troubleshooting was done using 'mount -t cifs' commands with various options to test.

1) I tried a USB3 gigabit adapter. This made no change.
2) I ensured via ethtool that the NICs are full duplex and reading as 1000mb.
3) I replaced the switch with another gigabit switch. No change.
4) I replaced network patch cables. No change.
5) I tried vers=1.0, 2.0, and 3.0 in the mount -t cifs command to compare. No change.
6) I put my file server and desktop on the same gigabit switch, nothing else connected, and tested. No change. The problem still persisted on that ultra-local-LAN.
7) I tested rsync, using the same ISO file as the above tests to the same share. Speed was upwards of 80 MB/s. 
8) I replicated the exact same transfer test, but this time, to my web server. To my surprise, this too exhibited the *exact same issues* as my file server. Here all along I was thinking this was an isolated thing with my file server, somehow.

Then lastly, I linked up to my share via gvfs. To my surprise, gvfs was transferring the same ISO file to the same share I was using for testing at 70 MB/s. That's right, gvfs was exactly 10 times faster than mounting the share directly. The mount command I (last) used was this:

sudo mount -t cifs //192.168.0.200/vault /home/jason/testmount -o user=jason,rw,uid=1000,gid=1000,file_mode=0600,dir_mode=0700

I tried searching online for answers, but it seems that the overwelming majority of discussions I saw relating to this was with folks complaining about the speed of gvfs being too slow. I didn't see any other posts indicating that manual mounting of shares via CLI was slower than gvfs -- in fact, the manual mount method via CLI was often the recommended solution/workaround.

Lastly, I ran this command to test a file transfer to the mount point of the remote system:

dd bs=128x1024 status=progress if=/home/jason/Downloads/ubuntu-16.04.3-server-amd64.iso of=/home/jason/testmount/public/ISOs/Test/ubuntu-16.04.3-server-amd64.iso

I was able to transfer this file at a final average of 63 MB/s. This begs whether the file manager is somehow getting confused between local and remote filesystems, perhaps? As we can see above, Antergos, Ubuntu 16.04, and Ubuntu 17.10 (all running Gnome, and thus, Nautilus) are problematic areas. Likewise, Ubuntu Mate 16.04 had the same issues, though Mate has a different file manager. Perhaps Mate's file manager is coded similarly to Nautilus -- not sure of this offhand.

At this point, I am feeling a mixed cocktail of thoughts. Clearly I'm having issues on multiple systems with multiple patch cycles with multiple network switches with multiple servers, but only when mounting directly in CLI and working with those shares in the file manager. When using gvfs, all issues go away. Days ago I didn't have these problems, and yet nothing major changed to instigate this that I'm aware of. I'm reluctant to believe an update caused this due to some systems being on different patch cycles (unless it was somehow an automatic security update).

With that said, gvfs clearly works well, it's clearly been improved, it's wicked easy to work with, so I'm inclined to start using that now instead of dealing with the setup of autofs/systemd auto mounts/etc. But even still, the curiosity is burning red hot. Has anybody else seen this? Has anybody else ever experienced this sort of behavior? This is going to keep me up tonight.

Lastly, a screenshot. Same ISO to the same server on the same share. The top line is a gvfs transfer, the bottom line was mounted with the mount -t cifs command I highlighted above.
[https://i.imgur.com/B6CeGeX.png](https://i.imgur.com/B6CeGeX.png)

EDIT - I spoke to a buddy of mine who uses Gentoo on server and client along with autofs. He confirmed the findings, almost exactly. Specifically these 3 items:

1) When using mount.cifs in any capacity and using a file manager (he tried thunar, nautilus -- I tried nautilus, caja), the speed tanks dramatically.
2) When using mount.cifs in any capacity and using terminal to initiate a file transfer, speed is significantly higher.
3) He only had massive speed degredation when pushing from his computer to his server, just like I did. Both of us had better speed by several magnitudes when downloading from server.

Anybody else?

---

### Post by Roasted on 2017-12-04
I've been reading more about this over the last day and have found a few reports earlier in 2017 of folks running in to the same thing. With that, I ask a simple favor.

Anybody out there who mounts their samba shares in terminal, specifically using mount -t cifs, what is your speed transferring *to* server and what is your speed pulling *from* server? If you could test via using Nautilus (copy/paste of an ISO file, for example) as well as terminal (I've been using rsync --progress) that would help _bigtime_. This curiosity kept me up last night. :)

---

### Post by Roasted on 2017-12-04
Well, I'm possibly on to something. In the mount.cifs man page, I found the cache entry. I did some testing. Specifically regarding *upload* (from client to server) on a gigabit wire, my findings were:

cache=strict: 7 MB/s
cache=none: 7MB/s
cache=loose: 112 MB/s

So, quite a large margin. According to some reading, cache=loose was the default setting until kernel 3.7. After that, cache=strict took over. From what I gather this is tied to the way file modification times are handled. Evidently a share where multiple people are working at once on the same files can cause data corruption issues. This is likely a non-issue in the case of a home server, but it still makes me wonder. Has anybody ran into a data corruption issue when using cache=loose? I feel tempted to use cache=loose simply because 7 MB/s over a gigabit line is nothing short of hysterically bad (and to think RHEL's man page cited cache=strict comes with a 'slight performance penalty', ha!), but even still, figured if the kernel devs felt this was a necessary change that perhaps I should at least question it.

I've been reading more about NFS. I was reluctant to try it because I found the way it handles permissions to be irritating (via UID/GID). I think the reality is I've been using UID/GID all along even if it's not in the forefront of my mind (my user translates to a UID, after all). I think the only irritating thing about it is I would need to change the UID and GID of the user of each client system. For example, the first user on my server is 'administrator', thus ID of 1000. But the first user on my laptop and desktop is jason, thus ID of 1000. Naturally, any files I copy to server come across owned as administrator. Mildly irritating, but nothing I can't overcome. Benefit here is I would get good speeds. Tested transfer of 90 MB/s upload, 110 MB/s download. Maybe it would serve me well to do this and be done with it.

[RAMBLING THOUGHT] I still quite admire, and like, cifs/samba. I personally always found it easy to set up, though I always handled my permissions via octal rights. What I mean is, I'll set, say, /media/vault as my samba share, but within /media/vault are top level directories. Things like pictures, music, documents, etc. These directories are owned by root with group assignments. I like doing this so I have just one share definition but I still reign full control of everything below it via octal rights. This makes chmod/chown/chgrp commands over SSH a breeze. The groups are the same name as the top level folder. I.E. root:pictures would own pictures with octal rights of 770 or 775 (775 for more readable flexibility to users not in pictures group). From there I still control the permissions via octal rights, sticky bits for group settings (chmod +s), etc. I guess what this means is my setup is a lot less "samba-y" than perhaps typical setups, so perhaps it stands to reason that NFS would just make sense here. I'll still have samba set up as once in a blue moon I may need to use a Windows system to connect, or even spin up a random Ubuntu system to connect --- and let's face it, being able to open Nautilus, CTRL L, type in the samba path, WICKED simple. I don't know how I could do that in NFS, given NFS's dependence on UID/GID. It seems as if NFS is better necessitated by "established" systems. In other words, if I want to spin up an Ubuntu test system but pull files off my server, if I'm bent on doing this entirely via GUI/file manager, then Samba really is the best way. I suppose I could use sshfs too in a pinch with equal success. Anyway, some thoughts.

---

### Post by Roasted on 2017-12-09
> **Roasted said:**
> I've been reading more about this over the last day and have found a few reports earlier in 2017 of folks running in to the same thing. With that, I ask a simple favor.

Anybody out there who mounts their samba shares in terminal, specifically using mount -t cifs, what is your speed transferring *to* server and what is your speed pulling *from* server? If you could test via using Nautilus (copy/paste of an ISO file, for example) as well as terminal (I've been using rsync --progress) that would help _bigtime_. This curiosity kept me up last night. :)

Bumping this with the above request. Even though I integrated NFS into my setup, part of me still misses the flexibility of Samba with user based auth. 

The TL DR of this is mounting cifs over terminal without using (and risking possible data corruption according to the man page) the cache=loose option. Curious about your speed results when uploading/downloading to samba server over gigabit. I can't imagine I'm the only one out there slinging 7 MB/s on gigabit as I feel like I'd have heard more about this, but with the magnitude of testing and experimenting I've done, it's so easy to replicate... so my curiosity to what others are seeing remains burning hot.

Thanks all.

EDIT - This has to be connected to Nautilus somehow. I just tested Plasma on Antergos. Using the exact same process as above, but this time with Dolphin, I got better speeds. To recap with everything that I've tried:

1) CIFS mounted via terminal, Ubuntu 16.04, Ubuntu Mate 16.04, Ubuntu 17.10: Upload with Nautilus -- 7 MB/s
2) CIFS mounted via terminal, Ubuntu 16.04, Ubuntu Mate 16.04, Ubuntu 17.10: Download with Nautilus -- 70 MB/s
3) CIFS mounted via terminal, Ubuntu 16.04, Ubuntu Mate 16.04, Ubuntu 17.10: Download with rsync in terminal -- 100 MB/s
4) CIFS mounted via terminal, Ubuntu 16.04, Ubuntu Mate 16.04, Ubuntu 17.10: Upload with rsync in terminal -- 80 MB/s
5) CIFS mounted via GVFS, Ubuntu 16.04, Ubuntu 17.10: Upload with Nautilus -- 30 MB/s
6) CIFS mounted via GVFS, Ubuntu 16.04, Ubuntu 17.10: Download with Nautilus -- 40 MB/s
7) NFS mounted via terminal, Ubuntu 16.04, Ubuntu 17.10: Upload with Nautilus *or* rsync in terminal -- 110 MB/s
8) NFS mounted via terminal, Ubuntu 16.04, Ubuntu 17.10: Download with Nautilus *or* rsync in terminal -- 110 MB/s
9) CIFS mounted via terminal, Antergos with Plasma: Download with Dolphin -- 110 MB/s
10) CIFS mounted via terminal, Antergos with Plasma: Upload with Dolphin -- 35 MB/s

SSHFS yielded nearly identical speeds to NFS (7 and 8 above), though at the expense of slightly higher CPU usage (though less than I would have thought). I'm still debating whether I want to use SSHFS or NFS full time. SSHFS is crazy easy to set up (just need ssh) and I don't need any export files (looking at you, NFS), but, so far at least, NFS seems to be a little more forgiving if I'm on my laptop connected to the share, suspend, and resume elsewhere off network. SSHFS is a bit rough as it makes Nautilus spin, even as I click on local folders not on the share. NFS was a bit more forgiving, but not free of sin in this regard. If anybody has any insight here as a viable alternative I'd greatly appreciate it.

To wrap up... I love Samba, but that 7 MB/s is nothing short of downright agonizing.

---

### Post by dblegend on 2018-10-04
THANK YOU for this post.  I've been pulling my hair out trying to troubleshoot something VERY similar to this.  I added cahce=loose to my fstab mount options, and my throughput on upload went from 13MB/s to 90MB/s.  Like you, I need to do some thinking as to how I feel about leaving things that way, but at least I've got a much better idea of where the problems exist.  If you see this, can you tell me where you ultimately landed?

---

### Post by Roasted on 2018-10-04
Hi there. I ended up changing my direction a little bit. I already use SSH everywhere so what I did was tested out gvfs with SFTP. I was quite impressed with it so I ran with it. That's currently what my systems at home use since everything is Linux based. I do have a Windows system I use for work and at times it's nice to lean on samba so I still keep samba running and active, I just don't use it as primary. So really all I did was in Nautilus I hit up SFTP://ip.of.server, navigated to the top level share, and bookmarked it. One thing to note is Nautilus has a weird thing when you click on the sidebar entry when mounted. It defaults to the home directory of the remote user. Even though it originally mapped to SFTP://server/share, later it defaults to /home/user on the server. That's not okay and remains an active bug with Nautilus but a quick workaround is on the home directories for each user on the server I just put a symlink there that points to the main server share. There's nothing in the remote home directory anyway except hidden directories like .ssh so with only having one visible directory there it's quick to get routed to where I need. An extra click sure but it's easy and SFTP over gvfs still provides great speeds. Hope this helps!

---

