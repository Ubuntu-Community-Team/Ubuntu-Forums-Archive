---
title: "File Transfers Take 30s to 1m to Begin Over Network Only on One Drive"
date: 2018-10-21
forum: Networking &amp; Wireless
---

### Post by rebeltaz on 2018-10-21
I have my main system at my shop (across the yard) set up running 16.04 LTS with it's three hard drives shared via samba. I use samba so that they can be recognized by windows systems as well as Kodi. All three drives are mapped to the /mnt/ directory on my laptop. When I initiate a file transfer to or from either of the two auxiliary drives (one internal, one external) on the main system to my laptop (running 18.04 LTS) with either Nemo (the default file manager) or Files, the transfer is initiated immediately and the transfer is swift. If I initiate a file transfer to or from the third drive (which happens to be the main system hard drive on the main system with my home directory) via Nemo or Files, the transfer takes anywhere from 30 seconds or more before it will even begin. Once it starts, it's relatively swift, but depending on the size of the file(s), it may hesitate during the transfer. However, if I do the same transfer via the command line (with cp) everything goes smoothly and quickly. 

This is a new-ish problem. I don't know how long ago it began, but everything worked fine before. 

I hope that makes sense... Any idea what could be going on?

---

### Post by TheFu on 2018-10-21
Which file system is used by each HDD?
Are they connected via SATA or eSATA or some other way?
Are any of the HDDs set to power-saving?  Do they spin down when not in use?

If it happened always between the systems, I'd look for name resolution issues and suggest using IP addresses to test the transfers instead of names or browsing.

---

### Post by rebeltaz on 2018-10-21
The two that work fine are ext3/4. The main drive I am having trouble with is ext4. 
One of the drives working fine is sata, the other is usb. The main drive is sata.
I am pretty sure I have disabled all power saving modes. That is usually the first thing I do with new drives.

All three drives are on the same computer/IP address. Could name resolution still be a cause? 

Oh... and I'm not transferring from:

smb://shop_docs/documents/ to /home/transfers/

I'm transferring from:

/mnt/shop_docs/documents/ to /home/transfers/

where the network drives are mounted at boot time (on the remote laptop) via autofs with all three using the same mount command.

---

### Post by TheFu on 2018-10-21
Any NTFS involved?

Is the slower drive USB? I didn't see which was slower.  Any "fuse" file systems access or GVFS?

**df -hT** wouldn't hurt. No need to show **any** loop anytthing.

---

### Post by rebeltaz on 2018-10-21
:) Already had df-hT up in my terminal:

```

derek@shop:~$ df -Th
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sdb2      ext4      226G   54G  161G  25% /
/dev/sda1      ext4      1.8T  1.6T  120G  94% /mnt/multimedia
/dev/sdc1      ext3      459G  367G   69G  85% /mnt/shop.data
/dev/sdb1      vfat      511M  3.5M  508M   1% /boot/efi

```

Now this was run on the remote system, the one where the drives are physically located. 

No, the slower drive is sdb2, an internal SATA, ext4 drive. No NTFS and I don't know what "fuse" is, so I guess no?

---

### Post by TheFu on 2018-10-22
And where is the network drive in this list?  I don't see it.  Those are all local disks.  Show the mounts from the view of the remote client please.

---

### Post by rebeltaz on 2018-10-26
I'm sorry... I've been sick. This is the output from the laptop:

```

derek@laptop:~$ df -hT
Filesystem               Type      Size  Used Avail Use% Mounted on
/dev/sda1                ext4      458G  297G  138G  69% /
//192.168.1.15/shop_docs  cifs      226G   66G  161G  29% /mnt/shop_docs
//192.168.1.15/multimedia cifs      1.8T  1.7T  101G  95% /mnt/multimedia
//192.168.1.15/shop.data  cifs      459G  391G   69G  86% /mnt/shop.data

```

---

### Post by TheFu on 2018-10-26
Periodic slowness can happen from all sorts of issues.  Using wifi networking is one.  Having a bad cable that hasn't failed is another.  A disk beginning to fail is another.

