---
title: "Can't access Samba shares from 2 other Kubuntu PC, but ok from Windows"
date: 2018-02-17
forum: Networking &amp; Wireless
---

### Post by darknice on 2018-02-17
Hello to all. 

I have a network at home composed by 3 PC running Kubuntu (14.04 and 16.04) and 2 PC running Windows 7. 

The Kubuntu PC with 14.04 has samba installed to share files with Windows. From both Windows PCs I can access in full the shared folder in the 14.04 PC, but from the two 16.04 PCs I have 2 different reactions:

from one I get 'Could not connect to host smb://workgroup/' (hence I cannot see even the PCs in the workgroup), while from the other 16.04 Kubuntu I can access the workgroup, the 14.04 PC, but when I try to open the shared folder it tells me that it doesn't exist....

I am constantly trying different solutions, but without success. I find a lot of solutions on how to connect Linux to Windows, but not a network like mine. 

I don't want to use ssh (already installed, by the way) since it won't allow me to access a file on the other PC, but just to copy it over. I want to be able to 'edit' a file located in the 14.04 PC. 

Thanks 

AB

---

### Post by Morbius1 on 2018-02-17
Need to see how the 14.04 machine is set up. Please post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```
```
hostname
```

---

### Post by darknice on 2018-02-17
Testparm -s gives

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[Anonymous]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Shared]"
Loaded services file OK.
Server role: ROLE_STANDALONE

# Global parameters
[global]
        server string = %h server (Samba, Ubuntu)
        server role = standalone server
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb


[Anonymous]
        path = /samba/anonymous
        force user = nobody
        read only = No


[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes                                                                                                                                                             
        browseable = No                                                                                                                                                             
                                                                                                                                                                                    
                                                                                                                                                                                    
[print$]                                                                                                                                                                            
        comment = Printer Drivers                                                                                                                                                   
        path = /var/lib/samba/printers                                                                                                                                              
                                                                                                                                                                                    
                                                                                                                                                                                    
[Shared]                                                                                                                                                                            
        path = /home/Documents/Private/Shared                                                                                                                                       
        read only = No                                                                                                                                                              
        guest ok = Yes 

```

while 'net usershare info --long' gives 
```

[Shared]                                                                                                                                                                            
path=/home/andrea/Documents/Private/Shared                                                                                                                                          
comment=                                                                                                                                                                            
usershare_acl=Everyone:F,                                                                                                                                                           
guest_ok=y


```
and 'hostname' returns

```
office
```

I am not sure on how to get these returns in little windows the way you did for the codes...

Thanks

---

### Post by Morbius1 on 2018-02-17
There's two ways to create a samba share.

This is called a Classic share and it's in /etc/samba/smb.conf:
> [Shared]                                                                                                                                                                              
        path = /home/Documents/Private/Shared                                                                                                                                         
        read only = No                                                                                                                                                                
        guest ok = Yes 
This is called a UserShare and is created from Dolphin:
> [Shared]                                                                                                                                                                              
path=/home/andrea/Documents/Private/Shared                                                                                                                                            
comment=                                                                                                                                                                              
usershare_acl=Everyone:F,                                                                                                                                                             
guest_ok=y
You can use both methods at the same time but you can not use the same share name ( [Shared] in this case ) with different paths. So rename one of the shares to something other than Shared.

If you change the name in smb.conf restart smbd:
```
sudo service smbd restart
```
For the wierd workgroup error you got go to one of the 16.04 PC's, open a terminal, and run:
```
dolphin smb://office.local
```

Tho only other potential problem I see here is the Linux permissions of the Shared folder regardless of path. In both cases you want guest write access to the folder but unless the shared folder has Linux permissions of 777 that won't happen.

---

### Post by darknice on 2018-02-17
Ok, ok... it comes automatic that I am a real newbie to this. 

Now I removed the settings via Dolphin, so the command 'net usershare info --long' gives out nothing and every computer does access with writing capabilities to the shared folder. 
I wasn't aware that the settings of Dolphin were going to be redundant with the settings of the smb.conf file .

