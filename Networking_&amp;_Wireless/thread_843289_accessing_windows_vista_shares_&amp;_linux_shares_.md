---
title: "accessing windows vista shares &amp; linux shares with elyssa (&amp;hardy)"
date: 2008-06-28
forum: Networking &amp; Wireless
---

### Post by ptrbee on 2008-06-28
hi,
can anyone help with this I also posted here
[http://www.linuxmint.com/forum/viewtopic.php?f=150&t=14162]("http://www.linuxmint.com/forum/viewtopic.php?f=150&t=14162")
briefly I can't access network shares in hardy & elyssa ( i installed hardy on a spare drive to test) even if i manually mount the shares i cant copy data to the network machine. 
sudo mount -t (cifs or smbfs) -o username=ptrbee //10.0.0.2/g /mnt/vistasharedfolder mounts the share & i can browse with nautilus but cant copy at home i have 2x vista sp1 desktops, 1 winxp pro, 1 powerbook, at work 2 office locations, linux servers with varios os shares....helppp:confused: 


> Hi,


I have a problem which I have seen similar post to in the forums since installing elyssa. I can see machines on my network in nautilus but when i try to access them nothing happens, if i try to connect to server & select windows share as the service type, I get "Couldn't display my shared folder" error. This is driving me mad as It worked seamlessly in daryna. Is this the price of progress?? I have seen post refering to fusesmb being taken out due to being a security risk & i have tried everything i know so far which isn't much :( nmblookup \* displays the list of pc's connected to my network but i can't connect.

I use my laptop at home & at the office, at home my domain is "MSHOME" which is in my samba config but i can be at 2x different office locations which are run by linux servers & have windws, linux, & mac shares all of which i can see but can't connect to. I used to be abled to plug & go with daryna but elyssa is turning me old & grey fast, someone please save me :? :shock:

ptrbee.

---

### Post by linfidel on 2008-06-28
So, if you type "smbclient -L ComputerName" (windows ComuterName), does it list the shares?  When it asks for a password, be sure to enter the Windows password.

I can get a full list of shares, and then, in Nautilus, I enter "smb://ComputerName/ShareName" and it mounts the share.  I can enter an administrative share such as c$ to get to the entire drive.

I do have the same user name on both machines, which may or may not matter.  :-)

But if I try to browse via the menu item "Places", "network", it comes up blank.

One thing that occurs to me is that I have the Windows comuter name in my hosts file (/etc/hosts).  This may not work if it isn't there, unless you have another way to resolve the host name.  You can test it though, I think, by putting in the IP address for computername.

---

### Post by ptrbee on 2008-06-30
yes, & smbtree gives a list of all shares as well, another strange thing about this is, if I boot from Hardy live cd the when i click network & browse to the pc & can see the shares & folders, last night i installed hardy on my spare drive but the same does not work, i can still connect though if i select connect to server & type in the necessary details I would get an error {Can't display location "smb://myvistapc/f/"} the specified location is not mounted. Click ok go to the desktop & there is a new icon there called "f on myvistapc" double click that & my share is mounted. Strange:confused: looks like  the live cd just works without any fiddling.in Nautilus, I enter "smb://ComputerName/ShareName" & works in hardy, looks like I'm leaving Mint.

---

### Post by linfidel on 2008-06-30
I believe the problem is a new feature of Gnome that Nautilus uses - something like Gnome Virtual File System.  I tried Konqueror, from KDE, and it worked fine.

I saw bug reports with discussions within the last day or two, so it's being looked at.

---

