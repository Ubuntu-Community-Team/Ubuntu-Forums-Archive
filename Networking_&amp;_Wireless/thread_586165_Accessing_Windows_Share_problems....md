---
title: "Accessing Windows Share problems..."
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by twilightomni on 2007-10-22
Complete newcomer to Ubuntu, recently installed it on his little brother's laptop.  I'm reasonably competent enough to edit textfiles and use the sudo command.  Just don't quite always understand what I'm editing. :)

At any rate, two windows computers (XP desktop, Vista laptop) have visible shares on the network.  [Vista is the one I'm trying to access].  When using Ubuntu's Nautilus to browse the network, I cannot enter either computer.  Both are visible, but give "Cannot open folder" when clicked.

So I tried many things on the Vista laptop.  Firewall off, Guest account on, Password sharing off [Network & Sharing Center], Public folder sharing on for all users, etc.  (I don't know the technical details of how to efficiently and securely setup my network shares.  I was just hoping to get inside the laptop's share, thus indiscriminately opening access as much as possible).  Made sure the Guest had read access to all the folders I was currently sharing.  But nothing worked.

I didn't think I had to worry about the SAMBA stuff I've heard of -- no clue how to use it -- mainly because I thought it was for servers only, and because there was some page in the Ubuntu community docs -- MountSharesPermanently or whatever it was that said Ubuntu no longer used Samba, or it was deprecated, or whatever.

At any rate, I could enter the share by doing Connect to Server, giving the laptop IP on the local home network ["smb://192.168.x.y" or somesuch].  This brought up the folder and I could navigate the share just fine.  But browsing through the Network folder never worked.

Ubuntu was able to detect the desktop's printer [shared on network], and print to it.  But it could not casually browse any of the shares in the Network folder on Nautilus, only accessing a share when I specified IP address using connect to server.

It appears other posters have had this problem [I've only gone a few pages back], but I didn't see an obvious solution.  I want to be able to casually and easily browse shares through the Network section in Nautilus.  Is there something very simple I'm missing?

---

### Post by froy02 on 2007-10-22
If you're using vista, click on start> network then the network window pops up.  Click on Network and Sharing Center.  On the bottom half It says Sharing and Dicovery.
Set the following: 
Network discovery --on
File Sharing -----------on
Public folder sharing --on
Printer sharing --on
Passwordprotected sharing --OFF
Media sharing --off

After you set that up.  Choose a folders you want to share and right click for properties> share. A windows pops up. Click on the drop-down button od Add and choose the people who can access the folder.  The administrator is autmatically added with full rights. You can add other users and permission levels for the folder or files.   Then click the button at the bottom that says Share.  Now that folder is shared with other windows and Ubuntu system in your network. 

Note: windows XP, Vista home and Premium do not share with domain.  You would not see your Ubuntu shares from them but you'll see other Windows shares from other windows machines,

---

### Post by twilightomni on 2007-10-22
Thank you for the information, but I think it might be something slightly less trivial.  I will try these steps again, but as far as I know, the folders and Network Sharing Center options are set correctly.  Also, the home network is a workgroup, and in addition to those options, Guest account is on and added to the access list of the shared folders.  Could there be anything I'm missing?

Should Ubuntu ask for a username or password whenever it tries to access a Windows share?  Since the share only allows certain users (those on the access list for that folder in Vista) I would think I somehow need to tell Windows what user I want to log in as.  But I have no clue how to do that, and apparently the guest account doesn't work either.


But this is all aside -- I **can access** the network shares by doing System --> Connect to Server and typing in the computer's IP.  But I want to know why I can't browse them under the System --> Network folder [since they all give "Cannot connect/open folder" errors when I go inside one of the systems, but work perfectly when I specify that system using IP under Connect to Server].

---

### Post by Cryophallion on 2007-10-22
I have the same problem.

I have fresh installs on a laptop and desktop, and they can't see each other networking (although the printer sharing works).

As they use dhcp, the ip sometimes changes, so I don't want to have to connect them by using ip.

I then tried to see if it could see a samba share on a dapper server I was setting up at home. Nothing there either.

I brought the laptop into the office, to try and see the office xp comps and edgy server.

Once again, no computers listed in windows network. I can connect via connect to server.

On the other side, I cannot see the samba folders on my laptop from the xp computers, although my access is share and everything is visible.

So something is wrong with either nautilus or samba, if we can't view network connections.

Once again, fresh installs, so it is not a firestarter etc issue.

---

### Post by rocket777 on 2007-10-22
Are you giving it enough time? I find that it sometimes takes as long as 5 minutes after bootup before my computers see each other's windows shares. Usually, it's on the windows to windows computers that refuse to let me see the workgroup. I believe it's because a newly booted system has to wait for the next time there's a broadcast of advertised services, and that doesn't happen all that often. But don't hold me to this.


Also, this thread was helpful to have my XP system see my ubunutu shared folders:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Actually, all I had to do was the  section on:

"2. Changing network settings in Windows"

although I also did first try setting up some samba passwords.

I had thought that this was maybe a firestarter issue, and turned off/on the firewall, but that didn't seem to matter in this case.

---

### Post by froy02 on 2007-10-22
I agree that sometimes you have to wait a little bit for the computers to sync before you can access the shared folders.

---

### Post by Cryophallion on 2007-10-22
Is one hour enough of a wait?

I am thinking that it is a nautilus issue more than anything else. 

I am loathe to add all of kde's stuff, but I might need to in the name of troubleshooting.

---

### Post by twilightomni on 2007-10-22
That link is very interesting.  I don't know if it fits my case -- I don't want to host shared folders under Ubuntu, merely access another Windows' PCs shares.

But the article does mention something about "setting up NetBIOS name resolution using Samba" so you don't have to access every computer by IP address only.  I wonder if that might be relevant to my problem.

That would make me surprised that this isn't setup correctly by default.  Not much good for the casual user to be able to see Windows shares without being able to access them except only by IP...which is very much unintuitive.  I'm guessing the average home network user doesn't know much about NetBIOS and WINS either.  I sure don't, but guess I'll learn a thing or two.

The other guess is that _maybe_ it is a Nautilus problem.  I plan to try out Kubuntu, so I'll see what happens.

Still...not everyone seems to have this problem.  I wonder why there is a specific group of people for whom accessing shares in Nautilus by Network doesn't function properly.

---

### Post by Cryophallion on 2007-10-23
I gave it a half hour in kde. Nothing to see there.

So, it looks to be an underlying problem, and I'm running out of ideas.

---

### Post by Cryophallion on 2007-10-24
So, I had problems uninstalling the kubuntu packages, as they did not autoremove once the meta package  was deleted. Plus, I wanted to do another test of the install as I am about to install it on a friends comp. 
Therefore, I reformatted and re-installed... and the network shares show up just fine now.

I have no idea why it didn't work before. I will have to check my desktop at home and see if it is working now also. I'll update you all later.

---

