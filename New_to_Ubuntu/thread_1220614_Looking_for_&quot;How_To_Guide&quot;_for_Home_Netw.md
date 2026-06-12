---
title: "Looking for &quot;How To Guide&quot; for Home Networking"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by Razmear on 2009-07-23
I just converted my wife's PC from XP to Ubuntu 9.04. I've been on Ubuntu for a while now. When she was on XP she could print to my Ubuntu box fine, and file sharing also worked fine. 
Now that she's on Ubuntu too we have no access to each others pcs. 
When I check Places/Network I see Windows Network and clicking on it gives an Unable to Mount, failed to retrieve share list from server error.
 
Anyways, seeing how I've never networked two linux boxes before, is there a good "How To" guide out there for home networking? I'm sure there is just something that I need to setup that I haven't done before. 

Thanks,
eb

---

### Post by bodhi.zazen on 2009-07-23
samba would work =)

you can share files and printers over samba.

[Setting Up Samba - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SettingUpSamba")

---

### Post by Razmear on 2009-07-23
Found this link while searching:
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch02_:_Introduction_to_Networking](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch02_:_Introduction_to_Networking)

Very detailed tutorial. 

Samba is setup on both boxes, but they still don't see each other, so I'm guessing its some basic config I missed. 
Will RTFM and see if that helps.

eb

---

### Post by Razmear on 2009-07-23
Update: 
Got it working now. Used Firestarter to set the config instead of trying to figure out which text file to edit. 
Added her IP to the Inbound Traffic Policy and Allow Service for Samba from her IP also. 
I guess I had done this before when she was on WinXP, but her IP changed when 9.04 was installed so had to add her new one. 
Trying to access from Places/Network still fails on both sides, but using Connect to Server and specifying a bookmark fails with an error like no application exists to handle this operation, but it leaves behind a bookmark in the filemanager that can then be used to access the shares just fine. 
Still reading the manual to be able to set things up proper, but using firestarter as the config interface seems to have gotten things going for now. 

eb

---

### Post by mdsmedia on 2009-07-23
> **bodhi.zazen said:**
> samba would work =)

you can share files and printers over samba.

[Setting Up Samba - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SettingUpSamba")
This might sound like a silly question, but is Samba required to network 2 Ubuntu/Linux computers?

The page that you link to refers to networking Linux with Windows. I haven't had time to read through it yet, but I want to network 2 Linux computers too.

On the other hand, with Samba on one, will I need smbfs on each as well?

---

### Post by lisati on 2009-07-23
<please disregard>

---

### Post by mapes12 on 2009-07-23
Hi

If you're looking for a really simple way to network 2 Ubu boxes then have a look at Spaceteddy's reply in this post:

[http://ubuntuforums.org/showthread.php?t=793308](http://ubuntuforums.org/showthread.php?t=793308)

I've used this method without a hitch.

---

### Post by bodhi.zazen on 2009-07-23
> **mdsmedia said:**
> This might sound like a silly question, but is Samba required to network 2 Ubuntu/Linux computers?

The page that you link to refers to networking Linux with Windows. I haven't had time to read through it yet, but I want to network 2 Linux computers too.

On the other hand, with Samba on one, will I need smbfs on each as well?

You can do it in many many ways, samba, nfs, cups, ftp, http, ssh (scp).

IMO samba is easiest and for the most part can be configured via a gui, so good option for new users. Nothing wrong with another solution.

You need samba server on one box, the one with the printer, and samba client on the other.

---

