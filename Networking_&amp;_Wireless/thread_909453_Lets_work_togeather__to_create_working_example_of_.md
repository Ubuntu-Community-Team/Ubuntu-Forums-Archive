---
title: "Lets work togeather  to create working example of peer-to-peer browsing setup"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by gregphil on 2008-09-03
I have been trying for a week to get ubuntu to do real browsing of Windows Shares, i.e. to do peer-to-peer sharing of files.  I have not succeeded.  I actaully think gnone is "broken" but maybe someone can prove me wrong by helping create a full working example of how to do "normal" samba file sharing in a simple network with NO SERVERS!.   (This 'just works' under Windows)

I don't want any servers because I have about 8 computers and none of them are left on all the time (energy savings...).  About half of them are Windows Xp, two are CentOS and two more are ububtu/kubuntu.  The Windows boxes and the CentOS-KDE machines can "see" each other and do full share browsing.  I do NOT need to tell a machine where to look for a specific share, it actually "browses".  I could not get CentOS and gnome to do GUI browsing. (I think gnome is "broken").

With ubuntu I tried to setup Samba the same way as under Centos 5.2 but it does not work.  With enough effort I can get ubuntu to show a browse list of the other machines, but when I click on the machines in the gnone network GUI I just get a blank pane instead of the shared folders. (I can get kubuntu to work).  Various stange things happen when using command line browsing like smbtreee or smbclient -L PC-NAME.  I normally CAN connect using smbclient, but I need to know the exact name and spelling ot each computer and shareed item.

So... for this working example I would like the thread to end up with a full list of all ubuntu items that need to be set/checked and a full posted example of a working smb.conf (without commnets).  The desired configuration is the normal "encrypted passwords", no servers (no one machine must be on for other machines to browse).. Lets assume the workgroup is "MYGROUP" and the computer name and net-bios name is "LIVING-ROOM".  I don't need Unix password sync, I can just enter the passwords into a Samba database using smbpasswd.  Lets try to share a folder "/transfer" the the users "root" or "john"

Let the games begin ! (please make sugestions on how to make peer-to-peer file sharing with Windows boxes work)

---

### Post by Iowan on 2008-09-03
See if [this [SOLVED]]("http://ubuntuforums.org/showthread.php?p=5720269#post5720269") thread helps.

---

### Post by gregphil on 2008-09-03
Two issues with that answer:

1. I believe Wins requires a server  (remember "no server" req)

2. I want to get a FULL working EXAMPLE posted so others can benifit and have a working "starting point" from which to change the settings from.

I will try some of those settings when I get home, but I know I do not have a WINS sever enabled on my home network.  If there is an answer I think it will be more basic than that.  For example, what should a /etc/hosts file look like? (does the workgroup name need to appear in it anywhere).  Also, I did not need to do any of that to get kubuntu to work (on the same hardware in the same network).

Thanks for posting.

---

### Post by gregphil on 2008-09-03
I think I am a little closer.  I totally re-installed Samba using the ubuntu 8.04.1 package manager and tried to change as little as possible in the standard ubuntu/kubuntu files.  Now (for the first time) I can connect and browse the ubuntu machine from the other computers (Windows or CentOS 5.2).

However now (again for the first time) I can not use the command line Samba commands to connect to myself.  So, for example smbtree looks like this (LIVING-ROOM is the ubuntu machine)

/home/greg $smbtree
Password: 
MYGROUP
	\\UPSTAIRS-3GHZ  		UPSTAIRS-3GHZ
		\\UPSTAIRS-3GHZ\C$             	Default share
		\\UPSTAIRS-3GHZ\ADMIN$         	Remote Admin
		\\UPSTAIRS-3GHZ\C              	C drive
		\\UPSTAIRS-3GHZ\IPC$           	Remote IPC
	\\S02-1          		S02-1
		\\S02-1\greg           	Home Directories
		\\S02-1\IPC$           	IPC Service (S02-1)
		\\S02-1\DISK           	DISK
	\\S01-1          		S01-1
		\\S01-1\greg           	Home Directories
		\\S01-1\IPC$           	IPC Service (S01-1)
		\\S01-1\DISK           	DISK
	\\LIVING-ROOM    		LIVING-ROOM
