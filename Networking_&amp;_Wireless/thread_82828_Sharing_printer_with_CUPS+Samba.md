---
title: "Sharing printer with CUPS+Samba"
date: 2005-10-27
forum: Networking &amp; Wireless
---

### Post by fourhead on 2005-10-27
Hi, I have a parallel printer on a Linux server which I want to share via Samba. It's an HP DesignJet 650C. The printer works fine on the Linux box, and Samba also works very well. I want a setup so that the Windows clients automatically pull the printer driver from the Linux machine. According to several howtos, I've setup the [printers] and [print$] shares, and I've downloaded the cups-samba drivers for Windows and ran the install script they provide, so the Windows drivers are now in /usr/share/cups/drivers. Now, all howtos say that you have to run

cupsaddsmb -H server -U root -h server -a

to add the drivers for all printers to the  print$ share. I tried that, and it didn't work, which may be because root has no pwd at all in Ubuntu. I tried it with -U administrator then (administrator is my normal user account I use in Ubuntu), it asks for my password, but it still doesn't work. It just asks for the password again and again. I tried to enable writing in all printer-related shares, I also tried to make administrator the "printer admin", but it all doesn't work!

Does anybody of you know of a way to get cupsaddsmb to work, or is there another way to get the CUPS windows drivers installed correctly?


Any help would be greatly appreciated!!


Tom

---

### Post by fourhead on 2005-10-27
Okay, I've solved this, but now another problem. The printer works fine on the Linux server, Samba also works perfectly for all clients, but when I click on "Connect printer" on any windows machine, it won't work! I'm pulling my hairs out with this. I have an absolutely standard Ubuntu install, my smb.conf looks like this:

```

[global]
load printers = yes
printing = cups
printcap name = cups

[printers]
path = /tmp
browseable = no
public = yes
guest ok = yes
writable = no
printable = yes
printer admin = administrator

```

I can see the printer from Windows, but when I try to connect it says "Couldn't connect to printer. Access denied". This is so rediculous. On the Windows machines, I have regular user accounts (Users group) and the admin, when I try to connect the printer, I'm logged in as Administrator, and I have a corresponding administrator account on Linux in /etc/passwd and smbpasswd - and the file shares work fine as Administrator.

I already checked if I have a guest account "nobody" and I do, I tried changing the guest account to "administrator", I tried enabling/disabling guest access, write acces, browsing etc. - all to no avail, I just can't print.

Can anybody please help me? I'm really stuck and I've already lost the whole day only getting this to work....


Tom

---

### Post by byourg on 2005-10-27
Here is part of my samba config, I have my printer on XP and I print from my Ubuntu laptop no problems. Hope this helps.


```
[printers]
   comment = All Printers
   browseable = yes
   path = /tmp
   printable = yes
   public = yes
#   guest account = smbprint
   writable = yes
   create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
```

---

### Post by fourhead on 2005-10-28
Okay, this is starting to really annoy me. Thanks for your smb.conf, but it didn't work out. My complete smb.conf now looks like this:

```

[global]
   workgroup = ibrnetz
   server string = Ubuntu Linux Server
   wins support = yes

   security = user
   encrypt passwords = true
   unix password sync = yes
   passdb backend = tdbsam guest
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spasswor$

   admin users = administrator

   load printers = yes
   printing = cups
   printcap name = cups
   printer admin = administrator

   preserve case = yes
   short preserve case = yes
   inherit permissions = yes
   map archive = no
   map hidden = no
   map system = no

   socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

[Daten]
   path = /srv/daten
   browseable = yes
   writeable = yes
   create mask = 0660
   directory mask = 0770

   vfs object = recycle
   recycle:repository = Papierkorb
   recycle:keeptree = yes
   recycle:exclude = *.tmp *.bak



[Backup]
   path = /srv/backup-daten
   browseable = yes
   writeable = no



[HP-DesignJet-650C]
   path = /tmp
   browsable = yes
   printable = yes
   writeable = no
   create mode = 0700



[printers]
   path = /tmp
   browsable = yes
   printable = yes
   writeable = no
   create mode = 0700



#[print$]
#   path = /etc/samba/printers
#   browseable = yes
#   writeable = no
#   write list = administrator

```