On the Kodi forums, it is suggested to avoid CIFS/Samba for any media and use NFS.

If you are using Wifi, switch to almost any other sort of networking.  Wired ethernet is best, then powerline, then the cable networking, and wifi is a last resort. Using wired connections for networking provides predictable, consistent bandwidth, unlike wifi.

For the cable and drive health, I'd look at SMART data using smartctl.  Run a long test first, then review the data.  SMART data only shows problems 78% of the time for failing disks.  Some disks fail without displaying anything bad in the SMART data.  Hopefully, the disks are fine, especially the slower one.

Those are all guesses.  I can't see anything wrong with your setup.  I use autofs extensively too.  I've seen a 1-2 sec delay when it is first being mounted on-demand, but after that, performance is just like a typical mounted disk.  I don't use the "ghost" option, usually.

Totally unrelated, nothing to do with performance but placing permanent mounts under /mnt/ is an anti-pattern.  Professional Admins use /mnt/ for temporary mounts while working on stuff.  It is short and quick.  A pro might mount over the storage out of habit. I also see /media/ abused.  That area is for automatically mounted storage. A human shouldn't place anything there.   The Filesystem Hierarchy Standards are pretty clear on these. But it is your system.

---

### Post by rebeltaz on 2018-10-27
I appreciate the remarks. The /mnt/ thing... I started that back when I was new to linux and the habit just stuck. I have since read exactly what you pointed out, but by then I was already set in my ways :) I will look into NFS. As for wireless versus wired, with my laptop, that just isn't possible. Oh... and I will be sure to check the harddrive for potential errors, too/. Thanks for trying.

---

### Post by TheFu on 2018-10-27
NFS over spotty wifi is a bad idea.  Use read-only mounts if the wifi isn't 100% solid.  I'd use the "soft,async" option too.

I have a chromebook that doesn't have any wired ethernet port. Got a $20 3-port USB3-to-GigE adaptor for it.  It is wired at home 99% of the time.  Spent a year designing wifi deployments for a very large company with over 1,000 locations and helping with a few of their harder locations.  That convinced me to avoid wifi whenever possible.  Wifi isn't as stable as we humans think it is. The available bandwidth fluctuates wildly for no apparent reasons. Even when we were able to trace back to a cause and remove it, the fluctuations, just a little less, still happened.  10 ft or 50ft away, there were still wild fluctuations.  That's fine for human needs - surfing or email, but not for constant streaming.  To get around those issues, huge buffers are normally used on streaming devices and for streaming programs on computers, but having huge buffers is bad for all other uses on a computer.  It makes the network on the device appear to be locked up.

NFS and Samba/CIFS can be used to share the same storage areas.  CIFS for Windows and NFS for all Unix-like systems and sftp for portable devices like smartphones or tablets.  SFTP and NFS support native file permissions, which is very important.

Anyway, I hope you figure it out.  If you can, check out a powerline setup between the shop and the router.  Expect to get only 10% of the bandwidth, but it will be consistent, IME.  YMMV, of course, because we all have different wiring.  I've got a 600 Mbps powerline setup and use it to bridge floors here.  That provides 60 Mbps on the other floor which is more than enough for streaming and other needs. The rest of my network is GigE.

---

### Post by rebeltaz on 2018-12-01
I'm sorry for the delay in replying - I just saw this... I still haven't figured this out, but I have noticed that the problem seems to be with this laptop with the new 18.04 setup. I can transfer the same file from my shop computer to my girlfriend's Windows laptop (the same file that I transfer from my shop computer to my laptop), sitting right beside this laptop on the same wifi network and it starts the transfer immediately with no delay....

---

### Post by rebeltaz on 2018-12-27
OK, so I finally figured this out - quite by accident. It seems that one of the devices I had on my network was being auto-assigned the same IP address as something else on the network - not sure if it was the IP of my laptop or the server, but ... Once I forced that device to use a static IP, everything worked fine again. I have no idea how that could have happened, since my DHCP server is set to only give out addresses between .30 and .50 and my computers are in the single digit IPs, but... leave it to me to have odd issues.

---

