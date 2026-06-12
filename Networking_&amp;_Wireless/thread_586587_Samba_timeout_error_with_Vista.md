---
title: "Samba timeout error with Vista"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by dylanrjones on 2007-10-22
Hey everyone,

I'm having a problem copying files and directories via a samba network with my windows vista box. The files will start copying, but if it takes longer than a minute I get an "Error "Timeout reached" while copying "smb://...." and it refuses to let me retry I couldn't find anything in the forums similar to this. I have no issues copying files from an XP box on the same network, and small files that take less than a minute to copy on the vista network can complete normally.

I'm using gutsy and have not modified the default smb.conf and I couldn't find anything in it regarding timeout options. Let me know if you need more info, I'm still a bit new to the linux thing.

Thanks for the help
Dylan

---

### Post by muddoc on 2007-10-23
I haven't found a solution but I am having the same issue...

---

### Post by nordberg on 2007-10-24
Same issue here, using fusesmb on xubuntu gutsy, networking with Vista.  Small files transfer fine, larger files (over 5mb or so) cause timeout error after 20 seconds or so.  
Networking is flawless when sharing with WindowsXP instead of Vista.

---

### Post by starfry on 2007-10-24
I've experienced problems when copying very large files (i.e. recorded videos) from a windows machine to a samba share hosted on Linux. I haven't found a solution but I use rsync instead without problems.

---

### Post by Kynddelic on 2007-10-25
Same thing here. Small files are OK, large file copy end with a timeout that say "Erreur « Délai d'expiration atteint » lors de la copie de « /media/COR...ns fin.avi », meaning  "Error, timeout during the copy of xxx.avi."

The timeout can be from 10 sec to several minutes (file copied from 5MB to 200MB for an original file of 700MB).
My network is Wifi (WMP54GS, WRT54GS). I have no problem to copy from XP to Vista using this network.

Can't find why ....

---

### Post by dylanrjones on 2007-10-28
Has anyone tried the 4.0 alpha from the samba website yet? Would that be more compatible with vista?

---

### Post by kay.one on 2007-11-04
same problem here, any solutions yet?

---

### Post by kay.one on 2007-11-06
bump, please can someone even confirm that they dont have this problem. is this a bug or are we doing something worng!

---

### Post by WanderingStar on 2007-11-06
I am also affected by this.  Connecting to 2 different Vista computers has the same effect.  

Also using wireless, so not sure if that is the issue.

---

### Post by dylanrjones on 2007-11-06
Yeah, wireless here too.

---

