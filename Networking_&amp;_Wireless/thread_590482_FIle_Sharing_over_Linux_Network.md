---
title: "FIle Sharing over Linux Network"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by t2000kw on 2007-10-24
I've read through some of the posts regarding file sharing over a Linux network. They don't explain how to name the workgroup or where to put this information, what the server is--is it the ISP or one of the two computers on the network???, how to do this with a DCHP network at  home (not at work) where a router assigns the IP addresses, how to get the IP address of the router, and much more that is just glossed over, assumptions made that the new person will understand, etc. 

There is ONE Windows PC on the network that I MIGHT need to connect with at some time in the future, but for now, all I need to share is my email program folder's files so I have an exact duplicate on my newly installed Gutsy desktop. 

In the process of upgrading, my /home partition was trashed. I hadn't backed it up since I had a lot of faith in the upgrader, which I shouldn't have. That won't happen again now since I have an extra partition the same size as my /home partition, so I can simply back up /home every so often, especially before the next upgrade. But I digress, as this is not about a partly failed install. 

If there is an article somewhere that doesn't make assumptions and doesn't overlook the fact that some of us don't know where to put some of the information mentioned in other articles, I would be happy to look it over. If I had a burner in the other laptop PC I would just burn the files to a CDROM and copy them with a sneakernet connection. 

When I went from Windows to Linux I shared the files over the network and burned a CD before I switched one to Linux. This time, though I have an XP (dual boot on this desktop) installation available, I want to network two Ubuntu PCs (one Dapper, one Gutsy). 

If I can throw in support for the third computer (a Windows laptop), so much the better, but if it's simpler to do Linux to Linux, let's try that first. Though I was able to print from my Windows laptop through my Feisty desktop (now Gutsy) before. Somehow I accidentally set up printer sharing correctly but I couldn't get file sharing between Windows and Linux working. Go figure!

I have done some research and tried some things, unsuccessfully, before resorting to a post in this forum. 

I realize it's either NFS or Samba--is one easier than the other to set up? Do I have to have a Windows PC to use Samba?

I'm not looking for a re-write of something that's already out there, but let's face it, if you have lots and lots of hits on a web or forum search, it's possible that the exact thing you need was on the next page after giving up on finding a suitable answer.

Thanks in advance,

And if someone is willing to talk me through this, I might be able to record and then transcribe the recording for an article (or not--just an idea). A talk-through would be nice, but I can work through a forum or by email since I do most of my Ubuntu fixes by email with someone (who unfortunately has very little networking experience, but is very helpful in other Ubuntu matters). 

Donald

---

### Post by eugo on 2007-10-24
Sounds like quite the trouble.

Samba is the way to go. It can do linux->windows and linux->linux file sharing. When I moved to Ubuntu I had trouble with special-language characters messing up filenames when transfered between computers (I was using SCP and FTP), I finally figured out that Samba preserves true Unicode support. That means that you can copy a filename with any special character between computers running different OS's!

First, make sure you have the following packages (Synaptic Package Manager):

```

samba
samba-common
smbclient
smbfs
winbind
```

Next we edit the samba config file. Type in terminal:

```

sudo gedit /etc/samba/smb.conf

```

I had to add 'netbios name = ' to the config. Make sure it's there. Change the following:

```

netbios name = <your-hostname>
announce version = 5.0
workgroup = <your-workgroup>
wins support = yes
name resolve order = lmhosts host wins bcast
security = user

```

You can change everything else to your liking. The config file has lots of documentation. Find your hostname by typing: 'hostname'. At the bottom of the config file you can enable user home shares (the [homes] section). If you want to add your own share, add this to the bottom of the config (eg. a upload folder):

```

[Upload]
	path = /home/user/Upload
	comment = Upload folder
	valid users = yourusername
	writable = yes
	guest ok = no

```

After saving smb.conf, you should restart the samba server, by using this command:
```

sudo /etc/init.d/samba restart

```

When you connect to the share, you have to supply a username that exists on the computer you are connecting to. You can change this by changing "security = share" in the smb.conf file (see 'man smb.conf'). To enable a user to connect to the share, you have to add him to the samba userlist:

```

smbpasswd -a yourusername

```

For more info about the userlist, type 'sudo pdbedit -Lv your-user-name'.

You should now have set up samba. How to use the share?

For a single connection, on a Windows machine, go to My Computer and type in the address bar: \\hostname or \\ip-address . Supply your username and password you supplied with the 'smbpasswd' command. You can also use My Network Places to browse for the computer.

