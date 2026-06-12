---
title: "Samba won't display Windows Share content"
date: 2008-10-25
forum: Networking &amp; Wireless
---

### Post by LegoAddict on 2008-10-25
I am running Ubuntu 8.10 on a Dell Precision M20 laptop which has always connected no problem to an in-house wireless network.

In this network we have my laptop (Ubuntu/XP dual boot), the family desktop (Ubuntu XP/dual boot), my dad's laptop (XP), my mom's laptop (XP), my brother's laptop (PPC Mac on whatever the newest one is), and my mom's desktop (XP).  We also have a home server named Cookie, which is a Windows-based server (NFS?  This isn't my area  EDIT the FS is CIFS).  Inside Cookie are two Windows Shares called info and share.  This disk is hooked directly to the wireless router, with no gateway computer.

So I can see Cookie and it's folders, and I can open and view shares on the other Windows computers, but after opening "share" in Cookie I can't see anything in the folder.  Nautilus doesn't output any errors.  I have Samba installed.

What is my potential problem and how do I fix it or what additional data need I post?

EDIT:  Cookie's file system is CIFS

---

### Post by dmizer on 2008-10-26
Please see the second link in my sig.

---

### Post by LegoAddict on 2008-10-27
I've read that one before...  the problem is that nothing shows up even though the share is chock full.  Even if I create a folder in there with Ubuntu it doesn't show up when I go into share again.

---

### Post by dmizer on 2008-10-27
Please post the output of:
```
smbtree
```

Also, can you post the mount command you were attempting to use?

---

### Post by LegoAddict on 2008-10-27
```
WORKGROUP
	\\CHRIS-LAPTOP   		chris-laptop server (Samba, Ubuntu)
		\\CHRIS-LAPTOP\IPC$           	IPC Service (chris-laptop server (Samba, Ubuntu))
		\\CHRIS-LAPTOP\print$         	Printer Drivers
TOMALTY
	\\TOMALTYLAPTOP  		Carol's Laptop
		\\TOMALTYLAPTOP\BAC sermons    	
		\\TOMALTYLAPTOP\Laptop Videos  	
		\\TOMALTYLAPTOP\C$             	Default share
		\\TOMALTYLAPTOP\ADMIN$         	Remote Admin
		\\TOMALTYLAPTOP\HP5740         	HP Deskjet 5700 Series
		\\TOMALTYLAPTOP\2007 08August  	
		\\TOMALTYLAPTOP\Hewlett-Packard	
		\\TOMALTYLAPTOP\CARRICDESIGN-LpTp	
		\\TOMALTYLAPTOP\My Music       	
		\\TOMALTYLAPTOP\print$         	Printer Drivers
		\\TOMALTYLAPTOP\SharedDocs     	
		\\TOMALTYLAPTOP\D$             	Default share
		\\TOMALTYLAPTOP\IPC$           	Remote IPC
		\\TOMALTYLAPTOP\GARRETT        	
		\\TOMALTYLAPTOP\2007 06June    	
		\\TOMALTYLAPTOP\HP             	
		\\TOMALTYLAPTOP\LTRS           	
	\\OFFICEPC       		TOMALTY2006
		\\OFFICEPC\WEBSITE        	
		\\OFFICEPC\BOOKSTORE CAFE 	
		\\OFFICEPC\Sound FX       	
		\\OFFICEPC\Carol's Music folder	
		\\OFFICEPC\Production Loops&Tracks	
		\\OFFICEPC\C$             	Default share
		\\OFFICEPC\Data - Rick    	
		\\OFFICEPC\ADMIN$         	Remote Admin
		\\OFFICEPC\ASBUILT CLIMATE CARE	
		\\OFFICEPC\F$             	Default share
		\\OFFICEPC\ECHO           	
		\\OFFICEPC\5700 HP        	HP Deskjet 5700 Series
		\\OFFICEPC\OPHELIA        	
		\\OFFICEPC\My Pictures    	
		\\OFFICEPC\From GARRETT'S camera	
		\\OFFICEPC\F55FJanuary 2008	
		\\OFFICEPC\Business Card  	
		\\OFFICEPC\Interesting pics	
		\\OFFICEPC\PICTURES       	
		\\OFFICEPC\print$         	Printer Drivers
		\\OFFICEPC\Documents      	
		\\OFFICEPC\IPC$           	Remote IPC
		\\OFFICEPC\Data-Garrett   	
		\\OFFICEPC\Web Downloads  	
		\\OFFICEPC\Carol's pictures in office	
		\\OFFICEPC\Chris' Comps - RYV	
		\\OFFICEPC\E$             	Default share
	\\COOKIE         		Cookie Monster Link Station
		\\COOKIE\share          	HD-LAN Share Folder
		\\COOKIE\info           	Link Staion information
		\\COOKIE\lp             	Network Printer for Windows
```

I'm not mounting from the command line, I'm just double clicking on the share in Nautilus (this is Ubuntu Intrepid), so whatever command that invokes...

EDIT:  It seems, upon further inspection, that the server is NTFS, not CIFS...  weird...

---

### Post by dmizer on 2008-10-27
A couple of things.

1) NTFS is the file system (format) of the disk itself. This has absolutely no effect on how you will connect to the share.
2) CIFS is a network file system based on Windows SAMBA which is used to transfer files from a SAMBA server. This is what you should be using to connect to the share from Ubuntu.

