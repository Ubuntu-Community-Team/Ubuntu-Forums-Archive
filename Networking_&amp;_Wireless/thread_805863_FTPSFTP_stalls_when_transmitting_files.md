---
title: "FTP/SFTP stalls when transmitting files"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by userwaldo on 2008-05-24
Hello,

I'm have a very strange problem, that I can't figure out how to fix.

The problem is when I try to transmit a file via ftp or sftp, to an web server outside of my network, using Ubuntu 8.10.  I previous didn't have problems with Ubuntu 7.04.

The problem is that when I try to transmit a large file, that is stall at somewhere between 1-4 MBs, and never recovers.  The actual place it stalls varies each time I try to transmit the file, but it is always between 1-4MBs.

I can how ever transmit files over sftp to another computer in my own network.  I tested files as larger as 800MB to see if I could reproduce the failure.  I then transmitted that same large file from my other computer (MAC OSX) to the site that failed with my ubuntu install, and I have been sucessful.

So the problem seems to be with my ubuntu machine.  I can't figure out why I can't transmit large files from it.  I've check and I don't even have a firewall setup on my ubunut, as I thought that this might be part of the problem.

If anyone has any suggestions on how to troubleshoot this, I would really appreciate the help.  I'm tempted to try going back to ubuntu 7.04.

---

### Post by SpaceTeddy on 2008-05-25
i have a (somewhat) similar problem (i think) - can you please try to drop your mtu to 1490 bytes instead of the normal 1500 on the sending machine and see if the transfers still stalls ?

make sure you drop the mtu on the source machine - NOT the router. You can drop the mtu on an ubuntu machine with this command:
```
sudo ifconfig %device mtu 1490
```
where %device is eth0, wlan0 ath0 or something like that (depending on your device)

let's see if you get the same results as me...

---

### Post by userwaldo on 2008-05-25
I tried reducing the mtu to 1490, but I still see the problem with the uploads stalling at about the same point, 1MB - 4MB.

I'm willing to try other ideas, as well.

---

### Post by SpaceTeddy on 2008-05-28
i've been searching myself a little - but i have no idea how to even start debugging that problem (apart from doing paket dumps and looking where the connections stalls, e.g. which part of the connection will suddenly not pass pakets anymore)...

