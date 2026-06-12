---
title: "Can't browse windows network, can access via smb"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by richtea on 2009-04-30
Hi,

I can connect to specific shared folders on an XP box on my home network by the following:

alt + f2
smb://192.168.1.117/Shared

but when I go to places > network and try and browse my network, I get an error can't access file list from server, and it is very very slow to tell me this.

Any ideas why?

---

### Post by cariboo on 2009-04-30
Are your two computers in the same workgroup? Depending on the Windows version, Home versions default to MSHOME, while pro versions default to WORKGROUP. 

There are two ways to change the workgroup:

[list]
[*] Install samba and edit the workgroup name in /etc/samba/smb.conf
[*]Press Alt-F2 and type:
```
gksu gconf-editor
```
then navigate to System-->smb, right click workgroup and select edit, add a new name and exit. The change will take effect after a rebot.
[/list]

---

### Post by richtea on 2009-05-05
Tried both those methods, together and separately, and it still doesn't work browsing the network - get error "unable to mount volume, failed to retrieve share list from server".

Anyone have any other ideas?

---

### Post by roger_1960 on 2009-05-05
Hi

Have you tried the smb:// address in the nautilus location box.  If it works, bookmark it.  I find that smb://machinename/sharename as the location works.

---

### Post by Dngrsone on 2009-05-05
Stoopid question-- do you have a network server?  In other words, is there a machine on the network issuing IP addresses (DHCP)?

---

### Post by richtea on 2009-05-05
> **Dngrsone said:**
> Stoopid question-- do you have a network server?  In other words, is there a machine on the network issuing IP addresses (DHCP)?

Networking is not my strong point, but I don't think so. Have modem bridged to router (router is set to PPPoE), and then 1 XP pc connected by wired network, and 2 ubuntu laptops connected by wireless. Actually XP might be DHCP? Should I set up static a IP for the XP machine?

Will try what Roger suggests too!

---

### Post by Dngrsone on 2009-05-05
Your router should be set up as a DHCP server.  Also, you need to enable sharing on the Windows machines to be able to see anything.

---

### Post by richtea on 2009-05-06
> **Dngrsone said:**
> Your router should be set up as a DHCP server.  Also, you need to enable sharing on the Windows machines to be able to see anything.

Router has DHCP enabled, but XP machine has a static IP. Ubuntu machine has dynamic IP assigned by router.

Still doesn't work using places>network, but roger_1960's idea of using address bar works, so I'm going to use that!

Cheers for all your help :)

---

### Post by antmenj on 2009-05-06
Should he be useing a mix of DHCP and static IPs from the same router:???:

---

### Post by Dngrsone on 2009-05-06
> **antmenj said:**
> Should he be useing a mix of DHCP and static IPs from the same router:???:

That's fine.  He hasn't said whether he has enabled file sharing in Windows yet.

---

### Post by richtea on 2009-05-07
Yes, I've enabled sharing of the particular folders/drives on my XP machine I want to share. I'm assuming this wouldn't be the issue, or I wouldn't be able to use Rogers solution would I?

Regarding DHCP/static IP issue, I followed the advice at portforwarding.com, and set a dhcp range on my router - which I use for devices I occasionally attach - laptops, ipod etc. and then my main machine (the XP one) has a static IP outside of that range - for portforwarding purposes.

---

### Post by Dngrsone on 2009-05-07
> **richtea said:**
> Yes, I've enabled sharing of the particular folders/drives on my XP machine I want to share. I'm assuming this wouldn't be the issue, or I wouldn't be able to use Rogers solution would I?

<--- Not a mind reader.  Also not in the mood for childish games and attitude.

> **richtea said:**
> Regarding DHCP/static IP issue, I followed the advice at portforwarding.com, and set a dhcp range on my router - which I use for devices I occasionally attach - laptops, ipod etc. and then my main machine (the XP one) has a static IP outside of that range - for portforwarding purposes.


Glad to see you did your homework in that respect.

---

### Post by richtea on 2009-05-07
> **Dngrsone said:**
> <--- Not a mind reader.  Also not in the mood for childish games and attitude.

Hey, sorry dude, really didn't mean it that way. Was meant in all sincerity, just figured that won't be the issue.

Last people I want to p**s off are fellow ubuntuers.

Sorry mate! :P

---

### Post by fuzzyworbles on 2010-05-20
same exact issue here. i know the problem isn't with my samba server because it's accessible from windows machines. since lucid, samba clients can't browse the samba/ms file share network.

when i use smbtree, i get "cli_start_connection: failed to connect to MYTHICAL<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL" .. it *can* find the machine, but not the shares/resources.

some post elsewhere suggested enabling lanman in the server's smb.conf. i tried that, but with no avail. 

a solution or suggestion to this problem would be really appreciated.

---

### Post by Nythain on 2010-05-20
its a gvfs problem, gotta wait to see if they iron it out in next gnome release

---

### Post by fuzzyworbles on 2010-05-23
yeah, it appears to be related to gvfs, however according to 
[https://bugs.launchpad.net/ubuntu/+source/libgnome-keyring/+bug/530605](https://bugs.launchpad.net/ubuntu/+source/libgnome-keyring/+bug/530605)
it's been fixed. 

... i'm gunna switch over to linux and see if deleting seahorse passwords [and if necessary] purging and reinstalling various related packages does the trick (i'm already totally updated, so that can't be the issue)

edit: 
ok, got it. the above didn't work, but this did: on samba server you can't use security=share anymore; it has to be security=share. this alone, however, didn't fix the problem. while perusing other samba problem related posts on this and other fora, i added the following lines to smb.conf global section:

client NTLMv2 auth = Yes
client lanman auth = Yes
client signing = auto
server signing = auto
client schannel = Auto
server schannel = Auto

now samba CLIENTS can work with my samba server. because these measures (whatever the hell they do) made it possible to use samba clients when windows clients were already working with zero tweaking of the server, it seems clear that the new samba client distribution is to blame. i don't know if it's by design or a bug. point is, it works and i'm happy.

OP might want to mark this as SOLVED.

---

