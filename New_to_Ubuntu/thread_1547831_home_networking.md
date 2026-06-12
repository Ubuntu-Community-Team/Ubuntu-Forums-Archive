---
title: "home networking"
date: 2010-08-07
forum: New to Ubuntu
---

### Post by Stan% on 2010-08-07
I have two home computers (XP on one, Karmic on the other) that I want to network to share files and a printer which is connected to the XP system. 

There is so many "instructions" out there I don't know which to follow. Could somebody direct me to the proper "instructions". 

The wife and I are the only users so physical access security is not a big deal.

Samba is installed; the conf file is the sample file to which I added; (following one of those "instructions")



[test]
path = /home/stan/test
available = yes
valid users = stan
read only = no
browsable = yes
public = yes
writable = yes

Thank You for your help.

---

### Post by GlazedDonut on 2010-08-07
Dont forget to add the user stan to samba.
```
sudo smbpasswd -a stan
```

---

### Post by ratcheer on 2010-08-07
Stan, I have some instructions that have worked well for me. I will post them when I get a chance. It may be a couple of hours from now, though.

Tim

---

### Post by Morbius1 on 2010-08-07
Or you could get rid of the "valid users = stan" line and have a guest share since there are only two users on the network. Then you won't have to create a stan smbpasswd.

Can the XP machine see the share and just not access it or can it not see the Ubuntu machine at all.

---

