---
title: "Samba Network with PC's"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by txwooley on 2008-12-08
After myriad problems with Samba, smbfs, and smb.conf, I went into the package manager and completely removed Samba, Samba-common, and smbfs.  I then restarted my laptop (running Ubuntu 8.04).  I then went back to the packet manager and re-installed all of those and winbind.  When I go to network servers, everything looks spiffy for Ubuntu's shares, but my desktop running XP on a wireless card and desktop running Vista wired to wireless router do not show up.  Likewise, the PC's can see each other but not the Ubuntu laptop.  I ran smbtree and got the following results:


Password: 
WORKGROUP
	\\TXWOOLEY-LAPTOP		txwooley-laptop server (Samba, Ubuntu)
		\\TXWOOLEY-LAPTOP\great white    	
		\\TXWOOLEY-LAPTOP\PDF            	PDF
		\\TXWOOLEY-LAPTOP\printer        	printer
		\\TXWOOLEY-LAPTOP\print$         	Printer Drivers
		\\TXWOOLEY-LAPTOP\IPC$           	IPC Service (txwooley-laptop server (Samba, Ubuntu))
WOOLEY
Error connecting to 192.168.0.2 (Connection refused)
cli_start_connection: failed to connect to 192.168.0.2<20> (192.168.0.2). Error NT_STATUS_CONNECTION_REFUSED
Packet send failed to 192.168.0.2(137) ERRNO=Operation not permitted


192.168.0.2 is the XP desktop.  The Vista is 192.168.0.3 but it doesn't even show up in smbtree (with or without errors).

What am I doing wrong?

---

### Post by LowSky on 2008-12-08
have you tired to ping the other machine to make sure it is connected?

I too am haing problems with SAMBA, it seems that networking has become crap in the last two releases, because back on Gutsy and Fiesty everything worked easily.

also for the Windows computer is it on the same network, window's default is MSHOME, while Linux/samba creates WORKGROUP.

---

### Post by txwooley on 2008-12-08
Yes, it can ping both machines.  The workgroup for the Windows is WOOLEY, but I don't know how to change it on Ubuntu so it is still WORKGROUP.  Do I just edit the smbf.conf file with:

workgroup = WOOLEY 

At some point before I re-installed Samba, the Windows comps saw the Ubuntu comp and could access it's shares, but Ubuntu never did see the Windows.  Since the re-install, the Windows see each other but not Ubuntu.  Likewise the Ubuntu only sees itself.

---

### Post by LowSky on 2008-12-08
I looked around the web and found something that said you need to use

sudo nautilus to share the folders.. it works for me with a local folder, but when I try to share a Partition it says  it fails to mount... so go figure.
If you ask me networking is really flawed in Ubuntu. In windows I can create a share easily, but Samba/Ubuntu is way to difficult...

Hope my suggestion helps, and maybe some networking guru can help you out more

---

### Post by txwooley on 2008-12-08
Any input helps.  When your boat is taking water, you don't turn away anyone offering a bucket!  That said, I have no problem with the shares themselves (I think).  I right-clicked the folder, clicked sharing options, and checked share this folder.  When I lookin network services I have an icon for the Ubuntu laptop.  When I open that, I see the folder(s) I wanted to share.  I think if the crappy Vista could see the Ubuntu, it wouldn't have any trouble accessing said folders.

---

### Post by txwooley on 2008-12-08
bump

---

### Post by Kellemora on 2008-12-08
Hi TXW

First thing you want to do is REMOVE smbfs, it prevents shares from showing up in smbtree!

IF a share does show up in smbtree you should be able to go to Places/Network click on GO/Location and type in the IP number of the machine and all the shares should then appear.

When you mount a share (by clicking on it) it will appear on your desktop until unmounted.  Clutter on the desktop, but handy!

Don't count on shares showing up in Places/Network on their own as expected.  It has a bug in it that has been unresolved now for over two years.  Sometimes it works, sometimes it don't!

TTUL
Gary

---

