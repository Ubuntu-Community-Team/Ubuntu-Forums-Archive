---
title: "root access permission denied on SMB share"
date: 2022-06-08
forum: Networking &amp; Wireless
---

### Post by mickeyluv on 2022-06-08
I have a BT Smarthub 2 router with a SSD drive plugged into the USB port. The protocol used is SMB1, which cannot be changed. I'm accessing the drive using an SMB share in Nautilus on Ubuntu 20.04.4 LTS. I've encountered an issue where as root user I get Permission Denied when attempting chmod or chown on any files/folders. If I plug the drive in to my laptop there's no problem. There's also no problem with the share if I move a file locally, change permissions and move it back. In smb.conf  client min protocol = NT1, server min protocol = NT1.

What is the mechanism that prevents root access to the SMB share?

---

### Post by TheFu on 2022-06-08
> **mickeyluv said:**
> I have a BT Smarthub 2 router with a SSD drive plugged into the USB port. The protocol used is SMB1, which cannot be changed. I'm accessing the drive using an SMB share in Nautilus on Ubuntu 20.04.4 LTS. I've encountered an issue where as root user I get Permission Denied when attempting chmod or chown on any files/folders. If I plug the drive in to my laptop there's no problem. There's also no problem with the share if I move a file locally, change permissions and move it back. In smb.conf  client min protocol = NT1, server min protocol = NT1.

What is the mechanism that prevents root access to the SMB share?

SMB doesn't know anything about root or Unix permissions.  Typically, the root account (or sudo accounts running with elevated privileges) have that account converted to 'nobody' as a security feature.

SMB doesn't support chmod or chown.  The user account and group accounts are set by the share configuration.  NTFS, exFAT, FAT32 don't support chmod or chown either.

Sorta off-topic, but it is extremely common for routers that have USB storage features to be hacked.  Probably not a good idea.  Don't use sudo with GUI tools. That's a general recommendation. There are plenty of bad repercussions that we've seen over the years when people do it.

If you want chown and chmod to work, use Unix/Linus file systems and either local or NFS storage mounts.

---

### Post by mickeyluv on 2022-06-09
Ah, thanks for that. I take your point about the attached storage and today I'm moving the drive off the router. Is there any way to tell from stats if the drive has already been compromised? I'm pretty annoyed that a router that was new just 15 months ago has such a security flaw and uses SMB1.

---

### Post by Morbius1 on 2022-06-09
I don't understand the question.

Are you connecting to the SMB share from Nautilus?

Are your trying to do something like this:
> /run/user/1000/gvfs/smb-share:server=192.168.1.145,share=public/Documents$ sudo chmod 0777 "Untitled Document"
chmod: cannot access 'Untitled Document': Permission denied
Yep, root cannot in fact do that.

You can't do that as the user that connected to the server either:
> /run/user/1000/gvfs/smb-share:server=192.168.1.145,share=public/Documents$ chmod 0777 "Untitled Document"
chmod: changing permissions of 'Untitled Document': Operation not supported

Imagine the chaos that would ensue if a samba / smb client to a samba server could alter file permissions - on the server itself. This is verboten.

The server is in charge of what permissions are allowed / created on the server. 

The client is free to create a "view" of the share with any permissions he wants - relative to that client system - however.

For example if I did a cifs mount of the share above:

```
sudo mount -t cifs //192.168.1.145/Public /home/tester/SrvPub -o guest,uid=tester,gid=plugdev,dir_mode=0775,file_mode=0664,vers=1.0
```

To the client any new file added will have owner=tester, group=plugdev, and permissions of 664.

To the server the very same file will save with whatever ownership and permissions are defined on that server for - in this case a guest user - for that share.

---

### Post by TheFu on 2022-06-09
> **mickeyluv said:**
> Ah, thanks for that. I take your point about the attached storage and today I'm moving the drive off the router. Is there any way to tell from stats if the drive has already been compromised? I'm pretty annoyed that a router that was new just 15 months ago has such a security flaw and uses SMB1.

I didn't say that YOUR router has a security issue, just that it is extremely common.  There are always bugs in all software.  That's why using well-supported devices is so very important.  Over the years, router software that allows storage sharing commonly has multiple issues. After fixing 1 issue, there's is often another one found.  And another.  And another.

For me, the risks of having that storage shared with the world is too great to risk.  OTOH, if you do file sharing using a computer or even with other devices inside your LAN, just not on the WAN router, that usually mitigates most risks.

Security is often about risk management, since all software has bugs and we don't know all the bugs in any software at any point in time.

