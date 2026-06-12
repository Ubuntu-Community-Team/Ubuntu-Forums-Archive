---
title: "[SOLVED] problems connecting to Windows network"
date: 2008-03-17
forum: Networking &amp; Wireless
---

### Post by kd4dii on 2008-03-17
Hi, I am an absolute noobe with Linux.  I just installed Ubuntu on my laptop.  So far, it looks great.  My main problem is connecting to my Windows network.  I have a desktop running XP home and a wired connection to my laptop.  When I first installed Linux, I could see my workgroup name in the places network browser, but now I can't.  I have Samba installed and changed the SMB.CONF file as recommended in another post on here.  Now the network browser only shows Windows network, when I click on that it goes blank.  Before it would show my workgroup name and when I clicked on that I would get an error message saying unable to show folders.  Also before I did this, I could see my note book from the Windows PC, but was unable to open it, now it doesn't show at all.  I can connect to the net without problems, the router assigns me an IP address normally and the laptop shows up in the router DHCP list.  Any help anyone can give me will be appreciated, I have checked around on here without luck.  Thanks.

Bob

---

### Post by superprash2003 on 2008-03-17
try doing this.. go to Places->Connect to a Server .. and type your windows pc ip addres there and connect
  or you can also go to Places->Computer and type smb://192.168.1.10 where 192.168.1.10 is xp's ip address

---

### Post by Pengwyn44 on 2008-03-17
I am fairly new to Linux but with help from this forum I have got Samba working correctly.
I have a network of two Ubuntu machines and one Windows XP.
Connecting a Ubuntu machine to the XP was easier than connecting the two Ubuntu's.
There are two things to be sorted, taking the easy one first, you have to tell XP to share its files with the network.
To do this, click on My Computer, then right click on the C: drive; left click on "Sharing and Security", then on the Share Tab, then tick the boxes in "Network sharing and security".Put a share name in the box also (I use C).
Finally click OK. An alternative is to only share certain files.
The second thing to be sorted is the smb.conf file. This has many combinations of items which to a newbie are baffling. I found the best way is to initially change nothing and then by trial and error to make one change at a time. In my case I hashed out any line which referred to encryption or passwords under the heading "Authentication".
Then under "Share Definitions" I allowed [homes], comment = Home Directories, browsable = yes. Next allow 'writable =yes'. Then I allowed [netlogon] and the next 5 lines changing to 'no's to 'yes'.
After saving the changes I restarted the computer and ran the checks as advised by "rouben" on this forum. If you cannot find them,I will post them on request.

---

### Post by Eiríkr on 2008-03-17
Hello Bob --

> **kd4dii said:**
> Hi, I am an absolute noobe with Linux.  I just installed Ubuntu on my laptop.  So far, it looks great.  My main problem is connecting to my Windows network.  I have a desktop running XP home and a wired connection to my laptop.  When I first installed Linux, I could see my workgroup name in the places network browser, but now I can't.  

So to make sure I understand you correctly, you have files on your XP machine that you want to access from Ubuntu -- if so, this makes your XP machine the share server, and your Ubuntu machine the share client.  So long as you do not need to go from you XP machine to your Ubuntu machine, this means you **do *not*** need to install the full [FONT="Courier New"]samba[/FONT] package (the server program) or configure the [FONT="Courier New"]smb.conf[/FONT] file.  Instead, all you should need to install is the [FONT="Courier New"]smbclient[/FONT] package (which might be installed by default).  


> **kd4dii said:**
> I have Samba installed and changed the SMB.CONF file as recommended in another post on here.  

See above.  You **only** need to have the full [FONT="Courier New"]samba[/FONT] package installed if you need to share files **from** your Ubuntu machine **to** your XP machine; i.e., browsing **from** your XP machine **to** your Ubuntu machine.  Otherwise, you're much better off simplifying things by removing the [FONT="Courier New"]samba[/FONT] package (but leaving [FONT="Courier New"]smbclient[/FONT] installed).  


