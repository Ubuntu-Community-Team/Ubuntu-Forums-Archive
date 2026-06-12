---
title: "Share folder over network- SMB, NFS- using GUI"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by FreewheelinFrank on 2007-11-08
Hello!

I've been trying to work out how to share files between two computers running Ubuntu 7.10 over a network. I've only just acquired a router, so I'm new to home networking even in Windows. Been using Windows for years, but relatively new to Ubuntu.

Most of the guides I came across used the terminal. Eventually I found this simple guide showing how to do it with the GUI:

[http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/](http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/)

It was quite simple to share a folder using this method, but I have a few questions I hope somebody can answer.

If I want to use NFS, I'm prompted for the hostname, IP address or network for allowed hosts. How can I find these? I'm using a router with one computer wired and the other wireless. 

As Samba works for Ubuntu to Ubuntu sharing, is there any advantage to using NFS?

Another guide I found says it's necessary to edit smb.conf and add a smb password: I shared folders without doing this. Is it still necessary to do this in Ubuntu 7.10? (The guide was for 6.10).

[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM) 

Thanks in advance for any help!

---

### Post by FreewheelinFrank on 2007-11-08
> If I want to use NFS, I'm prompted for the hostname, IP address or network for allowed hosts. How can I find these? I'm using a router with one computer wired and the other wireless.

OK, I found hostname and IP address in my router settings: hostname is just the name I gave to the computer.

It was under LAN > DHCP Client List.

---

### Post by Yfrwlf on 2007-11-09
In Windows if you open a terminal and type in ipconfig it will give you the computer's IP.  If you have it set for DHCP instead of static, it may change though.  In Linux, you can open a terminal and type in ifconfig to get it.  You can also use the GUI in both cases, but the terminal is faster (for me).

I have heard that NFS is faster at file transfers than Samba is, so I was interested in using it as well.  However, I have not yet been able to find out how to access NFS shares using the GUI.  smb:// can access any Samba shares, and network:// doesn't work either.  I know that you can mount a NFS location through the terminal, but of course it needs to be accomplished through the GUI too.

I'll let you know if I find out how to do this through the GUI, if there is such a way yet.

---

### Post by mpierce on 2007-11-09
I've found samba to be the best and most reliable but it you want to use nfs, add all the packages, i.e., nfs-common, nfs-kernel-server.
1) Ensure you run rpcinfo at startup and check that portmapper is running
   sudo /usr/bin/rpcinfo -a
     portmapper should be in list
2) Create a list of drives to share:
   sudo vi /etc/exports
     e.g. /home/mpierce 192.168.1.0/24 (rw,no_root_squash)
3) Run:
   sudo  /usr/sbin/exportfs -a
     this refreshes the list
4) Start your nfs server
   sudo /etc/init.d/nfs-kernel-server start
5) Verify that all has started
   sudo /usr/bin/rpcinfo -a
   you are looking to see if nfs and mountd have been added
6) create a mount point to your nfs drive, e.g.
   sudo mkdir /media/xp
7) mount your drive:
   sudo 192.168.1.252:/home/mpierce /media/xp

That's the trick!
Hope this helps...

---

### Post by FreewheelinFrank on 2007-11-09
> **Yfrwlf said:**
> In Windows if you open a terminal and type in ipconfig it will give you the computer's IP.  If you have it set for DHCP instead of static, it may change though.  In Linux, you can open a terminal and type in ifconfig to get it.  You can also use the GUI in both cases, but the terminal is faster (for me).

I have heard that NFS is faster at file transfers than Samba is, so I was interested in using it as well.  However, I have not yet been able to find out how to access NFS shares using the GUI.  smb:// can access any Samba shares, and network:// doesn't work either.  I know that you can mount a NFS location through the terminal, but of course it needs to be accomplished through the GUI too.

I'll let you know if I find out how to do this through the GUI, if there is such a way yet.

There is a way to do this through the GUI:

[http://www.techotopia.com/index.php/Sharing_Ubuntu_Linux_Folders_with_Remote_Linux_and_UNIX_Systems](http://www.techotopia.com/index.php/Sharing_Ubuntu_Linux_Folders_with_Remote_Linux_and_UNIX_Systems)

Although it didn't work for me. I suspect that this is because of the way my wireless router is set up, but I don't know enough about networking to say for sure.

Samba also works through the GUI:

[http://www.techotopia.com/index.php/Sharing_Ubuntu_Linux_Folders_with_Remote_Windows_Systems](http://www.techotopia.com/index.php/Sharing_Ubuntu_Linux_Folders_with_Remote_Windows_Systems)

I managed to connect wired to wireless and wireless to wired using SMB, although it did take several attempts before the wireless computer saw the folders on the wired computer, and I had to re-do the 'share folder' thing again for folders to show up after a reboot, but again this might be the result of the way my router is set up.

 	
> Re: Share folder over network- SMB, NFS- using GUI
I've found samba to be the best and most reliable but it you want to use nfs, add all the packages, i.e., nfs-common, nfs-kernel-server.
1) Ensure you run rpcinfo at startup and check that portmapper is running
sudo /usr/bin/rpcinfo -a
portmapper should be in list
2) Create a list of drives to share:
sudo vi /etc/exports
e.g. /home/mpierce 192.168.1.0/24 (rw,no_root_squash)
3) Run:
sudo /usr/sbin/exportfs -a
this refreshes the list
4) Start your nfs server
sudo /etc/init.d/nfs-kernel-server start
5) Verify that all has started
sudo /usr/bin/rpcinfo -a
you are looking to see if nfs and mountd have been added
6) create a mount point to your nfs drive, e.g.
sudo mkdir /media/xp
7) mount your drive:
sudo 192.168.1.252:/home/mpierce /media/xp

That's the trick!
Hope this helps...

As Samba seems to be working, I think I'll use that, but thanks anyway.

Thanks both for comments.

---

### Post by Yfrwlf on 2007-11-23
> **FreewheelinFrank said:**
> although it did take several attempts before the wireless computer saw the folders on the wired computer, and I had to re-do the 'share folder' thing again for folders to show up after a reboot, but again this might be the result of the way my router is set up.

Samba and Windows file sharing takes a while to propagate over the network, it will be a few minutes before new shares show up, but you can access them immediately before they do by typing in the location directly into Nautilus or whatever file browser you're using.

---

### Post by jonandrews on 2007-11-24
If you're a windows guy like me, you might find my XP/Ubuntu networking guides helpful:

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

---

