---
title: "Setting up Samba"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by Hickeydog on 2007-02-07
I need a good walk through to set up Samba.  I have my Linux box along with 4 other windows 2000 pc's.  I need to be able to read and write files to and from all of the computers.  It is a windows network and I don't want to change any of the settings.  From my Linux box, I can see most of the computers some of the time.  From my 2000's, I cannot see the Linux box.  I need a walkthrough on how to set up Samba that will make all the computers visible all the time.

---

### Post by dmizer on 2007-02-07
to set up ubuntu so windows can see it, use the first link in my sig.

to set up ubuntu so it can see windows, use the second link in my sig.

---

### Post by Hickeydog on 2007-02-08
ok.  I managed to get my Windows to see my Ubuntu.  However, I cannot do anything with that.  I would like the Windows to be able to see my / and be able to edit all files in there.  How do I go about setting that up? 

by the way.  THANK YOU SOOOOO MUCH FOR THAT WALKTHROUGH!!!!!!:) :)  other's i've tried were a complete disaster

---

### Post by dmizer on 2007-02-09
if you followed the directions in the howto carefully, you should end up with read/write permissions on your share.

you MUST add your windows login id to your ubuntu machine.

---

### Post by gradedcheese on 2007-02-09
> 
I would like the Windows to be able to see my / and be able to edit all files in there. How do I go about setting that up? 


I advise you against sharing the entire root file system.  This is a security risk and generally not a good idea.  Consider the fact that, outside your home directory, you need root privileges to write, so your share would have to be shared that way too... ouch.   

Share one isolated directory (like /opt/share or something) instead.  If you want to access/edit the entire file system in Windows, use ssh to log in and do it (this is normally how servers are administered, for example).  Also, a more minor note: Windows uses the rather stupid '\r\n' line termination for lines in text while Linux uses '\n' -- that may mess up some settings files unless your Windows text editor can be told to work in '\n' mode (same goes for viewing).

---

### Post by monomaniacpat on 2007-02-09
> **dmizer said:**
> to set up ubuntu so windows can see it, use the first link in my sig.

I am having a similar problem. In an effort to get my linux box connected to Xbox Media Center, I have been trying to test the samba server with a Windows PC.

I have followed the how-to to-the-letter, but I cannot get access from the PC. In fact, it doesn't even show up in the workgroup (MSHOME) initially, but when I've tried to mount the drive (as per the tutorial) it magically appears. When I double click on the Samba Server, it says "you may not have permission to use this network resource". 

I have setup the username and password, and added it into the dialogue box in windows, but no give.

Here's the contents of my smb.conf:

```
[global]
    ; General server settings
    netbios name = inspiron-8200
    server string =
    workgroup = MSHOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
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
    path = /home/patrick/downloads
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = patrick
    force group = patrick
```

Thanks for any help you can give!

---

### Post by dmizer on 2007-02-09
this might be your problem ...

per the howto, if you are running dhcp, then this line:
```
wins support = yes
```
should read
```
wins support = no
```

> I advise you against sharing the entire root file system. This is a security risk and generally not a good idea. Consider the fact that, outside your home directory, you need root privileges to write, so your share would have to be shared that way too... ouch.
yes.  this is quite right.  there is zero reason to share your entire root directory over samba.  in fact, doing so will probably result in a broken system.

---

### Post by monomaniacpat on 2007-02-09
> **dmizer said:**
> this might be your problem ...

per the howto, if you are running dhcp, then this line:
```
wins support = yes
```
should read
```
wins support = no
```


Thanks for the reply. Sadly, this didn't work. I even tried it with all my firewalls turned off - to no avail. :(

Any more ideas?

---

### Post by Iowan on 2007-02-09
> **monomaniacpat said:**
> I have setup the username and password, and added it into the dialogue box in windows, but no give.
The username  (and password) were set up both for the server AND Samba?

---

### Post by Hickeydog on 2007-02-09
I can see were you would be saying not share the entire / directory, but i would like to be able to able to have my /home/hp266 (were i store all my files) (hp266 is my computer name) available on the network.  The walkthrough really didn't explain how.  other than that it was great.

---

### Post by monomaniacpat on 2007-02-09
> **Iowan said:**
> The username  (and password) were set up both for the server AND Samba?

