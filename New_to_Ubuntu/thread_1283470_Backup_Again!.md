---
title: "Backup Again!"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by cmcanulty on 2009-10-05
Well I spent 2 days reinstalling everything and even bought a new external Hard drive and I am having the same problem. I am extremely upset. I try to backup and after a few minutes the hard drive (NTFS) unmounts itself and backup stops. Please someone help me solve this soon or it is back to XP which I hate.I tried mount in terminal and plug in to mount both unmount spontaneously. It is not hardware as same thing happens on every external I try and they all work fine on my XP machine.Also no matter what I set in authorizations and user groups it lists the ex drive properties as owned by root. How can I change all external devices to my ownership. This is crazy that I can't even access my own devices no matter how much time or tweaks I do!Ok so I added sharing and I still can't share it here is the error message. I reinstalled everything to get rid of all this crap trying to get backup to work and now I am right back to adding pmount? sharing? and nothing works!They don't tell you where global smb.conf is
net usershare' returned error 255: net usershare add: cannot share path /media/New Volume as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = false" 
	to the [global] section of the smb.conf to allow this.

'net usershare' returned error 255: net usershare add: cannot share path /media/New Volume as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = false" 
	to the [global] section of the smb.conf to allow this.
Now I try it in Nautilus and I get 
this mess
cmcanulty@Gateway:~$ gksudo nautilus 
Initializing nautilus-open-terminal extension

** (nautilus:3524): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: unknown format for key 'new volume/usershare_acl' as it contains 'Everyone:F,'.  Assuming that the share is read-only
Nautilus-Share-Message: unknown format for key 'new volume/usershare_acl' as it contains 'Everyone:F,'.  Assuming that the share is read-only

--- Hash table keys for warning below:
--> file:///media
--> file:///root
--> file:///

(nautilus:3524): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 3 elements at quit time (keys above)

(nautilus:3524): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 4 elements at quit time
Shutting down nautilus-open-terminal extension
cmcanulty@Gateway:~$ 
cmcanulty@Gateway:~$ 
cmcanulty@Gateway:~$

---

### Post by Sir Jasper on 2009-10-05
Hi,

Google HDClone for a US $50ish almost guaranteed solution.

My regards

Also, did you try SimpleBackup as suggested in another of your many threads on this subject?

---

### Post by cmcanulty on 2009-10-05
I tried every backup program I could find. The problem is periodic unmounted of ext devices is there any solution to this and how to I enable sharing of them it just says root only even when I do sudo or sudo su.

---

### Post by Sir Jasper on 2009-10-05
Hi,

I have no other suggestions. I can see you are in desperate need of help but do try to give full though brief answers to any questions you may be asked. Possibly edit your post above if you can make it shorter and clearer and do not keep opening new threads.

My regards

---

### Post by cmcanulty on 2009-10-05
Well I only open a new thread because nothing works. The problem is very simple. Any ext drive I use randomly unmounts. So I can't unmount properly either as they unmount themselves. This prevents the backups from ever finishing.

---

### Post by Sir Jasper on 2009-10-05
Hi again,

Hopefully your last post will bring some help, though I would still suggest you simplify your first post above.

Good luck and just bump this thread once a day, as may be necessary, if a 
solution is not forthcoming.

My regards

---

### Post by steveneddy on 2009-10-05
Not sure where to start here:

I suggest you copy and paste in terminal, not typing. Just highlight with mouse and then go to terminal and push the scroll wheel down and viola! auto paste!

How to [COLOR=Red]**locate**[/COLOR] **smb.conf**

In Terminal:

```
locate smb.conf
```

path is /etc/samba/smb.conf

So, in Terminal we:

```
gksudo gedit /etc/samba/smb.conf
```

and add this line at the** bottom of the file**:

 ```
usershare owner only = false
```

Restart and see where you are. 

SUGGESTION:

Calm down.

Break up your threads in small easy to read sections.

Explain again what you are trying to accomplish? Are trying to backup an NTFS drive installed on a desktop to an external HD?

---

### Post by cmcanulty on 2009-10-05
I am simply trying to put my own files from an ext HD onto my laptop without constant unmounts of the ext HD. I did the above addition to etc/samba but didn't see a save option, will that be OK? I am so upset because I have spent countless hours trying to fix this. I am very experienced on windows and support 10 computers at our local library which I have put Ubuntu  on 8 of them. I am committed to Ubuntu but have to be able to backup my files and have them on the laptop, without spending hours a day trying to do that.

---

### Post by steveneddy on 2009-10-05
You also might try installing **ntfsprogs**

```
sudo apt-get install ntfsprogs
```

and use the ntfsclone tool in this set of programs.

Good luck.

Post results back here and **don't start any other threads regarding this issue.**

---

