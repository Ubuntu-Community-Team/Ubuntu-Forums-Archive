---
title: "Ubuntu system-config-samba refuses to show up"
date: 2015-12-30
forum: Networking &amp; Wireless
---

### Post by tre4 on 2015-12-30
Okay so this seems different to a whole load of other threads in that I've followed all the advice on those and still don't seem to be able to get this program to show.  It takes my password then nothing.  No error message, just nothing at all.

I've installed all the glade and python packages noted.  I've autoremoved samba, deleted /etc/samba and reinstalled and yet I still can't get this utility to run.

The only reason I'm trying to do that is that I cannot get any shares to show up on the machine at all which is quite frustrating.  I assumed the tool might help me figure out what was wrong but I've been at this for over two hours now on the web and still not managed to figure it out.  I'm convinced it is an easy kick myself thing but I just cannot see it.  Anyone got any ideas that could help?

---

### Post by bab1 on 2015-12-30
> **tre4 said:**
> Okay so this seems different to a whole load of other threads in that I've followed all the advice on those and still don't seem to be able to get this program to show.  It takes my password then nothing.  No error message, just nothing at all.

I've installed all the glade and python packages noted.  

Noted where?  What instructions were you following?> 

I've autoremoved samba, deleted /etc/samba and reinstalled and yet I still can't get this utility to run.
Does Samba run?  The default install of Samba only needs a share to be defined at the bottom of the /etc/samba/smb.conf file.> 
The only reason I'm trying to do that is that I cannot get any shares to show up on the machine at all which is quite frustrating.  I assumed the tool might help me figure out what was wrong but I've been at this for over two hours now on the web and still not managed to figure it out.  I'm convinced it is an easy kick myself thing but I just cannot see it.  Anyone got any ideas that could help?
Maybe, but maybe not.  There is no reason to remove the /etc/samba directory and sometimes it is not easily reconstructed.  Post the output of these commands to see where your configuration```

cat /etc/samba/smb.conf

pgrep -l mbd

```
Post the text output between [noparse]```
 
```[/noparse] blocks.  This preserves the fixed text formatting.  The easiest way to do that is to click on the **[SIZE=5]#[/SIZE]** icon at the top of the advanced reply editor and paste the data between the blocks.

---

### Post by tre4 on 2015-12-30
Hi BAB1

Too many instructions I'm afraid, I just kept looking at threads with a similar problem and tried out their solutions.  Mistake may have been going down into the weeds of some of the threads.

Samba seems to be running.  doing smbclient -U% -L localhost gets me:

Domain=[LARCH] OS=[Unix] Server=[Samba 4.1.17-Ubuntu]

	Sharename       Type      Comment
	---------       ----      -------
	TestShare       Disk      
	IPC$            IPC       IPC Service (Samba 4.1.17-Ubuntu)
	Test            Disk      
Domain=[LARCH] OS=[Unix] Server=[Samba 4.1.17-Ubuntu]

	Server               Comment
	---------            -------
	MACHINEONE           Samba 4.1.17-Ubuntu

	Workgroup            Master
	---------            -------
	LARCH                MACHINEONE
	WORKGROUP            MEDIAHUB

The smb.conf I have currently is really straight forward

[Global]
	workgroup = LARCH

[TestShare]
	path=/home/system/Test
	read only=no
	guest ok=yes


Just knocked it up to at least try something.  This all seems to be out there but if I attempt to access from a windows machine using net view \\192.168.... rather than a list of services I get access denied 5 error.  I thought the samba utility would help me to configure users and passwords etc.  but it just refuses to run.

pgrep -l mbd  gets me

2554 smbd
2555 smbd
2591 nmbd


I seem to have two smbd processes...  that is curious  if I stop smdb they both stop.  I can see how having two different processes could cause the samba configuration utility some challenges, if this is indeed what this suggests.  I'll have a poke in my init files see if I can find out what is going on but some pointers would be good if you have any.

---

### Post by bab1 on 2015-12-30
What happened to "Post the text output between [noparse]```
 
```[/noparse] blocks." ?

Samba always runs 2 instances of smbd.  The first is the root process.  The second is a fork of the first.  This allows multiple users to access shares.

>  I get access denied 5 error...
This looks like a permissions issue to me.

---

