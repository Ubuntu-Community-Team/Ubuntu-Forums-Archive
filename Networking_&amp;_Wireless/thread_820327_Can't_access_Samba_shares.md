---
title: "Can't access Samba shares"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by anton on 2008-06-06
First off, I'm a newbie . . .

I've installed Hardy Heron and successfully setup Samba for file and printer sharing with a Win XP laptop.  The laptop can access shared folders on the Ubuntu machine and print to the printer connected to the Ubuntu desktop.

BUT try as I might I cannot see the workgroup and shared folders in Nautilus.  Places - Network - Windows Network just gives me a blank screen.

I've spent countless hours looking for a solution on the web and fiddling with smb.conf, to no avail.

I can succcessfully ping both machines using either IP address or hostname.

Ubuntu desktop is called anton-desktop, ip is 192.168.0.2.
Laptop is called Jvorster, ip is 192.168.0.3.

Running smbclient -L anton-desktop gives the following result:

Error connecting to 192.168.0.2 (Connection refused)
Connection to anton-desktop failed (Error NT_STATUS_CONNECTION_REFUSED)

Smbtree yields the following:

session request to 192.168.0.3 failed (Called name not present)
session request to *SMBSERVER failed (Not listening on called name)
session request to JVORSTER failed (Not listening on called name)
session request to *SMBSERVER failed (Not listening on called name)

PLEASE give me some newbie-friendly pointers for trouble-shooting.  I really want to get this to work, but it's driving me nuts!

---

### Post by Peter09 on 2008-06-06
Check /etc/samba/smb.conf

In there is a line that specifies your workgroup. You will need to be in the same workgroup as your windows machines for access to work.

Here is my section

> ## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = HOME
   netbios name = TOSHLAPTOP
   security = user




Note you could also experiment with the 
security=user
line, try
security=share

remember to stop and start samba after editing

sudo /etc/init.d/samba stop
sudo /etc/init.d/samba start


PC

---

### Post by dmizer on 2008-06-06
> **anton said:**
> First off, I'm a newbie . . .

I've installed Hardy Heron and successfully setup Samba for file and printer sharing with a Win XP laptop.  The laptop can access shared folders on the Ubuntu machine and print to the printer connected to the Ubuntu desktop.

BUT try as I might I cannot see the workgroup and shared folders in Nautilus.  Places - Network - Windows Network just gives me a blank screen.

configuring smb.conf only works for allowing other computers to see your ubuntu shares.  if you want to set up your computer to see shares on other computers, please see the second link in my sig.

---

### Post by anton on 2008-06-06
Thanks for the response, both of you.

I've already checked the workgroup and other settings in smb.conf.  Everything *looks* fine.

dmizer -- so no amount of tinkering with smb.conf is going to help me see the shares on the local machine?  I guess I should leave well alone then, since the Windows machine can access the Ubuntu machine without any problems, and I don't want to break that . . .

I've tried manually mounting the shares following your very detailed instructions, but haven't been successful.  I just get the "Usage" instructions in the terminal window, so I must be doing something wrong.  Will keep trying . . .

The irony is I actually had this working at some stage, before I started tinkering again.  Nautilus showed the Windows workgroup ("HOME") with the Windows shared folders inside.  But it also showed a second workgroup (called "Workgroup") and that's where the shared folders on the Ubuntu machine were.  Obviously, I wanted both computers to be part of the HOME workgroup, and I think that's why I started experimenting again (and messed things up).  So now on the Windows machine both computers ARE in the HOME workgroup -- but neither the workgroup itself nor the shared folders are accessible on the Ubuntu box.  If only I could retrace my steps!

I'm beginning to think I should just reinstall Samba and the related packages from scratch, but I'm too afraid of losing the connectivity from the Windows machine.  Uggggh . . . why can't this be as simple as setting up file & printer sharing in Windows? I also believe it was a lot easier in the previous versions of Ubuntu.

---

### Post by dmizer on 2008-06-06
yes, if windows can see ubuntu ... no further configuration of smb.conf will change things.

