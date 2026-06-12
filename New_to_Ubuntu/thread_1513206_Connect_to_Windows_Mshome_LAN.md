---
title: "Connect to Windows Mshome LAN"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by ozstar on 2010-06-19
Hi,

I have a XP MsHome LAN with a few boxes on it and now want to connect my new Linux ubuntu 10.4 box to it.

On my Linux box in the Windows shares on mshome panel, I see all the XP boxes but get this message when trying to connect to each box.  

Unable to mount location . Failed to retreive share lits from server.

I cannot see the Linux box on the XP either.

What do I need to do to open the connections please?

Thanks

oz

---

### Post by cariboo on 2010-06-19
Open a terminal and type:

```
smbtree
```

the above command will show a listing of all the shared directories on your network, it should look something like this:

```
smbtree
Enter my password: 
APLUS
	\\WILLY          		willy server (Samba, Ubuntu)
		\\WILLY\print$         	Printer Drivers
		\\WILLY\Movies         	Movies & TV Shows
		\\WILLY\Music          	Music
		\\WILLY\Documents      	Documents
		\\WILLY\Stuff          	Everything Else
		\\WILLY\Iso            	Mounted iso's
		\\WILLY\Images         	iso images
		\\WILLY\IPC$           	IPC Service (willy server (Samba, Ubuntu))
	\\RISKY          		XP Computer
		\\RISKY\C$             	Default share
		\\RISKY\ADMIN$         	Remote Admin
		\\RISKY\EPSONSty       	EPSON Stylus Photo R340 Series
		\\RISKY\All Users      	
		\\RISKY\SharedDocs     	
		\\RISKY\print$         	Printer Drivers
		\\RISKY\IPC$           	Remote IPC
```

By default Ubuntu sets the workgroup as WORKGROUP, this may be part of the problem. To change the workgroup name you need to install samba, which is in the repositories. Once it's installed, press Alt-F2 and type:

```
gksu gedit /etc/samba/smb.conf
```

Change the workgroup name to MSHOME, then restart samba, rebooting is probably the easiest way. Once you have setup shared directories, and restarted samba your Windows computers should see the shared directories.

---

### Post by mapes12 on 2010-06-19
On my home network I couldn't get Samba to work properly and after much Googling I found a PyNeighbourhood HowTo. Once installed it's GUI. It goes like this for me:-

Go into Control panel in XP and enable "File and print sharing". Then go to the folder you want to share. Right click and enable "sharing". If the user account where the share is located in XP is a Limited account then you may have problems. The account needs to be given Administrator permission. Bad security but that's not my fault.

Next, on the Ubu machine go into Synaptic and install pyNeighborhood. Once installed it will be an application you can select from Applications. Click it. First some tweaks:

PyNeighborhood - Edit>Preferences
- Mount folder change to /home/username (this saves root having to do everything).
- Then "Remove mount point after unmount" = tick
- Then "File Manager" tab - add Nautilus

Then in the left hand pain right click the globe and select "Scan"

This should find your shared windoze folders. Double click the one you want in the right hand pain. This mounts it. Then right click it and select Nautilus as the file browser. You can then transfer stuff between the 2 machines.

If you have followed the above and still have problems then in my experience the problem is always with the XP machine, not Ubu. XP can sometimes lead you into thinking folders are being shared when in fact they are not. Hence my comment about Limited windoze accounts. It took me 3 days to figure that one out.

Hope this helps.

Mark

---

### Post by ozstar on 2010-06-19
Thank you guys for going to all that. It is appreciated.

I already have a network called MsHome on my XP boxes so just want to connect to that same mob.

In the Synaptic Package Manager I have found samba but as there are a few files showing am not sure which one to load.  The main one I guess, as it does have a red icon next to it.

When I highlight it the message says there are 5 packages which will be held back and not upgraded and 1 pack will be installed so that is a little confusing.

Do I get eveything that has samba or smb in the title or just the samba with the icon next to it?

Once again I do appreciate your help which I am sure many will benefit from as they start like me.

oz   :-)

---

### Post by ozstar on 2010-06-22
I did download the Samba with the red icon and left the others.

I rebooted the Linux box and now I am able to see it in the XP box under  the folder Workgroup wheareas the others are in MSHome.

I did a traceroute from Linux to an XP box and it did show the route in  .826ms.

Ping from Linux to XP was okay too.

So it looks like now I can connect but we are in different groups.

How do I get them on the same path?


oz

---

### Post by ozstar on 2010-06-23
In samba.conf I a groupt named  WORKGROUP, so I guess I need to  change that to MSHOME.

I tried but it was 'read only'.

How do I get into gui as root admin to make the change?

How can I login as the root admin in Ubuntu please?

Thanks

oz

---

### Post by Peter09 on 2010-06-23
Just do the edit command with the prefix sudo.
 
```
sudo gedit <your file>
```
 
as an example

---

### Post by anewguy on 2010-06-23
> **cariboo907 said:**
> Open a terminal and type:


By default Ubuntu sets the workgroup as WORKGROUP, this may be part of the problem. To change the workgroup name you need to install samba, which is in the repositories. Once it's installed, press Alt-F2 and type:

```
gksu gedit /etc/samba/smb.conf
```

Change the workgroup name to MSHOME, then restart samba, rebooting is probably the easiest way. Once you have setup shared directories, and restarted samba your Windows computers should see the shared directories.


Cariboo907 posted this for you already - be sure to read all the posts carefully.  The gksu prefix on the gedit runs as super user so you can edit the file.  The file is owned by root, and doesn't have write access for you.  By using the gksu, you give yourself temporary super user (root) access, thus letting you write the file as well.

Dave ;)

---

