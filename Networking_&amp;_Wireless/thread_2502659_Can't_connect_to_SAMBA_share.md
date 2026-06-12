---
title: "Can't connect to SAMBA share"
date: 2024-11-23
forum: Networking &amp; Wireless
---

### Post by peyre on 2024-11-23
I have two Samba shares on my Xubuntu 24.04 desktop, and can connect to them from my son's Windows 10 machine.  However, from my Xubuntu 24.10 laptop, when I open Thunar and enter **smb://%computername%**, it asks what application I want to use to open it.  It offers samba-tool, but when I select that the dialog box goes away but nothing happens, and it never connects to my desktop.  What have I missed?

---

### Post by TheFu on 2024-11-23
MSFT changed how they do share discovery a few years ago.  It used to be through broadcasting "I'm here" all the time, but with internet scaling and corporate networks with many thousands of computers, that didn't scale.  I have these notes for Win10 clients to be able to find Linux Samba shares:
Install Samba, WS-Discovery tool, and Avahi:
```
  sudo apt update
  sudo apt install samba wsdd avahi-daemon
```
Make it so Windows can discover and connect to it by installing WS-Discovery and use Avahi so DNS isn't needed, but {hostname}.local will be the name used.

If your hostname is xubu-linux, then other computing machines can see it as xubu-linux.local.  That's the theory.

Between Linux systems, the best way to connect to a Samba share is by setting up credentials and placing a mount line in the /etc/fstab.  You can search these forums for more details about that, if you want to go that direction.

Of course, the native way for storage to be shared between Unix and Linux computers is by using NFS, but that seems to confuse lots of people, since it makes remote storage appear like it is local storage with all the permissions we expect on a Unix computer. There are a few tricks to ensure this works well, as NFS doesn't care about usernames or groupnames. Rather, it cares about uid and gid - those numbers - so it is important to ensure any files that are shared have the correct uid/gid on all computers.  There are setup by step NFS how-to guides for the client and server at help.ubuntu.com.  This is a 1-time setup, then it "just works" for decades.

NFS is a kernel module, so it performs slightly better than Samba, but samba isn't bad at performance either, if setup correctly.  For media sharing, NFS is superior to samba. 

Anyway, that should be enough to get you access/sharing between Linux computers.

---

### Post by peyre on 2024-11-24
Um.  Yes, I have a line in fstab that automounts my second hard drive on my desktop.  I hadn't added one to mount the drives on my desktop because it isn't always on (and besides I travel with the laptop sometimes) and anyway I don't need to access them from the laptop all that often.  But when you need to it can be important.

I tried installing samba wsdd avahi-daemon and it seemed to run successfully, but that hasn't made a difference that I can see.

I wonder what I'm missing!  I know I've been able to do this before; maybe 24.04 made a change in security settings that makes smb connections more difficult?

---

### Post by TheFu on 2024-11-24
There's a **x-systemd.automount** option for the fstab which won't mount storage until it is actually requested. I use this with my laptops.  At home, it has access to 25TB of network storage (NFS), but when I'm away, accessing that storage never enters my mind, so it never gets accessed or even attempted.

---

### Post by Morbius1 on 2024-11-24
> from my Xubuntu 24.10 laptop, when I open Thunar and enter smb://%computername%, it asks what application I want to use to open it.
Seems to be an evolutionary progression from what happened in 24.04.

In 24.04 under Browse Network in thunar the subcategory of Windows Network was removed:

It has always been labeled incorrectly since it implies SMB is only for windows.
Windows Network is a NetBIOS browsing function. There is no "browsing' in a modern network ... since there is no NetBIOS .. since there is no SMBv1.

smb://%computername% will initiate - or try to initiate - a browsing for that SMB host.

Try to access the server this way which will bypass NetBIOS:
```
smb://computername.local
```

Just make sure avahi-daemon is installed and running on both server and client.

---

### Post by peyre on 2024-11-24
**smb://computername.local** works on my desktop; I can see my shares there. But on the laptop it again asks what I want to use, and offers samba-tool, which does nothing.

avahi-daemon is running.

---

### Post by Morbius1 on 2024-11-24
None of this will work unless you are in the same subnet. Are you sure both machines are connected to the same router?

Can you - from the 24.10 machine - ping the server:
```
ping -c3 computername.local
```
Or even by ip address:
```
ping -c3 server-ip-address
```