please post the output of:
```
smbtree
```

and post the command you used to attempt to mount (the one you got a usage error from).

---

### Post by anton on 2008-06-06
[INDENT]Code:
anton@anton-desktop:~$ smbtree
Password: 
session request to 192.168.0.3 failed (Called name not present)
session request to *SMBSERVER failed (Not listening on called name)
session request to JVORSTER failed (Not listening on called name)
session request to *SMBSERVER failed (Not listening on called name)
anton@anton-desktop:~$ [/INDENT]

I tried the mount command again, and this time I got:

Code:
[INDENT]mount error 112 = Host is down
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)[/INDENT]

Just to clarify: "Host" here refers to the Windows machine,right? (Sorry, my head is spinning.)  Why would it be reported as "down" -- file and printer sharing is enabled, it can see the Ubuntu machine, and I can ping both machines from each other . . .

Another newbie question: how do you create the boxes for the code in these postings?

Thanks for all the help!

---

### Post by linux6994 on 2008-06-06
To get windows file sharing to work I installed these applications... see attached...

Good Luck

---

### Post by anton on 2008-06-06
Yes,I've got all those installed, except for system-config-samba -- but isn't that just a GUI for smb.conf?

---

### Post by anton on 2008-06-06
Okay, I also installed system-config-samba and added my Documents folder as a share,

I'm assuming it should now show up when I browse the network in Nautilus,the same way remote *and* local folders show up in the Workgroup on a Windows machine?  Well, I'm still greeted with a blank screen when I open "Windows Network" -- and yes, I did restart Samba.

---

### Post by dmizer on 2008-06-06
okay.  well, you installed a bunch of stuff that wasn't necessary, but it doesn't hurt anything.

just to be very clear:
smbfs and samba are each one way.

to share files to windows from ubuntu, you need samba which is a one way service built to host windows shares on a linux computer
to access windows shares in ubuntu, you need smbfs which is a one way protocol built to allow linux to access shares hosted on windows computers.

you've configured samba (via smb.conf) and it works, so it's probably wise to leave that just as it is.

what this looks like to me is that you may have a firewall interfering with your shares.  do you have firestarter or some other iptables configuration running on ubuntu?  alternatively ... are there any firewalls running on your windows computers?

when you followed my howto, did you install winbind and configure /etc/nsswitch.conf as described?

---

### Post by anton on 2008-06-06
Don't know if this is of any use, but I just successfully queried the workgroup and both computers' hostnames with nmblookup.

---

### Post by anton on 2008-06-06
Windows firewall is switched off.

I didn't install any firewall on Ubuntu -- does the default installation set one up?

Winbind is installed.  And here's my nsswitch.conf:

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files wins mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

---

### Post by dmizer on 2008-06-06
please post the output of:
```
sudo iptables -nvL -t filter
```

---

### Post by dmizer on 2008-06-06
also ... let's make sure your winbind daemon is running.

please post the output of the following command:
```
ps -aux | grep winbind
```

---

### Post by anton on 2008-06-06
sudo iptables -nvL -t filter:

[INDENT]Chain INPUT (policy ACCEPT 10621 packets, 9026K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 10245 packets, 4900K bytes)
 pkts bytes target     prot opt in     out     source               destination [/INDENT]

ps -aux | grep winbind:

[INDENT]Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
root      4948  0.0  0.1   8072  1376 ?        Ss   18:43   0:00 /usr/sbin/winbindd
root      4989  0.0  0.1   8072  1220 ?        S    18:43   0:00 /usr/sbin/winbindd
root      5991  0.0  0.0   8072   880 ?        S    19:14   0:00 /usr/sbin/winbindd
root      5992  0.0  0.1   8080  1304 ?        S    19:14   0:00 /usr/sbin/winbindd
anton     6029  0.0  0.0   3008   776 pts/0    R+   20:20   0:00 grep winbind
[/INDENT]

---

### Post by linux6994 on 2008-06-06
I do have the system config for samba installed, that is one of the screenshots

---

### Post by davisha2008 on 2008-06-06
and how doest to start smb.conf?