You mentioned that you had looked at my guide earlier, so I was wondering what you had used in that case.

Finally, "Cookie" appears to be a NAS device, is that correct? If so, please provide the make and model of the device. It's possible there is a better way to connect to it than SAMBA.

**EDIT**
Humm, I have another idea which requires a tiny bit of command line, but should also get you working correctly. Simply copy and paste the following commands:

First, make sure samba is installed:
```
sudo aptitude install samba
```
Then make a backup of smb.conf (in case you want to refer to it later):
```
sudo mv /etc/samba/smb.conf /etc/samba/smb.conf-backup
```
Now create a new smb.conf file with the following command:
```
gksudo gedit /etc/samba/smb.conf
```
Paste the following text:
```
[global]
    ; General server settings
    netbios name = CHRIS-LAPTOP
    workgroup = TOMALTY
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    name resolve order = hosts wins bcast
    wins support = no
```
Save the file and exit gedit.

Finally, restart the samba server,
```
sudo /etc/init.d/samba restart
```
Now see if you can view the \\COOKIE\share in Nautilus.

---

### Post by LegoAddict on 2008-10-28
No dice...

nothing changed...

The exact model is Link Station HD-H250LAN

This is weird... I can see all the other shares on my network but not these ones.

EDIT:  Interestingly enough, I can no longer see TOMALTYPC and it's not in smbtree either...

EDIT II:  Though I can access it through smb://tomaltypc/

---

### Post by dmizer on 2008-10-28
Check "TOMALTYPC" and make sure it's part of the "TOMALTY" workgroup.

Is the Linkstation's "Access restriction function" turned on? (under "security" > "setup shared folder")

Are you using Hardy?

---

### Post by LegoAddict on 2008-10-29
TOMALTYPC is a part of the TOMALTY workgroup...

Where would I find Security?  I can't seem to get to the control panel of the server because I can't figure which IP address it is (bah)

And I'm using Intrepid, but the same problem existed under Hardy.

---

### Post by dmizer on 2008-10-29
> **LegoAddict said:**
> TOMALTYPC is a part of the TOMALTY workgroup...
Then you most likely have a firewall problem on TOMALTYPC

> **LegoAddict said:**
> Where would I find Security?  I can't seem to get to the control panel of the server because I can't figure which IP address it is (bah)
I don't have the manual handy, but you should open firefox and browse to [http://cookie](http://cookie)

That should get you to the Linkstation's web configuration page. If not, try [https://cookie](https://cookie)

---

### Post by LegoAddict on 2008-10-29
[http://cookie](http://cookie) takes me to a parked website [www.cookie.com](www.cookie.com).  No page found for HTTPS.

I'm trying to get the manual from my uncle...

---

### Post by dmizer on 2008-10-29
I found the manual in pdf form here: [http://www.amazon.com/Buffalo-HD-H250LAN-LinkStation-Network-External/dp/B0002ICEIQ](http://www.amazon.com/Buffalo-HD-H250LAN-LinkStation-Network-External/dp/B0002ICEIQ). The manufacture's website will provide a copy as well.

> **LegoAddict said:**
> [http://cookie](http://cookie) takes me to a parked website [www.cookie.com](www.cookie.com).  No page found for HTTPS.

I'm trying to get the manual from my uncle...

This may be why you're having a problem. Let's try configuring your name resolution.

First, edit /etc/nsswitch.conf:
```
gksudo gedit /etc/nsswitch.conf
```
Look for this line (it may not look exactly like this):
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```
Add "wins" to this line, in front of "dns" like so (the order IS important):
```
hosts:          files mdns4_minimal [NOTFOUND=return] [COLOR="Red"]wins[/COLOR] dns mdns4
```
Save the file and exit gedit.

Now, install winbind:
```
sudo aptitude install winbind
```

Restart networking:
```
sudo /etc/init.d/networking restart
```

Now try both accessing your shares and the web configuration page for your Linkstation.

---

### Post by LegoAddict on 2008-10-31
Ok - Status update:

I found Cookie's IP Address

[http://192.168.1.134/](http://192.168.1.134/)

And checked all the shares.  They're set to "win/mac" mode.  There isn't any authentication or anything that should block me.

Interestingly, I downloaded xsmbrowser and was using that (how I got the IP).  It can see the contents of share but it can't actually open anything...

EDIT:  I tried your method above and still no dice...  hmm...

---

