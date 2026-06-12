---
title: "I can't get Win10 PC to Access Ubuntu 18.10 Samba Shares"
date: 2019-02-02
forum: Networking &amp; Wireless
---

### Post by jmhine on 2019-02-02
Actually, I don't know if I have a Windows problem or a Ubuntu problem, but it's easier to find help from Ubuntu people, so I'm starting here.

I've been using a Ubuntu server for years accessing it with Windows computers with no problems. Then I upgraded to Ubuntu 18.10
I'm trying to share several folders from my Ubuntu server with my Win10 machines. Three of my four PCs are running Win10 ver 1809 and one is running ver 1803. 
Two of my vers 1809s can access and write to the Ubuntu's Samba Shares perfectly, no problemo. One of the vers 1809 can see the shares, but cannot access them. Neither can the vers 1803. However, just to make things more confusing, of the multitude of Samba shares that I've created during this whole head-banging experience, all 4 of the Win10 PCs can access one of the Samba Shares.
Of the two PCs that are not having difficulty, one has SMB 1.0/CIFS checked and one does not. The 1803 has it checked.
I have tried turning off the Windows firewall.  

  
Do I have a windows problem or a Ubuntu problem? 
 
Where do I go from here? I am open to any suggestions.

Thank you in advance for any help.
John H

---

### Post by Morbius1 on 2019-02-03
I guess the first place to start is for you to post how your server is set up. Please post the output of this command:
```
testparm -s
```

And let us know which of the shares does this:
> However, just to make things more confusing, of the multitude of Samba  shares that I've created during this whole head-banging experience, all 4  of the Win10 PCs can access one of the Samba Shares

---

### Post by jmhine on 2019-02-03
Morbius1   Thank you for your reply.    here is the output of the testparm -s command.  I'm just trying to set up one share at the moment (WilHineShare) thinking that if I can get one to work, I'll be able to get 6 more to work.

john@Ubuntu1810:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[homes]"
Processing section "[printers]"
Processing section "[WilHineShare]"
Loaded services file OK.
Server role: ROLE_STANDALONE
 
# Global parameters
[global]
                dns proxy = No
                log file = /var/log/samba/log.%m
                map to guest = Bad User
                max log size = 1000
                obey pam restrictions = Yes
                pam password change = Yes
                panic action = /usr/share/samba/panic-action %d
                server role = standalone server
                syslog = 0
                unix password sync = Yes
                usershare allow guests = Yes
                idmap config * : backend = tdb
 
 
[homes]
                comment = Home Directories
                create mask = 0700
                directory mask = 0700
                read only = No
                valid users = %S
 
 
[printers]
                browseable = No
                comment = All Printers
                create mask = 0700
                path = /var/spool/samba
                printable = Yes
 
 
[WilHineShare]
                guest ok = Yes
                path = /media/john/9d35a8c2-039d-40bc-aaa0-b84f60aa6e8e/WilHineShare
                read only = No
john@Ubuntu1810:~$

---

### Post by Morbius1 on 2019-02-03
Change this:
> [WilHineShare]
                guest ok = Yes
                path = /media/john/9d35a8c2-039d-40bc-aaa0-b84f60aa6e8e/WilHineShare
                read only = No
To this:
> [WilHineShare]
                guest ok = Yes
[COLOR=#0000cd]**force user = john**[/COLOR]
                path = /media/john/9d35a8c2-039d-40bc-aaa0-b84f60aa6e8e/WilHineShare
                read only = No
Then restart smbd:
```
sudo service smbd restart
```

The problem here is the /media/john folder Linux sets up and then applies special permissions to that allows only john access to what is past it. The remote guest user isn't "john" so it never gets to the /9d35a8c2-039d-40bc-aaa0-b84f60aa6e8e/WilHineShare part of the path.

**force user **makes the remote user appear to be you - at least for that share.

---

### Post by jmhine on 2019-02-03
Well, that had unanticipated results.  Now my Win10 PC can't see any Ubuntu Shares.  However, my wife's Win10 PC can still read and write to the WilHineShare

---

### Post by Morbius1 on 2019-02-03
That symptom I cannot reproduce.

---

### Post by jmhine on 2019-02-03
Ok, I'm having some luck now.
Thank you.

---

