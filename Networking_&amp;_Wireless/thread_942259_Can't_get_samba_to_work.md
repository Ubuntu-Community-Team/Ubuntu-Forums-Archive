---
title: "Can't get samba to work"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by ELMIT on 2008-10-09
Hi,

I followed several instructions to setup samba, but each one left me unhappy.

I have two Desktops (A, B) and one notebook with wired and wireless connection to a Netgear router.

The smb.conf looks for each one the same:
>  grep -v ^# smb.conf |grep -v ^$|grep -v ^\;
[global]
   workgroup = ELMIT
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   invalid users = root
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
map to guest = bad user
   socket options = TCP_NODELAY
   usershare allow guests = yes
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
[Ronald Shares]
path = /home/ronald/Desktop/Ronald_Shares
comment = Folder Ronald Shares with you
available = yes
browsable = yes
public = yes
writable = yes


I cannot see the other computers.

One thing is also strange. If I use wireless on the notebook, I see MY notebook and NETWORK with ELMIT and herein my notebook. With wired I don't see anything.

I would like to be able to connect the notebook via wired, wireless and E220 3G modem. I know later one needs more thought.

bye

R.

---

### Post by superprash2003 on 2008-10-09
firstly ensure that all the pcs are able to ping each other...and to access samba shares go to places->computer and under "go to" type smb://x.x.x.x where x.x.x.x is the ip of the ubuntu machine which has the samba server running

---

### Post by ELMIT on 2008-10-09
Thanks for helping me:

1. I can ping the location! (*.101, *.103)
2. Location smb://*.103 gives me the icons for Shared folder of the other computer and a folder print$  BUT  not for smb://*.101
3. Trying to open the folder of the shares on *.103 gives me an error: Unable to mount location
4. Trying to open the folder print$ asks for a password, but my password does not work there.
5. trying the same on *103, sees under Network "ELMIT" within ELMIT it sees my computer (*.103), within my computer it sees the same shared folder and print$ and here I get exactly the same as in 3. and 4.

What can we try next?

bye

R.

---

### Post by warchief_ryan on 2008-10-09
I would suggest you simplify your smb.conf, get it working then add to it.

---

### Post by ELMIT on 2008-10-09
> **warchief_ryan said:**
> I would suggest you simplify your smb.conf, get it working then add to it.

Thank you for your time to reply, ... it was really very helpful.

---

### Post by Skip Da Shu on 2008-10-10
> **warchief_ryan said:**
> I would suggest you simplify your smb.conf, get it working then add to it.

I might suggest first only running samba on one machine to start with and get rid of all the password security since this is all on your local home lan (I assume).

Try [**THIS**]("http://www.debuntu.org/guest-file-sharing-with-samba") super simple set-up first.

Maybe this config file I was working on for a more specific how-to in another forum might help also:

