---
title: "Still Trying to Diagnose Laggy Netwrok Connection 6 Months"
date: 2019-08-06
forum: Networking &amp; Wireless
---

### Post by rebeltaz on 2019-08-06
I posted on this issue before about six months ago or so - [https://ubuntuforums.org/showthread.php?t=2404177](https://ubuntuforums.org/showthread.php?t=2404177) - At the time, I thought I had found the problem. I found two devices trying to share one IP address. Apparently, that was not the issue. 

To recap... Back on 16.04, everything network related worked fine. As soon as I migrated to 18.04, I began having issues accessing network shares through this laptop. Nothing changed on the computer hosting the shares, and all other systems are still able to access the shares with no problem. 

The problem exhibits differently at different times.

[LIST]
[*]Sometimes, you can pull up a video file from one of the shares and it'll play fine. Other times, if you try to play that same file (or any other file) it takes the program (usually vlc) 30 seconds to a minute to begin playback. Once it begins, it plays fine. When this happens, you can try to reopen that same file with Videos and it may play fine or it might have the same delay.
[*]Almost every time that I try to open an archive file on a share, archive manager will start up , but it takes over a minute for the file to finally open.
[*]If I try to add files to an archive that is stored on a share, it will tell you that the operation completed successfully, but when you reopen that archive, it's been corrupted. 
[*] (I knoew I would think of something else)... When I try to transfer a file to or from one of the network shares from this laptop, it will take 30 seconds or more for each file being transferred to begin.
[/LIST]

These are just a few of the issues that I can think of right now. I'm sure there are more symptoms. 

I am mounting the shares via autofs, but I have also tried mounting them via fstab. The method(s) I am mounting these shares has not changed since I migrated to 18.04 - at least not that I'm aware of. 

The shares are, now, being hosted on two external USB drives connected to a raspberry pi running rasbian with samba installed and setup as a server. I was having this exact same issue, though, before moving the files to the pi. The files were on one of the same external USB drives and an internal drive connected to a desktop running Ubuntu 16.04 with samba installed and setup as a server.

If ANYONE could help me with this, I will provide any logs or information that you need. This is just driving me more bonkers than I already was!

---

### Post by rebeltaz on 2019-08-12
*** bump ***

---

### Post by rebeltaz on 2019-08-25
*** bump ***

---

### Post by Skaperen on 2019-08-25
is any other network activity besides file shares laggy?  is always the case that lag only happens at the start?

---

### Post by rebeltaz on 2019-08-25
> **Skaperen said:**
> is any other network activity besides file shares laggy?  is always the case that lag only happens at the start?

Any other activity such as? I guess I consider playing audio and video files over the network the same as file sharing, so...

As for "only happens at the start"... yes and no. 

Say I'm playing a video. I usually play then at 1.75 to 2x speed. When there is a delay before playback begins, it will play through just fine for the rest of the video. I can pause it, move it around, and it's fine throughout that one file. Occasionally, at that high a playback speed, on long videos, there may be an issue with buffering, but I don't know if that's related or not. Standard playback doesn't have that issue. 

If I'm moving/copying files in a batch, there will (usually) be a delay at the beginning of each file being transferred. 

I don't know if I said this or not, but no other device connected to the same shares exhibits this issue. An Android TV Box, a Raspberry Pi running Kodi, a Windows 7 laptop... all connect just fine to the file server computer.

---

### Post by Skaperen on 2019-08-26
anything not involving file share servers.  one possibility is that the file share software is doing a lookup of the IP address and waits until the lookup times out.  if other things like internet access work fine, then that possibility is stronger.

---

### Post by rebeltaz on 2019-08-26
> **Skaperen said:**
> ...the file share software is doing a lookup of the IP address and waits until the lookup times out. 

By "file share software," do you mean samba? If so, why is it looking up an IP address for a local network connection? In the autofs.smb file, I am specifying an IP address, not a hostname. Is there something I can do to test/fix this, if this is the case?

---

### Post by Skaperen on 2019-08-26
software that handles incoming connections very oftens looks up IP addresses so it can put the hostname in the logs it writes, instead of the IP address.  some software even uses that to decide who has access (not in your case).

do you ever access anything else from that computer?  does that network even allow you access to the internet?

if this is the problem (still not real sure) it could be fixed by adding your IP address to the data it looks up.  that might include the **[FONT=courier new]/etc/hosts[/FONT]** file on Linux.

---

### Post by rebeltaz on 2019-08-26
The internet works fine - no problems there. http, ftp...  I do run a vpn along with ufw, but both have been configured to allow LAN traffic unfettered. Just to be sure that that wasn't causing the issue, I did try it with both the vpn and the firewall disabled and still got the same results. 

I'll look at my hosts file tonight and add an entry for the file server... see if that helps..

---

### Post by SeijiSensei on 2019-08-26
If I play an MKV file over the network from my server (using SMPlayer + mpv and NFS), there is always a 10-15 second lag at the beginning when the file begins playing, but I cannot navigate within it. After that initial lag, everything is fine. It's not that big a deal, so I just live with it.  It's not a name resolution issue since I run a local DNS server, and it happens if I'm playing a series of files from a playlist.

> If I'm moving/copying files in a batch, there will (usually) be a delay at the beginning of each file being transferred.


Are you using NFS or CIFS/Samba?  What if you transfer files with rsync?

---

### Post by rebeltaz on 2019-08-26
> **SeijiSensei said:**
> If I play an MKV file over the network from my server (using SMPlayer + mpv and NFS), there is always a 10-15 second lag at the beginning when the file begins playing, but I cannot navigate within it. After that initial lag, everything is fine. It's not that big a deal, so I just live with it.  It's not a name resolution issue since I run a local DNS server, and it happens if I'm playing a series of files from a playlist.



Are you using NFS or CIFS/Samba?  What if you transfer files with rsync?

10-15 seconds, I could live with. This is more like 30-60 seconds. :(

I'm using Samba. rsync.... I want to think that that works fine every time. If I'm not mistaken, when I am moving/copying a lot of files, I us that as a work around. scp may work also, but I forget for sure right now. Besides that, it's kind of hard to tell since this delay doesn't always occur. It happens more often than not, but still....

---

### Post by TheFu on 2019-08-26
Provided about all the help I can in the prior thread (see link in #1 post).  Standard troubleshooting is to simplify and test until you isolate the issue. I would start by using a wired ethernet connection.

Most raspberry pis are poor choices as file servers.  A v4 Pi might change that. v3 and v2 Pis fall into the "poor choice" list, unfortunately. Mainly because of the limited and shared bus architecture.

---

### Post by rebeltaz on 2019-08-28
> **TheFu said:**
> Provided about all the help I can in the prior thread (see link in #1 post).  Standard troubleshooting is to simplify and test until you isolate the issue. I would start by using a wired ethernet connection.

Most raspberry pis are poor choices as file servers.  A v4 Pi might change that. v3 and v2 Pis fall into the "poor choice" list, unfortunately. Mainly because of the limited and shared bus architecture.

I know... and I really do appreciate all of your help in this issue. I do understand the wired connection recommendation. My only issue with that (and I will take this laptop to the shop tomorrow and test that theory and report back) is that I never had this problem with my network setup until I "upgraded" to 18.04. Under 16.04, it worked flawlessly. Well... flawlessly enough anyway...

I know the pi isn't an ideal solution, but for my needs, it's serviceable. I was running a 24/7 desktop computer as a server and I needed to cut power consumption as much as possible. The pi fit that bill. File transfer speeds are abysmal, but I have more time than cash, so that's ok. Other than the 18.04 related delay on startup, I've never had any trouble with media streaming, which is my main concern with this setup, so that's ok too. I may think about a pi4, or even a Libre SBC (I'm running one of those as a basic web server and they're pretty nice) later on, though...

-=[ EDIT ]=-
Oh... and to @SeijiSensei , I tried adding my IP address / hostname to the hosts file, but that didn't affect the delay any.

---