### Post by davidsrsb on 2010-08-07
Is the XP Home or Pro? Their network behaviour is very different.
Printing should be easy enough, make sure that the XP machine is set to share the printer. On the Ubuntu PC I prefer to use the CUPS web interface to add and setup network printers ([http://localhost:631](http://localhost:631))

---

### Post by Stan% on 2010-08-08
> **davidsrsb said:**
> Is the XP Home or Pro? Their network behaviour is very different.
Printing should be easy enough, make sure that the XP machine is set to share the printer. On the Ubuntu PC I prefer to use the CUPS web interface to add and setup network printers ([http://localhost:631](http://localhost:631))

XP Home

---

### Post by Stan% on 2010-08-08
How do I know if I have a static IP address or fixed DHCP lease? I need to determine the WINS setting.

---

### Post by Morbius1 on 2010-08-08
I'm probably wrong but I think you're making this more complicated than it needs to be.

From the Ubuntu machine post the output of the following commands:
```
net usershare info
``````
testparm -s
``````
smbtree
```From the WinXP machine:
Open **Command Prompt** ( not "Run" )
and post the output of the following command:
```
net view
```

---

### Post by Stan% on 2010-08-08
> **Morbius1 said:**
> I'm probably wrong but I think you're making this more complicated than it needs to be.

From the Ubuntu machine post the output of the following commands:
```
net usershare info
``````
testparm -s
``````
smbtree
```From the WinXP machine:
Open **Command Prompt** ( not "Run" )
and post the output of the following command:
```
net view
```

I have not yet run any networking apps on the XP system so net view says "The list of servers for this computer is not currently available".

net usershare draws a blank.

stan@Gateway:~$ net usershare info
stan@Gateway:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[print$]"
Processing section "[printers]"
Processing section "[MyFiles]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = HOME
	netbios name = STAN
	server string = 
	null passwords = Yes
	username map = /etc/samba/smbusers
	syslog only = Yes
	announce version = 5.0
	name resolve order = hosts wins bcast
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
	printcap name = CUPS
	wins support = Yes

[print$]
	path = /var/lib/samba/printers
	write list = root
	create mask = 0664
	directory mask = 0775
	guest ok = Yes

[printers]
	path = /tmp
	guest ok = Yes
	printable = Yes
	browseable = No
	browsable = No

[MyFiles]
	path = /home/sambashares/
	force user = stan
	force group = stan
	read only = No
	create mask = 0644
stan@Gateway:~$ smbtree
Enter stan's password: 
WORKGROUP
	\\GATEWAY        		Gateway server (Samba, Ubuntu)
		\\GATEWAY\print$         	
		\\GATEWAY\MyFiles        	
		\\GATEWAY\IPC$           	IPC Service ()

---

### Post by Morbius1 on 2010-08-08
Why oh why do so many people follow this HowTo: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

See if these minimal changes improves your situation.

In your first post you said you added this:
> [test]
path = /home/stan/test
available = yes
valid users = stan
read only = no
browsable = yes
public = yes
writable = yesBut that's not there in testparm so I don't know if you took it out.

This line:
>      wins support = YesHas turned your Ubuntu box into a WINS server for reasons unknown. I would comment it out since it serves no purpose by adding a # sign in front of the line like this:
```
#wins support = Yes
```You'd have to go into your current and any future windows or linux box and point it to this box for this to work. If you really want the box to be a wins server you can always go back and un-comment the line.

Now restart samba:
```
sudo service smbd restart
```> "The list of servers for this computer is not currently available".Go to your windows box and at least temporarily turn off the firewall.

---

### Post by Stan% on 2010-08-09
> **Morbius1 said:**
> Why oh why do so many people follow this HowTo: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

See if these minimal changes improves your situation.

In your first post you said you added this:
But that's not there in testparm so I don't know if you took it out.

This line:
Has turned your Ubuntu box into a WINS server for reasons unknown. I would comment it out since it serves no purpose by adding a # sign in front of the line like this:
```
#wins support = Yes
```You'd have to go into your current and any future windows or linux box and point it to this box for this to work. If you really want the box to be a wins server you can always go back and un-comment the line.

Now restart samba:
```
sudo service smbd restart
```Go to your windows box and at least temporarily turn off the firewall.

MORBIUS,

That HowTo seems to be the easiest to follow and it has instructions for Windows setup too.

I saved the master smb.conf to a separate file and deleted the existing smb.conf info and copied and pasted the smb.conf from the above HowTo. So yes the [test] section is gone. Should I put it back in?

#wins support = yes is now commented out.

I don`t use Windows firewall but Zone Alarm. Yes, I can disable it when the need arises. 

Sudo service smbd restart command gets response of ......
smbd: unrecognized service

---

### Post by Morbius1 on 2010-08-09
Didn't notice your using Ubuntu 9.10:

```
sudo service samba restart
```

EDIT: And disable Zone ALarm.

---

### Post by Stan% on 2010-08-09
> **Morbius1 said:**
> Didn't notice your using Ubuntu 9.10:

```
sudo service samba restart
```

EDIT: And disable Zone ALarm.

Samba restarted

ZA disabled

---

### Post by Morbius1 on 2010-08-09
Can your WinXP box access the Ubuntu share. If not run this command again from winXP:
```
net view
```

---

### Post by Stan% on 2010-08-09
> **Morbius1 said:**
> Can your WinXP box access the Ubuntu share. If not run this command again from winXP:
```
net view
```

I do not see the ubuntu share.

net view           
                   

server name        remark

\\AOL              office
\\stan

The command completed successfully.

end net view

office should be under remark.

---

### Post by Morbius1 on 2010-08-09
You may not be able to see the share but WinXP can see the box:
From testparm -s:
> [global]
    workgroup = HOME
    [COLOR=Blue]netbios name = STAN[/COLOR]From net view:
> server name        remark

\\AOL              office
[COLOR=Blue]\\stan[/COLOR]Now go to WinXP again and use this command:
```
net view \\stan
```Does it show your share?

---

### Post by Stan% on 2010-08-09
> **Morbius1 said:**
> You may not be able to see the share but WinXP can see the box:
From testparm -s:
From net view:
Now go to WinXP again and use this command:
```
net view \\stan
```Does it show your share?

net view \\stan

system error 5 has occurred.

Access is denied.

end nv \\stan

still don't see the share.

---

### Post by Morbius1 on 2010-08-09
Use "My network Places" or "network Neighborhood" or whatever Windows calls it and try to access the share. The way you set up that share it will ask for a username and password which you should have set up already if you followed the rest of the How To.

---

### Post by Stan% on 2010-08-09
> **Morbius1 said:**
> Use "My network Places" or "network Neighborhood" or whatever Windows calls it and try to access the share. The way you set up that share it will ask for a username and password which you should have set up already if you followed the rest of the How To.

I can get to "My Files" from the xp system but My Files is a empty folder.

My current smb.conf follows.

[global]
    ; General server settings
    netbios name = stan
    server string =
    workgroup = HOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    #wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/sambashares/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = stan
    force group = stan

---

### Post by Morbius1 on 2010-08-09
Um ... did you put anything in the folder on the Ubuntu side.

---

### Post by Stan% on 2010-08-09
Does it matter that I've not run any networking app on the XP system?

I did not finish thge whole HowTo.

---

### Post by Stan% on 2010-08-09
> **Morbius1 said:**
> Um ... did you put anything in the folder on the Ubuntu side.

No but shouldn't the folder be /home/sambashares?

I have now put a file in /home/sambashares. I'll go see if windows sees it.

---

### Post by Stan% on 2010-08-09
> **Stan% said:**
> No but shouldn't the folder be /home/sambashares?

I have now put a file in /home/sambashares. I'll go see if windows sees it.

Success, Windows sees the file.

---

### Post by Morbius1 on 2010-08-09
You're going to have to go back into WinXP and figure out how to allow Samba access through Zone Alarm. I can't help you with that but if I remember correctly the following ports have to be open to allow access:
> 135
137
138
139
445

---

### Post by Stan% on 2010-08-09
> **Morbius1 said:**
> You're going to have to go back into WinXP and figure out how to allow Samba access through Zone Alarm. I can't help you with that but if I remember correctly the following ports have to be open to allow access:

Okay Morbius1 I'll check out the ZA thing. Thanks for your help.

Do you take your name from the movie Forbidden Planet?

---

### Post by tahitiwibble on 2010-08-09
> **Morbius1 said:**
> Why oh why do so many people follow this HowTo: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)


Hello there Morbius1, can you suggest a better one? Thanks in advance. :)

---

### Post by Morbius1 on 2010-08-10
> **tahitiwibble said:**
> Hello there Morbius1, can you suggest a better one? Thanks in advance. :)
You really should start your own thread on this subject because it's not related to stans predicament but I'm in a strange mood this morning :p

The problem with most of these HowTo's is that they presume something is wrong with the network. The HowTo above for example sets up a WINS server which is  a legitimate way of resolving netbios names but it depends on that machine always being up when everyone else on the network is up. It  also requires modification on all the client machines - throw in a MacBook and now you have to explain how to point the Mac to a WINS server. It also stated that you have to set up a samba password for the remote user to access the share when the user may not want to have a password protected share. Other HowTo's go further and state that you MUST install winbind and all machines have to have the same Workgroup name, etc....

I would argue that for most users the network is not broken so this is one of those few situations ( perhaps the only situation ) where I would suggest that new users approach this as though they were using a Windows machine:

Open Nautilus ( your Home folder )
Right click on a folder you own, like say ... Documents
Select "Sharing Options"
Select "Share this folder", "Allow others to create and delete..", "Guest Access".
Select "Create Share"
It will ask you if you want it to modify permissions - you do.
You just created a Samba guest share that does not require a username and password to access.

This process is called Nautilus-share ( Samba calls it usershare ) and is nearly identical to how you would create a "simple share" on Windows.  In a given situation there may in fact be something wrong with the network and something may be necessary to reconfigure it . Some of these HowTo's may then become necessary, but use the simple method first - no need to overdo things.
[B][COLOR=Blue]
NOTE TO STAN:[/COLOR][/B] The method I described above will not work for you because things that are required to make it work have been removed from your smb.conf. You have a system that works now so as you would say "If it ain't broke don't fix it" ;)

---

