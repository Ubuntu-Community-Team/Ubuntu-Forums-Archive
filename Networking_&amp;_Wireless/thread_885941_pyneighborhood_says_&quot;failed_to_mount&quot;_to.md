---
title: "pyneighborhood says &quot;failed to mount&quot; to Windows XP"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by fspade on 2008-08-10
Hello,

I spend the better part of today trying to connect to two **Windows XP** computers over my network.

The wiki gave me some good advice, from which I installed the following packages:
samba
smbfs
ntfs-config
pyneighborhood

PyNeighborhood shows me the XP computers with their names and shares, but when I click on one of the shares I get the message "failed to mount".

I have told PyNeighborhood to use /media as mount folder (which exists) and entered the user name and password from an XP user (admin user); checking anonymous login didn't do it either.

On the Network tab, **Always use msbrowse** is checked, **Client command** is *smbclient* and **Lookup** is *nmblookup*.

It didn't seem to make a difference whether **SMB** was enabled or not, or if **CIFS** was enabled or not. 

In one post it was recommended to install **mc**, which I did, but didn't seem to change anything.

From the Windows box I can see the samba shares and access the content, with no problem (I am quite happy about this).

The Windows firewall is turned off.

I am at my wits end and beg for your help to figure out how to access the windows shares.

Kind regards,

Frank

---

### Post by MatthewPlanchard on 2008-08-13
Hey fspade,

I am actually about to write a howto on this topic, which I'll link to as soon as I've made it, but to answer your question quickly:

in order to mount and unmount shares, you'll have to go into the Preferences dialogue and for both SMB and CIFS change the commands to include 'sudo' at the beginning so they read

```
sudo smbmount
sudo smbumount
sudo mount.cifs
sudo umount.cifs
```

It is also recommended to mount your drives to a folder in your home folder, so that you automatically have the correct mounting permissions. I create and use /home/username/mnt/lan for mine. (Create the folders beforehand).

Also, make sure that in the File Managers pane, remove xclient -e mc option and add 'natilus' if you're using Ubuntu or 'thunar' for Xubuntu or 'dolphin' for Kubuntu.

Let me know if this works.

---

### Post by fspade on 2008-08-13
Thank you Matthew for your reply.

It all seemed to make sense, but it didn't get me connected yet.

It appears to take longer now until I get the message "failed to mount" but that is the only difference I noticed.

It also is not able to start the file manager (I tried it with and without sudo). 

In my despair I upgraded to version 0.5.0-pre3. It was first able to show me the workgroup name but no shares. After I rebooted, it wasn't even able to do that any more. From that perspective version 0.4 seemed more capable.

I did change the mount point to under my home folder and 0.4 did create subfolders for each share it tried to open, but as I said, wasn't able to actually mount the share.

I don't insist in using pyNeigborhood, if I know another reliable way. Maybe, if we get this resolved, you have some more base for your HowTo.

Last thing, I guess you ment nautilus as the file manager. Either way neither spelling worked.

Please advise.

Kind regards,

Frank

---

### Post by fspade on 2008-08-13
I did some further testing, after I added a second ubuntu box to the network. There I am using pyNeigborhood 0.4.

After setting everything as you suggested, it showed my the workgroup and after klicking the other two PCs (one Windows Xp the other ubuntu).

When I clicked at the PC name a window labeled "Add machine" popped up with the PC name in the Network name field. Everything else was blank. After hitting "Try to retrieve missing data" that field was cleared too. That happend for both PCs.

Somehow I got each PC name to show up in the right pane. When I double-clicked on them, the progress bar in the status line got busy and after a while it showed: scanning host xxx... failed in the status line. That again was the same for both PCs.

In case that matters: I am using ubuntu 8.04.

Hoping this is additional food for thought. ;-)

Kind regards,

Frank

---

### Post by MatthewPlanchard on 2008-08-13
Dear Frank,

I also tried version 0.5 pre 3 and found it to be lacking to say the least.  The best option to get back to 0.4.1 is to uninstall and reinstall via synaptic.

As far as 0.4.1 goes, try running the entire program in root mode:

```
gksudo pyNeighborhood
```

That should automatically root any commands that the program offers, and so we will know if the problem is a permission problem or if it's something within the network.

Blessings,

Matthew

---

### Post by fspade on 2008-08-14
Hi Matthew,

thanks for your reply.

I uninstalled pyNeighborhood 0.5 and found out that through Synaptic I can only get 0.4-0ubuntu3, universe only carries 0.4-0ubuntu5.

I got the source of 0.4.1 from Sourceforge and installed it. This was one step forward insofar as pyNeighborhood is now able to retrieve the ip-address of the PC. It shows me the workgroup names in my network, scans the group and then reports: Failed to scan workgroup xyz.

Best wishes,

Frank

---

### Post by kevindontenville on 2008-08-15
I use pyNeighborhood a fair bit and wondered if it was worth clearing up a couple of things.

First if you run it as yourself and not root then make sure you mount the shares rooted in your home directory. eg /home/fred/lan/....  otherwise your username wont be able to create the directory or have permissions in it. Personally I mount in my home directory for convenience anyhow.  There can be various problems with running it as root eg complex permissions, generally I prefer too run as few apps with root perms as possible.

The username and password configured in the application is the one to be used when connecting to the remote share. If there are no permissions or restrictions on the share then you may be able to use anon, otherwise use the same credentials as the sharing server has set.

You can check that the share works from your login and requirements are met by using the Places Connect to Server in the top Ubuntu menu. Making a connection here will confirm that your computer has all the basic software and configuration to connect to the cifs/smb shares.

Hope this helps, let me know how you get on.

BTW the current 5 pre release is buggy for me too, though other pre versions have been fine to this point for me. As it is now being actively maintained and developed I am sure this slipup will be fixed, and I look forward to a great release.

I presume you can connect to these shares from XP machines on the network? I have had problems with local firewalls on XP blocking shares, esp things like McAfees/Nortons/et al.

---

