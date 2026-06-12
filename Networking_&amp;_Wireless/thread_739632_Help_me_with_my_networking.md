---
title: "Help me with my networking"
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by luceerose on 2008-03-29
I am clueless as to how to network with Ubuntu. 
---
Here's my current setup;

Computer1 - Ubuntu w/ attached printer
Computer2 - XP
DSL modem - 4 port router
8 port hub - not using yet
Spare PC - to be used as standalone firewall
[We're talking wired 100mbps & adsl]
ISP is on dynamic IP > all computers are set to automatic addressing
---
Here's what I am working towards;

FirewallOS pc [zoned - Red / Purple / Green] hooked into the router/modem.
[The way this works is Red zone connects to internet (router), Green (trusted) zone PCs can freely access each other & the internet, Purple zone can access the internet but not the other PC's]

All items below will be connected to the above Firewall PC
Computer1 & 2 hubbed to Trusted zone + eventually more *buntu pcs on same hub.
2nd Hub to Purple zone for laptops to hook into
---
I pretty much know how to sort out the firewall pc, so that's not an issue at this stage.
For now, I just need my Trusted zone PC's communicating with each other the way I want.
So, to make things nice & simple, we're just working with PC 1& 2 hooked into the router.

What I want;
i)  I want XP(PC2)  to be able to print using the printer attached to Ubuntu(PC1).
ii) I want to be able to access the files on XP from Ubuntu pc. (Ideally I want Ubuntu PC to be able to access anything on the network, maybe with the exception of the laptop hub).
iii) I don't want XP to have access to files on Ubuntu at all.
iv) If I plug a complete strangers Laptop into the network I want to able to use the printer with it.

On the XP computer I will probably only want to access it's 'Shared Documents' folder, which I have already told windows to share.
Also XP pc has a firewall program [zonealarm] which I suspect will prevent me from doing things easily, so for now I have turned zonealarm off.

And, No I don't actually use the XP computer for anything. It is only there as a convenience for retards to use.
Thanks in advance for your help, everyone...

---

### Post by Eiríkr on 2008-03-30
Looking over your wish list:
[list=i][*]I have no idea about proper printer sharing except that you'll want to install and configure Samba, with the printer as the only share.  I'm pretty familiar with Samba file sharing, but not printer sharing, so someone else will have to chime in on that score.
[*]You'll need to configure folders on XP for sharing.  Right-click the folder(s) for sharing, select "Sharing and Security...", click the "Share this folder" radio button, and click the Permissions button to set up which XP users have access to the share and with what permissions (read, write, etc.).  Sounds like you've already done this.
[*]So long as you don't go to the trouble of adding file share definitions to your Ubuntu machine's Samba config file, no files will be shared.  
[*]See above about printer sharing.  [/list]

HTH get things started,

Eiríkr

---

### Post by luceerose on 2008-03-30
Step i) - accomplished
Step iv) - untested but presumably accomplished

Only step ii & iii remain.

All I need now is the ability to access the shares on the Microsuck Winblows computer.

Have enabled sharing on Shared Documents folder on Winblows but can't figure it out from Ubuntu end.
Tried GSAMBAD and some other things, but all they did was stuff things up. Reverted back to original file.

Here is my smb.conf ;
--------------------------

[global]

## Browsing/Identification ###

   workgroup = GUITARS

   server string = %h server (Samba, Ubuntu)

;   wins support = no

;   wins server = w.x.y.z

   dns proxy = no

;   name resolve order = lmhosts host wins bcast

#### Networking ####

;   interfaces = 127.0.0.0/8 eth0

;   bind interfaces only = true



#### Debugging/Accounting ####

   log file = /var/log/samba/log.%m

   max log size = 1000

;   syslog only = no

   syslog = 0

   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

;   security = user

   encrypt passwords = true

   passdb backend = tdbsam

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

   unix password sync = yes

   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

   pam password change = yes

map to guest = bad user

########## Domains ###########

;   domain logons = yes

;   logon path = \\%N\profiles\%U

;   logon path = \\%N\%U\profile

;   logon drive = H:
;   logon home = \\%N\%U

;   logon script = logon.cmd

; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

########## Printing ##########

   load printers = yes

;   printing = bsd
;   printcap name = /etc/printcap

   printing = cups
   printcap name = cups

############ Misc ############

;   include = /home/samba/etc/smb.conf.%m

   socket options = TCP_NODELAY

;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

;   domain master = auto

;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

;   winbind enum groups = yes
;   winbind enum users = yes

;   usershare max shares = 100

   usershare allow guests = yes

#======================= Share Definitions =======================

;[homes]
;   comment = Home Directories
;   browseable = no

;   read only = yes

;   create mask = 0700

;   directory mask = 0700

;   valid users = %S

