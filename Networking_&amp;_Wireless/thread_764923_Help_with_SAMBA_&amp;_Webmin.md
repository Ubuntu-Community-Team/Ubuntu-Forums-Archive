---
title: "Help with SAMBA &amp; Webmin"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by oxsyn on 2008-04-24
I've been trying to get SAMBA running on my Gutsy Server install for quite some time with no luck.  I went back at it again last night, still no luck.

I started out with this guide: [http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+guide](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+guide)

Followed it step by step, got to the end.  On my Vista laptop, I can browse to the share, it prompts me for a username/password, I enter them - and get denied.

So, I decided to try webmin.  I installed it w/o a problem.  Used it to configure SAMBA, I now have the following smb.conf file:

> [global]
        name resolve order = hosts wins bcast
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192
SO_SNDBUF=8192
        announce version = 5.0
        username map = /etc/samba/smbusers
        null passwords = true
        passdb backend = tdbsam
        wins support = true
        netbios name = HAWKING
        printing = CUPS
        default = library
        workgroup = ANARCHIA
        syslog only = yes
        os level = 20
        printcap name = CUPS
        syslog = 1
    ; General server settings





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





[library]
        valid users = f4rr4r
        path = /mnt/library

The /etc/samba/smbusers file contains:
> 
system_username = "f4rr4r"


The server's name is "hawking" & the share is "library," it's a linux partition on hdb that's mounted to /mnt/library.  The user account I'm trying to log in with is "f4rr4r".  I can browse to the share, but access is denied when I enter my username and password.  Any ideas?

---

### Post by IcarusR on 2008-04-26
Hi
Samba can be frustrating to get set up. Took me ages.
It seems to me you have no shares defined in your smb.conf.

This is my working smb.conf
 > 
[global]

workgroup = Home

server string = Samba Server Florence

hosts allow = 192.168.1. .127

hosts deny = all

#  guest account = guest

   log file = /var/log.%m

   log level = 3
   
   max log size = 200

   dos charset = CP850

   security =  user

  encrypt passwords = true

   socket options = TCP_NODELAY 

   interfaces = eth0  

[data]
comment = MY JUNK
path = /data
public = no
guest only = no
writeable = yes
browseable = yes
valid users = andy
create mask = 0777
directory mask = 0777

[pics]
path = /pics
public = no
guest only =  no
writeable = yes
browseable = yes
vailid users = andy
create mask = 0777
directory mask = 0777

[music]
comment = Ripped CD's
path = /music
public = no
guest only = no
writeable = yes
browseable = yes
create mask = 0777
directory mask = 0777

I do not use samba for printing so couldn't help you there.
All your shares must be read/writable by the user that you want to use them.

You need to follow this part of the howto you linked...

> -> [MyFiles]

This is the name of the share. Leave it as it is or adjust it to whatever you prefer. Don't use more than 31 characters and try to avoid spaces!

-> path = /media/samba/

This suggests that you've mounted an hard drive or partition on /media/samba where all the shared files will be stored.

In case you don't have an extra hard drive/partition you may also create folder.

I assume you've been wise enough to put /home onto a separate partition having an reasonable amount of storage space.

To create the folder type (inside a new terminal) ...

Code:

sudo mkdir /home/samba

... and adjust "path =" to read ...

path = /home/samba/

Remember that this is just an example - you are free to put things wherever you like.

-> force user = YOUR_USERNAME
-> force group = YOUR_USERNAME

Well, this should say it all. Replace "YOUR_USERNAME" with the name you use for login (no spaces!).

Example:

force user = stormbringer
force group = stormbringer

Now we completed the part of editing smb.conf

Save the file and close gedit.

Since we are going to share the folder with other users we should now make sure that the permissions are set. Type:

Code:

sudo chmod 0777 /media/samba

NOTE: Don't forget to correct the path to the location you chose above!

That's it - now we need to start samba ...


Hope this helps

---

### Post by chicoharv on 2008-04-27
I don't know if this will help but if you are on your vista computer and it asks you for your user and password it wants the one for your Ubuntu  not your windows log on. I have a different problem, my shares worked right out of the upgrade but I can't get my windows printer to work on Hardy but it was working on Gutsy

---

