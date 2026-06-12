---
title: "Samba transfers half as fast as FTP transfers"
date: 2008-07-27
forum: Networking &amp; Wireless
---

### Post by Cryptic1911 on 2008-07-27
Hello, I'm having an issue with samba transfer speeds from my workstation to my server. I can FTP at 120MB/s over gigabit but Samba seems to hit a cap at around 65MB/s both ways. Is this just a limitation of samba, or is there any tuning that can speed it up?


hardware:

Workstation: Mac Pro 8x2.8ghz, 3 drive raid array, gigabit interfaces

Server: 4x2.4ghz 8 drive raid array, gigabit  (8.04 server)
Switch: Dell powerconnect 5324

Cables: All brand new cat6 cables that I just made myself (replaced them all earlier because even FTP was slow, but found that ipv6 enabled on the server was capping my throughput even for FTP at ~70MB/s)

thanks

:guitar:

---

### Post by dmizer on 2008-07-27
how are you connecting to your samba shares?  if you've just used the Places > Connect to server, then you'll be very disappointed with speeds.  in order to increase samba file transfer speeds, you'll need to mount the shares manually as outlined in the second link in my sig.

---

### Post by Cryptic1911 on 2008-07-27
I'm actually trying to connect from the Mac (OSX 10.5.4) to the Ubuntu server's samba share. I did try it as a direct mount through the terminal on my mac, but that didn't make any difference.

I looked for other options, and ended up downloading the src packages for netatalk (afp) and building it with encryption enabled so that I could connect using AFP instead of SMB from my mac, but that didn't make it any faster

at this point I'm probably just going to leave it for now.. been screwing around with it all day and I'm getting tired of thinking about it :lolflag: anyways, thanks for the help.. if I figure out what it is, I'll post up the resolution.

oh and its not any kind of speed miscalculation in the ftp program, I'm actually looking at the send/rec speed in activity monitor on the mac, and also at the disk io, so the numbers are correct

---

### Post by dmizer on 2008-07-27
Actually since you're going from a Mac to Ubuntu, I suggest you try some alternatives to samba.

Mac is capable of nfs ... you'll probably get much better results with that.

You could also just stick to FTP.

---

### Post by kevdog on 2008-07-27
dmizer

congrats on your appt to forum staff -- well deserved to say the least.  

Why is connecting through samba so slow?  Ive noticed this personally and am very disappointed in the performance myself.

---

### Post by dmizer on 2008-07-28
> **kevdog said:**
> dmizer

congrats on your appt to forum staff -- well deserved to say the least.  

Why is connecting through samba so slow?  Ive noticed this personally and am very disappointed in the performance myself.

Thanks!

Samaba is slow for lots of reasons, but according to what I've read, the biggest factor is poor packet handling. The problem has been address and at least resolved in part, but problems still remain.  In this case, it could be that Mac is using the older (and much slower) smbfs instead of cifs.

Many complaints about samba speed are a result of Nautilus. Since Nautilus soft-mounts shares, packet handling is not directed through the ip stack at the kernel level.  Nautilus is not any better at hosting shares either.  The /etc/samba/smb.conf file isn't even modified, so I'm not entirely sure how Nautilus and the gvfs host samba shares.

---

### Post by Cryptic1911 on 2008-07-28
I may give nfs a try when I get home.. that's the only thing I haven't tried yet. I had hoped appletalk / afp would solve my problem since it would be bypassing samba, but its about the same speed.

---

### Post by dmizer on 2008-07-28
> **Cryptic1911 said:**
> I may give nfs a try when I get home.. that's the only thing I haven't tried yet. I had hoped appletalk / afp would solve my problem since it would be bypassing samba, but its about the same speed.

