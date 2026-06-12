---
title: "Can't Acess Files in and from Windows"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by Cris987 on 2008-07-19
I'm trying to transfer files from Vista to/from Hardy. I have spent the last 4 hours trying to get Samba to work but it won't.

1) Setting up a share folder on Ubuntu and accessing it from Windows:

I followed the guide in this forum and got my samba user set up. Vista sees my ubuntu laptop and prompts me for a username and password. It then shows me a bunch of files that I have chosen to share on Ubuntu and prompts me again when I try to open them. But here is when it says:

"\\GILBERT-LAPTOP\gilbert-share is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.

The group name could not be found."

Here's my conf file

> [global]
    ; General server settings
    netbios name = gilbert-laptop
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    ;security = user
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

[gilbert-share]
    path = /home/gilbert/
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = gilbert
    force group = gilbert



I got fed up trying to work it out, so I tried the other way

2) Looking at Vista using Ubuntu:

I set a bunch of files on Vista to share and tried to look it up on Hardy. I see my Vista computer, but it showed nothing. After wasting another hour trying to search up a sol'n, I finally found out that the locations would show up if I go to location "smb://gilbert-tablet/users/gilbert" The files show up! ... but I can't create folders/files. I can edit existing files, but I can't create anything new. 


Can someone please help? I really don't understand why such an essential and simple feature is still screwed up in Hardy.

---

### Post by cybrsaylr on 2008-07-19
The way I've moved files from Windows to Ubuntu, is just drag them. 
I haven't done that much but the few I did were music files (mp3s) and pictures. All I did was go into Windows from Ubuntu, open two windows up and drag the files I wanted from Windows to Ubuntu with no problems. 
Once I even downloaded a big file for Windows while in Ubuntu (300MBs) then dragged that file from Ubuntu to Windows, then used it in Windows when I went back into Windows on my dual boot setup.

---

### Post by superprash2003 on 2008-07-19
please post your /etc/samba/smb.conf file here.. regarding the 2nd question.. you might have to setup the vista sharing properly.. to allow creation of new folders

---

### Post by Cris987 on 2008-07-19
> **superprash2003 said:**
> please post your /etc/samba/smb.conf file here.. regarding the 2nd question.. you might have to setup the vista sharing properly.. to allow creation of new folders


just edited my post to include that file

---

### Post by superprash2003 on 2008-07-20
replace 
;security = user
with
security = user
i.e. remove ;
and restart samba

---

### Post by Cris987 on 2008-07-21
> **superprash2003 said:**
> replace 
;security = user
with
security = user
i.e. remove ;
and restart samba


Hi, I did as you said and the same thing happened.

I am prompted for a password when i double click on GILBERT-LAPTOP (my linux box) and I'm able to pass the verification. using the same credentials however, I'm not able to get into my share folder from there.

---

### Post by superprash2003 on 2008-07-22
are you trying to access using the username gilbert?? ensure that the file /etc/samba/smbusers contains the username gilbert..try sharing another folder graphically i.e. by right clicking on the folder and clicking on shared folder..

---

