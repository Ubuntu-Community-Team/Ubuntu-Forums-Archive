---
title: "Can't Access Samba Server from WinXP"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by galileo81580 on 2007-05-12
Warning: Linux Novice Ahead

Almost a year ago, I tried setting up a Fedora based file server at home but when it didn't work and life took over, I gave up.  I'm taking another stab at it and running into the same problems I had before.

I just installed Ubuntu yesterday and I'm trying to set up my Samba shares.  Here's what works and what doesn't:
**Works:**
Ubuntu sees, reads, writes all WinXP shares from both computers on my network.
Ubuntu sees, reads, writes it's own shares through the smbclient.
WinXP sees Ubuntu in the workgroup.

**Does NOT work:**
WinXP cannot access or even view a list of Ubuntu shares.
Login via WinXP "Connect to ***" dialog rejected for all users that I just created on the linux box.

I've read through several dozen sets of setup instructions and forums on the web, but everything **looks** to be in order to my untrained eye.  I have created linux users, set smbpasswords for them, created shares, set the workgroup, and even modified some Windows security settings according to one site I found.  All to no productive end.  I'm sure what I'm missing is obvious.  Someone please point it out to me.

---

### Post by murlosad on 2007-05-12
I ran into this same problem setting up my samba shares a few months ago. I found work around either here or on samba's website.  basically what I did was tell samba to login all connections from my network as me (my linux box login), it allows access from multiple XP boxes. It's not a perfect solution but if your network is secure it **should** be ok. 

I had to set 'security' to 'share' and 'guest account' to 'steve' (my linux username) under the security section

and set 'guest ok' and 'public' to 'yes' in my share section.

I can post my smb.conf file if you need/want it.

---

### Post by galileo81580 on 2007-05-12
I've just got a small home network.  Two(ish) windows computers, a wireless access point, and my linux box.  I'm trying to use the linux machine for extra storage as all the windows hard drives are full and this thing is otherwise just sitting around.  I also like to play on it.

Since there are three of us, I want each to have their own private space, as well as commonly accessible folders for media files.  The windows usernames are set up as full names in the form "First Last", where as the linux usernames are just "first".  I can change the linux names in anyway that's convenient, but not the windows names at this point.

I don't want to use the samba server as a domain controller or a wins controller or anything fancy.  This machine isn't on 24/7.  I just want it to host some directories and restrict access to them.

This seems to me like a fairly straightforward application of a wide-spread application.  What's the deal?

---

### Post by Wiebelhaus on 2007-05-13
Bump - having same issue.

---

### Post by Wiebelhaus on 2007-05-13
double post , my bad.

---

### Post by Wiebelhaus on 2007-05-13
First install samba

sudo apt-get install samba

With this you will have samba installed on your system, now you need to edit the configuration file which is located at:

/etc/samba/smb.conf

Enter this at the bottom on the .conf file


> [global]

workgroup = MSHOME

netbios name = UBUNTU_SERVER

security = SHARE

auth methods = guest

domain master = No

wins support = Yes

[share1]

comment = mi home

path = /home/ubuntu user
read only = No

guest ok = Yes

This will enable windows to see the folders you specify for the shared folders applet.

---

