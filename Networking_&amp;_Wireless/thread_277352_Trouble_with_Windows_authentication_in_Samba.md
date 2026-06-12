---
title: "Trouble with Windows authentication in Samba"
date: 2006-10-14
forum: Networking &amp; Wireless
---

### Post by Zendarin on 2006-10-14
Hey, I'm pretty new at Linux and also networking.  I wanted to connect my Linux box to my XP PC and share my MP3's on the PC.  I did the sharing setup on the PC, downloaded Samba and did an initial setup and Windows was able to connect to my Linux box.  However, by Box can't connect to Windows.  I get an 
error message "NT_STATUS_LOGON_TYPE_NOT_GRANTED". ??  I have no idea what to do.  I tried [Stormbringer's guide to setting up Samba]("http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba"), but now I can't even get into the Linux shares from Windows.

If someone would please help me, I would really appreciate it! :)


BTW, when I use testparm /etc/samba/smb.conf, the output shows a weird error (marked in red).

Load smb config files from /etc/samba/smb.conf
Processing section "[print$]"
Processing section "[printers]"
Processing section "[SharedFolder]"
Loaded services file OK.
[COLOR="Red"]WARNING: passdb expand explicit = yes is deprecated[/COLOR]
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = MSHOME
        server string =
        null passwords = Yes
        passdb backend = tdbsam
        username map = /etc/samba/smbusers
        syslog only = Yes
        announce version = 5.0
        name resolve order = hosts wins bcast
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
        printcap name = CUPS
        printing = cups
        print command =
        lpq command = %p
        lprm command =

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

[SharedFolder]
        path = /home/andrew
        force user = andrew
        force group = andrew
        read only = No
        create mask = 0644

---

### Post by Zendarin on 2006-10-18
Okay, I googled everything I could think of, and I think the problem is with XP Home Edition.  XP can read Ubuntu, but now when I run smbclient -L hal-9000, it shows up Error opening shares: NT_STATUS_OK  

I don't understand what the problem is, unless it is the fact that XP Home doesn't have group policy and security settings.

However, I hear that it is possible to change the settings with the Windows Server 2003 Toolkit Terminal.  If anyone knows how or what else the problem might be, I would really appreciate help!

This is getting very annoying ](*,) 

Thanks

---

### Post by Zendarin on 2006-10-23
For anybody who may have the same trouble, here is a solution that worked for me.

[http://www.ubuntuforums.org/showthread.php?p=1652469]("http://www.ubuntuforums.org/showthread.php?p=1652469")

Hope it helps :)

---