> **kd4dii said:**
> Now the network browser only shows Windows network, when I click on that it goes blank.  

If you decide you *need* to have a Samba server running on your Ubuntu machine as well, then we'll need to muck about with your [FONT="Courier New"]smb.conf[/FONT] file.  This particular issue sounds like it might be related to master browser problems.  Windows sharing is organized around the idea of one machine in each workgroup becoming the master for that share group, and if two or more machines each claim master status, all kinds of unproductive silliness ensues.  If this is the problem, try changing related settings in the [FONT="Courier New"]smb.conf[/FONT] file as follows (all of these should be towards the top of the file in the [font=courier][global][/font] section; add these lines if missing):
```
preferred master = yes
domain master = yes
local master = yes
```

Another possibility is workgroup name issues.  Make sure the workgroup names in both the XP machine and the [FONT="Courier New"]smb.conf[/FONT] file match.  


> **kd4dii said:**
> I can connect to the net without problems, the router assigns me an IP address normally and the laptop shows up in the router DHCP list.  

This is good to know, as it rules out basic network issues.  Basic connectivity was also confirmed by your description of seeing the workgroup name in Nautilus; without a connection, you wouldn't see any workgroup at all.  


> **kd4dii said:**
> Before it would show my workgroup name and when I clicked on that I would get an error message saying unable to show folders.  

Getting this error message when double-clicking the workgroup name might be a bug in Nautilus, as viewing the workgroup works just fine in Konquerer.  Anyway, one workaround in the Nautilus file browser is to specify the machine name in the location bar.   For reasons beyond my ken, the Nautilus developers decided to hide this by default, but you can make it appear by either hitting Ctrl+L or clicking View -> Location Bar.  When you first click Go -> Network, the location bar should show [FONT="Courier New"]network:///[/FONT] -- clicking the Windows Network icon will change this to [FONT="Courier New"]smb:///[/FONT].   Try deleting the last slash and adding your XP machine's name, so the location looks like [FONT="Courier New"]smb://xpmachine[/FONT], and this should at least display your shared folders.  Clicking on one of these should now show an Authentication Required dialog prompting you for your username and password to access the share -- use the XP username and password you use to log into your XP machine.  If you have no password at all, this raises various other issues due to a bug in the Samba code, but there are workarounds, so just let me know and we'll go from there.  


> **kd4dii said:**
> Also before I did this, I could see my note book from the Windows PC, but was unable to open it, now it doesn't show at all.  

You were unable to open your Ubuntu notebook from your Windows PC because the notebook did not have any shares -- you need the full [FONT="Courier New"]samba[/FONT] server package installed and properly configured before you can go **from** XP **to** Ubuntu.  To be honest, I'm surprised your XP machine could see your laptop at all without Samba installed; where exactly would your laptop show up?  

HTH,

Eiríkr

---

### Post by kd4dii on 2008-03-17
Thanks for the replies.  To further explain my situation, I had shared directories on my Windows pc that were working fine when I had Windows on the laptop.  I also set up shared directories on my Linux machine.  I have installed the full version of Samba.  I will check on editing my SMB file further as mentioned above.  Linux no longer sees the work group at all.  So far, this is the only difficulty I am having with Linux, I like it a lot except for this problem and would like to switch over to it on both machines.  I do need to be able to move files in both directions as it would save me a lot of back and forth running around.  Thanks again for all the replies.

Bob

---

### Post by Eiríkr on 2008-03-17
Thank you for further explaining the situation.  Ubuntu - Ubuntu sharing can actually be *much* simpler than Ubuntu - Windows sharing, due to the highly complex and arbitrary nature of how Windows networks work, and the consequent complexity of the various Samba settings.  It doesn't help matters either that Windows sharing seems to change every so often when new updates come out.  Suffice it to say that *not* using Samba will likely simplify things if / when you move over to an Ubuntu-only setup.  :)

In the meantime, do let us know if you run into any problems.  Posting your [font=courier]/etc/samba/smb.conf[/font] file is usually a good first step to figuring out problems on the Samba server side.  