I've given up trying to make the print driver available on the Server, so what I want now is that every client can connect to the printer and use their own, local print driver. The file server part of this setup is working PERFECTLY for ALL users in the network, all have access to it - but printing won't work. If I go to Network Neighborhood, Server, HP-DesignJet and right click on "Connect" it tells me there's no driver on the server, which is okay. It gives me the printer list, I select to add my own driver, click on it, choose the correct printer model, and then it suddenly says (translated from German) "Connection to printer could not be established. You either gave a wrong printer name, or the printer is not connected to the server anymore". What does that mean?? I'm really at the end of my knowledge, I'm working on this for TWO whole days now .... Please can anybody help me???


Tom

---

### Post by happynix on 2006-07-02
I know this is kind of late but hopefully someone else will be helped.

The permission denied problem on the printer might be affected by two things:
1.  If you are going to use [print$] the a root equalivan admin needs to be defined 
    AND
2. Make sure you don't have on of these invalid "users = root" in smb.conf 

next Windows Cups driver

man cupsaddsmb and download/copy the files as directed.
in the CUPS gui you can export your printers to samba and have click and print on your windows clients

Caveot:  Cups 1.2.0 (Dapper) has a broken cupsaddsmb which squashes the PPD in to a bid oneline mess that Windows gets very unhappy about.

You can fix the generated PPD thusly:
    sed 's/.\*/\n\*/g' /var/lib/samba/printers/W32X86/{yourprintername}.ppd    >/tmp/{yourprintername}.ppd
   cp /tmp/{yourprintername}.ppd /var/lib/samba/printers/W32X86/
   cp /tmp/{yourprintername}.ppd /var/lib/samba/printers/W32X86/3

Cups 1.2.3 fixes the problem

---

### Post by sgla1 on 2006-07-29
If you set security = user in smb.conf, then windows machines trying to print will need to log on to the samba server first with a valid username and password.

This is the same as a windows user printing to a nt server when that user is not a member of the domain > permission denied.\

You could either change security = share, or create a samba user like "print_user" and tell the windows machines to connect as that user. (I am assuming that your windows box authenticate against the samba server).

---

### Post by sutley on 2006-10-12
I know this will sound like a repost, but the information provided as either gone over my head or not worked. Any help or dumbing down would be useful.

I am unsuccessful in printing from a WinXP machine to a HP DesignJet 650c shared by Ubuntu. I am able to print from the Ubuntu machine perfectly fine. I can see the printer on my network when browsing from the WinXP machine. I can connect to the printer from the WinXP machine. However the drivers are not found. If I choose to load the printer with the local windows drivers and try to print a test page, the printer goes through the motions, but no ink is put to paper.

I know the windows machine needs to be using a postscript print driver, but do not know how to implement that.


**SYSTEM SETUP**
*Ubuntu Dapper Drake
*System is authenticating against a ClarkConnect (Linux) server setup as the PDC (Win NT style) - Used the following guide to accomplish this (thanks vizvayu) [http://ubuntuforums.org/showthread.php?t=5409](http://ubuntuforums.org/showthread.php?t=5409)


**PRINTER ON SYSTEM**
HP DesignJet 650c was setup using CUPS (localhost:631)

1) Added cupsys To shadow
```
# sudo adduser cupsys shadow
```

2) Added printer named "plotter" on LPT#1 using "djns" driver through CUPS web admin.

3) Removed cupsys From shadow
```
# sudo deluser cupsys shadow
```

4) Edited /etc/cups/cups.d/ports.conf to read
```
Listen *:631
Listen /var/run/cups/cups.sock
```

