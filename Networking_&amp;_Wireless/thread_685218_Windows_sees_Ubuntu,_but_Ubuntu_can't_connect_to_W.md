---
title: "Windows sees Ubuntu, but Ubuntu can't connect to Windows"
date: 2008-02-02
forum: Networking &amp; Wireless
---

### Post by timzak on 2008-02-02
I'm a little frustrated here.  I used to be able to network between Ubuntu and Windows via Samba on my current setup.  Since I don't do it often, I'm not sure if there's been a configuration change or what.  But I can no longer connect to the Windows PC from Ubuntu.  It sees the Windows Network (takes awhile to find), then when I double-click, it shows me my workgroup.  But once I double-click on the workgroup, it takes a long time, then tells me "The folder contents could not be displayed."  The weird part is I have no problem walking to the Windows machine and connecting to my Ubuntu computer.  I've double-checked my Network settings to make sure the workgroup name is correct.  It should be working...it used to work a month ago and I don't think I've changed anything on my computers in that time.  Any ideas?

---

### Post by mbrush on 2008-02-02
having same problem here

the only workaround I found is to use a command like this:

smbmount //192.168.0.x/windows-share ~/mnt/mount-point

---

### Post by timzak on 2008-02-02
Thanks for replying.

Hopefully there is a more permanent solution.  As seldom as I connect to my Windows PC, it seems easier to just walk to it (it's in the next room) and connect to my Ubuntu PC from there to do file transferring.  I hope there's a more elegant solution!

Any other ideas?

---

### Post by psycho5 on 2008-02-02
i'm having the same problem ,except windows can see my pc but can't access it. In ubuntu, I can only see my Windows network, once i open it, I can't see my workgroup in smb:/// 

Everything used to work just fine. All my settings are still the same as they were when the networking was working.

---

### Post by gioland71 on 2008-02-02
Have you tried turning off the Windows firewall? Or at least allowing your linux computer in? I had the same problem and it turned out it was the Norton "super secure" firewall that was refusing the connection (similar sequence of events as you describe).

Cheers!

---

### Post by swerdna on 2008-02-02
The firewall in windows by default allows SMB (Samba) networking through. But other firewalls need to have an opening put in them as hinted by gioland71, so investigate the add-on firewalls. My money is on a flaw in your Samba configuration file as a probable suspect. Can you post the contents into a forum reply. I will check it out. But four things for you to check first:
1: the workgroup name in [global] of smb.conf must be the same as the workgroup name on windows machines.
2: the [global] paragraph in smb.conf must contain the line: **netbios name = something_or_other** where you choose a name you want to see for the icon in Network Neighbourhood
3: add a user to the samba user database, a real Linux logon user, probably yourself. Do that like this: **sudo smbpasswd -a username**
4: It helps VERY MUCH to have this line in [global] of smb.conf:
**name resolve order = bcast lmhosts wins host**
If there's an alternate version, comment it out with a # at the beginning

Restart Samba with **sudo /etc/init.d/samba restart**

Wait 5 mins or reboot to seep around the LAN

If no good post smb.conf

Swerdna

---

### Post by timzak on 2008-02-03
Thanks for your help.  With your help, swerdna, combined with the HOWTO for Samba, I somehow got it working.  I kept playing with different combinations of smb.conf settings.  What finally did the trick was putting this at the end of smb.conf:

> [MyFiles]
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = YOUR_USERNAME
    force group = YOUR_USERGROUP

I just changed the path to my path, and the last two lines I changed to my login name.  Right after I made this change, I was able to log onto the Windows machine.  

Thanks again.

---

### Post by timzak on 2008-02-06
swerdna,

I spoke too soon.  I'm not sure why (and I've changed nothing since my previous post when it started working), but now I can no longer connect from the Ubuntu machine to the Windows one (again).  As before, I have NO PROBLEMS connecting to Ubuntu from Windows.  It's just a one-way street right now.  FYI, I've done the whole password setting thing in Ubuntu, so that I need to enter username and password from Windows to log in.  That works beautifully!  I just wish I could do the same from Ubuntu to Windows!  Here is my smb.conf file if you could have a look and see if you can spot any problems:
> [global]
    ; General server settings
    netbios name = tim-desktop
    
    workgroup = MSHOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

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