```
; To implement samba, install the packages Samba and Samba-common (I use Synaptic Package manager).
; Other than a one line entry in /etc/fstab to mount an entire HDD to be shared and creating (optionally) a guest user from the System menu, all the
; configuration is done in this file.

#
# Configuration file for the Samba suite for Debian GNU/Linux.
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
#
#======================= Global Settings =======================

[global]
## Browsing/Identification ###
#
   workgroup = CRUNCHERS  	; Set to name of your windows workgroup.  
				; File as installed will have this as "MSHOME"(W2K).  Your windows (XP) machines may default to WORKGROUP.  
;				; I set all mine to 'CRUNCHERS' in WinXP via My Computer, right click, properties, computer name, workgroup=CRUNCHERS
   server string = %h server
   wins support = yes		; enable wins client
   name resolve order = wins lmhosts host bcast
;				; above is the order of methods invoked to resolve remote host names to IPs
;   dns proxy = yes		; defaults to no

#### Networking ####
#
   interfaces = lo eth0		; local network, your ethernet port ID (usually eth0, but might be eth1 if 2nd nic installed
   bind interfaces only = true	; bind Samba to eth0 port
   netbios name = crunch20	; the name of THIS machine
;				; following are to use your Samba server as a maintainer of the computer browser list instead of WinXP
   announce version = 5.9	; only required if this machine to be the primary 'master computer browser'. else omit
   os level = 64		; ditto above, else omit
   domain master = yes		; ditto above, set to no otherwise
   preferred master = yes	; ditto above, set to no otherwise 
   local master = yes		; ditto above, set to no otherwise
;				; use the following settings if you have two Samba servers and 2nd one is to be the secondary 'master computer browser'
;   domain master = no		; these settings for secondary computer browser 
;   preferred master = no	; ditto above
;   local master = yes		; ditto above, set to no otherwise

####### Authentication #######
#					; there are 100s of combinations of authorization methods using domain servers, etc, available.
;					; assuming this is only to be accesed between your machines inside the same LAN/sub-net little is really needed.
   security = share			; settings to require no security to access from within your LAN, any machine.  Use security=user if you are going
					; to setup multiple user accounts on this machine for access to netshares.
   guest account = guest		; create user=guest, I set the pw=guest or something easy to remember
;  guest account = nobody		; try this and see if it eliminates the need to have "guest" user defined
					; some Windows based backup software (Acronis) will require this to create disk image backups on your netshares
;					; from a scheduled background task.			
   invalid users = root admin_user	
   encrypt passwords = true
   guest ok = yes			; allow unauthenticated user
   guest only = yes			; force no authentication
   hosts allow = 192.168.2. 127.0.0.1	; will allow any node on the LAN with IPs of 912.168.2.xxx and this machine itself to access netshares
   hosts deny = all

#### Debugging/Accounting ####

   log file = /var/log/samba/log.%m	; put log file in /var/log/samba
   max log size = 999			; rename old and roll in new log file after 999KB
   syslog only = no			; allow samba to write it's own log
   syslog = 0				; minimal logging
   panic action = /usr/share/samba/panic-action %d
   veto files = /*Security*/*.tmp/*root*/*boot*/

########## Domains ###########
#
;					; no domain, workgroup only set-up
########## Printing ##########
#
    load printers = no			; to load printer drivers for shared printers on your samba server.  Sharing printers not covered here.

############ Misc ############
#					
   socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536	;some parms that are supposed to improve thruput, copied
   deadtime = 15
   default case = lower			; default new filenames to all lower
   max connections = 5			; max machines to access netshares at same time
   preserve case = no			; convert copied file names to lowercase
   printable = no

#======================= Share Definitions =======================
#
 [netshare2]				; define what you want to share
   comment = network shared drivespace	
   path = /mnt/netshare2		; where the device to be shared is mounted.  In this case it's an entire HDD.
;					; to share an entire drive you need an entry in the /etc/fstab file to mount that HDD. 
;					; since I'd originally pulled this drive from a WinXP machine I originally left it as a NTFS drive.
;					; Samba will support this also you need only change the 'ext3' entry in fstab to be set for ntfs.
;					; I later converted the drive to ext3 format for better linux tool compatibility and better journalling
;					; Samba will also support ReiserFS.  My fstab entry for the shared HDD below:
;					
; # network shared - netshare2          /dev/sdb1  	  			/mnt/netshare2  ext3 	  defaults 	  	   	0 	2
;
;
   writeable = yes
;  create mask = 0664
   create mask = 0775			; allow read, write 
   directory mask = 0775		; allow directory read, write (create)
   public = yes				; not subdivided by user
   guest ok = yes			; guest access allowed
   only guest = yes			; guest access only, force no authorization


; you are now done with the smb.conf configuration of Samba.  If you are sharing an entire HDD as here and have already created the fstab entry then
; you need only reboot and your netshares should be available to any machine (windows or linux) on your network.  To access the netshares from a
; winxp machine just open an explorer window and navigate to My Network Places-->Entire Network-->Microsoft Windows Network-->Workgroup (or in my case
; Crunchers) and you should see your Samba server there.
;
; Long after I had done this I found a possibly even simpler setup here http://www.debuntu.org/guest-file-sharing-with-samba
;
; To access your netshares on Xubuntu machine first create a folder under your home/user/ on that machine.  I created netshare2 under /home/user 
; (/home/user/netshare2).  Then in a termnal enter the following:
; sudo mount //192.168.218.20/netshare2 /home/user/netshare2
;
; you should then be able to go to /home/user/netshare and see everything on the shared drive.
;
; before leaving that machine do this command in a terminal
; sudo umount /home/user/netshare2
; I've created two desktop launchers one called "mount netshare2" and another called "drop netshare2".  Use same commands as above and check 
; the "run in terminal" box.
; In Jeff's earlier NFS how-to he used autofs to do the mount/unmounts.  That sounds like a better option but as of this writting I haven't implemented 
; it yet.
```

---