Cheers,

Eiríkr

---

### Post by kd4dii on 2008-03-17
I keep trying things but no joy.  I tried the connect to a server with the IP address of the Windows machine, no joy.  I can ping the Windows machine's Ip address.  I uninstalled Samba and reinstalled it and checked that the shares were set.  I also modified the smb.conf file as mentioned above without luck.  The work group still doesn't show, even though the Windows network does.
     Well, I will keep trying, don't want to go back to Windows.  Thanks again to all for your replies.

Bob

---

### Post by Eiríkr on 2008-03-17
Please post the full contents of your [font=courier]smb.conf[/font] file.  You can output this to the screen by running either of the following commands in a terminal.
```
cat /etc/samba/smb.conf
less /etc/samba/smb.conf
```
[font=courier]cat[/font] just spits out the contents, while [font=courier]less[/font] allows you to scroll around (useful for larger files).

---

### Post by kd4dii on 2008-03-17
Hi again.  Here is my smb.conf file:

[global]
	message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
	workgroup = dadswifi
	server string = dadslaptop
	dns proxy = no
	log file = /var/log/samba/log.%m
	max log size = 1000
	syslog = 0
	panic action = /usr/share/samba/panic-action %d

	preferred master = yes
	domain master = yes
;	local master = yes

####### Authentication #######

       preferred master = yes
       domain master = yes
       local master = yes

	security = share
        hosts allow = dads

;	socket options = tcp_nodelay
	wins support = yes
;	guest ok = no
;	guest account = nobody


[printers]
	comment = All Printers
	browseable = no
	path = /var/spool/samba
	printable = yes
;	public = no
;	writable = No
	create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
;	browseable = yes
	writeable = yes
	valid users = dad

#Then I add shares off my PC like this
[work]
	path = /home/dad/Aarec
	
	locking = no
	guest ok = yes
;	available = yes


;	browseable = yes

available = yes
browsable = yes
public = yes
writable = yes
[Pictures]
	path = /root/Pictures
;	available = yes
;	browseable = yes
	guest ok = yes
	
available = yes
browsable = yes
public = yes
writable = yes

I just noticed that I have the preferred master lines in there twice, I will edit out the extra and try again.  It still is not showing the work group like it did before.  Thanks again for everyones help.

Bob

---

### Post by Eiríkr on 2008-03-17
A few thoughts:
[list][*]If your printer is not physically hooked up to and shared via your Ubuntu machine, you can remove the [font=courier][printers][/font] and [font=courier][print$][/font] sections.  
[*]Setting the security mode to [font=courier]share[/font] can lead to all kinds of interesting problems.  This is why the mode defaults to [font=courier]user[/font].  Have a look at [the relevant section of the man page]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#SECURITY") for details.  
[*]Defining how guests are handled is a very complicated issue.  The security section linked to above includes some detail.  Have a look here for more about the specific [font=courier]guest account[/font] global setting.  Note that the guest account so specified **must** have permissions on the shared directories, as defined within the Ubuntu filesystem, or guest logins won't be able to do anything.  
[*]The share definition entries [font=courier]public = yes[/font] and [font=courier]guest ok = yes[/font] are synonyms.  If you are definitely allowing guest access after reading through the above linkes, delete one or the other of these lines to simplify.
[*]I notice you have the [font=courier]locking[/font] option defined for one of your shares.  This is generally not needed except in specific circumstances, and setting this to "no" is regarded as a bad idea.  From [the man page section]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#LOCKING"):
> This option may be useful for read-only filesystems which may not need locking (such as CDROM drives), although setting this parameter of no is not really recommended even in this case.

