---
title: "Samba Networking with Vista + Ubuntu with Nautilus"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by rhys_rhaven on 2008-10-21
Maybe this has been said before, somewhere, but I never ever found it. I work at Uni IT group, and needed to get Ubuntu playing nice with our windows shares. 

This Post: [http://ubuntuforums.org/showthread.php?t=187049](http://ubuntuforums.org/showthread.php?t=187049)
and this one: [http://www.nabble.com/ntlmv2-td4691183.html](http://www.nabble.com/ntlmv2-td4691183.html)
and this one: [http://ubuntuforums.org/showthread.php?t=428093](http://ubuntuforums.org/showthread.php?t=428093)
all discuss this problem, with all sorts of ideas to fix it. 

We don't use Vista, but we do force NTLMv2 authentication only on our Windows XP shares for security reasons. In Vista this is the default way of sharing files. smbclient works just fine from the command line, but that is messy for our users. 

The common idea is to add ```
client ntlmv2 auth = yes

``` to /etc/samba/smb.conf.  This works for smbclient, but not for nautilus, for the simple reason that nautilus sources $HOME/.smb/smb.conf, NOT /etc/samba/smb.conf. 

Thus this is the fix. 

As your own user: 
```

mkdir ~/.smb
echo "client ntlmv2 auth = yes" >> ~/.smb/smb.conf

```

Just to note, I do work in a domain environment. So I also added "workgroup = server" to my configuration. Doubt this will break anything for everyone else. Hope this fixes things, or at least clarifies them for some people.

---

### Post by HDTimeshifter on 2008-11-02
> **rhys_rhaven said:**
> 
The common idea is to add ```
client ntlmv2 auth = yes

``` to /etc/samba/smb.conf.  This works for smbclient, but not for nautilus, for the simple reason that nautilus sources $HOME/.smb/smb.conf, NOT /etc/samba/smb.conf. 

Thus this is the fix. 

As your own user: 
```

mkdir ~/.smb
echo "client ntlmv2 auth = yes" >> ~/.smb/smb.conf

```


I tried the above with Ubuntu 8.04, but I still got a blank panel with my Vista share.

Someone said this was going to be fixed in Ubuntu 8.10, so I upgraded on Thursday, but it still doesn't work.  I tried the above again, and now I don't even see the Vista PC.  In fact, when I click on Windows Network, I get a blank panel - I no longer can even see the XP PCs or the Vista PC!  I tried renaming ~/.smb/smb.conf to undo and even rebooted, but now all I get is a blank panel under Windows Network.  What is wrong???

---

### Post by Zimmer on 2008-11-06
As the OP said, it is the Vista default authentication  that does not play nice with Samba (yet).

Try.
[http://www.nobluescreens.com/solutions/samba_vista.php](http://www.nobluescreens.com/solutions/samba_vista.php)

Security policies were the problems on a friend's network.

[http://www.techiecorner.com/355/vista-how-to-connect-to-samba-or-mac/](http://www.techiecorner.com/355/vista-how-to-connect-to-samba-or-mac/)

This is the actual link we used to get it going, I think
[http://www.builderau.com.au/blogs/codemonkeybusiness/viewblogpost.htm?p=339270746](http://www.builderau.com.au/blogs/codemonkeybusiness/viewblogpost.htm?p=339270746)

---

### Post by Piupardo on 2008-11-06
> **Zimmer said:**
> As the OP said, it is the Vista default authentication  that does not play nice with Samba (yet).

Try.
[http://www.nobluescreens.com/solutions/samba_vista.php](http://www.nobluescreens.com/solutions/samba_vista.php)

Security policies were the problems on a friend's network.

[http://www.techiecorner.com/355/vist...-samba-or-mac/](http://www.techiecorner.com/355/vist...-samba-or-mac/)

This is the actual link we used to get it going, I think
[http://www.builderau.com.au/blogs/co...tm?p=339270746](http://www.builderau.com.au/blogs/co...tm?p=339270746)

Hi!

Two of this links you gave are incomplete. Would appreciate if you fix that :)

Thanks :)

---

### Post by dmizer on 2008-11-06
> **Piupardo said:**
> Hi!

Two of this links you gave are incomplete. Would appreciate if you fix that :)

Thanks :)

Fixed. They work now.

I have included this thread in my CIFS tutorial here: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

### Post by HDTimeshifter on 2008-11-07
> **Zimmer said:**
> As the OP said, it is the Vista default authentication  that does not play nice with Samba (yet).

Try.
[http://www.nobluescreens.com/solutions/samba_vista.php](http://www.nobluescreens.com/solutions/samba_vista.php)

Security policies were the problems on a friend's network.

[http://www.techiecorner.com/355/vista-how-to-connect-to-samba-or-mac/](http://www.techiecorner.com/355/vista-how-to-connect-to-samba-or-mac/)

This is the actual link we used to get it going, I think
[http://www.builderau.com.au/blogs/codemonkeybusiness/viewblogpost.htm?p=339270746](http://www.builderau.com.au/blogs/codemonkeybusiness/viewblogpost.htm?p=339270746)

I assume the first link is connecting to Ubuntu from Vista.

The 2nd link still doesn't work.

I tried following the 3rd link (which is what I'm concerned with right now - accessing Vista from Ubuntu Nautilus), but typing "secpol.msc" from the Vista search bar simply returns "No items match your search".  Maybe I don't understand the non-intuitive Vista interface, but I'm not sure how to get a "run command" like in old XP.  I assumed you type your command in the Vista search box to run a command???

---

### Post by Piupardo on 2008-11-07
> **HDTimeshifter said:**
> I assume the first link is connecting to Ubuntu from Vista.

The 2nd link still doesn't work.

I tried following the 3rd link (which is what I'm concerned with right now - accessing Vista from Ubuntu Nautilus), but typing "secpol.msc" from the Vista search bar simply returns "No items match your search".  Maybe I don't understand the non-intuitive Vista interface, but I'm not sure how to get a "run command" like in old XP.  I assumed you type your command in the Vista search box to run a command???

You can do that on a menu "Run..." from Start Menu. Just above the shut down button.

Regards,

---

### Post by Piupardo on 2008-11-07
Thanks anyway :)

I still have the same problem, can´t see my windows vista shares when browsing the network with Nautilus, but I have also read that this is a bug of Nautilus or ubuntu or samba, being worked by ubuntu. 
So I guess we'll just have to wait for a pathc/solution/update to come out.

Best regards.

---

### Post by HDTimeshifter on 2008-11-08
> **Piupardo said:**
> You can do that on a menu "Run..." from Start Menu. Just above the shut down button.

Regards,

There is no "Run..." command in Vista.  I see it on my XP PC, but there is no equivalent in Vista.  I hate Vista.  The interface sucks - MS made a backwards move IMHO - that's one reason I went to Ubuntu instead of Vista for my new PC.

I found it.  You have to type "run" in the search field to get the run command in Vista.  Still damn unintuitive, and wasted a few days before I figured that out.  Unproductivity for you Microsoft!

But wait...there's more...when I finally ran it, it doesn't work:  "Windows cannot find 'secpol.msc...".  F*cking POS!!!

---

### Post by dmizer on 2008-11-08
> **HDTimeshifter said:**
> There is no "Run..." command in Vista.  I see it on my XP PC, but there is no equivalent in Vista.  I hate Vista.  The interface sucks - MS made a backwards move IMHO - that's one reason I went to Ubuntu instead of Vista for my new PC.

I found it.  You have to type "run" in the search field to get the run command in Vista.  Still damn unintuitive, and wasted a few days before I figured that out.  Unproductivity for you Microsoft!

But wait...there's more...when I finally ran it, it doesn't work:  "Windows cannot find 'secpol.msc...".

According to [this thread]("http://forums.microsoft.com/TechNet/ShowPost.aspx?PostID=1250796&SiteID=17"):
> Secpol.msc does not exist in the home versions of Vista. But basically secpol.msc is just another GUI for registry settings. All settings regarding UAC can be found in the registry at HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Policies\System.

---

### Post by HDTimeshifter on 2008-11-09
Ok, so rather than mucking with the registry directly, I used the Admin Tools as one poster described:

> To stop the UAC you can go into your Control Panel, then Administrative Tools --> System Configuration --> Tools Tab --> Down to Disable UAC.

In fact, the easiest way is to simply run msconfig as I've always been doing in XP to get to that panel to remove unnecessary services.

I disabled UAC and rebooted, but still get a blank folder when I try to access my Vista shares.  I made sure "Password protected sharing" is off, and I can access the share from my XP PC, although it still requires me to type in my username and password.  I even rebooted my Ubuntu PC and still can't access Vista.

---

### Post by dmizer on 2008-11-09
Try adding your Ubuntu username and password to the Vista machine (you can do this without giving it a login account), and grant it local access to the shared folder.

---

### Post by HDTimeshifter on 2008-11-10
I added a new user account and gave it access to the shared folder, but it makes no difference.  I think there is something more as when I click on the share representing the Vista laptop, no shares are displayed.  When I click on one of the shares representing an XP PC, all of it's shares are displayed, even the ones without shared access (ex., the root drives show up as $C, $D, $E, but if I try to click on them, it prompts to enter a password, which then fails to mount since I haven't shared them.  When I click on a share that I've actually shared, the password works and I get the display of its contents).

I also found out I can enable/disable UAC through the Control Panel / User Accounts rather than drilling all the way down from Admin Tools or running msconfig.  The check box to use UAC is unchecked here so I definitely turned it off with the other method that runs a DOS shell.

---

### Post by dmizer on 2008-11-10
What is the output of:
```
smbtree
```

---

### Post by HDTimeshifter on 2008-11-11
[I](Computer and network names have been changed to protect the not so innocent's privacy, but patterns remain the same, so you get the idea.)
[/I]
The only real difference I see between my Vista laptop and the XP PCs is that the Vista box has a hyphenated name and the main shared folder is Documents rather than "Documents and Settings".  Also I make sure the laptop screen is open and illuminated while testing this just to be sure it doesn't go to sleep and foul things up.

HOME
	\\PC1       		PC1 XP
		\\PC1\Printer        	Microsoft Office Document Image Writer
		\\PC1\C$             	Default share
		\\PC1\ADMIN$         	Remote Admin
		\\PC1\SharedDocs     	
		\\PC1\print$         	Printer Drivers
		\\PC1\D$             	Default share
		\\PC1\IPC$           	Remote IPC
		\\PC1\E$             	Default share
		\\PC1\Documents and Settings	
	\\VISTA-LAPTOP  		Laptop Vista
		\\VISTA-LAPTOP\Public         	
		\\VISTA-LAPTOP\print$         	Printer Drivers
		\\VISTA-LAPTOP\Pictures       	
		\\VISTA-LAPTOP\IPC$           	Remote IPC
		\\VISTA-LAPTOP\Documents      	
		\\VISTA-LAPTOP\D$             	Default share
		\\VISTA-LAPTOP\C$             	Default share
		\\VISTA-LAPTOP\ADMIN$         	Remote Admin
	\\PC2         		PC2 XP
		\\PC2\Printer        	Microsoft Office Document Image Writer
		\\PC2\C$             	Default share
		\\PC2\ADMIN$         	Remote Admin
		\\PC2\SharedDocs     	
		\\PC2\print$         	Printer Drivers
		\\PC2\D$             	Default share
		\\PC2\IPC$           	Remote IPC
		\\PC2\E$             	Default share
		\\PC2\Documents and Settings

---

### Post by Zimmer on 2008-11-12
There may be another difference  .
For XP the default workgroup is MSHOME
and for VISTA it is  WORKGROUP  

Does this have any effect on how your SAMBA sharing should be configured?
(Sorry I cannot test this for you as I am dual booting VISTA not networking it! But my limited knowledge of networking is nagging me that those sharing should be members of the same workgroup).

Hope this is helpful
regards Zimmer

---

### Post by dmizer on 2008-11-12
> **Zimmer said:**
> There may be another difference  .
For XP the default workgroup is MSHOME
and for VISTA it is  WORKGROUP
I had the same thoughts. Unfortunately, the smbtree output above indicates that all the computers in the network are indeed a part of the same workgroup.

> **Zimmer said:**
> Does this have any effect on how your SAMBA sharing should be configured?
Sometimes it makes a difference, sometimes it does not. It certainly makes things much easier if the workgroup is homogeneous.

---

### Post by HDTimeshifter on 2008-11-12
I actually have the workgroup as MSHOME.  (remember some names were changed in a feeble attempt to try to protect the not-so-innocent ;))  I don't think the workgroup name matters as long as it is homogeneous.  And yes, when Nautilis/Samba prompts me the first time I open an XP share, I do have to change the workgroup from WORKGROUP to MSHOME to connect.  I do remember the first time I tried to network a Vista PC to my XP network, it was somewhat of a PITA - I think it was more than simply the workgroup name, but I don't remember - maybe that was it since that was not long after I first networked my PCs and I was still new to networking.

I played around with the shares a bit (I had originally shared the entire Vista user folder, but to be consistant, moved the share down to the Documents folder, same as with the Documents and Settings folder on my XP PCs).  When I removed the Vista share at the user level, immediately the Explorer browser on my XP PC noticed the update and popped up a dialog saying it didn't have permission for that folder.  Yet, when I go back to browsing my Ubuntu Networks and the Vista shares, it still comes up with a blank folder.

Last night, I did install Virtualbox and try to load XP since there are still some MS programs that I need for which I haven't found a Linux replacement.  I was hoping that this will give me a workaround as being an XP system, it should give me access to Vista that way.  However, I couldn't get the floppy drive to mount and my XP CD not being bootable, wasn't able to load XP.

---

### Post by ignacio69 on 2008-11-19
Hello,
My experience trying to connect vista with ubuntu is the following.
in my vista i made all the recomendations said in the forum:
1. network to private
2. password protected sharing off
3. the first 3 parts of the network and discovery are turned on, the exceptions are made in the wiindows firewall.
(I do not know if I had to turned off the firewall of Norton also?)
4. I added a new user account in Vista to recognice, the same user I am using in Ubuntu.

In Ubuntu,
samba installed, (do not know how to know which version I am using, though)
this is the result of smbtree:
WORKGROUP
	\\KMJL-PC        		
**cli_start_connection: failed to connect to KMJL-PC<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME**
	\\IGNACIO-DESKTOP		ignacio-desktop server (Samba, Ubuntu)
		\\IGNACIO-DESKTOP\PDF            	PDF
		\\IGNACIO-DESKTOP\Phaser_3117    	Xerox Phaser 3117
		\\IGNACIO-DESKTOP\IPC$           	IPC Service (ignacio-desktop server (Samba, Ubuntu))
		\\IGNACIO-DESKTOP\print$         	Printer Drivers
ignacio@ignacio-desktop:~$ cd \\KMJL-PC
bash: cd: \KMJL-PC: No existe el fichero ó directorio
ignacio@ignacio-desktop:~$ cd \KMJL-PC
bash: cd: KMJL-PC: No existe el fichero ó directorio
ignacio@ignacio-desktop:~$ cd \\WORKGROUP\KMJL-PC
bash: cd: \WORKGROUPKMJL-PC: No existe el fichero ó directorio

in my ubuntu Nautilus/samba network I can see the vista pc called KMJL-PC but inside it there is nothing.


any suggestions?
I am trying to concect  using ubuntu hardy 8.04 L.T:S.
and VISTA Home Premium.

th only thing I have not done is to configure the samba as it was said before in the forum: 
/etc/samba/smb.conf. This works for smbclient, but not for nautilus, for the simple reason that nautilus sources $HOME/.smb/smb.conf, NOT /etc/samba/smb.conf.


I believe this is important, but i have not configured anything in ubuntu and I woudl like to know if this is necessary, buecause user HDTImesHifeter has done and did not help.

do you think is necessary in my case also to configure it? I have done about the same as he did, and Had a blank panel in vista like he got.
is it a problem with vista or with samba, what do you think?

---

### Post by HDTimeshifter on 2008-11-19
ignacio69, I tried all your steps 1-4 as well as changing $HOME/.smb/smb.conf so Nautilus can source it as someone else mentioned and still get a blank folder.  Until yesterday, I was only accessing XP (and trying to access Vista) from Ubuntu.  Well I tried sharing my Ubuntu printer to the Windows PCs, but that didn't work.  Last night I tried sharing an Ubuntu folder, but that didn't work.  Someone suggested configuring Samba to add user permission in my other thread [http://ubuntuforums.org/showthread.php?p=6210960#post6210960](http://ubuntuforums.org/showthread.php?p=6210960#post6210960)
that I will try next.

---

### Post by dmizer on 2008-11-19
This possible solution was just posted a few days ago: [http://ubuntuforums.org/showpost.php?p=6204264&postcount=81](http://ubuntuforums.org/showpost.php?p=6204264&postcount=81)

---

### Post by crucial123 on 2008-12-08
I have a rediculous solution, in that it is so easy it is almost silly. 

In the file browser click on network.
Click on WORKGROUP
Click on the VISTA pc...

append the vista share folder into the LOCATION bar

ie:...   smb://Vista_machine/VISTA_SHARE

and bang there it is.

The problem seems to be a Nautilus GUI bug.

---