This may be of use to you then: [http://mactechnotes.blogspot.com/2005/08/mac-os-x-as-nfs-client_31.html](http://mactechnotes.blogspot.com/2005/08/mac-os-x-as-nfs-client_31.html)

Take a look at the fourth link in my sig for how to configure ubuntu as an NFS server.

---

### Post by Cryptic1911 on 2008-07-28
ok, I got nfs installed and working, but it is about the same speed as samba and afp were. The odd thing is now my FTP's are slow as 
well. 

I'm going to wipe the machine and try windows 2003 r2 server on it to see if I still have speed issues. I really don't want to use Windows, but I dont want to have slow transfers when I know they should be ALOT faster considering the equipment that I'm using

---

### Post by dmizer on 2008-07-28
rather than wiping the machine and starting fresh, you might consider trying an ubuntu (or knoppix) live cd as a test platform.

---

### Post by Cryptic1911 on 2008-07-28
too late :) already done. It's just a home server, and I haven't actually moved all my data and services over to it yet since I've been trying to iron out the kinks.

---

### Post by dmizer on 2008-07-28
> **Cryptic1911 said:**
> too late :) already done. It's just a home server, and I haven't actually moved all my data and services over to it yet since I've been trying to iron out the kinks.

Ha! ... ah well, you can't say I didn't try ;)

---

### Post by kevdog on 2008-07-28
What would be best between sharing between windows and ubuntu systems?  Samba or something else (non-ftp).

---

### Post by dmizer on 2008-07-29
> **kevdog said:**
> What would be best between sharing between windows and ubuntu systems?  Samba or something else (non-ftp).

That would depend largely on your needs.

Depending on what software you're willing to install, Windows can connect to: NFS, SCP, SMB, CIFS, AFS, and a few obscure others.

Obviously, each system has advantages and disadvantages, so there's not one particular "silver bullet" that would fit all situations.

Hosting shares from Windows is an entirely different subject though.

---

### Post by wannabegeek on 2010-12-12
Hi...found this thread quite helpful...especially dmizer's links in his sig...

I am setting up a research lab data aquisition scheme using a windoze box and an Ubuntu box . In this setup, I will have a Windoze machine interface with some bench equipment, then send data to a shared drive, which the Ubuntu machine will crunch on with MATLAB and MIT Photonic Bands (mpb).

The files shared are only about 5K each, consisting of binary data. In ascii, they would be four columns of numbers. Speed is an issue, since we want to try and get some analysis on the data done between collection cycles. That way an experimenter can have some output to look at still at the test bench. This may not be possible, but want to try...

It seems like a samba mount wouldn't be too bad for such small files. Would do you think ?
Also, is it a mistake to consider using FAT16 for the file system of the shared HD ?

thank you,
wbg

---

### Post by dmizer on 2010-12-12
> **wannabegeek said:**
> Hi...found this thread quite helpful...especially dmizer's links in his sig...

I am setting up a research lab data aquisition scheme using a windoze box and an Ubuntu box . In this setup, I will have a Windoze machine interface with some bench equipment, then send data to a shared drive, which the Ubuntu machine will crunch on with MATLAB and MIT Photonic Bands (mpb).

The files shared are only about 5K each, consisting of binary data. In ascii, they would be four columns of numbers. Speed is an issue, since we want to try and get some analysis on the data done between collection cycles. That way an experimenter can have some output to look at still at the test bench. This may not be possible, but want to try...

It seems like a samba mount wouldn't be too bad for such small files. Would do you think ?
Also, is it a mistake to consider using FAT16 for the file system of the shared HD ?

thank you,
wbg

The two best methods for sharing files between Windows and Linux are FTP and Samba.

The only time you need to be concerned about what file system to use is when both Ubuntu and Windows are installed on the same computer as a dual boot and you want to have access to the same drive in both systems.

For a network file share (samba, nfs, ftp, etc), it doesn't matter what file system is on the server's hard drive. Ubuntu could host a samba share from an ext4 hard drive and your Windows client would have no problems saving data there.

FAT16 (or even FAT32) would be a huge mistake because there are lots of file system limits. For example, the volume size limit (total disk size) for FAT16 is 2 Gig.

---

### Post by wannabegeek on 2010-12-15
thanks dmizer,  I shall use ext3 

I originally thought FAT16 might be OK since the data aquisition drive only holds data for a short time. With a 2GB partition, that's a lot of 5k files....it turns out that the main impediment to speed is the serial connection used for the GPIB interface...gonna research a USB interface instead...

---

