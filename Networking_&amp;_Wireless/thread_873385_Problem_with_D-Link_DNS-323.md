---
title: "Problem with D-Link DNS-323"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by Brain_of_J on 2008-07-28
I am attempting to use a D-Link DNS 323 with Ubuntu 8.04.
For awhile I had been dual booting into Windows XP and Ubuntu 7 (Gibbon).  I was able to connect to the NAS in both Windows and in Ubuntu. On occasion I would have issue connecting in Ubuntu but this usually occurred after the NAS had gone into power saving mode.  A quick reboot would fix the issue.  I had no troubles (relatively anyways for a few months)

I re-formated my PC after vacation and now only have 8.04 Hardy installed.
I'm unable to connect to the device at all. My router is showing good lights but i'm pretty well out of ideas as i'm fairly new to linux...

any help would be appreciated.

thank you.

---

### Post by fregger on 2008-09-06
I am in the same boat as you.  DNS-323 and I cannot connect to it with my ubuntu desktop.  It worked one day perfectly and now no connection.  Did you ever get it working?

---

### Post by itcave on 2008-11-04
I have a very similar issue.  I too have the D-link DNS-323 and I'm running Ubuntu 8.10.  One day it was working fine, and the next nothing.  Currently I can only connect to the unsecured folders.  When I try to connect to a secured folder I get an error saying "Unable to mount location".  Using the same user name and pass on windows xp I have no problem at all.

Please help!

---

### Post by OO-Dragon on 2008-11-19
I have the same problem!  It's really annoying...

---

### Post by cebesius on 2008-11-23
I ran into some problems connecting to my DNS-323 after upgrading (fresh install) to Ubuntu 8.10.  It's much easier to troubleshoot this type of issue using the command line.  Adapt this to suit your environment:
```
smbclient --debuglevel=1 //yourdns323/yourshare
```
If you know the IP address of your DNS-323, use it instead of its hostname, unless you know for certain that DNS will resolve its hostname to the correct IP address.
In my environment, that means I tried:
```
smbclient --debuglevel=1 //sanbox/volume_1
Enter cebesius's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.24]
Server not using user level security and no password supplied.
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
tree connect failed: SUCCESS - 0
```
Ubuntu 8.10 is trying to use a (more secure) form of authentication that the DNS-323 doesn't support.  There is definitely more than one way to solve this.

One way is to hack your DNS-323 to have an updated Samba server which supports more secure types of authentication.  This would probably void your warranty, and since I'm not going to try, I won't be covering it.

Another way is to contact D-Link and complain about the Samba on the DNS-323 until they release a firmware with a better version of Samba.

Another way is to make Ubuntu authenticate with your DNS-323 using the weak lanmanager style authentication that the DNS-323 expects.  To make this work, I had to edit my samba configuration.  Open it up for editing by doing:
```
gksu gedit /etc/samba/smb.conf
```
Find the [global] section, and insert this line:
```
client lanman auth = yes
```

Now try to connect.  That solved it for me.  Hopefully it will for you too.

---

### Post by kennyams on 2008-11-24
Thanks, worked great for me.

---

### Post by rirad on 2008-12-29
Thanks a lot cebesius. I own a CH3SNAS box which is very similar to the DNS-323 and had the same problem on ubuntu 8.10. Your solution fixed my problem as well.

---

### Post by jkeating on 2009-01-09
cebesius, you're the man!  i've been trying to figure this one out for a while.  worked great!

---

### Post by ogger on 2009-02-18
Sorry - I cannot figure out what to type in. I start thinking linux is not for me, if I am unable to get a simple of the shelf product to run like the DNS-321. Any last words of wisdom? Thanks

---

### Post by ddalley on 2009-02-18
It didn't work for me, either. :(

Any suggestions?

---

### Post by alanh on 2009-03-23
> **cebesius said:**
> I ran into some problems connecting to my DNS-323 after upgrading (fresh install) to Ubuntu 8.10.  It's much easier to troubleshoot this type of issue using the command line.  Adapt this to suit your environment:
```
smbclient --debuglevel=1 //yourdns323/yourshare
```
If you know the IP address of your DNS-323, use it instead of its hostname, unless you know for certain that DNS will resolve its hostname to the correct IP address.
In my environment, that means I tried:
```
smbclient --debuglevel=1 //sanbox/volume_1
Enter cebesius's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.24]
Server not using user level security and no password supplied.
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
tree connect failed: SUCCESS - 0
```
Ubuntu 8.10 is trying to use a (more secure) form of authentication that the DNS-323 doesn't support.  There is definitely more than one way to solve this.

One way is to hack your DNS-323 to have an updated Samba server which supports more secure types of authentication.  This would probably void your warranty, and since I'm not going to try, I won't be covering it.

Another way is to contact D-Link and complain about the Samba on the DNS-323 until they release a firmware with a better version of Samba.

Another way is to make Ubuntu authenticate with your DNS-323 using the weak lanmanager style authentication that the DNS-323 expects.  To make this work, I had to edit my samba configuration.  Open it up for editing by doing:
```
gksu gedit /etc/samba/smb.conf
```
Find the [global] section, and insert this line:
```
client lanman auth = yes
```

Now try to connect.  That solved it for me.  Hopefully it will for you too.

-----------------------------------------------------------------------------------------------------

Thanks for this.  I've had a string of problems with samba shares, since I upgraded from Gutsy, which worked just fine.  Firstly there was the gvfs issue over samba shares with passwords -details here:

