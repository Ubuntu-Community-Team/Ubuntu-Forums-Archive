---
title: "While Configuring Samba Apache Shows Instead"
date: 2018-12-12
forum: Networking &amp; Wireless
---

### Post by anewcreation on 2018-12-12
Hello and thanks in advance!

I am trying to configure Samba server on Ubuntu Server 16.04.5 (32 bit) for Windows 10 machines to access without passwords on local network

I followed this tutorial: [https://help.ubuntu.com/lts/serverguide/samba-fileserver.html.en](https://help.ubuntu.com/lts/serverguide/samba-fileserver.html.en)

Then I went through other networking tuts

Instead of accessing the File Share via Samba when I enter the server ip I get Apache serving me a default web page

I don't know what wires are crossed here, please advise

---

### Post by TheFu on 2018-12-12
Are you using a file manager or a web browser for access?

File manages will have a "Browse Network" button or you can enter smb:// like URLs. They are NOT web browsers.

Web browsers will insert http:// or https:// into the URL.  They are NOT file managers.

---

### Post by anewcreation on 2018-12-12
The instructions I followed seemed to suggest I would get a directory listing if I used a web browser. So one method I tried was the browser. But I got an Apache served default page instead of a share directory listing.

I also cannot see the share in Network on Windows 10. I tried searching different combinations of ip address/share name in the network search pane but I think my Windows network is just not able to see the file share.

From what I can tell, Samba should be set up to not require a password and I should be able to see it on the network.


I have the network name in Samba config set to the network name given by the ISP. Workgroup is set to WORKGROUP... I'm not sure what the issue is but I suspect its Windows related.

---

### Post by TheFu on 2018-12-12
If you use a web browser, then you will only see web servers.  Use a Linux file manager with the smb://xxx.xxx.xxx.xxx/ 
You'll need to enter the IP address.  This will tell us if the issue is Windows or Linux and cut the possible problems 50%.

There are lots of answers in these forums about setting up samba with Win10. If you search, one of those is likely exactly what is needed. To get more help here, we need facts.

Post the output from **testparm -n** . Please use code tags, so the text is aligned. The easier it is to read, the more people will look at it.  That is the first step.

Also, exactly what did you enter into the file manager URL and which one have you used?

---

### Post by anewcreation on 2018-12-13
UPDATE:

I am able to see the share, and files in it, and READ ONLY when I map a network drive (still dont see it as part of network)

But I cannot write anything to the share. 

Here is the output of testparm -n

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Processing section "[cvbc]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions
# Global parameters
[global]
        server string = %h server (Samba, Ubuntu)
        interfaces = 192.168.1.150/24 enp0s5
        bind interfaces only = Yes
        server role = standalone server
        security = USER
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:                                                                                                                                                             * %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        wins support = Yes
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[cvbc]
        comment = CVBC File Share
        path = /srv/samba/share
        read only = No
        create mask = 0755
        guest ok = Yes

---

### Post by TheFu on 2018-12-13
```
interfaces = 192.168.1.150/24 enp0s5
```
looks funny to me.
 The manpage for smb.conf on your system will have more details.  Basically, if you aren't 100% positive, don't touch this setting.```

       interfaces (G)

           This option allows you to override the default network interfaces
           list that Samba will use for browsing, name registration and other
           NetBIOS over TCP/IP (NBT) traffic. By default Samba will query the
           kernel for the list of all active interfaces and use any interfaces
           except 127.0.0.1 that are broadcast capable.

```
and delete the **bind interfaces only** setting. It isn't needed 99.99% of the time.

As for allowing anyone, "guest", to have write access, I don't do that. But the config posted shows "Bad User" which won't exist for guest access.  Isn't it normal to map to "nobody" instead, then setup the permissions on the shared storage from inside Linux to be owned by "nobody"?

I just noticed that the guide you linked is for 18.04, not 16.04.  The versions of samba are different. Best to find a 16.04 samba guest how-to.  Between every LTS, lots of things change.  Google found this [https://askubuntu.com/questions/781963/simple-samba-share-no-password](https://askubuntu.com/questions/781963/simple-samba-share-no-password)  , but I don't like that it suggests 777 file permissions. OTOH, anything with guest CIFS access isn't secure on the LAN anyways.  LAN security is 1 thing.  777 permissions is something much, much, worse.

I don't understand this:
> I am able to see the share, and files in it, and READ ONLY when I map a network drive (still dont see it as part of network)

BTW, have you looked at the samba log files?  Log are the first place to check for issues.

---

### Post by Morbius1 on 2018-12-13
> I am able to see the share, and files in it, and READ ONLY when I map a network drive
Remember the samba share definition determines what the client [COLOR=#0000cd]**may**[/COLOR] do. Linux permissions determines what the client [COLOR=#0000cd]**can**[/COLOR] do. What are the Linux permissions of the target shared folder:
```
ls -dl /srv/samba/share
```
In a true anonymous access setup "map to guest = Bad User" will convert the Win10 user to the user "nobody" automatically. So if you want the Win10 user to have write access to the share "nobody" has to have write access to the /srv/samba/share directory.
>  (still dont see it as part of network)
Unless you went out of your way to reverse it Win10 disables the SMB1 dialect on both the server and client side. Without smb1 on the client side Win10 will never be able to "discover" your Linux machine. Works the same way in Linux. Disable smb1 on the client and it can no longer "discover" samba hosts - at least not by it's netbios name.

Win10 should be able to access the machine but it must ask for it explicitly:

\\192.168.1.xxx\cvbc
\\netbios-name\cvbc
\\host-name.local\cvbc

What is the host name of your samba server?

---

### Post by Morbius1 on 2018-12-13
Should have read your original post more carefully. Your linked HowTo is flawed and really should be removed from the site.

It has you create the share:
> [share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755

Then it has you change ownership to nobody:
> sudo chown nobody:nogroup /srv/samba/share/
If you do nothing else that will actually work. THe Win10 user will be converted to "nobody" because he is a "Bad User" ( one who does not have a samba password or the incorrect one ) and he will have write access.

It will break the moment you add the Win10 user to the samba password database because at that point he is no longer a "Bad User" he is a known user and he is not "nobody".

I would change the share definition to this :
> [share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
[COLOR=#0000cd]**force user = nobody**[/COLOR]
    create mask = 0755
Then restart smbd:
```
sudo service smbd restart
```
Now if you give a user a samba password or create a share that requires credentials it will not break access to the guest share.

---

