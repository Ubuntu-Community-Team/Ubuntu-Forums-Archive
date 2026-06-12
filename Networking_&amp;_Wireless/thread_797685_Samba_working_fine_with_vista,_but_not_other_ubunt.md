---
title: "Samba working fine with vista, but not other ubuntu!??"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by buntu_noob on 2008-05-17
like the title says, I can get samba to work with vista, but not with my other ubuntu computer.
Here is the setup:

Desktop-ubuntu
Laptop_1- ubuntu
Laptop_2 - Vista


I have files shared on Lapatop_1 and desktop, these files are visible and usable on the vista laptop. However, the two ubuntu machines should the computers as being in the network but no shared folders. Any thoughts?

---

### Post by buntu_noob on 2008-05-17
bump

---

### Post by buntu_noob on 2008-05-19
anyone have any ideas...... windows can access everything fine. Ubuntu can see file on the other ubuntu computer. Where am I going wrong?

---

### Post by jtrindle on 2008-05-19
Are they all in the same workgroup?  Or are you trying to use a domain?

Do you have to use a user name to log into the share on laptop_1  from the vista box?

Could you post the /etc/samba/smb.conf from laptop_1?

---

### Post by buntu_noob on 2008-05-19
Yes, they are all on "workgroup" they all show up on the workgroup. I can see and access the files on the Ubuntu machines through the vista machine. I have no issue with the vista machine, I don't need a user name to sign in because I added it as a user on both the Ububt machines through samba. No I am not trying to use a domain. Here is the congf file for samba on the laptop_1

> [global]
    ; General server settings
    netbios name = daniel-laptop
    server string =
    workgroup = WORKGROUP
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/daniel/Pictures
    browseable = yes
    read only = yes
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = daniel
    force group = daniel


Like I said before vista is not an issue at all. However, between the two Ubuntu boxes, the computers show up, but no files are visible.


Thanks in advance.

---

### Post by jtrindle on 2008-05-19
That all looks good.

Can you go in from a command line client from laptop_2?

First try to list the shares on the computer:

smbclient -L //laptop_1

(Or smbclient -L \\\\laptop_1 if you like backslashes)

If MyFiles shows up there, then 

smbclient //laptop_1/MyFiles -U daniel


should give you an ftp-like program to navigate your share.  If you can do a dir from here (and get to copy a file down) then your laptop_1 samba is set up fine.

Do you have the smbfs package installed on the Ubuntu systems?

---

### Post by buntu_noob on 2008-05-19
yeah, it all checks out!

the problem is not with laptop_1 or the vista laptop. Perhaps the desktop is wrong?

Oh, yes i can get in the command line on the vista laptop.

> Domain=[DANIEL-LAPTOP] OS=[Unix] Server=[Samba 3.0.28a]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      
	MyFiles         Disk      
	IPC$            IPC       IPC Service ()
	PDF             Printer   PDF
Domain=[DANIEL-LAPTOP] OS=[Unix] Server=[Samba 3.0.28a]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
	WORKGROUP            ANGELS-PC
daniel@daniel-laptop:~$ smbclient //daniel-laptop/MyFiles -U daniel
Password: 
Domain=[DANIEL-LAPTOP] OS=[Unix] Server=[Samba 3.0.28a]
smb: \> dir
  .                                   D        0  Sat May 17 18:50:06 2008
  ..                                  D        0  Mon May 19 17:56:11 2008
  img_0910.jpg                           1027051  Wed May 14 23:49:31 2008
  img_0951.jpg                           1504218  Wed May 14 23:49:39 2008
  img_0934.jpg                           2393972  Wed May 14 23:49:36 2008




One thing I noticed is that there are two workgroups "WORKGROUP" and "Workgroup"
what does this mean?

---

### Post by buntu_noob on 2008-05-19
perhaps this will make thing easier to follow.

Laptop_1:daniel-laptop (Ubuntu machine)
Laptop_2: Angels-pc (Vista machine)
Desktop: master-desktop (ubuntu machine)

---

### Post by buntu_noob on 2008-05-19
any more thoughts guys?

---

### Post by jtrindle on 2008-05-20
Nope, I'm not familiar enough with the GUI Linux environment and Samba.  Almost all my experience has been with smbclient and smbfs from the command line.

It's almost got to be a permissions or authentication issue, but I don't know why the command line would work and the GUI wouldn't.

Sorry!!

---