;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   read only = yes
   create mask = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = yes

;   write list = root, @ntadmin

;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom
------------------------------------------

It's pretty much stock standard, I've only changed about 2 things.
So what do I need to add, change, uncomment to be able to access the XP computer ?

---

### Post by SpaceTeddy on 2008-03-30
if you are trying to access the windows machine from ubuntu, you don't even need the samba server (afaik) - the client should suffice. If the client is installed, you should be able to access the computer directly from nautilus (filebrowser) by typing smb://IP where you replace the IP by the acctual ip address assigned to the computer. Also, you might try and use the computer name, but the name resolution in windows networks was always a little... shaky... 

Of course this will only work if you have the windows setup properly. I am not entriely sure of how to go about this, but what you could try (on the windows machine) to see if the shares are at least there is connect to yourself and see what shares get offered. 

This can be done by going to start->run and typing \\127.0.0.1
that should give you a list of shares your windows computer holds at the moment... 

hope it helps

---

### Post by luceerose on 2008-03-30
Yeah, see that's the problem. If I just type the IP in Nautilus I get an error mesage.
Refer to attached image.

---

### Post by luceerose on 2008-03-30
PROBLEM SOLVED
All solved. All iv goals accomplished. Mission a complete success.

Zonealarm on the XP computer was stopping me from accessing it, despite the fact that I had disabled & exited it. Stoopid winblows programs. I really hate that $%^%&^% %%% $$((^% Windoze computer.

I just added my IP range to the trusted zone in Zonealarm, and all the XP shares, etc popped up in Nautilus pretty much straight away.

The things we sometimes overlook, huh.

---

### Post by Eiríkr on 2008-03-30
Well, seems I'm late in my reply, but since I started it last night and finally finished it, I may as well post.  ;)

-----
> **larsenguitars said:**
> Step i) - accomplished
Step iv) - untested but presumably accomplished

Only step ii & iii remain.

Good news.  :)

> **larsenguitars said:**
> All I need now is the ability to access the shares on the Microsuck Winblows computer.

Have enabled sharing on Shared Documents folder on Winblows but can't figure it out from Ubuntu end.
Tried GSAMBAD and some other things, but all they did was stuff things up. Reverted back to original file.

A *very* good idea.  gsambad appears to be **extremely** behind the times in terms of valid conf file options, and I have yet to see a case of someone using gsambad and getting anything out the other end that doesn't royally bork their Samba setup.  

From all I've read, the smb.conf file is irrelevant when your Ubuntu machine is acting as a Samba client, i.e. accessing another share.  For that, you need to make sure you have the [font=courier]smbclient[/font] and [font=courier]smbfs[/font] packages installed.  Then, in Nautilus, you should be able to click Go -> Network, and see your Win XP box right there.  If not, double-click Windows Network, then your workgroup, and you should see your XP machine and your Ubuntu Samba server.  Double-clicking your XP machine should show you the shares on that machine (possibly after a slight lag), and double-clicking a share should prompt you for login and password, and then give you access to the files.  

--------------------------
Looking over your smb.conf file here, I've only commented on those items that seemed noteworthy:

**[global]**

[b][unix password sync](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#UNIXPASSWORDSYNC) = yes
[url=http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PAMPASSWORDCHANGE]pam password change = yes[/b]

These are interesting options, but given your setup it looks like you have them here for a good reason.  ;)

[b][printing](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PRINTING) = cups
[printcap name](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PRINTCAPNAME) = cups[/b]

These options are only relevant within a printer share definition, and do *not* belong in the [global] section.  Have a look at the relevant man page sections linked to in the option names. 

**[usershare allow guests](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#USERSHAREALLOWGUESTS) = yes**

This is also an interesting option, but it looks a bit odd here as you have none of the other user share options specified...?  [The relevant man page section](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#id2483661).


[b][[printers](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PRINTERSSECT)]
[print$][/b]

These look fine.  One thing to note, though, is actually listed in the [font=courier][guest account](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#GUESTACCOUNT)[/font] section:
> On some systems the default guest account "nobody" may not be able to print. Use another account in this case. You should test this by trying to log in as your guest user (perhaps by using the su - command) and trying to print using the system print command such as lpr(1) or  lp(1).

Your [font=courier]guest account[/font] option is commented out, which means your Samba server will use this "nobody" account.  It sounds like this might work on some systems, but not on others, so test and change as needed.  

--------------------------
Out of curiosity, where had you picked up the template smb.conf file you used?  I've seen a number of folks using an smb.conf file with these mysterious printing options that don't belong in the [global] section, which makes me think there's either a GUI tool or an online template somewhere that does this.  

Glad to hear things are working now.  Let us know if there are any further wrinkles to iron out.  :)

Cheers,

Eiríkr

---

