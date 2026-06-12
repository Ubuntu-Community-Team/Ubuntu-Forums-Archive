---
title: "STILL can't browse windows shares??!?!?!"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by b0b138 on 2008-11-03
Does this issue really still exist? Or am I missing something?

---

### Post by LeBurt on 2008-11-03
In my case I can browse Windows shares from Ubuntu but not Ubuntu shares from Windows.

Here's [my post]("http://ubuntuforums.org/showthread.php?t=970160") about it, still waiting for some help.

---

### Post by cariboo on 2008-11-03
To use Ubuntu shares from Windows you need to set up Samba. There probably isn't a howto for Intrepid yet, but this one should work:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Another great resources is this:

[www.samba.org/samba/docs/Samba3-ByExample.pdf](www.samba.org/samba/docs/Samba3-ByExample.pdf)

This one helped me quite a bit.

Jim

---

### Post by b0b138 on 2008-11-04
Yeah, seeing ubuntu shares from windows hasnt been a problem. Though it does not do it "out of the box". The easiest way to set that up is to right-click a folder, goto sharing options, and when you click share this folder, it will install what it needs to (samba and a couple of other packages I think)

But starting with Hardy, no browsing of windows shares.

---

### Post by fwre01 on 2008-11-04
What's the error message you get when trying to access a windows share?

I think I know what you're refering to, and i believe its a bug.

---

### Post by rickatnight11 on 2008-11-04
There is no error message.  This has been a problem for me as well since 8.04.  Opening up Network shows Windows Network.  Double-clicking that results in the window thinking for a while before displaying a blank page.  It doesn't find any computers.

---

### Post by apt on 2008-11-04
Yeah same here.  I was hoping Intrepid would fix this issue but not as yet.  Does anyone know of a time-frame for when this will be fixed?  I'm not sure of the background to this bug (It is a bug right?) but in my opinion if Ubuntu want to integrate into big business (or even small business) they need to be able to access windows servers/clinets for a true cross platform experience.

---

### Post by rickatnight11 on 2008-11-04
I haven't been able to get a straight answer on where this bug originates from.  Ubuntu supporters want to blame gnome, gnome supporters want to blame smb, and smb supporters are blaming everyone else.

---

### Post by b0b138 on 2008-11-04
No error message, it just doesn't show the shares. It shows the computers though. I can manually type in the share (smb://computer/share) But thats not browsing though.

It is my understanding it has to do with the newer gnome in hardy and intrepid. Cause the share information seems to be handled more by gnome. For example, ubuntu share information used to be stored in smb.conf. Now if make a share, smb.conf doesn't show it. Though you can manually add to it or use a gui frontend for smb.

But who knows, I just cant believe this bug is still around.

---

### Post by zacktu on 2008-11-04
I did a clean install of 8.10 onto one of my computers.  It was important to me to be able to view Windows shares, so I wanted to confirm that Windows shares would work.  I had to do two things in order to view Windows shares:

1) Install smbfs.

2) Place the IP address of the Windows host into the /etc/hosts file.  

My notes aren't clear as to whether #2 was necessary for viewing Windows shares.  I was also enabling use of the mount command to mount Windows shares, for which #2 was definitely necessary.

---

### Post by gbus1 on 2009-01-02
This is a tragic set back for Ubuntu, or linux in general if it is a gnome problem.  This is such basic functionality.  How could Ubuntu release this product with such a known bug?  If linux is trying to become more mainstream in business and in the home, this will be a real deal breaker for most users.
Get this problem fixed - fast.

---

### Post by sgage on 2009-01-14
I am running Intrepid, and I can browse Windows shares just fine. I don't think it's a bug, I think it's a simple matter of configuring your smb.conf correctly. I just cut'n'pasted from an smb.conf that I found on a message in this forum from some time ago - 2006 I think.

Samba has gotten complicated - I used to actually understand most of the parameters. Now I just use the following, and it works fine in a network with XP boxes. Adjust to your situation:

[global]
    ; General server settings
;	netbios name = your_computer_name
	server string = 
	workgroup = your_group_name
	announce version = 5.0
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

	passdb backend = tdbsam
	security = user
	null passwords = true
	username map = /etc/samba/smbusers
	name resolve order = hosts wins bcast

	wins support = no

;	printing = CUPS
	printcap name = CUPS

;	syslog = 1
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
    ;path = /var/lib/samba/profilhttp://us1.samba.org/samba/docs/man/Samba-Guide/simple.html#id2543020es
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
;	read only = yes
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

; A share
[MyFiles]
	path = whatever
;	browseable = yes
	read only = no
;	guest ok = no
	create mask = 0644
;	directory mask = 0755
	force user = your_user_name
	force group = your_group

---

### Post by ASchweitzer on 2009-01-14
I can't get at my windows shares from Ubuntu either, though I vaguely remember doing it at some point. Maybe 7.10. Still haven't found the problem/solution.

---

### Post by tarvinder on 2009-01-14
I did a fresh install of Ubuntu 8.10 x64 and I'm so disappointed by not being able to access my server (samba running on PCLinuxOS). I can access my server from Mac OS X and my Laptop (Windows) but from Ubuntu it's invisible. Thinking of going back to Ubuntu 7.04.

---

