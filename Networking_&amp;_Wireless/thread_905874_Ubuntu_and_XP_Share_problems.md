---
title: "Ubuntu and XP Share problems"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by benign on 2008-08-30
I have a workgroup setup called WORKGROUP. One host is LAPTOP and the other is UBUNTU. The laptop is running XP, and can see the printer and shared folders on UBUNTU from XP under the workgroup. I can USE the printer on UBUNTU from XP. When I try to access a shared folder from UBUNTU, it asks for a username and password (which does not work). If I change the setting on the Ubuntu shared folder to allow guest access, XP can't even find the folder.

From UBUNTU, I can see the workgroup, but not LAPTOP (Places -> Network). From the Terminal I CAN 'ping laptop' and get a response coming from 'hit-nxdomain.opendns.com' rather than the local IP from the machine (192.168.0.100). What's with that? If I try to ping that IP then I get host unreachable. 

I set a samba password with smbpasswd -a myname, but it doesn't work. I also can't connect with using the IP address with smb:// network:// remote:// etc...

Any ideas? This is killing me because my last Ubuntu install has everything working right out of the box.

Update: After giving up and turning the laptop off, I just tried again and now I can access the Ubuntu shares. I'm not sure what I did, but I did reset the router and also reload samba on Ubuntu with 'sudo /etc/init.d/samba reload'. I still can't access the XP shares from Ubuntu

---

### Post by benign on 2008-08-30
I checked my router and the IPs for the hosts changed :/

I ran 'smbclient -L session 192.168.0.110' I get the following output:

```

Domain=[LAPTOP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       Remote IPC
	print$          Disk      Printer Drivers
	SharedDocs      Disk      
	hpphotos        Printer   hp photosmart 7700 series
	Downloads       Disk      
	UbuDocuments    Disk    
 
session request to 192.168.0.110 failed (Called name not present)
session request to 192 failed (Called name not present)

Domain=[LAPTOP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------

```

So it sees the shares, but can't access them. What is the meaning of the session request error?

'smbtree' tries to access the laptop over opendns, and if I run a tracert on the laptop IP it returns, it goes halfway across the country. What is it doing? There must be somewhere I can edit this?

For the heck of it, I just tried to access the XP shares with: 

'smb://192.168.0.110/' again, and it worked :/.

I'm not too happy with the blind troubleshooting. It's partially working, but I have no idea why. I still can't seem to access the printer on XP, just all the files in PRINT$ or whatever.

Helps meh?

---

### Post by GepettoBR on 2008-08-30
Nautilus has a serious problem with SAMBA in Hardy.

Have you tried setting both computers to use static IPs?

---

### Post by benign on 2008-08-31
> **GepettoBR said:**
> Nautilus has a serious problem with SAMBA in Hardy.

Have you tried setting both computers to use static IPs?

I'm not sure how to do that, or why they've changed. They used to be .100, and .101 (I had certain ports forwarded, and the settings are still in the router) and that was for 6 months or so, so I don't know? There is something I don't know - I just started a Network+ class, so maybe I'll find out later, hehe.

---

### Post by GepettoBR on 2008-08-31
You can most likely reserve the IPs in the router's config page. I have three computers here at home, all set to use DHCP but all with their IPs reserved by the router (so it always attributes the same IP to the same MAC address).

---

### Post by bab1 on 2008-08-31
> **GepettoBR said:**
> Nautilus has a serious problem with SAMBA in Hardy.

Indeed it does!  

Once the networking basics are taken care of, I believe that installing smbfs should be part of the OP's  solution.  See this:[http://ubuntuforums.org/showthread.php?t=903974&highlight=smbfs]("http://ubuntuforums.org/showthread.php?t=903974&highlight=smbfs")

---

### Post by benign on 2008-09-02
> **bab1 said:**
> Indeed it does!  

Once the networking basics are taken care of, I believe that installing smbfs should be part of the OP's  solution.  See this:[http://ubuntuforums.org/showthread.php?t=903974&highlight=smbfs]("http://ubuntuforums.org/showthread.php?t=903974&highlight=smbfs")

Unfortunately I already have that installed. :/

---