[tim-desktop-disk]
path = /media/disk
browseable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = tim

---

### Post by swerdna on 2008-02-07
Turn off Ubuntu firewall if any. Windows xp firewall lets Samba through by default. But third party windows firewalls like Norton, ZoneAlarm etc close Samba off by default. So turn any third party win firewalls off. You can sort those out later.

/media is a folder that's owned by root and consequently is a bad place to locate shares. It's menat as a spot where external media (e.g. usb drives, IPODs etc) are mounted. It's not meant to be a store for personal media files like movies and songs. Ownership of the share by root requires special treatment so I suggest that you change the location. 

Backup smb.conf with this shell command: **sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.backup**

So I suggest that you make a share in the home territory of user tim (or someone else, but I'll use tim as a template), say a folder 'media' at /home/tim/share.

Then open smb.conf for editing with this command: **sudo gedit /etc/samba/smb.conf**. Make these changes to the share: make it like this:
> [tim-share]
path = /home/tim/share
read only = no
force user = tim

Notice to make the share name (e.g. tim-share) <= 12 characters
All the other things like mask 644 were either in error or superfluous.
To access from windows will require password challenge supply tim/password as per the samba user database entry (see below). If you want unfettered access then include this line: **guest ok = yes**

These need to be done to the [global] paragraph:
change these lines:
> [global]
; General server settings
netbios name = tim-desktop

workgroup = MSHOME
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

passdb backend = tdbsam
security = user
null passwords = true
username map = /etc/samba/smbusers
name resolve order = hosts wins bcast

wins support = yes

printing = CUPS
printcap name = CUPS

syslog = 1
syslog only = yes

into this (can use copy/paste):
> [global]
	workgroup = MSHOME
        netbios name = tim-desktop
	server string = ""
        map to guest = Bad User
	passdb backend = tdbsam
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	panic action = /usr/share/samba/panic-action %d
        socket options = IPTOS_LOWDELAY TCP_NODELAY
	invalid users = root
        name resolve order = bcast host lmhosts wins
        printing = cups
        printcap name = cups
        cups options = raw
        use client driver = yes

Then add the owner of the share (in this case tim) to the samba user database with this shell command: **sudo smbpasswd -a tim**.


Reboot Ubuntu and windows

OK try that

Swerdna

PS your smb.conf is so changed from the original that I've attached a copy of the default originakl for you and other in your position for reference

---

### Post by timzak on 2008-02-07
Swerdna,

Thank you.  I don't have time right now to follow your instructions, but I will tonight.  I wanted to ask one question related to your comment about /media/disk being changed to my home directory.  How do I handle this if my /home directory is on a different drive than /media/disk?  Can I have two different physical hard drives BOTH be home?  I ask because I use clonezilla to back up my system (root and home) and I don't want to increase the physical size of the backup file by including all of my digital photos in with the backup. 

Thank you.

---

### Post by swerdna on 2008-02-07
> **timzak said:**
> Swerdna,

Thank you.  I don't have time right now to follow your instructions, but I will tonight.  I wanted to ask one question related to your comment about /media/disk being changed to my home directory.  How do I handle this if my /home directory is on a different drive than /media/disk?  Can I have two different physical hard drives BOTH be home?  I ask because I use clonezilla to back up my system (root and home) and I don't want to increase the physical size of the backup file by including all of my digital photos in with the backup. 

Thank you.
OK I thought it was on the same drive as / and /home - not very clear thinking really. Let's keep it the way you had it. Then make the share in smb.conf like this:
> [tim-share]
path = /media/disk
read only = no
force user = tim


The permissions may need manipulating depending on filesystem and/or mounting. So just try it as is and if problems then report back at that stage.

Swerdna

---

### Post by timzak on 2008-02-09
Swerdna,

Wow, everything seems to be working great now!  I'll keep trying it over the next few days and report back if the connection problems come back.  Otherwise, thank you again for your help!

---

### Post by swerdna on 2008-02-09
> **timzak said:**
> Swerdna,

Wow, everything seems to be working great now!  I'll keep trying it over the next few days and report back if the connection problems come back.  Otherwise, thank you again for your help!

A pleasure to help

---

### Post by phlsphr on 2008-02-09
Swerdna, 

I just want to thank you again for that very helpful post.  I had a similar problem to timzak and your suggestion fixed it for me too.  

phlsphr

---

### Post by swerdna on 2008-02-09
> **phlsphr said:**
> Swerdna, 

I just want to thank you again for that very helpful post.  I had a similar problem to timzak and your suggestion fixed it for me too.  

phlsphr

Glad it worked for you too. :)

