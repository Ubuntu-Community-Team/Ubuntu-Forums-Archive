---
title: "Network Manager problems"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by jimcameron on 2009-01-27
Hi,

I'm having some problems with my Network Manager. I use a wired network connection and it connects to the router fine as i can go on the internet. However when i go on to the network through Network Manager to view shared files with other computers on the network there is nothing to connect to. Under 'Windows Network' it comes up with only Vaio (my own computer).

I can do the same thing in Windows (as i have a dual boot system) and it works fine, i can access the shared files. 

Can anyone hel with my Network Manager problems...something to do with NM settings?

Please help..i don't wan to have to go into Windows just to view things on the network.

Cheers

Jim

---

### Post by 73ckn797 on 2009-01-27
Go into System/Administration/Synaptic Package Manager.

Select "Samba" and let it install. That should help on viewing other computers on the network.

Here is the info listed in Synaptic:
[html]a LanManager-like file and printer server for Unix
The Samba software suite is a collection of programs that
implements the SMB/CIFS protocol for unix systems, allowing you to serve
files and printers to Windows, NT, OS/2 and DOS clients. This protocol
is sometimes also referred to as the LanManager or NetBIOS protocol.

This package contains all the components necessary to turn your
Debian GNU/Linux box into a powerful file and printer server.

Currently, the Samba Debian packages consist of the following:

 samba - LanManager-like file and printer server for Unix.
 samba-common - Samba common files used by both the server and the client.
 smbclient - LanManager-like simple client for Unix.
 swat - Samba Web Administration Tool
 samba-doc - Samba documentation.
 samba-doc-pdf - Samba documentation in PDF format.
 smbfs - Mount and umount commands for the smbfs (kernels 2.2.x and above).
 libpam-smbpass - pluggable authentication module for SMB/CIFS password
                  database
 libsmbclient - Shared library that allows applications to talk to SMB/CIFS
                servers
 libsmbclient-dev - libsmbclient shared libraries
 libwbclient0 - Shared library for interfacing with the winbind service
 winbind - Service to resolve user and group information from Windows NT
           servers

It is possible to install a subset of these packages depending on
your particular needs. For example, to access other SMB/CIFS servers you
should only need the smbclient and samba-common packages.

http://www.samba.org/

Canonical provides critical updates for samba until May 2010.[/html]

---

### Post by Kellemora on 2009-01-27
Hi JC

Make sure you have Samba, smbclient and smbtree installed.
If smbfs is installed uncheck it, it prevents seeing all shares.

Open smb.conf and make sure you have the name of your WORKGROUP listed there.
The Default in Ubuntu is WORKGROUP = WORKGROUP
The Default in Windows is WORKGROUP = MSHOME
and anytime you mess with Windows it reverts to the default so check your Windows machine to make sure it's set to the name of your workgroup.
So it should read WORKGROUP = NameOfYourWorkgroup

Restart Samba or Reboot!

Go into Terminal and Type smbtree to see if ALL of your shares show up.  They WILL if everything is configured correctly.
But that does NOT mean they will appear under Places/Network.

I thought they had the 2 year old bug fixed in Nautilus, but it reared it's ugly head on me again yesterday!

You can also use Network Tools to PING your other machines to make sure that is working!

Now, if Nautilus is misbehaving.  Here it works for 3 days then takes a 2 day vacation, then for no reason, shows back up for work again, hi hi.........

You can open Nautilus, select Go/Location from the toolbar and type in the IP address of the machine you wish to see the shares on, they will appear that way.  When you select a shared folder it should mount and appear on your desktop as well as in Nautilus.

Tomorrow, Nautilus may or may not show it's shares, depends totally what side of the bed Nautilus got up on in the morning!

I used to use the three reboot trick, but that quit working.  Now it seems that rather than rebooting the machine nautilus is being blind on, go reboot the other machines, sometimes this wakes him up, but you have no idea what type of mood he will be in when woken up that way, hi hi..........

TTUL
Gary

---

### Post by jimcameron on 2009-01-31
"Make sure you have Samba, smbclient and smbtree installed.
If smbfs is installed uncheck it, it prevents seeing all shares.

Open smb.conf and make sure you have the name of your WORKGROUP listed there.
The Default in Ubuntu is WORKGROUP = WORKGROUP
The Default in Windows is WORKGROUP = MSHOME
and anytime you mess with Windows it reverts to the default so check your Windows machine to make sure it's set to the name of your workgroup.
So it should read WORKGROUP = NameOfYourWorkgroup

Restart Samba or Reboot!

Go into Terminal and Type smbtree to see if ALL of your shares show up.  They WILL if everything is configured correctly.
But that does NOT mean they will appear under Places/Network."


Hi thanks for your reply Gary.

Where do i install smbtree and smbclient?

I tried Synaptic Manager but nothing there...

Cheers
Jim

---

