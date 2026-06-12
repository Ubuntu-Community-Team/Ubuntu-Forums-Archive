---
title: "[SOLVED] Samba: Server not configured for transactions error"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by GuiGuy on 2008-03-18
Try two: I had asked this a couple of days ago but didn't get a reply. At the risk of causing offence, I'll try again:

On a simple share setup my Samba file server has been working fine for six months or so. Without having changed anything, I can still see the share names on the Samba PC from the Windows PC. But when I try to access them , now  I get 

" <share_name> not found.  Server not configured for transactions" 

Googling has failed to reveal anything helpful in respect of the error.

Does anyone here have an idea what might be causing the problem.

NB: There is no problem the Windows PCs from the Linux/ Samba PC.

Thanks

---

### Post by Eiríkr on 2008-03-18
A few questions:
[list=1][*]Could you please post your [font=courier]/etc/samba/smb.conf[/font] file?
[*]Have you made any changes to usernames or passwords on the Samba server side?  Windows caches this data and **will not** recognize that any changes have occurred, stupidly offering the cached username and password and failing out.  If this is your issue, have a look at [thread=720889]this HOWTO[/thread] for shutting off this caching on the Windows side.  
[*]How are you trying to access the shares?  In Windows, are you clicking My Network Places -> Entire Network -> Microsoft Windows Network -> WORKGROUPNAME -> SERVERNAME -> SHARENAME?[/list]

Cheers,

Eiríkr

---

### Post by GuiGuy on 2008-03-19
Thanks for the reply:

> **Eiríkr said:**
> A few questions:
[list=1][*]Could you please post your [font=courier]/etc/samba/smb.conf[/font] file?



	workgroup = MSHOME
	netbios name = FF01_SMB
	security = SHARE
	auth methods = guest
	null passwords = Yes
	passdb backend = tdbsam
	username map = /etc/samba/smbusers
	syslog only = Yes
	acl compatibility = winnt
	announce version = 5.0
	name resolve order = hosts wins bcast
	server signing = auto
	socket options = SO_KEEPALIVE TCP_NODELAY IPTOS_LOWDELAY SO_SNDBUF=8192 SO_RCVBUF=8192
	printcap name = CUPS
	preferred master = No
	domain master = No
	wins support = Yes
	ldap ssl = no
	read only = No
	guest ok = Yes
	hosts allow = 127.0.0.1, 192.168.1.0/24
	hosts deny = 0.0.0.0/0
	printing = cups
	print command = 
	lpq command = %p
	lprm command = 
	case sensitive = No
	strict locking = No
	msdfs proxy = no

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[MYMOUNTS_HDF]
	comment = /home/auser/mymounts/hdf
	path = /home/auser/mymounts/hdf/
	wide links = No

[MUSICCOLLCTN]
	comment = /home/auser/mymounts/hdf/music_collection
	path = /home/auser/mymounts/hdf/music_collection/

[HDF_DATA1]
	comment = /home/auser/mymounts/hdf/Data1
	path = /home/auser/mymounts/hdf/Data1/
	wide links = No

[DOCUMNTSWBST]
	comment = /home/auser/documents/website
	path = /home/auser/documents/website

[AUSEREUSENET]
	comment = /home/auser/mymounts/hdf/home/auser/usenet
	path = /home/auser/mymounts/hdf/home/auser/usenet
	force user = auser
	force group = auser
	wide links = No

NB: Using WINS=YES and static local IP addresses.


> 
[*]Have you made any changes to usernames or passwords on the Samba server side?  

No. 

> Windows caches this data and **will not** recognize that any changes have occurred, stupidly offering the cached username and password and failing out.  If this is your issue, have a look at [thread=720889]this HOWTO[/thread] for shutting off this caching on the Windows side.  

Thanks, but I had already eliminated that from my googling. 

> 
[*]How are you trying to access the shares?  In Windows, are you clicking My Network Places -> Entire Network -> Microsoft Windows Network -> WORKGROUPNAME -> SERVERNAME -> SHARENAME?[/list]

Any which way including the way you mention. I can ping the linux/ samba box OK from Windows, the share names are displayed in "My Network Places", but that's about it. 

I should add that I am reasonably networking savvy, but this has me stumped. 

Cheers




Cheers,

