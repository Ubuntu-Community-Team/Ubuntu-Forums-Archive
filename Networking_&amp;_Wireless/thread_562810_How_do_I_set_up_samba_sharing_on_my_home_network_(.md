---
title: "How do I set up samba sharing on my home network? (yes I've searched)"
date: 2007-09-29
forum: Networking &amp; Wireless
---

### Post by Haute Pie on 2007-09-29
I have a home network, it originated as a windows network and has metamorphosed through mac/windows and now it is mac/windows/linux.

I now almost exclusively use mac and want to use this old (now ubuntu) pc as a place to store all my media. Since I want to occasionally connect via windows, and because it's easy with mac anyway, I want to stick with samba.

I am a total linux novice so please bear this in mind before rattling off a list of arcane commands - I'll need to know where to type and when to press enter, really, I'm THAT clueless. I have not been able to follow any other posts enough to know if they are even solve the same problem I have, so apologies for the undoubted repost that this is.

I am running feisty fawn, and also installed kubuntu for a test, but now run it in gnome evironment - essentially I think I have KDE underneath now? I'm sure you'll know.

I have shared a folder on ubuntu using samba (by right clicking and going through the obvious motions). The shared folder is called 'share' in my ubuntu home. The ubuntu computer is called, 'Ubuntu'. I have followed instructions from somewhere else here to install samba and other bits and pieces needed.

So in my mac, as I would usually to join a samba network (previously always to a windows machine) I click [go>connect to server>browse] and select my home network (still called MSHOME from back in the day) and lo, there is a familiar network icon and it has the label 'Ubuntu'. Hooray. Actually no, for the icon is, ominously, greyed out. Bravely and courageously, I throw caution to the wind and I double click it to see if I can select a share anyway. I can! there in the dropdown list is 'shared'. I select it ... 

"the alias Ubuntu could not be opened because the original item could not be found"

Bugger.

I would appreciate any help very much.
Thanks in advance.

---

### Post by dbott67 on 2007-09-29
I've posted a few times about samba & file sharing and have basically just cut & pasted an old response (so excuse the background stuff about DNS vs. WINS & what-not).  I've got a few other related posts that might shed a little light on the inner workings here:
[http://ubuntuforums.org/showthread.php?p=2745863](http://ubuntuforums.org/showthread.php?p=2745863)

Here's my little HOWTO:

Install the following packages from the repos:

```
 sudo apt-get install samba smbfs smbclient winbind
```[U][B]

BACKGROUND

[/B][/U] (This is from another thread that I posted in regarding local name resolution. The full thread is for here: [http://www.ubuntuforums.org/showthread.php?p=1770797#post1770797](http://www.ubuntuforums.org/showthread.php?p=1770797#post1770797))

... some issues arise because of the way SMB shares "announce" themselves to the network. Generally, connecting via IP address works properly, but browsing by 'computer name' can occasionally fail. Windows uses WINS service to allow users to browse by computer name (also known in Windows-speak as Netbios name). WINS binds the computer name to the IP address. For the most part, this has been superceded by DNS, which binds the fully-qualified domain name to the IP address. The problem is that DNS resolution requires that:

a) You're running a DNS server (locally)
b) Each client is registered in the DNS server

The problem here is that most people don't run their own DNS server at home and if you have any Windows computers on the network (or Samba shares), you really should have a WINS server installed.

There is a package in the repositories called 'winbind' that is a service that resolves user and group information on NT-based networks and also allows you to browse by computer name.

This info is provided by 'featherking' from [this thread]("http://www.ubuntuforums.org/showthread.php?t=288022"): 

```
sudo gedit /etc/nsswitch.conf
```find this line (it may not be exactly that)

```
hosts:          files dns mdns
```and add wins, so now it looks like

```
hosts:          files dns mdns wins
```then install winbind
```

sudo apt-get install winbind
```The advantage to using winbind vs. static IPs is that I can add/remove PCs without worrying about editing the hosts file. There are also a few tools that can aid in discovery:
```
dbott@thedrake:~$ sudo smbtree
Password:
WORKGROUP
        \\THEDRAKE                      thedrake server (Samba, Ubuntu) *[COLOR=Blue]<--- My Dapper desktop[/COLOR]*
                \\THEDRAKE\ADMIN$               IPC Service (thedrake server (Samba, Ubuntu))
                \\THEDRAKE\IPC$                 IPC Service (thedrake server (Samba, Ubuntu))
                \\THEDRAKE\dbott
                \\THEDRAKE\print$               Printer Drivers
        \\PIII-600 [COLOR=Blue]*<--- the kids XP PC; no firewall; no shares*[/COLOR]
        \\OMEGA-XP [COLOR=Blue]*<--- My laptop; Running XP firewall*[/COLOR]
Error connecting to 192.168.1.105 (No route to host)
cli_start_connection: failed to connect to OMEGA-XP<20> (192.168.1.105)
        \\NAS-160GB [COLOR=Blue]*<--- My NAS device*[/COLOR]
                \\NAS-160GB\IPC$
                \\NAS-160GB\Videos
                \\NAS-160GB\Music
                \\NAS-160GB\Archive
                \\NAS-160GB\Data
                \\NAS-160GB\PUBLIC
        \\JBOTT-PC [COLOR=Blue]*<--- My wife's laptop; Running Vista firewall; no open shares*[/COLOR]
timeout connecting to 192.168.1.101:445
timeout connecting to 192.168.1.101:139
Error connecting to 192.168.1.101 (Operation already in progress)
cli_start_connection: failed to connect to JBOTT-PC<20> (192.168.1.101)
dbott@thedrake:~$

```All of the discovered data is stored in **var/cache/samba/browse.dat**:
```
dbott@thedrake:~$ cat /var/cache/samba/browse.dat
"WORKGROUP"               c0001000 "THEDRAKE"                    "WORKGROUP"
"THEDRAKE"                40059a03 "thedrake server (Samba, Ubuntu)" "WORKGROUP"
"NAS-160GB"               40412003 ""                            "WORKGROUP"
"OMEGA-XP"                40011203 ""                            "WORKGROUP"
"JBOTT-PC"                40001003 ""                            "WORKGROUP"
"PIII-600"                40011003 ""                            "WORKGROUP"

```After installing samba, winbind & smbfs, you need to configure samba and add your Windows XP accounts to samba, where *[COLOR=Blue]username[/COLOR]* is the login name of your Windows XP computer (use the same password for both accounts)
```
sudo  smbpasswd -a [COLOR=Blue]*username*[/COLOR]

New SMB password:
Retype new SMB password:
Added user username.
```For more information, please read this document:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

-Dave

---

### Post by alsehendo34 on 2007-09-29
Quit kicking yourself in the head use NFS supported by OSX and Linux alike.

If you still have a windows box in there.

Set up samba server make sure the workgroup name in the configure file  [http://samba.netfirms.com/sambconf.htm](http://samba.netfirms.com/sambconf.htm) 
Manually configure your shares in the same config file

Start the smb server somehow
smb start
smb stop

At this point you should be able to see the samba server from any windows system in the same workgroup but you won't be able to access the share; not until you add the user(s) on the server.
Adding users to samba  [http://www.comptechdoc.org/os/linux/manual4/sambausers.html](http://www.comptechdoc.org/os/linux/manual4/sambausers.html)
[root@server2 samba]# smbpasswd &#8211;a agustin
	New SMB password: ********
	Retype new SMB password:********

Mac OS X users can connect to a Windows share using the built-in Samba client. Samba uses the native Windows file-sharing protocol SMB (Server Message Block), which lets the Mac connect via IP using a Windows-native protocol.

Look here on how to use client from OSX to connect to Samba server on Ubuntu---rember to use username/password you set up when adding user above!!!!
[http://www.networkcomputing.com/channels/storageandservers/showArticle.jhtml?articleID=26806360](http://www.networkcomputing.com/channels/storageandservers/showArticle.jhtml?articleID=26806360)
OR JUST:
Try mount an SMB / Samba share from the OS X command line  
[http://snipplr.com/view/2580/mounting-samba-share-from-osx-terminal/](http://snipplr.com/view/2580/mounting-samba-share-from-osx-terminal/)
# I usually create a dir inside /Volumes before mounting
mkdir /Volumes/mntpoint
mount_smbfs -W workgroup //user@SERVER/folder /Volumes/mntpoint

---