---

### Post by dmizer on 2008-06-06
> **anton said:**
> sudo iptables -nvL -t filter:

[INDENT]Chain INPUT (policy ACCEPT 10621 packets, 9026K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 10245 packets, 4900K bytes)
 pkts bytes target     prot opt in     out     source               destination [/INDENT]

ps -aux | grep winbind:

[INDENT]Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
root      4948  0.0  0.1   8072  1376 ?        Ss   18:43   0:00 /usr/sbin/winbindd
root      4989  0.0  0.1   8072  1220 ?        S    18:43   0:00 /usr/sbin/winbindd
root      5991  0.0  0.0   8072   880 ?        S    19:14   0:00 /usr/sbin/winbindd
root      5992  0.0  0.1   8080  1304 ?        S    19:14   0:00 /usr/sbin/winbindd
anton     6029  0.0  0.0   3008   776 pts/0    R+   20:20   0:00 grep winbind
[/INDENT]

something is blocking netbios. i don't see anything on your ubuntu computer which would block netbios.  you said there is no firewall on your xp laptop, but that's really what it looks like.

also please post your /etc/samba/smb.conf file.

---

### Post by anton on 2008-06-07
Here are the uncommented lines from my smb.conf.  I know there's a lot of unnecessary stuff; it's based on the default smb.conf. I tried to remove as many access restrictions as possible just to try to get initial connectivity.


[global]
	dns proxy = no
	name resolve order = lmhosts host wins bcast
	log file = /var/log/samba/log.%m
	max log size = 1000
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	security = user
	encrypt passwords = true
	passdb backend = tdbsam
	obey pam restrictions = yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	pam password change = yes
	usershare allow guests = yes

[homes]
	read only = no

[printers]
	comment = All Printers
	browseable = no
	path = /var/spool/samba
	printable = yes
	create mask = 0700

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Documents]
	path = /home/anton/Documents
	writeable = yes
	browseable = yes
	guest ok = yes


In case this is relevant, here are the results from an nmblookup:

anton@anton-desktop:~$ nmblookup 192.168.0.2 -A
Looking up status of 192.168.0.2
	ANTON-DESKTOP   <00> -         B <ACTIVE> 
	ANTON-DESKTOP   <03> -         B <ACTIVE> 
	ANTON-DESKTOP   <20> -         B <ACTIVE> 
	HOME            <1e> - <GROUP> B <ACTIVE> 
	HOME            <00> - <GROUP> B <ACTIVE> 

	MAC Address = 00-00-00-00-00-00

anton@anton-desktop:~$ nmblookup 192.168.0.3 -A
Looking up status of 192.168.0.3
	JVORSTER        <00> -         M <ACTIVE> 
	HOME            <00> - <GROUP> M <ACTIVE> 
	HOME            <1e> - <GROUP> M <ACTIVE> 
	HOME            <1d> -         M <ACTIVE> 
	..__MSBROWSE__. <01> - <GROUP> M <ACTIVE> 

	MAC Address = 00-12-F0-3B-B7-ED

Doesn't this indicate that in principle I should be able to see the machine jvorster (192.168.0.3)?

The only firewall on that machine is the Windows firewall, and that's been turned off.  There is an antivirus program (Fsecure) running -- could that prevent access?

Thanks again for all your help. I really appreciate it.

---

### Post by mahela007 on 2008-06-07
I have a similar problem so I thought i will post it over here rather than open a new thread.

my linux and windows XP computers are networked.
I can access the Windows PC form the linux PC but I cant access the linux computer form my windows computer although it is visible in the network computers window. I have posted a screenshot of the error message i get when i try to acess it. I have SAMBA installed on the linux machine.
the error I get is
"Desktop server SAMBA is no accessible.you might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions"

"parameter is not correct"

---

### Post by dmizer on 2008-06-07
> **anton said:**
> Here are the uncommented lines from my smb.conf.  I know there's a lot of unnecessary stuff; it's based on the default smb.conf. I tried to remove as many access restrictions as possible just to try to get initial connectivity.


