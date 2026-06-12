---
title: "Stupid noob: Windows doesn't see Ubuntu box"
date: 2005-05-05
forum: Networking &amp; Wireless
---

### Post by fallsroad on 2005-05-05
I have two Windows boxes networked via a router.

Ubuntu box is also attached to the router, has Internet connectivity, and can see the two Windows boxes. It can also open shared folders on both Windows boxes.

Neither Windows box can even "see" the Ubuntu box. I fumbled to set up a share, but that doesn't seem to have helped. Also tried to follow the how-tos for networking to no avail.

This is probably really easy, but I don't even know if the trouble is in Windows network settings or Linux.

Any help is truly appreciated. I am attempting to flee Windows altogether. :)

---

### Post by ltmon on 2005-05-06
I think your ubuntu box has to run a Samba server to allow windows to see it's shared drives.

[http://ubuntuguide.org/#sambaserver](http://ubuntuguide.org/#sambaserver)

Cheers,

L.

---

### Post by fallsroad on 2005-05-06
I followed the instructions - samba was already installed, and I edited the conf as directed by the guide. Then I set up a share folder.

But Windows still cannot see the Linux box at all.

Any further pointers (please refrain from baseball bats!) are much welcomed.

---

### Post by WakkiTabakki on 2005-05-06
Can you ping Win from Ubuntu, and the other way 'round?

And also, post your /etc/samba/smb.conf (but, please remove all comments first, it's huge!)

/N

---

### Post by Che on 2005-05-06
Sorry to interrupt on this threat but ím having the same issue.
Samba setup as described etc. Ubuntu seems to work (no error messages) but no wat to reach the defined directory from XP on the linux machine.
Have setup the network on XP again but that did'nt help either....  any ideas....   :confused:

ps: I can ping the linux machine

---

### Post by WakkiTabakki on 2005-05-07
[QUOTE=Che]Sorry to interrupt on this threat but ím having the same issue.
Samba setup as described etc. Ubuntu seems to work (no error messages) but no wat to reach the defined directory from XP on the linux machine.
Have setup the network on XP again but that did'nt help either....  any ideas....   :confused:

ps: I can ping the linux machine[/QUOTE]


Again, I believe the answer is in your smb.conf, so please post it...

/N

---

### Post by Che on 2005-05-07
thanks for helping, you can find the conf file here: [dummy.txt](http://www.limasol.com/files/dummy.txt) 

I hope it can tell you something.   Please don't be too hard on me, it's all new for me and I try to understand it...    :roll:

---

### Post by TopDog on 2005-05-07
In the 
```
  # Change this to the workgroup/NT-domain name your Samba server will part of    
workgroup = UBUNTU
``` 
Try changing the workgroup name to the exact same as you Windblows machine uses.

You can also try to install the Samba Webmin to get a more GUI approach.

I've also set up **proftpd**, think it works a bit faster, at least here where I only use IEEE802.11b between my machines. Then SMB is sooooo slow, but FTP give me good speeds.

PS: On Warty I had no problems using Samba to print, but now, with Hoary (clean install) I get access denied. Anyone knows why? Here is the print conf:
```
[Epson_Stylus] 	
printer = Stylus-Color-740 	
guest account = gaute 	
printable = yes 	
writeable = yes 	
path = /tmp 	
comment = Printer 	
create mode = 0700 	
guest only = yes 	
public = yes  

[print$] 	
guest account = gaute 	
comment = Printer 	
writeable = yes 	
public = yes 	
guest only = yes 	
path = /var/lib/samba/printers
```

---

### Post by Che on 2005-05-08
> Try changing the workgroup name to the exact same as you Windblows machine uses. 

Was already defined on Windows as on Linux: UBUNTU 
Even in uppercase.   :-?

---

### Post by WakkiTabakki on 2005-05-09
[QUOTE=Che]Was already defined on Windows as on Linux: UBUNTU 
Even in uppercase.   :-?[/QUOTE]

Did you run smbpasswd on your ubuntu machine?

/N

---

### Post by blindpete on 2005-05-09
Hello and thankyou for a womderfull system!

I am attemting to set up a shared folder on the linux-ubunto box.  There are macs and winXP pro machines on the network.  I followed the instructions in:

[http://www.ubuntulinux.org/wiki/SettingUpSamba](http://www.ubuntulinux.org/wiki/SettingUpSamba) 

However when I attempt 
**[FONT=Courier New]sudo smbpasswd -a *username*[/FONT]**

it appears to work BUT when finish the second password entry I get an error message:> 
Failed to initialise SAM_ACCOUNT for user *username*. Does this user exist in the UNIX password database ?
Failed to modify password entry for user *username*

Contrary to others above, I can see the linux-ubunto box in the network browser on XP, however I can not log in.  The account is always rejected.

[B]Here is my smb.conf:
[/B]> 
[FONT=Courier New][global]
   workgroup = Home
   server string = %h server (Samba, Ubuntu)
;   wins support = no
;   wins server = w.x.y.z
   dns proxy = no
;   name resolve order = lmhosts host wins bcast
   log file = /var/log/samba/log.%m
   max log size = 1000
;   syslog only = no
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
;   security = user
   encrypt passwords = true
   passdb backend = tdbsam guest
   obey pam restrictions = yes
;   guest account = nobody
   invalid users = root
;   unix password sync = no
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
;   pam password change = no
;   load printers = yes
;   printing = bsd
;   printcap name = /etc/printcap
;   printing = cups
;   printcap name = cups
;   printer admin = @ntadmin
;   preserve case = yes
;   short preserve case = yes
;   include = /home/samba/etc/smb.conf.%m
   socket options = TCP_NODELAY
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
;   domain master = auto
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
wins support = no
[homes]
   comment = Home Directories
   browseable = yes
   writable = yes
   create mask = 0775
   directory mask = 0775
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no
[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
;   write list = root, @ntadmin
[Home]
path = /home/benstack
comment = Ben's Desktop
available = yes
browseable = yes
public = yes
writable = yes[/FONT]


---

### Post by Spoofhound on 2005-05-10
I've had similar problems with my machines. I've followed the HOW TOs, setting up Samba, user, password etc. It all works only if I disable the Firestarter firewall. 

I've tried setting policy, opening Samba ports, specifying ip addresses, etc. Results vary, sometimes it seems to work, sometimes not.

However, when I disable Firestarter I can see and access windows shares from my linux machine and vice versa with no problems. This is not exactly a "solution", but it might help speed the process.

---

### Post by Tremblay on 2005-05-11
I experience similar problems with my network. But I found out that, in order to have Windows machines see my Ubuntu share over the network, I have to restart Samba after each fresh boot (browsing the forums to figure out how to get around this).

```
sudo /etc/init.d/samba restart
```

I followed the instructions at: [http://www.ubuntuforums.org/showthread.php?t=26438](http://www.ubuntuforums.org/showthread.php?t=26438)

---

### Post by m0e on 2005-05-14
I did a search for my problem and this thread seemed to be the closest to my problem so I decided to post here instead of starting a new thread. 
I have a dual boot computer running Suse 9.2 and Windows XP Home, a Mandrake 10.1 box I use as a print server, an Ubuntu 5.04 box, and a notebook running Windows XP Pro. For some reason the Suse partition keeps losing the network connection so I decided to upgrade to 9.3 rather than try to figure out what is wrong. The only machine I wanted to leave running long enough to get the 8gb bittorrent download of the Suse 9.3 DVD ISO that had enough space on the hard drive was the Ubuntu box. But the only machine I have with a dual layer DVD burner is the Win XP notebook. The problem I am having is my Windows machines can’t access the Ubuntu box. It shows up in the workgroup folder but I get an access denied message when I try to browse it. All of the machines can connect to the Mandrake box and use the printer and the Mandrake box can browse the Ubuntu box using Samba. The Mandrake box has Samba 3.0.7 and the Ubuntu box is using Samba 3.0.10
Here is the smb.conf file on the Mandrake box:

[global]
log file = /var/log/samba/log.%m
smb passwd file = /etc/samba/smbpasswd
load printers = yes
printer = myprinter
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
map to guest = bad user
encrypt passwords = yes
user = user1,user2,user3
printer admin = @adm
dns proxy = no
netbios name = mandrakebox
server string = Samba Server %v
printing = cups
only user = yes
workgroup = myworkgroup
os level = 20
printcap name = cups
security = user
max log size = 50

[sharedfolder]
revalidate = yes
valid users = user1,user3,@user1,@user3
public = yes
user = user1,user3,@user1,@user3
path = /home/user1/sharedfolder

[myprinter]
printable = yes
public = yes
user = user1,user2
only user = no

This is the smb.conf file on the Ubuntu box:

[global]
log file = /var/log/samba/log.%m
smb passwd file = /etc/samba/smbpasswd
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
map to guest = bad user
encrypt passwords = yes
user = user1
dns proxy = no
netbios name = ubuntubox
server string = Samba Server %v
only user = yes
workgroup = myworkgroup
os level = 20
printcap name = cups
security = user
max log size = 50

[sharedfolder3]
path = /root
available = yes
browseable = yes
public = yes
writeable = yes


[sharedfolder2]
path = /home/user2
available = yes
browseable = yes
public = yes
writeable = yes


[sharedfolder]
valid users = user1,@user1
user = user1,@user1
path = /home/user1
available = yes
browseable = yes
public = yes
writeable = yes


So to recap:
XP Home machine can print to and share files with Mandrake, Ubuntu machine is in workgroup folder but not browseable. 
XP Pro machine can print to and share files with Mandrake, Ubuntu machine is in workgroup folder but not browseable. 
Mandrake machine can share files with XP Home, XP pro, and Ubuntu.
Ubuntu machine can print to and share files with Mandrake, both XP machines are visible in Nautilus/Network window but access is denied when attempting to browse them.
If Ubuntu has a firewall by default how do I set that to allow LAN access? I used Webmin to set up the Samba server on the Mandrake box. Is there something like that included in Ubuntu? Or is there an error in my smb.conf file? Oh and the Mandrake box only has a 10gb drive so I can't transfer the ISO to it and then transfer it to the laptop, not enough space left.

Well it’s getting late here so I’m going to bed. Hopefully I will find some suggestions when I get up in the morning. And I would like to thank you in advance for any help with this.

---

### Post by blindpete on 2005-05-14
I had the exact problem.  I could see the ubuntu box in the work group but could not browse, it would never accept the login.

1. I added a Samba User with the same name as a user already on the ubuntu box but with a different password.  

2. I restarted the samba server on ubuntu

3. Then on winXp Pro I logged in as that user with samba password and it works.  I can browse the shares on the ubuntu box.

Here is the thread that helped me
[http://ubuntuforums.org/showthread.php?t=33313](http://ubuntuforums.org/showthread.php?t=33313)
 
Good Luck!

---

### Post by m0e on 2005-05-14
Using smb4k on the Mandrake box I can browse the shares on the Ubuntu box. So I believe the Samba server and user accounts are set up correctly on the Ubuntu machine. But using the same user name and password information on the Windows machines I get a popup saying "\\Ubuntu is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions. The network path not found." But I can browse shares on the Mandrake box from either Windows box using the appropriate user name and passwords for that box. So I believe the Windows boxes are set up correctly for accessing Samba shares. 
Still no joy here.

---

### Post by m0e on 2005-05-14
Well I came up with a temporary solution to my immediate problem. I found a 10bg hard drive, hooked it up with my ide/usb connecter, saved the files I needed on it to another machine, and am currently copying the Suse DVD ISO to it. With the USB 1.1 on the Ubuntu machine it should only take a couple of hours to copy, LOL. Then I should be able to copy it to the laptop and burn the disk. But I still have the problem of no network connection between Ubuntu and Windows, so if anyone else has any other suggestions they would be greatly appreciated. I have read through all the how-to’s linked in this thread and the links inside the links, still no joy. I just don’t understand what I could be doing wrong since Samba works perfectly between the Ubuntu box and the Mandrake box and it also works perfectly between the Windows machines and the Mandrake box. Once again any help would be appreciated.

---

### Post by Che on 2005-05-15
yea, as defined in [http://www.ubuntuguide.org/#installsamba](http://www.ubuntuguide.org/#installsamba) 

also question:
is there any validation of user from and to Windows ? I assume that setting this up like in the tutorial all windows users can get to this filespace on the lnx machine. Is this correct ?

ps: many thanks for helping me out until now. Iknow this is very frustrating for all of you also but I really trying to solve this, whouldn't like to put my old W98 on that pc again.....  this OS is really cool. :cool:

---