### Post by kay.one on 2007-11-09
i reported this as a bug in launchpad [https://bugs.launchpad.net/ubuntu/+bug/161118](https://bugs.launchpad.net/ubuntu/+bug/161118)

if you experience this problem please add a comment to the bug report confiriming the bug, and add any information you think might be helpful.

---

### Post by edwardTheGreat on 2007-11-09
I had a similar problem using a wireless connection and found that it went away after IPV6 was disabled.

So I disabled IPV6 on my Ubuntu box and now it works at normal speeds.

Try that and let us know how it goes...

---

### Post by kay.one on 2007-11-09
> **edwardTheGreat said:**
> I had a similar problem using a wireless connection and found that it went away after IPV6 was disabled.

So I disabled IPV6 on my Ubuntu box and now it works at normal speeds.

Try that and let us know how it goes...


I just tried disabling the IPV6 using the method below, but no help, it did not effect the speed which is 1.5 MB/s comparing to 2.2 MB/s  in windows and it still timedout the connection.

---

### Post by edwardTheGreat on 2007-11-09
cool no prob, sorry it was no help.

---

### Post by kay.one on 2007-11-09
> **edwardTheGreat said:**
> cool no prob, sorry it was no help.

hey no problem, thanks for the suggestion, it was definitely worth the try.

---

### Post by WanderingStar on 2007-11-10
Also nogo on IPv6. Manually mounting the shares with smbfs and attempting a copy results in the following errors over and over again in the syslog:

Nov 10 07:23:42 ubuntu6400 kernel: [  427.336000] smb_fill_super: missing data argument
Nov 10 07:27:24 ubuntu6400 kernel: [  649.296000] smb_add_request: request [f0baa0c0, mid=746] timed out!
Nov 10 07:27:55 ubuntu6400 kernel: [  679.864000] smb_add_request: request [f0baa0c0, mid=881] timed out!
Nov 10 07:28:25 ubuntu6400 kernel: [  710.124000] smb_add_request: request [f0baa0c0, mid=945] timed out!
Nov 10 07:28:56 ubuntu6400 kernel: [  741.320000] smb_add_request: request [f0baa0c0, mid=1193] timed out!
Nov 10 07:29:27 ubuntu6400 kernel: [  771.856000] smb_add_request: request [f0baa0c0, mid=1278] timed out!
Nov 10 07:29:57 ubuntu6400 kernel: [  802.296000] smb_add_request: request [f0baa0c0, mid=1355] timed out!

CIFS results in the operation locking up with:

Nov 10 07:40:12 ubuntu6400 kernel: [ 1417.160000]  CIFS VFS: server not responding
Nov 10 07:40:12 ubuntu6400 kernel: [ 1417.160000]  CIFS VFS: No response to cmd 46 mid 189
Nov 10 07:40:12 ubuntu6400 kernel: [ 1417.160000]  CIFS VFS: Send error in read 

I will also comment on the bug.

---

### Post by kay.one on 2007-11-11
anybody know how does the bug fixing procedure for Ubuntu is, should we have any hope on this bug being addressed? or will it be blamed on vista and go unheard?

---

### Post by Peter09 on 2007-11-12
I was getting a similar error, I used cifs and it worked, this was in Fiesty. I mount my permanent shares in FSTAB - looks like this:-

//192.168.0.8/nas1share		/mnt/nas1/nas1share	cifs	rw,defaults,errors=remount-rw

I have not bothered to change since Gutsy so do not know if the problem is the same.

---

### Post by jsmithy on 2007-11-14
Hello :)

It also happens on Dapper while trying to copy to a Windows XP Pro x64 share.  I think it is not just the OS share.

I Google it a bit and found a solution that worked for me.

I checked the net interfaces for the MTU.  Dapper was set to 1500 on the interface that connects to the Windows share.  Next I checked the Windows interface and found it to be on its default.  I explicitly set the MTU to 1500 on the Windows machine and rebooted.  By the way, it turns out that after making some tests 1500 is the proper MTU for my Internet connected interfaces too.

I tried the same copy process I had made before and it worked without any problems.

I hope this helps.

Peace to all  :)

---

### Post by dylanrjones on 2007-11-14
Ok, great. Thanks for the tip. Um, for those of us less smart than you, any idea how to change this in vista?

---

### Post by dylanrjones on 2007-11-14
Ok, tried it out. 

Used this in the command line to show my current settings in vista:

netsh interface ipv4 show subinterfaces

It told me my MTU was already at 1500, so no help there. Keep trying everyone.

P.S. If you try the above command and your MTU isn't 1500 you can change it using:

netsh interface ipv4 set subinterface "Local Area Connection" mtu=1500 store=persistent

Try this at your own risk, it's just from a forum post and I haven't tried it.

---

### Post by kay.one on 2007-11-14
> **jsmithy said:**
> Hello :)

It also happens on Dapper while trying to copy to a Windows XP Pro x64 share.  I think it is not just the OS share.

I Google it a bit and found a solution that worked for me.

I checked the net interfaces for the MTU.  Dapper was set to 1500 on the interface that connects to the Windows share.  Next I checked the Windows interface and found it to be on its default.  I explicitly set the MTU to 1500 on the Windows machine and rebooted.  By the way, it turns out that after making some tests 1500 is the proper MTU for my Internet connected interfaces too.

I tried the same copy process I had made before and it worked without any problems.

I hope this helps.

Peace to all  :)

i just checked my vista installation and the MTU on my Ethernet card is 1500.

you can check yours by typing this in the command prompt
```
netsh interface ipv4 show subinterfaces
```

---

### Post by edwardTheGreat on 2007-11-15
I said in an earlier post that I disabled ipV6 and that it picked the speed up. 