For a permanent connection, you can go to My Computer -> Tools -> Map Network Drive, and put in "Folder": '\\hostname\sharename'. Click on "Connect using a different user name" and supply your username and password.

To do this the command line way, go to Start -> Run -> cmd -> Ok. Type in:

```

net use x: \\hostname\sharename /user:username

```

You now have a new drive letter X: (or any available letter. Use * instead of x: to select the next-available drive letter) of the freshly created share. After next reboot you should only need to enter your password when using the share.

If you specified 'guest ok = yes' in the smb.conf, you should not need to enter a username or password. If you do, try enabling the Guest user on the Windows computer.

On Linux, you can either use the windows manager like Nautilus or Konqueror (type smb://computername in the address bar) or you can use the command line like in Windows:

```

sudo mount -t cifs //netbiosname/sharename /media/sharename -o username=yourusername,password=yourpassword,iocharset=utf8

```

For get more acquainted with samba, make sure you read the following man pages:

```

man samba
man smbclient
man smb.conf
man 5 passwd
man smbpasswd
man 5 smbpasswd
man pdbedit
man smbtree

```

One thing i'd like to point out is this: If you are having trouble connecting to any computers, make sure the following ports are open on both computers:

```

137
138
139
445

```

If you use iptables or Firestarter you might need to configure them to open these ports.

Please also see these links:

[http://gentoo-wiki.com/HOWTO_Setup_Samba](http://gentoo-wiki.com/HOWTO_Setup_Samba) <-- A detailed text about Samba for Gentoo Linux, provides good basic info.
[http://www.swerdna.net.au/linhowtosimpleshares.html](http://www.swerdna.net.au/linhowtosimpleshares.html) <-- An introduction to the more recent Samba 3.0 (used in Ubuntu)
[http://www.cyberciti.biz/faq/access-windows-shares-from-linux/](http://www.cyberciti.biz/faq/access-windows-shares-from-linux/) <-- Shows you how to mount shares at system boot.
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534) <-- This is a more in-depth guide. Take a look.

Good luck.

---

### Post by t2000kw on 2007-10-25
Thanks. I'll try to tackle this on the weekend, 

This looks a lot simpler than what I've seen so far, and I don't have to be concerned about my floating IP addresses, just the hostname. 

If I add my /home directory, will everything "below" that folder be available and browseable on the other computer?

---

### Post by t2000kw on 2007-10-25
I got one system set up already--found some time this evening to do that. Made some mistakes but figured out that the password part is done with SUDO in a terminal, not by adding lines to the Samba file, but that's just my newness to this and it wasn't too difficult to figure out. 

One question--once set up, how do I log into the other computer, browse files, etc.? Is there a program that I need to use, do I have to use the /mount command somehow, or some other method?

I have it set up right now to share /home/[myusername]. If I can only see that folder and not below it, I'll need to change this to /home/shared and dump everything that needs shared into that folder. Otherwise, it will be a piece of cake, once I get connected and can see the folders I need to transfer, to set up my email program the way it is on the laptop.

One nice thing about this is that I can see many possibilities, like backing up my laptop Ubuntu installation onto a large unused partition on my Windows drive, and the same for this installation. I have LOTS of room there, enough to back everything Linux up and even my wife's Windows laptop, which could come in handy when I move up to another laptop and give her mine. I should be able to set her up a Windows machine by restoring her files to a blank drive. At least, that would be nice if I can.

---

### Post by Robocoastie on 2007-10-26
Eugo thanks for that! I was having a heck of a time getting my 7.10 rig to share a folder anonymously. Now it works! Now to just solve the mythtv problem...

Rob

---

### Post by t2000kw on 2007-10-26
I set the second computer up. I On the desktop I can see "myself" but not the other computer. I'm missing something here. I'll work some more on it this weekend and see if I missed something.

---

### Post by eugo on 2007-10-26
You are both most welcome.

I made some minor changes to the guide, adding 'winbind' to the packages (used to lookup windows names), I also removed the command 'smbpasswd -e yourusername', it should not be needed. I also added a section on how to connect to the shares. There is also a links section on the bottom.

[quote=t2000kw]
I have it set up right now to share /home/[myusername]. If I can only see that folder and not below it, I'll need to change this to /home/shared and dump everything that needs shared into that folder.
[/quote]

If you add /home/username as a share, any folder below it (like the other /home folders) won't be accessable.

If you need all the /home directories to be shared and want each user only to be able to access his/her home directory, uncomment the '[homes]' section in smb.conf. Read the comments to tweak it to your own preferences.

If you want all the /home directories to be shared and want every user to be able to access other users accounts, you must use 'chmod' to change the permissions on the directories. See 'man chmod' and google a bit to find out how to use it. Check out [this page](http://www.javascriptkit.com/script/script2/chmodcal.shtml).

---

### Post by t2000kw on 2007-10-26
You mentioned a guide that you made changes to. Is it one of those 4 links in your original post?

I'll check out the man pages and the link, but only after I resolve a more serious problem that has noting to do with the general setup.

I am getting errors trying to install Samba on my Dapper notebook computer. I got an error right after trying to install it with Synaptics telling me there were errors during install. I marked it for complete removal, then reinstalled it, and now I get a different message. And, when I run an update for other programs now (they might be related to Samba, not sure), I get a message about an erorr with Samba, so some of my problems might be a corrupted Samba installation. Not sure, though. The latest error message is below this post.

I'm wondering if I dare upgrade this notebook to Gutsy since it has only a 300 Mhz processor. And, if I do, can I keep my /home partition from being overwritten? (I plan to ask about these two questions elsewhere, but I thought I'd mention where I am with this networking thing. I think I'll try using a zip drive for my file transfers in the meantime, provided that both computers will recognize the USB zip drive, and if I have enough disks (I only have about 35 100 MB disks). 

------------------------------------------------------------------------------------------------------------
Here's the latest error message:

E: /var/cache/apt/archives/samba_3.0.22-1ubuntu3.3_i386.deb:
subprocess new pre-removal script returned error exit status 102

---

### Post by eugo on 2007-10-28
The guide I made changes to was the one on this thread.

Maybe the package database is corrupted or something, you seem to be quite unlucky with your notebook. I'd probably keep the /home partition (if it's worth keeping) and reinstall ubuntu.

It's a 300mhz processor? Pentium 2? Have you considered Xubuntu?

---

### Post by t2000kw on 2007-10-29
Yes, this is a slow computer. I tried xfce with the live CD but it wouldn't recognize my network card. I like Gnome but might consider setting up another Gnome-compliant window manager like IceWM, After Step, Fvwm2, or Windowmaker. I've tried Enlightenment and don't care for it all that much, and it didn't seem to speed things up much over Gnome's deafult Metacity. Hopefully, I will be able to replace this laptop sometime soon, but other financial matters are more pressing right now.

I reinstalled Dapper after having problems with Gutsy working with a combination of my Windows email program (Agent) and Crossover Office. It installs Crossover OK but every time I tried to install Agent it froze up. It doesn't on the fast desktop computer, though, and works fine. So I'm back to Dapper.

Which leads me to good news (for a change!). After installing Dapper and before running any updates or installing anything at all, I installed Samba, and it went perfectly this time. So I'll be looking back at this next weekend (maybe sooner) to see if I can set it up for networking. For now, I use a 2 GB USB thumb drive for my "sneakernet" setup. 

I did notice that Samba is not installed by default but there are samba-related programs that were already installed with the OS. Why would they be there already but not the main program?

---

### Post by bbrand on 2007-10-30
Please note guys and gals: Samba shares have a maximum side of 2GB. That means if you want to share movies, backups etc across your network you will run into this limitation. 

For this reason I moved to FTP for internal Linux shares on top of Samba for setting up user shares and drive mapping for Windows PC's.

---

### Post by t2000kw on 2007-10-30
Assuming I can get Samba working (hopefully this coming weekend), can you recommend any good how-to's for beginners on the subject of using FTP with Samba?

---

### Post by eugo on 2007-10-31
> For this reason I moved to FTP for internal Linux shares on top of Samba for setting up user shares and drive mapping for Windows PC's.

Do you know a solution to copying files with special characters between systems? I tried various FTP servers and clients, SCP didn't work either. I got it working by using a program called Febees Backup (febees.com) by forcing UTF-8 encoding, I could connect to a FTP server and copy my files without screwing up the filenames.
> 
Assuming I can get Samba working (hopefully this coming weekend), can you recommend any good how-to's for beginners on the subject of using FTP with Samba?

I don't think you use FTP with Samba. I tried proftpd and pureftpd, pureftpd has user home shares on by default when you install it, so there's minimal configuring. There are numerous guides on the forum on how to setup a FTP server.

---