i'd use wireshark or tcpdump for that - but that is really only an idea and i don't know if anything can even be seen there... really ;(

---

### Post by kgibbs on 2008-05-30
> **SpaceTeddy said:**
> i have a (somewhat) similar problem (i think) - can you please try to drop your mtu to 1490 bytes instead of the normal 1500 on the sending machine and see if the transfers still stalls ?

make sure you drop the mtu on the source machine - NOT the router. You can drop the mtu on an ubuntu machine with this command:
```
sudo ifconfig %device mtu 1490
```
where %device is eth0, wlan0 ath0 or something like that (depending on your device)

let's see if you get the same results as me...

This did the trick for me.  I have been trying to sync a few GB of files between my workstation, my laptop and my server at home.  Between the workstation and the laptop (sitting across the room), no problem, between the workstation and my home server, repeated stalls even after upgrading rsync to v3.0.2(?).  Setting the mtu as you suggested fixed the problem
(well, I transferred a random directory containing 60MB with no hitch).
Thanks!

- k

---

### Post by hpark21 on 2008-08-12
I am running into Exactly same issue.

Uploading via FTP will stall.

Changing MTU to 1490 makes it a LITTLE better, (it does not down right cancels the upload, but it stalls about once every 30 MB transfer for about 10 seconds)

This did NOT happen with Ubuntu 6.10.

Please help.

---

### Post by hpark21 on 2008-08-12
Ok, here is something new.

IF using PORT setting (and not PASV) and when I limit the upload transfer speed to 400KB/s then, stalling frequency lessens severely.
(I can transfer around 100MB before stalling out, still not good, but MAYBE tolerable)

I transfer 1GB+ regularly to my xbox from my computer and when I had 6.10, I had ZERO issues uploading.

Now, I installed the Hardy, I am having issues (upgrade was needed because I could not upgrade packages anymore for my 6.10)

I have seen another forum that this may be due to router interface.  Maybe it is time for me to reboot all my routers, it has been few weeks.

---

### Post by hpark21 on 2008-08-30
It has been couple of weeks and still no resolution.

I noticed that this problem worsens when there is rather moderate/heavy load on network.

Even when throttling at 350KB/sec it stalls frequently (around every 10-30MB)

Please help as I am not planning to go back to 6.10 if I can help it (maybe 7.04 may help?)

Does anyone know what changed in network/ftp side for 8.10?

Thanks.

---

### Post by afischer on 2008-09-04
I have used psftp, an option in putty without any problems, while the regular sftp stalled.

---

### Post by hpark21 on 2008-09-09
Well, the way I finally resolved this issue is:

By installing OpenSUSE 11.

After installing OpenSUSE 11, no issues with FTP at all.

I can upload at 1.5MB/sec without any issues using gftp (which was what I was using when I was on Ubuntu).
No stalling, no re-connect.

Overall, I believe NX connection feel smoother as well.

I think there is definite issue with networking component issue on 8.04.
(Although, I never achieved steady 1.5MB/sec upload even using 6.10, which is odd - Best I got was around 800KB-1MB/sec many times falling below 500KB/sec, but never stalled out though)

There was no change to the networking components.

Maybe this posting will help people, (either to debug the issue, or IF FTP upload is important to them, solution seems to be installing another distro)

PS:  I installed and ran FTP server on Ubuntu 8.04 as well, which is little bit better than upload, but not much better, downloading from my server, it would require about 5 reconnects to download 800MB file.

---

### Post by Vermind on 2008-09-16
Hello, I have recently posted about a similar issue, which did not go away with mtu changes. [scp and rsync stall when transferring from Ubuntu hardy heron 8.04]("http://ubuntuforums.org/showthread.php?t=891695")

---

### Post by caue.rego on 2009-05-25
amazing... sftp, scp, ftp, nothing was working right until i've changed that MTU setting from 1500 to 1490! now i wonder why, and what else it could affect, since i'm having seceral network issues.

---

### Post by rituraj_tiwari on 2009-06-15
I am seeing this problem too recently. My networking is onboard RealTek driver r8169. I have been reading bad things about this version and I am considering downgrading to 8168. 

I'd love to find out how many of the people who have reported this issue on this thread have the same hardware as I.

Thanks.
-Raj

---

### Post by caue.rego on 2009-06-17
in my case it's surely not the driver. it has something to do with the routing and that MTU setting, losing packaged somehow because of it. I've changed the router and no more need on the MTU.

i know it's a network issue because it's the exact same symptom in every computer (more than 5) on the same network, in every operational system (between windows and linux).

so, it's all about bad standards and a lot of miss information once again.

---

### Post by rituraj_tiwari on 2009-06-18
So, update from me is that I downgraded the driver version and my networking problems went away.

Anyone else with RealTek hardware, if you are on r8169, consider reverting to 8168!

-Raj

---

### Post by rushtovijay on 2009-08-28
> **SpaceTeddy said:**
> i have a (somewhat) similar problem (i think) - can you please try to drop your mtu to 1490 bytes instead of the normal 1500 on the sending machine and see if the transfers still stalls ?

make sure you drop the mtu on the source machine - NOT the router. You can drop the mtu on an ubuntu machine with this command:
```
sudo ifconfig %device mtu 1490
```
where %device is eth0, wlan0 ath0 or something like that (depending on your device)

let's see if you get the same results as me...

Thanks changing the mtu to 1490 
fixes stall problem in ftp and http.
In both ubuntu 8.04 and ubuntu 9.04.
upload speed also improves.

---

### Post by hongquan1987 on 2012-09-27
> **SpaceTeddy said:**
> i have a (somewhat) similar problem (i think) - can you please try to drop your mtu to 1490 bytes instead of the normal 1500 on the sending machine and see if the transfers still stalls ?

make sure you drop the mtu on the source machine - NOT the router. You can drop the mtu on an ubuntu machine with this command:
```
sudo ifconfig %device mtu 1490
```
where %device is eth0, wlan0 ath0 or something like that (depending on your device)

let's see if you get the same results as me...
Thank you so much

---