And for the life of me I don't know how samba-tool is even an option on your desktop system/

---

### Post by peyre on 2024-11-24
I'm at home, and only have one router.  In fact I'm at my desk, with the laptop on my left, the computer on the right, and the router on the back of the desk.  Laptop's on wifi.

ping -c3 computername.local returns: Temporary failure in name resolution

ping -c3 ipaddress returns pings.  So does ping -c3 ipaddress.

smb://ipaddress in Thunar still does the thing with samba-tool.  I agree, I've never seen that before, don't know why it's there.  Maybe something I installed in Synaptic.

---

### Post by Morbius1 on 2024-11-24
I can't reproduce any of your symptoms in my live xubuntu 24.10 so ............

Install smbclient on the client:
```
sudo apt install smbclient
```
Then run the following command with the correct ip address of the server:
```
smbclient -L 192.168.1.103
```
If the server requires a username pass that user name this way:
```
smbclient -L 192.168.1.103 -U username
```

Do you get a listing of the server's shares?

---

### Post by peyre on 2024-11-24
Ah, that's better!  It challenges for a password.

```
Password for [WORKGROUP\leon]:

	Sharename       Type      Comment
	---------       ----      -------
	HomeFolder      Disk      Home folder share
	Storage         Disk      Storage share
	print$          Disk      Printer Drivers
	IPC$            IPC       IPC Service (%servername% server (Samba, Ubuntu))
SMB1 disabled -- no workgroup available

```

However, when I enter my password (I think the samba password is the same as my login one), it denies me, as above.

---

### Post by Morbius1 on 2024-11-24
If you go to Thunar and ask for the server and it's share explicitly: [COLOR="#0000CD"]smb://192.168.1.103/Storage[/COLOR]
Do you get prompted for credentials or do you get that stupid "Open With" dialog?

---

### Post by peyre on 2024-11-24
I get the "open with" dialog.

---

### Post by Morbius1 on 2024-11-24
Well, I can reproduce part of your symptoms.

From Xubuntu 24.10 I ran the smbclient command against my own server. That tells me that the samba client part seems to be working.

Then I ran the following command to mount a specific share on that server:
> xubuntu@xubuntu:~$ gio mount smb://192.168.1.103/srvpublic
Authentication Required
Enter user and password for share &#8220;srvpublic&#8221; on &#8220;192.168.1.103&#8221;:
User [xubuntu]: guest
Domain [WORKGROUP]: 
Password: 

That is the backend command that Thunar should be running when I specify smb://192.168.1.103/srvpublic.

It does in fact mount it just the way it should:
> xubuntu@xubuntu:~$ ls -l /run/user/1000/gvfs
total 0
drwx------ 1 xubuntu xubuntu 0 Nov 22 15:58 'smb-share:server=192.168.1.103,share=srvpublic'

I can now go into Thunar and view the contents of that share.

This tells me that the backend process works as it should.

However if I unmount the share, close Thunar, reopen Thunar and specify smb://192.168.1.103/srvpublic I get the "stupid Open With" dialog as if it has no idea what I'm talking about,

I truly have no idea what's going on there. Sure sounds like a bug to me.

---

### Post by peyre on 2024-11-24
Huh!  Well thanks for taking the time.  Maybe I just won't be able to do this for a while.  Ironic that it works Windows-Linux, but not Linux-Linux.

---

### Post by Morbius1 on 2024-11-24
Two interesting items:

[1] Gigolo, already installed in Xubuntu, can access the server and it's share just fine using Actions > Connect and will display it's contents in Thunar if desired. You can use gigolo to bookmark this connection if you want.

[2] There was a bug report submitted to XFCE through redhat that describes this exact situation:
> How reproducible:
Always

Steps to Reproduce:
1. Install all Fedora 15 XFCE spin updates and gvfs-smb.
2. Try to navigate to a Windows or other share using SMB.
3.
  
Actual results:
Can not navigate to share instead get asked what application to use.

It was fixed 13 years ago:
[https://bugzilla.redhat.com/show_bug.cgi?id=712469](https://bugzilla.redhat.com/show_bug.cgi?id=712469)
[https://bugzilla.xfce.org/show_bug.cgi?id=7774](https://bugzilla.xfce.org/show_bug.cgi?id=7774)

---