Eiríkr[/QUOTE]

---

### Post by Eiríkr on 2008-03-19
Looking over your [global] options, I noted the following:

[list][*]You're missing the [global] header.  Presumably this is in the file, but just didn't make it into your post?

[*]The [font=courier]acl compatibility[/font] option is likely not needed, and is share-level, not global.  From the [relevant section of the man page]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#ACLCOMPATIBILITY"):
> acl compatibility (S)

This parameter specifies what OS ACL semantics should be compatible with. Possible values are winnt for Windows NT 4, win2k for Windows 2000 and above and auto. If you specify auto, the value for this parameter will be based upon the version of the client. There should be no reason to change this parameter from the default.

[*]The [font=courier]announce version[/font] option probably isn't needed anyway, but it doesn't look quite right as it is here in your file.  From [the man page]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#ANNOUNCEVERSION"):

> announce version (G)

This specifies the major and minor version numbers that nmbd will use when announcing itself as a server. The default is 4.9. Do not change this parameter unless you have a specific need to set a Samba server to be a downlevel server.

[*]The [font=courier]server signing[/font] option strikes me as a bit obscure.  I don't use this, and my configuration seems to work just fine.  [Man page quote]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#SERVERSIGNING"):
> server signing (G)

    This controls whether the server offers or requires the client it talks to to use SMB signing. Possible values are auto, mandatory and disabled.

    When set to auto, SMB signing is offered, but not enforced. When set to mandatory, SMB signing is required and if set to disabled, SMB signing is not offered either.

    Default: server signing = Disabled 

[*]You have a whole bunch of other share-level-only options floating around in your global section:
```
   read only = No
   guest ok = Yes
   case sensitive = No
   strict locking = No

```
In addition to these, you have the share-level-only option [font=courier]msdfs proxy = no[/font], which is completely incorrect and might be another part of your trouble.  From [the man page](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#MSDFSPROXY):
> msdfs proxy (S)

    This parameter indicates that the share is a stand-in for another CIFS share whose location is specified by the value of the parameter. When clients attempt to connect to this share, they are redirected to the proxied share using the SMB-Dfs protocol.

    Only Dfs roots can act as proxy shares. Take a look at the msdfs root and host msdfs options to find out how to set up a Dfs root share.

    No default

    Example: msdfs proxy = \otherserver\someshare 
    
So even if this setting was relevant and useful for your config, it would need to be a path.  The current value of "no" in your conf file is a non-existent path, and will bork things up.

[*]You have a whole bunch of printer-related options that do not belong in the global section either:
```
   printcap name = CUPS
   printing = cups
   print command =
   lpq command = %p
   lprm command =
```
   
[*]Your individual share definitions look okay.  The only point to note is your use of [font=courier]wide links = no[/font], which [the man page](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#WIDELINKS) states may slow things down:

> Note that setting this parameter [to no] can have a negative effect on your server performance due to the extra system calls that Samba has to do in order to perform the link checks.[/list]

Once you clean up the substantial mess in your [font=courier][global][/font] section and restart Samba, things should run much more smoothly.  Was this perchance the result of a GUI Samba config tool?  I've seen numerous instances of gsambad and possibly SWAT making a right royal mess of things.  Plus, it's clear that newer versions of Samba are less forgiving of past mistakes -- either because parsing is stricter, or perhaps because options changed.  I had to rework my own long-standing conf files when moving up from Ubuntu 7.04 to 7.10.  

Anyway, try the cleanups mentioned (use a text editor!  NOT a GUI config tool!), and see if that doesn't help.  

Cheers,

Eiríkr

---

### Post by GuiGuy on 2008-03-21
> **Eiríkr said:**
> 
Anyway, try the cleanups mentioned (use a text editor!  NOT a GUI config tool!), and see if that doesn't help.  


I'd been using SWAT. Did as suggested and went back to my original plain, vanilla config using text editor. Jeez I hate that :( 

But it  seems to have fixed it. :)

Many thanks

---

### Post by Eiríkr on 2008-03-21
Glad it helped, and glad your Samba install is back up and running!  :D  If this fixes your issues for this thread, please also remember to mark the trhead as SOLVED in the Thread Tools dropdown towards the top of the page.  :)

Cheers,

Eiríkr

---