5) Changed Ubuntu's default /etc/samba/smb.conf to read

```
[global]
   workgroup = MYNETWORK
   netbios name = %h
   server string = %h server (Samba, Ubuntu)
   wins support = no
   wins server = 192.168.1.228
   password server = *
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   security = domain
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   invalid users = root
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

   load printers = yes
   printing = cups
   printcap name = cups
   printer admin = @lpadmin

   socket options = TCP_NODELAY
   idmap uid = 10000-20000
   idmap gid = 10000-20000
   template shell = /bin/bash
   template homedir = /home/%D/%U
   winbind enum users = yes
   winbind enum groups = yes
   winbind cache time = 10
   winbind separator = +
   winbind use default domain = yes

[printers]
   comment = All Printers
   browseable = yes
   path = /tmp
   printable = yes
   public = yes
   writable = no
   create mode = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = yes
   public = yes
```

6) Downloaded from cups-windows-6.0-source.tar.gz and placed contents into /var/lib/samba/printers
```
# wget [http://www.cups.org/windows/software.php?6.0](http://www.cups.org/windows/software.php?6.0)
# tar -zxvf cups-windows-6.0-source.tar.gz
# cd cups-windows-6.0/i386
# cp cups* /var/lib/samba/printers/
# cp cups* /var/lib/samba/printers/W32X86
# cp cups* /var/lib/samba/printers/WIN40
```


7) Restarted services
```
# sudo /etc/init.d/samba restart
# sudo /etc/init.d/cupsys restart
```

---

### Post by paradexes on 2008-02-29
I too would like the see the solution for this. All the posts out there make it seem so easy, But the fact is there is no troubleshooting documentation to make this work. running  cupsaddsmb -U root -a -H localhost -v Which is a valid user added via smbpasswd yields the following output. 

Unable to copy Windows 2000 printer driver files (2)!
Running command: smbclient //localhost/print$ -N -A /tmp/47c8afcbea59c -c 'mkdir W32X86;put /tmp/47c8afc611613 W32X86/lgto-1140-BW.ppd;put /usr/share/cups/drivers/ps5ui.dll W32X86/ps5ui.dll;put /usr/share/cups/drivers/pscript.hlp W32X86/pscript.hlp;put /usr/share/cups/drivers/pscript.ntf W32X86/pscript.ntf;put /usr/share/cups/drivers/pscript5.dll W32X86/pscript5.dll'

I have seen alot of other similar posts, but no solutions. I can see the printers, I can connect to them, But when I try to Windows asks for drivers. Anyone have a solution for this? I am willing to post up any additional info as needed. Right now I have a pretty basic SMB.conf file that I am using to make sure that the printers are viewable at least. 

I have tried manually copying the files over. That is not working either. Any solutions would be greatly appreciated.

---

### Post by superprash2003 on 2008-03-01
have you checked out the tutorial to setup samba and cups in the ubuntu guide?? it has a very easy to follow tutorial.. [http://ubuntuguide.org](http://ubuntuguide.org) it comes under samba and setting up printer

---

### Post by paradexes on 2008-03-18
Ok I got this figured out.

This is the smb.conf file I used. It is right out of the cupsmbadd man page. 

[global]
            load printers = yes
            printing = cups
            printcap name = cups

           [printers]
            comment = All Printers
            path = /var/spool/samba
            browseable = no
            public = yes
            guest ok = yes
            writable = no
            printable = yes

           [print$]
            comment = Printer Drivers
            path = /etc/samba/drivers
            browseable = yes
            guest ok = no
            read only = yes
            write list = root

No errors copying the files in. 

Now I just need to add the lines back in that I need to allow windows to see the server and the printers. I do not recommend changing the lines as they are now if you intend on adding in more drivers.. Just add on what you need for windows users to access the printers. I will add my final smb.conf in a later post once I have verified that the driver pushing works.

---

