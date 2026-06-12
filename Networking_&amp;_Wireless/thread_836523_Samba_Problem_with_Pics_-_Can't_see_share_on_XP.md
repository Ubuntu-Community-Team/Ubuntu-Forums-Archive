---
title: "Samba Problem with Pics - Can't see share on XP"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by AlucardXXVII on 2008-06-21
I have a media center with XP.  The PC's name is MEDIACENTER.  It's hooked up to my TV

I have a desktop PC running ubuntu 8.04.  Its name is Justin-desktop

I can't figure out what I'm doing wrong.  I can get to my MEDIACENTER share by typing smb://192.168.1.104 in nautilus.  That's how I got the screenshot into GIMP.

Take a look
[IMG]http://i6.photobucket.com/albums/y241/justinxxvii/ubuntu.png[/IMG]

the untitled.png is a screenshot I shared over from MEDIACENTER

I get this error on Windows XP:
[IMG]http://i6.photobucket.com/albums/y241/justinxxvii/xp.png[/IMG]

As you can see, in My Network Places I can see the justin-desktop machine.  I just can't get into any of my shared files (/media/samba/)

By the way, I can't check the "allow guest" box in the sharing properties.

[IMG]http://i6.photobucket.com/albums/y241/justinxxvii/guest.png[/IMG]

What have I done wrong?
smb.conf =
```
[global]
    ; General server settings
    netbios name = justin-desktop
    
    workgroup = AMBERSON
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    usershare owner only = False
    passdb backend = tdbsam
    security = share
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

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
    path = /media/samba/
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = justin
    force group = justin
available = yes
browsable = yes
public = yes
writable = yes

```

---

### Post by AlucardXXVII on 2008-06-21
anyone?  i can share between two xp machines, also.

---

### Post by superprash2003 on 2008-06-21
have you added samba users successfully?are you able to ping your ubuntu from windows successfully?

---

### Post by AlucardXXVII on 2008-06-21
I'm not sure what you mean by adding samba users successfully.  In my system, admin, users, manage groups, smbguest and justin both have access to share files and justin also is a member of sambashare,

as far as pinging ubuntu from windows, if i type the IP address 192.168.1.107 i get a success but i can't ping \\justin-desktop, that fails

---

### Post by sp0nge on 2008-06-21
Windows networking wizard is rather picky in my experience. I have never experience Windows MCE, but I would suggest running through the setup of the network settings just to see if it works itself out.

---

### Post by AlucardXXVII on 2008-06-21
i tried that already on both my xp laptop and media center.  by the way, it's XP Pro on the media center pc

---

### Post by AlucardXXVII on 2008-06-21
So by my pictures, can anyone determine what I'm doing wrong?  I know that one part of the deal is set up right.  For some reason Ubuntu isn't authorizing my windows xp pro to open any shared folders.  Windows XP doesn't seem to mind that Ubuntu can open shares.  Why does this have to be so hard?

---

### Post by AlucardXXVII on 2008-06-22
on Ubuntu, my main login is

justin

I am not root, I have to use sudo commands to change anything

on XP, the account name is "Administrator" but there is no password.  The dialog comes up when the computer starts, but I just press enter for no password and windows starts.  In XP, I turned the guest account On.

Does this help any?

---

### Post by superprash2003 on 2008-06-22
i'd say its better you setup samba again [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by plewisfdx on 2008-06-22
> **AlucardXXVII said:**
> on Ubuntu, my main login is

justin

I am not root, I have to use sudo commands to change anything

on XP, the account name is "Administrator" but there is no password.  The dialog comes up when the computer starts, but I just press enter for no password and windows starts.  In XP, I turned the guest account On.

Does this help any?

yes, I think. 

On your smb.conf you "force user = justin" so maybe "justin" needs to be the user to see the share because of the permissions.

When I have trouble on winxp accessing a share, it pops up a dialogue asking for name/password.  I assume this isn't happening?  See if there's a way to enter this, otherwise, create user justin on the winmce machine and see if he can see the share.

---

### Post by Djzn.BR on 2009-11-07
I HAD the same problem. I had to help a friend to transfer some SATA HDD files to his notebook and I used the network to do this. I was able to make Linux copy the files to Windows Vista. Windows could see Linux but could not access the folders, like the issue you are having. But later, investigating the issue, I found out that my Linux box was set to DHCP and thus not having IP manually configured.

Before this came to my mind, I went and wrestled with Samba without success, installed gadmin/samba and messed with config files, etc. Nothing would work. In the end, I restored the original smb.conf in /etc/samba and figured out: MY NIC had to be manually configured.

**After entering the IP, Gateway, Net Mask.... EVERYTHING WORKED for Windows XP and Vista**. Both systems could see Linux. The share could be easily setup via Nautilus by the Share option, **RIDICULOUSLY EASY.** Before this I went to IRC channel ask questions, people replied me to make user access accounts, etc. But I didn't have to do this. Set up properly your network card and see what happens. I believe that through DHCP requires another special configuration. The sharing option in Nautilus really does what it says: Allow anyone to mess with this share.

---