For what concerns the weird issue, using your command the access is granted and I can do anything I want, but if I go through the normal route of clicking 'network' in the tree and browsing to the workgroup folder, it gives me the same error...

You mention Linux permissions, but this is an issue related only to that machine. Is it possible that Dolphin is not refreshing the locations even by pressing f5?

Any other way you might think to work around that?

For the moment, thank you a lot for the above findings. I owe you one...

---

### Post by Morbius1 on 2018-02-17
The ability of a machine to scan the network, discover other machines by name, and resolve that name to an ip address [s]can be done in two ways[/s] - can be done in at least two ways: The Windows way and the Linux way. The Windows way is a convoluted mess ( workgroups, netbios names, etc, ..) while the Linux way is more direct, simpler, and more reliable.

I don't like to mess with things that are working and you indicated that the Windows machines have no problem finding your Linux boxes so I don't want to do anything to your Linux box to mess that up.

The Linux way can be used alongside the Windows way for your Linux boxes or any MacBooks that you may have in the network. The Linux way uses avahi ( the .local ) part. There are no Workgroups or any of the other peculiarities associated with the way a Windows box accesses a server.

---

### Post by darknice on 2018-02-17
I still have a feeling that the problem somehow resides within Dolphin or within the refresh of the network shares. 

I need to focus a bit more and see what kind of test I might do. 

Thanks for your great help....

---

### Post by Morbius1 on 2018-02-17
You seem to really want the Windows way to work on the one machine that yields the 'Could not connect to host smb://workgroup/' error. The classic way to do this is:

Edit /etc/samba/smb.conf and right under the workgroup = WORKGROUP line add this one:
```
name resolve order = bcast host lmhosts wins
```
Save the file. Then restart samba in this order:
```
sudo service smbd restart
```
```
sudo service nmbd restart
```
Now go make a pot of tea or at least wait ... about 5 minutes. Then go though the the whole network .. whatever process in dolphin again.

By default the samba client will use "name resolve order = lmhosts wins host bcast". Out of all of those bcast is the only one that's functional but it's listed last. Put it first. 

The system will use name resolve order if you use the Windows Way to try and resolve a name to an ip address. It goes from one method to the other in sequence lmhosts first , then wins, then host file, and finally bcast. What can happen is the name resolution process hits wins and leaves the network - as in it tries to leave the local network - to find things.

Like I said, the Windows way is a convoluted mess. So much so that Microsoft itself deprecated way back in Windows 2000. They had to keep it alive though for legacy systems since they didn't have anything to replace it until they invented HomeGroups. And a HomeGroup is not compatible with Linux.

The Linix way is less convoluted. Linux can do it. macOS can do it. Even Windows 10 can do it.

---

### Post by darknice on 2018-02-18
Hello Morbius1.

First of all, the 'faulty' system is now working. Since nothing was done, I guess that it was just a matter of being patient. 

Reading your last message, you are referring to a 'windows' way of file sharing. 

I am not exactly sure what you are referring to, since that is the only way I know, except, of course, FTP or SFTP. 

What I would like is a way to browse the computer 14.04, where I stored some files, and be able to modify them without having to download them. Well, I understand that the satellite computer actually downloads them and saves them where it was downloaded to begin with, but it's doing that in automatic. 

Point being is that personally I can use an ftp browser (filezilla or so), but I cannot ask the other people in my house to do the same. They would be entirely lost. 

Anyhow, I digress...

You mention that there is also a more linear Linux way to do so... 

How does that work?

AB

---

### Post by Morbius1 on 2018-02-18
When you ran **dolphin smb://office.local **you were using the Linux way. Avahi ( it's really multicast DNS ) is a way of setting up a lan side name resolution system amongst the peers in the local network. It's automatic in Linux and macOS and it's just recently been available to Windows 10.

If everything now works for you don't worry about it.

---