---

### Post by quantumboy85 on 2008-02-09
I was having the exact same problem that timzak initially described. I have 3 computers running 7.10 (one has Ubuntu server with Gnome installed) and each used to see and connect the windows machines and smb network drive fine but each were suddenly unable to see any machines on the network. This seemed to happen all at once and I never messed with the network settings on any other them. Is it possible that some update came through that messed up the smb.conf file, I noticed this about a week ago?
I got one machine working and haven't tried the others yet. I did only the following 3 things to the conf file, restarted and everything seemed fine:

1. Added the line " netbios name= COMPUTER_NAME", it was missing
2. Added the line "name resolve order = bcast lmhosts wins host", it was missing
3. Changed the line ";   wins support = no"  to  "   wins support = yes"

I'll now go try this on the other two machines and see if there is success.

---

### Post by swerdna on 2008-02-09
> **quantumboy85 said:**
> I was having the exact same problem that timzak initially described. I have 3 computers running 7.10 (one has Ubuntu server with Gnome installed) and each used to see and connect the windows machines and smb network drive fine but each were suddenly unable to see any machines on the network. This seemed to happen all at once and I never messed with the network settings on any other them. Is it possible that some update came through that messed up the smb.conf file, I noticed this about a week ago?
I got one machine working and haven't tried the others yet. I did only the following 3 things to the conf file, restarted and everything seemed fine:

1. Added the line " netbios name= COMPUTER_NAME", it was missing
2. Added the line "name resolve order = bcast lmhosts wins host", it was missing
3. Changed the line ";   wins support = no"  to  "   wins support = yes"

I'll now go try this on the other two machines and see if there is success.

If you have **wins support = yes** on machine **A** you have to tell every other computer on the LAN to get their pairings of netbios names -vs- IP addresses for all computers from computer**A**. And no other computer can contain the line **wins support = yes**. Further to that, computer A must have a fixed IP address.

So your plan is a bad one, sorry. I recommend instead for you take the line completely out or use the alternate **wins support = no**. Wins server was designed for advanced users with full domain names and multiple subnets -- for big LANs, government departments, corporations etc.

Also I suggets this: **name resolve order = bcast host lmhosts wins** is marginally better than tis: name **resolve order = bcast lmhosts wins host** because you're not coding netbios names -vs- IP addresses into the lmhosts files

Swerdna

---

### Post by quantumboy85 on 2008-02-09
All the computers worked with the changes I stated, however I followed your suggests and reversed those configurations. So I guess the only thing wrong was the lack of a netbios name on each computer. Thanks.

---

### Post by swerdna on 2008-02-09
> **quantumboy85 said:**
> All the computers worked with the changes I stated, however I followed your suggests and reversed those configurations. So I guess the only thing wrong was the lack of a netbios name on each computer. Thanks.

That's great. For the benefit of others who read this thread B4 it fades. You were lucky IMHO. But, hey, what works for you, works for you :lolflag:

---

### Post by timzak on 2008-02-09
I have to chime in and say that I (ignorantly) have each computer on my LAN set up as WINS=yes and it is working.  I didn't realize it wasn't supposed to be that way til you just said so.

Here is my full setup:

