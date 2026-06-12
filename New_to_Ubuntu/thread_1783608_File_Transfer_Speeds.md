---
title: "File Transfer Speeds"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by mfarith on 2011-06-15
Hi All,

Total noob here. Just installed 11.04 server a coupla weeks ago. The server is setup to perform the following:
[LIST=1]
[*] Serve as a filesharing server to 2 windows 7 machine
[*] Serve as an UPNP server for an ACRYAN Media Streamer
[*] Serve as a download server for torrents
[*] Ability to manage the whole server via LAN and over the Internet
[/LIST]

Here's the Hardware specs:
[LIST=2]
[*] Pentium 4 2.08mhz HT
[*] ASUS P5GC/MX1333 MoBo
[*] 3GB DDR2 RAM
[*] WD 80GB HDD - Primary MBR (I have dual boot with Windows 7) which 40GB is NTFS for Windows 7 MBR and the rest in EXT 3 for Ubuntu plus a 4GB Swap]
[*] WD 400GB HDD called DownloadCentral - Where all the downloaded torrent files resides prior to completion. Disk is NTFS.
[*] WD 1TB HDD called VidzCentral - Central repositories of completed torrents. Disk is NTFS
[/LIST]

Packages Installed:
[List=3]
[*] Samba File Sharing Server - Works ok as i can see all my shares via the 2 windows 7 machines. Cant see it on my ACRYAN though.
[*] OpenSSH for PUttY
[*] Mediatomb for UPnP
[*] Logmein Hamachi for VPN to manage things over the internet when im outside of the LAN.
[/LIST]

Other Info:
[List=4]
[*] Mapped all the shared drives on SMB via \\xxx.xxx.xxx on both the windows machine for easy access
[/LIST]

So heres the real question, when I use the mapped shares to transfer completed files from DownloadCentral to Vidz central, the transfer rate is so low like 800kb/s for any file. Is this normal?

I resimulated the transfer via the Windows 7 installed on the same Ubuntu server(dual boot), it gave me a whopping 80mb/s. Someone mentioned about some filesystem issues somewhere.

But i dont get it, why in Windows its superfast and in Ubuntu super sluggish? whereby they are 2 hdds on the same machine?

A solution is cool...an explanation shall suffice!

PS-> I've tried using the mv command too...same speeds..800kb/s

---

### Post by cariboo on 2011-06-16
Dual boot a server? Why? It sounds like you have a misconfiguration somewhere, When running a server, network transfer speed is more a bottleneck than anything else. How are you network transfer speeds. You can use iperf, it's in the repositories, and a windows client is available to test it. I have a 100Mbps network, and I can max out the connection @ 12MBs with zero problems.

My storage drives are formatted as XFS, and shared via samba for Windows systems, and NFS for Linux based systems. How do you have your partitions formatted?

---

### Post by mfarith on 2011-06-16
> 
Re: File Transfer Speeds
Dual boot a server? Why? It sounds like you have a misconfiguration somewhere, When running a server, network transfer speed is more a bottleneck than anything else. How are you network transfer speeds. You can use iperf, it's in the repositories, and a windows client is available to test it. I have a 100Mbps network, and I can max out the connection @ 12MBs with zero problems.

My storage drives are formatted as XFS, and shared via samba for Windows systems, and NFS for Linux based systems. How do you have your partitions formatted?


Hi,

Thanks for your response.

Reason for dual booting would be that previously I ran my Media Server via Windows 7 on the very _same machine_ and got the itch to try Ubuntu for fun. Hence the dual boot server. If all works well in Ubuntu i might just ditch Windows altogether.

FYI, the server is connected to a gigabit router and I,m accessing it via PuTTy on my laptop which connects to the network wirelessly on Wireless N(108mbps).

Do you think it really is a network issue as the shares I am moving files to are located on the very _same machine_?

My shares are all in NTFS format.

Ive used mv to perform the move before and it still gives me crappy speeds..800kb/s not even a Meg!

Thanks!

---

### Post by alphacrucis2 on 2011-06-16
> **mfarith said:**
> Hi,

Thanks for your response.

Reason for dual booting would be that previously I ran my Media Server via Windows 7 on the very _same machine_ and got the itch to try Ubuntu for fun. Hence the dual boot server. If all works well in Ubuntu i might just ditch Windows altogether.

FYI, the server is connected to a gigabit router and I,m accessing it via PuTTy on my laptop which connects to the network wirelessly on Wireless N(108mbps).

Do you think it really is a network issue as the shares I am moving files to are located on the very _same machine_?

My shares are all in NTFS format.

Ive used mv to perform the move before and it still gives me crappy speeds..800kb/s not even a Meg!

Thanks!

Check the interface stats via ifconfig to see if you are getting transmission errors.

---

### Post by mfarith on 2011-06-20
> **alphacrucis2 said:**
> Check the interface stats via ifconfig to see if you are getting transmission errors.

Hey alpha,

Thanks for the response. I did check my ifconfig and all looks good. Was wondering why peeps are asking me to check my network stuff while my issue was file transfers between disks in a same machine.

Anyways, i am trying ntfs-3g to mount those drives instead. Will see how that goes.

---

### Post by mfarith on 2011-06-23
Had some time to mount the NTFS partitions via ntfs-3g. Very minor improvements earlier transfer speeds without ntfs-3g was about 800kbps, now its at 900kbps.

At least an improvement. Still don't understand why I couldn't get my actual sata transfer speeds. Theres a lot of complaints about slow transfer speeds going around but no one has a solution yet.

Will look around further.

---

