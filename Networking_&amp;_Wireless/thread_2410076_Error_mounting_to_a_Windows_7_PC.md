---
title: "Error mounting to a Windows 7 PC"
date: 2019-01-10
forum: Networking &amp; Wireless
---

### Post by stormthirst on 2019-01-10
A couple of days ago, my Ubuntu PC stopped being able to map to a file share on my Windows 7 PC. I've Googled quite a bit, but none of the results seem to help.

If I use:

sudo mount.cifs //192.168.2.10/kodi temp/ -o user=<username>,pass=<password>

I get:

mount error(9): Bad file descriptor
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

What is a bad file descriptor, and why has this recently started happening? Windows 7 has recently had some updates, but none of them seem relevant to the problem at hand. I can SSH into my Ubuntu PC, and I can access the CIFS share I've got set up on the Ubuntu PC just fine. I don't think connectivity is a problem. I even disabled the firewall on the Windows PC, but that has not helped

Perhaps someone who has had this issue before enlighten me as to what I'm doing wrong?

---

### Post by gazzap on 2019-01-11
> **stormthirst said:**
> A couple of days ago, my Ubuntu PC stopped being able to map to a file share on my Windows 7 PC. I've Googled quite a bit, but none of the results seem to help.

If I use:

sudo mount.cifs //192.168.2.10/kodi temp/ -o user=<username>,pass=<password>

I get:

mount error(9): Bad file descriptor
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

What is a bad file descriptor, and why has this recently started happening? Windows 7 has recently had some updates, but none of them seem relevant to the problem at hand. I can SSH into my Ubuntu PC, and I can access the CIFS share I've got set up on the Ubuntu PC just fine. I don't think connectivity is a problem. I even disabled the firewall on the Windows PC, but that has not helped

Perhaps someone who has had this issue before enlighten me as to what I'm doing wrong?


REPLY: to Stormthirst  
I had the same issue sharing a couple of Win7Pro shared resources over my LAN to my mythBUNTU server.  Discovered that Microsoft introduced three updates the same day (AEST: 10/1/19) , and that night my backup process failed to MOUNT those shares on the mythBUNTU box.

The offending updates (not sure which one or more of these three) were:   KB4481480  KB4480970  and   KB890830
I uninstalled those three from the Win7 box, rebooted it,  and then my MOUNT commands on themythserver box worked OK.

root@mythserver-desktop:/etc# mount -t smbfs //absbetty.lan/LIVE_QBI_accounts_AUT /absdata/data/samba/business/accounts/ABS_as_AUT/ABS_live_mirror --verbose  -o user=<password>  -o password=<password> 

Hope this clue helps you too  - took me all day messing with IPv4 versus IPv6,  network security settingso on Win7 - you name it, till I smelt a rat in MS updates.

Cheers

Gary
(AUST)

---

### Post by gsid2 on 2019-01-11
I had the same issue as Gary after installing Windows 7 updates on Jan 9, 2019. Trying to mount a Windows share from Raspbian failed with "Bad file descriptor". After deinstalling KB4480970 it worked again.

---