Cable modem (dynamic IPs? not sure), wired router (I think the router maintains fixed IPs for me?), 4 computers.  My main desktop (Gutsy 64bit); wife's desktop (Windows 2k); laptop (Gutsy 32bit); garage computer (Gutsy 32bit).  All three Gutsy computers are set with identical smb.conf files (except for the netbios names, share descriptions, and paths) and so far (since last night) all seems to be working better than it ever has before.  

What's weird is when I first set the network up, I didn't have to touch smb.conf for it all to just work.  I'm not sure what happened, but it seems like what quantumboy said about an update coming through and messing things up might be a possibility?

Is there a preferred way I should set up my LAN?

Thanks.

---

### Post by swerdna on 2008-02-10
> **timzak said:**
> I have to chime in and say that I (ignorantly) have each computer on my LAN set up as WINS=yes and it is working.  I didn't realize it wasn't supposed to be that way til you just said so.

Here is my full setup:

Cable modem (dynamic IPs? not sure), wired router (I think the router maintains fixed IPs for me?), 4 computers.  My main desktop (Gutsy 64bit); wife's desktop (Windows 2k); laptop (Gutsy 32bit); garage computer (Gutsy 32bit).  All three Gutsy computers are set with identical smb.conf files (except for the netbios names, share descriptions, and paths) and so far (since last night) all seems to be working better than it ever has before.  

What's weird is when I first set the network up, I didn't have to touch smb.conf for it all to just work.  I'm not sure what happened, but it seems like what quantumboy said about an update coming through and messing things up might be a possibility?

Is there a preferred way I should set up my LAN?

Thanks.

From what you say, the linux computers will attempt to find the network workstations according to name resolve order = whatever list.
Wins will fail because the wins server is kaput
lmhosts will fail because no name/address pairs were put into the lmhosts file
host will fail because the name/address pairs weren't put in the /etc/hosts file
bcast will work, but inefficiently because it's not the first in the resolve-order list.

The  netbios name if it's missing from smb.conf will default to the Linux hostname, found in the file /etc/hosts.

So in a roundabout fashion your network has managed to stumble on track - and so SUCCESS!
Normally you'd get network blindness and hair loss, but hey it works in this case for you.

Swerdna

---

### Post by timzak on 2008-02-10
So at the very least, I should put bcast first in the resolve-order list?

I hate to  continue asking you questions on this topic when it is working for me, but can you point me to a good howto on setting up WINS properly?  I'd like to attempt to do it right.  I guess before I can do anything, I need to know if my router is providing me a static IP, because I'm almost positive that from my cable provider it is dynamic.  

Thanks, swerdna.

---

### Post by swerdna on 2008-02-10
> **timzak said:**
> So at the very least, I should put bcast first in the resolve-order list?

I hate to  continue asking you questions on this topic when it is working for me, but can you point me to a good howto on setting up WINS properly?  I'd like to attempt to do it right.  I guess before I can do anything, I need to know if my router is providing me a static IP, because I'm almost positive that from my cable provider it is dynamic.  

Thanks, swerdna.
Put bcast first unless you use a wins server in which case put wins first and bcast second. It works its way along the list until it gets success.

Routers always serve dynamic IP addresses. If you configure the NIC for dynamic (the do-nothing default) it will get an IP from the DHCP server built into the router. If you want a static address for the wins server, just use the GUI tool to code one in. Then that computer will not bother negotiating an IP with the router when it boot up.

HowTo wins server:
Just out this in the comoputer you choose to be the wins server **wins support = yes** and set it's IP addreess with the GUI. Check first what it's getting from the router and stick with that. For this demo suppose it's gettin g 192.168.1.1. Well code that in with the gui.

Then leave the other computers to get their IP dynamically if you like. But in their [global] of smb.conf put this line:
**wins server = 192.1681.1**

Make them all: **name resolve order = wins bcast host lmhosts**

You also make the windows boxes aware that they should use the 192.168.1.1 (or whatever) in the network connection settings 

That's brief so if obscure in places just ask

Swerdna

---