Server requested plaintext password but 'client use plaintext auth' is disabled
failed tcon_X with NT_STATUS_OK
	\\LAPTOP         		LAPTOP
		\\LAPTOP\C$             	Default share
		\\LAPTOP\ADMIN$         	Remote Admin
		\\LAPTOP\C              	
		\\LAPTOP\print$         	Printer Drivers
		\\LAPTOP\IPC$           	Remote IPC

And,sbmclient fails like this:
 
/home/greg #smbclient -L LIVING-ROOM
Password: 
Server requested plaintext password but 'client use plaintext auth' is disabled
tree connect failed: SUCCESS - 0

HOWEVER as I said the other machines can now all browse ubuntu and ubuntu can browse the CentOS machines, but not itself or the Windows machines.

I cleaned out all the unused lines (comments) from my smb.conf file and it looks like this:

/etc/samba #cat smb.conf
[global]
   workgroup = MYGROUP
   server string = LIVING-ROOM
   wins support = no
   dns proxy = no
   name resolve order = lmhosts host bcast
   interfaces = lo eth0 127.0.0.0/24
   hosts deny = ALL
   hosts allow = 127.0.0.1/24 192.168.0.0/24
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
[homes]
   comment = Home Directories
   browseable = no
   writable = yes
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
[DISK]
   comment = DISK
   path = /
   public = yes
   writable = yes
   printable = no
   write list = root, greg
   admin users = root, greg
   browseable = yes
   available = yes
 
Does anyone know what I should change to get Samba ver 3.0.28a fully working? (without adding any servers to the mix).  Some forum threads suggest the smb.conf lines
   client plaintext auth = yes
   client lanman auth = yes
but although these line look like they could help, they don't. (and I want to stick with encrypted passwords anyway)

Any suggestions?

---

### Post by gregphil on 2008-09-04
Ok, I finally stumbled onto the correct keywords to find lots of posts about who changed what (try using google on ubuntu, samba, and "client lanman auth = yes")

It seems some Samba ver 3.0.28a developers decided to change the default authorization protocol away from the basic encrypted authorization that has been used for years by Windows and Samba.  However, something about the new tigher authorization encryption requirements is preventing success for the normal peer-to-peer case.  

Ok...fine (not really) but the poor users need to be told how to adjust the smb.conf settings to make existing networks work once again. This does not mean changing settings in all the other machines on the network.  The posts do not make it clear how to drop back to the ubuntu 7 samba shares authorization defaults.  I believe I have always been using encrypted passwords, but probably not NTLMv2 auth. Somehow the default ubuntu samba on my network won't even connect to itself now (using smbclient -L NETBIOS-NAME) claiming "Server requested plaintext password but 'client use plaintext auth' is disabled"

So.....what changes to the standard smb.conf configuraton file are needed to allow use of basic (non-NTLMv2) encrypted passwords again?  (why would 'Server request plaintext password' ? )

Once someone helps, I will post the ENTIRE solution here so others can get ubuntu 8.04.1 peer-to-peer browsing working again.

Thank You.

---

### Post by redmk2 on 2008-09-04
> **gregphil said:**
> Ok, I finally stumbled onto the correct keywords to find lots of posts about who changed what (try using google on ubuntu, samba, and "client lanman auth = yes") It seems some Samba ver 3.0.28a developers decided to change the default authorization protocol away from the basic encrypted authorization that has been used for years by Windows and Samba.
  
However, something about the new tigher authorization encryption requirements is preventing success for the normal peer-to-peer case.  

Ok...fine (not really) but the poor users need to be told how to adjust the smb.conf settings to make existing networks work once again. This does not mean changing settings in all the other machines on the network.  The posts do not make it clear how to drop back to the ubuntu 7 samba shares authorization defaults.  I believe I have always been using encrypted passwords, but probably not NTLMv2 auth. Somehow the default ubuntu samba on my network won't even connect to itself now (using smbclient -L NETBIOS-NAME) claiming "Server requested plaintext password but 'client use plaintext auth' is disabled"

So.....what changes to the standard smb.conf configuraton file are needed to allow use of basic (non-NTLMv2) encrypted passwords again?  (why would 'Server request plaintext password' ? )

Once someone helps, I will post the ENTIRE solution here so others can get ubuntu 8.04.1 peer-to-peer browsing working again.