I don't know your specific router to know if logs are retained that can be checked for unwanted access. Sorry.  When choosing a router, don't look for a long list of features that have nothing to do with "routing".  A WAN router should do 2 things.  Routing and firewalling.  Those are complex enough to get right that other features like printer support or file sharing or complex DNS or any of 150 other things people put on their home routers are probably just a bad idea.  More features enabled == more software being used == more bugs in the software with critical flaws.

---

### Post by mickeyluv on 2022-06-09
The share is connected in Nautilus through other locations>connect to server. Then right-click on a folder and open in terminal. Log in as root (or use sudo) and then try to change permissions etc. I now understand better the relationship between the drive and my machine. I was incorrectly thinking that as root I would have full control over 'my' network, wherever the drive is located.

There's a level of discontent over the security of this particular router regarding the USB port. It came as a package from my ISP, so perhaps is very basic. Users were expecting security/protocol updates which have never happened. I've now shifted the drive to my Raspberry Pi for better protection. It would have been nice to have left it connected to the router - it's more convenient, but seems that this is unlikely.

---

### Post by TheFu on 2022-06-09
ISPs have 1 primary goal with the CPE.  It needs to work so support complaints and phone calls are minimized.  Patching is often an afterthought, if even done.  I worked on a large ISP project to patch our 45M customers CPE.  We'd push out firmware updates every 3-6 months. This didn't start until at least a year after the different CPE devices were already widely used.  Fear of front-page newspaper articles was the primary driver for upper management to take any steps. That scenario was actually discussed in meetings.  

Smaller, regional ISPs would have less concern about nationwide news coverage, I suppose.

With your R-pi, being a storage server is less ideal, since those devices aren't exactly built for network or disk performance.  I have a few and while they can be used for a NAS, I've never bothered after looking at the specs.  Perhaps a r-pi v4 has better performance where the networking and USB3 bus speeds won't be shared, so GigE is possible?  I don't have any pi v4 devices. Before I was ready to buy, they had usb-c power plug issues and by the time that was fixed, the supply chain for all computing devices dried up.  IMHO, they are about 2x the correct cost.  There are other options for low-end computers with great networking and SATA/USB3 support.  PCEngines makes some devices. I think they use 10-12 Watts, which is about what a r-pi would use.  My WAN router is a PCEngines purpose-built x86-64 router (no wifi).

Years ago, I used a $50 WD-TV Live HD as a NAS device.  It had only 100Mbps LAN connection and USB2 storage support, provided the external drive was wall-powered.  These days I have a Ryzen 5xxx that is a NAS (it was a Pentium G3258 until last fall). The Ryzen does lots and lots of other things.  For a pure NAS that can stream some videos, books, music, the prior Pentium was a great platform, provided the video didn't need any transcoding.  Had about 40TB connected to it.  Also ran a few VMs on it.  Not bad for a 65W computer. That Pentium system cost $126 for the MB+CPU+RAM, which was all I needed.  Reused a case, fans, storage, etc. The Pentium iGPU was perfect too. Took 6 yrs before I needed more capability.  Initially, the Pentium had a single 4TB HDD which would be more than enough for any family that didn't do video hoarding.  Always buy 2 HDDs, 1 for primary and 1 for backups.  I've replaced that 4TB main drive 3 times due to failures. Beware. Get backup religion BEFORE you need it.

There are lots of options for having a low-powered NAS on your network.  You could setup a cheap router in bridge mode that has storage sharing features, just put it inside your LAN, not part of your WAN security.  Some of those routers have DLNA servers in addition to SMB sharing.  Disable the wifi on it, since a cheap router probably isn't being patched anymore.  By placing the storage on a router (in bridge mode) inside your LAN and not using any wifi on it, you've likely mitigated the access methods that could be abused on a WAN router.  Just be certain not to sign up for any cloudy-account with that LAN storage device.  

Lots of options at lots of different cost points.

SMB1 really needs to die on your home network, BTW.  Win7 supports SMB2.1, so that's really the oldest SMB protocol that should be used anywhere. The security differences in later SMB versions are tremendous. Plus, performance is always improving.  Who wouldn't want more performance AND better security?

---

### Post by mickeyluv on 2022-06-09
I'm wondering if using OpenWRT would give me some options to connect an SSD to my LAN - I have a spare router that's a favourite in the UK (BT Home Hub 5) for OpenWRT. Performance isn't a huge issue - it's used mainly as a backup drive or to share a few files between machines. I currently have a R-pi v4 (4gb) which does a decent job over Ethernet using USB3 with the SSD, but this is usually turned off unless I'm watching TV, so reconfiguring the spare router as a poor-man's NAS would be better. It also uses half the power of the R-pi.

---

