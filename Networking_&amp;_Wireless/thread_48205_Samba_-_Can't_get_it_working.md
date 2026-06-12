---
title: "Samba - Can't get it working"
date: 2005-07-11
forum: Networking &amp; Wireless
---

### Post by Win2Kuser on 2005-07-11
Hi Guys/Gals, it's a newbie here I'm afraid :)

I have taken the leap into Linux, and I'm having a few problems *talking* to Windows boxes.

I have Samba running, and I have changed my smb.conf file to share out a couple of folders etc, but I can't seem to access it from windows.

Heres where I'm up to;

If I do a search for computers from windows and type in the ip of the Ubuntu box, it will list it, and I can click it and access it etc, so at least I have something shared and working, but it just won't show up in My Network Places.

At the same time though, if I select Places and Network Servers from Ubuntu, I get a box with a Windows Shares icon, clicking this just brings up and empty box, so I can't seem to access the Windows boxes from Ubuntu.

As far as I can see, Samba is running, as are the nmbs and smbd deamons, I tried manually starting them with /usr/sbin/nmbd -D etc, but that made no difference, I have also ran testparm, and I get no errors.

A bit of info about the network;
I have an adsl router connected to several switches and a total of 15 boxes, 14 of which are Windows XP or 2K, all are on the Main workgroup and use fixed IP's, the Ubuntu box is also using a fixed IP, and will connect to the gateway (router) without problem and access the internet etc.

All the windows boxes are logged in as Administrator as I run a DC client (Find-a-Drug) and run a job queue server, difference usernames causes problems with this, so it's just easier.

Could this be a part of the problem, i.e. I use Administrator in Windows, but set up a username as mark in Ubuntu?

This is what my /etc/samba/smb.conf file looks like, I have removed all the commented out lines out to save space;
[global]

   workgroup = Main
   netbios name = ubuntu64

   server string = %h server (Samba, Ubuntu)

   dns proxy = yes

   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0

   panic action = /usr/share/samba/panic-action %d

   encrypt passwords = true
   passdb backend = tdbsam guest

   obey pam restrictions = yes

   invalid users = root

   socket options = TCP_NODELAY

wins support = no
[homes]
   comment = Home Directories
   browseable = yes
   writable = yes
   read only = no
   writable = yes
   create mask = 0700
   directory mask = 0700

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

[mark]
comment=Windows Share
path = /home/mark
available = yes
browseable = yes
public = yes
writable = yes
write list=mark,Administrator,administrator,root
read only = no

[main]
comment = Main Drive Folder
path = /
available = yes
browsable = yes
public = yes
writable = yes
write list = mark,Administrator,administrator,root
read only = no

Any ideas what I'm doing wrong?  I would ideally like to get probably 10 of these machines running Ubuntu as it's faster (and better) than Windows, but I don't want to plunge right into it until I know I can access the machines from the Windows 2000 AS job queue server and other machines.

Thanks in advance :D

Please be gentle with me though, I am still learning the basics :)

---

### Post by slippy on 2005-07-11
Can you access your samba shares from your Windows machine after searching and finding it? Does it prompt you for a password?

Well, it depends on what kind of security you want. If you are just on a small internal network, and are not too worried about security, then you can add this to your global section...

security = share

*The default for Samba on Ubuntu is security = user*

This is what got it working for me. Even if this is not the solution to your immediate problem, you might remember this for the future.

---

### Post by Win2Kuser on 2005-07-12
Thanks for the reply slippy :)

I tried the security = share, but it made no difference :(

I did have a little play with it though, and now I can access computers from Ubuntu, but it asks me for a Username and password to connect, I type these in right, but it won't take it for some reason :confused:

One thing I have noticed, when searching for 10.0.0.19 (the ip of the Ubuntu box), it has now created a quick click icon in My Network Places listed as 'mark on Ubuntu64 server (Samba, Ubuntu)(10.0.0.19)', but it is listed at the bottom under Internet links, and not at the top with the Network links - WTF!

Could this be down to a netbios name issue, and if so, anyone know how to resolve it?

If I open up My Computer, I can type into the address bar //10.0.0.19/ and it will show the shares, but if I type in //Ubuntu64/ it fails to find it.

Thanks again...

---

### Post by Win2Kuser on 2005-07-29
[QUOTE=Win2Kuser]Thanks for the reply slippy :)

I tried the security = share, but it made no difference :(

I did have a little play with it though, and now I can access computers from Ubuntu, but it asks me for a Username and password to connect, I type these in right, but it won't take it for some reason :confused:

One thing I have noticed, when searching for 10.0.0.19 (the ip of the Ubuntu box), it has now created a quick click icon in My Network Places listed as 'mark on Ubuntu64 server (Samba, Ubuntu)(10.0.0.19)', but it is listed at the bottom under Internet links, and not at the top with the Network links - WTF!

Could this be down to a netbios name issue, and if so, anyone know how to resolve it?

If I open up My Computer, I can type into the address bar //10.0.0.19/ and it will show the shares, but if I type in //Ubuntu64/ it fails to find it.

Thanks again...[/QUOTE]
 Bumpety Bump!
:D

Thanks :)

---

### Post by starNIX on 2005-07-30
I am having the exact same problem.  Using the IP address I can access it but using the hostname gives a "Not accessable - Network share not found" in windows.

---

### Post by wjp.reg on 2005-07-31
[QUOTE=Win2Kuser]Bumpety Bump!
:D

Thanks :)[/QUOTE]
 I haven't seen any mention of adding your windows user as a valid Samba account.  Normall you would do the following:

sudo smbpasswd -a user

at which point you will be prompted for a password and confirmation.

You should be able to see and access your linux shares from windows when prompted for that username and password

There's a useful intro to Samba if you follow this link which seems to apply to your situation: [http://www-128.ibm.com/developerworks/library/l-samba3.html](http://www-128.ibm.com/developerworks/library/l-samba3.html)

 :smile:

---

### Post by al7kz on 2005-08-01
corrected

---

### Post by xbaez on 2005-08-09
protocol=lanman2
max protocol=lanman2

I had the same problem

---