Thank You.

Where ***specifically*** did you see this?  I would like to read about this myself.  I went back to Gutsy for because of all problems.

---

### Post by gregphil on 2008-09-04
The are *many* posts on Google just enter all this in the google search box:
ubuntu samba "client lanman auth = yes"

I don't know exactly how to fix it yet, but at least I can see how it probably got "broke".

Basically the developers changed the Samba default minimum authorization protocol to require NTLMv2 and dis-allow lower authorization levels.  I suspect they didn't consider the simplest peer-to--peer network setup or got something wrong in the change.  Anyway, tonight I am going to experiment with various smb.conf file lines and see if I can improve things.  Specifically it looks like these might be needed or help:

   lanman auth = yes
   client lanman auth = yes 

I am ammazed that this has not been more of an issue to date.  I can only assume that most developers tested on a network with at least one server enabled (domain, wins, etc).  I need to be able to browse with ANY combination of machines powered up, so the dedicated server solution is not for me (not to mention the additional cost and/or complexity of setting up the servers)

If I find a solution I will post the entire settup necessary to get peer-to-peer browsing working on ubuntu here.

Thanks for helping look for an answer.

---

### Post by gregphil on 2008-09-04
The various Samba authorization modes did not seem to change things at all. (so I ended up leaving all the authorization setting lines out of the smb.conf file and accepted the default)

However while reading up on "ntlm2 auth = " issues I noticed that others had commented on the very strange format of the /etc/hosts file under ubuntu 8.04.1   Someone in ubuntu 8.04.1 development decided the thing to do was list computer aliases on a different /etc/hosts line starting with 127.0.1.1, instead of adding aliases on the normal 127.0.0.1 line.  It was mentioned that changing this back to "normal" speed up the networking quite a bit and might fix issues.

So I decide to try it, I changed the first two lines of my /etc/hosts file from

127.0.0.1 localhost
127.0.1.1 LIVING-ROOM.MYGROUP

to 

127.0.0.1 localhost LIVING-ROOM LIVING-ROOM.MYGROUP
127.0.1.1 LIVING-ROOM.MYGROUP

and then restarted the services:
/etc/inid.d/networking restart 
/etc/init.d/samba restart.

SUCCESS! That fixed the problem with smbtree and smbclient not being able to connect to themselves (i.e. they stopped trying to use plaintext authorization).  And they now are much faster responding.  So the original host file format is needed !

AND under kubuntu using the GUI Konqueror to browse Network Folders I can now connect to all my remote machines (WindowsXp or CentOS 5.2) and read or write files.

AND the remote machines can browse to me and connect to me.
So full sucess under kubuntu, peer-to-peer browsing now works.