```
[global]
	dns proxy = no
	name resolve order = lmhosts host wins bcast
	log file = /var/log/samba/log.%m
	max log size = 1000
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	security = user
	encrypt passwords = true
	passdb backend = tdbsam
	obey pam restrictions = yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	pam password change = yes
	usershare allow guests = yes

[homes]
	read only = no

[printers]
	comment = All Printers
	browseable = no
	path = /var/spool/samba
	printable = yes
	create mask = 0700

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Documents]
	path = /home/anton/Documents
	writeable = yes
	browseable = yes
	guest ok = yes
```
okay, i see a couple of things here that i'm concerned about.

first of all, this won't likely help your problem but it needs to be fixed anyway. these two options mean the opposite thing:
```
security = user
usershare allow guests = yes
```

you should delete the "usershare allow guests = yes" and change "security = user" to this:
```
security = share
```

secondly, there are some things missing from this smb.conf that could cause problems (unless you mistakenly edited them out).

at the very top, under [global], you should add these two options:
```
netbios name = ANTON-DESKTOP
workgroup = HOME
```

restart samba, and run smbtree again to see if there's been any improvement.


> **anton said:**
> Doesn't this indicate that in principle I should be able to see the machine jvorster (192.168.0.3)?

The only firewall on that machine is the Windows firewall, and that's been turned off.  There is an antivirus program (Fsecure) running -- could that prevent access?

Thanks again for all your help. I really appreciate it.

it's no problem.

even though you are able to resolve host name by nmblookup, this is not very helpful.  cifs uses winbind to resolve host names, so if you cannot resolve via winbind (smbtree), neither will cifs.

i don't know anything about fsecure, but if it is purely an antivirus, then it shouldn't cause a problem.

---

### Post by dmizer on 2008-06-07
> **mahela007 said:**
> I have a similar problem so I thought i will post it over here rather than open a new thread.

this is not a similar problem.  you will need to add your ubuntu user name to the samba user group with the following commands:
```
sudo smbpasswd -L -a [COLOR="Red"]ubuntu_username[/COLOR]
sudo smbpasswd -L -e [COLOR="Red"]ubuntu_username[/COLOR]
```
replace "[COLOR="Red"]ubuntu_username[/COLOR]" with your actual ubuntu user name.

if this is not successful, please see the first link in my sig.

---

### Post by anton on 2008-06-07
Progress!

When I click on "Network", I now see an "Anton-Desktop" (the Ubuntu machine) icon alongside the Windows Network icon.  And when I open Windows Network, the workgroup (HOME) appears.  Opening that shows "Anton-Desktop" again.  But still no sign of the Windows machine.

When I run smbtree I now get:

Server requested LANMAN password (share-level security) but 'client use lanman auth' is disabled
failed tcon_X with NT_STATUS_OK
Server requested LANMAN password (share-level security) but 'client use lanman auth' is disabled
failed tcon_X with NT_STATUS_OK

> secondly, there are some things missing from this smb.conf that could cause problems (unless you mistakenly edited them out).

at the very top, under [global], you should add these two options:
Code:

netbios name = ANTON-DESKTOP
workgroup = HOME



Yes, I accidentally edited them out.  But I'm confused here: for the netbios name I had "jvorster" (the name of the remote Windows machine).  So I need to put in the local (Ubuntu) machine's netbios?

---

### Post by dmizer on 2008-06-07
> **anton said:**
> Progress!

When I click on "Network", I now see an "Anton-Desktop" (the Ubuntu machine) icon alongside the Windows Network icon.  And when I open Windows Network, the workgroup (HOME) appears.  Opening that shows "Anton-Desktop" again.  But still no sign of the Windows machine.

When I run smbtree I now get:

Server requested LANMAN password (share-level security) but 'client use lanman auth' is disabled
failed tcon_X with NT_STATUS_OK
Server requested LANMAN password (share-level security) but 'client use lanman auth' is disabled
failed tcon_X with NT_STATUS_OK