[http://bugzilla.gnome.org/show_bug.cgi?id=524485](http://bugzilla.gnome.org/show_bug.cgi?id=524485)

I installed the 8.10 update containing the gvfs patch.

After this, I still couldn't connect to my DNS-323. 

Your fix above worked for me. I can now mount, browse and access files on my DNS-323.  

However, I'm left with a residual problem in that I can't resave files to folders on the DNS-323.  In addition, if I drag a file to a folder, the modification date is changed to the date and time that the file was copied over and it loses it's original modification date.  In addition, rsync complains with the following message: "failed to set times on 'directory_name': Not a directory (20)"

Any ideas on what is going on here?

---

### Post by Raidue on 2009-05-09
Just wanted to say that **cebesius **fix worked perfectly for me as well.  I just upgraded to Jaunty 9.04 yesterday.  I could not connect to the NAS before adding the necessary line to the config file.  Once the file was added I could mount the drive with no issues.

Thanks again.  

Cheers,
Mo

---

### Post by geoff511 on 2009-05-20
Hi,
Upgraded to Jaunty 9.04 over week ago when bought DNS-323.
Connected without any probs at all, have been able to see, add files to & remove by giving the Linux machine a user name and password in the DNS-323 configuration.

My problem is How Do You Mount the DNS-323 automatically when Ubuntu starts ?
If I go into File Browser and click on Network, then DNS , it is now avail to some programs to add/change/delete files but not all.
But til then, no program can see it, as it is not mounted.

If I click on the DNS-323 once mounted and try to Make A Link an error message comes back - "Target doesn't support symbolic links"
Why ? and how do I get round it ?

Thanks

---

### Post by geoff511 on 2009-05-22
Hi,

Have just posted a thread on how to mount a folder your DNS-323 into a folder in Ubuntu when it loads.

[http://ubuntuforums.org/showthread.php?t=1166719](http://ubuntuforums.org/showthread.php?t=1166719)


Hope it helps
Geoff

---

### Post by dslink on 2009-09-23
thanks for that info on the smb.conf on the first page. worked right away in karmic.

---

### Post by jer.lawrence on 2010-02-05
Better late than never?  Thanks for this, it worked perfectly.

> **cebesius said:**
> I ran into some problems connecting to my DNS-323 after upgrading (fresh install) to Ubuntu 8.10.  It's much easier to troubleshoot this type of issue using the command line.  Adapt this to suit your environment:
```
smbclient --debuglevel=1 //yourdns323/yourshare
```
If you know the IP address of your DNS-323, use it instead of its hostname, unless you know for certain that DNS will resolve its hostname to the correct IP address.
In my environment, that means I tried:
```
smbclient --debuglevel=1 //sanbox/volume_1
Enter cebesius's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.24]
Server not using user level security and no password supplied.
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
tree connect failed: SUCCESS - 0
```
Ubuntu 8.10 is trying to use a (more secure) form of authentication that the DNS-323 doesn't support.  There is definitely more than one way to solve this.

One way is to hack your DNS-323 to have an updated Samba server which supports more secure types of authentication.  This would probably void your warranty, and since I'm not going to try, I won't be covering it.

Another way is to contact D-Link and complain about the Samba on the DNS-323 until they release a firmware with a better version of Samba.

Another way is to make Ubuntu authenticate with your DNS-323 using the weak lanmanager style authentication that the DNS-323 expects.  To make this work, I had to edit my samba configuration.  Open it up for editing by doing:
```
gksu gedit /etc/samba/smb.conf
```
Find the [global] section, and insert this line:
```
client lanman auth = yes
```

Now try to connect.  That solved it for me.  Hopefully it will for you too.

---

### Post by LetsLinux on 2010-06-05
> **cebesius said:**
> I ran into some problems connecting to my DNS-323 after upgrading (fresh install) to Ubuntu 8.10.  It's much easier to troubleshoot this type of issue using the command line.  Adapt this to suit your environment:
```
smbclient --debuglevel=1 //yourdns323/yourshare
```
If you know the IP address of your DNS-323, use it instead of its hostname, unless you know for certain that DNS will resolve its hostname to the correct IP address.
In my environment, that means I tried:
```
smbclient --debuglevel=1 //sanbox/volume_1
Enter cebesius's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.24]
Server not using user level security and no password supplied.
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
tree connect failed: SUCCESS - 0
```
Ubuntu 8.10 is trying to use a (more secure) form of authentication that the DNS-323 doesn't support.  There is definitely more than one way to solve this.

One way is to hack your DNS-323 to have an updated Samba server which supports more secure types of authentication.  This would probably void your warranty, and since I'm not going to try, I won't be covering it.

Another way is to contact D-Link and complain about the Samba on the DNS-323 until they release a firmware with a better version of Samba.

Another way is to make Ubuntu authenticate with your DNS-323 using the weak lanmanager style authentication that the DNS-323 expects.  To make this work, I had to edit my samba configuration.  Open it up for editing by doing:
```
gksu gedit /etc/samba/smb.conf
```
Find the [global] section, and insert this line:
```
client lanman auth = yes
```

Now try to connect.  That solved it for me.  Hopefully it will for you too.

Worked for me - thanks buddy.

---

### Post by jackob4 on 2010-10-18
I have a DNS 323. I want to know how can I search for files from this drive. I have dedicated this drive for music files. It can be seen from my ubuntu 10.10. But there was no option to search files. Does anybody know any good application, to organise music files,tagging,find files, that are on a network? Any help is greatly appreciated.

Regards!
Jackob

---

### Post by furball4 on 2012-12-22
I had the same issue, and the 'lanman' change alone didn't fix it. After a few more searches I found additional recommended settings. The full set I added to /etc/samba/smb.conf is:

```
max protocol = NT1
client lanman auth = yes
client ntlmv2 auth = no
```Now it's working.

---

### Post by wildmanne39 on 2012-12-22
Old thread closed.

---