### Post by steveneddy on 2009-10-05
[https://help.ubuntu.com/community/jmburgess/Backup](https://help.ubuntu.com/community/jmburgess/Backup)

Try this for reference.

There are three or four applications that may help you.

You may want to search for mounting external hard drives.

[http://ubuntuforums.org/showthread.php?t=687376](http://ubuntuforums.org/showthread.php?t=687376)

---

### Post by steveneddy on 2009-10-05
> **cmcanulty said:**
> I am simply trying to put my own files from an ext HD onto my laptop without constant unmounts of the ext HD. I did the above addition to etc/samba but **didn't see a save option**, will that be OK? I am so upset because I have spent countless hours trying to fix this. I am very experienced on windows and support 10 computers at our local library which I have put Ubuntu  on 8 of them. I am committed to Ubuntu but have to be able to backup my files and have them on the laptop, without spending hours a day trying to do that.

See picture

---

### Post by steveneddy on 2009-10-05
If I read this correctly you are trying to back up an NTFS formatted external hard drive to an Ubuntu laptop.

Let me ask you [B]why are you trying to back up NTFS files to an Ubuntu machine?
[/B]
Linux (Ubuntu) will not read/write NTFS file systems natively. You will need additional tools to read/write NTFS.

If they are backed up files from a Windows machine why don't you leave them on the external hard drive?

Explain why you need to put Windows (NTFS) files on you Ubuntu laptop.

---

### Post by LewRockwell on 2009-10-05
why did you start yet another thread?

how did Clonezilla work for you?

.

---

### Post by lavinog on 2009-10-05
I am really confused:
Are you using a usb external hd? 
If so:
 What is the reason for using samba?
 Does the drive mount when it is first connected?
 Is the problem that the drive randomly unmounts?
 if so:
  Post the output of **dmesg** after a random unmount...it could be a hardware issue. (Some chipsets have issues still with linux drivers...sometimes you may have to dropdown to usb1.1 to get a reliable connection.  Also try another usb cable...not all cables are the same)

---

### Post by NTolerance on 2009-10-05
> **steveneddy said:**
> If I read this correctly you are trying to back up an NTFS formatted external hard drive to an Ubuntu laptop.

Let me ask you [B]why are you trying to back up NTFS files to an Ubuntu machine?
[/B]
Linux (Ubuntu) will not read/write NTFS file systems natively. You will need additional tools to read/write NTFS.

If they are backed up files from a Windows machine why don't you leave them on the external hard drive?

Explain why you need to put Windows (NTFS) files on you Ubuntu laptop.

Recent versions of Ubuntu have full NTFS read/write support built into the default install thanks to NTFS-3G.  

I'd like to know what options the thread starter is using with rsync.  If any of them have to do with the archive option or permission transfer, that will likely fail when copying to an NTFS drive.  I see no reason why you can't rsync a directory to an NTFS drive as long as you don't try to preserve the permissions.

The biggest problem here is that the rsync errors are non-descript.  We need more info and testing to get to the point where we get a meaningful error message e.g. permission denied, operation not supported, etc...

---

### Post by Sir Jasper on 2009-10-05
Hi,

I had totally misunderstood. I originally thought the idea was to back up an effectively working copy of your Ubuntu internal hard drive to an external drive.

**As asked in the post before Lew&#347; can you please explain clearly what you want to do and why you want to do it?**

[COLOR="Blue"]Lew[/COLOR], I would like to suggest you delete most of your post, which certainly makes your point but is not at all helpful and it is the second time you you have made your point at such length and I would assume that your message is now received. The guy is frustrated and needs help.

My regards to all
**Added:**
Lew, Thanks for withdrawing most of your post.

---

### Post by ankspo71 on 2009-10-05
Hi,
I see there is a laptop involved so I was wondering if the external drive was connected by USB cables through a USB Hub. I don't have a laptop or an external drive, so this advice is only from searching the web.

> Many USB devices don't work well on hubs. Cameras, scanners and especially USB drives are known to have problems with hub connectivity. 
Borrowed from:
[http://www.everythingusb.com/usb2/faq.htm](http://www.everythingusb.com/usb2/faq.htm)

You might have to use the drive with it's own connection to the laptop (if possible)
James

---

### Post by cariboo on 2009-10-05
How is the usb drive powered? does it have a separate power supply, or does it use a second usb cable for power?

If your drive uses a second usb cable for power plug it into a powered usb hub instead of into the computer, as the computer may not be producing enough power for the hard drive.

You don't need samba to mount a usb connected drive, so you are looking in the wrong place to solve your problem.

One other thing I would suggest, the next time the drive disconnect open a terminal and type:

```
dmesg | grep -n20
```

The above command may give us a clue why the drive is disconnecting. copy and paste the output into a text editor, then paste the output in your next post.

---

### Post by cmcanulty on 2009-10-05
Here is the output
cmcanulty@Gateway:~$ dmesg | grep -n20
Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.
cmcanulty@Gateway:~$ 
cmcanulty@Gateway:~$ 
cmcanulty@Gateway:~$ 

I am simply trying to get my files from my XP machine over to Ubuntu. As I said this happens with every ext usb device.And with every backup application and it happened when I tried ext3, fat 32 and NTFS
formatting on the drives and I just did a clean install of Ubuntu and it still happens. 
It is driving me crazy! And it just went unmounted (the power DOES'T go out it just unmounts) again so I will do the terminal command again incase that may help but it doesn't say much.And it has a power brick it isn't usb powered. It does it with 2 ext drives, with flash drives with my SDHC card in a usb adapter.I'm sorry apparently I have posted too much but unless this 
is solvable I can't stay with Ubuntu which I really want to. I am posting screen shots of the grsync errors and my settings which certainly could be incorrect.
cmcanulty@Gateway:~$ dmesg | grep -n20
Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.
cmcanulty@Gateway:~$ 
cmcanulty@Gateway:~$ 
cmcanulty@Gateway:~$

---

### Post by Sir Jasper on 2009-10-05
Hi again,

It appears you can mount your external drive, so have you tried to copy and paste some files as an interim measure?

My regards

**Added:**

What method did to use to get your files from your Windows machine to your external drive?

---

### Post by lavinog on 2009-10-05
> **cmcanulty said:**
> Here is the output
cmcanulty@Gateway:~$ dmesg | grep -n20
Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.
cmcanulty@Gateway:~$ 
cmcanulty@Gateway:~$ 
cmcanulty@Gateway:~$ 

I think the -n20 was supposed to be just -n. can you try to post the output of **dmesg** (with or without |grep -n) again. dmesg outputs messages from the kernel, it will help with finding a solution to your problem.  Whenever something weird happens, always look at dmesg first.

when you post the output to the forum, please enclose inside [noparse]```

```[/noparse]
example:
[noparse]```

cmcanulty@Gateway:~$ dmesg | grep -n20
Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.
cmcanulty@Gateway:~$ 
cmcanulty@Gateway:~$ 
cmcanulty@Gateway:~$ 

```[/noparse]
will look like:
```

cmcanulty@Gateway:~$ dmesg | grep -n20
Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.
cmcanulty@Gateway:~$ 
cmcanulty@Gateway:~$ 
cmcanulty@Gateway:~$ 

```
When the output is long, this will make the thread much more easier to read, and will help you get a solution quicker.  Also stick with one thread per problem. It will be less frustrating for you if you don't have to re-explain your problem over and over.

It will also be helpful to post the output of **lshw** this will tell us exactly what hardware you have.  The issue you are experiencing may be common to brand X component.

So we know exactly what kernel you are using post the output of:
```
uname -a
```
This will tell us the exact kernel version you are using.

I have experienced the same symptoms in the past, where any usb storage device would disconnect at random times.  There were work arounds for this behavior, and eventually the bug was fixed.  I would like to see the requested information before I start giving you the wrong advice.

---

### Post by steveneddy on 2009-10-05
It may not matter, but what kind of data are you trying to copy?

Is it music, pics, video or just raw data?

---

### Post by cmcanulty on 2009-10-06
I have tried copy and paste but the same thing happens, it unmounts before I can get them copied, it is 70 GB I need. I put files on ext HD before I switched from XP to Ubuntu. As I have said I can always mount it but I can't keep it mounted.

---

### Post by Sir Jasper on 2009-10-06
Hi,

Thank you for your reply.

Can you copy and paste just a few files before the unmount?

Did you originally copy and paste to your external drive or did you use a Windows backup program?

My regards

---

### Post by stinger30au on 2009-10-06
> **cmcanulty said:**
> 
I am simply trying to get my files from my XP machine over to Ubuntu. As I said this happens with every ext usb device.And with every backup application and it happened when I tried ext3, fat 32 and NTFS
formatting on the drives and I just did a clean install of Ubuntu and it still happens. 
It is driving me crazy


ok, so lets get this stright

you plugged the external hdd in to a windows xp pc and backed up data to it


what program on xp did you use to back up the data to the external hdd??

the data you backed up, what is it? it is photos, mp3's, avi files, or the windows directory itself??

---

### Post by NTolerance on 2009-10-06
Can we throw out rsync for just a minute?  Rsync is a complex program with poor error reporting.  

Try using just the Nautilus file manager to copy the files and see if that works.  Try juts a few folders at a time instead of the whole 70GB.  Baby steps.

---

### Post by cmcanulty on 2009-10-06
Well I got backed up by restarting the ext HD about a hundred times. The reason I need grsync is to not have to do 70GB every time. The random unmounting is driving me crazy though. Is there a way to have a permanent mount point? I don't want it always running though.I searched for documentation of the various options on grsync but had no luck.I just copied the files to the ext HD from windows and it is pdfs, word docs, pictures etc no windows specific things.

---

### Post by Sir Jasper on 2009-10-06
Hi again,

Can you please confirm that you now have all those essential files on your:
(1) Windows internal hard drive,
(2) External hard drive, and
(3) Ubuntu internal hard drive (despite it was a slow and painful process)?

(4) Can you also say if you have one or two external hard drives large enough to hold all your essential data?

If you can answer YES to (3) and (4) above what do you think about trying to back up your Ubuntu data to a free external drive so that you could save any new documents etc as well? It just might or might not work better than the reverse direction, but if it works you could then do much smaller incremental or differential backups to add to or to amend that data.

My regards

PS I hope any volunteer helper(s) will still try to solve your ¨unmount¨ problem.

---

### Post by cmcanulty on 2009-10-06
I will soon have a large enough HD to do that yes to all your questions. I was having so much trouble backing up to my 500GB Maxtor that I returned it as it was still under warranty. Now I know that it was not defective as the same exact thing happens with my WD 120GB drive. But next week I should receive back my 500GB then I will do as you suggest and do a new clean backup to the Maxtor, although it will take forever as it unmounts every few minutes. Is it possible I need a Linux specific driver for both the ext HDs? Oh I just got an email my 500GB drive is already shipped via UPS so please check this thread in a few days to a week when I try it again, thanks for all the advice! I am afraid I got really upset as I had 2 backups to both ext drives and then had none and I really need the files. Now that I have a backup I can relax and go slow. The random unmounting thou is really strange and no solution so far.

---

### Post by cariboo on 2009-10-06
Sorry, that was a typo on my part the command should be:

```
dmesg | tail -n20
```

I'm surprised no one else picked that up.

---

### Post by Sir Jasper on 2009-10-06
Hi,

Suppose you make a ¨New_Stuff¨ folder in your Home Directory with sub-folders say, Documents, Music or whatever you want.

Then if you save everything new there, all your current essentials will be on your 120 GB external drive and XP internal drive and you can do a much quicker ¨New_Stuff¨ backup.

My regards

---

### Post by cmcanulty on 2009-10-06
Here is the command with the ext HD attached, I will immediately post another with it unmounted
cmcanulty@Gateway:~$ dmesg | tail -n20
[44744.619202] sd 13:0:0:0: Attached scsi generic sg2 type 0
[46091.598710] usb 1-4: USB disconnect, address 21
[46104.092072] usb 1-3: new high speed USB device using ehci_hcd and address 22
[46104.232599] usb 1-3: configuration #1 chosen from 1 choice
[46104.236478] scsi14 : SCSI emulation for USB Mass Storage devices
[46104.241094] usb-storage: device found at 22
[46104.241100] usb-storage: waiting for device to settle before scanning
[46109.240291] usb-storage: device scan complete
[46109.240899] scsi 14:0:0:0: Direct-Access     WDC      WD1200BB-22FTA0  15.0 PQ: 0 ANSI: 2
[46109.244849] sd 14:0:0:0: [sdb] 234441648 512-byte hardware sectors: (120 GB/111 GiB)
[46109.245620] sd 14:0:0:0: [sdb] Write Protect is off
[46109.245627] sd 14:0:0:0: [sdb] Mode Sense: 53 00 00 08
[46109.245632] sd 14:0:0:0: [sdb] Assuming drive cache: write through
[46109.281836] sd 14:0:0:0: [sdb] 234441648 512-byte hardware sectors: (120 GB/111 GiB)
[46109.298143] sd 14:0:0:0: [sdb] Write Protect is off
[46109.298153] sd 14:0:0:0: [sdb] Mode Sense: 53 00 00 08
[46109.298159] sd 14:0:0:0: [sdb] Assuming drive cache: write through
[46109.298170]  sdb: sdb1
[46109.317534] sd 14:0:0:0: [sdb] Attached SCSI disk
[46109.317665] sd 14:0:0:0: Attached scsi generic sg2 type 0
cmcanulty@Gateway:~$

---

### Post by cmcanulty on 2009-10-06
Here is the terminal with ext HD unmounted
cmcanulty@Gateway:~$ dmesg | tail -n20
[46091.598710] usb 1-4: USB disconnect, address 21
[46104.092072] usb 1-3: new high speed USB device using ehci_hcd and address 22
[46104.232599] usb 1-3: configuration #1 chosen from 1 choice
[46104.236478] scsi14 : SCSI emulation for USB Mass Storage devices
[46104.241094] usb-storage: device found at 22
[46104.241100] usb-storage: waiting for device to settle before scanning
[46109.240291] usb-storage: device scan complete
[46109.240899] scsi 14:0:0:0: Direct-Access     WDC      WD1200BB-22FTA0  15.0 PQ: 0 ANSI: 2
[46109.244849] sd 14:0:0:0: [sdb] 234441648 512-byte hardware sectors: (120 GB/111 GiB)
[46109.245620] sd 14:0:0:0: [sdb] Write Protect is off
[46109.245627] sd 14:0:0:0: [sdb] Mode Sense: 53 00 00 08
[46109.245632] sd 14:0:0:0: [sdb] Assuming drive cache: write through
[46109.281836] sd 14:0:0:0: [sdb] 234441648 512-byte hardware sectors: (120 GB/111 GiB)
[46109.298143] sd 14:0:0:0: [sdb] Write Protect is off
[46109.298153] sd 14:0:0:0: [sdb] Mode Sense: 53 00 00 08
[46109.298159] sd 14:0:0:0: [sdb] Assuming drive cache: write through
[46109.298170]  sdb: sdb1
[46109.317534] sd 14:0:0:0: [sdb] Attached SCSI disk
[46109.317665] sd 14:0:0:0: Attached scsi generic sg2 type 0
[46256.422440] usb 1-3: USB disconnect, address 22
cmcanulty@Gateway:~$

---

### Post by Sir Jasper on 2009-10-06
Hi,

One last idea is to think about using the Partition Editor, Gparted, to perhaps partition your Maxtor (unmounted) into smaller chunks with appropriate formatting before you backup any data.

Good luck
**Added:**
If the ¨unmount" problem is solved it would probably be a good idea for your Maxtor to have, if possible, at least one partition of the same size as your Ubuntu drive so that you could clone everything to it including all your essential data.

---

### Post by cmcanulty on 2009-10-07
Unmount isn't solved I backed up by taking 3 days and hundreds of remountings.

---

### Post by lavinog on 2009-10-07
If you mount the drive and don't do anything, does it eventually unmount on its own?

---

### Post by cmcanulty on 2009-10-07
Yes that is the whole problem it unmounts itself every few minutes so I can never unmount it properly.Both hard drives do exactly the same thing.

---

### Post by Sir Jasper on 2009-10-07
Hi,

My second paragraph in my # 34 was badly worded. It started ¨If¨" whereas ¨When¨ would have been a better choice.

My suggestion @ # 31 may well be your best and most efficient option until the ¨unmount¨ problem is fixed.

I am out of ideas except I just wonder if your external drive problem _might_ have been caused by overheating.

My regards

Do not give up hope though - there are some very clever helpers who may well find the answer.

---

### Post by lavinog on 2009-10-07
> **cmcanulty said:**
> Yes that is the whole problem it unmounts itself every few minutes so I can never unmount it properly.Both hard drives do exactly the same thing.

So it has nothing to do with what backup program you are using.

Does it have the same behaviour using a live cd?

Are you using the same usb cable for both harddrives.

also can you post the output of lshw so we know what your machine specs are.

If you feel confident, you may want to hookup one of the drives internally. (open up the external enclosure and you will find an internal hard drive that should hook up to your motherboard)

---

### Post by cariboo on 2009-10-07
What is the output of:

```
dmesg | tail -n20
```

When the drive fails, as soon as the drives umounts itself check the output of dmesg and post it here.

I haven't read the whole thread, but do you have the same problem when running Windows?

---

### Post by lavinog on 2009-10-07
he posted the dmesg earlier
all it showed was:
```
[46256.422440] usb 1-3: USB disconnect, address 22
```

---

### Post by cmcanulty on 2009-10-07
No I have said it happens only in Ubuntu with both ext drives they work fine in windows. Different USB cords for each, happens with every backup program.It is an unmounting problem. As soon as they unmount I can remove USB and immediately plug it back in and they run for a few more minutes.Yes also happens with live CD.

---

### Post by lavinog on 2009-10-07
I noticed in one of your other posts that you are backing up the thumbnail cache.
There is no need to back this up, and you can purge the cache by using this command:
```
find ~/.thumbnails -name '*.png' -delete
```
leave the '-delete' off if you want to check what will be deleted first.

also if you are using grsync. in the advanced options there is a option to keep partially transferred files...you might want to enable that so that if the drive unmounts while transferring a large file, it wont have to start over on the next time around.

---

### Post by cmcanulty on 2009-10-07
```
cmcanulty@Gateway:~$ dmesg | tail -n20
[   21.483143] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   21.561580] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   21.794598] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   21.956051] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[   21.956056] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed in July 2008.
[   21.956059] b43-phy0 warning: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[   22.001459] Registered led device: b43-phy0::tx
[   22.001474] Registered led device: b43-phy0::rx
[   22.001491] Registered led device: b43-phy0::radio
[   22.024586] b43-phy0: Radio turned on by software
[   22.025015] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.092040] b43-phy0: Radio hardware status changed to DISABLED
[   22.124085] b43-phy0: Radio turned on by software
[   22.124089] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[   22.818864] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   22.819044] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   33.652033] eth0: no IPv6 routers present
[   51.761427] sky2 eth0: rx length error: status 0x5ea0100 length 1510
[   53.325342] sky2 eth0: rx length error: status 0x5ea0100 length 1510
[   79.444054] Clocksource tsc unstable (delta = -245219968 ns)
cmcanulty@Gateway:~$ 

```
That is without the ext HD connected. I will next post with it connected

---

### Post by cmcanulty on 2009-10-07
```
cmcanulty@Gateway:~$ dmesg | tail -n20
[  383.498350] usb 1-3: configuration #1 chosen from 1 choice
[  383.650439] Initializing USB Mass Storage driver...
[  383.652670] scsi2 : SCSI emulation for USB Mass Storage devices
[  383.653063] usbcore: registered new interface driver usb-storage
[  383.653071] USB Mass Storage support registered.
[  383.695084] usb-storage: device found at 3
[  383.695091] usb-storage: waiting for device to settle before scanning
[  388.695310] usb-storage: device scan complete
[  388.695849] scsi 2:0:0:0: Direct-Access     WDC      WD1200BB-22FTA0  15.0 PQ: 0 ANSI: 2
[  388.704123] sd 2:0:0:0: [sdb] 234441648 512-byte hardware sectors: (120 GB/111 GiB)
[  388.704946] sd 2:0:0:0: [sdb] Write Protect is off
[  388.704953] sd 2:0:0:0: [sdb] Mode Sense: 53 00 00 08
[  388.704958] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  388.705972] sd 2:0:0:0: [sdb] 234441648 512-byte hardware sectors: (120 GB/111 GiB)
[  388.707071] sd 2:0:0:0: [sdb] Write Protect is off
[  388.707078] sd 2:0:0:0: [sdb] Mode Sense: 53 00 00 08
[  388.707083] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  388.707092]  sdb: sdb1
[  388.759181] sd 2:0:0:0: [sdb] Attached SCSI disk
[  388.759305] sd 2:0:0:0: Attached scsi generic sg2 type 0
cmcanulty@Gateway:~$ 


``` 
That was with it connected I don't have a clue what it means

---

### Post by lavinog on 2009-10-07
> **cmcanulty said:**
> 
That is without the ext HD connected. I will next post with it connected

please post after it **automatically** unmounts, so we can see if there is an error that causes it.

---

### Post by cmcanulty on 2009-10-07
I just found a new backup program called back in time I am trying to see if unmounting continues with it.

---

### Post by lavinog on 2009-10-07
Taken from [http://backintime.le-web.org/documentation/](http://backintime.le-web.org/documentation/)
> Keep in mind that Back In Time is just a GUI. The real magic is done by rsync 
It uses rsync as a back end...you are going to have the same problems.
In fact, rsync is the back end for many backup utilities.  I would at least try the partial option i mentioned before.

---

### Post by renkinjutsu on 2009-10-07
it IS possible to get data from an unmounted drive.. but that involves dd and creating a block device on your own harddrive and then mounting it with a loop option then moving all your backed up files out of it D;

---

### Post by lavinog on 2009-10-07
> **renkinjutsu said:**
> it IS possible to get data from an unmounted drive.. but that involves dd and creating a block device on your own harddrive and then mounting it with a loop option then moving all your backed up files out of it D;
It wont work if the drive is disconnected though. It keeps unmounting because it keeps disconnecting.

---

### Post by cariboo on 2009-10-07
If you mount the drive manually does it automatically unmount?

To mount manually, make sure the drive is unmounted. then in a terminal type:

```
sudo mount /dev/sdb1 /mnt
```

The drive won;t show up on your desktop, you will have to navigate to /mnt. Open nautilus and click File System-->/mnt

---

### Post by Temposs on 2009-10-07
Another idea that comes to my mind is to try different USB ports in the machine. If you have front and rear USB ports, try all of them and see if the problem persists in all of them. Sometimes USB ports can have wonky behavior for some reason.

------

Also, if you want a backup program that is quite simple to use and doesn't use rsync as the backend, there is Deja Dup, which uses duplicity as the backend.

[https://launchpad.net/deja-dup](https://launchpad.net/deja-dup)

It's in the Ubuntu repositories, but if you want a better version, try installing the ppa:
[https://launchpad.net/~deja-dup-team/+archive/ppa](https://launchpad.net/~deja-dup-team/+archive/ppa)

---

### Post by cmcanulty on 2009-10-08
I had tried the manual mount but I was typing
sudo mount /dev/sdb1 
I wasn't adding the /mnt at the end, didn't realize I should
will try that and the other suggestions tomorrow, thanks.

---

### Post by cmcanulty on 2009-10-09
OK I think I have narrowed down the problem. When I select all and copy files to ext HD it doesn't unmount. Any backup that front ends rsync causes the drive to unmount every few minutes. So now I can copy 70GB to ext HD OK but sure would like to be able to do incremental backups. I tried the deju Dup suggested above but couldn't get the app source to add to repositories. The add window didn't like the link given on page so I downloaded it but there wasn't a deb package to install I could see. MY EZ BackitUP in windows was a great easy fast incremental backup. I like to just have exact copies of files, no compression and no encryption as that way I can carry the ext HD and use it at other places as needed.I tried using it on Ubuntu with wine but it would stop with the error, too many open files or folders. Is there a Ubuntu backup that isn't a front end for rsync as that seems to be the villan in the unmounting issue? Thanks:KS

---

### Post by cmcanulty on 2009-10-09
I am now trying to remove Back in Time and Back in Time Root (which came along with it). It doesn't show up in synaptic or add/remove any suggestions? It was another rsync front end that didn't work.Oh it doesn't work to copy and paste docs eitther it goes awhile then again get input output error and drive disappears.

---

### Post by cmcanulty on 2009-10-09
Well I was wrong, I tried copying my docs and pasting to ext drive and again power light stays on and after a few minutes red light goes out and drive unmounts.This is a huge issue if I can't back up my files.

---

### Post by Sir Jasper on 2009-10-09
Hi,

You told us your Ubuntu 70 GB data is already on your 120 GB external and your XP internal drive. I had previously suggested you open a separate Ubuntu file with sub-folders for Music etc since it would be hugely quicker to tranfer (ie backup) just your new data to your 120 GB external or your 500 GB external.

You did not reply to that suggestion as a temporary solution.

Did you try a different USB slot as someone else suggested?

I cannot remember what you said about a different cable?

Your problem seems more likely to be hardware (rather than software) related since even copy and paste is temperamental. I would strongly suggest you do not experiment with different software until your hardware is checked.

My regards

---

### Post by cmcanulty on 2009-10-09
Well I have tried different ports, small copy and pastes and I am about ready to throw in the towel. I love the idea of Ubuntu but I can't spend weeks trying to accomplish something and risk losing all my data.The library now has Ubuntu on 6 computers which I did, but there the librarians now can't print from their XP machines. I tried Ubuntu with 5. a few years ago. So far, I can't backup I can't use my wireless and I am totally frustrated.If I could have someone hands on and maybe edit fstab or something else esoteric maybe it would work. But how can it be hardware when everything works fine in XP on this machine before I switched and on other machines still.There is a Ubuntu bug on ext hard drives which I found lots of references to ext Hard drives randomly unmounting but no solutions anywhere except buy all new equipment.And I am sick of you cannot mount this volume no matter how many times I set it with r &W, very weird security if it allows me to reformat and destroy everything but won't let me mount externals.If Ubuntu wants to keep people you have to be able to actually use your computer not get messes like this that I am supposed to understand, nowI can't even mount my flash drive from sudo nautilus
cmcanulty@Gateway:~$ sudo mount
[sudo] password for cmcanulty: 
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/cmcanulty/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=cmcanulty)
/dev/sdc1 on /media/sdc1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
cmcanulty@Gateway:~$ 
cmcanulty@Gateway:~$

---

### Post by Sir Jasper on 2009-10-09
Of course it can be hardware. My car works today but there is no guarantee it will tomorrow, nor that the light bulb I am now using will last for ever.
Power surges, thunderstorms, spilt coffee, children or whatever may do harm.
Wires fray, connections come loose ................

---

### Post by LewRockwell on 2009-10-09
Clonezilla works across all platforms without all those annoying problems inherent in any specific version of any specific operating system on any specific subset and assembly of hardware

.

---

### Post by cmcanulty on 2009-10-09
But how can I use anything if I can't mount a drive and they work today on windows machines, in fact every so often I can mount them in Ubuntu until they unmount again or I get only root can mount so I do sudo mount but of course I can't navigate to the right place because they aren't mounted. Everyone has been very kind and helpful but nothing has worked and I can't even dump Ubuntu as I need my files. I was hoping with me installing Ubuntu on 6 public library machines I would have more luck with solutions.

---

### Post by LewRockwell on 2009-10-09
> **cmcanulty said:**
> But how can I use anything if I can't mount a drive and they work today on windows machines, in fact every so often I can mount them in Ubuntu until they unmount again or I get only root can mount so I do sudo mount but of course I can't navigate to the right place because they aren't mounted. Everyone has been very kind and helpful but nothing has worked and I can't even dump Ubuntu as I need my files. I was hoping with me installing Ubuntu on 6 public library machines I would have more luck with solutions.


Step One: Get Clonezilla and make the necessary clones of the desired partition(s) and/or disk(s)

(we make CLONES and not images so that we can actually manipulate the data on the clones...as opposed to not being able to do that with images)



Step Two: After securing desired data through your preferred method(s) then you can adjust/manipulate/create/delete/erase/whatever/etc. your partition(s), directories, and/or data

(we like smallish partitions that are easy to clone/maintain/replace/reformat/etc.)

Some of these partitions can be viewed here:

[http://ubuntuforums.org/showthread.php?t=1222961](http://ubuntuforums.org/showthread.php?t=1222961)

And here:

[http://ubuntuforums.org/showthread.php?t=1252042](http://ubuntuforums.org/showthread.php?t=1252042)




Step Three: After making the desired alterations and improvements to your systems/partitions/drives then you'll obviously need to make new clones/back-ups for these




Additional Commentary:

It's great that you've contributed your valuable time in facilitating machines other than your own personal units, however...without a firm plan to administer those machines you might end up being criticized for your efforts if there are difficulties/failures

.

---

### Post by stinger30au on 2009-10-09
do u have a different brand of external hdd you can try

i have tried a number of them and they all work fine

---

### Post by mike555 on 2009-10-09
I have used a bunch of different ext. harddrives and the only one I had trouble with is a USB powered one , I think my laptop had not enough power to the USB , because when I plugged it into a powered USB hub it worked fine ........... could that be your problem?
    If your ext. harddrive is USB powered you might try a powered hub .

---

### Post by LewRockwell on 2009-10-09
> **mike555 said:**
> I have used a bunch of different ext. harddrives and the only one I had trouble with is a USB powered one , I think my laptop had not enough power to the USB , because when I plugged it into a powered USB hub it worked fine ........... could that be your problem? If your ext. harddrive is USB powered you might try a powered hub.

+ 1

We do NOT recommend the purchase or usage of external peripheral devices which rely solely on the power supplied through the USB cable/connection(s)

If you already have these devices then a powered hub will indeed make your experience much more enjoyable and potentially less problematic

Furthermore, it should be noted that operating additional consumptive devices via your primary power supply(desktop/laptop/server/etc) should be done sparingly and with caution(if at all) and may overload the device causing it to fail prematurely and/or catastrophically(fire)

To wit:

Just because there are fifty outlets in your home...that does NOT mean fifty high-wattage devices(say hair-dryer/toaster-oven/microwave) can be plugged in and operated at the same time

Or...

There is plenty of money in your checking account as long as you have checks in your pocket...no?

Oui!

[http://upload.wikimedia.org/wikipedia/en/5/58/OuiF.ogg](http://upload.wikimedia.org/wikipedia/en/5/58/OuiF.ogg)

.

---

### Post by cmcanulty on 2009-10-09
I have 2 ext HDs, 4 flash drives, and a usb adapter for a SDHC card all won't mount in Ubuntu both HDs have their own power brick. I know how to back up but it is impossible if nothing will stay mounted.

---

### Post by Temposs on 2009-10-09
Something very odd is going on with your setups. As you can tell this is not a typically encountered issue. It is not typical of Ubuntu to have this effect.

I'm running a server right now with an external drive attached. I have automatic backups that go remotely to that server and then on through to the external drive. It is seamless. It stays on 24/7. I never have to do anything to it.

Try installing Deja Dup from the Applications->Add/Remove program, since you couldn't figure out how to install the ppa. See if you can get a backup going with that.

---

### Post by cmcanulty on 2009-10-09
I searched for it and got nothing

---

### Post by Temposs on 2009-10-09
Which version of Ubuntu are you using?

---

### Post by LewRockwell on 2009-10-09
> **Temposs said:**
> Something very odd is going on with your setups. As you can tell this is not a typically encountered issue. It is not typical of Ubuntu to have this effect.

I'm running a server right now with an external drive attached. I have automatic backups that go remotely to that server and then on through to the external drive. It is seamless. It stays on 24/7. I never have to do anything to it.

Agreed that something is just not right

Might be some sort of wierd Gateway BIOS/Motherboard schism

.

---

### Post by cmcanulty on 2009-10-10
I am using 9.04. I think I'll have to go back to dual boot as this constant hassle and losing all my externals isn't worth it. I wish they would stop adding glitzy stuff to the distros and first make everything work with Linux. I was willing to spend weeks reading and tweaking to get my system up which most people wouldn't but still it defeated me.

---

### Post by Sir Jasper on 2009-10-10
Hi,

HDClone has its own Operating System. The Standard edition costs about US $50 and will almost certainly work, except perhaps if there is a hardware fault (which does seem to be the most likely explanation as I am not aware of another reader experiencing your serious unmounting problem).

My regards

---

### Post by lavinog on 2009-10-10
Why have you not posted the system specs yet???
```
lshw

```

---

### Post by cmcanulty on 2009-10-10
Here it is
```

```cmcanulty@Gateway:~$ lshw
WARNING: you should run this program as super-user.
gateway                   
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1001MiB
     *-cpu
          product: Mobile AMD Athlon(tm) 64 Processor 3700+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 15.4.2
          size: 2400MHz
          capacity: 2400MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 1MiB
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI-X Root Port
             vendor: ATI Technologies Inc
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-display UNCLAIMED
                description: VGA compatible controller
                product: M24 1P [Radeon Mobility X600]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: 88E8036 PCI-E Fast Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 10
                serial: 00:03:25:1b:f2:62
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.2.2 latency=0 module=sky2 multicast=yes
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ohci_hcd latency=64
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ohci_hcd latency=64
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide
             description: IDE interface
             product: IXP SB400 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_atiixp latency=64
        *-isa
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-pcmcia
                description: CardBus bridge
                product: CB1410 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 5
                bus info: pci@0000:03:05.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-network
                description: Network controller
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 7
                bus info: pci@0000:03:07.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: driver=b43-pci-bridge latency=64 module=ssb
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306 Fire II IEEE 1394 OHCI Link Layer Controller
                vendor: VIA Technologies, Inc.
                physical id: e
                bus info: pci@0000:03:0e.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=32 module=ohci1394
        *-multimedia
             description: Multimedia audio controller
             product: IXP SB400 AC'97 Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ATI IXP AC97 controller latency=64 mingnt=2 module=snd_atiixp
        *-communication
             description: Modem
             product: SB400 AC'97 Modem Controller
             vendor: ATI Technologies Inc
             physical id: 14.6
             bus info: pci@0000:00:14.6
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ATI IXP MC97 controller latency=64 mingnt=2 module=snd_atiixp_modem
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:47:03:8a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: e6:13:c5:0a:3b:77
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
cmcanulty@Gateway:~$

---

### Post by lavinog on 2009-10-11
Are you familiar with bios?
If so see if you can find an option to disable High speed (or enhanced) USB support. Then see if the drives keep disconnecting.  If that fixes the problem then you are suffering from a compatibillity issue with the ehci_hcd module.  As of jaunty the module has been compiled into the kernel so the workarounds involving rmmod will no longer work: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/354832](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/354832)

Also I would check with gateway to see if there is an updated bios for your system.

---

### Post by LewRockwell on 2009-10-11
> **LewRockwell said:**
> Agreed that something is just not right

Might be some sort of wierd Gateway BIOS/Motherboard schism

.

> **lavinog said:**
> Are you familiar with bios?
If so see if you can find an option to disable High speed (or enhanced) USB support. Then see if the drives keep disconnecting.  If that fixes the problem then you are suffering from a compatibillity issue with the ehci_hcd module.  As of jaunty the module has been compiled into the kernel so the workarounds involving rmmod will no longer work: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/354832](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/354832)

Also I would check with gateway to see if there is an updated bios for your system.

agreed

.

---

### Post by cmcanulty on 2009-10-13
I finally think I have pinned down the problem with my hard drives unmounting and a solution page but I am not knowledgeable enough to know which fix to do on the link below and the exact procedure like with it mounted or not and does it need doing once or every time I use the ext drive. I would appreciate if someone could look at the link and tell me what I should actually put in terminal, many thanks.My drive is the maxtor One Touch 4 .My western digital spins down also and thereby unmounts itself.
[http://www.nslu2-linux.org/wiki/HowTo/SetSpinDownTimeOnMaxtorOneTouch](http://www.nslu2-linux.org/wiki/HowTo/SetSpinDownTimeOnMaxtorOneTouch)

Here is another Ubuntu fix but I am not sure which parts to enter in terminal and which to enter into the usb-hd-fix.rules doc

---

### Post by lavinog on 2009-10-13
> **cmcanulty said:**
> I finally think I have pinned down the problem with my hard drives unmounting and a solution page but I am not knowledgeable enough to know which fix to do on the link below and the exact procedure like with it mounted or not and does it need doing once or every time I use the ext drive. I would appreciate if someone could look at the link and tell me what I should actually put in terminal, many thanks.My drive is the maxtor One Touch 4 which is also the same apparently according to the web page.My western digital spins down also and thereby unmounts itself.
[http://www.nslu2-linux.org/wiki/FAQ/DealWithAutoSpinDownOnSeagateFreeAgent](http://www.nslu2-linux.org/wiki/FAQ/DealWithAutoSpinDownOnSeagateFreeAgent)

I doubt this is your problem.
The spindown is set to happen after 15 mins of inactivity.  Your issue is the the drive is disconnecting during activity.

---

### Post by cmcanulty on 2009-10-14
In my continuing failed attempts at getting my jaunty to recognize any storage devices  so I can backup I formatted a ext HD to half ntfs and half ext4 but I can't seem to mount the ext4 partition. Do I need to do something special to mount it?

---

### Post by LewRockwell on 2009-10-14
> **cmcanulty said:**
> In my continuing failed attempts at getting my jaunty to recognize any storage devices  so I can backup I formatted a ext HD to half ntfs and half ext4 but I can't seem to mount the ext4 partition. Do I need to do something special to mount it?[http://ubuntuforums.org/showthread.php?t=1133719](http://ubuntuforums.org/showthread.php?t=1133719)

.

---

### Post by LewRockwell on 2009-10-14
> **cmcanulty said:**
> In my continuing failed attempts at getting my jaunty to recognize any storage devices  so I can backup I formatted a ext HD to half ntfs and half ext4 but I can't seem to mount the ext4 partition. Do I need to do something special to mount it?

just for the sake of saying we did it...

what happens when you boot into the test-drive LiveCD mode of the Ubuntu disk?

are all your various external devices recognized?

.

---

### Post by cmcanulty on 2009-10-14
Yes I did that and they work OK I just reinstalled again hoping for a fix, and ext HDs already unmount. I wish I understood how to set up an auto mount in fstab I read the tutorial several times but is quite complicated.Oh it just unmounted again trying to put my docs back on laptop. And now I have ext HD formatted to ext4.  About one more week of this frustration and it will be back to XP no matter how much I want Linux

---

### Post by lavinog on 2009-10-14
If you are needing an ext file system for backups, I would use ext3 for reliability reasons.

---

### Post by lavinog on 2009-10-14
Have you tried Ubuntu 9.10?

---

### Post by LewRockwell on 2009-10-14
> **cmcanulty said:**
> Yes I did that and they work OK I just reinstalled again hoping for a fix, and ext HDs already unmount. I wish I understood how to set up an auto mount in fstab I read the tutorial several times but is quite complicated.Oh it just unmounted again trying to put my docs back on laptop. And now I have ext HD formatted to ext4.  About one more week of this frustration and it will be back to XP no matter how much I want Linux

we're still just dealing with one specific hardware set...correct?

you may find nirvana with different equipment

we know that isn't what you probably want to hear

and there really isn't a good reason why the LiveCD session works...but the install doesn't...

(except that the LiveCD does NOT have any of the updates or newer kernels)

after your last reinstall...did you do the updates?

.

---

### Post by steveneddy on 2009-10-15
> **cmcanulty said:**
> I am using 9.04. I think I'll have to go back to dual boot as this constant hassle and losing all my externals isn't worth it. I wish they would stop adding glitzy stuff to the distros and first make everything work with Linux. I was willing to spend weeks reading and tweaking to get my system up which most people wouldn't but still it defeated me.

My Opinion:

Reinstall using Intrepid 8.10 and see if you have the same experience.

8.10 is more stable than 9.04, and this may be where you are having issues.

Just try it, it will only take 20-30 minutes.

Sometimes the latest/greatest software isn't great for everyone.

---

### Post by steveneddy on 2009-10-15
> **lavinog said:**
> Have you tried Ubuntu 9.10?

Don't go to the cutting edge first, go back to stability first. You may find that stability is better than bleeding edge.

Just trust me on this one.

---

### Post by Pelsia on 2009-10-15
One of my Raptor drives either kicked the bucket, or has some filesystem errors that's keeping it from booting.  Went to WD's page to get the diagnostic tools and found this:

[http://support.wdc.com/product/downloaddetail.asp?swid=119&type=download&wdc_lang=en](http://support.wdc.com/product/downloaddetail.asp?swid=119&type=download&wdc_lang=en)

If you have a WD drive I believe its free (it'll detect if you're not using a WD drive and then not run).  I've used Acronis cloning products for 5 years and they've got me out of some major jams in the past dealing with uncooperative Raid arrays.  

Just boot from cd (make from the program once installed), and clone the internal hd to the external one (it works with almost all usb devices, only ran into 1 that it wouldn't recognize).  I use it as my backup program since it can restore everything to how it was when the image was created.  Restoring files from an image is pretty easy, or if you continue to have unmounting problems you can move them via the bootable disk.

Btw (sorry I admit I didn't read all 9 pages of this thread) have you checked your external drive for SMART errors?  I recently had a drive that while still working, was spitting out SMART errors all the time until the disk finally died.  While it would still work up till it failed, it was extremely slow and had a tendency to unmount itself if I tried to copy a large (single) data file to it.

---

### Post by steveneddy on 2009-10-21
I am curious if the OP ever got his issue resolved, and if so, how?

---

### Post by cmcanulty on 2009-10-22
I did not get it solved I have found out it is probably an automatic spin down feature of my hard drives that is a power save and in Linux causes the drive to unmount. I found some tweaks but am not sure how to do them I have to go to work but later will post fixes and maybe someone can help me do them, thanks

---

### Post by LewRockwell on 2009-10-22
how did Clonezilla work for you?

.

---

### Post by initiallyM on 2009-10-25
I am having the same problem as the original poster.

I'm thinking about starting a new thread with this question because this thread is so cluttered. But I'll try it here first. So let me see if I can clarify some things.

Although cmcanulty named the thread Backup Again and mentions his issues with backing things up, the problem has nothing to do with that. The problem is just indirectly affecting his ability to perform backups. The suggestions given about different backup programs and alternatives are not the help he needs.

Here is the problem as I am having it. I attach my external hard drive and it mounts. I can manage files on it and do all the regular things with it. Some time later, right after the hard drive spins down, it immediately and automatically unmounts itself. This automatic unmounting is the problem.

I just started having this problem today, after I upgraded to 9.10. Before the upgrade, with ubuntu 9.04, the external HD would never unmount itself. It would spin down after some time but it would stay mounted and the icon would stay on my desktop.

The problem seems related to something in the upgrade, some difference between 9.04 and 9.10. Any suggestions?

---

### Post by Sir Jasper on 2009-10-25
Hi initiallyM,

Edit your post and start a new thread. It is not a question of clutter (though that will not help) it is that your problem may be similar but not identical.

My regards

---

