---
title: "Configuring lan network"
date: 2007-09-29
forum: Networking &amp; Wireless
---

### Post by Metaphor on 2007-09-29
Hi.

I'm new to ubuntu and I'd like to know how do I configure my home lan.

the other computer has XP installed and we both get internet through a router.

When I had XP the configuring was almost automatic so how can I configure it with Ubuntu?

I've searched forum but couldn't find a solution, sorry if i skiped any...

Thx in advance!

---

### Post by stalker145 on 2007-09-29
> **Metaphor said:**
> Hi.

I'm new to ubuntu and I'd like to know how do I configure my home lan.

the other computer has XP installed and we both get internet through a router.

When I had XP the configuring was almost automatic so how can I configure it with Ubuntu?

I've searched forum but couldn't find a solution, sorry if i skiped any...

Thx in advance!

Are you able to access any part of your network/internet from your Linux computer? If you are unable, please post your network card make/model and someone *should* be along to help.

Basically, if your hardware is automatically supported, you should be able to get on the internet *if* your router is set to DHCP all computers on your LAN. If your router is set to hand out static addresses or you have MAC filtering on your router, please check to make sure that your Linux computer is allowed access.

---

### Post by Metaphor on 2007-09-30
I have internet access. What I want is to create a home network, in order to share files,etc.

How can I do it with Ubuntu?

---

### Post by unisol on 2007-09-30
try this:
You have to install samba. (you may only need to install the samba client) Now what do you want to do that doesn't work, specifically?  Do you want to share your Ubuntu's filesystem?  Which piece?  What's your workgroup name being used on the Windows machines?  In general, you need to go into your smb.conf file and make some tweaks, like the workgroup name, who's the master browser, what ID to use and what the translation is between your Ubuntu user accounts and the ID's as Windows knows them (if different) in smbusers, etc.

To mount a Windows shared drive on your Ubuntu system, you need to create a mount point directory, then issue the smbmount or mount command.  I typically use something like this:

    mount -t smbfs //machine1/share1 /mnt/machine1/share1

This command will generally prompt you for a username and password (depending on how you have smb.conf layed out), or you can add the "-o username=windowsid,password=winpassword" option string to the end of the command.  If you really know what you're doing, you can add this into /etc/fstab and never issue it again.

I can go on and on, but it would help if we know EXACTLY what you were trying to do.
To be able to see and access other machines on the network, in particular those running Windows or Samba, then you'll need to make sure that the packages smbclient and samba-common are already installed. Now, you have three main choices:

The first is to use a file browser, such as Nautilus or Konqueror, to access the shares. Thunar, XFCE's file manager, does not yet have this ability.

If in GNOME, then hit 'Places' on the panel, and then 'Network Servers'. From here, you should be able to see all of the Windows machines. From within Nautilus, open the 'Go' menu, and then select 'Network' to get the same screen.

If using Konqueror, then use the 'Go' menu and select 'Network Folders'. You then want to select 'Samba Shares' to view all of the Windows and Samba shares on the network.

With Windows machines, you'll generally be asked for a username and password. However, if anonymous browsing is allowed, but you want to be a specific user (for instance, some shares may only be viewable by certain users), as frequently occurs when accessing Samba shares hosted on a Linux machine, then you need to add a couple of steps. Firstly, navigate to the machine you want, so that you're viewing all of the shares.

If you're using Nautilus, hit Ctrl+L, so that you can see the current address. It should be in the format smb://nameofmachine. To login a specific user, change this to smb://user@nameofmachine, replacing user and nameofmachine with your username and the name of the machine respectively. You'll then get a prompt asking for a password, which, once entered, should allow you to browse that machine as the user specified.

If you're using Konqueror, then change the location from smb://nameofmachine to smb://user:password@nameofmachine. Of course, showing your password in this manner isn't terribly secure (meaning that somebody could just look over your shoulder), so if you do use Konqueror, you might want to consider an alternative method of accessing shares.

The second choice is to use LinNeighborhood (packagename linneighborhood). This will allow you to browse all of the shares on the network. If you want to access a machine as a specific user, rather than anonymously, then just right-click that machine and hit 'Scan as user'. Then, pick the share you want to access, double-click it (or right-click and select 'mount'), enter a username/password if necessary, and hit 'Mount'. Then, you should be able to access the share from wherever you mounted it - the default is /home/user/mnt/MACHINENAME/sharename, although of course you can change this at your leisure.

The final method is to mount it yourself. To do this, just use the command smbmount //machine/share /path/to/mount/point, or smbmount //machine/share /path/to/mount/point -o username=username if you need to use a username/password. Once you've finished, you can unmount the share by typing smbumount /path/to/share.

To set up shares, you still need Samba installed. From here, you have two main choices - install and setup a package called swat (not covered here), or use the utilities of the desktop environment.

In GNOME, you'll need the package gnome-system-tools to be installed. Then, go to the Desktop menu, and find Shared Folders within Administration. In KDE, make sure is installed. From the KDE menu, choose the Settings entry under Actions, followed by Internet & Network, and finally File Sharing. This package also provides the entry Samba under the same menu, allowing you to configure more than just what files are shared.

---

### Post by Metaphor on 2007-09-30
:shock:

WOW too many information at a time! :D

I'll try those methods and I'll keep in touch to let you know if it worked fine!

Anyway, answering your question about what i exactlly want is simple : i just want to access the other computer in my house like i used to do in windows (my network places). I've shared some folders in the other computer, so now i just want to access them with read and write permissions. I regularly need to send files from one computer to another so that's why i need to get this working...:)

Thanks a lot for your DETAILED answer!

---

### Post by Metaphor on 2007-09-30
I went to nautilus into the menu GO --> NETWORK and amazingly there it was my other computer! 

And i've tried to erase a file and it did so i have full access!

thanks a lot for your help!

:)

---