I'm not sure what you mean. I followed the commands: 

```

sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username

```

My username for ubuntu and samba are the same, as it happens.

---

### Post by Hickeydog on 2007-02-09
now i can't access my network without a user name and password.  I did not need it before i re-booted, but now i do.  everytime i try to open up my network, i get 
"Authentication Required"
"You must log in to access guest@hxengr" (hxengr is my network/workgroup name)
then it asks for a username, domain, and password.  I have tried entering in my Ubuntu username and password.  that doesn't work.  I tried the administrator name and password.  That doesn't work.  my network does not have a domain name.  I have no idea why it is asking me this and even more why it won't let me connect.  It's really annoying.  any help would be greatly appreciated

---

### Post by gradedcheese on 2007-02-10
All Windows networks have a domain or workgroup name, it's part of the spec I think.  The workgroup name is in the Shared Folders tool (click the Properties tab).  You can configure yourself to be a WINS server there too, sometimes that helps.  

Other than that, if you've set up Samba by adding yourself as a samba user, you should be set, but did you restart the samba daemon?

sudo /etc/init.d/samba restart

---

### Post by RichardL on 2007-02-10
Gentlemen, I wonder whether you can help me with the SAMBA too and ask to accept my apologies if the the problem was described somewhere  else but I missed out.

I managed to do the network between two computers and can see dedicated folders. 
On one I have path = /home/polon, on the other path = /home/richard and this "combination" allows me to read and copy the files between them. What I can not do though is to write on another computer for example update some data information.  
How should I modify smb.conf to solve this hassle.

Also, I have an external HDD connected to one computer with two partitions that is one NTFS for XP operations and one FAT32 as a common for Linux and Windows to read and write there. It works very well however I would like to make that FAT32 one available for the second computer when is turned on. Please tell me whether it is possible and what should be added to smb.conf file. Perhaps additional pass is needed or something. I still lack experience in Linux ( just few weeks at the moment ) and it will take ages before I will manage this problem myself. 
Thanks.
Richard

---

### Post by gradedcheese on 2007-02-10
> 
How should I modify smb.conf to solve this hassle.


Yeah, namely there will be a line "writable = yes" that you want set in your share.

---

### Post by dmizer on 2007-02-12
if followed closely, the samba thread i linked to will give you access to your samba shares with password protected access only.  this means that you will need to configure your windows computer with a password protected account (iow: not owner, and not admin).  this is of course intelligent and preferable network design for many more reasons than attacks from the net.

for example, if you have a wireless network ... someone with very little skill and a good howto can crack your wireless security in a few minutes.  then, without a password protected share, they will have complete and unrestricted access to anything you have shared on your network (which for most windows computers ... is EVERYTHING) ... even if you have a firewall.

this, of course, is not the only way you become vulnerable in such a situation but it's the most obvious.

however, if you are (unwisely) unafraid of a completely exposed network share, you can look at this thread: [http://www.ubuntuforums.org/showthread.php?t=336553](http://www.ubuntuforums.org/showthread.php?t=336553) to find out how to remove the password protection from your samba server.  it's not in a howto format, but all the necessary parts are there, and the thread is short.

@hickeydog:
> The walkthrough really didn't explain how. other than that it was great.
the walkthrough did indeed explain how.  quoted directly from the howto:
> > path = /media/samba/

This suggests that you've mounted an hard drive or partition on /media/samba where all the shared files will be stored.

In case you don't have an extra hard drive/partition you may also create folder.

I assume you've been wise enough to put /home onto a separate partition having an reasonable amount of storage space.

To create the folder type (inside a new terminal) ...

```
sudo mkdir /home/samba
```

... and adjust "path =" to read ...

path = /home/samba/

**[COLOR="Red"]Remember that this is just an example - you are free to put things wherever you like.[/COLOR]***

or iow, path = /whatever/folder/you/want/here/

*emphasis mine

---

### Post by Hickeydog on 2007-02-12
thankz for all the help.  I know i kinda go against the flow as far as security goes, but I have a very good firewall between my network and the internet, so I think im set.  Once again, THANK YOU ALL SO MUCH.  u guys r like gods to me.  i don't know what i'd do without this support forum.  :) :)

---

