---
title: "Mounting a windows 95 share in linux"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by lestat on 2008-08-14
Hi,

I have been using the regular mount command which calls mount.cifs (which from what I understand is the replacement for smbmount and smbfs). The command works great for windows xp and windows nt shares, but I am having trouble with win95 shares. 

Using another windows computer and the "net use" command from the command prompt, I am able to mount the win95 share. So I have the servername and share name correct. I do not specify a username, only the password, which seems to be the way win95 shares work. 

With mount in linux, I have tried specifying the user as Guest, i tried not specifying a user but I keep getting a 

mount error 112 = Host is down

error message. I can definitely ping the IP address from my linux box. So the host is definitely up and running. 

Any help?

---

### Post by Iowan on 2008-08-14
For Samba sharing with XP and above (don't remember about Win98 ) smb.conf contains the line "encrypt passwords = true". Win95 doesn't encrypt passwords (unless there's a patch I don't remember).

---

### Post by dmizer on 2008-08-14
I don't think CIFS is compatable with Win95, you will have to compile SMBFS from source.

---

### Post by ccaaee on 2010-02-22
I've had no problem using smbmount with windows 95 in previous versions of ubuntu but now in 9.10 I get the "mount error 112 = Host is down" message as well.  Windows XP is no problem.  I still have a server running ubuntu 5.10 and another running 7.10. Each of these machine can mount windows 95 shares.  I've googled myself blue on this one but to no avail...
Any Ideas??

---

### Post by dmizer on 2010-02-23
> **ccaaee said:**
> I've had no problem using smbmount with windows 95 in previous versions of ubuntu but now in 9.10 I get the "mount error 112 = Host is down" message as well.  Windows XP is no problem.  I still have a server running ubuntu 5.10 and another running 7.10. Each of these machine can mount windows 95 shares.  I've googled myself blue on this one but to no avail...
Any Ideas??

Frankly, you should no longer be using Windows 95. It is way out of date, extremely susceptible to infection, is not capable of running current/secure software, and as such is a liability to other computers connected to your LAN.

If you have a serious need for Windows 95 (or Win98 for that matter), you really need to consider a solution which allows you to completely sever it's LAN connection and run it as an isolated work station with no LAN access at all.

It might make things inconvenient for transferring needed files, but that's a small price to pay for the overall health of your network.

---

### Post by ccaaee on 2010-02-23
I knew I'd get a reply like this...
This machine is only connected to the lan for archiving, is never connected to the internet and has hardware that works very well in win95 and NOT AT ALL in either linux or more recent versions of windows.  Nevertheless, I'd quite like to know what algorithm produces "Host is down" for a host that can be pinged and can be accessed by other versions of smbmount....

---

### Post by dmizer on 2010-02-23
> **ccaaee said:**
> I knew I'd get a reply like this...
This machine is only connected to the lan for archiving, is never connected to the internet and has hardware that works very well in win95 and NOT AT ALL in either linux or more recent versions of windows.  Nevertheless, I'd quite like to know what algorithm produces "Host is down" for a host that can be pinged and can be accessed by other versions of smbmount....

I don't intend to be rude or condescending. But the reality is that Win95 is no longer under development while Samba is. Even if you do fix your current issue, it's bound to be broken permanently sooner or later.

---

### Post by ccaaee on 2010-02-25
In hopes that this might help someone else with this sort of problem
and credit where credit is due: 
[https://bugzilla.redhat.com/show_bug.cgi?id=190006](https://bugzilla.redhat.com/show_bug.cgi?id=190006)


The windows host = lkj6
the share = tmp
the local mount pount = /mnt/lkj6_tmp

--what used to work:
smbmount //lkj6/tmp /mnt/smb_lkj6_tmp username=lkj8 -o password=???

--what now works:
mount -t cifs //lkj6/tmp /mnt/smb_lkj6_tmp -o password=???,servern=LKJ6

Note the uppercase in servern


Thanks for your comments dmizer, no offense taken...

---