****************
But (isn't there always a but....) under ubuntu 8.04.1 with the exact same samba and network configuration (as far as I can tell) The gnome Nautilus GUI network browsing only works to the CentOS machines, it still does not display the shares on the WindowsXp machines it finds.  Also, it never askes for a username/password pair as kubuntu does each time I expand a share on a Windows machine.  I would think gnome should need to know the username and password to authorize, and it would be better if it asked me for them rather than assumed something.
My ubuntu username and password is the same as on the WindowsXp box, so if it is trying to use them it should have succeeded.

I will keep trying to get gnome GUI browing to work.....

Good Luck.

---

### Post by redmk2 on 2008-09-05
> However while reading up on "ntlm2 auth = " issues I noticed that others had commented on the very strange format of the /etc/hosts file under ubuntu 8.04.1 Someone in ubuntu 8.04.1 development decided the thing to do was list computer aliases on a different /etc/hosts line starting with 127.0.1.1, instead of adding aliases on the normal 127.0.0.1 line. It was mentioned that changing this back to "normal" speed up the networking quite a bit and might fix issues...

SUCCESS! That fixed the problem with smbtree and smbclient not being able to connect to themselves (i.e. they stopped trying to use plaintext authorization). And they now are much faster responding. So the original host file format is needed !


It would be a big help if you documented your comments. Show us the source of your  "others have commented". As an example the 127.0.0.0 network always refers to the local host. It really doesn't matter whether it is 127.1.1.1 or 127.0.0.1 it's still the local host.  Not the name "localhost", but the host you are at.  The hosts files were the original method of resolving computer names (DNS or NetBIOS if you will).  If you bind the computers name (my desktop is malibu) to the 127.0.0.0 network then it probably will not be resolved correctly anywhere else on the network.  My /etc/host file looks like this:```
redmk2@malibu:~>cat /etc/hosts
127.0.0.1 localhost
192.168.1.12 malibu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

The references you've made to NTLM2 and such refer to the transition from non network aware W95/98/ME O/S's used in a NT4 or even later in a Win2K AD environment.  They are not really relevant today.  

As your real intent was to have a local P2P sharing situation NTLM or clear text logins should be even farther from the discussion.  A typical workgroup using Samba needs only to compare the logged in user name to  the smbusers database.  I have made sure that my Windows and Linux users have the same login and also in smbusers.  Even if you decide NOT to do that you can still use the "bad user" directive to allow access.   

In my mind P2P sharing is more about transient, and temporary mapping (soft mount) of shares.  Whether it's  Windows shares or Samba, it's still a client/server based protocol.  So even in a P2P discussion we need at least 2 servers.  The Windows Share [[COLOR="Blue"]**(lanmanserver)**[/COLOR]]("http://www.thenetworkencyclopedia.com/d2.asp?ref=1768") and the Samba server.  

**[SIZE="1"]We should have a reliable infrastructure[/SIZE]**
We need DNS.  This means the ability to configure DNS.   Or WINS if you use netbios naming.  (NetBIOS and WINS has not been used by windows for naning since W2K).  Note: If you insist on using WINS (NetBIOS) to resolve names with Ubuntu, then WinBind needs to be installed for the WINS server. Also nsswitch needs to be configured.  Most times I see WINS used to overcome the limitations of someones poorly conceived DHCP setup.

**[SIZE="1"]We need and IP addressing scheme[/SIZE]**. 
By that I mean the ability to configure DHCP or to set up static IP addressing.  If you use DHCP you will need to control the hostnames for those machines via the DHCP client or by reserving the IP addresses and naming.  

Now we are up to 4 servers.  Admittedly we could use host files to resolve names as we said above and static IP addressing.  This would bring us back to the 2 servers at the very least.

**[SIZE="1"]Why does Ubuntu Hardy have problems?[/SIZE]**
In Hardy, the Gnome libraries have been changed.  This causes the "setup scripts" that the GUI uses to create the install configuration fail.  This is NOT a problem with Samba.  I don't believe it's a problem with Gnome being able to "browse shares".  I think it's only a problem with the "auto" configuration.  The answer is -- manually configure.

**[SIZE="1"]What are the Samba components?[/SIZE]**
Not much has been written in plain language on various components that make up the Samba suite of applications.  Below is a simple table of these components.

_*Samba Server *_(the part that is installed when you try to "share files" via the GUI in Hardy.  ie:
[COLOR="Blue"]Windows Client (browsing Network Neighborhood)[/COLOR] <==========> [COLOR="DarkOrange"]**Samba server**[/COLOR]
You can see the Samba server processes by issuing the following command from the terminal: ```
ps -ef | grep smb
```  The daemon (server) is [SIZE="1"]smbd[/SIZE] and there should be 2 of them.

*_SMBFS_*  (the part that is NOT installed when you "share files" in Hardy).  This is needed for you to browse Windows shares.

  [COLOR="DarkOrange"]**SMBFS (Samba client)**[/COLOR] <==============> [COLOR="Blue"]Windows Share (lanmanserver)[/COLOR]
 
You can see the server processes by by checking the "services" running in **Admin Tools >> Services** in Windows (XP)
 The service is called "server" (real name is: lanmanserver).  Highlight it and read the description.

There is one more client that can be used to browse Windows shares.  This is the CLI tool "*_smbclient_*"

I prefer to "roll my own", so I have only manually configured Samba installs. My home setup has an Ubuntu Samba server with Ubuntu and XP clients. One of those is a wireless/DHCP laptop.  I can browse my XP hosts from Ubuntu and browse my Ubuntu Samba server from XP.  Actually, I can even browse the Ubuntu host that the Server resides on from that host!  One machine as both client and server.

One last thing.  If you use the GUI to "share files", The configuration files are stored at: ```
/var/lib/samba
```  The /etc/samba/smb.conf file is only used to set the workgroup and minor default settings.  A quick look, I'm sure will reveal no "share" is configured.

So now, the choice is ours.  Wait until they sort out Gnome, maybe try KDE using Kubuntu,  go back to CentOS or manually configure Samba for your particular use.

I highly recommend reading [[COLOR="Green"]**Samba-3 by example**[/COLOR]]("http://us1.samba.org/samba/docs/man/Samba-Guide/").  This is a very good guide for the beginner wishing to understand and configure a Samba installation.  It starts with a basic example and takes the reader through more complex configurations.

**EDIT:** Sometimes the proof is in the pudding. See the following successful Hardy Samba installs: [http://ubuntuforums.org/showthread.php?t=903974&highlight=smbfs]("http://ubuntuforums.org/showthread.php?t=903974&highlight=smbfs")
[http://ubuntuforums.org/showthread.php?t=890869&highlight=bab1&page=3]("http://ubuntuforums.org/showthread.php?t=890869&highlight=bab1&page=3")

---

### Post by gregphil on 2008-09-05
I don't think you have fully read my earlier posts.

This thread was started to try and define a full working example of how to setup peer-to-peer browsing.  I would argue this is the most common and the most likely network setup new users of ubuntu (or kubuntu) would like to use.  The ubuntu 8.04.1 the Live DVD setup does not "just work" upon install.  After three weeks of hard efort I have still not managed to get ubuntu GUI browsing to work correctly, and I don't think it is "just me".  (I am a senior design engineer with around 30 years of experience).  I did get CentOS 5.2 KDE to work in a few hours, but never could get CentOS 5.2 gnome (on same hardware) to GUI browse at all.

The problem I am describing is with a true peer-to-peer network, where no one PC is a required server. This "no server" configuration is required so that any pair of PC's on the sub-net can be turned on and do share browsing without requiring help from other servers.  I do understand how to setup more complicated networks with servers, but that is not the point.  A peer-to-peer network should work (as it did in earlier distributions).

So with Samba installed and configured (see the smb.conf file a few posts back)  I find that even sbmtree and sbmclient can NOT connect to themselves.  In spite of what you say about the /etc/hosts allowed format, to get smbtree and smbclient to fully work, it was necessary to edit the /etc/hosts line starting with 127.0.0.1 and include the NetBios names of the computer (as well as "localhost").  Once the edit was done, it immediately fixed the broken smbtree and smbclient.  They now can connect to the machine they are run on (and have stopped trying to use palin text authorization to do it)

So, one problem identified and fixed.  On a separate kubuntu install, with the same samba seup and the same /etc/host change, I find that all peer-to-peer file browsing works as it should.  This means the GUI browsing works in Konqueror and I can both browse shares (without knowing their name ahead of time) and connect to them on both CentOS machines and on Windowsxp machines. The other machines can also browse kubuntu and connect to it.

Now back to the ubuntu setup.  Smbtree and smbclient both work fine (after the changes to /etc/hosts) and I can do command line browsing and file sharing.  Other machines can browse and connect to ubuntu.  HOWEVER the gonome nautilus GUI network file manager DOES NOT WORK.  It shows all the machines on the sub-net and can expand the shares and connect to the shares on CentOS machines.  It can NOT expand the shares on WindowsXp machines, it just gives a blank pane when I click on a Windows machine icon (and no prompt for passwrod etc).  If I switch the nautilus network file manager dialog box to text mode and then enter the entire path to the share (like smb://LAPTOP/C) then nautilus DOES mount the share and connect to it (you could call this a work-around).  But browsing is not working, you need to know and type in the share name to connect to using the gnome nautilus GUI network file manager.  This is the problem I am looking for a solution to.

There are a few offical bugs that sound related to this open at the offical ubuntu site (I don't have the bug numbers with me here at work) but the developers seem confused and have not acknowledged this specific problem as "real"  (in spite of the many posts by poor users who point out this worked fine under ubuntu 7 but stopped working on the "update" to 8.04.1)

Any help will be appreciated.  Thank You.

BTW, The sharing setup is not longer available in the default ubuntu menus.  It is however still installed and can be invoked from the command line (something like "sudo share-admin").  I didn't use it to setup Samba.

---

### Post by gregphil on 2008-09-05
These may be interesting reading to people following this thread:

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/209520](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/209520)
Note that is is titled with "security = share" but many posters in the *long* thread mention using "security = user", as I am using.

As far as I can tell this is a real ubuntu 8.04.1 peer-to-peer file sharing bug (probably in the gnome nautilus network file browser) that can not be configured away.

On a related note, this mentions some issues with the /etc/hosts file:
[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/72341](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/72341)

---

### Post by gregphil on 2008-09-06
I have spent another full day researching the peer-to-peer problem with ubuntu 8.04.1.  No matter how it is configured it appears the default gnome GUI network file browser, Nautilus does not correctly request the available shares from a Windows Xp box.  Thus the Windows Xp box rejects the request and the GUI browser displays no shares.  The specific problem seems to be with the Nautilus application, it trys using anonymous login instead of prompting for a username and password (or using the logged on client credentials, or using cached credentials). Most Windows machines will allow the anonymous login but refuse to offer up any details about the shares:  (the -N option to smbclient means "no password" = anonymous)

/home/greg #smbclient -L LAPTOP -N
Anonymous login successful
Domain=[MYGROUP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine LAPTOP.  Error was NT_STATUS_ACCESS_DENIED
Error returning browse list: NT_STATUS_ACCESS_DENIED
Anonymous login successful
Domain=[MYGROUP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------
        LAPTOP               LAPTOP
        LIVING-ROOM          LIVING-ROOM
        S01-1                S01-1
        S02-1                S02-1
        UPSTAIRS-3GHZ        UPSTAIRS-3GHZ

        Workgroup            Master
	---------            -------
        MYGROUP              UPSTAIRS-3GHZ

*************************************************************************
If Nautilus would do a full user login it would get the data it needs:

 /home/greg #smbclient -L LAPTOP
Password:********** 
Domain=[LAPTOP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        IPC$            IPC       Remote IPC
        print$          Disk      Printer Drivers
        C               Disk      
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
Domain=[LAPTOP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------

I have been unable to find anyway to configure Nautilus to stop using anonymous logins and use a real user and password  (i.e. actually do security = user)

Anyone have any suggestions?  <--------------------------------

As I mentioned in an earlier post, a "workaround" is to click on a Windows box browse icon in the 'Network File Browser', then switch the target dialog to text by clicking on the pencil, and then append the name of the share in the dialog.  This would look something like:  smb://laptop/c/  (and press enter).  However this is not really browsing because you need to know the name of the share ahead of time.  But you could use a command line command such as "smbclient -L LAPTOP" to find the names of the available shares on the computer "LAPTOP".

---

### Post by gregphil on 2008-09-08
I see these long standing bugs are still in Intrepid Alpha 5 (released this week).  Not much chance for a fix any time soon.

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/224351](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/224351)

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)

---

### Post by chocka on 2008-10-22
Thanks gregphil. This is definitely an issue with 8.10. SMB browsing works fine with 8.04LTS on our computers which browse a NAS device and its shares on the network. But once we installed 8.10 the ubuntu boxes are unable to recognize anything using the smb:// method on Nautilus, which used to work fine earlier. Also even if we type in the actual share name still we are unable to browse further into the sub-directories and files under the share name.

I hope this gets resolved soon, for its a showstopper for us going forward with a full-fledged conversion of our client boxes from windows to Ubuntu.

---

### Post by chocka on 2008-10-22
Duplicate post

---

### Post by Business Convert on 2008-10-23
> **chocka said:**
> Thanks gregphil. This is definitely an issue with 8.10. SMB browsing works fine with 8.04LTS on our computers which browse a NAS device and its shares on the network. But once we installed 8.10 the ubuntu boxes are unable to recognize anything using the smb:// method on Nautilus, which used to work fine earlier. Also even if we type in the actual share name still we are unable to browse further into the sub-directories and files under the share name.

I hope this gets resolved soon, for its a showstopper for us going forward with a full-fledged conversion of our client boxes from windows to Ubuntu.

Agreed.  We are having the same peer to peer networking issues as well.  We have 10 identical machines set-up, running to the internet through a gateway.  All are using Ubuntu 8.04, and none are now working.  Our original set-ups with 6.06LTS worked fine.  What happened, and who will fix it?

---

