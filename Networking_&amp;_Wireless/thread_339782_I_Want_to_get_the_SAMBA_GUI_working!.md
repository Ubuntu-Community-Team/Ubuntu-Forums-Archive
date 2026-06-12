---
title: "I Want to get the SAMBA GUI working!"
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by msimon1960 on 2007-01-16
](*,)   Samba configuration is a serious problem - even setting up a simple share seems to be accidental if you get it working at all.

I've been working on it fairly diligently for a little over 6 weeks now and really dove into it this weekend (I'm like a dog with a bone) -- haven't run into anyone yet that seems to be able to make it work on demand yet.  So far I've got about 160 hours invested in setting up a simple share -- the most miserable experience with networking since Win95.  Even my first experience with Novell 2.2 was easier than this.

Here's what I've learned so far --

1. the smb.conf sharing is dependent on the issuance of chmod commands to set access.  If you use smb.conf without this preconfiguration none of the writeable/read-only commands will function.  Could someone with more knowledge and experience with the linux security system describe what needs to be done in preparation for smb.conf command to function.

Without some pre-configuration the following smb.conf command are not functional:
'writeable =' 
'readonly = '

2.  Samba seems to be dependent on some subsidiary system for name resolution -- I found installing winbind before samba seem to help samba with name resolution but it's very slow to respond when browsing.  Most problems with Samba seems to revolve around WINS name resolution.  Could someone with more knowledge of the interaction between WINS and Samba outline which modules need to be installed and how they should be configured?

Without some pre-configuration the following smb.conf commands are not functional:

'browseable ='
'public = '
'available = '

3.  I notice most everyone writing on the topic uses 'browseable' whereas the GUI generates 'browsable' -- a typo?

If the community will help my objective is to develop a HOWTO intended to reliably network computers WITHIN the limits of what was obviously intended within the Ubuntu GUI in a mixed Ubuntu/Windows environment.  This should satisfy most home and SOHO users.  Most of the other guides get into complex networking / security scenarios that are the domain of system administrators and beyond the scope of the basic GUI provided by Ubuntu.  All most of us need is what seems to be intended by the GUI.

My secondary objective is to pull this together and provide it to the SAMBA team to address in their next stable release.  I consider the ability to network computers probably the most critical component of any OS and I'd like to help get it working properly.

====================================================

I would ask that Linux experts responding to this post be guided by the following premise:

1. The absolute minimum number of terminal commands are to be used.  A perfect score is zero terminal commands.  When providing instructions please reference the Ubuntu 6.10 user interface wherever possible.

2.  Take a look at the GUI provided in Ubuntu 6.10.  None of it is functional out of the box -- if anyone doubts this do a clean install -- be honest about it :-D -- no terminal commands and no installing anything other than the default setup with the updates applied.  The objective is to get the SAMBA GUI to function with the minimum number of terminal commands.

3. What are the minimum installation packages required to get WINS to function within the context of SAMBA and how should they be configured?  The ability to browse the network from Ubuntu or Windows machines is required.

4. What are the minimum installation packages required to set permissions within a WINS/Samba context?  How are they configured?  Again, the guiding principal is the minimum number of terminal commands required for the GUI to function as intended.  Full R/W access to the shared folder is required.

5. Printing is not an issue -- I just want to get file sharing set up as a discrete item.

6. In documenting your answers use the following conventions -- 

Machine and netbios names are: MyServer, Workstation1
User names are: admin and jdoe

I, and the thousands of us struggling with SAMBA thank you in advance.

Matt.

---

