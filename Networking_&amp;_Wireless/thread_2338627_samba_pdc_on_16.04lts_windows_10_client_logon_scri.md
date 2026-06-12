---
title: "samba pdc on 16.04lts windows 10 client logon scripts not running"
date: 2016-09-30
forum: Networking &amp; Wireless
---

### Post by giggler2 on 2016-09-30
hi, 


I have samba 4.3.9-Ubuntu setup (16.04.1 lts).  followed a guide to get a  windows 10 client to join my pdc OK but cannot get netlogon scripts to  run.  I can see them in the share \\<server>\netlogon and I can  manually run them from windows shell or by double clicking them.  They  just won't run by themselves. 


I have done the registry pokes + policy changes as: 


[https://community.spiceworks.com/topic/1389891-windows-10-and-sysvol-netlogon](https://community.spiceworks.com/topic/1389891-windows-10-and-sysvol-netlogon)
[https://support.microsoft.com/en-us/kb/2895815](https://support.microsoft.com/en-us/kb/2895815)


[https://s18.postimg.org/643ketg49/regedit_samba.png](https://s18.postimg.org/643ketg49/regedit_samba.png)


[https://s22.postimg.org/6awshoi8h/network_samba.png](https://s22.postimg.org/6awshoi8h/network_samba.png)


[https://s16.postimg.org/aul5oxh91/grouppolicy_samba.png](https://s16.postimg.org/aul5oxh91/grouppolicy_samba.png)


everything  appears to work just no execution of script automatically.   I have  made sure they are windows line ending format (via unix2dos). 


also using virtual box and windows 7 IE 10 test ovp, I can join same pdc and  the netlogon scripts run so it's something to do with samba and windows  10.


testparm output: 


Load smb config files from /etc/samba/smb.conf 
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384) 
Processing section "[homes]" 
Processing section "[share]" 
Processing section "[temp]" 
Processing section "[netlogon]" 
Loaded services file OK. 
Server role: ROLE_DOMAIN_PDC 

Press enter to see a dump of your service definitions 

# Global parameters 
[global] 
        workgroup = COMPO 
        server string = %h server (Samba, Ubuntu) 
        security = USER 
        log file = /var/log/samba/all_log 
        server max protocol = NT1 
        max protocol = NT1 
        protocol = NT1 
        name resolve order = wins lmhosts hosts bcast 
        add machine script = sudo /usr/sbin/useradd -N -g pdcmachines -c Machine -d /var/lib/samba -s /bin/false %u 
        logon script = logon.bat 
        logon drive = H: 
        domain logons = Yes 
        preferred master = Yes 
        domain master = Yes 
        wins support = Yes 
        idmap config * : backend = tdb 


[homes] 
        comment = Home Directories 
        valid users = %S 
        read only = No 
        create mask = 0700 
        directory mask = 0700 
        directory mode = 0700 
        browseable = No 


[share] 
        comment = Global shared directory 
        path = /home/share 
        valid users = %U 
        read only = No 
        create mask = 0700 
        directory mask = 0700 
        directory mode = 0700 


[temp] 
        comment = Temporary shared data directory 
        path = /home/temp 
        valid users = %U 
        read only = No 
        create mask = 0700 
        directory mask = 0700 
        directory mode = 0700 


[netlogon] 
        comment = Network Logon Service 
        path = /srv/samba/netlogon 
        create mask = 0700 
        directory mask = 0700 
        directory mode = 0700 
        browseable = No 


any suggestions going forward?

---

