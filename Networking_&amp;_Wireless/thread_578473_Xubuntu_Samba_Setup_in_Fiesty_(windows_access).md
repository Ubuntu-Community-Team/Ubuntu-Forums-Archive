---
title: "Xubuntu Samba Setup in Fiesty (windows access)"
date: 2007-10-17
forum: Networking &amp; Wireless
---

### Post by jdier on 2007-10-17
I am not quite a newbie, but I am only a desktop user using Xubuntu for simple desktop tasks, printer sharing, file share and some Gimp and CAD...

Anyway, since Breezy (and fedora before that) I have struggled with Samba.  The only system I really had luck with was a Kubuntu system.  I typically wait for one of my buddies to come over and they fix it for me.

Here is what I want:  
Xubuntu Machine set up with Samba shares so Any windows machine on my home network can read and write files in a directory called /home/share/  

I have the permissions set up correctly for that directory but when I try to access from Windows I see the computer in my workgroup (WORKGROUP) but when I click on it I get [PHP]\\xdesk is not accessible.  You might not have permission to use this network resource.  Contact the Administrator of this server to find out if you have access permissions.  

the server service is not started[/PHP]

So, I am getting that this is telling me to set up smb passwords for all users that match their windows log ons, but what I would rather have (and HAVE had on all of my last machines) is a pop up that requires me to type in a login and password each time I access that share, or no log in or password requirements at all.

With that said, any help or guidance would be greatly appreciated.  I am not defecting from ubuntu (Xubuntu) any time in the future, but would rather work this out myself and document it instead of waiting for one of my buddies to visit.

Thanks in advance for the help.

Jim

---

### Post by jdier on 2007-10-17
Well, I have it running.  Here is what I did.

```
sudo mousepad /etc/samba/smb.conf

```

I blew away everything in there and replaced with this:

[PHP][global]
netbios name = xdesk
server string = xdesk_share
workgroup = Workgroup
hosts allow = 127. 192.168.0.
printcap name = /etc/printcap
load printers = yes
printing = cups
cups options = raw
security = share
username level = 8
password level = 8

wins support = no
wins server = 
wins proxy = no
dns proxy = no
preserve case = no
winbind use default domain = yes
idmap uid = 16777216-33554431
idmap gid = 16777216-33554431
template shell = /dev/null

[share]
path = /home/share/
comment = xdesk_share
guest ok = yes
read only = no
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup
available = yes
browsable = yes
public = yes
writable = yes[/PHP]

I saved that then I verified that permissions were aggressively open:

```
sudo chmod -R 777 /home/share/

```

Then I restarted samba:

```
sudo /etc/init.d/samba restart

```

I still have to work out the printing aspect, but what this gives me is a viewable computer (Name in windows neighborhood = xdesk_share (Xdesk) with a comment = xdesk_share) that when I click on it I see a "Printers and Faxes" link and a "share" folder link.  When I click on the 'share' folder I see the folders inside and I have full read and write privileges WITHOUT needing to enter a username or password.

I need to test from other machines, but right now from my work WinXP machine, all is good.

Hope this is useful to others.

Jim

---

### Post by MarkWarwick on 2007-12-11
thanks for the pointers... was bugging me that

---