### Post by dbott67 on 2007-01-16
This thread ([http://www.ubuntuforums.org/showthread.php?t=280473](http://www.ubuntuforums.org/showthread.php?t=280473)) has the techniques I have used in getting my home network sharing (NAS device, Win XP, OSX and Ubuntu).

The key packages are:

- **smbclient **& **smbfs** (the client and filesystem for SMB networking)
- **winbind** (WINS server for name resolution) or **bind** (if you want to run your own nameserver; not generally needed or recommended for home/soho networks or for the faint or heart)

The Windows firewall (or ZoneAlarm, Norton, McAfee and 400 other personal firewalls) may also cause problems as they will be blocking ports 137-139 & 445, which are needed for sharing.

-Dave

---

### Post by msimon1960 on 2007-01-16
Hi Dave,

Thanks for responding.

I checked out the thread you suggest -- I think i read it before during my research.  LinNeighborhood is exactly the kind of GUI need for the configuration of SAMBA.  I'm going to use it from now on.

winbind, smbclient, and smbs are all installed on the server.

I tested your suggestion against my out-of-the-box Edgy 6.1 setup.  Totally no go.  The server couldn't even find itself without painfully long delays in the browsing -- it would eventually work but I had to click on each icon in the tree, clear the error dialog, and keep doing that until the system finally identified the resource.  The response time is too slow to be practical.

Here's the challenge at this point --

1. Name resolution is the problem and is it possible that the SAMBA implementation of WINS may the culprit?  

2. Maybe SAMBA may require something more than winbind for WINS support?

3. Maybe winbind needs additional configuration beyond the default setup (e.g. nsswitch.conf)?

I'm going to do some reading on WINS within Linux and specifically anything on WINS/SAMBA interactions.

Matt.

---

### Post by dmizer on 2007-01-16
for name resolution:
Edit your nsswitch file
```
sudo nano /etc/nsswitch.conf
```

search through the file and look for the line that looks something like so:
> hosts: files dns
and add "wins" to the end of the line so it looks something like this:
> hosts: files dns wins
Save the file by hitting ctrl+x, type "y" to save the buffer, and <enter> to exit.

Now you'll need to install winbind
```
sudo aptitude install winbind
```

Reboot, or restart your network.

sorry, there's just no good way (that i'm aware of) to get this done without using cli ... obviously replacying gksudo gedit would eliminate cli text editing, but gedit is gnome specific.  is there a universal gui text editor?

---

### Post by all4linux on 2007-01-17
I too am trying to get a local area network established with my ubuntu machine. I have just loaded ubuntu 6.10 on one of the machines that I have attached to my private windows network. The same machine previously was set up to dual boot into Windows 2000 and Xandros Linux, Version 3. I had no problems with file sharing under either operating system.
My current network has three computers. One runs Windows 2000 all the time, one runs Xandros Linux, and the third is running ubuntu 6.10. I am having the following problems.

1. similar to you, when I click on:
places - network servers - windows network
I get a folder named 'mygroup' (the group name for my windows workgroup). If I doubleclick this folder, it will not open, but gives me an error box...
'Couldn't display "smb:///mygroup" '
If I get rid of the error box, I have a 30% or so chance that the folder labeled 'mygroup' will be replaced with a computer icon with the same name. If this happens, I can then double click on it, and then I can (sometimes) access the other two computers in the 'mygroup' workgroup. Sometimes, however, these computers show up instead as empty folders, in which case, if I doubleclick one of them, I get an error box similar to the first one. This is very frustrating.

2. On my Ubuntu 6.10 computer, I tried to share a large backup drive named /media/hda6, by the following gui method - click on:
System - administration - shared folders - add

At about this point, since this was the first time I had tried to share a folder, Ubuntu automatically downloaded and installed Samba on my system... very impressive...
When it was done, I got back to the same place, but this time when I clicked the 'add' button. it allowed me to share /media/hda6. I unchecked the button for read only, because I wanted to share the drive so other computers could use it to backup their data files.
Everything up to this point was very impressive, but......
When I tried to access this drive on the windows network, from my windows 2000 computer, I get the error message, "\\ubuntubox\hda6 is not accessible.  Network access is denied.
In addition, I got no such message when accessing the share from my Xandros box, but I could not read any of the contents of the drive, and could not write to the drive either.
Going back to the ubuntu machine, I tried to browse to the network share that I had created, and I could not gain access to the drive using ---
places - network servers - windows network - mygroup - ubuntu - hda6 
The first time I tried, it asked me for a username and password, to which I entered my paramaters, and got an access denied message. When I subsequently tried accessing the drive in the same manner, the error was...
'folder contents could not be displayed. You don't have the permissions necessary to view the contents of "hda6" .'

Having worked on the ubuntu machine for 3 days trying to get sharing to operate properly, I have become frustrated. I've tried following the example given at this url:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_share_public_folders_with_read.2Fwrite_permissions_.28Authentication.3DNo.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_share_public_folders_with_read.2Fwrite_permissions_.28Authentication.3DNo.29)
this involves editing the smb.conf file. I had no luck with that either.

I would like to join msimon1960 in challenging the ubuntu gurus to get local area networking up and running, even if it takes some editing of the smb.conf file to do so, at least as a work-around while we wait for a new release to come out with the gui methods repaired. While I am very impressed with ubuntu, not having file sharing working is a festering issue with me.

Dick.
[email]linux4all@bergerweb.net[/email]

---

### Post by dmizer on 2007-01-17
all4linux -

ubuntu's default configuration for sharing is configured with password protected access.  this can be disabled by following the directions in this post: [http://www.ubuntuforums.org/showpost.php?p=2024123&postcount=2](http://www.ubuntuforums.org/showpost.php?p=2024123&postcount=2)

now, keeping in mind that ubuntu defaults to password protected shares, if you tried to sign in to your ubuntu share with your ubuntu username and password from a remote windows computer, this will not work.  your remote windows computer must have an account with a separate username and password on your ubuntu box in order to access the share.  this username and password should match the one you use to log into your windows computer.

side note ... password protected windows shares operate the same way.

furthermore, msimon1960 is not challenging the guru's to get this working (ex, pointing at a non-functional file share and saying, "wtf dude, it don't work ... you better fix it").  msimon1960 is attempting to work toward the resolution individually ... presumably with the idea of presenting a workable solution to the "gurus" (ex. saying, "wtf dude, it don't work ... wonder what i can do to correct that?").

until then, you can follow the directions in the first two links in my signature to get a fully functional two way ubuntu peer to windows peer network established.

---

### Post by all4linux on 2007-01-18
Thanks, dmiser, for the reply, and the two links. I haven't yet tried to implement either of the solutions, but they look quite helpful, especially the first link, which give a complete smb.conf file which should work.

You pointed out that ubuntu defaults to password protected shares, which I found out early in my quest to get sharing working. From the reading I have done, I haven't yet figured out how to create share accounts on the ubuntu box, so I have tried to modify my smb.conf file to allow non-password- protected shares. I thought that this could be done by changing the global parameter...
security = user
to...
security = share.
Apparently there is more which needs to be done to accomplish this, and currently I'm trying to figure out what it is by reading the man pages for smb.conf.
I mentioned that I have another linux machine on my network which is successfully sharing drive partitions with windows machines. I'm currently comparing the options included in share definitions of it's smb.conf file with the ones given in the howto that you furnished a link to. (they aren't the same, of course.) It's beginning to appear that there are a multitude of ways to accomplish the same thing under Samba, and I'm going to need a much better understanding of the program to figure out how to set things up so they are easy, yet secure.

Finally, I would like to clarify that I did not mean to be derogatory about the work of the "gurus" on this project. By "challenge" I meant simply to evoke further discussion within this forum, and join with msimon1960 in asking for any additional helpful information toward his stated purpose. Also, I hope that by pursueing my personal objectives, I will be able to contribute to his effort.

---

### Post by msimon1960 on 2007-01-20
What I'm gathering from this, and other threads is that people are coming at this from different starting points which creates all kinds of problems coming up with standard documentation.

As a starting point I've started with section 5 'Windows Networking' of the the official Ubuntu documentation at:

[https://help.ubuntu.com/6.10/ubuntu/serverguide/C/windows-networking.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/windows-networking.html)

I've started with a clean install of 6.06 LTS Desktop.  My assumption is that if we can get 6.06 properly documented then a 6.10 user can probably figure it out.

I'm taking a tedious, methodical approach to working through the documentation.  It's too much documentation to post here so I'll post the document in html format as each problem is overcome with community support.

I'm a total newb to the Ubunutu community -- I hope this is an acceptable approach.  If there is a more efficient method for a group to work on resolving a problem please let me know.

Matt.

---

### Post by dmizer on 2007-01-20
the ubuntu wiki [https://help.ubuntu.com](https://help.ubuntu.com) has provisions for documentation in progress, and documentation proposals, so it seems to be as good a place as any to dump raw documentation for peer review and editing/testing.

this is probably something that should be put forward to the ubuntu documentation team, and coordinated either through this thread or the ubuntu wiki.  beyond that, this is the first official doccumentation project that's generated any interest for me, so i'm here to learn the ropes too.

as a last resort, i could have a wiki environment set up on my home server as a stand in, but i doubt that'll be necessary.

also, i am preparing a box to be dedicated to this project, so if you need anything let me know.

---

### Post by all4linux on 2007-01-23
dmizer and msimon1960,
I just wanted to let the two of you know that I too am interested in seeing the GUI for SAMBA working, and also to throw in a tidbit of information about the problem I was having before dmizer's help.

I was trying to share a large windows fat32 drive on my windows network, and could not get it's contents to show up on either my Xandros Linux computer, or my Windows 2000 computer. I had tried just about every method suggested by the Samba how-to's and the Ubuntu forums, when I finally found the answer to the problem, and it wasn't a Samba problem at all.

It turns out that the default installation for Ubuntu will mount all existing windows partitions in such a manner that they are read/write enabled for local users, but not for shares. In order to correct the problem I had to edit the file /etc/fstab so that it would allow shares to read/write the drive. the line in fstab which controls the mount of my big windows partition looked like this:

# /dev/hda6
UUID=1865-1DC1  /media/hda6     vfat    defaults,utf8,umask=007,gid=46 0       1

the umask option blocks the 'others' group from reading or writing the contents of the mounted drive. Once I changed this to umask=0, I was able to see my shared drive on all the other computers on my network.

I just wanted to add this to this thread in case anyone else is having similar problems sharing a windows fat32 drive over samba.

---

### Post by msimon1960 on 2007-02-04
It's been a while since I've posted here -- haven't forgot -- just really busy with work.

In the interim I've been installing 6.06 and working through the official documentation.  A very tedious process to be sure since I've found at least 8 material errors in the documentation in the first 3-4 pages of documentation.  Not simple typos but commands that are just plain WRONG!

After working through each syntax error I've installed a clean system of 6.06 and started again.

I've reached an impasse on two fronts:

1. Name resolution doesn't appear to function.  Winbind installed and the smb.conf file are configured to use this computer as the Samba server.

Result: The workstation doesn't seem to be able to connect unless I bang on the browse leading to my shared folder.  It really has trouble resolving the name for the server.

2. Even when I pound my way to the shared folder I can't do anything with it.  It appears to be permissions problems -- insists I'm not the owner of the shared folder and access is denied.  The whole linux security system is soooo anal it's unusable.  Setting permissions using the gui is useful -- it doesn't appear to have any impact on actual functionality.

I'm throwing in the towel.  It's cheaper to buy a copy of WinServer 2003 then to invest hundreds of hours for a dubious outcome.  I'm not trying to be a troll.  It's simply that Samba is too complex, poorly documented, and unstable for use.

That having been said I'll continue to watch the documentation section.  If the documentation team can provide clear, accurate instructions on setting up a simple one-folder SAMBA share on 6.06 I'm willing to give it another try.

Matt.

---

### Post by msimon1960 on 2007-02-04
> **dbott67 said:**
> This thread ([http://www.ubuntuforums.org/showthread.php?t=280473](http://www.ubuntuforums.org/showthread.php?t=280473)) has the techniques I have used in getting my home network sharing (NAS device, Win XP, OSX and Ubuntu).

The key packages are:

- **smbclient **& **smbfs** (the client and filesystem for SMB networking)
- **winbind** (WINS server for name resolution) or **bind** (if you want to run your own nameserver; not generally needed or recommended for home/soho networks or for the faint or heart)

The Windows firewall (or ZoneAlarm, Norton, McAfee and 400 other personal firewalls) may also cause problems as they will be blocking ports 137-139 & 445, which are needed for sharing.

-Dave

All the packages you listed were installed.  I disable the firewalls on both computers -- still nothing.  Glacial name resolution and apparently infinite permission issues that I couldn't overcome.  'One big share' for everyone on my LAN is still just a dream!

---

### Post by Erlander on 2007-02-04
Parts of the requested GIU are in System/Administration/Shared Folders and in System/administration/Networking.

I found that by altering some of the settings in the Shared Folders item I was better able tho get the required result.  It altered my smb.conf

Now I can browse the mounted folders on my XP pc from the Ubuntu pc and from the XP pc I can browse the shared folders in my Ubuntu pc.  Videos on either pc can be played on the other across the network.  Thank you DMizer.:KS 

With XP Home I find the browsing of XP Shared folders the hardest to set up.  I think it is the fault of XP home.  We also have an XP Pro laptop that connects to the network by wireless and it is much easier the set up to browse its shared folders.

Rob

---