### Post by GuiGuy on 2008-03-23
> **Eiríkr said:**
> Glad it helped, and glad your Samba install is back up and running!  :D  If this fixes your issues for this thread, please also remember to mark the trhead as SOLVED in the Thread Tools dropdown towards the top of the page.  :)


Well, it's solved, Sort of. 

The Linux box is a little more accessible from Windows PCs. However, it's a lottery:

From Windows XP boxes:

[LIST]
[*]Intermittently a log in dialog appears with the grayed out name "guest". Since guest doesn't have a password it's not possible to log in
[*]Doing a "repair" once or twice on the network connection will usually overcome the dialog and eventually it is possible to browse the samba shares
[*]It is always possible to browse the samba shares using the ip address
[/LIST]

From Vista  boxes:

[LIST]
[*]Can see the samba shares but cannot open them
[*]Initally cannot even access the Samba shares using the ip address
[*]Doing a "Disable" and "Enable" on the Vista network connection several times will eventually allow access to the Samba Shares.
[/LIST]


Thanks

---

### Post by Eiríkr on 2008-03-23
A suggestion -- map a network drive to the Samba shares you want to connect to regularly.  I have no idea about Vista, but on XP, I've found that to be more reliable for some reason.  

Also, guest access isn't enabled for any of your shares, so it's not surprising that user "guest" wouldn't work.  

How are you currently accessing shares from your XP machine?  Are you drilling down through the network in Explorer, clicking My Network Places -> Entire Network -> Microsoft Windows Network -> WORKGROUP -> SERVER -> SHARE?

---

### Post by GuiGuy on 2008-03-23
> **Eiríkr said:**
> A suggestion -- map a network drive to the Samba shares you want to connect to regularly.  I have no idea about Vista, but on XP, I've found that to be more reliable for some reason.  

I get the same issue with mapped drives. Regarding Vista, network performance is already bad. Mapping a drive makes it worse. FYI, network performance can approach dial up speeds on Vista. 

> 
Also, guest access isn't enabled for any of your shares, so it's not surprising that user "guest" wouldn't work.  


Thanks for the tip. I didn't realise I had to explicitly specify the guest user on shares. That seems to have solved a raft or problems

> 
How are you currently accessing shares from your XP machine?  Are you drilling down through the network in Explorer, clicking My Network Places -> Entire Network -> Microsoft Windows Network -> WORKGROUP -> SERVER -> SHARE?

Sometimes. But usually I go to the address bar and type \\<samba_server\someshare 

However, the "guest" thing seems to have solved things. 

I owe you one. Many thanks.

---

### Post by Eiríkr on 2008-03-23
No worries, glad it's working!  :D  Sorry to hear about Vista; out of curiosity, has that sped up at all once you've added the "guest ok = yes" share parameter?

Cheers, 

Eiríkr

---

### Post by GuiGuy on 2008-03-23
> **Eiríkr said:**
> No worries, glad it's working!  :D  Sorry to hear about Vista; out of curiosity, has that sped up at all once you've added the "guest ok = yes" share parameter?

Cheers, 

Eiríkr

The VISTA networking performance issues are a hot topic. Generally performance is degraded in a mixed OS environment (my case).  M$ claims SP1 has solved it, but I observe no discernable difference. 

My own tests show that if I boot the Vista box into WinXP, wireless networking throughput is around 40mbps. Using vista, same hardware, same location, it's between 30kbps to 128kbps. These measurements are consistent. Others people record similar experience. 

BTW, the only reason I have a Vista box in the mix is because it drives our home entertainment system. Vista media center is about the best of for now (IMO). I'm playing with MythDora and MythUbuntu at the moment but am finding it frustrating. Poor choice of jargon (IMO) that only confuses, confusing configuration on TV cards, cryptic messages when it goes pearshaped etc.. One for the geeks at this point, I think. 



Samba <> WinXP has been and now is again good, both wireless and cabled. 

Linux PC <> LinuxPC is perfect. The wife has an ASUS EEE PC, and it connects to Linux fileserver from anywhere in the house and the yard.

As I hinted, I'd like to get off M$ Windows, but there are a few things where Linux is still playing catchup. But we're getting there I think.

Anyway, many thanks for your help and yes, I have backed the samba config up :) 

Cheers

---

