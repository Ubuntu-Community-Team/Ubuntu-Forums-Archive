---
title: "NFS Mounting, what am I dong wrong"
date: 2018-01-09
forum: Networking &amp; Wireless
---

### Post by frappe792 on 2018-01-09
Hi all,

Trying to setup some network drives like I used to do on windows. I look back and can't believe how easy it was in comparison.
I never had trouble with it on windows nor on my android devices. I am using a QNAP NAS with 5 or 6 parent folders with variouis permission etc. For the purpose below I am trying to map with admin which has no restrictions in the QNAP.

I was easily able to mount the public folder by 

[SIZE=2][COLOR=#0000FF][FONT=arial]sudo mkdir ~/mnt/QNAP/Public[/FONT][/COLOR][FONT=arial]  [/FONT][COLOR=#000000][FONT=arial](I then checked to see it made the directory)[/FONT][/COLOR]
[COLOR=#0000FF][FONT=arial]sudo mount -t nfs -O username=admin,password=123456 192.168.0.111:/Public  /mnt/qnap/public[/FONT][/COLOR][COLOR=#000000][FONT=arial]

No problem, works well.

but let's say I wanted to map my 'multimedia' directory, I did

[/FONT][/COLOR][COLOR=#0000FF][FONT=arial]sudo mkdir ~/mnt/QNAP/Multimedia[/FONT][/COLOR][COLOR=#000000][FONT=arial] (I then checked to see it made the directory)
[/FONT][/COLOR][COLOR=#0000FF][FONT=arial]sudo mount -t nfs -O username=admin,password=123456 192.168.0.111:/Multimedia  /mnt/qnap/multimedia[/FONT][/COLOR][COLOR=#000000][FONT=arial]

[/FONT][/COLOR][COLOR=#000000][FONT=arial]However this returns an error

[/FONT][/COLOR][COLOR=#0000FF][FONT=arial]mount.nfs: access denied by server while mounting 192.168.0.111:/Multimedia[/FONT][/COLOR][FONT=arial][COLOR=#000000][/COLOR][/FONT]

[FONT=arial]I have tried with 2-3 others folders, that I have successfully mapped on other devices, but no luck in Ubuntu. I doubled checked all settings when I log into QNAP and everything is enabled for NFS.
[/FONT]
[FONT=arial]Would appreciated any help I can get, thanks![/FONT][/SIZE]

---

### Post by wyliecoyoteuk on 2018-01-09
Unlike Windows, File names in Linux are case sensitive: Multimedia is not the same as multimedia

---

### Post by frappe792 on 2018-01-09
> **wyliecoyoteuk said:**
> Unlike Windows, File names in Linux are case sensitive: Multimedia is not the same as multimedia

Thanks, but that wasn't it. Still gives error - [FONT=monospace][COLOR=#000000]mount.nfs: access denied by server while mounting [/COLOR]
[/FONT]
I did [COLOR=#0000FF][FONT=arial]sudo mount -t nfs -O username=admin,password=123456 192.168.0.111:/Multimedia /mnt/qnap/Multimedia

[/FONT][/COLOR]ON my QNAP it is Multimedia. Also the folder I created is also [COLOR=#0000FF][FONT=arial]/mnt/qnap/Multimedia
[/FONT][/COLOR][FONT=arial]
Credentials I used are absolutely correct and taking into account case sensitivity.
[/FONT][COLOR=#0000FF][FONT=arial][/FONT][/COLOR]

---

### Post by papibe on 2018-01-10
Hi frappe792.

Could you run these commands and paste back the results?
```
showmount -a

showmount -e  192.168.0.111
```
Also, please double check your mounting directories since from post #1, it looks you created folders on your user's home (~), but then mount the remote directories under root (/).

Regards.

---

### Post by frappe792 on 2018-01-11
> **papibe said:**
> Hi frappe792.

Could you run these commands and paste back the results?
```
showmount -a

showmount -e  192.168.0.111
```
Also, please double check your mounting directories since from post #1, it looks you created folders on your user's home (~), but then mount the remote directories under root (/).

Regards.

Thanks for that,

First command results in 
[FONT=monospace][COLOR=#000000]All mount points on King-PORTEGE-R835[/COLOR]
[/FONT]
With the second command, I'd prefer not to paste back the results as it contains some sensitive info I don't want broadcasted.

Basically it will correctly list all the folders in my QNAP

---

### Post by papibe on 2018-01-12
Thanks.

Did you spot an misspelled error?

That message is very common with spelling problems. For example, in my LAN:
```
$ showmount -e vaughan
Export list for vaughan:
/home/data/alemedia              192.168.2.0/24

$ sudo mount vaughan:/home/data/**[COLOR="#FF0000"]a[/COLOR]**lemedia ./tmp
[sudo] password for user: 

$ ls tmp/
things/   more_things/   file1   file2

$ sudo umount tmp

$ sudo mount vaughan:/home/data/**[COLOR="#FF0000"]A[/COLOR]**lemedia ./tmp
mount.nfs: access denied by server while mounting vaughan:/home/pablo/**[COLOR="#FF0000"]A[/COLOR]**lemedia

```

---

### Post by frappe792 on 2018-01-12
Hi Papibe,

Appreciate your efforts, however still having trouble with it.

I definitely do not have case sensitivity issue - if I deliberately replace a lower case letter to uppercase - it says that it doesn't not exist.
I have made sure the it is not case sensitive anywhere and I still get the error [COLOR=#0000ff] mount.nfs: access denied by server while mounting 

[/COLOR]
You also made comment
[COLOR=#000000][FONT=monospace][COLOR=#000000]
"[/COLOR][/FONT][/COLOR][COLOR=#000000]Also, please double check your mounting directories since from post #1, it looks you created folders on your user's home (~), but then mount the remote directories under root (/).[/COLOR][COLOR=#000000]."[/COLOR]

I have tried with both these directories setup ( not sure which one is correct)

/home/king/mnt/qnap/Multimedia/
/mnt/qnap/Multimedia/[COLOR=#000000][FONT=monospace][COLOR=#000000]

[/COLOR][/FONT][/COLOR]

---

### Post by frappe792 on 2018-01-16
Bump

---

### Post by joebeasley on 2018-01-18
Sounds like nfs permissions are not set. [https://www.qnap.com/en/how-to/tutorial/article/advanced-folder-permission](https://www.qnap.com/en/how-to/tutorial/article/advanced-folder-permission)

---

### Post by frappe792 on 2018-01-19
> **joebeasley said:**
> Sounds like nfs permissions are not set. [https://www.qnap.com/en/how-to/tutorial/article/advanced-folder-permission](https://www.qnap.com/en/how-to/tutorial/article/advanced-folder-permission)

Not sure what you mean entirely, but permissions are set in the QNAP. I am able to access QNAP from various windows and android devices around the house with the correct usernames and password.

The issue I am having is _only_ in Linux.

---

### Post by frappe792 on 2018-01-23
Bump

---

### Post by frappe792 on 2018-01-29
Bump

---

### Post by frappe792 on 2018-02-01
post deleted as it is incorrect.
[LIST]
[/LIST]

---

### Post by frappe792 on 2018-03-10
An update for all - the last post I made was not the fix.

I finally worked out the fix.My password for the network share had a $ sign and doing the sudo mount command in the terminal failed with the $ sign worked without it.
Funny that, because my android and windows devices never had an issue with it. I will just have to remember to simplify all my passwords now that I am using linux. Surprising.

---

### Post by wyliecoyoteuk on 2018-03-11
That is because in Linux $ is a reserved character.
Windows and android have different ones. Possibly putting qoutes around the password would have worked

---

### Post by frappe792 on 2018-03-11
> **wyliecoyoteuk said:**
> That is because in Linux $ is a reserved character.
Windows and android have different ones. Possibly putting qoutes around the password would have worked

Thanks - Well that is still a surprise for a newbie.

I am now trying to figure out how to map it permanently, it seems after a reboot the shortcuts I have created to my QNAP folders are dead links.
Something that normally takes me 1 min to do in windows or on my android tablet is taking me hours in linux, it's stressing me out big time.

I have followed instructions from 3 or 4 different sources on how to automount without any luck. 

FYI I can succsefully mount manually via the terminal using the following command

```
[FONT=monospace][COLOR=#000000]sudo mount -t cifs -o username=admin,password=123456 //192.168.0.111/Multimedia /etc/nfs/multimedia[/COLOR]
[/FONT]
```

---

### Post by frappe792 on 2018-03-12
I take it all back, all of it. The above statement only mounted the silly useless samba share and not nfs. 

Anyway I have read through 100 websites and followed so many tutorials. I can "mount" my shared folders, but then they appear empty.

I am not going abslutely nuts here, I have just spend most of my long weekend for the something that I could do in windows in 1 minute. I can do it in android in 1 min. In a Mac in 1 minute. Why can't it take a minute in Linux? If anyone says it can, then please help me. 
I know I am not alone because there are thousands of posts online echoeing the same frustration that I am encountering. It's the little things like this that always get me thinking about going back to windows which I don't want to do because I enjoy the rest of it. But this is a deal breaker.

I have been on and off at it for a couple of months. When I migrated to linux from windows I read the spill that there is a ton of useful support out there, but where?

My QNAP address is 192.168.0.222
I have a shared folder call kkdocs
I have created a directory /home/kk/nfs/kkdocs
This folder is restricted to only 1 user with a password (which works perfectly with any other OS as it asks me when mapping and remembers credentials!)
NFS shares activated, turn on in the QNAP settings (Otherwise it wouldn't work from other Operating Systems right?)


What is the magic formula?

---

### Post by frappe792 on 2018-03-18
anyone?

---

### Post by frappe792 on 2018-04-14
Bump

Is it really that impossible to "map a network drive" ie mount an NFS share automatically in Linux?
Something so basic and quick to setup in other operating systems.

Why on earth would anyone use the slow and annoying SMB?

---

### Post by wyliecoyoteuk on 2018-04-15
Sorry, I dont use NFS. I use SMB rarely, just for windows.
I actually have a nextcloud server.
I vaguely remember that .NFS links are treated like local drives, i.e. They need to mounted and unmounted safely, not just disconnected.

---

### Post by frappe792 on 2018-04-15
> **wyliecoyoteuk said:**
> 
I vaguely remember that .NFS links are treated like local drives, i.e. They need to mounted and unmounted safely, not just disconnected.

So NFS which is native to Unix file system is sensitive and needs to be mounted and unmounted safely but when using NFS via windows where samba is native you can be rough with it? 

I mapped my server folders to my work windows 7 pc. Took 20 seconds to do it. Did it over 2 years ago. Never EVER have I had to remap or run into server unavailable.

For what I am trying to achieve, Linux is just Garbage.

---

### Post by wyliecoyoteuk on 2018-04-15
I think that is because what you are trying to do is not what NFS is meant for.
NFS is a true network filesystem, not a file sharing protocol.
Which means that it functions like local storage.
It is nothing like SMB.

---

### Post by frappe792 on 2018-04-18
I am just trying to get it working like it does on my windows pc work computer. Apparently this is impossible in Linux.

Decisions decisions. To stick with the slow SMB in Linux or move back to windows? A deal breaker when continually working on and off the serve with very large files.

---

### Post by wyliecoyoteuk on 2018-04-18
Apparently, Windows NFS mounts are soft mounts by default, whereas in Linux, the default is a hard mount.
There are disadvantages to both.
This discussion might be of interest:

[https://www.centos.org/forums/viewtopic.php?t=8787](https://www.centos.org/forums/viewtopic.php?t=8787)

The reason SMB is slower is because it involves a caching overhead.

---

### Post by frappe792 on 2018-04-19
Thanks I read that.
I cant find the way to do a soft mount in linux?

---

### Post by frappe792 on 2018-04-21
Is it time to ditch Linux?

---

### Post by QIII on 2018-04-21
Might be.  That's entirely up to you.

---

### Post by frappe792 on 2018-04-21
Done.

All other devices in the house whether they are a mac, windows or android easily connect to my QNAP. It's fast, reliable and exactly how it should be. All take 30 seconds to map. With Linux that is impossible and ridiculously wants to download a copy first. Yeah right! I consistently deal with large files and I am truly out of patience. 

Look at the original posting of this thread, I have given it a good go. I have been fairly patient and at it not for hours, day or weeks, but months. They said "try linux", there's plenty of help out there. But not one person can assist with this. 

Tell me good riddance, but the fact is the "experts" don't know the answer or it would have been offered. So I think the Linux community thing is just a myth. Thousands of web-pages all to no solution.....

Like I said, in other OS it just works and instantly. While some things are great with Linux and better in some ways than other OS's, it just doesn't work for me. 

):P

---

### Post by wildmanne39 on 2018-04-21
Glad you have it working by whatever means, it is always best to use what works for your needs! We are not experts we are normal users that share our knowledge voluntarily.

---

### Post by wyliecoyoteuk on 2018-04-22
Not hard to find:
[https://www.ibm.com/support/knowledgecenter/SSGSG7_7.1.2/com.ibm.itsm.client.doc/c_bac_nfshsmounts.html](https://www.ibm.com/support/knowledgecenter/SSGSG7_7.1.2/com.ibm.itsm.client.doc/c_bac_nfshsmounts.html)

if you are prepared to put up with silent data loss, carry on using NFS with soft mounts..
NFS was developed by Sun for constantly connected workstations as a distributed filesystem. 
A different scenario to SMB. which is designed for file sharing between unreliable (at the time it was written, very unreliable!) windows systems. Hence the additional overhead of file caching and oplocks etc.
Personally, I rarely use either on Linux.

---

### Post by frappe792 on 2018-04-22
Amongst all the crap over the internet, yes the right information can be hard to find but it's a little late for that. That's why we turn to forums.

Anyway, in the last 2 hours, I have setup windows 10 pro. Sure it's not linux, but at least I was able to map my 6 NFS drives in under a couple of minutes. Now I can get to work.

Haven't used windows for a while and certainly not windows 10. My early observation is that it is a cross of windows 7 and some of the cool features from Linux.
Sure there's no privacy and it 'may' lag, however that really doesn't phase me. Linux crashed on me and was laggy at times also, so I think Ubuntu at least is far from perfect.

I can now deal with my gb's and gb's of data easily and that is the main thing!

---

### Post by BFG on 2018-07-17
Probably too late, but in case anyone else arrives at this thread -  this is part of your problem:

> **frappe792 said:**
> Hi all,

Trying to setup some network drives **[COLOR="#FF0000"]like I used to do on windows[/COLOR]**. I look back and can't believe how easy it was in comparison.
I never had trouble with it on windows nor on my android devices. I am using a QNAP NAS with 5 or 6 parent folders with various permission etc. For the purpose below **[COLOR="#FF0000"]_I am trying to map with admin_[/COLOR]** which has no restrictions in the QNAP.


It's one the *NIX community sees perpetually from windows migrants.  Nothing in windows works well unless you give yourself godlike permissions. I.e. Admin. 
It's so embedded in windows history that no-one ever stops to think about why it's an insane scenario.  On linux it's essential to unlearn this, or you will have constant frustrations.  Users must get out of the habit of trying to do everything as root / admin.
The QNAP is like any other linux server in that it will explicitly prevent root (admin) accounts from mounting over NFS and it will "squash" any attempts to do so. This is because it's such as a terrible idea in security terms.  You can override this (look up "no_root_squash")  but it's strongly advised to do it properly. 


For NFS to work properly you need to create a user on both server and client which has the same UID number (and by convention, the same username). All the permissions hang off the UID.  When this is done, you do not need to specify a username and password in the mount command (that was actually added as a workaround to get CIFS / Samba to work).
All this is in the man pages, but I can see your frustration.  You've probably started with a CIFS mount command and tried to tweak it to make it work for NFS - but the CIFS is a bolt on, so it's a bad starting point.

Line up your user IDs first. Forget everything you know about how windows/samba works and read through the literature for NFS.  
Once you have lined up the permissions, e.g. You can change the UID on ubuntu to be the same UID as on the QNAP. Then the command you will need is simply something like:

sudo mount 192.168.0.111:/Multimedia /mnt/qnap/multimedia -o tcp,hard,nfsvers=4,rsize=65536,wsize=65536,noatime,intr


Then you can put a line to this effect in /etc/fstab

A caveat though - as others have said, NFS is designed to make the share appear as part of your local filesystem.  This is not ideal over WiFi.  There are ways to make it work over WiFi but beginners would be better off just using samba.

---