Yes, I accidentally edited them out.  But I'm confused here: for the netbios name I had "jvorster" (the name of the remote Windows machine).  So I need to put in the local (Ubuntu) machine's netbios?

remember, smb.conf is configured to allow windows computers to see your ubuntu computer.  the netbios name and workgroup options are in the smb.conf file in order to identify your ubuntu computer.  if you enter information belonging to your windows computer in this file, then there will be problems with netbios resolution (two computers on the network with the same name).

double check the windows workgroup on your xp machine:
To find the _netbios name_ in Windows xp:
[LIST]
[*]start > my computer > view system information (under "system tasks" on the left) > computer name (tab)

The workgroup name is next to "Workgroup"[/list]

---

### Post by dmizer on 2008-06-07
let's do one more thing with your smb.conf file.

first let's make a back up of your current configuration so we can go back to it if this is not successful.
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf-old
```

now edit your /etc/samba/smb.conf file and replace everything in it with this (please just copy and paste everything):
```
[global]
    ; General server settings
    netbios name = ANTON-DESKTOP
    workgroup = HOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

[Documents]
    path = /home/anton/Documents
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = anton
    force group = anton
```
then run these three commands:
```
sudo smbpasswd -L -a anton
sudo smbpasswd -L -e anton
sudo /etc/init.d/samba restart
```

after the samba server restarts, try smbtree again.  even if smbtree is not successful, please try to mount your windows share according to my howto again.

---

### Post by anton on 2008-06-07
Hmmm . . . now the Windows Network window is empty again - not even showing the workgroup or the local shared folder..

Smbtree fails:

session request to 192.168.0.3 failed (Called name not present)
session request to *SMBSERVER failed (Not listening on called name)
session request to JVORSTER failed (Not listening on called name)
session request to *SMBSERVER failed (Not listening on called name)


And when I try to mount the Windows share,I get: "mount error 112 = Host is down".

The Windows machine is still able to see the Ubuntu pc's shared folder and printer.

I'm about ready to give up . . .

---

### Post by mahela007 on 2008-06-07
> **dmizer said:**
> this is not a similar problem.  you will need to add your ubuntu user name to the samba user group with the following commands:
```
sudo smbpasswd -L -a [COLOR="Red"]ubuntu_username[/COLOR]
sudo smbpasswd -L -e [COLOR="Red"]ubuntu_username[/COLOR]
```
replace "[COLOR="Red"]ubuntu_username[/COLOR]" with your actual ubuntu user name.

if this is not successful, please see the first link in my sig.

hi I Followed the instructions you posted. Now i can access my windows shared folder from my Linux PC but it doesnt work the other way round. I still get the same error when I try to access linux from the windows PC.
I didnt modify the smb.conf file. Should I do that as well? I'm an absolute newbie and basically I am groping around in the dark here

---

### Post by dmizer on 2008-06-07
> **anton said:**
> Hmmm . . . now the Windows Network window is empty again - not even showing the workgroup or the local shared folder..

Smbtree fails:

session request to 192.168.0.3 failed (Called name not present)
session request to *SMBSERVER failed (Not listening on called name)
session request to JVORSTER failed (Not listening on called name)
session request to *SMBSERVER failed (Not listening on called name)


And when I try to mount the Windows share,I get: "mount error 112 = Host is down".

The Windows machine is still able to see the Ubuntu pc's shared folder and printer.

I'm about ready to give up . . .

well, the only thing left i have for you is to take a look at the setup on your windows, because everything on your ubuntu machine seems to be set up properly.

did you double check your workgroup in xp?

also in xp, check to make sure that:
[LIST]
[*]client for microsoft networks is installed
[*]file and printer sharing is enabled
[*]netbios is enabled.
[*]netBEUI is disabled.
[/LIST]
howto here: [http://www.homenethelp.com/web/howto/net-xp.asp](http://www.homenethelp.com/web/howto/net-xp.asp)

---

### Post by jonandrews on 2008-06-08
Have a look at my step by step guide to networking between Ubuntu & Windows XP:

[www.europe.eclipse.co.uk/Ubuntu](www.europe.eclipse.co.uk/Ubuntu)

---

### Post by anton on 2008-06-08
> **dmizer said:**
> well, the only thing left i have for you is to take a look at the setup on your windows, because everything on your ubuntu machine seems to be set up properly.

did you double check your workgroup in xp?

also in xp, check to make sure that:
[LIST]
[*]client for microsoft networks is installed
[*]file and printer sharing is enabled
[*]netbios is enabled.
[*]netBEUI is disabled.
[/LIST]
howto here: [http://www.homenethelp.com/web/howto/net-xp.asp](http://www.homenethelp.com/web/howto/net-xp.asp)

I've checked and double-checked all of this a zillion times.  The network is definitely up and running -- the Windows machine can see the workgroup called HOME and can access the files on the Ubuntu machine, as well as print to the printer connected to the Ubuntu machine.  And the firewall is disabled.

On the Ubuntu machine, I was able, before loading the new smb.conf,to see the workgroup as well as the shared folder on the Ubuntu machine, but not the shared folder on the Windows machine.  Now I see nothing in the Windows Network.

There's obviously something I'm missing . . . but what????

---

### Post by anton on 2008-06-08
Well, there definitely is something amiss with the network settings on the Windows laptop, but I'll be damned if I can figure out what it is.  I've booted my desktop in Windows and I can't access the laptop from there either.  This is the situation:

On the laptop (which I've renamed from "jvorster" to "laptop"):
* When I open the Workgroup, I can see the desktop (remote machine) but not the laptop (local machine).
* When I run a search for the laptop by name, it is found and I can open it to access the shared folders.

On the desktop (now running Windows):
* In Workgroup I can see the desktop (local machine) but not the laptop (remote machine).
* When I run a search for the laptop by name, it is found BUT I cannot open it.  Windows gives me this message: "\\laptop is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions."

I've carefully compared the network configurations on both machines and they are exactly the same.  There are no access restrictions as far as I can see and the Windows firewall is disabled.

I guess I should really be posting this in a Windows forum, but thought I'd post here as well just in case somebody has any idea what could be wrong.

A big thank you in the meantime to everybody who tried to help, especially dmizer.  I've learned a lot in the process.

---

### Post by dmizer on 2008-06-08
take a look here: [http://support.microsoft.com/kb/304040](http://support.microsoft.com/kb/304040)

pay special attention to the directions under "Level 5: Shared on the network (Read and Write)"

i suspect you simply have the permissions set up incorrectly on your share.

---

### Post by anton on 2008-06-08
Yip, it's definitely a permissions thing.  I've gone and done everything as far as I could see to give everybody full access to the shared folder -- and now at long last I can see the laptop on the desktop machine, in both Windows and Ubuntu!  But I still can't get to the shared folder.

In Windows I get this message when I click on the laptop's icon: "Logon failure: the user has not been granted the requested logon type at this conputer."

In Ubuntu, smbtree now gives me:

HOME
	\\LAPTOP         		Notebook

Mounting the share appears to be successful, as I don't get any error messages.

Opening "Windows Network" in Ubuntu shows me the workgroup, and opening that I see both computers.  But when I open the laptop, I just get a blank screen.

So I guess I'll just have to keep investigating the intricacies of permissions in Windows . . . The laptop was setup by my university for interfacing with the network there -- perhaps they have secured it in some obscure way?  As I've said, I've removed all restrictions as far as I can see -- everybody has been granted full read and write access to the shared folder.

Just one other question: in the Network screen, the two computers appear alongside the Windows Network, as well as inside the Workgroup.  Is this duplication normal, or does it indicate some configuration issue I should look at?

---

### Post by anton on 2008-06-08
Well, I decided to give PcLinuxOS 2007 a spin from the live CD -- and guess what?  I have perfect access to the Samba shares!  Yes, I can open the files, no problem . . . and I did not have to do a single thing to configure this! After clicking on the laptop's icon, I was prompted for my username and password, and hey presto, I could access everything!

And no, I did not change anything on the Windows machine since my last attempt with Ubuntu.

Go figure . . .

---

### Post by dmizer on 2008-06-08
> **anton said:**
> Yip, it's definitely a permissions thing.  I've gone and done everything as far as I could see to give everybody full access to the shared folder -- and now at long last I can see the laptop on the desktop machine, in both Windows and Ubuntu!  But I still can't get to the shared folder.

In Windows I get this message when I click on the laptop's icon: "Logon failure: the user has not been granted the requested logon type at this conputer."

In Ubuntu, smbtree now gives me:

HOME
	\\LAPTOP         		Notebook

Mounting the share appears to be successful, as I don't get any error messages.

Opening "Windows Network" in Ubuntu shows me the workgroup, and opening that I see both computers.  But when I open the laptop, I just get a blank screen.

So I guess I'll just have to keep investigating the intricacies of permissions in Windows . . . The laptop was setup by my university for interfacing with the network there -- perhaps they have secured it in some obscure way?  As I've said, I've removed all restrictions as far as I can see -- everybody has been granted full read and write access to the shared folder.

Just one other question: in the Network screen, the two computers appear alongside the Windows Network, as well as inside the Workgroup.  Is this duplication normal, or does it indicate some configuration issue I should look at?

how are you attempting to mount at this point?  since you have samba configured for sharing files from ubuntu to windows, you will have difficulty mounting/browsing the share through places > network servers

with my howto, the share is mounted at /media/mountpoint and should be found on the desktop.  if the folder is not on the desktop, it can be found by browsing to places > computer > /media > /mountpoint

---

### Post by anton on 2008-06-09
Okay, for a variety of reasons I've now switched to PCLinuxOS, so I guess I shouldn't really be posting here any more.  But the question I now have is a general one and applies to any distro.  It concerns firewalls.

The only way I could get access to my Windows machine from Linux, was to disable the Windows firewall.  But what are the security implications?  I've just visited another site saying one should NEVER run a PC without a firewall, even if the router has a built-in firewall.  

So how do you reconcile accessibility with security?

In the meantime, let me once more express my gratitude to dmizer for all the hand-holding.  It's largely thanks to you I now have a working network, albeit in another distro.  And when I give Ubuntu another try (as I'm sure i will), I'll definitely be in a better position to get the network up and running.

---

### Post by b0b138 on 2008-06-09
> **anton said:**
> Well, I decided to give PcLinuxOS 2007 a spin from the live CD -- and guess what?  I have perfect access to the Samba shares!  Yes, I can open the files, no problem . . . and I did not have to do a single thing to configure this! After clicking on the laptop's icon, I was prompted for my username and password, and hey presto, I could access everything!

And no, I did not change anything on the Windows machine since my last attempt with Ubuntu.

Go figure . . .


I was under the impression this was related to a bug in Hardy, either with nautilus or gnome. That is why pclinux works and so did gutsy. I'm guessing that since this thread is only a few days old it still hasn't been resolved. :(  

The easiest workaround I know of is that you can still access your windows shares by typing in the whole share name. i.e.   smb://hostname/sharename/

---

### Post by Major_Kong on 2008-06-09
Quick Question, did you install firestarter earlier ?

---

### Post by Mgiacchetti on 2008-06-09
actually i have found that i can access WORKGROUP and MSHOME without having to change MY workgroup... although i cannot see my own machine when WORKGROUP is online, only MSHOME which isnt my workgroup, my workgroup is WORKGROUP... as in the smb file...

interesting....

---

### Post by anton on 2008-06-09
> **Major_Kong said:**
> Quick Question, did you install firestarter earlier ?

No.  Should I, and if I do, can it also cause problems connecting to the network?  If firewalls are a problem on LANs,how should one go about providing security?

---

### Post by dmizer on 2008-06-09
don't worry about firestarter.  a firewall is far more important on windows where services are open to the world even when not in use, whereas this is not true in linux.  and yes, a firewall will inhibit local network activity.

just stick with PClinuxOS as long as it's working for you.  i'm sorry i couldn't get you working in ubuntu correctly, but the important thing is that you have a functional computer which meets your needs.

---

### Post by Major_Kong on 2008-06-10
> **anton said:**
> No.  Should I, and if I do, can it also cause problems connecting to the network?  If firewalls are a problem on LANs,how should one go about providing security?

Yes it can. But it's not a firewall problem, but the settings that firestarter changes. 

[http://ubuntuforums.org/showthread.php?t=190542](http://ubuntuforums.org/showthread.php?t=190542)

---

### Post by anton on 2008-06-11
I've finally discovered the cause of all my hassles. Apparently, there's a bug in gvfs in Ubuntu 8.04 which prevents Nautilus from opening shares on Windows machines. You can read all about it here: [https://bugs.launchpad.net/ubuntu/+s...fs/+bug/207072](https://bugs.launchpad.net/ubuntu/+s...fs/+bug/207072). That thread also has a patch to fix the bug, but my Linux skills don't yet include the application of patches!

With a clean install of Ubuntu (the umpteenth one) I now have no problem accessing the Windows network -- as long as I realize I can't see the shares by double-clicking on the Windows machine's icon. There's no problem accessing them by typing smb://computername/sharename in the address bar.

Hopefully a fix will arrive soon (apparently it is being worked on). Until then, I think this issue should be made widely known (perhaps in a sticky on the forum?), as it seems a lot of people are scratching their heads over this. It's especially confusing for a new Ubuntu convert like me, who just couldn't fathom why, despite carefully following all the advice and instructions, I simply couldn't get it to work. Ironically, the network connectivity is really there "out of the box" -- all I had to do in smb.conf. was specify the correct workgroup.

Despite this bug, I'm really happy with Ubuntu and I'll probably be sticking with it as my OS of choice.

---

### Post by dmizer on 2008-06-11
actually, the bug you mention would not have effected you ability (or in this case: inability) to mount your shares according to my howto.

again though ... most important thing is that it works to your satisfaction.

---

### Post by anton on 2008-06-11
> **dmizer said:**
> actually, the bug you mention would not have effected you ability (or in this case: inability) to mount your shares according to my howto.

again though ... most important thing is that it works to your satisfaction.

Sure, I appreciate that.  I'm just saying that, from the perspective of a new user who wants to get up and running with the minimum of fuss (and technical know-how), it would not even have been necessary to learn to mount the shares if it weren't for this bug.

As it turns out, though, the bug really is no more than a minor inconvenience -- you can access your shares easily enough by entering the address in the Nautilus address bar.  Another workaround is to switch to KDE, as Konqueror isn't affected by the bug.  Or, if you're savvy enough, you can apply the patch that's available here: [https://bugs.launchpad.net/ubuntu/+s...fs/+bug/207072](https://bugs.launchpad.net/ubuntu/+s...fs/+bug/207072).

---

### Post by jbizcocho on 2008-07-11
Here is another discussion about it here.  

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/208531](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/208531)

I spent a while working on it and here is a work around.  Still waiting on a Nautilus gvfs fix but until then, this works just as well and for me, even better.  Use "fusesmb".  See below.

1. Install fusesmb if you don't already have it.
2. "sudo mkdir/media/network/whatever-you-want-to-call-the-folder.
(make it easy on yourself and use short all lowercase names)
3. "fusesmb /media/network/name-of-folder-you-created-in-two"
4. Now go to "Computer" and you should see a mounted directory of the
exact same name you gave in step 2.  All files will be useable etc.

You might need to sudo your fusesmb command... (still working out some
of the details). You don't need to do step 2 if you simply want the
network folder to display the contents of you network.

Note that the shares are mounted so the system thinks they are locally
mounted directories.  Your networked computers will come up as
directories.  The system will treat them as such so you might want to
disable things like previewing of local files as well as it will take
longer for directories to display.

You will have to stop using the Nautilus icon for the network and use
the one fusesmb created as I've found, trying to connect using both
causes Nautilus to slow down while the internal command fails as we've
noted earlier.

---