Be careful about disabling locking either globally or in a specific service, as lack of locking may result in data corruption. You should never need to set this parameter.
[*]The [font=courier]available[/font] and [font=courier]browsable[/font] share settings both default to "yes", and may therefore be removed from your smb.conf file.  
[*]I notice that you have the [font=courier]valid users[/font] share option set to "dad" for the [font=courier][print$][/font] share.  This means that **only** user "dad" can access this share; if this is not what you intend, delete this line.  
[*]Looking over your custom share definitions (i.e. not the printer-related shares), I'm intrigued by the paths.  Your [font=courier][Pictures][/font] share, for instance, is located in [font=courier]/root/Pictures[/font].  It's generally not a good idea to put any user-accessed content in the [font=courier]/root[/font] directory.  Plus, anything so located will likely default to being owned by root, and would thus be inaccessible to Samba users (unless logging into Samba as root, which is likewise a very strongly disadvised way of doing things).  I would urgently suggest that this share be moved somewhere else entirely, perhaps by creating a new root-level directory such as [font=courier]/shares[/font], and placing the [font=courier]Pictures[/font] directory within that.  Then make sure your filesystem permissions are appropriately configured so that your Samba users can access.  [/list]

Note that you do need to consider more than just your smb.conf file -- you must also think about permissions on your Ubuntu filesystem as well, to ensure that users are able or unable to do things as required.  Have a look at [post=4423357]this other post[/post] for some ideas; [post=4496702]this post[/post] also goes over Samba and filesystem setup for single- and multi-user configurations.  

Setting up file sharing is not as point-and-click easy as it is in Windows by a long shot, but for a very good reason -- Windows is wildly convenient, but to the bad guys as well.  Ubuntu's approach (and Linux's in general) requires more up-front planning and effort, but it should result in a more secure configuration.  

HTH,

Eiríkr

---

### Post by kd4dii on 2008-03-17
I have had some success finally.  I uninstalled Samba and cleared the files from the etc/samba directory.  Reinstalled Samba and set up a couple of shares and edited the smb.conf, see below.  I ran a program called Py neighborhood and it could see the Windows shares but not open them.  Next I tried what was suggested above, open a server in places using the IP address of the Windows machine, I tried that before, unsucessfully but this time it worked.  Some of the folders wanted me to log in to open them, some didn't.  Finally getting somewhere.  Here is the smb.conf file I am using.



[Aarec]
	path = /home/dad/Aarec
;	available = yes
;	browseable = yes
	guest ok = yes
	writeable = yes

[global]
;	wins support = yes
	workgroup = dadswifi
;	server string = samba 3.0.26a
	username map = /etc/samba/smbusers
	security = user
	encrypt passwords = no
;	guest ok = no
;	guest account = nobody


preferred master = yes
	domain master = yes
	local master = yes

[Pictures]
	path = /home/dad/Pictures
;	available = yes
;	browseable = yes
	guest ok = yes
	writeable = yes

[Music]
	path = /home/dad/Music
	writeable = yes
;	browseable = yes
	guest ok = yes


It seems to be heading in the right direction.  Thanks again to all for your help.

Bob

---

### Post by Eiríkr on 2008-03-17
Glad to hear things are working!  A few notes:
[list][*]The [font=courier]guest ok[/font] setting is only relevant in share definitions.  The stray line for this setting in your [font=courier][global][/font] section might want removing. 
[*]The need for authentication on some of your XP shares might be due to filesystem / share permissions on the XP side.  [/list]
I don't recall if there's a fix for the hostname-vs-IP address issue, but I'll see what I can find.

Cheers,

Eiríkr

---

### Post by kd4dii on 2008-03-18
Got things much more the way I wanted now.  Thanks to all for your help.  I also found a version of VNC which works in Ubuntu and can now remotely control my Windows desktop.  I can't switch the desktop to Linux yet as my daughter needs some of the software that runs in Windows for school.  Once again, my thanks to all and a special mention to Eiríkr who gave a lot of input.

Bob

---

### Post by Eiríkr on 2008-03-18
Great to hear, Bob!  If that resolves your current issue, please also remember to mark this thread as SOLVED in the Thread Tools dropdown towards the top of the page.  :D

Incidentally, you might want to post over on [thread=727623]this thread[/thread]; the parent poster is looking for advice with VNC.

Cheers,

Eiríkr

---