But I was accessing a Samba share last night on my Ubuntu PC from my Vista Laptop, and noticed that it was slow (100K/s ish). The Samba Share is an NTFS filesystem mounted using ntfs-3g. 

But when I accessed a different Samba Share from a ext3 filesystem it was a lot faster (800-900K/s)... 

Copying roughly the same sized files (about 350 Mb), but on the other hand it could've been my wireless connection for some reason playing up...

This is speculation at the moment. I'll do some speed checks over the weekend to see if there is any correlation between ntfs-3g samba shares and slow network speeds...

Has anyone else noticed that samba shares from ntfs-3g file systems are slower than samba shares from ext3 file systems?

---

### Post by jsmithy on 2007-11-15
Hello, :)

It is not to set MTU at 1500 but finding out what is your optimum MTU and checking that both of the machines have the same MTU at the interfaces using to communicate them.

Did you check the Ubuntu box?

I hope this helps.

Peace to all :)

---

### Post by kay.one on 2007-11-15
> **jsmithy said:**
> Hello, :)

It is not to set MTU at 1500 but finding out what is your optimum MTU and checking that both of the machines have the same MTU at the interfaces using to communicate them.

Did you check the Ubuntu box?

I hope this helps.

Peace to all :)

how do you check the MTU in ubuntu?

---

### Post by jsmithy on 2007-11-17
> **kay.one said:**
> how do you check the MTU in ubuntu?

Using ifconfig

But I have bad news.

Today I tried the same copy operation and it is behaving like before.  So, I can conclude is not fixed.

It helps, because packets will not be fragmented during the copy operation if you choose the proper MTU for your particular setup.  But is not the fix.

I set up the samba server in the Ubuntu box and shared a directory on this box.  I can copy from the Windows box to the Ubuntu box and from the Ubuntu box to the Windows box if I am located at the Windows box.

This suggests that the problem lays in the relation between Nautilus and samba. But I do not have enough knowledge to determine if is samba or is Nautilus who is broke.

Today I received an update to samba over the web, but it did not fixed it.  This could indicate that is Nautilus that is causing the problem.

I am going to check if there is another file manager I can use to make the copy.  One that works by using samba. This could be an interesting test.

I will share the results with you guys.

Btw, theres a lot of people looking for a fix for this situation on the web.  Lots of posts in different forums.

There's even a bug report filed with the samba group.

Take  look at this thread:

[http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

...some interesting samba guide in there. The problem with Nautilus is well documented.

Peace to all :)

---

### Post by WanderingStar on 2007-11-18
I don't think the problem is with Nautilus, as I'm having the same issues using smbmount - taking Nautilus out of the equation completely.

---

### Post by kay.one on 2007-11-18
> **WanderingStar said:**
> I don't think the problem is with Nautilus, as I'm having the same issues using smbmount - taking Nautilus out of the equation completely.

anybody tried to see if the same thing happens with kubuntu? i downloaded a live cd and will give it try as soon as i have time to burn it.

---

### Post by NiteShdw on 2007-11-19
I am having the same problem copying files via smb:// links from Vista machines.

