---
title: "Samba shares and permissions"
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by likwid on 2007-03-28
Hi

I'm having the hardest setting up my network correctly and would really appreciate some help so i don't waste more hours at it.

I have ubuntu sharing files via samba to another ubuntu pc and a windows laptop. I have set up the shares by editing smb.conf and they can be accessed on the network, however there's no write permission. 

So far i've

- edited smb.conf
- set consistent usernames and passwords on accounts on all machines and samba (smbpasswd)
- set file permissions of the shared files and folders to 775
- added users to same group on both machines requiring write access ie the two ubuntu machines

[QUOTE=smb.conf][global]
        workgroup = ****        
netbios name = ****
        security = user
	encrypt passwords = yes
        unix charset = ISO8859-1


[homes]
        read only = No
        browseable = No

[Music]
        path = /mnt/Music
        writable = yes
        write list = mark media
        public = Yes

[TV]
        path = /mnt/Video/TV
        public = Yes
        writable = yes
        write list = mark media

[Movies]
        path = /mnt/Video/Movies
        write list = mark media
        public = Yes

[Shared]
        path = /mnt/Video/Shared
        write list = mark media mati loli
        public = Yes[/QUOTE]

Any ideas how to proceed? I realise i've edited smb.conf, but this is due to my wanting to learn about it. It may well be this is the problem?

Thanks in advance!

---