I followed the instructions [in this thread](http://ubuntuforums.org/showthread.php?t=288534) to mount the shared folder as cifs.  That allowed me to copy files without a problem.

---

### Post by kay.one on 2007-11-19
> **kay.one said:**
> anybody tried to see if the same thing happens with kubuntu? i downloaded a live CD and will give it try as soon as i have time to burn it.

I downloaded the kubuntu but couldn't get the network working so i couldn't test it out, can someone please test this out with kubuntu so we know if the problem is with GNOME or something underneath it in Ubuntu.

---

### Post by kay.one on 2007-12-26
any update? anyone who doesn't have a problem with vista and ubuntu?

---

### Post by PeterTL on 2008-01-13
Anyone noticed this from MS:

[http://support.microsoft.com/kb/938475](http://support.microsoft.com/kb/938475)

I have not tried out this patch, and my VISTA is running with the latest patches, so it is apparently not generally distributed yet. But it sounds exactly like something that could explain this weird behavior.

---

### Post by kay.one on 2008-01-13
> **PeterTL said:**
> Anyone noticed this from MS:

[http://support.microsoft.com/kb/938475](http://support.microsoft.com/kb/938475)

I have not tried out this patch, and my VISTA is running with the latest patches, so it is apparently not generally distributed yet. But it sounds exactly like something that could explain this weird behavior.

for not i have given up on ubuntu (Linux in general) for two different reason, I'm gonna try back after vista SP1 to see if this problem is solved, and the other problem is my ATI video card, full screen video looks like **** with current drivers, so hopefully a better driver will be available by the time SP1 is release.

---

### Post by dent_a on 2008-01-14
I think park of the problem lies with Nautilus not mounting the share/folder as CIFS.  I don't know where to summit the error so if anyone does let me know or summit it for me.

---

### Post by Vuen on 2008-02-29
Guys, nautilus is *NOT* the problem. As a dozen people have mentioned already, the problem happens when mounting shares directly, and you can all stop burning Kubuntu cds because I have Kubuntu and am experiencing the same problem using Dolphin.

---

### Post by fadhater on 2008-03-01
I was having the same timeout error till I found this fix

"I had the same issue

Came across this under the control Panel

Go to the Control Panel
Open Programs and Features
Click on " Turn windows features on or off" on the left side of the panel
Uncheck "Remote Differential Compression"

Fixed up the problem for me"

So the problem is on the windows side.
Just disabling RDC fixed it for me.

---

### Post by swerdna on 2008-03-01
Samba only spoke nicely with vista after the release of this version of Samba: 3.0.25b-1.1.72 (approx, near this version)
So check your versions and if necessary, upgrade.

Swerdna

---

### Post by midlifecrisis on 2008-03-12
I'm getting this error between my unbuntu laptop and nslu2 unslung share's when I try to copy large files via wireless. I've also been unable to mount a upnp share with djmount via wireless.

I've disabled ipv6 but it's not sorted out my prob's.

I'm using an old viao pIII with a new ralink pcmcia card. It's works ok for web and downloads but as soon as I try to pull a file from a smb it times out.

---

### Post by midlifecrisis on 2008-03-15
I've been looking into this a bit more and I don't think the problem is down to samba. I've connected to my nslu2 via ssh and when trying to copy a large file it gets about 400 mb though and then drops the connection.

The problem seems to be down to the wireless network connection.

Any advice on either tracking down the poblem or gathering more info about it would be great, Please bear in mind I'm a noob so go easy on me.

---

### Post by midlifecrisis on 2008-03-15
On my other l (dell d620) I'm running vista and have set up ubuntu under vmware and I can transfer large files via wifi. I'm not sure what this tells us, but as far as I can see it's not the remote shares issue

---

### Post by funnypanks on 2008-03-24
apparently the problem is gone in vista sp1

---

### Post by maniaq on 2008-05-09
Hi I'm having the same problem sharing between a Hardy desktop and a Hardy laptop using samba. I also have another machine running samba (Vector linux not Ubuntu) and it works just fine...

Seems to me the problem is with the smbd?

---

### Post by Warmask on 2008-05-15
Same problems here, laptop is Gutsy on wireless, connecting to Vista with shared folders

---

### Post by deadalus.ai on 2008-05-18
Hi. I'm experiencing the same problem on my Hardy laptop (an Asus eee) to my Vista desktop via wireless. Copying any file larger than about 6 megs times out.

Sharing the same file via my desktop XP boot or Hardy boot (same machine, on Wubi) presents no problems whatsoever.

The problem for me then is probably Vista.

Can anyone confirm if Vista SP1 does fix this problem? (I've almost reached the end of my monthly cap and cannot download it right now..)

---

### Post by deadalus.ai on 2008-06-14
Installing Vista SP1 does solve the problem.

---

### Post by Nigel74 on 2008-07-13
> **deadalus.ai said:**
> Installing Vista SP1 does solve the problem.

I am having this problem after installing Vista SP 1. It worked before I installed it.

I have even tried turning off the firewall (Bullguard), but that made no difference. When the firewall is on, ping requests are logged, but the connection attempt is not even logged.

---

